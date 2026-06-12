---
title: "backup to DVD"
date: 2010-12-25
forum: Server Platforms
---

### Post by Vegan on 2010-12-25
OK given a DVD burner on the Linux box, and of course a blank disk in the drive. what tool is available to send file to the burner and then eject the disk?

I would like to do this on say a monthly schedule?

---

### Post by lncoll on 2010-12-25
I use wodim, can't remenber exactly what parameters but some like:
```
wodim -eject -checkdrive dev=/dev/sr0 /home/share/oficina 
```
As allways we have man pages ;)

Of course this is added in a line at /etc/crontab
```
30 02 0 root wodim.....
``` 

Hope this helps

---

### Post by Vegan on 2010-12-28
I already have a script running as a cron task under /etc/cron.daily

So I noticed in webmin there is a tool called cdrecord but I am not sure of that tool is right for me?

---

### Post by HermanAB on 2010-12-28
Yup, you got to script mkisofs and cdrecord.  Some googling and man page reading will get you going.  Note that it may be a good idea to experiment using a rewriteable CD.

---

### Post by Vegan on 2010-12-31
I have a couple of CD-RW disks in the shop, used them to convert DRM music to MP3 when some internet music stores went **** up. Not sure if they are still good, but they should be OK.

---

### Post by rubylaser on 2011-01-01
This page has a good script in the second entry. 
[http://www.brighthub.com/computing/linux/articles/50837.aspx]("http://www.brighthub.com/computing/linux/articles/50837.aspx")
 You'd just need to add a call to eject at the end of the script to have it eject the disk.

---

