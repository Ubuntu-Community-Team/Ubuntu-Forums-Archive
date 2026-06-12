---
title: "Which ubuntu do I need"
date: 2007-12-01
forum: Server Platforms
---

### Post by wantserversoftware on 2007-12-01
A freind @ work told me I should download Xubuntu for an old PC that I want convert into a home server. My ?'s are; does Xubuntu come with the server software or should I just download ubuntu server, the PC I am converting has windows 98se should I delet it or leave it after I install the new software, I will be conecting an Xp and a VistaPC to the server will it be compatible? My end result (hopefully) is going to be a hole house multimedia/internet/printer server. Sarry cant spell

---

### Post by mouseboyx on 2007-12-01
Ubuntu server would be the best bet, just do a clean install and wipe the hard drive clean when you install it, and yes it is compatible with windows networks, it comes with samba.

---

### Post by prodezigner on 2007-12-01
I agree with mouseboyx, use server ed. setup ssh and samba, and whatever other servers you want.

If a GUI is a must have after you install server ed. you can sudo apt-get install <whatever desktop you want Xubuntu, Kubuntu, Ubuntu>...

sudo apt-get install xubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo apt-get install kubuntu-desktop

There ya go.

---

### Post by HermanAB on 2007-12-01
For a server with a screen & keyboard attached, Xubuntu is a good choice.  The Xfcewindow manager is screaming fast and doesn't waste resources.

Cheers,

Herman

---

### Post by popeye6984 on 2007-12-13
Hi there! Just a quick question:
How do I install a xubuntu desktop over a server from the CD-ROM ? Thanks!

---

### Post by Archmage on 2007-12-13
> **popeye6984 said:**
> Hi there! Just a quick question:
How do I install a xubuntu desktop over a server from the CD-ROM ? Thanks!

sudo apt-get install xubuntu-desktop

---

### Post by popeye6984 on 2007-12-13
NOPE! Can't find xubuntu-desktop .... what's wrong???

---

