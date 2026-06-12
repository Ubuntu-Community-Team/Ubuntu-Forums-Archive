---
title: "Setting up a home server"
date: 2009-08-19
forum: Server Platforms
---

### Post by Kugerfang on 2009-08-19
Hello.

Like any other (un)wise computer user, I often face a situation familiar to all of us:

No backups.

I thought about setting up a home server because all my USB drives spread viruses like AIDs, I can't find any of my backup disks, and all of my Windows PCs are infected like a transvestite prostitute. Since I have a spare PC lying around, why can't I make my own home server to back up my files?

Here are the requirements for my home server:

1. Accessible from both Windows and Ubuntu PCs from my network.

2. Both Win and Ubuntu can upload/download files from the server.

3. Can stream music/movies from the server.

4. Must run on Linux. (I've been tempted to use Windows Home Server because of its simplicity, but it's made by M$ and it isn't free.)

So, can anyone help me? Any and all help is appreciated. :)

---

### Post by Maheriano on 2009-08-19
Just install Ubuntu Server Edition and then use one of the free backup utilities to backup your data on the server. It'll do it on a schedule you set up and automatically synchronize everything, you don't have to do anything.
But I think you'd be better off just putting a second hard drive into the computer you have, it's overkill to set up a whole new computer just to backup files onto a separate disk.

---

### Post by Kugerfang on 2009-08-19
You mean all I have to do is to install Ubuntu Server Edition, transfer my files, and then connect to my network? Really?

As for the "second hard drive" option, I can't. My family has 5 PCs and we need a place to store and retrieve our data.

---

### Post by hessiess on 2009-08-19
Use samba and mount it as a network drive in Windows.

---

### Post by Diabolis on 2009-08-19
[http://lmgtfy.com/?q=how+to+set+up+a+home+server+with+ubuntu](http://lmgtfy.com/?q=how+to+set+up+a+home+server+with+ubuntu)
:)

---

### Post by TwiceOver on 2009-08-19
1.  Samba will handle your network shares
2.  Same as 1
3.  Same as 1
4.  Ubuntu Server 9.04

For backups, look up BackupPC.  This will poll your systems throughout the day and create backups when necessary.

---

### Post by randyks on 2009-08-19
Not Linux, but FreeBSD. It will do all you want plus a little more without a huge configuration issue. It maybe just what you need.

[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by Jerry.S on 2009-08-19
Do you Have an extra box laying around? If you do take a look at FreeNAS you could install it to a usb stick. I have it set up on a usb stick and I use the hdd in the box to store files, Plus if you need more storage all you need to do is to install a second HDD by any methoed. I have installed a raid card and hook up my SATA HDD's. Also if you dont have the room for that you can hook them up via USB, eSATA, or just use the chanel for your cd/dvd player after you configure freeNAS.

---

### Post by jocampo on 2009-08-19
> **Kugerfang said:**
> Hello.

Like any other (un)wise computer user, I often face a situation familiar to all of us:

No backups.

I thought about setting up a home server because all my USB drives spread viruses like AIDs, I can't find any of my backup disks, and all of my Windows PCs are infected like a transvestite prostitute. Since I have a spare PC lying around, why can't I make my own home server to back up my files?

Here are the requirements for my home server:

1. Accessible from both Windows and Ubuntu PCs from my network.
2. Both Win and Ubuntu can upload/download files from the server.
3. Can stream music/movies from the server.
4. Must run on Linux. (I've been tempted to use Windows Home Server because of its simplicity, but it's made by M$ and it isn't free.)

So, can anyone help me? Any and all help is appreciated. :)

Not all prostitutes are infected or with AIDS ;-) ... 

1. Samba
2. Samba
3. Samba (put your mp3s there and pull or play them from anywhere)
4. Ubuntu Server

Read and enjoy [Samba Tutorial]
[http://samba.netfirms.com/index.htm]("http://samba.netfirms.com/index.htm")

And regarding backups...go to an electronic store and get an external USB enclosure...connect a big and fast drive to it ...connect the USB enclosure to the Ubuntu Server and mount it. Finally, backup from server to external drive using any of the free Linux Backup utilities or tar and gzip.

---

