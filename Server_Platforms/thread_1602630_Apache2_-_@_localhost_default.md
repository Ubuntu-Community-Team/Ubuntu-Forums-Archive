---
title: "Apache2 - @ localhost default"
date: 2010-10-21
forum: Server Platforms
---

### Post by stefanov on 2010-10-21
I have installed lamp from tasksel , and while everything work fine i  got one small problem, that is when i open "localhost" it ask me do i  want to save file , witch type is .phtml.
So i saved file to check it  , and it hold this content :
[PHP]<?php
echo "Hello World"
?>[/PHP]
witch is the content that i added @ index.php to check does php configuration works correctly.
I have deleted all files that are held there , and i added .htaccess ,  restarted apache and same thing happens everytime i try to load  localhost.
Any idea how can i fix this?
Thanks in advance!

---

### Post by Ryan Dwyer on 2010-10-21
The default configuration for the PHP module allows it to parse .phtml files, so I'm guessing you might not have the PHP module installed.

Please run: sudo apt-get install libapache2-mod-php5

---

### Post by stefanov on 2010-10-21
I found out where problem lied, i actually played a little and created a new site, and in this site file existed which i completely forgot about , all is fine now!
Thanks for help though!

---

