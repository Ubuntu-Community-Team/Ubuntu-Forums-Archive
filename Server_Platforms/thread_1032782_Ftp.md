---
title: "Ftp"
date: 2009-01-06
forum: Server Platforms
---

### Post by jairom70 on 2009-01-06
i installaded Ubuntu Server Edition on my computer. I was wondering is there  aguide. for beginners. on the Command Line. for example I have no idead how to download things. 

im running  a game server on Ubuntu server. and i want to download Maps from a website. how would i got about doing this?

---

### Post by albinootje on 2009-01-06
> **jairom70 said:**
> i installaded Ubuntu Server Edition on my computer. I was wondering is there  aguide. for beginners. on the Command Line. for example I have no idead how to download things. 

im running  a game server on Ubuntu server. and i want to download Maps from a website. how would i got about doing this?

You can install ncftp and lynx :
```

sudo apt-get update
sudo apt-get install ncftp lynx

```
Lynx is a txt-based web-browser, downloading files from a webpage in Lynx can be done by using ctl-d.
There's also links and w3m as text-based web-browsers.

Ncftp is a nice txt-based ftp client.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://tips.webdesign10.com/lynx-browser](http://tips.webdesign10.com/lynx-browser)

---

### Post by jairom70 on 2009-01-06
so when using Lynx. would then enter like [www.whatever.com](www.whatever.com)

and view the page. in txt?

---

### Post by albinootje on 2009-01-06
> **jairom70 said:**
> so when using Lynx. would then enter like [www.whatever.com](www.whatever.com)

and view the page. in txt?

In text mode, yes. Same for links and w3m.

You probably have w3m installed already, but I like plain old lynx better.
If you find problems with frames or tables in webpages, then choose links.

And if you copy and paste all the *exact* download links you want, then you can use wget (which should be installed by default).
For example :
```

wget -c [http://www.rxn.com/~uffda/archive/uucp/linus3.gif](http://www.rxn.com/~uffda/archive/uucp/linus3.gif)

```

---

### Post by jairom70 on 2009-01-06
kk i get it :D 

for wget tho i would need to know the *exact* links tho. and i could use wget without installin lynx is that right?

but with lynx i could txt browse and find links i dont know of right?

---

### Post by albinootje on 2009-01-06
> **jairom70 said:**
> kk i get it :D 

for wget tho i would need to know the *exact* links tho. and i could use wget without installin lynx is that right?

but with lynx i could txt browse and find links i dont know of right?
Hmm, yes and no.
You can use lynx but I never saw a way in lynx to copy and paste a link.
Maybe it's best to try links,lynx and w3m.

Try e.g. :
```

w3m google.com

```
Navigation will be weird the first time ;-)
Use the "q" character to quit.

But perhaps it makes more sense for you to copy all the maps on some usb stick, and then learn how to mount the usb stick, on the command line, on your server.

---

### Post by jairom70 on 2009-01-06
well. the maps are all on the Vista OS. i can just mount that HD and access the files can i?

---

### Post by albinootje on 2009-01-06
> **jairom70 said:**
> well. the maps are all on the Vista OS. i can just mount that HD and access the files can i?

Can you clarify the situation a bit ?

Is MS-Vista on another machine, or are you dual-booting on one machine ?

If the latter, then it's a matter of manually mounting the NTFS partition that MS-Vista is on.

If it's on another machine, then using a FAT formatted usb stick would be fine to transfer the files.

You can also install a ssh-server on the Ubuntu box, and then use winscp from [http://winscp.sf.net](http://winscp.sf.net) as a ssh-client on Vista to copy things.
(Make sure you use good passwords for your user accounts when installing the ssh server)

---

### Post by jairom70 on 2009-01-06
yes its on dual boot. Vista is on a 2nd HD on the same machine

---

### Post by albinootje on 2009-01-06
> **jairom70 said:**
> yes its on dual boot. Vista is on a 2nd HD on the same machine

Okay, please post the output of the following :
```

sudo fdisk -l

```
Thanks.

---

### Post by jairom70 on 2009-01-06
ok hopefully im gettin this right in on the server now. using w3m
i did fdisk and i get this

Disk /dev/sda 320gb
Device Boot
        /dev/sda1
	/dev/sda2
	/dev/sda3


Disk /dev/sbd 150gb
Device Boot
	/dev/sdb1
	/dev/sdb2

---

### Post by Clawthedruid on 2009-01-06
How do you host php on ubuntu?

---

### Post by albinootje on 2009-01-07
> **jairom70 said:**
> ok hopefully im gettin this right in on the server now. using w3m
i did fdisk and i get this

Disk /dev/sda 320gb
Device Boot
        /dev/sda1
	/dev/sda2
	/dev/sda3


Disk /dev/sbd 150gb
Device Boot
	/dev/sdb1
	/dev/sdb2
This is not enough information. 
You should have used the full output of "sudo fdisk -l".

Assuming that /dev/sda is the disk with Vista on it, try :
```

sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
sudo mkdir /media/sda3
sudo mount -t ntfs-3g /dev/sda3 /media/sda3
ls /media/sda1
ls /media/sda2
ls /media/sda3

```

---

### Post by albinootje on 2009-01-07
> **Clawthedruid said:**
> How do you host php on ubuntu?

See here : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Please start a new thread when you have a new question, which is unrelated to the current thread.

---

