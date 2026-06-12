---
title: "GRUB 2 bootloader - Full tutorial"
date: 2009-12-04
forum: The Cafe
---

### Post by Dedoimedo on 2009-12-04
Hello all,

Hear, hear! The long awaited GRUB 2 ultra-guide is ready!

I have carefully prepared and written an extensive tutorial about how to setup and configure GRUB 2 (version 2, the next generation) bootloader with multiple operating systems, including GRUB legacy and GRUB 2 mix, dual-boot and triple-boot real-life testcases covering Ubuntu, Kubuntu, openSUSE, Mandriva, and Windows 7, upgrading from GRUB legacy to GRUB 2, menu customization, and basic and intermediate troubleshooting. 

You will love this, I promise you!

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)


Cheers,
Dedoimedo

---

### Post by leorolla on 2009-12-04
Thanks for the page!

I have been googling like crazy and haven't found a simple tutorial on how to replace commands of the good old grub1, like these for making a live USB:

grub
grub>device (hd3) /dev/sdc
grub>root (hd3,0)
grub>setup (hd3)
grub>quit

Could you post some links?

Thanks.

---

### Post by Dedoimedo on 2009-12-04
I'm not sure what you're asking ...

You have the list of commands in the article, linking to the official GRUB 2 page, with comparison to GRUB legacy.

Cheers,
Dedoimedo

---

### Post by leorolla on 2009-12-04
I mean with GRUB legacy I could install GRUB to the MBR of (hd3)=/dev/sdc running those commands. Frist grub to open the shell and the next commands inside the shell.

And there are lots of tutorials over the web (for instance that of Super Grub Disk itself) making reference to this procedure.

Now without grub1 we cannot copy-paste those commands, and I didn't find a simple tutorial of how to replace them by grub2-equivalents.

---

### Post by audiomick on 2009-12-04
Nice work, thanks very much.
Bookmarked it immediately..:p

---

### Post by mc.prtk on 2009-12-05
Gonna try it out really soon................. THNX A MILLION!:lolflag:

---

### Post by Leppie on 2009-12-05
> **leorolla said:**
> Thanks for the page!

I have been googling like crazy and haven't found a simple tutorial on how to replace commands of the good old grub1, like these for making a live USB:

grub
grub>device (hd3) /dev/sdc
grub>root (hd3,0)
grub>setup (hd3)
grub>quit

Could you post some links?

Thanks.

You can install grub wherever you want without the need to enter the grub shell:
```
$sudo grub-install /my/dev  ##if your usb stick is /dev/sdc, change /my/dev to /dev/sdc and... voila!
```

---

### Post by Torrilin on 2009-12-05
Just a warning... on some systems (like mine last month) the command line route you give for fixing a damaged Grub2 install will fail. Instead, I needed to boot from a LiveUSB, and use the gui to make mounting and binding happen... apparently on my system the correct mount points are quite different from that given in the guide. This then changes the paths for all subsequent commands, and a new user would be in pretty serious trouble.

I'd strongly suggest you add sections detailing what the grub> and grub recovery> prompts are supposed to have in the way of commands. When my grub install was damaged, grub recovery had ls and root available. None of the other commands that were supposed to work did (including the help command). It was a pretty serious failure, and a pretty bad failure mode. I got out of it with no data loss, but it took all day to dig up how to do it.

If you *do* end up booting into a grub> or grub recovery> prompt, there's a theoretical way to fix it from there, and it would be good to cover it. It's easier to make the instructions in that mode generic enough to cover all systems :). My problem was that the two commands I had available were less than half of what was needed to actually get through a repair.

---

### Post by Dedoimedo on 2009-12-05
Torrilin - that's why it's called beta software ...
Dedoimedo

---

### Post by Torrilin on 2009-12-06
Yup. The problem is, right now your guide only covers one way to recover from a fried Grub2 :). And I know from experience it's possible to fry Grub2 badly enough that the method fails, just off a simple Ubuntu reinstall. That makes your method a bad one to have as the only one in an Ubuntu focused guide.

One of the big hurdles for documentation is getting things laid out so a n00b who knows how to type man (commandname) and (commandname) --help can get themselves out of trouble using your documentation. Right now, this isn't the case for your guide (coz well, I found at least a half dozen versions of it with google when I was stuck). If you'd like help digging out how to use the grub>, grub recovery> and LiveCD graphical tools to get things clearer, I'd be happy to.

Good documentation is often the difference between a clumsy beta and software that everyone loves too.

---

### Post by Dedoimedo on 2009-12-06
I have in the tutorial reference to 3 different error codes you might encounter, super grub disk method, and two manual methods, all for beta software. I guess it's a reasonable share.

Don't forget that if you screw your system so badly then you might start over, be an expert and not need my tutorial, try using automated tools like SGD.

Dedoimedo

---

### Post by pbrane on 2009-12-06
This is a great thread! However I still haven't found the answer to this:
[http://ubuntuforums.org/search.php?searchid=67925193]("http://ubuntuforums.org/search.php?searchid=67925193")

I tried gfxpayload using several different forums suggestions and tutorials. But I either get just a flashing cursor or with vesafb enabled I get nothing.

Any suggestions?

---

### Post by dany8907 on 2009-12-06
Oh man This is what I needed last week. 

Thanks for the guide. helps out a lot lot lot.

---

### Post by l-x-l on 2009-12-06
> **pbrane said:**
> This is a great thread! However I still haven't found the answer to this:
[http://ubuntuforums.org/search.php?searchid=67925193]("http://ubuntuforums.org/search.php?searchid=67925193")

I tried gfxpayload using several different forums suggestions and tutorials. But I either get just a flashing cursor or with vesafb enabled I get nothing.

Any suggestions?

I have the same problem. There's been a bug report already created in launchpad about it. Do you have a NVidia graphics card? Still it seems that the short answer to your question is that the "set gfxpayload" isn't fully working feature yet in Grub2.

---

### Post by Flymo on 2009-12-06
**Many thanks for the tutorial! ** Still studying it, & trying to fathom out what we need to do here....   
Do wish that the nice Ubuntu devs had waited a bit before choosing this beta Grub2 which seems to fail on 4 out of 5 Ubuntu 910 installations here.  Xubuntu 910 installs and boots OK, just won't recognise any other OS.... <sigh>

---

### Post by pbrane on 2009-12-06
l-x-l:

Yes I have an nvidia card. And yes it does seem that gfxpayload isn't working yet. I have seen posts about enabling a framebuffer but that doesn't fix it either, makes it worse. for now **vga=xxx** seems to be the way to go.

---

### Post by meborc on 2009-12-14
> **pbrane said:**
> l-x-l:

Yes I have an nvidia card. And yes it does seem that gfxpayload isn't working yet. I have seen posts about enabling a framebuffer but that doesn't fix it either, makes it worse. for now **vga=xxx** seems to be the way to go.

+1

i have been trying to get framebuffer to work... debian guys seem to get gfxpayload to work - [http://forums.debian.net/viewtopic.php?f=5&t=41881](http://forums.debian.net/viewtopic.php?f=5&t=41881)

but no luck for me... i still have to use vga=795

---

