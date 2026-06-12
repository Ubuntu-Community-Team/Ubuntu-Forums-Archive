---
title: "VMWare on Gutsy"
date: 2007-11-12
forum: Virtualisation
---

### Post by martianc on 2007-11-12
Does VMWare work in Gutsy? I recently upgraded from Feisty and my virtual machines no longer boot. This is very frustrating, as you might imagine, as I need to work with Windows for my job.

The error message I get when attempting to boot a virtual machine is "Unable to change virtual machine power state: The process exited with an error: End of error message."

I just checked Synaptic, and I'm definitely using the latest version of VMWare provided in the repositories. When I start VMWare, I get a message saying that there's a new version available on the VMWare website, but I don't want to do a manual configure/install.

Any help would be great, thanks!!

---

### Post by zvacet on 2007-11-12
Try to boot in old kernel and see if it is work.Maybe that is it,because when you installed VMware you used Feisty kernel and kernel moduls,and now you have different kernel.Let somebody correct me if I´m wrong.

---

### Post by Green_Star on 2007-11-12
Yup, that is correct.

I am not longer using VMware, I moved to Virtual box.

The days when I was using VMware, when ever the kernal updates then I have to re-compile the moudles, I do not remember the process but you can google it with keywords something like this "new kernal vmware not working"

---

### Post by martianc on 2007-11-12
Thanks for the tips.

@zvacet: I'm still learning Linux, so could you give me some direction on how to boot into the old kernel?

@Green_Star: Virtual box sounds interesting. I presume it doesn't have these upgrade issues like vmware? Googling it seems like I can convert vmware images to virtual box images.

---

### Post by kuja on 2007-11-12
Very frustrating indeed I'm sure. It seems it isn't in the canonical repositories either. It seems it's not in the canonical repository, so you're best off installing from upstream. Here's what I would do (the manual install, seeing as you *need* to build the kernel modules yourself, seeing as it's also missing from the repo!!):

```

sudo apt-get remove --purge vmware-server
sudo rm -rf /etc/vmware

```

Next, download the vmware .tar.gz file from [www.vmware.com/download/server/](www.vmware.com/download/server/)

Then
```

sudo apt-get install linux-headers-`uname -r` build-essential
sudo apt-get install xinetd
cd
tar -xf VMware-server-1.0.4-56528.tar.gz
cd vmware-server-distrib
sudo ./vmware-install.pl

``` (at least most of the defaults should be okay)

---

### Post by zvacet on 2007-11-12
When you start your comp you see grub from wich you can choose wich OS you want to run(if you have two),or wich kernel you want to run.If your grub is show just for feew seconds press **esc** and that willl stop it.Select kernel with lower number(2.6.20-16).

@ **kuja**

I don´t use Gutsy but isn´t Vmware server in synaptic?It is easyer to install it from synaptic,don´t you think.You are basicly tell him to reinstall.I don´t have expirience with Virtual box,but if it doesn´t make this kind of problem why not try it?

---

### Post by dabl on 2007-11-12
VMWare Player 2.0 (downloaded) installed flawlessly on my Kubuntu Gutsy 64-bit system.  Upon inviting it to open my Player 1.5.whatever version .vmx machine, it asked if I want to "move" it and I said "yes", and VOILA it's now working perfectly -- did not need to re-install the OS or the applications that are on it. Very cool.

I know it will be less cool when the next kernel upgrade breaks it ... but I spent an evening fidding with Virtual Box and never did get it working right, so I dunno.  :)

---

### Post by fjgaude on 2007-11-12
The same for me with 64-bit Gutsy using an old vmx file from my 32-bit Feisty. It worked perfectly after I downloaded the VMware Server from their site, unpacked, did the no-brainer install. Bravo! It's so wonderful to be able to re-use vmx folders, and not have to re-install the OS and all the apps for it.

---

### Post by kuja on 2007-11-12
> **zvacet said:**
> 
@ **kuja**

I don´t use Gutsy but isn´t Vmware server in synaptic?It is easyer to install it from synaptic,don´t you think.You are basicly tell him to reinstall.I don´t have expirience with Virtual box,but if it doesn´t make this kind of problem why not try it?

