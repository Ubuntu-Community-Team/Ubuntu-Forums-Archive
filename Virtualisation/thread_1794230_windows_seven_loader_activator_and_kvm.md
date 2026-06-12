---
title: "windows seven loader activator and kvm"
date: 2011-06-30
forum: Virtualisation
---

### Post by jeferson.lucio on 2011-06-30
Hi Folks!

Does anybody have any help for me?
I'm trying hard to install and activate Windows Seven Professional 32 bits in a KVM host (host info above).

The  fact is, that when I use a loader like 7loader, by Daz, Hazard and so  on... (I've already tried more than 3 diferent loaders) to activate  Windows, the VM hangs on boot with no info of what is causing so.  (Perhaps I'm missing info, boot is so fast, and I'm using VNC terminals  over network... [IMG]http://forums.meulie.net/images/smilies/icon_rolleyes.gif[/IMG] )

I  don't know what to do. I've already did several tricks that I saw in  Internet, like restoring original Windows boot loader, or overide MBR,  but none of them made things better. If you do so, Windows will start  normally again, however, with no activation info and 30 days left to you  find a suitable serial and activate  [IMG]http://forums.meulie.net/images/smilies/icon_redface.gif[/IMG] .

I  don't know but I think KVM will not work with SLIC activators, or maybe  there is some workaround possible to do in order to achieve that.

Thanks very much all of you! Actually is my first time on this forum.  [IMG]http://forums.meulie.net/images/smilies/icon_biggrin.gif[/IMG] 

Like I said, guys, host info down here ->

Linux (none) 2.6.35-30-server #54-Ubuntu SMP Tue Jun 7 20:13:05 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.10 
GNU/Linux

root@(none):~# kvm --version
QEMU PC emulator version 0.12.5 (qemu-kvm-0.12.5), Copyright (c) 2003-2008 Fabrice Bellard

root@(none):~# modinfo kvm-intel
filename:       /lib/modules/2.6.35-30-server/kernel/arch/x86/kvm/kvm-intel.ko
license:        GPL
author:         Qumranet
srcversion:     0DA388328E3FDE0E15764A5
depends:        kvm
vermagic:       2.6.35-30-server SMP mod_unload modversions
parm:           bypass_guest_pf:bool
parm:           vpid:bool
parm:           flexpriority:bool
parm:           ept:bool
parm:           unrestricted_guest:bool
parm:           emulate_invalid_guest_state:bool
parm:           ple_gap:int
parm:           ple_window:int

 [IMG]http://forums.meulie.net/images/smilies/icon_mrgreen.gif[/IMG]

---

