---
title: "ubuntu 9.10 i386 livecd uses harddisk swap partition"
date: 2009-12-13
forum: Security
---

### Post by walterav on 2009-12-13
When using the livecd it automatically mounts the swap partition on my local harddisk. Typing the command 'free' in the terminal shows that the system uses allot of swap space including the local partition. Also typing 'sudo swapon -a" show the local hard-disk partition as being used for swap. 

This might be enabled for better performance on the livecd, but I think its bad because it alters the pc on which the livecd is running on.

My final goal is creating a customized livecd without this swap behaviour.

How do I disable this swapping and let it only use the swap in the compressed fs on the cd?
[http://ubuntuforums.org/showthread.php?t=518496](http://ubuntuforums.org/showthread.php?t=518496)

---

### Post by Joeb454 on 2009-12-13
Using the swap area wouldn't alter the PC which the LiveCD is running on at all. And it will only use that swap partition if one exists - it wouldn't create one.

---

### Post by walterav on 2009-12-14
> **Joeb454 said:**
> Using the swap area wouldn't alter the PC which the LiveCD is running on at all. And it will only use that swap partition if one exists - it wouldn't create one.

I'm not saying it creates one, it uses a existing swap area and therefore can leave marks like passwords or keys unencrypted on the local harddisk swap area.

Is there a other way than typing after the livecd has booted "sudo swapoff -a" to turn this off by default?

---

### Post by walterav on 2009-12-26
> **walterav said:**
> I'm not saying it creates one, it uses a existing swap area and therefore can leave marks like passwords or keys unencrypted on the local harddisk swap area.

Is there a other way than typing after the livecd has booted "sudo swapoff -a" to turn this off by default?

Anyone?

---

### Post by q.dinar on 2009-12-27
on the one hand livecd OS should ask for permission from user to change hard disk content, on the other hand may be it will not show how will look real installed OS truly if asks about swap space on start. 2009-12-28 10:55 utc+3 : not, there is nothing bad if such option, live cd is already not like installed system, it asks for language and where too boot.

---

### Post by Jekshadow on 2009-12-28
I think that it is a bad idea to do ANYTHING with the HD from a Live CD, without explicit user permission. Swapping can only hurt a dying drive you are trying to get important files off of.

---

### Post by adam814 on 2009-12-28
So you're wanting to make a LiveCD for your own personal use to make absolutely certain none of your passwords or encryption keys end up in an unencrypted swap partition anywhere you might take it?

It seems like there should be an option for it.  In Knoppix you can add noswap as a "cheat code."

Either way if the first thing you do is run swapoff after boot the only password that might be recoverable would be the liveuser password for the CD, which is probably not that useful.

If you're doing it in the context of rescuing a system you might try one of the more forensically-inclined LiveCDs like Backtrack, Helix, or Trinity Rescue Disk.

P.S. swapon -a turns on all available swap, it's swapon -s that shows which swap files/partitions are in use.

---

