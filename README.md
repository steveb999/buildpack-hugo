## buildpack-hugo

Dokku or Heroku buildpack for Hugo (gohugo.io)
It will always use the latest stable version of Hugo.

## Features

* Build your Hugo website
* Always using the latest version of Hugo

## Requirements

* Dokku server
* Git

## Deploy Hugo on Dokku

First you need to create a dokku app

```bash
dokku apps:create awesome-hugo-website
```

Create a `.buildpacks` at the root of your git repository containing your hugo website and add `buildpack-nginx` and `buildpack-hugo`

```bash
touch .buildpacks
echo "https://github.com/Valdomar/heroku-buildpack-hugo" > .buildpacks
echo "https://github.com/dokku/buildpack-nginx" >> .buildpacks
```

Create a `.static` at the root of your git repository

```bash
touch .static
```

set NGINX_ROOT env variable of your `awesome-hugo-website` dokku app to `public` (the output directory of Hugo)

```bash
dokku config:set awesome-hugo-website NGINX_ROOT=public
```

And now you just need to deploy your app to your dokku server and it will be builded and rendered!
