---
title: "Virtualising different Ubuntu versions."
date: 2013-11-24
forum: Virtualisation
---

### Post by jw4165 on 2013-11-24
Hi all,

I wish to run a virtual version of Ubuntu 12.04 64-bit to test some software compatibility.

My question: Is VirtualBox the best method of achieving this? and if so what files are are required?

---

### Post by bashiergui on 2013-11-24
VirtualBox is an option. So are XEN and VMWare. Whatever you're trying to accomplish drives which one to choose.
```
sudo apt-get install virtualbox
``` or ```
sudo apt-get install xen-hypervisor-amd64
``` or download vmware from the vmware website.

---

### Post by jw4165 on 2013-11-25
Update: I should have mentioned that my base operating system on my drive is Precise 32-bit.

When I try to boot an instance of 64-bit Ubuntu on VirtualBox I receive the following error:

[IMG]http://i40.tinypic.com/2w2hi7b.png[/IMG]

I guess that it is impossible to emulate 64-bit when the base is 32-bit?

---

### Post by JKyleOKC on 2013-11-25
Not impossible; I'm doing it on another machine here. However you have to get into the BIOS of the host machine and enable the hypervisor options. The specific means of doing this varies from one BIOS publisher to the next, but so far as I know all of them do have this option, and most of them default to OFF rather than having it enabled.

Getting to the BIOS itself requires that you re-boot and press a key immediately after the POST process but before the boot load begins, which is usually a time window only a second or two wide. Which key to press depends on the box's manufacturer. My HP and Compaq boxes require F10; some of my older machines required DEL. Most systems give you a very brief message during the self-test that tell you which key they need...

EDIT: Older machines that are not 64-bit compatible at all won't have this option. If you don't find it in the BIOS setup screens, your system may be one of these antiques. However any system built within the past decade or so should be compatible, and have the option in BIOS.

---

### Post by ibjsb4 on 2013-11-25
This may help

 	  	  	 		  		 			  			[h=3][Re: 64bit guest on a 32bit host]("https://forums.virtualbox.org/viewtopic.php?f=1&t=46904#p211781")[/h] 			[[IMG]https://forums.virtualbox.org/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("https://forums.virtualbox.org/viewtopic.php?p=211781#p211781")by **[mpack]("https://forums.virtualbox.org/memberlist.php?mode=viewprofile&u=17541")** » 24. Dec 2011, 12:59 
  			  			Support for 64bit guests requires CPU  virtualization support in the host, A.K.A. VT-x (or AMD-v). You need to  verify that your CPU has this feature (use google). Intel used to think  of this as a premium feature so only found on higher end chips.  If the  feature exists in the CPU, then it may need to be enabled in the BIOS,  as in many cases it is disabled by default. Tweaking the BIOS would  involve pressing Del or F10 or something like that as your PC begins to  boot up. There's usually a very brief message telling you the correct  key. Once in, you would need to find an option which says something like  "Virtualization technology: disabled", and make sure it is enabled.  Remember to save changes. Finally, make sure the VT-x option is selected  in your VM recipe.

[https://forums.virtualbox.org/viewtopic.php?f=1&t=46904](https://forums.virtualbox.org/viewtopic.php?f=1&t=46904)

---

### Post by jw4165 on 2013-11-26
As my computer is capable of running a 64-bit OS I just decided to install it as the base Operating System.

Thank you for sharing your thoughts [COLOR=#000000]JKyleOKC and ibjsb4. After some rooting around in my BIOS I found and enabled the "Secured Virtual Machine Mode" which seemed to do the trick for VirtualBox (I have tested Ubuntu Precise 32-bit which functions well).

I am interested in trying out XEN but I am unsure how to use it properly once installed through the terminal.[/COLOR]

---

### Post by jdeca57 on 2013-11-26
> **jw4165 said:**
> 
I am interested in trying out XEN but I am unsure how to use it properly once installed through the terminal.

The question is always - what do you want to accomplish and with what effort? The least effort with very good results is without doubt Virtualbox. Effort-wise, KVM is better than XEN and comparable in speed. I've tried the three, and I've tried VMWare. Nowadays if it's simply to try out a version like Xubuntu vs OpenSUSE I use Virtualbox. XEN is a true hypervisor and that changes your system rather profoundly. It's no rocket science, but the term RTFM springs to mind.

---

