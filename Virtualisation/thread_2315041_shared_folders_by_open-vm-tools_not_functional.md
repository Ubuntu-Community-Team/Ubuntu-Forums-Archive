---
title: "shared folders by open-vm-tools not functional"
date: 2016-02-25
forum: Virtualisation
---

### Post by kaweka on 2016-02-25
Shared folders do not work in following setup, Ubuntu 15.10 64Bits Desktop virtual, on OS X physical and VmWare Fusion 7.1.3, open-vm-tools version provided by Ubuntu package manager.
So currently VmWare Tools are installed along with open-vm-tools, I know a strange configuration, but generally we tend to open-vm-tools, but need shared folders to be functional.
open-vm-tools programmers seems to have provided a fix in their's repository.
When the next possible deadline for Ubuntu 15.10 to get this update?

---

### Post by MAFoElffen on 2016-02-26
This is what I see on the VMWare boards:

While your Ubuntu VM is running, select Virtual Machine -> Reinstall Vmware Tools. It mounts the ISO as a VM CD. It uninstalls open-vm-tools, and reinstalls it. It complaians that everything is there, but after a reboot, then works??? No -one there can seem to explain the wehy of that, but it seems to be working? But the version of the toolset needs to match the arch of the VM... 64 or 32 bit.

You say there is now a newr version of the toolset? (You know you can also dl it straight from VMWare right? That is what I do for VMWare Player, and vSphere...)

I don't have a MAC here, just Linux and Win machines... So that is what I hear on the VMWare forums.

---

### Post by kaweka on 2016-02-26
Thanks. Actually I target to use open-vm-tools as it promises less efforts on kernel updates. Is your answer to be understood as suggestion
it will be a very long way to have shared folders working in open-vm-tools packages offered by Ubuntu 15.10? Actually did not get the quoted board discussion.

Any chance to find Ubuntu document with future plans for open-vm-tools packages maintenance?
When could 15.10 offer the package version with shared folders  functional?

---

### Post by MAFoElffen on 2016-02-26
I researched what you said... This launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/1500581](https://bugs.launchpad.net/ubuntu/+source/open-vm-tools/+bug/1500581)

That report said that open-vm-tools version 9.10.2 (2:9.10.2-2822639-1ubuntu3) fixed that. Did it? 

I searched in launchpad and that version is in main for Wiley 15.10 now. The search also said that version 10.0 (2:10.0.0-3000743-3ubuntu1) is in main for Xenial 16.04.

---

### Post by kaweka on 2016-02-27
Well, I have got working shared folders and guest can use screen's full physical resolution.
All this by installing just Fusion bundled VmWare Tools and applying fix as described in Fusion 7.1.3 release notes.
open-vm-tools had been purged from machine.

The only pity is, used config is based on VmWare Tools which by vendor is no more recommended to be used
and it generates lot of maintenance when guest os kernel receives updates.
So the current solution can be only a short term workaround.
Next major updates of guest os and the problems will be deeper because VmWare support/development discontinued.

2:9.10.2-2822639-1ubuntu3 does not fix it, as for our setup the shared folders are not working.
Main and universe are enabled.
Wily-updates and Wily-security are enabled.

---

### Post by MAFoElffen on 2016-02-29
And... for my own benefit, what was the fix that worked for you, that was in those release notes? 

I kept hearing from users that there was a problem with 15.10 and vmware "products" with host shared folders (among other things)... if I update it to the current 15.10's kernel (current updates). And yes, I found, like you did, that 9.x of the toolset did not fix that.

I'm not using Fusion, but with VSphere, Workstation and VMware Player... And I can reproduce those errors with all I'm using. So pretty much across the board. 

I'm still trying things. I can access them via smb shares, but not directly mounted through the VMware Tools Toolset, with access directly from the VM's Advanced settings menus. I've been at it since Friday night.

Hoping what worked for you on your MAC, might help me find an answer for these other VMware products.

---

### Post by kaweka on 2016-03-01
Hi,
Sorry for the delay, lot of tasks to accomplish these days.
In posting no.5 - this thread - I described the taken path.
Did you take a look at Fusion's 7.1.3 RN? 
[VMware Fusion 7.1.3 Release Notes]("http://pubs.vmware.com/Release_Notes/en/fusion/7/fusion-713-release-notes.html")

> If the bundled VMware Tools are installed, perform the following steps:

    As root, edit the /etc/vmware-tools/vmware-user.desktop file by changing this line:
    Exec=/usr/bin/vmware-user
    To this line:
    Exec=env VMWARE_USE_SHIPPED_LIBS=1 /usr/bin/vmware-user
    Log out of the virtual machine and log in again.
    This change can prevent the VMware Tools service (vmtoolsd) from crashing.
Me did not perform RN workaround step 3.

To whole history in our environment belong following facts:
* After had removed open-vm-tools , but bundled VmWare Tools still installed, an error pop-up was generated
on every user logon. Don't remember those details, I guess it was something about vmware.
* Error pop-ups on user logon, lack of full physical resolution on guest side were fixed by applying the fix from Fusion 7.1.3 RN
* At very beginning the setup was: Ubuntu version 15.04 and Fusion version 7.2.1
* Many months ago Fusion was updated to 7.3.1 - no problems neither with shared folders
  nor with full resolution upon this update
* Some months later, following the Ubuntu update to 15.10, the guest Ubuntu was updated to 15.10
  The new Ubuntu came with some kind of platform detection, the Ubuntu 15.10 seems to had detected Fusion
  as platform, I conclude it because open-vm-tools were automatically installed along with Ubuntu 15.10, without any
  admin's action. From this point of time both were installed: bundled and the open one. This combination led to problems
  as described.
* Admin was not aware of open-vm-tools existence until the guest upgrade to Ubuntu 15.10 was completed.
  So immediately after update completion admin started the application of bundled Tools as usual, based on experiences from past.
  The installer script of bundled tools made a hint open tool  were installed, this was the point where open-vm-tools awareness 
  started to exist on admin's side.


I wonder if shared folders not working (open tools) is problem of open-vm-tools rather
than Ubuntu 15.10 package management. Any idea?

---

### Post by kaweka on 2016-03-08
I got informed by VmWare last days in following way.
If one needs shared folders to be functional and one wants to use open-vm-tools
the vmware bundled tools need to be installed too.

All this, as I believe, due to vmhgfs driver which is not included in open-vm-tools and VmWare 
is opportunistic if it comes to provision of stand-alone vmhgfs driver, or to provide it as firmware or other form into kernel.
Basically on VmWare side there are no  objections reg. parallel installation of both packages.

Actually, for those using shared folders it is a real pity as it makes open-vm-tools with their's gold-valued target useless.

Further conclusion, neither 2:9.10.2-2822639-1ubuntu3 nor any later patch can fix it as long
as VmWare position reg. vmhgfs driver licencing/availability does not change.

---

### Post by kaweka on 2016-03-12
Some of my statements made here recently seem to be a mess/********. I will correct it as soon as some free time resources available.
Concluded on my research made since my last activity in this thread.
Please accept my apologize.

---

