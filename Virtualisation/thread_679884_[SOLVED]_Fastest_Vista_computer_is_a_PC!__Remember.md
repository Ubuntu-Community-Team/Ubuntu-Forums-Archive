---
title: "[SOLVED] Fastest Vista computer is a PC!  Remember the Macbook commercial on TV guys?"
date: 2008-01-27
forum: Virtualisation
---

### Post by rosegarden78 on 2008-01-27
Well it's true Windows runs faster in a _Virtual PC_.  Download **VirtualBox** from the repositories.  I had to use "_sudo chgrp user /dev/vboxdrv_" from Xterminal to get past permission errors.  I used a _FAT32 setting expandable to 30 gigs_.  Then _I gave it 192 MB memory_ out of my 512 MB system.  It ran okay but it lags. Then I had an epiphany!  _I allocated 64 MB video memory_ and it runs like a charm!  I can even _access Windows-only web content_ on Linux such as **Abc.com **and **Worldwinner.com**.  Wowzers! :KS EDIT: You can't upgrade video card on Dell laptop so this is a BIG deal for someone like me.

Similar threads:  On a Ubuntu/XP/Vista computer, grub won't boot vista, You guys know if Vista can be resold? I don't hate Windows but I just saw a Vista commercial that made me scoff; World's fastest computer?

EDIT: To use existing XP/Vista/Mac installation you need disk image like Norton Ghost in the ISO format so VirtualBox can boot.

EDIT: Tried MGS games won't work in virtual but vector graphics, video editing, compositing and Internet too faster in virtual mode.

EDIT: Also download Firefox 2.0+ for Windows and install using WINE from repositories to access Windows-only web content.

EDIT: XP in virtual mode on Blackbox Ubuntu.  I did a security check from Gibson Research while not stealth all unused ports are closed.  The hard drive light blinks less in XP virtual mode than Ubuntu or XP in hardware mode.  I think because neither allocates precisely 64MB of video memory on a computer with poor graphic card.  I may stick with using XP on Blackbox this way.

---

