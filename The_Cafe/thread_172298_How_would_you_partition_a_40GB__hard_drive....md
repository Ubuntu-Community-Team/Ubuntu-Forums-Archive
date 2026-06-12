---
title: "How would you partition a 40GB  hard drive..."
date: 2006-05-08
forum: The Cafe
---

### Post by dolny on 2006-05-08
I bought a laptop to install Ubuntu + XFCE/KDE on it:

[http://rodan.net/eSklep/prod?id=acer+2423nwxmi++053](http://rodan.net/eSklep/prod?id=acer+2423nwxmi++053)

+ additional 512MB of RAM

...and I have to partition the hdd. The /home/ will have a separate partition for sure, I will be using the laptop alone + give it sometimes to my friends (separate guest account with very basic apps). How would YOU use this hard drive?

PS. I'm praying for a working WiFi (the card seems very basic)
PS2. The computer will be shipped in two days time. Can't wait to test it with Penguin.

---

### Post by louis_nichols on 2006-05-08
I would definitely use LVM. It can resize partitions (or equivalents, cause it uses a different terminology) on the go, especially with reiserfs filesystem.

So you could just give the home partition and the root partition some comfy values in the beginning, then resize them with the unused space, with just 2 commands, without even unmounting that partiton.

What I did: I had 15GB on my hdd for Ubuntu. I gave / a 1.5 GB space and /home a 2 GB space in the beginning. Then, when space was getting low for Ubuntu, I would add 500MB more. It is now at 2.5 GB, with quite a lot free, actually. /home evolved faster, and has 9GB. So, I still have some 3 GB to add where needed. The only thing is that /boot cannot be in lvm, so for that I made a 100MB partition. Anyway, the bios sees the whole LVM space as one partition, and only the kernel can read the logical volumes and mount them as if they were partitions.

Info [here]("http://www.tldp.org/HOWTO/LVM-HOWTO/index.html")

---

### Post by Stormy Eyes on 2006-05-08
I'm not sure I'd recommend using LVM outside of a RAID environment. I've never had any reason to use it on my desktop machines at home, anyway. For a 40GB drive, I'd recommend the following layout:
```
mount   size    filesystem
/boot   100MB   ext3
/       15GB    reiserfs
swap    512MB   swap
/home   24GB    reiserfs
```

This should give you plenty of room for Ubuntu, as well as a reasonably large /home partition. The swap partition is the same size as your physical RAM, and the /boot partition is separate (and comes first) so that if you're paranoid, you can adjust /etc/fstab so that /boot isn't mounted and thus cannot be altered by mistake. (This is the Gentoo way, and I think it's a good idea. You can always manually mount it if you're going to compile the kernel or install a new one.) I suggest ext3 for /boot instead of reiserfs because I've heard that GRUB doesn't always cope well with reiserfs.

---

### Post by louis_nichols on 2006-05-08
[QUOTE=Stormy Eyes]I'm not sure I'd recommend using LVM outside of a RAID environment. [/QUOTE]

Well, I use it on only one hard drive. I haven't had any problems. I don't think you were suggesting I might, though. Why do you say you wouldn't recommend LVM? I might reconsider....

> I've never had any reason to use it on my desktop machines at home, anyway.

That may be so, but my experience has been that it offers an extra bit of comfort. I mean, for me it meant relief from struggling to find out the best partitioning scheme in the beginning and just resizing when needed.


>  For a 40GB drive, I'd recommend the following layout:
```
mount   size    filesystem
/boot   100MB   ext3
/       15GB    reiserfs
swap    512MB   swap
/home   24GB    reiserfs
```

This should give you plenty of room for Ubuntu, as well as a reasonably large /home partition. The swap partition is the same size as your physical RAM, and the /boot partition is separate (and comes first) so that if you're paranoid, you can adjust /etc/fstab so that /boot isn't mounted and thus cannot be altered by mistake. (This is the Gentoo way, and I think it's a good idea. You can always manually mount it if you're going to compile the kernel or install a new one.) I suggest ext3 for /boot instead of reiserfs because I've heard that GRUB doesn't always cope well with reiserfs.

Isn't 15GB for / kind of a lot? I mean, how could Ubuntu, with all the software someone might need, reach that size? It's not Windows! :)

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=louis_nichols]Isn't 15GB for / kind of a lot? I mean, how could Ubuntu, with all the software someone might need, reach that size? It's not Windows! :)[/QUOTE]

