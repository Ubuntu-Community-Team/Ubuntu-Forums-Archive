---
title: "VirtualBox on Ubuntu 14.04"
date: 2016-05-24
forum: Virtualisation
---

### Post by matthew210 on 2016-05-24
[SIZE=3]***[Before you read my thread, please note I'm on Ubuntu version 14.04 [http://prnt.sc/b80w32](http://prnt.sc/b80w32)******. I have made a mistake In my thread title, *****my apologies *****for getting you guys confused.]***[/SIZE]

Hello,

I am kinda new to Ubuntu/Linux/Unix so please bare with me. I have purchased a virtual private server and installed Ubuntu 14.10 on the server, afterwards I have Installed VirtualBox on the server and I have created a Windows 7 machine. When I try starting up my box it gives me this error.

[IMG]http://i64.tinypic.com/2csjq6x.png[/IMG]

I tried using the command '/sbin/rcvboxdrv setup' to reinstall the kernel module but after pressing enter it gave me another error.

[IMG]http://i65.tinypic.com/14ij39t.png[/IMG]

I tried going on Google to search for the kernel module, but I had no luck in finding the right Linux Header. I would appreciate it if you could help me out, I'm new to Linux and I'm trying to figure out this problem I am having.


Thanks,
Matthew

---

### Post by QIII on 2016-05-24
Hello!

First, before we go anywhere:  You do realize that 14.10 has passed its End Of Life date and is no longer supported, right?

Also:  Some VPS vendors do not allow some modifications to kernel modules and may block this.

---

### Post by matthew210 on 2016-05-24
> **QIII said:**
> Hello!

First, before we go anywhere:  You do realize that 14.10 has passed its End Of Life date and is no longer supported, right?

No I didn't know that.... I'm sorry, any suggestions on what I should do?

---

### Post by QIII on 2016-05-24
I would reinstall a supported LTS release.  I use 14.04 on my servers.  It is supported until 2019.

I haven't put 16.04 on my servers yet.  I'll wait at least until the first point release.

How much time/data/software do you have invested in this installation?

---

### Post by matthew210 on 2016-05-24
> **QIII said:**
> I would reinstall a supported LTS release.  I use 14.04 on my servers.  It is supported until 2019.

I haven't put 16.04 on my servers yet.  I'll wait at least until the first point release.

How much time/data/software do you have invested in this installation?

Well, the host I bought the server from only supports to Ubuntu 15.04. All I have on the machine is mate desktop environment, and Virtualbox at the moment. I was hoping this would work because I wanted to use a Virtualbox on the ubuntu machine and run Windows 7. What LTS release are supported? basically like I said the host only has up to version 15.04. There're other Linux/Unix OS but I'm not familiar with them as ubuntu.

Thanks,
Matthew

---

### Post by ajgreeny on 2016-05-24
The supported versions at present are 14.04, 15.10 and 16.04.

Like QIII, I would suggest 14.04 until the first point release, 16.04.1, due out in July, I believe.

14.04 is super stable and highly recommended in my opinion, but use either 14.04.1 or the most recent 14.04.4, though if you use that .4 point release you will need to update the hardware enablement stack packages ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) in July.  If you use the .1 version (or the original 14.04) it will retain support for everything until April 2019.

---

### Post by matthew210 on 2016-05-24
> **ajgreeny said:**
> The supported versions at present are 14.04, 15.10 and 16.04.

Like QIII, I would suggest 14.04 until the first point release, 16.04.1, due out in July, I believe.

14.04 is super stable and highly recommended in my opinion, but use either 14.04.1 or the most recent 14.04.4, though if you use that .4 point release you will need to update the hardware enablement stack packages ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) in July.  If you use the .1 version (or the original 14.04) it will retain support for everything until April 2019.

Thank you for replying, I've got one question. How do I check what Ubuntu version I have Installed right now? Is there a command to check?

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Yes you can enter this in the terminal
```
lsb_release -a
```
Will give you the current booted system.
Kind Regards

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Yes you can enter this in the terminal
```
lsb_release -a
```
Will give you the current booted system.
Kind Regards

Thank you so much, I'm on Ubuntu version 14.04. I thought I was on Ubuntu version 14.10, my bad. 

> **QIII said:**
> I would reinstall a supported LTS release. I use 14.04 on my servers. It is supported until 2019.

I haven't put 16.04 on my servers yet. I'll wait at least until the first point release.

