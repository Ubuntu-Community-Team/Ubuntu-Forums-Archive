---
title: "Can't setup my virtualized windows 7 screen to my screen resolution"
date: 2012-12-04
forum: Virtualisation
---

### Post by fakedave on 2012-12-04
Hello,

this is my first post on this forum because I'm very new to Linux & Ubuntu.
I already apologize for my Linux understanding but I'm confident I'll improve.

I run Ubuntu 12.10 and installed virtualbox 4.1.18 (failed to install 4.2...).
I installed Windows 7 in a VM and I'd like to use it full screen, i.e. 1920x1200 and/or 2560x1440.

I read so many different things on the net but none worked (yet).
I tried ```
VBoxManage controlvm "my_vm" setvideomodehint 1920 1200 16
```. I get no error if the vm is running and an error if it's not running. I both case I can't change the resolution in W7.

I tried installing guest additions (failed) and finally understood it's not what to do in my case.

Since I'd like to use this configuration for work, I like to have my base image/environment fully working before I deploy some projects in different vms.

I apologize for that additional question on the topic but I'm afraid I have an additional problem.

Thanx a lot for your help.

Nicolas

---

### Post by howefield on 2012-12-04
Guest additions are required to be installed for you to run full screen. Why did they fail to install ?

---

### Post by fakedave on 2012-12-04
Ha ok ...

Well, I found the following on tutorials:
```
sudo apt-get update --> ok
sudo apt-get install dkms build-essential linux-headers-`uname -r`--> apparently ok
sudo yum install dkms binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers kernel-devel --> says No package available ...

```

Then when i go into the virtualbox menu bar, I should see a 'Device' menu which I don't. I have 'File' + 'Machine' + 'Help' so I don't know what to do.
I never have a virtualbox terminal.

Any clue?

---

### Post by howefield on 2012-12-04
What is the "sudo yum ect ect..." command for ?

---

### Post by howefield on 2012-12-04
> **fakedave said:**
> Then when i go into the virtualbox menu bar, I should see a 'Device' menu which I don't. I have 'File' + 'Machine' + 'Help' so I don't know what to do.

The menu you describe is what you see from the Oracle VM VirtualBox Manager window, the Device menu will show up from the actual Virtual Machine Window...

---

### Post by fakedave on 2012-12-04
I don't know what the 'yum' stuff is doing, just stupidly followed a tuto ([https://forums.virtualbox.org/viewtopic.php?f=3&t=15679](https://forums.virtualbox.org/viewtopic.php?f=3&t=15679))

Regarding the menu, that's the thing, I don't see any when I have the vm window selected ...
See the attachment :(

---

### Post by howefield on 2012-12-04
Are you moving the mouse up over the panel, to where it says Virtualbox in order to reveal the menu ?

---

### Post by fakedave on 2012-12-04
> **howefield said:**
> Are you moving the mouse up over the panel, to where it says Virtualbox in order to reveal the menu ?

Yes I am although it not shown.
It works for all other apps, even the main virtualbox window but not the vms themselves...

---

### Post by howefield on 2012-12-04
Try installing guest additions by mounting the guestadditions .iso onto the CD drive.

You should already have the iso on your machine, but might be simpler to download from here, make sure you navigate to the correct folder to match your installed version of Virtualbox..

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

and mount to the virtualbox CD drive by right clicking on the CD icon at the bottom right of the virtual machine window.

---

### Post by fakedave on 2012-12-04
> **howefield said:**
> Try installing guest additions by mounting the guestadditions .iso onto the CD drive.

You should already have the iso on your machine, but might be simpler to download from here, make sure you navigate to the correct folder to match your installed version of Virtualbox..

[http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

and mount to the virtualbox CD drive by right clicking on the CD icon at the bottom right of the virtual machine window.

You won't believe me but I don't have those icons at the bottom right of that vm window. However I do remember seeing them few days back.
I wonder if they have not disappeared when I chose the seamless mode. I don't know how to revert now.

Would it be a good idea to reinstall?
Would i lose my vms? (I already spent time setting one up with software).
I installed 4.1.18 from the software center because I failed installing the 4.2 from the oracle website.
What would you recommend??

Thanx a lot for your time because I'm not there yet :(

---

### Post by howefield on 2012-12-05
> **fakedave said:**
> You won't believe me but I don't have those icons at the bottom right of that vm window. However I do remember seeing them few days back. I wonder if they have not disappeared when I chose the seamless mode.

Oh, I believe you ;-)

When in seamless mode, you should have the menu available in the task bar, like in the screenshot. It is one pixel high when not in use, but mouse over to reveal - as per screenshot. 

> Would it be a good idea to reinstall? Would i lose my vms?

You can uninstall Virtualbox, and you won't lose the actual VM.

[qoute]I installed 4.1.18 from the software center because I failed installing the 4.2 from the oracle website.[/QUOTE]

I have never used that method, but guest additions are also in the Software Centre. You could try installing from there.

---

### Post by fakedave on 2012-12-05
brilliant brilliant brilliant !!!
I could not get the small icons at the bottom of my vm window but I actually found that I could get a menu with Host + Home key.
It proposed me to install the Windows Guest additions.
Then it did not go very smooth to have an image in full screen but it eventually worked. It even manages 2 screens but the final target is 4 screens :D

So I'm gonna work a bit in that configuration to be sure that it works according to my expectations.
I need to schedule regular backups on the VM to a server. Anyway ...

Thanx a lot for your support, I would not have managed to do it without you!

Last question: would you recommend another virtualization software that virtualbox for professional usage? It can have a reasonable price.
I used Parallels a lot on my macs and it was good.

Thanx again 

=D>=D>

---

### Post by howefield on 2012-12-05
> **fakedave said:**
> I could not get the small icons at the bottom of my vm window but I actually found that I could get a menu with Host + Home key.

Glad to hear you are making progress. :-)

> Last question: would you recommend another virtualization software that virtualbox for professional usage? It can have a reasonable price.

Hmm, my needs are well served by VirtualBox and have been since they were an Innotek company. I have used it in a professional setting with networking in bridged mode, worked flawlessly.

Perhaps others can suggest if there are better solutions.

---