There's a difference between "all you need" and "everything you want". I'm always generous when allocating space to /, because I know I'll want to tinker and install more stuff. Also, depending on the laptop's specs, you might want to install a game or two in /opt. *Neverwinter Nights*, for example has taken up 3GB on my hard drive.

---

### Post by ubuntu_demon on 2006-05-08
IMHO I wouldn't use LVM because it isn't necessary and AFAIK it isn't very easy to do (with that I mean well integrated into the installer).

/ : ext3 6 gb  (6 gb is enough for everything you will want to install using apt-get including gnome,kde and xfce but if you want to install big games add more space here as you see fit)

swap as big as your memory unless you are planning to use applications that use lots of memory such as video editting then you should 

/home ext3 the rest of the harddisk

---

### Post by dolny on 2006-05-08
I appreciate your answers guys. Another question btw. Would you use KDE or XFCE on such laptop? I bought additional 512MB (default: 256). I don't use Gnome because I always used KDE and really like it, but maybe XFCE would be a better choice for such specs? I think I'll install both and check the performance etc.

---

### Post by BoyOfDestiny on 2006-05-08
[QUOTE=dolny]I appreciate your answers guys. Another question btw. Would you use KDE or XFCE on such laptop? I bought additional 512MB (default: 256). I don't use Gnome because I always used KDE and really like it, but maybe XFCE would be a better choice for such specs? I think I'll install both and check the performance etc.[/QUOTE]

I hope there is an open slot :) Not that I've been ripped off... So you'd have 768mb total? Here is what I'd use:

6.5 gig reiserfs /
remaining reiserfs /home
1 gig swap (maybe for suspend to ram etc, it'd be a good call)

---

### Post by Orunitia on 2006-05-08
You don't need 15GB for ubuntu... at all. That's too much overkill. I use a 6GB partition and that's **plenty**. When all you have is 40GB why waste all that space? What I do with my 100GB is give 6GB for Ubuntu, 512 or whatever for swap, and give the rest for a storage partition. Easy to reinstall ubuntu without losing anything. (I like completely fresh installs so I don't make my /home seperate.)

---

### Post by lordofkhemenu on 2006-05-08
I partitioned my 60G this way -
100MB boot
512MB  - swap
10-ish GB  - /
the rest - /home

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=dolny]I appreciate your answers guys. Another question btw. Would you use KDE or XFCE on such laptop? I bought additional 512MB (default: 256). I don't use Gnome because I always used KDE and really like it, but maybe XFCE would be a better choice for such specs? I think I'll install both and check the performance etc.[/QUOTE]

I think that if you upgrade the RAM, you should be able to use KDE. I'd take a look at the factory-default hard drive, though. If it's only a 5400RPM drive, instead of 7200RPM, the drive will slow down the rest of the machine.

---

### Post by ubuntu_demon on 2006-05-08
Just install ubuntu,kubuntu and xubuntu together. Try them all and use whichever suits you.

It's a laptop so differences in power management are important. I don't have a laptop so I don't know much about it.

Personally I use gnome for my desktop and xfce4 for my 2nd machine (gateway/fileserver/I work on it using vnc for example when I'm not at home)

---

### Post by Orunitia on 2006-05-08
[QUOTE=Stormy Eyes]I think that if you upgrade the RAM, you should be able to use KDE. I'd take a look at the factory-default hard drive, though. If it's only a 5400RPM drive, instead of 7200RPM, the drive will slow down the rest of the machine.[/QUOTE]

Additional? You **really** like overkill don't you? You don't need something like a gig of ram to run KDE.

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=Orunitia]Additional? You **really** like overkill don't you? You don't need something like a gig of ram to run KDE.[/QUOTE]

Like Oscar Wilde said, **nothing succeeds like excess**.

---

### Post by Omnios on 2006-05-08
Either way you look at it you are going to want a partition for your / and for your home now this brings up a question. When you do a fresh install and make a seperate partition for your home will it whipe your current home directory in which case you will want a documents directory to back up all your stuff.

---

