---
title: "Best OS for file sharing."
date: 2009-12-15
forum: Server Platforms
---

### Post by twin-08 on 2009-12-15
Hey guys I got an old xeon computer of ebay, and its being shiped to me now. I was going to use it as a file hosting or file sharing server.

The thing is I don't know which is the best linux platform to start with, also being a noob to linux so I would like one thats simple to use.

I've only ever used ubuntu and thats on a laptop, also it be a file sharing for mainly 2 desktops which run windows 7 and a linux laptop, which was xp till I put linux on it a while back.

Another problem is that the computer is only a 40gb hdd however its being replace by a 1tb drive later on as I don't have the cash atm so I wanna get this server up and running before I do this.

Anyways back to the question which linux would be best for this.

Thanks Twin-08. (sorry for the long post).

The server specs are 2.8ghz xeon with HT, 2gb ram and a 40gb.

---

### Post by amauk on 2009-12-15
to be honest, any

I'd suggest Ubuntu server, as you're already familiar with Ubuntu

---

### Post by spydeyrch on 2009-12-15
FreeNAS is great. It is a web based interface, you can mange drives, backups, file sharing, etc. Take a look at their website.
 
-Spydey

---

### Post by munky99999 on 2009-12-15
Practically anything but windows or mac tbh.

freenas if you simply want it to be a nas.

Ubuntu server/desktop otherwise would be fine..


If i recall correctly. Freenas will be moving to ubuntu/debian also.

---

### Post by twin-08 on 2009-12-15
Ye, but does ubuntu come in a 32bit OS?

as when I go to download it only comes in 64bit and tbh I only ever use 64
if its more 4gb ram.

---

### Post by munky99999 on 2009-12-15
> **twin-08 said:**
> Ye, but does ubuntu come in a 32bit OS?

as when I go to download it only comes in 64bit and tbh I only ever use 64
if its more 4gb ram.

Yep.

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)


ubuntu-9.10-desktop-i386.iso.torrent

That's 32bit.

---

### Post by twin-08 on 2009-12-15
> **munky99999 said:**
> Yep.

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)


ubuntu-9.10-desktop-i386.iso.torrent

That's 32bit.

Thats the desktop version I need a server edition which is 32bit.

---

### Post by BkkBonanza on 2009-12-15
They're all on that page. Look more closely, 6th item down in list.
Those are the torrent links which are preferred since they save Canonical money.
Further down you can find local mirrors which likely have direct downloads too.

---

### Post by twin-08 on 2009-12-15
Oh thanks dude, I never saw that

Thanks for the help guys, and also will windows see the linux server on the network so I can access it?

---

### Post by benjaminsuman on 2009-12-15
the download link for server from the ubuntu.com website defaults to 64bit but if you click the Alternative download options link you will see choices for 32bit server as well as the current LTS

---

### Post by BkkBonanza on 2009-12-15
To have windows access your server you will want to install "samba". 

sudo apt-get install samba  

You can probably choose this during OS install as well.
And then look into a tutorial on configuring that according to your needs.

---

### Post by twin-08 on 2009-12-15
All right thanks for the help guys.

---

### Post by Vegan on 2009-12-15
> **twin-08 said:**
> Oh thanks dude, I never saw that

Thanks for the help guys, and also will windows see the linux server on the network so I can access it?

Use SAMBA as it can make Linux look like an NT server for Windows clients.

---

