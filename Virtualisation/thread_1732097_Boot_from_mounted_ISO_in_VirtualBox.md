---
title: "Boot from mounted ISO in VirtualBox"
date: 2011-04-17
forum: Virtualisation
---

### Post by jordanae on 2011-04-17
I'm trying to install Arch on a virtual machine, but so far it's not working. When booting up Arch on a virtual machine I get a different result that when I boot it up on my computer. In stead of the normal setup I see
EFI Shell version 2.10 [1.1]
Current running mode 1.1.2
Device mapping table
blk0 :BlockDevice - Alias (null)
     stuff stuff stuff
blk1 :BlockDevice - Alias (null)
     more stuff stuff stuff

Press ESC in [5-1] seconds to skip startup.nsh, any other key to continue.
Shell>

And when I type in help there's too much information to read and I can't pipe it to more or less :'(

Anyway, that stuff's not too relevant, just putting it out there in case anyone can solve that problem. 

What I want to try is an alternate boot method to see if it's just a problem with booting Arch ISOs on VB (although I don't think it's very likely). So does anyone know if it's possible to boot from a mounted ISO in VirtualBox from Ubuntu?

---

### Post by lmarmisa on 2011-04-18
No problem here. I attached the iso file archlinux-2010.05-core-i686.iso as a virtual CD/DVD.

This is the md5sum of this file:

```

luis@UB1010ZOTAC:/media/VirtualBox/ISOs$ md5sum archlinux-2010.05-core-i686.iso 
5db5fd11713635cff208b11a498c59ef  archlinux-2010.05-core-i686.iso
luis@UB1010ZOTAC:/media/VirtualBox/ISOs$

```What iso file did you use?.

Best regards,

Luis

---

