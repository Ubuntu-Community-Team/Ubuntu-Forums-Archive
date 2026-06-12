---
title: "Drupal Video Player???"
date: 2015-03-05
forum: Server Platforms
---

### Post by benrob0329 on 2015-03-05
So I am trying to get a localhost test site running with Drupal 7, and I can't get the Video module to work. 
```

[LIST]
[*]*Notice*: Undefined index: wxh in *Transcoder->executeConversion()* (line *161* of */var/www/html/modules/video/includes/Transcoder.inc*).
[*]*Notice*: Undefined offset: 1 in *TranscoderAbstractionFactoryFfmpeg->setAspectRatioOptions()* (line *676* of */var/www/html/modules/video/transcoders/TranscoderAbstractionFactoryFfmpeg.inc*).
[*]*Warning*: Division by zero in *TranscoderAbstractionFactoryFfmpeg->setAspectRatioOptions()* (line *676* of */var/www/html/modules/video/transcoders/TranscoderAbstractionFactoryFfmpeg.inc*).
[*]*Warning*: fmod() expects parameter 1 to be double, string given in *video_utility::roundToEvenNumber()* (line *324* of */var/www/html/modules/video/video.utility.inc*).
[*]Something went wrong with transcoding *Animation Movie - Caminandes Episode 2 - 3D Animated Short Film HD (HD).mp4*. Please check your [recent log entries]("http://localhost/?q=admin/reports/dblog") for further debugging.
[/LIST]

```

Any suggestions? Or maybe a different *free* module? I know I could just use Wordpress, but Drupal has* way* more customize-ability.

BTW, I am running Apache2 with Php5 and mysql. I also am not using the Drupal7 package from the repositories.

---

