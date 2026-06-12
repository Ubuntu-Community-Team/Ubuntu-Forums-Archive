---
title: "154: /usr/local/twonkymedia/twonkymedia: not found"
date: 2011-01-29
forum: Server Platforms
---

### Post by gadikas on 2011-01-29
Hi 

Im trying to install TwonkyMediaServer from this guide
[http://www.twonkyforum.com/viewtopic.php?f=6&t=7870](http://www.twonkyforum.com/viewtopic.php?f=6&t=7870)

I get this message:
```
sudo /etc/init.d/twonkyserver start
Starting /usr/local/twonkymedia/twonkymedia ... /etc/init.d/twonkyserver: 154: /usr/local/twonkymedia/twonkymedia: not found
```funny...

```
ls -l /usr/local/twonkymedia/
totalt 4672
drwxr-xr-x 2  16733   5513    4096 2010-10-22 20:32 cgi-bin
-rw-r--r-- 1  16733   5513     193 2010-10-22 13:09 initial_keystore.dat
-rw-r--r-- 1 root   root      5209 2011-01-25 03:41 install.log
-rw-r--r-- 1  16733   5513    2768 2010-10-22 13:09 Linux-HowTo.txt
drwxr-xr-x 2  16733   5513    4096 2010-10-22 20:32 plugins
-rw-r--r-- 1  16733   5513     421 2010-10-22 13:09 radio.m3u
drwxr-xr-x 4  16733   5513    4096 2010-10-22 20:29 resources
-rw-r--r-- 1  16733   5513   45252 2010-10-22 13:09 RevisionHistory
-rwxrwxr-x 1  16733   5513    4744 2010-10-22 16:45 twonkymedia
-rwxrwxr-x 1  16733   5513 1538780 2010-10-22 16:45 twonkymediaserver
-rwxrwxr-x 1  16733   5513     127 2010-10-22 20:32 twonkymedia-server-default.ini
-rwxrwxr-x 1  16733   5513    3775 2011-01-25 03:41 twonkymedia.sh

```Any one got a suggestion whats wrong..

---

### Post by 5h4d3 on 2011-02-13
I had the same problem until i found this: > [http://blog.simpletechs.net/tag/twonky/](http://blog.simpletechs.net/tag/twonky/)

The problem was that i was running 64-bit and ... anyways:

```
sudo apt-get install ia32-libs
```

did the job for me.

---

### Post by jcm1979 on 2011-02-14
Thanks for that tip, it worked for me as well.

---

