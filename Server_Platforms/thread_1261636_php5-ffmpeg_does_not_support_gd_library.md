---
title: "php5-ffmpeg does not support gd library"
date: 2009-09-09
forum: Server Platforms
---

### Post by amrmahrous on 2009-09-09
when i run php --info | grep GD it show the GD library is enabled

> GD Support => enabled
GD Version => 2.0 or higher

I have done the FFmpeg and FFmpeg-php installation

php -i | grep ffmpeg

> additional .ini files parsed => /etc/php5/cli/conf.d/ffmpeg.ini,
ffmpeg
ffmpeg support (ffmpeg-php) => enabled
ffmpeg-php version => 0.5.1
ffmpeg.allow_persistent => 0 => 0it

the gd library is not enabled in the php5-ffmpeg
how may i enable

---

