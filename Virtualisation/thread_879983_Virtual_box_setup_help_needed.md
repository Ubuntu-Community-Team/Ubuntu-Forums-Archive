---
title: "Virtual box setup help needed"
date: 2008-08-04
forum: Virtualisation
---

### Post by heiowge on 2008-08-04
Hi there.  While I prefer to stay in Ubuntu most of the time, occasionally I need to load WinXP.  It's a pain in the a** to do it because I have to reestablish links and reactivate kopete etc, not to mention the fact that I actually have to wait for windows to load...

I thought I'd get virtualbox up and running, but I'm not sure what it wants me to do.

I have an 80gb hd split about 50-50 between hardy and XP.  I tend to use the XP partitions as storage, because I can access them easily with either OS.

I want to set up virtual box to activate my existing XP install and save me having to reboot.

It seems however to want a brand new ISO or suchlike of XP to work from.  Am I right here or just reading it wrong?

Can anyone walk me through the setup?

Ta.

---

### Post by dca on 2008-08-04
I believe VirtualBox is available from the 'Add/Remove Software' app under the 'Applications' menu from main menu bar.  Just be sure you set the drop-down to 'All Available' and use virtualbox as your search string.  I'm sure you'll be forced to lose your XP because of Microsoft licensing, you may want to check on that.
 
I basically use VMware for my VM(s), but, the below link seems like a pretty good how-to:
 
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html)

---

### Post by benerivo on 2008-08-04
> **heiowge said:**
> It seems however to want a brand new ISO or suchlike of XP to work from.Yes, it does. It will set up a file on your hard disk, which acts like a new physically separate drive, to be used to install an OS on to. I don't think it can use an existing partition with an existing OS, and then capture that to run in a virtual environment.

As i understand it, the main problem is that your current xp, is set up/installed on your existing hardware, which is not perfectly emulated by virtualbox, so it would be like trying to unplug your hard drive, and plug it in to someone elses computer and turning it on -- it's not going to work. All i think you can do, is to use your xp install disk, and install it on to a new virtual machine.

---

### Post by dca on 2008-08-04
> **heiowge said:**
> 
I want to set up virtual box to activate my existing XP install and save me having to reboot.

It seems however to want a brand new ISO or suchlike of XP to work from.  Am I right here or just reading it wrong?


If I'm getting all this straight (above) what you would need in order to run XP through your VM is an actual Windows XP Home or Pro installation CD...

---

### Post by y@w on 2008-08-04
VMware offers a tool that can migrate a system from a physical disk to a virtual machine. [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

Not sure about a migration path from VMware to Virtual Box, but you can download and install VMware server onto Linux for free..

---

### Post by snowpine on 2008-08-04
A virtual machine is just that, a virtual machine. You would install XP (or any other OS) by mounting the install CD (or an ISO) to the virtual machine and following the normal install procedure. By default (there is a shared folders option), the virtual machine can't see anything on your ubuntu or windows partitions, since it has its own virtual hard drive. 

Common sense would dictate that your Windows license would allow you to run Windows on a virtual machine on that same computer, but common sense may or may not be the law in your jurisdiction...

---

### Post by heiowge on 2008-08-04
Problem is the only legit copy of XP i've got is the one that came with this machine.  It's XP home that installs with a restart disc - not the stand alone version.  I don't have a stand alone disc for XP (or any other Windows OS for that matter.)

Any ideas?

I'm not after removing the XP install I've got, I just want to be able to open a window in hardy that runs my XP copy that's already installed for me when I need to.  If that's possible...:confused:

---

### Post by y@w on 2008-08-04
So, you want to leave the Windows install the way it is and still be able to boot it up virtually while Linux is running? I'm assuming it's on the same machine.. I'm pretty sure Parallels can do that: [http://parallels.com](http://parallels.com)

It's pay-for software, but it might get the job done.

---

### Post by heiowge on 2008-08-05
That might actually do it.  Now I just need the cash...:(

---

### Post by stevebakerj on 2008-08-05
> **heiowge said:**
> Hi there.  While I prefer to stay in Ubuntu most of the time, occasionally I need to load WinXP.  It's a pain in the a** to do it because I have to reestablish links and reactivate kopete etc, not to mention the fact that I actually have to wait for windows to load...

I thought I'd get virtualbox up and running, but I'm not sure what it wants me to do.

I have an 80gb hd split about 50-50 between hardy and XP.  I tend to use the XP partitions as storage, because I can access them easily with either OS.

I want to set up virtual box to activate my existing XP install and save me having to reboot.

It seems however to want a brand new ISO or suchlike of XP to work from.  Am I right here or just reading it wrong?

Can anyone walk me through the setup?

Ta.

Yes you can use your exsisting XP install, I have done it with Feisty but not with Heron, I would suggest you read this thread:

[http://ubuntuforums.org/showthread.php?t=852915](http://ubuntuforums.org/showthread.php?t=852915)

---

### Post by overdrank on 2008-08-05
Moved to Virtualization :)

---

