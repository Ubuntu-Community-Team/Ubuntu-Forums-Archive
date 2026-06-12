---
title: "avi to mov pipe to browser....?"
date: 2008-11-06
forum: Ubuntu Studio
---

### Post by brownrl on 2008-11-06
Ok

Here is one that should be fun!!!

I have an iPhone...  ya ya I know enough already... No flash.

I also have an Ubuntu media center with a web server.

When I torrent an .avi movie I would like to be able to 'preview' it on my iPhone without using a flash thingy.

iPhone can play mov or mp4... streams...

So using either ffmpeg or mencoder I would like to read in the avi file and output as a mov file.

Lastly, I would like to do this in a PHP page...

So far I can convert the file to another file...

Not very helpful because then I have to wait for the conversion to happen completely. Also I don't see how to make ffmpeg output to a pipe. It has to be possible?

So I want to do something like this:

```

<?php

   $file = "acitest.avi";

   header( "YADA YADADA THIS IN AN MOV FILE..." );

   passthru( "ffmpeg somestuff to convert $file to an mov" );
   
   exit( 0 );
?>

```

---

### Post by nowardev on 2008-11-06
try with this

```
ffmpeg -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 -i INPUT OUTPUT
```


some informationa bout bitrate and resolution can be found here
or googling

[http://forums.macrumors.com/showthread.php?t=430972](http://forums.macrumors.com/showthread.php?t=430972)

this one is for who has compiled ffmpeg ... if you have not compiled you have to change libx264 with h264 abd libfaac with aac

```
ffmpeg -i INPUT -r 29.97 -vcodec libx264 -s 480x272 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -crf 24 -bt 256k -refs 1 -coder 0 -me umh -me_range 16 -subq 5 -partitions +parti4x4+parti8x8+partp8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 128k -ar 48000 -ac 2 OUTPUT
```

---

### Post by brownrl on 2008-11-06
close but not so close...

the ffmpeg must have a file output as it parameter...

In my case I don't want to output to a file....

I would like to output to the browser....

---

