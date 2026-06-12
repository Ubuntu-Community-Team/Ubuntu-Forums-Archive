---
title: "Argh.. debian hates me!"
date: 2010-04-19
forum: The Cafe
---

### Post by kaldor on 2010-04-19
Many times I have tried to download Debian, but the connection I get to the site is horribly slow. It takes at least 10 minutes to view the FTP server, then when I click on my arch.. another 10+ minutes. When I finally get to download it, it downloads amazingly slow and would take days to finish. 

Anybody else have this problem? Always has happened on all my computers.

---

### Post by NightwishFan on 2010-04-19
Try using wget or axel from the command line. Whats a mirror near you?

---

### Post by kaldor on 2010-04-19
[http://www.debian.org/CD/torrent-cd/](http://www.debian.org/CD/torrent-cd/)

^Try clicking on i386, it's been saying "Loading..." for 5 minutes so far.

How do I check/change a mirror? And how do I use wget for this, I don't know what directory/file I am looking for =p

---

### Post by swoll1980 on 2010-04-19
Use bit torrent. It's always faster, and you can pause, and resume your download as well. I usually get a 1.5 Mb transfer rate on distro downloads,(10 minutes) compared to 6 or 700 kb/sec using the mirrors(25 minutes).

---

### Post by kaldor on 2010-04-19
> **swoll1980 said:**
> Use bit torrent. It's always faster, and you can pause, and resume your download as well. I usually get a 1.5 Mb transfer rate on distro downloads,(10 minutes) compared to 6 or 700 kb/sec using the mirrors(25 minutes).

That's what I am trying to do. It's taking ages to download the .torrent that's only like 25kb.

---

### Post by NovaAesa on 2010-04-19
How odd, it took me like 0.2 seconds to download the .torrent file. Hmmm.

---

### Post by kaldor on 2010-04-19
It's still saying "Loading" as we speak!

---

### Post by NightwishFan on 2010-04-19
I got into it just fine. Odd!

Here is Debian torrent file for you.

---

### Post by kaldor on 2010-04-19
awesome, ty :)

---

### Post by NightwishFan on 2010-04-19
I hope it works for you, good luck :)

---

### Post by kaldor on 2010-04-19
> **nightwishfan said:**
> i hope it works for you, good luck :)

90% :)

---

### Post by cariboo on 2010-04-19
I downloaded the 32-bit ppc netinstall iso from the U of Calgary this morning, it only took a couple of minutes. I installed it on my [B&W G3]("http://en.wikipedia.org/wiki/Power_Macintosh_G3_(Blue_&_White)") and it is happily playing mp3's streamed from my server.

---

### Post by kaldor on 2010-04-19
I'm trying out Stable because I need a stable OS for a work PC I'll have for the next year from school. They tried to make me use Windows XP with spy software in it to monitor me, but I quickly removed Windows and put Fedora on it. 

I hope it won't cause trouble, cause this comp they sent me was a beast; I wasn't going to let it go to waste due to being unable to even control my own documents Everything was locked up, had to store everything on Desktop and the PC took 10 minutes to boot up. On top of that, I had to spend about 5 minutes every day re-downloading the online classroom application because it was "unsafe" to have it installed. Been using Fedora on it since November, but due to a recent problem I need better stability. All files are safe though :)

---

### Post by themarker0 on 2010-04-19
Debian hates everyone, don't feel speeeshal :P /joking of course.

Just torrent it, the only decent way i've found.

---

### Post by kaldor on 2010-04-19
Just my luck! I used my last CD (no stores in the area to buy them) on Debian and it won't get past the keymap select..

"Problem reading data from CD-Rom"
"Failed to copy file from CD-ROM, Retry?"

[http://ubuntuforums.org/showthread.php?t=132065](http://ubuntuforums.org/showthread.php?t=132065)

Same problem as that

---

### Post by NightwishFan on 2010-04-19
You need to burn at a slower speed and verify data, this is a must.

---

### Post by kaldor on 2010-04-19
> **NightwishFan said:**
> You need to burn at a slower speed and verify data, this is a must.

Is 4x not slow enough? :(

I did verify it; not a clue what went wrong. Brasero must like making coasters.

---

### Post by NightwishFan on 2010-04-20
I see, not sure what happened then. Next time you get a try use the command version as an option as well.
```
wodim speed=1 /path/to/debian.iso
```

---

### Post by powder on 2010-04-20
I found this command on the sidux wiki and it has worked very well for me.

wodim dev=/dev/scd0 driveropts=burnfree,noforcespeed fs=14M speed=8 -dao -eject -overburn -v something.iso

---