How much time/data/software do you have invested in this installation?

I just found out I'm on version Ubuntu version 14.04. ([http://prnt.sc/b80w32](http://prnt.sc/b80w32)) I thought I was on Ubuntu version 14.10, my bad. The question now is how do I fix this VirtualBox issue? 

> **ajgreeny said:**
> The supported versions at present are 14.04, 15.10 and 16.04.

Like QIII, I would suggest 14.04 until the first point release, 16.04.1, due out in July, I believe.

14.04 is super stable and highly recommended in my opinion, but use either 14.04.1 or the most recent 14.04.4, though if you use that .4 point release you will need to update the hardware enablement stack packages ([https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)) in July.  If you use the .1 version (or the original 14.04) it will retain support for everything until April 2019.

I just found out I'm on version Ubuntu version 14.04. ([http://prnt.sc/b80w32](http://prnt.sc/b80w32)) I thought I was on Ubuntu version 14.10, my bad.

---

### Post by QDR06VV9 on 2016-05-24
Try this then
```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms

```
Now Restart your VB and now issue this in the terminal
```
sudo apt-get install virtualbox-dkms
```
EDIT: Sorry i had forgotten the last command was after restarting you Virtual Box

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Try this then
```
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

After entering the last command you suggested, it gave me this error. [http://prntscr.com/b818qs](http://prntscr.com/b818qs) any suggestions?

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Please reread my last post after issuing this in the terminal
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
I had forgotten the order and way of inputting those commands.
But let's resolve this first before we go back to that.

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Please reread my last post after issuing this in the terminal
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
I had forgotten the order and way of inputting those commands.
But let's resolve this first before we go back to that.

After putting the command ```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
``` this came up. [http://prntscr.com/b81fue]("http://prntscr.com/b81fgg")

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Humm? Seems one of the pics you uploaded has changed since I last looked at it.
But lets see what this will do now..and post back any errors.
```
sudo apt-get install linux-headers-generic build-essential dkms
```

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Humm? Seems one of the pics you uploaded has changed since I last looked at it.
But lets see what this will do now..and post back any errors.
```
sudo apt-get install linux-headers-generic build-essential dkms
```

I have Installed dkms with no problems.
[IMG]http://i64.tinypic.com/149ntyh.png[/IMG]

Thanks,
Matthew

---

### Post by QIII on 2016-05-24
matthew210:

It would be a lot easier for everyone if, instead of posting an images of terminal output off site, you copied the text directly from the terminal and pasted it here between code tags.

To do that:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by matthew210 on 2016-05-24
> **QIII said:**
> matthew210:

It would be a lot easier for everyone if, instead of posting an image off site, you copied the text directly from the terminal and pasted it here between code tags.

To do that:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Sorry about that, I will remember next time.

---

### Post by QIII on 2016-05-24
No worries.  Just trying to make things easier for you.

---

### Post by QDR06VV9 on 2016-05-24
Ok now this in the terminal
```
sudo apt-get remove --purge virtualbox-dkms
```
And if [U][B]no errors show 

[/B][/U]Reboot the Virtual Box and next issue this
```
sudo apt-get install virtualbox-dkms
```

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Ok now this in the terminal
```
sudo apt-get remove --purge virtualbox-dkms
```
And if [U][B]no errors show 

[/B][/U]Reboot the Virtual Box and next issue this
```
sudo apt-get install virtualbox-dkms
```

Done.

There were no errors after entering the first command. After rebooting and entering the second command. This came up. 

[IMG]http://i67.tinypic.com/29zvfqb.jpg[/IMG]

---

### Post by QDR06VV9 on 2016-05-24
Ya that's a old bug....But can you now start your Virtual Box?

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Ya that's a old bug....But can you now start your Virtual Box?

No I cannot start my Virtual Box, it's giving me the same error as before.



Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Well gaul darn it..what dose this show from the terminal 
```
uname -r
```

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Well gaul darn it..what dose this show from the terminal 
```
uname -r
```

When I enter uname -r this is what comes up. ```
2.6.32-042stab113.11
```

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Well how the heck did that happen? He he he.:D
Anyway that's a problem as mine shows
```
uname -r
4.2.0-36-generic
```
I am stumped here ATM
By the way you don't need to be running the same kernel version as me but kernel "2.6.32-042stab113.11" is just a mystery to me??

Can you tell me what this shows now
```
apt-cache policy linux-headers-generic
```

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Well how the heck did that happen? He he he.:D
Anyway that's a problem as mine shows
```
uname -r
4.2.0-36-generic
```
I am stumped here ATM
By the way you don't need to be running the same kernel version as me but kernel "2.6.32-042stab113.11" is just a mystery to me??

Can you tell me what this shows now
```
apt-cache policy linux-headers-generic
```

Aha, I tried searching for that kernel version on Google. I couldn't find anything for that kernel, it's weird ugh. This is what I get when I type in that command.

[IMG]http://i68.tinypic.com/hrexph.jpg[/IMG]

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
Yep that's a show stopper for sure...but one more just to verify something.
```
apt-cache policy linux-image-generic
```
And just one more question do you always run as root in the terminal?

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Yep that's a show stopper for sure...but one more just to verify something.
```
apt-cache policy linux-image-generic
```

[IMG]http://i66.tinypic.com/2prepuw.png[/IMG]

---

### Post by QDR06VV9 on 2016-05-24
Ok there is the problem...We need to install the right kernel
```
sudo apt-get install linux-image-generic
```
And after that is installed you will need to reboot your host system.
So in other words reboot Ubuntu and after a restart see if the VB now starts.

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> Ok there is the problem...We need to install the right kernel
```
sudo apt-get install linux-image-generic
```
And after that is installed you will need to reboot your host system.
So in other words reboot Ubuntu and after a restart see if the VB now starts.

After Installing and rebooting my Ubuntu server, I still cannot start my virtual machine. It also Installed 3.13.0.86.92 version not the one I need to run my virtual machines. 



Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-24
I do not understand?
Linux-image and headers match 3.13.0.86.92...What kernel version do you think you need? 
But now i see that you using Windows 7 as host and Ubuntu as Guest but I see no real reason that Ubuntu Server is not starting?

---

### Post by matthew210 on 2016-05-24
> **runrickus said:**
> I do not understand?
Linux-image and headers match 3.13.0.86.92...What kernel version do you think you need? 
But now i see that you using Windows 7 as host and Ubuntu as Guest but I see no real reason that Ubuntu Server is not starting?

I need version 2.6.32-042stab113.11 in order to run my virtual machine.

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-25
Reboot your virtual machine and when you see Oracle's logo , click the screen (focus there) and then hold down Shift until Grub menu appears. And there you will see a Menu with something along these lines.
[B]Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)[/B]
I have included screenshots to help.

Now select Advanced options for Ubuntu...and from there the kernel 2.6.32- should be shown there so select that kernel an hit enter to boot to that.
I will try to hang in here for today to see if we can get you sorted out.
Kind Regards

---

### Post by matthew210 on 2016-05-25
> **runrickus said:**
> Reboot your virtual machine and when you see Oracle's logo , click the screen (focus there) and then hold down Shift until Grub menu appears. And there you will see a Menu with something along these lines.
[B]Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)[/B]
I have included screenshots to help.

Now select Advanced options for Ubuntu...and from there the kernel 2.6.32- should be shown there so select that kernel an hit enter to boot to that.
I will try to hang in here for today to see if we can get you sorted out.
Kind Regards

I cannot do that because the Ubuntu Server is on a Virtual Private Server, I have a cPanel that the host gave me. I can restart the server, rebuild the server, and shutdown the server. I cannot get in the Grub menu.. Any other way to get to the Grub menu?

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-25
> **matthew210 said:**
> I cannot do that because the Ubuntu Server is on a Virtual Private Server, I have a cPanel that the host gave me. I can restart the server, rebuild the server, and shutdown the server. I cannot get in the Grub menu.. Any other way to get to the Grub menu?

Thanks,
Matthew
Again that is Odd I have always been able to get to grub menu...but that said I just do not use windows either.
Yes if you can Edit /etc/default/grub:

```
sudo nano /etc/default/grub
```

And add a # in front of [B]GRUB_HIDDEN_TIMEOUT=0
[/B]So it will now look like this**    [B]#GRUB_HIDDEN_TIMEOUT=0**
To save hit Ctrl + o and Ctrl +x[/B]
Apply with:

```
sudo update-grub
```

---

### Post by matthew210 on 2016-05-25
> **runrickus said:**
> Again that is Odd I have always been able to get to grub menu...but that said I just do not use windows either.
Yes if you can Edit /etc/default/grub:

```
sudo nano /etc/default/grub
```

And add a # in front of [B]GRUB_HIDDEN_TIMEOUT=0
[/B]So it will now look like this**    [B]#GRUB_HIDDEN_TIMEOUT=0**
To save hit Ctrl + o and Ctrl +x[/B]
Apply with:

```
sudo update-grub
```

When I do sudo update-grub it gives me this error.


```
/usr/sbin/grub-probe: error: failed to get canonical path of `simfs'.
root@sergio:~#

```

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-25
What dose
```
mount
```
show?

