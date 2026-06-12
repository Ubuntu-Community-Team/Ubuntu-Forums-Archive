---
title: "Virtualizing an existing OS"
date: 2010-04-09
forum: Virtualisation
---

### Post by sexybeast099 on 2010-04-09
I apologize if this was already posted or if this is in the wrong section, but I'm a new Linux convert and to the ubuntu forums.  ANYWAY!

What I'm wanting to do is to run a virtual machine of the other OS I have (I'm dual booting Se7en and Ubuntu 9.10) through my linux OS.  Sometimes I need to run iTunes or otherwise have to take info from one OS and apply it to the other one.  Is there a way to virtualize an already bootable operating system?  I want it to act just like a SAMBA connection or FTP in that any changes to the virtual windows OS changes the already existing windows installation just the same as if I booted into it instead of Ubuntu.  Any ideas?

I realize that with virtualization, the computer is going to run slower, have less accessible ram, etc... etc... but still I would like to make this the next step in my transition.  I'm mildly familiar with CLI and have no problem with typing commands if specifically directed.  As I get directed in a certain way I will most likely revisit the method used and see if I can tweak it to fit my preferences.  All I'm really asking for is to get some direction for research.  I will do the leg work of finding it if someone gives me some keywords at the very least.  Thanks!  If you're reading this far and haven't fallen asleep, I commend you. :lolflag:

~ Sexybeast099

---

### Post by BlazeXI on 2010-04-09
Hey Sexybeast099..

Mmmmm i see what you mean...virtualization will give you the ability to access both OS at the same time and allow for interactive communication between the two also.

I have a similar situation, but mine is more work related....lol ;)

I would suggest using ubuntu as your base/primary OS and install Sun virtualbox as your virtualization software, this software is free to use in a non commercial environment ( for home use ).

this is an extreamly awesome product and personally the best of it's kind.Virtualization will most definitly give you the freedom you require and much MUCH more...way more....hehehehe lol :).

What is the spec of your pc/laptop ??

For further information about virtualbox you can check out the website 
( [http://www.sun.com/software/products/virtualbox/](http://www.sun.com/software/products/virtualbox/) )

Hope this helps ... :) 

let me know if you need guidance...

---

### Post by sexybeast099 on 2010-04-09
yeah, I searched the forums for the answer to this when I was composing this post but most of them came up with windows XP solutions and I think most of us know that Windows XP is very different the Windows Se7en.  Some more directionality I would like is how to easily set something up for my system, a toshiba satellite a215 with an AMD64 AthlonX2 processor and ATI Radeon graphics card (4 GB RAM, 160GB HDD).  I'll look into the link you posted and see if it's on the site but I've very little clue on how to google the solution since, once again, I don't know many keywords if any at all related to my situation.

Thanks for answering though, BlazeXI.

EDIT: I looked where you directed me and couldn't find much more information.  The best I could find was to go to the forums there and post in a VERY similar way to this thread.  help?

---

### Post by TheFu on 2010-04-09
If I read your question correctly, you want to run Ubuntu as the Host OS and create a VM with an completely existing Win7 client.  

Here's the good news.
- that is entirely possible and really very easy using most of the virtualization tools. VirtualBox would be the easiest for you, IMHO.

Here's the bad news.
- Windows installations are tightly connected to the actual hardware on the system. That means unless you can EXACTLY MATCH the disk controller, NIC, and Video controller between your physical system AND the virtual machine, then you'll need to reinstall Windows. Further, if your copy of Windows7 is OEM, it probably will refuse to install since it has been tied to 1 hardware config.

Here's the good news.
- You can use Win7 as the VirtualBox host OS easily and run Ubuntu under it in a VM as the client very nicely.
- This will let all the normal drivers that work with Windows work. You won't have to fight much with sound or wonder why games are slow. Further, Ubuntu can run in constrained RAM environments, 512MB of RAM is plenty.
- You can basically copy your Ubuntu installation into the VBox image disk and it will work (95% likely). OTOH, doing a fresh install of Ubuntu is easy enough. Just capture the already installed packages, backup any custom stuff you've added outside APT and backup your HOME.  All this is really very easy.

Using VirtualBox is really easy under Windows. You have very little to lose in trying it out. You can always deinstall it later. If you use the non-free version, you'll get USB support too, which is handy.  If you do decide to use Win7 has the host, I can provide almost 2 yrs of knowledge. I ran multiple Ubuntu clients under vbox full screen most of that time and found I'd forget it was running in a VM. Performance was that good for me.  I did have odd/performance issues with `rm -rf dir1` commands on "shared" disk storage from the host, but all other disk access was fine even in the same exact directories.

If you intend to run 24/7 servers, virtualbox isn't quite ready, but for desktop virtualization, it is the best non-cost solution that I've found.

---

### Post by dcstar on 2010-04-09
> **TheFu said:**
> 
........
Here's the bad news.
- Windows installations are tightly connected to the actual hardware on the system. That means unless you can EXACTLY MATCH the disk controller, NIC, and Video controller between your physical system AND the virtual machine, then you'll need to reinstall Windows. Further, if your copy of Windows7 is OEM, it probably will refuse to install since it has been tied to 1 hardware config.
........

Which is exactly why you are supposed to create a separate "vanilla" hardware profile in Windows before you convert it to a VM. Then all of these (supposed) problems go away.

VMware have a free converter tool to convert any existing Windows install to a VM - so all the apps are still there and you don't need to reinstall anything.

There are many HOWTOs on the 'net for doing this process, they can be found with a search.

---

### Post by Azazel on 2010-04-11
I have done this in the past with XP as the client and it worked well for me. I am wanting to set up a virtual machine like this again, but I don't remember how. Also, some things are different from the last time I did it, such as Grub2. 

Some links would be nice! Also, what is the free converter tool?

---

### Post by Jpenguin on 2010-04-11
> **Azazel said:**
> I have done this in the past with XP as the client and it worked well for me. I am wanting to set up a virtual machine like this again, but I don't remember how. Also, some things are different from the last time I did it, such as Grub2. 

Some links would be nice! Also, what is the free converter tool?
He is probly refering to--
[http://www.vmware.com/products/converter/overview.html](http://www.vmware.com/products/converter/overview.html)

---

### Post by Azazel on 2010-04-11
Here is a How-To: [http://ubuntuforums.org/showthread.php?t=984437&highlight=virtualbox+existing+os](http://ubuntuforums.org/showthread.php?t=984437&highlight=virtualbox+existing+os)

but unfortunately it doesn't work with Grub2. I'm still trying to get it to work.

---

