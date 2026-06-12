---
title: "VM Ware Player 7.1.0 14.04 Issues"
date: 2015-05-22
forum: Virtualisation
---

### Post by bruacucunalsucri on 2015-05-22
Hi all,

I am trying to find more infos on possible reasons because my ubuntu 14.04 host plus vmware player 7.x it's almost impossible to use.

My short story:
- PC Sony Vaio VGN-FW21Z (it came with Windows Vista immediately Physical2Virtual'ized) FullHD with 8GB RAM and 512GB SSD
- Ubuntu initially with 7.10 then upgraded to 8.04 - 8.10 - 9.04 - 10.04 LTS - 12.04 LTS lastly to 14.04 LTS always via Internet
- Vmware Player 1.0 upgraded to 2.x, 3.x, 4.x, 5.x up to 6.06 lastly 7.x
- Guest VM: Windows (98, XP, Vista, 7, 8.1, 10) + CentOS 6.x + OpenSuse + MSDOS 6.x + Fedora (many)
Everything went in the best way possible up to migration to 14.04 LTS and after that upgrading Vmware Player to 7.x
After last migration/upgrade ALL VMs expecially the ones based on Windows became painfully slow...

Is anyone recognizing its troubles from my description?

Googling "ubuntu 14.04 vmware player 7 slow" does not help or at least it didn't help me up2now...
What I discovered already is that Vmware 7.x requires OpenGL 3.2 as minimum;
this level of support should be delivered in ubuntu from the package called "mesa" but as of today (2015.05.22) latest mesa package available does support only OpenGL 3.1.
I've tried the repository maintained from user "oibaf", working on the upgrade of Mesa package to support OpenGL 3.3. Nothing changed using the newest packages...

Another possible reason of my issue could be software support for the video card used in my PC (ATI/AMD 3650 HD); officially this card is left behind since more than 18months from AMD proprietary driver (fglrx) while should be fully supported from radeon open source driver.
Utililties like glxgears (using Opengl...) works like a charm...

It could be the reason is just the missed support for OpenGL 3.2?

What is it best to do for time being?

I do not know but I've disinstalled Vmware Player 7.x and reinstalled Vmware Player 6.06; I can survive for time being waiting for a complete solution...

Thanks to anyone helping me to clarify this issue...

Ciao,
Gianni

---

