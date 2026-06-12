---
title: "ffmpeg-php not working"
date: 2008-12-17
forum: Server Platforms
---

### Post by ulver on 2008-12-17
Hi, I have installed ffmpeg from source using some custon config on my server;

```
FFmpeg version SVN-r13737, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libtheora --enable-liba52 --enable-libgsm --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-libfaad --enable-gpl --enable-x11grab --enable-nonfree --enable-libamr-nb --enable-libamr-wb --enable-shared
  libavutil version: 49.7.0
  libavcodec version: 51.57.2
  libavformat version: 52.16.0
  libavdevice version: 52.0.0
  built on Jun 10 2008 14:07:39, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)

```

It worked perfectly, now I needed the ffmpeg-php extension so I downloaded it from [http://downloads.sourceforge.net/ffmpeg-php/ffmpeg-php-0.6.0.tbz2](http://downloads.sourceforge.net/ffmpeg-php/ffmpeg-php-0.6.0.tbz2)

phpize
./configure
make
make install

than I edited /etc/php5/apache2/php.ini
and added the line extension=ffmpeg.so 

when I do php -r 'phpinfo();' | grep ffmpeg i get

ffmpeg-php version => 0.6.0-svn
ffmpeg-php built on => Dec 17 2008 11:22:05
ffmpeg-php gd support  => enabled
ffmpeg libavcodec version => Lavc51.57.2
ffmpeg libavformat version => Lavf52.16.0
ffmpeg swscaler => disabled
ffmpeg.allow_persistent => 0 => 0
ffmpeg.show_warnings => 0 => 0

So it looks like it is installed properly but in my code

```
$movie = new ffmpeg_movie($fullPath);

            var_dump($movie);

            var_dump($movie->getDuration());

            var_dump($movie->getFilename());

            var_dump(filesize($fullPath));

            var_dump($movie->getBitRate());
```

When I run it I get 

```
string(39) "/var/www/dottv2/trle/web/uploads/cs.flv" object(ffmpeg_movie)#172 (1) { ["ffmpeg_movie"]=>  resource(173) of type (ffmpeg_movie) } float(O) string(O) "" int(12854883) int(O) 
```

It returns 0 to all parametars, doesnt seem to work...

Can anyone help me, did I miss something here?

---

