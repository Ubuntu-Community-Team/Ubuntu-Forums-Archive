---
title: "Migrating to Server edition?"
date: 2008-12-20
forum: Server Platforms
---

### Post by xelxel on 2008-12-20
I'm currently running the Desktop Edition of Ubuntu 8.10, and i have 4GB Ram. I have however heard that the 32bit Server Edition is capable of detecting all 4GB RAM and am considering to switch over to it. I do however have a few questions.

1,
If i chose to migrate to the server edition, after installation will there be a graphical login and GNOME desktop as in desktop edition or does server edition work from commandline? 

2. 
Assuming there will be a GNOME Desktop, will i have access to the same repositories as through the desktop edition so i can download software i use such as openoffice, VLC etc or will these be inaccessible?

---

### Post by albinootje on 2008-12-20
> **xelxel said:**
> I'm currently running the Desktop Edition of Ubuntu 8.10, and i have 4GB Ram. I have however heard that the 32bit Server Edition is capable of detecting all 4GB RAM and am considering to switch over to it. I do however have a few questions.

You're writing that the 32bit Ubuntu Server installation will detect the 4 Gb of RAM.
If this is correct (Are you sure it's not the 64 bit ?), 
then it's probably just a matter of installing and testing the Linux kernel from the Ubuntu Server, which can be done by :

```

sudo apt-get install linux-image-server

```

---

### Post by xelxel on 2008-12-20
that's how i undersetood it. I'm really not computer smart but i believe it had something to do with PAE or PEA?

---

### Post by albinootje on 2008-12-20
> **xelxel said:**
> that's how i undersetood it. I'm really not computer smart but i believe it had something to do with PAE or PEA?

Okay, yes, PAE.

[http://www.geolaw.com/blog/Enable-PAE-in-Hardy-kernel-to-support-4GB-memory.html](http://www.geolaw.com/blog/Enable-PAE-in-Hardy-kernel-to-support-4GB-memory.html)
[http://brainstorm.ubuntu.com/idea/10892/](http://brainstorm.ubuntu.com/idea/10892/)

Fastest and easiest option to try it, is to install the linux-image-server as mentioned in my previous posting.

---

### Post by cdtech on 2008-12-20
The server edition is command line only, although you could install gnome desktop. With that being said why not just use your desktop setup for a server and install whatever packages you need? The reason for the server edition with no GUI is the security. You can always ssh into the server via command line from your desktop or even run Xforwarding for applications on the server.

---

### Post by albinootje on 2008-12-20
> **cdtech said:**
> The reason for the server edition with no GUI is the security.

I think that Ubuntu came with a server edition for various reasons.

Amongst others i can think of the following reasons :
1) It's a smaller download (iso) for people who only want to install on a server.
2) It's focused on being installed on a server by using a kernel with different compiled in features than the desktop version (generic).
3) It's much faster to install than the desktop version, so people can also use it as a base to have a custom desktop, without having to remove a lot what they don't need (Think about fluxbox or icewm users).

Before i ever heard of, or saw the Ubuntu alternate iso images, i have used the Ubuntu server cdrom to perform installations where there was a problem with X (before that the desktop install cdrom had the "safe graphics" option). After installing it was a matter of running : 
sudo apt-get install ubuntu-desktop, and replacing the server kernel with the generic kernel, and the end result would be as if one had installed from the desktop installation cdrom (pretty cool that it's possible!). :)


Debian uses a different approach. With Debian Etch you can choose with tasksel wether you want a desktop or not, laptop software or not, webserver software or not. Except the kernel will be the same in Debian, whether you install on a server or not.

---

### Post by theozzlives on 2008-12-20
I ran Ubuntu Server with the desktop for awhile. I started thinking, "I can run my small web/print server from a desktop install". Anyhow, I went back (of course I don't have 4 GB of RAM to deal with). I use my router for DHCP, so I don't need the server software.

---

### Post by xelxel on 2008-12-20
Aah i see!

Thanks for your input everyone :)
The reason for me asking about this in the first place simply was that i have 4GB RAM and i have found that 64bit ubuntu just isn't pallatable for my laptop. Since Ubuntu server edition apparently can find all 4GB without resorting to the 64bit version, it seemed like a good idea :)

I made a fresh install of ubuntu desktop edition, and ran the above line from commandline and now i have all 4GB ram :)

Thanks! :D

---

### Post by albinootje on 2008-12-20
> **xelxel said:**
> 
I made a fresh install of ubuntu desktop edition, and ran the above line from commandline and now i have all 4GB ram :)

cool! :)

---