---

### Post by matthew210 on 2016-05-25
> **runrickus said:**
> What dose
```
mount
```
show?

```
simfs on / type simfs (rw,relatime)proc on /proc type proc (rw,relatime)
sysfs on /sys type sysfs (rw,relatime)
none on /dev type devtmpfs (rw,nosuid,noexec,relatime,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/cgroup type tmpfs (rw,relatime,size=4k,mode=755)
none on /run type tmpfs (rw,nosuid,noexec,relatime,size=104860k,mode=755)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
none on /run/shm type tmpfs (rw,relatime)
none on /run/user type tmpfs (rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755)
```

---

### Post by QDR06VV9 on 2016-05-25
Not what I was looking for??
Lets try this
```
sudo fdisk /dev/sda
```
And hit enter and then press "p"
and enter again

---

### Post by matthew210 on 2016-05-25
> **runrickus said:**
> Not what I looking for??
Lets try this

```
# sudo fdisk /dev/sda
fdisk: unable to open /dev/sda: No such file or directory
```

---

### Post by QDR06VV9 on 2016-05-25
Huumm..stubborn little critter isn't it..lol
Well this should show something i can go on.
```
sudo fdisk -l
```

---

### Post by matthew210 on 2016-05-25
> **runrickus said:**
> Huumm..stubborn little critter isn't it..lol
Well this should show something i can go on.
```
sudo fdisk -l
```

