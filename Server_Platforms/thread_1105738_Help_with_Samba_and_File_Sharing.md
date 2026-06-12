---
title: "Help with Samba and File Sharing"
date: 2009-03-25
forum: Server Platforms
---

### Post by Noah0504 on 2009-03-25
Okay, I just gutted my server and threw in a new motherboard, some more RAM and a 1TB HDD.  Essentially, all I'm going to use the server for is a simple web server, a BitTorrent seedbox and hopefully a file server.  I think I need to use Samba, but it's sure making me frustrated.

Here are the details.  I have a Mac, my father and mother run Windows XP.  I would like to set up Samba to give us all our own directory for storing files on the server.  I also have a Netgear Digital Entertainer that can read network shares, so I would like to have a separate share for it.

I've tried messing around with creating users on the system and in Samba, but I seem to have problems logging into the share from a Windows machine.  I'm not sure if I did anything wrong or not.  Is there anything wrong with just have public shares on a closed network?  How would I go about either one of these routes?

I've searched around for a few days, but I just get a mix of information and not really any good solid explanations.

Any help would be welcomed.

---

### Post by bryanl on 2009-03-25
You might check out [FreeNAS](http://www.freenas.org/). Also check out the [small net builder](http://www.smallnetbuilder.com/) website

Ubuntu seems headed towards [eBox](http://ebox-platform.com/) for small servers but that might be overkill for what you want.

There are other pre-built NAS type servers and they are often much easier to set up and get going for common file sharing needs than trying to build everything from scratch and coordinate the various services needed.

---

