---
title: "*simply* make a Ubuntu PXE boot server"
date: 2008-12-28
forum: Server Platforms
---

### Post by inxygnuu on 2008-12-28
Hello, I just got Ubuntu Server 8.10, and I wanted to *simply* set it up as a GUI boot server. there is currently a close-by thread about a same/similar subject, but that thread may have different circumstances, and I cannot make any sense of it. So I was wondering of a simple way to make it so that I could have a client boot their computer, and it would boot from the server, login, and be able to do stuff. This is simply becuase I don't have enough hard drives, because I want to learn to network a little more, and because my sisters need a computer. I have the command-line version of Ubuntu Server, and just need it so that I can have another computer boot onto this one.

---

### Post by koenn on 2008-12-29
howto: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by inxygnuu on 2008-12-30
> **koenn said:**
> howto: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

Almost. I don't know why, but nothing happens. what are the requirements for the host and client computers?
*bump*

---

### Post by koenn on 2008-12-30
there's a more in-depth thread going on here: [http://ubuntuforums.org/showthread.php?t=1019932](http://ubuntuforums.org/showthread.php?t=1019932)

and if you'd be just a little more precise than "Nothing happens", somebody might actually be able to help you.

Or we could just step through the howto:
1- get the Intrepid Ibex iso from [http://releases.ubuntu.com/releases/8.10/](http://releases.ubuntu.com/releases/8.10/). 

is this the part where nothing happens ?

---

### Post by inxygnuu on 2008-12-30
Oh, i am sorry,:( when I said that, I meant that I want to try to setup on old PC that I have as a server for fun, and when I said "nothing happens" I meant that my client computer will not boot off of the server at the moment. It always says "operating system not found". I will try some more.

---

### Post by TestDummy! on 2008-12-30
Usually to do a PXE boot, you have to have your network card set as the device to boot off of.

---

### Post by inxygnuu on 2008-12-30
> **TestDummy! said:**
> Usually to do a PXE boot, you have to have your network card set as the device to boot off of.

I have that option enabled. No dice.:(

---

