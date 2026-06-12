---
title: "adding the linux-rt kernel to normal ubuntu"
date: 2008-11-15
forum: Ubuntu Studio
---

### Post by homebrewalright on 2008-11-15
Hello,

New to the forums.  

My question is, when you install the linux-rt metapackage, does it uninstall the stock kernel, or do they both remain installed and audio programs just get redirected to use the linux-rt kernel?  

If the latter is the case, is it possible to uninstall the stock kernel and use the audio kernel exclusively? 

I'm trying to build a minimal live distro to use for ardour/hydrogen/etc exclusively so I'm not worried about the real time kernel causing issues with other applications/uses.

---

### Post by barisurum on 2008-11-15
First of all if you intend to use rt kernel with 8.10 version of ubuntu (2.6.27 rt kernel) then you should read this before doing so: [http://ubuntustudio.org/node/12](http://ubuntustudio.org/node/12) Ubuntu people don't suggest installing an rt kernel with 8.10 at this time. You can install 8.04 ubuntu studio and use it without problems as I do.
> 
My question is, when you install the linux-rt metapackage, does it uninstall the stock kernel, or do they both remain installed and audio programs just get redirected to use the linux-rt kernel?

When you install a kernel metapackage it will exist side by side with the older kernel and while booting you can select which kernel to boot with in the grub menu. So applications will depend on which kernel you boot with.

> If the latter is the case, is it possible to uninstall the stock kernel and use the audio kernel exclusively?

Yes if you experience no problems with the rt kernel it is safe to remove the other one. But as I said before install with 8.04 not 8.10.


> I'm trying to build a minimal live distro to use for ardour/hydrogen/etc exclusively so I'm not worried about the real time kernel causing issues with other applications/uses.

I use ubuntu 8.04 with no problems. I can use it with 3d acceleration too but I don't because it seems to cause problems with jack audio server as it needs much priority.

---

