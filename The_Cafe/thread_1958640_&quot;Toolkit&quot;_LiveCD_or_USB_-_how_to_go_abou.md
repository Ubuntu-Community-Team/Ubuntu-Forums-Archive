---
title: "&quot;Toolkit&quot; LiveCD or USB - how to go about this"
date: 2012-04-14
forum: The Cafe
---

### Post by Copper Bezel on 2012-04-14
Hey all. This doesn't seem specific enough for any of the support forums, but I'm not sure how to go about this.

What I want to make is an Ubuntu install I can boot from LiveCD or flash drive for hardware testing, partitioning, and other utility functions. I want one CD or flash drive I can go to if I want to check someone's hardware and run disk checks, fix my own GRUB and move partitions, etc.

I want a partition editor, something like Device Manager, Palimpsest or an equivalent, and a lightweight window manager like Openbox, along with a basic browser in case the machine I'm testing is the only one present and I need to look something up or download a file. Ideally, I want both a LiveCD and a flash drive install, in case the machine I'm using it on can't boot from one or the other. I want it to be an Ubuntu system because Ubuntu ships with some drivers that Fedora et al. don't.

What would you suggest, and how would you go about this?

Thanks for any help.

---

### Post by forrestcupp on 2012-04-14
You can do any of the things you want from the normal Ubuntu Live CD/USB. For a lighter weight version, you could try the Lubuntu Live CD. If you create a Live USB with the Startup Disk Creator, it will allow you to use some of the memory space to save changes. If you do that, you don't really need to "install it to the flashdrive".

---

### Post by Copper Bezel on 2012-04-14
Oh, cool. I had no idea. I'm going to have to poke around the software on the LiveCD, then, and find out what I've been missing. (Damn - I feel a little silly; I could have sworn that Palimpsest wasn't in the default apps, but there it is. And of course the other hardware stuff can be managed from the terminal.) Thanks!

---

### Post by forrestcupp on 2012-04-15
> **Copper Bezel said:**
> Oh, cool. I had no idea. I'm going to have to poke around the software on the LiveCD, then, and find out what I've been missing. (Damn - I feel a little silly; I could have sworn that Palimpsest wasn't in the default apps, but there it is. And of course the other hardware stuff can be managed from the terminal.) Thanks!

I could be wrong, but I think the default apps in the Live environment might be a little different than the ones in the real installation just to be useful for stuff like you're talking about. No matter what, you can still temporarily install anything in the repos; it just won't be there next time you boot to the LiveUSB. I don't know whether setting the flash drive to have memory space will also save installed apps, or just your settings.

---

