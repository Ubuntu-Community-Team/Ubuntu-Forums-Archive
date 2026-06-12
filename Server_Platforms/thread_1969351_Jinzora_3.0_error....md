---
title: "Jinzora 3.0 error..."
date: 2012-04-29
forum: Server Platforms
---

### Post by adduds on 2012-04-29
Going through the steps of setting up the server i get to step 7 where I'm to import my media files, server is on 11.10


> 
Importing Media
Please wait while we import the media for you.

Importing Media From: /media
Processing files: 100 (1% - 0:56)   . . . . 
PHP does not have iconv() support - cannot convert from to UTF-8

I've looked at this page:

[http://www.kplaylist.net/forum/viewtopic.php?f=4&t=2293](http://www.kplaylist.net/forum/viewtopic.php?f=4&t=2293)

aswell as this:

[http://www.getid3.org/phpBB3/viewtopic.php?f=3&t=201](http://www.getid3.org/phpBB3/viewtopic.php?f=3&t=201)

not sure where to go with these links and information

If anyone can help it would be appreciated

---

### Post by nichos79 on 2013-02-20
Ok I know I'm responding to an OLD thread here, but I just downloaded jinzora and I had the same issue. Here's what I did:
edit your jinzora/services/services/tagdata/getid3/getid3.lib.php file
Search for this line:
> die('PHP does not have iconv() support - cannot convert from '.$in_charset.' to '.$out_charset);and comment it out by adding 2 slashes in front of it, so you'll have:
> //die('PHP does not have iconv() support - cannot convert from '.$in_charset.' to '.$out_charset);You'll have to start the whole install over again. You can do that by removing jinzora/temp/install.lock, blow away the MySQL database and point your browser back to the install page.

Now the reason behind it looks like it might be caused by a bad mp3 tag, but with a huge library good luck finding it.

Have fun!

---

