---
title: "Network storage at home"
date: 2010-04-15
forum: Server Platforms
---

### Post by Nxion on 2010-04-15
So I was looking into setting up a NAS at home so I can quickly access my data from all my machines in the house. I really haven't had much use for one until recently. I am also in need of updating my wireless at home. I have a few devices that are N so I was looking into a N router. [THis is the router]("http://www.dlink.com/products/?pid=695") I was looking at. I choose it mainly for the 2 USB ports on it as well as the ability to install a 2.5in laptop drive to turn it into a NAS.

Another option I was thinking about was setting up a NFS share off a machine that would be solely for storage. It would be a very nice learning experience for me :).

 The LAST option is just setting up FreeNAS on a machine and using that. I wanted to get the input of the forum. What should I go with?

---

### Post by pricetech on 2010-04-15
If your goal is to learn, do it all.  One thing at a time of course.  Ultimately you decide which one you want to keep based upon how well it works, or just how fun it was to make work.  Your call.

Then post a how to on the forums about your experience to help others.

---

### Post by BobVila on 2010-04-15
Depending on your clients, you may be better off with Samba than with NFS. I totally agree with pricetech, though. If you want to learn, try 'em all and run with what you like most. On a personal note, I've got two ubuntu servers at home, one set up with Samba shares and a secondary file server sharing its datastore to the samba server via nfs. 

I've heard good things about freeNAS, but I stuck with Ubuntu server because you never know when you're going to make that simple file server into a file server that's also a torrent box, or a web server, or a sql server, etc.

---

### Post by Nxion on 2010-04-15
> **pricetech said:**
> If your goal is to learn, do it all.  One thing at a time of course.  Ultimately you decide which one you want to keep based upon how well it works, or just how fun it was to make work.  Your call.

Then post a how to on the forums about your experience to help others.

Thanks for the reply. Maybe I will try it all :) I will let you know what happens :)

> **BobVila said:**
> Depending on your clients, you may be better off with Samba than with NFS. I totally agree with pricetech, though. If you want to learn, try 'em all and run with what you like most. On a personal note, I've got two ubuntu servers at home, one set up with Samba shares and a secondary file server sharing its datastore to the samba server via nfs. 

I've heard good things about freeNAS, but I stuck with Ubuntu server because you never know when you're going to make that simple file server into a file server that's also a torrent box, or a web server, or a sql server, etc.

Hi Bob! thanks for your reply as well. Its funny that you mention SAMBA. I was thinking about that when I had submitted this. I will give SAMBA a try as well.

---

