---
title: "VirtualBox not working after kernel upgrade"
date: 2012-09-10
forum: Virtualisation
---

### Post by Statia on 2012-09-10
I installed 3.2.0.30 last week, now VirtualBox will not start a VM. It shows a dialog box:


```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```Trying to do that:


```
# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory

```I do have DKMS:


```
# dpkg -l | grep dkms
ii  dkms                                                              2.2.0.3-1ubuntu3                        Dynamic Kernel Module Support Framework
ii  virtualbox-dkms                                                   4.1.12-dfsg-2ubuntu0.1                  x86 virtualization solution - kernel module sources for dkms
```There is no /dev/vboxdrv on my system.


How to get VirtualBox working again?

---

### Post by ranger1021994 on 2012-09-10
sudo dpkg-reconfigure virtualbox-dkms
sudo dpkg-reconfigure virtualbox




You might have recently removed older kernel

---

### Post by nothingspecial on 2012-09-10
*Thread moved to **Virtualization**.*

---

### Post by Statia on 2012-09-10
> **ranger1021994 said:**
> sudo dpkg-reconfigure virtualbox-dkms
sudo dpkg-reconfigure virtualbox




You might have recently removed older kernel

I solved it by using Synaptic to do a reinstall.

I have indeed recently removed an older kernel, I normally have only the last two kernels installed.

This raises a number of new questions though:

- I removed 3.2.0.27, so was left with 3.2.0.29 and 3.2.0.30. Did VirtualBox use modules from 27 under 29? Why did that work? With a video driver, that won't work.
- Why does DKMS take care of my nvidia module, but not of the VirtualBox module?
- How can I make DKMS recompile the driver when I upgrade a kernel?

[moderator: thanks for moving my post, I had not seen there is a virtualization section on the forum]

---

### Post by ranger1021994 on 2012-09-10
Virtualbox uses kernel specific modules ie.29 will work with 29 only...so when you remove a kernel the modules of virtualbox associated with it are also uninstalled


2:) I dont think i know the answer

3:) I gave the command for that in my previous comment.The command reconfigures dkms modules for virtualbox according to the new kernel.

---

### Post by Statia on 2012-09-10
> **ranger1021994 said:**
> 

3:) I gave the command for that in my previous comment.The command reconfigures dkms modules for virtualbox according to the new kernel.

But should the reconfiguration not happen automagically, just like happens with video drivers? Now I'll have to remember to do that myself every time there is a kernel update.

---

### Post by Statia on 2012-09-22
So yesterday, I installed 3.20.31, VirtualBox stops working. I did not even remove an older kernel. I had to reinstall VirtualBox. This is inconvenient. Is there no way to make DKMS take care of the VirtualBox modules, just like happens with the nvidia module?

---

### Post by Statia on 2012-10-01
Apparently not.

---

### Post by idlemind324 on 2012-10-02
Are the kernel upgrades happening through an Ubuntu package or are you compiling and adding these kernels yourself?

---

### Post by Statia on 2012-10-04
Ubuntu packages, via update manager.

---

### Post by Oliphant on 2012-10-08
I've had this happen to me a couple times now and the simple fix that I've been using is:

sudo apt-get install dkms
sudo /etc/init.d/vboxdrv setup

---

### Post by Statia on 2012-10-08
```
statia@quokka:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
statia@quokka:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
```I think I already tried that once, as I usually Google first and only ask here if I can't solve it myself.

So why does that work for you, but not for me?
Sometimes I think I should call my box Murphy...

---

### Post by Kufa61 on 2012-10-13
I have this same problem after every kernel update my virtualbox stops working.  After searching I found this solution from this [here]("http://ubuntuforums.org/showthread.php?t=1885936") 

> sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

not convenient  but at least I don't have to re-install virtualbox and the two OS's I have in virtual machines.

I've created a bash script to execute these commands, now a little more convenient.

---

### Post by Kufa61 on 2012-10-15
> **Statia said:**
> ```
statia@quokka:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
statia@quokka:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
```I think I already tried that once, as I usually Google first and only ask here if I can't solve it myself.

So why does that work for you, but not for me?
Sometimes I think I should call my box Murphy...

I have found that you have to remove the dkms package first then install this forces the kernal module to recompile and fixes the problem with VirtualBox.

---

### Post by Statia on 2012-10-22
> **Kufa61 said:**
> I have found that you have to remove the dkms package first then install this forces the kernal module to recompile and fixes the problem with VirtualBox.

I think I already reinstalled DKMS once, but I'll give it a(nother) try. Thanks.

---

### Post by nowashburn on 2012-10-22
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

worked for me

---

### Post by dmahoon on 2012-10-23
Yes the same thing happened to me yesterday.  I haven't used Virtualbox for a few weeks and went to use it yesterday and had the same problem with the kernel.  
I spent a couple of hours trying to sort it out to no avail.  This was after spending quite a bit of time getting it installed in the first place.....this is totally frustrating.  I'm going to sent virtualbox to the bin and just use a dual boot.  I know it takes time to change from one system to another but it doesn't take that much time.  A lot less than the time I've spent trying to get a simple upgrade worked out.  Hey virtualbox...... this is just not acceptable....it's 2012 get it sorted.

DM

---

### Post by dmahoon on 2012-10-23
Well I used the two simple commands and virtualbox now works!

sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms

Note to self.....remember these commands.

DM

---

### Post by Statia on 2012-11-15
Well, just upgraded to 3.2.0-33 and this time VirtualBox kept working, so it seems solved. I'll mark this thread as solved and would like to thank everyone for their input.

---

