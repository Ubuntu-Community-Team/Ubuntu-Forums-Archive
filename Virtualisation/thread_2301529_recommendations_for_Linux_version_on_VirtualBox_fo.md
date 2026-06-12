---
title: "recommendations for Linux version on VirtualBox for corpus generation"
date: 2015-11-03
forum: Virtualisation
---

### Post by ankur9 on 2015-11-03
Hello,

I am new to Linux, and I am going to install a Linux version of OS onto an external hard drive, so that I can run it through Oracle VirtualBox. From what I saw on the Internet of system requirements, 512 MB of RAM should be enough (I have 1.9 GB of RAM on my system in total). However, I do have a question about the external hard drive on which I would be mapping the Linux OS: is an 8 GB pen drive enough for this purpose? Or should I buy an external drive with bigger capacity? Also, should I look for any other parameter while buying the hard drive?

I would also like suggestions about the flavour of Linux recommended to install, if any. My usage will be initially limited to running Perl, R and bash scripts for corpus generation and processing: I am not likely to do huge corpus searches for the time being. (I think once I reach that stage, I may eventually buy another laptop, Linux having all of it to itself.)

I have yet one more question: as I will be running everything through a virtual machine, what happens to the files I create: do they get destroyed when I exit (or saved if I save the machine state in VM?)? Is it possible to save them somewhere that I can access them later for both read and write from my Windows environment? (I am of course the administrator as well of my machine.) What about anything I install (say, Lynx browser) in the Linux environment?

Thanks a lot in advance!

---

### Post by Bucky Ball on 2015-11-03
> **ankur9 said:**
> ... I am going to install a Linux version of OS onto an external hard drive, so that I can run it through Oracle VirtualBox.

Welcome. Let's stop right there. You are going to install Ubuntu and then use it as a virtual machine in virtual box? This is not possible. With a virtual machine you have a host and a client. In the host, let's say the host is Windows but it could be any other OS, you install Virtualbox (or another virtual machine app). You then install the second OS as a client virtual machine using Virtualbox in the host. The client is installed from the ISO directly or from an install media, USB or DVD. 

There is no way I am aware of of running a virtual machine using an OS already installed on a hard drive. Not really the way it works. A virtual machine is so you can avoid installing the second OS to a hard drive.

Sorry if I've misunderstood, but I'm thinking there is some confusion somewhere along the way. :)

As for which one to use, install Virtualbox in whatever host OS you are using, download some ISOs, perhaps Ubuntu, Xubuntu and Kubuntu, or whatever you fancy, then run the ISO files as virtual machines using Virtualbox. That's it. See which one you like then you can set it up permanently so you won't lose data on reboot, but that is the next step. See if you can get the test virtual machine running from an ISO in Virtualbox to start. Let us know if/when you get stuck.

Good luck.

---

### Post by ajgreeny on 2015-11-03
> From what I saw on the Internet of system requirements, 512 MB of RAM should be enough (I have 1.9 GB of RAM on my system in total).
You also need to think again about the hardware needed to run any virtual machine efficiently and quickly enough for it to be useful.

You can not install any virtual OS on hardware that would not run the OS as a bare metal installation, and 512MB ram is not enough to run any of the current *ubuntu family of OSs in a way that would be useful, whether as a VM or bare metal install.

I use VBox on my Xubuntu 14.04 main system and have 8 VMs available.  The machine has 8GB ram and all my VMs are set to use half of that, ie 4GB ram, which may seem a lot for an OS such as Lubuntu, one of the 8, but it shows what is possible.  I also run Linux Mint, Fedora-22, Debian-8, and test the newest versions of Ubuntu as they become available in testing mode.

---

### Post by SeijiSensei on 2015-11-03
If you intend to work only in text-mode, which might apply if the use case is writing scripts in R, perl, and bash, then you can install the server version of Ubuntu into a 512K virtual machine.  Any version with a GUI is going to require more memory than that.  The smallest image I have used successfully is 1G, but my machines have enough memory to allocate 2G. 

You can store the virtual machines you create on the external drive, but you'll be booting from the images, not from that drive.  VB needs to be installed with the rest of the host operating system.  Depending on the speed of the external drive, and the amount of memory available, you might find that arrangement too slow compared with storing the virtual images on the host's primary drive.  However an 8 GB USB drive will probably be too small for any decently sized virtual machine image.  I do have an Ubuntu Server 14.04 image of about 6GB in size.  Most of my images with a GUI are pushing 10GB or more.  I'd get a 32G drive at a minimum, and at least a 64G or larger drive if you expect to be creating multiple virtual machines.

