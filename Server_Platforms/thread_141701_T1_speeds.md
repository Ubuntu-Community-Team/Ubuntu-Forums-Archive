---
title: "T1 speeds"
date: 2006-03-08
forum: Server Platforms
---

### Post by haxx0r07 on 2006-03-08
OK I have a vsftpd server running on a T1 line, and the max speed I can get uploading to it or downloading from it is only 40KBps. I know a T1 line is not as fast down as a normally cable connection, but shouldn't it be faster then 40KBps? :confused: :confused:

:edit: i had it in Kbps when it should have been KBps

---

### Post by Glut on 2006-03-08
t1 is rated at 1.5Mbps. 40 KBps = 320 kbps = .3Mbps 
So yes, it is slow for a T1.

---

### Post by haxx0r07 on 2006-03-09
Yes I know that I was just wounder if I might have done something on my server to cause it.
I'm running shorewall for my firewall.

---

### Post by dk_pa on 2006-03-10
Why dont you just test it with a regular PC by uploading a file somewhere.

---

### Post by dermotti on 2006-03-10
Maybe the ftp software has throttling setup?

---

### Post by haxx0r07 on 2006-03-10
thats what I was thinking. I'm using vsftpd i haven't seen anything in the configs that would point to that but i'm still really new to all of this.

---

### Post by jinacio on 2006-03-10
have you tried using http for file transfer and record the speed? also, try using somewhat large (10MB+) files for this purpose, as usually download speed measurements from browsers aren't that accurate.

---

### Post by haxx0r07 on 2006-03-11
ok ill try that

---

### Post by haxx0r07 on 2006-03-11
OK I have tried downloading a 26.2MB file through my apache2 web site, my speeds started at about 250KBps and quickly dropped to 60KBps. So does that mean it's something with the T1 line?

---

### Post by jinacio on 2006-03-11
[QUOTE=haxx0r07]OK I have tried downloading a 26.2MB file through my apache2 web site, my speeds started at about 250KBps and quickly dropped to 60KBps. So does that mean it's something with the T1 line?[/QUOTE]

I would say it looks that way...

---

