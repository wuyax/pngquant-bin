# ⚠️ Warn

This is a branch created for developers who can't access `raw.githubusercontent.com` properly. If you have a good internet connection, we do not recommend using this package.

# config

The default download site is `https://npmmirror.com/mirrors` or set to `https://raw.githubusercontent.com/imagemin` via the environment variable `PNGQUANT_BINARY_SITE`.

# pngquant-bin ![GitHub Actions Status](https://github.com/imagemin/pngquant-bin/workflows/test/badge.svg?branch=master)

> [`pngquant`](https://github.com/kornelski/pngquant) is a PNG compressor that significantly reduces file sizes by converting images to a more efficient 8-bit PNG format

You probably want [`imagemin-pngquant`](https://github.com/imagemin/imagemin-pngquant) instead.


## Install

```
$ npm install pngquant-bin
```


Make sure you have the correct version of [libimagequant](https://github.com/ImageOptim/libimagequant).

```
# via Homebrew for macOS
$ brew install libimagequant

# via apt-get for Debian distributions
$ sudo apt-get install libimagequant-dev
```

## Usage

```js
import {execFile} from 'node:child_process';
import pngquant from 'pngquant-bin';

execFile(pngquant, ['-o', 'output.png', 'input.png'], error => {
	console.log('Image minified!');
});
```


## CLI

```
$ npm install --global pngquant-bin
```

```
$ pngquant --help
```


## Updating pre-compiled binaries

The Linux binaries are statically linked so they should work on all Linux distributions. To recompile them:

1. `sudo apt-get install libpng-dev`
2. `./configure CFLAGS=-static && make && cp pngquant pngquant-64`
3. Repeat the above commands, but in a 32-bin docker container started with: docker run -ti -v `pwd`:/source i386/debian:9.3 bash
