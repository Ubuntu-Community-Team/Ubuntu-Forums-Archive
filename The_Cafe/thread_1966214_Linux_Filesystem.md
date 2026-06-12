---
title: "Linux Filesystem"
date: 2012-04-26
forum: The Cafe
---

### Post by TheMTtakeover on 2012-04-26
What do you think about this?
 
[http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/](http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/)

---

### Post by neu5eeCh on 2012-04-26
> **TheMTtakeover said:**
> What do you think about this?
 
[http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/](http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/)

There are occasional distributions which try to solve this problem (Moon OS is one and there is another recent one I can't think of), but it just doesn't seem to catch on. Inertia probably...

---

### Post by TheMTtakeover on 2012-04-26
I actually just noticed that there are distos that are attempting something of the sort. The one I found was called GoboLinux.
It's a very interesting idea, IMO.

---

### Post by TheMTtakeover on 2012-04-26
> **VTPoet said:**
> There are occasional distributions which try to solve this problem (Moon OS is one and there is another recent one I can't think of), but it just doesn't seem to catch on. Inertia probably...
  
Hmmm, Once I get Windows reinstalled on my XPS, I think I am going to give Moon a shot on my extra inspiron. The filesystem is my only gripe with Linux.

---

### Post by wolfen69 on 2012-04-26
Maybe it should, but I'm happy with what's available. Then again, Mark Shuttleworth doesn't have me on his payroll.

---

### Post by TheMTtakeover on 2012-04-26
> **wolfen69 said:**
> Maybe it should, but I'm happy with what's available. Then again, Mark Shuttleworth doesn't have me on his payroll.
 
If other distros are trying to gain ground with this type of feature I don't think it would unrealistic to think that Ubuntu might have something similar in the future? Because they aim for that user switching from Win. An "overlay" of the filesystem could help  the average-below user and help ease the transition of new users but still retain all the benefits of the Linux filesystem.

---

### Post by Bandit on 2012-04-27
> **TheMTtakeover said:**
> What do you think about this?
 
[http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/](http://www.psychocats.net/ubuntucat/should-the-linux-filesystem-hierarchy-change/)

The LFS is easy to understand and works great. Everything is laid out where it needs to be and is easy to find after you learn why everything is where it is. If you dont know why or think its not great then you dont know enough to be messing with the file system anyways. Just my 2.5 cents.. ):P

---

### Post by cariboo on 2012-04-27
The Linux file system makes a lot of sense once you learn what it is all about. Check out this document at the [Linux Documentation Project]("http://tldp.org/")

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by scheuri on 2012-04-27
> **cariboo907 said:**
> The Linux file system makes a lot of sense once you learn what it is all about. Check out this document at the [Linux Documentation Project]("http://tldp.org/")

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

This!
Well, lets say, there are some things in it that might look ancient and maybe really ARE ancient.
So looking at it again and maybe tweak it a little...that I would accept (if someone can tell me why something was changed and has some good facts).

However, completly changing it? No, why? Just to make it look better?
The linux admin will curse at you because he has to learn yet another thing about linux which might not make any sense (if we are unlucky enough) and was done only to attract the average user and the average user might not even appreciate it as she/he is using only graphical interfaces (which can hide that all already).

I, for one, do not see any reason to change...maybe optimise, but not change.

cheers
scheuri

---

### Post by neu5eeCh on 2012-04-27
> **cariboo907 said:**
> The Linux file system makes a lot of sense once you learn what it is all about. 

Yes, anything makes sense once you get used to it, but the Linux file hierarchy is the legacy of hard drives that were too small. In other words, the result of technological limitations -- not clever or forward thinking. There were some articles on this a couple months ago, but I can't find any of them.:rolleyes:

---

### Post by szymon_g on 2012-04-27
Well- developers of Fedora 17 change that- they move everything into /usr (so: no longer /bin /sbin etc) :)
although, two-decades old idea of one big /bin (with statically linked programs in it) from Plan 9 sounds much, much better.

---

### Post by forrestcupp on 2012-04-27
The Linux filesystem is part of what makes Linux Linux. It would be crazy to try to completely change that, and it would break a lot. Like others have said, it's just a different mentality. When you learn it, it makes a lot more sense.

We don't need to completely change the filesystem; we just need to standardize it so that every distro isn't doing its own thing.

---

### Post by mehaga on 2012-04-27
One part that I think could be improved is home directory. It might be good to have two dirs instead of one - one for stuff users typically keep when they upgrade/change distro, like documents, pictures, maybe some config files etc., and another for stuff you never want to keep, like various caches...

---

### Post by CharlesA on 2012-04-27
Cache and temp files are usually stored in either /var/cache or /tmp/ not your home directory.

---

### Post by mehaga on 2012-04-27
> **CharlesA said:**
> Cache and temp files are usually stored in either /var/cache or /tmp/ not your home directory.

Many applications (e.g. Chrome and Firefox) use a single folder within home for everything, including cache.

---

### Post by Bandit on 2012-04-27
> **VTPoet said:**
> Yes, anything makes sense once you get used to it, but the Linux file hierarchy is the legacy of hard drives that were too small. In other words, the result of technological limitations -- not clever or forward thinking. There were some articles on this a couple months ago, but I can't find any of them.:rolleyes:

I guess I give you that. It *could* use some tidying up. 

/Mnt shoudl be removed and everything including /CDROM dirs should be placed under /media. Since regardless if its internal, external, removable or welded in, its all media.

/Var, /Bin, /Sbin, /Run and /Opt shoudl be placed under /usr as they are simlilar in a way..

But in the end, nothing has changed except many legacy programs are gonna give everyone hell trying to cofigure and compile them. So you will end up with a cleaner root folder, but same amount of dirs will exist and you will have headache after headache pointing your config file to all the new locations and still praying the program doesnt have something hardcoded otherwise to prevent it from compiling.

---

### Post by Colo2 on 2012-04-27
[SIZE="2"]**_[COLOR="Red"]Linux is what it is[/COLOR]_**[/SIZE]

And what it is is brilliant! Professionals know how to use it properly, and non-professionals will only be following word-to-word tutorials. 

I don't think Linux should change for the less knowledgeable Linux users :P

---

### Post by TheMTtakeover on 2012-04-27
> **Colo2 said:**
> [SIZE=2]**_[COLOR=red]Linux is what it is[/COLOR]_**[/SIZE]
 
And what it is is brilliant! Professionals know how to use it properly, and non-professionals will only be following word-to-word tutorials. 
 
I don't think Linux should change for the less knowledgeable Linux users :P
 
Well it has over the years and if it the Linux community would like to have more of a market share, so maybe there would be more programs developed for Linux, then it will have to change to accommodate users.
 
Should we have no GUI because that accommodates  users that aren't knowledgeable enough to just use the terminal? You're certainly a forward thinker.

---

### Post by Ceiber Boy on 2012-04-27
> **Colo2 said:**
> [SIZE="2"]**_[COLOR="Red"]Linux is what it is[/COLOR]_**[/SIZE]
I don't think Linux should change for the less knowledgeable Linux users :P
As a 'less knowledgeable Linux user' I agree. Linux is not compromised by commercial pressures in the same manner that the propriety OS are. Keeping the focus on quality and security, it should not be watered down.

---

