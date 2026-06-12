---
title: "Syncing home directories."
date: 2009-09-09
forum: Server Platforms
---

### Post by cmwslw on 2009-09-09
I have two computers that I use regularly. I'd like to be able to use a common home folder with each one, so I don't have to copy over files and settings all the time. I'm aware of Ubuntu One, but it seems like it is only for documents and pictures. Is there some sort of server that is capable of syncing an entire home directory? I already have a home server set up so I could use that. I have an idea how to set something like this up myself (using rsync), but I was wondering if there are any open source projects that can do this already.

I'd rather not make my home directory remote, as that would slow things down considerably. What I need is something that can sync the home directory every so often. Syncing it on login and logout would be best, but I could configure that later.

Edit: I found something called [Unison]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html"), but it seems like that only handles syncs directly from computer to computer, no server as the middleman.

---

### Post by joshuahoover on 2009-09-09
> **cmwslw said:**
> I have two computers that I use regularly. I'd like to be able to use a common home folder with each one, so I don't have to copy over files and settings all the time. I'm aware of Ubuntu One, but it seems like it is only for documents and pictures. Is there some sort of server that is capable of syncing an entire home directory? I already have a home server set up so I could use that. I have an idea how to set something like this up myself (using rsync), but I was wondering if there are any open source projects that can do this already.

I'd rather not make my home directory remote, as that would slow things down considerably. What I need is something that can sync the home directory every so often. Syncing it on login and logout would be best, but I could configure that later.


We currently don't support syncing files outside of the ~/Ubuntu One folder but we are planning on adding this feature in the future.

Joshua Hoover

---

### Post by cmwslw on 2009-09-10
> **joshuahoover said:**
> We currently don't support syncing files outside of the ~/Ubuntu One folder but we are planning on adding this feature in the future.

Joshua Hoover

I'm not asking if Ubuntu One can do this. My home folder is way to big for that. I was thinking about something I could host on my own server that accomplishes this.

---

### Post by cariboo on 2009-09-11
this question really has nothing to do with Ubuntu One. Moved to Server platforms.

---

### Post by tom-ubuntu on 2009-09-22
Did you find a solution on how to sync your home directory between two computer?

I am looking into the same, like to sync my home folder between a workstation and laptop.

Thanks

---

### Post by hessiess on 2009-09-22
Unison.

---

### Post by dankdave on 2009-09-22
has anyone tried using amanda?

[http://amanda.zmanda.com/](http://amanda.zmanda.com/)

i'm also looking for some nice software to use with syncing the documents i regularly work on.  also serves as a nice backup if you have multiple copies!

---

### Post by openfly on 2009-09-23
Just use rsync... fast easy works.  It's been the #1 most used sync option in unix for like 20 years.

---

### Post by 3L33T on 2009-09-23
> **openfly said:**
> Just use rsync... fast easy works.  It's been the #1 most used sync option in unix for like 20 years.

Another vote for rsync.  You can also use "grsync".

Here's how to do it.

[From Ubuntu community]("https://help.ubuntu.com/community/rsync")

and here:

[From Marcel gagne (Linux Journal)]("http://myhowtosandprojects.blogspot.com/2009/06/freeboo-open-architecture-for-network.html")

I have been successfully replicating a 2GB and 4GB folder with hundreds of files from Ubuntu/CentOS/SuSE and vice versa without a hitch.

---