No, it's not in the repositories for gutsy, and seeing as it requires a kernel module (which of course only works for the kernel you're using), using the feisty package won't work.

---

### Post by martianc on 2007-11-12
@kuja & @fjgaude: Tell me if I'm wrong.. but doesn't the manual install make it harder to keep the software up-to-date? I must say I love synaptic and ubuntu's auto-updating features...

re: Virtual box, I'm having some trouble getting the conversion from VMware files to Virtual box files. Maybe the upgrade to Vmware 2.0 would be simpler at this point...

I wish this were all a little easier... sigh. :-)

Thanks for all your help thus far.

---

### Post by kuja on 2007-11-12
> **martianc said:**
> @kuja & @fjgaude: Tell me if I'm wrong.. but doesn't the manual install make it harder to keep the software up-to-date? I must say I love synaptic and ubuntu's auto-updating features...

re: Virtual box, I'm having some trouble getting the conversion from VMware files to Virtual box files. Maybe the upgrade to Vmware 2.0 would be simpler at this point...

I wish this were all a little easier... sigh. :-)

Thanks for all your help thus far.

All that you should need to do after an upgrade when installed this way is re-run the config script.

---

### Post by martianc on 2007-11-15
Regarding VirtualBox:

The install was easy and painless, but I'm receiving a bunch of cryptic errors when loading a virtual machine. The message I receive is "VirtualBox kernel driver not installed." The program kindly suggests I use sudo to start the VirtubalBox process located in /etc/init.d. I try this, and receive a message indicating that "module vboxdrv not found". After some googling without much luck, I decided to resort back to VMWare.

Regarding VMWare,

@kuja, I tried your suggestion of uninstalling the packages for vmware, then running the install script from the vmware website. This worked well, up until the point at which I receive a message saying "None of the pre-built vmmon modules for VMware Server is suitable for your running kernel. Do you want this program to try to build the vmmon module for your system...?" I say yes, and the system bugs out with a bunch of compiler errors. 

:-(

Any ideas as to what else I can do to make this work?

---

### Post by kuja on 2007-11-15
What error? If it's failing to build the module, you might need to use the "any-any" patch ... You can get it [here](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update113.tar.gz).
Extract it ```
tar xf vmware-any-any-update113.tar.gz
```
Now what you need to do with it is place vmmon.tar and vmmnet.tar into /usr/lib/vmware/modules/source/, and then re-run the install script, and it should be good to go after that.

---

### Post by martianc on 2007-11-20
@Kuja: your advice was great, thanks!

I had to copy vmmon.tar and vmnet.tar into the lib/modules/source file inside the extracted vmware install directory (rather than into /usr/lib/vmware/modules/source). But otherwise, a perfect install! 

I owe you a beer. :-D

---

### Post by bparncutt on 2007-11-22
> **martianc said:**
> Does VMWare work in Gutsy? I recently upgraded from Feisty and my virtual machines no longer boot. This is very frustrating, as you might imagine, as I need to work with Windows for my job.

The error message I get when attempting to boot a virtual machine is "Unable to change virtual machine power state: The process exited with an error: End of error message."

I just checked Synaptic, and I'm definitely using the latest version of VMWare provided in the repositories. When I start VMWare, I get a message saying that there's a new version available on the VMWare website, but I don't want to do a manual configure/install.

Any help would be great, thanks!!


I too have this same problem, but I didn't upgrade my kernel to Gutsy...it was a fresh install.  I cannot run VMWare server any other way but from the console.  It will run in this fashion, but I get some output before the program opens:

brandon@brandon:~$ sudo vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

I'm not sure if this means anything.  Once the program is running, and I try to power on my a virtual machine, I get the identical error message quoted above.  Any ideas?

---

### Post by ryke on 2007-11-22
Hi,

I'm running VirtualBox and VmWare Server on Ubuntu Gutsy, and I haven't had any problem.. I have just followed these tutos (they are in Spanish):

- VIRTUALBOX
[http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/](http://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/)
You should add this repo in yor sources.list:
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free
and install it from there.

- VMWARE SERVER
[http://www.ubuntu-es.org/index.php?q=node/67027](http://www.ubuntu-es.org/index.php?q=node/67027)

Regards

---

