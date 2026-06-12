---
title: "Boot Trouble"
date: 2011-05-01
forum: Ubuntu Studio
---

### Post by Miykel on 2011-05-01
G'Day guys;
   Tried to boot into Ubuntu this morning, after had it running perfect last night, went through the windows boot loader then to a screne which said;
  GNU GRUB Version 1.98 + 20100804-5Ubuntu2
Minimal BASH-Like line editing is supported for the first word,TAB list possible command completions. Anywhere else TAB lists possible device or file completions.

  Has anyone got any idea what this is and how to get around it, I can't get to the Grub boot options so I can't boot into recovery mode.
Kind regards  Miykel   :confused:

---

### Post by FuzzShifter on 2011-05-01
You should be able to update GRUB with the live CD.

Why are you using Windows bootloader?

---

### Post by Miykel on 2011-05-01
G'Day Fuzzshifter; Thanks for the reply; When I loaded Ubuntu with the live disk I couldn't get into into W7, so now I use Wubi, and install Ubuntu from W7 onto a partition on the second HDD, not a virtual disk in W7, and I end up with the W7 boot loader to choose W7 or Ubuntu then Grub to choose the latest upgrade or recovery, so it all works nicely, normally, and for someone like me who is new to Linux and keeps blowing it, it's a very easy and conventien way to reload Ubuntu, I'm not confident, or knowledgeable, enough yet to try to repair Grub from the disc. I'd still like to know what that screne is all about though for my own knowledge, if for nothing else, and if there is a work around.
Kind Regards  MIykel

---

### Post by wilee-nilee on 2011-05-01
> **Miykel said:**
> G'Day Fuzzshifter; Thanks for the reply; When I loaded Ubuntu with the live disk I couldn't get into into W7, so now I use Wubi, and install Ubuntu from W7 onto a partition on the second HDD, not a virtual disk in W7, and I end up with the W7 boot loader to choose W7 or Ubuntu then Grub to choose the latest upgrade or recovery, so it all works nicely, normally, and for someone like me who is new to Linux and keeps blowing it, it's a very easy and conventien way to reload Ubuntu, I'm not confident, or knowledgeable, enough yet to try to repair Grub from the disc. I'd still like to know what that screne is all about though for my own knowledge, if for nothing else, and if there is a work around.
Kind Regards  MIykel

Do not upgrade grub it is using the windows bootloader.

Take a look at this thread and see if it looks like your in this camp.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Also if you can it may be helpful to post the bootscript in my signature, for the people who are really in tune with wubi.

Post the script in code tags, by clicking on the** (#)** in the reply panel, then paste the text between the code tags generated.

---

### Post by Miykel on 2011-05-02
G'day wilee-nilee, thanks for the reply, that Wubi Megathread is great, it will take a while to read and digest it so I printed it to file to get into later, I have no problems at all with Wubi, it's mainly my lack of knowledge and experience which causes me problems with live disc installs, so Wubi is great for me, as far as I can understand it's designed to use the Windows boot loader the the grub option screen, the problem begun when I tried to load the nVidia drivers into 10.10, thats when it all come apart, then received the notice to upgrade to 11.04, that didn't work either, so yesterday I downloaded the latest version of Wubi, deleted the Ubuntu partition,in W&, and installed 11.04 using Wubi and look out, it's perfect, nVidia drivers loaded first time, the desktop is brilliant, turns out it's 64bit version but thats ok, just a bit of fiddleing round to get flashplayer to install, other than that is great. "like a toy with a new kid"    lol.
 Kind Regards  Miykel

---