Frankly, I'd go buy at least another 2G of memory before you start out on this endeavor.  Memory is pretty cheap these days and on a machine like yours well worth the investment.

---

### Post by ankur9 on 2015-11-05
Hello,

Thanks for your responses: sorry for being confused about the way I expressed myself.

So I have Windows on my computer currently, and VirtualBox installed. I plan to load an iso of a Linux OS in an external drive, so I can run Linux in the VM. I am actually using a very little version of Linux called TinyCore through this method, but it's too little or maybe I'm too inexperienced to do many things. That's why I thought of a bigger Linux: but my RAM is only 2 GB. Of course, I could upgrade it, or buy a new computer, but I was thinking that that much RAM could be enough: it isn't? Inside the VirtualBox, I will be using the terminal window to run scripts plus a Firefox browser so that my scripts could execute some searches, and something like Nano or Gedit to edit scripts: not much else.

Thanks again!

---

### Post by SeijiSensei on 2015-11-05
If you are going to run Linux in a VM, you need to install Linux *into* the VM, not run it from an external drive.  The VM is exactly what it says it is, a virtual "machine." Basically it's another computer running on top of the host computer.  The only difference is that the machine's "hard drive" is actually just a large file stored on the host.  So you need to have the complete version of Linux installed inside that file.  Usually these images are stored in /home/user/VirtualBox VMs/, but you could move the image onto the external drive and set up a symlink to it in your home directory, or repoint the VirtualBox manager to look to the external drive for its images.

As I wrote before you probably can get by with a 512MB memory image for the virtual machine if you are running only in text-mode.  Partly the answer depends on what version of Windows you're running.  XP can run successfully in 1280 MB leaving you 768MB for the virtual machine.  Win7 and later are more memory hungry.  I've found Win7 needs at least 1536MB to perform decently, leaving you 512MB for the virtual machine.

---

### Post by Bucky Ball on 2015-11-05
> **SeijiSensei said:**
> If you are going to run Linux in a VM, you need to install Linux *into* the VM, not run it from an external drive.  The VM is exactly what it says it is, a virtual "machine." Basically it's another computer running on top of the host computer.

This is it. When you say you are going to 'load' the ISO onto an external drive, do you mean install? You don't need to. You 'down-load' the ISO to anywhere you want and the install it as a virtual machine using Virtualbox, or whatever you're using for you VMs.

So, you only need the ISO. You then launch Virtualbox and install a virtual machine using the ISO *_file_*, not an OS installed from the ISO, as the source. 

Just in case it isn't clear ... :)

---

### Post by ankur9 on 2015-11-08
Yes, I am going to install the Linux OS in a VM (I already did so for TinyCore, as I said earlier), and I will just download the ISO to an external USB drive. Sorry for my confused terminology! I am running Windows 7 on my computer: so if I assign 512 MB RAM to the VM, that's not good enough for running a lightweight Linux OS? I am running TinyCore right now, but it's too lightweight.

I am going to do mainly text-based things inside the Linux, but all that will be running in a VM in a Windows GUI environment.

---

### Post by Bucky Ball on 2015-11-08
It depends on what distro you are going to run as to whether 512Mb RAM will be sufficient. Lubuntu might run but 1Gb will get Lubuntu running fine. Probably Xubuntu also.

---

### Post by ankur9 on 2015-11-12
Thanks, Bucky Ball! Any suggestions for a distro that can run fine with 512 MB RAM?

---

### Post by SeijiSensei on 2015-11-12
Try installing Ubuntu Server and adding any bits and pieces you might need via apt.  The server version has no GUI.

---

### Post by memilanuk on 2015-11-13
I was kind of wondering about this myself... in the past I've ran Virtualbox on the host OS (both Ubuntu 14.04 and Win 7), but had the files for the VMs in a directory on a secondary hard drive i.e. not stored in the user's home directory, which seems to be the default.  

I've got a new laptop on the way (current one is dying) and it has a 256GB SSD... rather than trying to shoe-horn Ubuntu and Windows 10 in side by side (did it before with Win7, felt cramped, didn't like it) on the SSD, I was curious as to whether it would be feasible to 'run' the guest OS's from an external USB 3.0 drive...?  Not sure if that is quite what the OP intended, but it sounds pretty close.

---

### Post by SeijiSensei on 2015-11-13
Sure, you can store the VM images on an external drive.  I'd imagine performance will suffer a bit though.  Allocating more memory to the VM might help with that since Linux will cache a larger amount of the disk transactions.

In the Oracle VB manager go to File > Preferences > General to set the "default machine folder."

---

