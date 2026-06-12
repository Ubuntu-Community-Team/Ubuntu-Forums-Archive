---
title: "network with GUI"
date: 2014-02-25
forum: Server Platforms
---

### Post by robin14 on 2014-02-25
I coming back to Linux after a long-ish absence - but its proving a bit of a frustrating experience. Hope someone can point me in the right direction
What I would like to have is a Linux based server system on an HP micro server. I allready have one that runs MS home server 2011. Once installed it works reasonably well but does have some limitations. 
I would really like to have a Linux based system on the 2nd server but so far finding one that is reasonably easy to install and configure has been elusive. 
Ubuntu desktop looks great. However Unbuntu server install is totally command line based. trying to install one, and get it to work with the other so far has proved impossible. |They just wipe each other out instead  of co-existing
So my question is,  is it possible to have the GUI  desktop version sitting on top of the server version?  (or vv)  
I have tried version 12,  32 and 64 bit  and  version 13 . Unfortunately 13 server only comes in 64 bit but desktop in 32 and 64. The server version refuses to install at all..seems to be a problem in the install process and just hangs at the 2nd language select page.

In another post where someone had a similar question they were directed to the Zentyal server site. I have tried that and it looks a good system except when it comes to setting up shares. No way to view folders on disks and select them for sharing. Couldn't get any sensible help from the user forum.
Ubuntu looks like it is a friendly, helpful forum and looks like it extends a warm welcome to newcomers instead of treating them as idiots which some forums do.

Hope someone can point me in the right direction and prevent me from giving up and having to go back to a dreaded MS solution! :P

---

### Post by aromo2 on 2014-02-25
after installing the server version, did you try this?
```

sudo apt-get install ubuntu-desktop

```

---

### Post by robin14 on 2014-02-26
Thank you for quick reply -  no I didn't, but I'll give that a try right away.

---

### Post by Bucky Ball on 2014-02-26
*Thread moved to **Server Platforms**.*

You might have more luck here. ;)

You could try installing the server version and then a lightweight DE. Xfce4 or lxde could be appropriate.

```
sudo apt-get install xfce4
```

Replace 'xfce4' with lxde for the other DE.

---

### Post by robin14 on 2014-02-26
unfortunately wont work returns error : unable to locate package ubuntu-desktop
I have put the install dvd in the dvd sdrive

---

### Post by robin14 on 2014-02-26
should I be switching to a different folder first?

---

### Post by The Cog on 2014-02-26
Are you aware that the difference between the server version and the desktop version is just that the server version has no GUI? Servers don't need a GUI as they don't normally even have screens attached. With windows you pay a much higher price for a server version which has artificial limits removed. With Ubuntu the desktop version doesn't have artificial limits built in, and the server version is the cut down version with the GUI removed.

I would suggest that you install the desktop version and be happy with it. If you want to make it look more like the server, run the command
```
sudo service lightdm stop
```
which will kill the GUI.

---

### Post by robin14 on 2014-03-12
Hi there   sorry for late reply. The hardware developed a fault so had to be sent back and replaced. Now got replacement unit, so I can start trying again. I'll give your suggestion a try. 
Have been trying the Zentyal version of server - after 6 install this morning it still wont work - refuses to boot in after install or else comes up with error message saying it cant find the opeing screen (Firefox error). Giving up on that and going back to the Ubuntu installation  and following the helpful suggestions given in the different replies.
really appreciate  he friendly helpful replies I have had so far

---

### Post by lukeiamyourfather on 2014-03-12
As others have said, you can just use the desktop version of Ubuntu if you want and then install the server packages you want to use (like Samba, Apache, whatever). The underlying software is the same between the two.

What exactly do you want to do with the server? If you want a file server with a few bells and whistles you might check out projects like NAS4Free (FreeBSD based, web interface for management, ZFS) which are easier to setup and manage compared to a full distribution.

---

