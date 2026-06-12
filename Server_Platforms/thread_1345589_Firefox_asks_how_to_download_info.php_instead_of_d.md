---
title: "Firefox asks how to download info.php instead of displaying it"
date: 2009-12-04
forum: Server Platforms
---

### Post by Stoneface on 2009-12-04
I have added a new folder to my localhost to work on an order form and to check what stuff I have on the server I added info.php with ```
<?php phpinfo(); ?>
``` When I surf to localhost/folder/info.php with Firefox 5.5 it asks me where to save the file (you have chosen to open info.php from [http://localhost](http://localhost) What should Firefox do with.. ), but it won't display in the browser. Any ideas why?

---

### Post by Bunnybugs on 2009-12-04
Well, I guess firefox recognizes that /localhost serves as an serverlocation, not as a webpage. As far as I know, this is how it should be!

---

### Post by Stoneface on 2009-12-04
Never mind. Forgot I had installed Ruby, but no PHP yet...

---

### Post by Stoneface on 2009-12-04
Well I installed php5 and restarted apache2, but still the same issue. Installed Wordpress before and all php files opened just fine. Strange...

---

### Post by Stoneface on 2009-12-04
Strike the last comment. I had to empy cache and now Firefox is purring like a little kitten :-)

---

### Post by BkkBonanza on 2009-12-04
Are you sure that apache knows to interpret php files rather than send them.
I haven't used apache for a few years but it used to be you had to add a config directive to ensure php files were executed.
Just googled it for you,

AddType application/x-httpd-php .php

Also make sure php module is being loaded.

---

### Post by Stoneface on 2009-12-04
@ BkkBonaza Well, it seems to work now with php5 installed and the module enabled. A final empty cache did the trick.

---

