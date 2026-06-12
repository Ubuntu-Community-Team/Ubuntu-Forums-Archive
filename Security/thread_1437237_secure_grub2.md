---
title: "secure grub2"
date: 2010-03-23
forum: Security
---

### Post by BigSteve_G on 2010-03-23
Well I'm surprised! - got my Linux Mint 8 (based on Ubuntu 9.10) system all up & running locked down user folders / files stuff like that & read all over the Internet about how Linux in general is so secure - imagine my surprise when I find out that with just a tiny a bit of info gathered on-line I was able to hack my system giving me access to EVERY single file & folder without being asked for a single password! - and with the aid of a grub2 feature at that.
 
So what I now need is a way to stop users from bringing up the grub menu then being able to use [e] to edit the boot line things.

---

### Post by bodhi.zazen on 2010-03-23
> **BigSteve_G said:**
> Well I'm surprised! - got my Linux Mint 8 (based on Ubuntu 9.10) system all up & running locked down user folders / files stuff like that & read all over the Internet about how Linux in general is so secure - imagine my surprise when I find out that with just a tiny a bit of info gathered on-line I was able to hack my system giving me access to EVERY single file & folder without being asked for a single password! - and with the aid of a grub2 feature at that.

So what I now need is a way to stop users from bringing up the grub menu then being able to use [e] to edit the boot line things.

It is quite a shock. Realistically your best option is to restrict physical access. A close second is encryption. You can perform full encryption with the alternate CD.

Your only option is encryption.

Other then that, physical access = pwnage

This advice applies to all OS.

---

### Post by BigSteve_G on 2010-03-23
Legacy grub had the ability to password protect the option to edit - does grub2 have something like this? - if not I'm just thinking about downgrading grub

---

### Post by bodhi.zazen on 2010-03-23
> **BigSteve_G said:**
> Legacy grub had the ability to password protect the option to edit - does grub2 have something like this? - if not I'm just thinking about downgrading grub

Yes

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

But IMO anything short on Encryption is not worth the bother as both GRUB passwords and BIOS passwords are easily circumvented. Sure it will slow some people down a bit, but I would not put that much trust into it.

---

### Post by BigSteve_G on 2010-03-25
Sorted!
 
I've found a way to secure things by stopping anyone even accessing the grub menu (only catch is (apart from NO-ONE can access the menu) its no good on a dual/multi boot setup)

[[COLOR=#444444]http://forums.linuxmint.com/viewtopic.php?f=46&t=44706[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=46&t=44706")

"I tried a more simpler method of setting all the background, text & highlight colors to black & that half worked but the background meant the text could still (arkwardly) be seen, then I noticed towards the bottom of the grub.cfg file a conditinal statement (IF) which seem to basicaly be saying if the SHIFT key is pressed set the timeout to -1 (show the menu) or if not (ELSE) set it to 0 (just boot) so I change the SHIFT to g expecting to have to use the 'g' key to get the menu but instead it just stops anyone bringing up the menu regardless of what key is press."

I'm using a XP machine at work at the moment so cant post the exact text but if anyone needs things explaining a bit better I'd be happy to post instructions here.

---

### Post by visual1ce on 2011-02-20
Only evil ppl fight koalas.

---

