---
title: "MiniGal Nano server problem"
date: 2011-07-04
forum: Server Platforms
---

### Post by coldraven on 2011-07-04
This is not really an Ubuntu related post but as I had asked here for advice I thought that this may help someone like me who is new to PHP.
I finally decided to use Minigal Nano to make a gallery on my site and it was all working well until this weekend when it crawled to a halt. It seems that their server is down and part of the script is trying to search for updates. So I edited the index.php and commented out that section. It now looks like this and the gallery is working great again.
Thanks to those forum members that inspired me to get my nose under the hood :)
Lines 126 to 136 of index.php
```
//-----------------------
// CHECK FOR NEW VERSION
//-----------------------
//if (ini_get('allow_url_fopen') == "1") {
//    $file = @fopen ("http://www.minigal.dk/minigalnano_version.php", "r");
//    $server_version = fgets ($file, 1024);
//    if (strlen($server_version) == 5 ) { //If string retrieved is exactly 5 chars then continue
//        if (version_compare($server_version, $version, '>')) $messages = "MiniGal Nano $server_version is available! <a href='http://www.minigal.dk/minigal-nano.html' target='_blank'>Get it now</a>";
//    }
//    fclose($file);
//}

```

---

