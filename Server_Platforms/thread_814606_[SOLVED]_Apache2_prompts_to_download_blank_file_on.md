---
title: "[SOLVED] Apache2 prompts to download blank file on root directory index"
date: 2008-05-31
forum: Server Platforms
---

### Post by fretless on 2008-05-31
Hi I have a standard repos install (upgrade from gutsy to hardy) of apache+php+mysql.

No problems in gutsy, only started appearing after upgrade.

Essentially it's a central development machine and I use the standard apache directory index (i.e. no index.html / index.php file) to just show the server tree at the root directory.

When I access the server I get (FF3b5):
-----
You have chosen to open

  which is a: ~ file
  from: [http://localhost](http://localhost)
-----

Subdirectories work fine.

I can recreate it in IE7, IE6 & FF2 on any computer in my network.

Edit:
Version: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch

---

### Post by webweaver on 2008-06-10
Hi, I am having the exact same problem.

Upgraded from Gutsy to Hardy, and now Apache2 gives me that open/download dialogue box when browsing to [http://localhost/](http://localhost/), but works fine browsing to [http://localhost/index.php](http://localhost/index.php) (FF3)

apache2handler:  Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch

I have tried adding a DirectoryIndex line into my [FONT="Courier New"]/etc/apache2/sites-available/default[/FONT] file, but no joy.

Any suggestions yet?

---

### Post by fretless on 2008-06-13
Finally fixed the problem:

Ensure the default index.html is removed from the root directory and clear the firefox cache.

I tried this and it didn't work.

I then deleted /etc/apache2 and reinstalled apache2.2-common

Then I tried clearing the cache again and it worked.

---

### Post by berriop on 2008-07-09
Problem Solved easy!!
I also had this problem, I uninstalled and installed everything (lamp) again several times and it didn't work. Finally I get the solution, easy:

I was opening the php files (eg. php_test.php) from the file>open of the browser or directly from the location /var/www folder, and it asked me to download the file, so instead I write the file name into the URL address eg. [http://localhost/php_test.php](http://localhost/php_test.php) and it works!! :)

---

### Post by fretless on 2008-07-09
That may be a quick fix for someone wishing to access a specific file.
My problem on the other hand involved access to the builtin apache directory index, which has no filename.
But, my solution wasn't overly complicated, so if you want a permanent solution, that would be it.

---

### Post by rps63ifid on 2008-07-16
I have apache2 + PHP + MySQL installed and configured, and have the "userdir" and "rewrite" modules enabled on my installation. I was seeing this same problem on anything coming out of my home directory where I didn't have a specific file specified on the URL (e.g., "http://localhost/~ron/goo/"). I was able to solve this problem by adding a "DirectoryIndex" directive pointing to the appropriate set of default files (e.g., index.php, index.html) within the Directory section of /etc/apache2/mods-available/userdir.conf and then restarting apache. (I had to flush my browser's cache, too, for it work.)

Your mileage may vary, but this could at least avoid the reinstall dance.

-- 
/ron

---

### Post by ULogger on 2009-05-21
Here is the solution for my part :

Faile: DirectoryIndex index.html index.htm index.shtml index.cgi index.php
Ok: DirectoryIndex  index.php index.html index.htm index.shtml index.cgi

If index.php is not first then index.php is downloaded.

---

### Post by bugmenot10 on 2009-09-11
I had this exact problem. When I just go to the site as [www.sitename.com](www.sitename.com) I get the error. When I type in [www.sitename.com/index.php](www.sitename.com/index.php) then it works. Turns out the problem was with the index.html file in the /var/www directory. There was a default file there which I did not want to delete. So, I renamed to index.html.bak. Now when I renamed it to bak.index.html.bak and cleared the firefox cache everything seems to work.

---