Yeah, this is really weird and frustrating. When I type in

```
sudo fdisk -l
```

Nothing shows up lol.....

---

### Post by Habitual on 2016-05-25
linux-headers-2.6.32* sure looks like RH/CentOS nomenclature to me.
OpenVZ been mentioned, like the other thread at [LQ]("https://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/virtualbox-on-ubuntu-14-04-issue-4175580655/")?

OP says he installed Ubuntu Server, but ....error message is that of CentOS/RH ?
Not sure myself OpenVZ "nodes" supports anything but CentOS.

Just sayin'...

---

### Post by matthew210 on 2016-05-25
> **Habitual said:**
> linux-headers-2.6.32* sure looks like RH/CentOS nomenclature to me.
OpenVZ been mentioned, like the other thread at [LQ]("https://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/virtualbox-on-ubuntu-14-04-issue-4175580655/")?

OP says he installed Ubuntu Server, but ....error message is that of CentOS/RH ?
Not sure myself OpenVZ "nodes" supports anything but CentOS.

Just sayin'...

Do you have any suggestions on what I should do? ugh

---

### Post by QDR06VV9 on 2016-05-25
> **Habitual said:**
> linux-headers-2.6.32* sure looks like RH/CentOS nomenclature to me.
OpenVZ been mentioned, like the other thread at [LQ]("https://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/virtualbox-on-ubuntu-14-04-issue-4175580655/")?

OP says he installed Ubuntu Server, but ....error message is that of CentOS/RH ?
Not sure myself OpenVZ "nodes" supports anything but CentOS
+1 Agreed ...that is what i have been trying to figure out where the heck they even came from? :confused:
Hey and thanks for the link Habitual.

---

