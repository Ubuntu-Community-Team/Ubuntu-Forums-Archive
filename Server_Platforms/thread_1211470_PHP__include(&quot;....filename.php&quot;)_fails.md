---
title: "PHP  include(&quot;../../filename.php&quot;) fails"
date: 2009-07-12
forum: Server Platforms
---

### Post by MalcolmCowen on 2009-07-12
I want to use the PHP include statement to include a file held two levels up, but it fails and I can't see why.

I've copied a working PHP website to my new Ubuntu (Hasty) system to work on it.  At the start of each path a config file is read from 2 levels up with 
include("../../Config.php");

On my Ubuntu system this translates to 
/var/www/includes/Setup.php   calling
/var/Config.php

except that it doesn't work.
If I use include("/var/Config.php");, then it works, but then it wouldn't work on the live site.

I've even set all 3 lots of permissions to anyone can read and write anything  for all directories and files involved (this system is behind a firewall) and it still fails.

Is there something that stops ".." going above the www level, or is there something about permissions I don't know?

---

### Post by abaden on 2009-07-12
This syntax should work just fine:
[PHP]
include("/var/Config.php");[/PHP]

Unless you have suPHP, you probably will need to have your PHP file owned by www-data:www-data. 

I'd take a look at the [php include()]("http://us3.php.net/manual/en/function.include.php") manual for more guidance, it's pretty loaded with examples. 


Alex

---

