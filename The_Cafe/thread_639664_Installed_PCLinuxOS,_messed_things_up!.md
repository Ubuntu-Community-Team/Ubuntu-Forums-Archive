---
title: "Installed PCLinuxOS, messed things up!"
date: 2007-12-13
forum: The Cafe
---

### Post by BigSilly on 2007-12-13
Can anyone help me please? Wasn't sure where to put this, but hopefully this will be OK. Please move it to a relevant area if needs be.

I have a fairly small hard drive (80Gb) and I set it up with 40Gb for Ubuntu Gutsy, 20Gb for a spare FAT32 partition, and another 20Gb at the end which up until an hour ago had Mandriva 2008. 

I decided I fancied a try of PCLOS to replace my Mandriva install. So I inserted the disc, installed it from the desktop, and though I'm not greatly techie minded I thought I'd requested it to add Ubuntu to the Grub menu fine. However when I rebooted it had listed it just fine, but wouldn't boot into it.

I had previously downloaded something called the [Super Grub Disk]("http://supergrub.forjamari.linex.org/"), and in a bit of a panic I decided to use it to repair the boot record. This it seems to have done for the most part.

However, when I boot into Ubuntu now I get a load of text which interrupts the bootsplash like this:

```
fsck.ext3:Unable to resolve 'UUID = d981d2be-3dcb-4c70-bb6c-8d13fd2173ab'

fsck died with exit status 8

failed (code 8)

*file system check failed
```

It requests I either put in my root password, or press CTRL-D to continue, which then boots into Ubuntu just fine. But is there a way to restore it to how it was ie boots into Ubuntu without intervention from the user? What actually has happened here, and is it easy to fix? 

Many, many thanks for your help from a bit of a...lets just say non-techie person!

---

### Post by smartboyathome on 2007-12-13
I tried PCLOS, and it screwed my comp up too. I was stuck on it for two weeks. Anyway, I had to revert to the grub from my Ubuntu install and wipe PCLOS off my system.

---

### Post by BigSilly on 2007-12-13
> **smartboyathome said:**
> I tried PCLOS, and it screwed my comp up too. I was stuck on it for two weeks. Anyway, I had to revert to the grub from my Ubuntu install and wipe PCLOS off my system.

ARRGH! Don't say that please! I wouldn't have done it if I'd known.

Can anyone help me out here? Have I messed up my Ubuntu permanently now?

---

### Post by timcredible on 2007-12-13
probably just a bad entry in menu.lst.  do a search on the configfile option in grub, it's better to point to the other OS and let it's grub handle the booting of it's own partition rather than another distro trying to guess at the parameters. 

shortened version, go to /boot/grub/menu.lst and erase the entry for ubuntu, and change it to an entry that uses the 'configfile' option.  then it'll work.

---

### Post by Lostincyberspace on 2007-12-13
Yes check the menu.lst for both distros you will probably need to merge them for both to work right.

---

### Post by BigSilly on 2007-12-13
Many thanks for your replies. 

Practically, how do I go about doing this? It's something I've never done before.

---

### Post by BigSilly on 2007-12-14
Fixed it now. Apparently Ubuntu was attempting to mount Mandriva, which of course isn't there anymore. I was told to comment out the old line, which has done the trick beautifully. My thanks to the Linux Format forums for the help I needed.

So far really enjoying PCLOS. I can't see it replacing Ubuntu as our main system, but it's nice to have both top rated Linux OS's on one PC.

---