### Post by QDR06VV9 on 2016-05-25
I would just reinstall now and here is a good guide for that here:[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Habitual on 2016-05-25
> **runrickus said:**
> +1 Agreed ...that is what i have been trying to figure out where the heck they even came from? :confused:
Hey and thanks for the link Habitual.
No worries.
I advise the OP to Export his sole Windows 7 Professional Virtualbox Appliance to an .ova file and 
get that export off the "server".

I am not convinced that the OP has an Ubuntu server.

---

### Post by matthew210 on 2016-05-26
> **Habitual said:**
> No worries.
I advise the OP to Export his sole Windows 7 Professional Virtualbox Appliance to an .ova file and 
get that export off the "server".

I am not convinced that the OP has an Ubuntu server.

Thank you for your help, Do you know what host is good that you recommend for VirtualBox to be Installed without any issues? Also thank you [COLOR=#000000]runrickus for trying to help me, sorry If I frustrated you.

[/COLOR]Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-26
> Also thank you [COLOR=#000000]runrickus for trying to help me, sorry If I frustrated you.
[/COLOR]
Hey no worries on the frustration..as mine comes only in not finding a solution for you.
And I also wish who ever sold you that software would have been a little more Professional.

Habitual may have another suggestion as well but here is a pretty striaght forward method I have used in the past with great success
[http://www.sysprobs.com/export-vmware-virtual-machine-ovf-import-virtualbox](http://www.sysprobs.com/export-vmware-virtual-machine-ovf-import-virtualbox)
Kind Regards and Good luck

---

### Post by matthew210 on 2016-05-26
> **runrickus said:**
> Hey no worries on the frustration..as mine comes only in not finding a solution for you.
And I also wish who ever sold you that software would have been a little more Professional.

Habitual may have another suggestion as well but here is a pretty striaght forward method I have used in the past with great success
[http://www.sysprobs.com/export-vmware-virtual-machine-ovf-import-virtualbox](http://www.sysprobs.com/export-vmware-virtual-machine-ovf-import-virtualbox)
Kind Regards and Good luck

Yeah I agree with you, they could of been more professional and give a little more support... I contacted the host if it's possible to update the kernel. They responded back "I'm sorry but container based VPS cannot run a newer kernel than is available on the host node." I basically paid $10 for **** service, and a server I cannot even use... Anyways I have a Dell Laptop, The specs are. 64-bit Operating System, Intel(R) Core(TM) i7 CPU Q 740 @ 1.73GHz 1.73 GHz. Which is better? VMware Workstation, or VirtualBox? I'm planning on using one of them, and Install Ubuntu 14.04 on it, and basically do what I was planning on doing before with this Host but it didn't work because of the kernel version.

Thanks,
Matthew

---

### Post by QDR06VV9 on 2016-05-26
> **matthew210 said:**
> Yeah I agree with you, they could of been more professional and give a little more support... I contacted the host if it's possible to update the kernel. They responded back "I'm sorry but container based VPS cannot run a newer kernel than is available on the host node." I basically paid $10 for **** service, and a server I cannot even use... Anyways I have a Dell Laptop, The specs are. 64-bit Operating System, Intel(R) Core(TM) i7 CPU Q 740 @ 1.73GHz 1.73 GHz. Which is better? VMware Workstation, or VirtualBox? I'm planning on using one of them, and Install Ubuntu 14.04 on it, and basically do what I was planning on doing before with this Host but it didn't work because of the kernel version.

Thanks,
Matthew
Tastes vary from user to user..so my opinion would be just that, an "opinion"
But try both and see witch one fits your needs or demands. That link I had gave you earlier is good place to start for VirtualBox.
But if i am correct in my assumption on being rather new to all of this...well the only advice I can suggest is 1st, Read to gain information, 2nd, begin to apply what you have learned and 3rd, Learn Patience it will keep you sane...LOL:D
Some good resources for help are VB Forums: [https://forums.virtualbox.org/](https://forums.virtualbox.org/)
And as far as VMware Workstation's I build my own.
And one final piece of advice is you have to learn to make them walk before you can make them run.:o
I wish you nothing but success in your new adventures.;)

---

### Post by Habitual on 2016-05-26
> **matthew210 said:**
> Thank you for your help, Do you know what host is good that you recommend for VirtualBox to be Installed without any issues? Also thank you [COLOR=#000000]runrickus for trying to help me, sorry If I frustrated you.

[/COLOR]Thanks,
Matthew
Virtualbox on a Server? Why?
You are confused enough (and no offense) but you have complications
of  not being able to distinguish between Virtual hosts, or the basic Client-Server model. Again, No Offense.
I use Virtualbox on my desktop to install other OSs.
It is separate from any other virtualized hosts I have.

Why are you installing Virtualbox on a Server that you have rented? 
To what end?
To install Ubuntu server in Virtualbox on a rented VPS running OpenVZ?
Virtualbox is a **Desktop** Computer Virtualization Package.
I doubt seriously any other hypervisor will allow you to further virtualize a virtualized guest, such as OpenVZ


[https://www.linode.com/linodes](https://www.linode.com/linodes) has Ubuntu guests.
[https://www.digitalocean.com/](https://www.digitalocean.com/) too.

Good Luck.

---

