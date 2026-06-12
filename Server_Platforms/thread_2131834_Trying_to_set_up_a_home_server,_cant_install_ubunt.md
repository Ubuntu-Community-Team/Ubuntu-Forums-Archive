---
title: "Trying to set up a home server, cant install ubuntu server"
date: 2013-04-02
forum: Server Platforms
---

### Post by rusg on 2013-04-02
Hello, I am tying to set up a home server and Cant get Ubuntu server to boot from either a CD nor a flash drive (I keep getting the message "Disk Boot failure, insert system disk and press enter). I have tried both 64bit and 32bit version. Its not a problem from my optical drive because I inserted a cd with an older version of Ubuntu desktop and it worked fine. I have tried everything I could think of but cant figure it out. Going crazy... Any suggestions or help would be very appreciated. Thanks!

---

### Post by papibe on 2013-04-02
Hi rusg. Welcome to the forums ):P

What server version are you trying to install?
Could you describe a little bit your computer's hardware (processor, RAM, HD space)?

I would make sure the download is not corrupted by checking the md5sum (check [here]("http://releases.ubuntu.com/")).

BTW, last time I tried, installing a server using USB stick does not work (because of a bug).

Regards.

---

### Post by darkod on 2013-04-03
If you are sure you are booting from the cd-rom, then the cd is not burned correctly. Did you try it on another machine?

---

### Post by rusg on 2013-04-03
thanks papibe!

The server version is 12.04.2, the one thats one the download page.

I am trying to install it on my old desktop computer which has:
-AMD Athlon 64 3700+ 2.2GHz processer
-2Gb of Ram
-300w powersupply
-1 250Gb hard drive (which has windows XP on it currently) This is the harddrive that I am trying to install ubuntu to.
-1 2Tb hard drive (This one is new and havent hooked it up yet)

My Idea was to have it be a file/media/printer server, be able to back up my devices (phone, computers...) and maybe eventually host a webpage for my fiancee's blog. I played around with Ubuntu in college, but havent touched it since so I pretty much don't know anything... i have been reading this forum and blogs to learn about running a server, so I figured it would be difficult, but I cant even get it loaded haha...

[COLOR=#000000]darkod - Ill double check that the cd is burend properly.[/COLOR]

---

### Post by oldschoolgentoo on 2013-04-05
i have run into this exact situation.  I have two drives installed in the server  one cd, one cd/dvd burner.  For me to install the server i used a **usb external cd drive** which it found quit easily.  it was the workaround i used for the past 3 server installs i have done.

hope it helps you get installed.

once server installed  it will find your internal drives on boot up.

on side note  Drako is correct  make sure you burn  if its ISO to DVD or CD is done right makes a big difference.

---

