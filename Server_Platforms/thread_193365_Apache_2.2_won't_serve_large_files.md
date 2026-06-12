---
title: "Apache 2.2 won't serve large files"
date: 2006-06-09
forum: Server Platforms
---

### Post by Churnd on 2006-06-09
I'm running Dapper Server 6.06 under a basic install so I could set it up with only what I wanted.  I decided to manually compile and install Apache 2.2 because I sometimes need to share dvd .iso's with family/friends.  The server is up and running fine.

My problem is, I can't get it to serve large files, which is supposed to be something 2.2 supports (main reason I chose to compile it myself vs. apt-get install apache2).  However, when I go to my site via browser and click on the download link for the .iso, it only downloads a 720 byte .iso file.  I can't figure out why it's doing this, so I hoped maybe you guys could shed some light.  My httpd.conf file is default; I haven't changed anything.  I know it's not my computer I'm trying to download to, as I've checked it on several with the same result on each.

Thanks in advance.

---

### Post by LordHunter317 on 2006-06-10
[QUOTE=Churnd]My problem is, I can't get it to serve large files, which is supposed to be something 2.2 supports (main reason I chose to compile it myself vs. apt-get install apache2).[/quote]The packaged Ubuntu apache2 should come with large file support.

It probalby doesn't work because you failed to compile it with large-file support. AFAIK it's still an option, even in apache 2.2.

---

### Post by Churnd on 2006-06-10
[QUOTE=LordHunter317]The packaged Ubuntu apache2 should come with large file support.

It probalby doesn't work because you failed to compile it with large-file support. AFAIK it's still an option, even in apache 2.2.[/QUOTE]

I actually tracked down the problem to being the browser I was using, Internet Explorer.  Once I tried it with FireFox, it worked fine.  :confused: 

Which leads the next question, why would it work ok in FireFox and not Internet Explorer?  IE bashing allowed, but please offer a valid reason too.  :)  I know it's not IE's cache, because I've cleared it several times in trying to download and it didn't help.

---

