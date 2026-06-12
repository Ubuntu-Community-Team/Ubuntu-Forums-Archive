---
title: "Problem installing Virtualbox Guest Additions"
date: 2010-09-04
forum: Virtualisation
---

### Post by seldon12 on 2010-09-04
Hi, I have a problem with VirtualBox that I would like to solve, but I'm not able to. 

The problem is as follow: on an Ubuntu Jaunty host (386), I have installed VirtualBox OSE (2.1.4) from APT in order to run Ubuntu Lucid on a VM.

I was able to setup a VM and install Lucid on it, but I can't get proper full screen behaviour for the window running the Lucid VM;
searching around, I discovered that I had to install Virtualbox Guest Additions on the virtualized environment.  Following the directions I found on the web, I took the following steps:

* on the VM, I installed, via APT, the **build-essential** and **dkms** packages;
* I downloaded the Guest Additions ISO from the VirtualBox menu for the VM (Devices >> Install Guest Additions);
* I mounted the ISO image on the guest
* I run the installation script shipped with the CD image, namely /media/cdrom/VBoxLinuxAdditions-x86.run

Now, the script start running, but it fails saying:

```
'Building the VirtualBox Guest Additions kernel module...
Building the shared folder support kernel module...
Unable to build the kernel module. See the log file /var/log/vboxadd-install.log
for more details.'
```Any ideas ?

Thanks in advance for any answer.

---

### Post by Toz on 2010-09-04
You also need the linux headers:

sudo apt-get install linux-headers-$(uname -r)

/ToZ

---

### Post by seldon12 on 2010-09-04
> **Toz said:**
> You also need the linux headers:

sudo apt-get install linux-headers-$(uname -r)

/ToZ

If you mean on the guest, I've the Linux headers already installed:

```
sudo apt-cache policy linux-headers-$(uname -r)

linux-headers-2.6.32-24-generic:
  Installed: 2.6.32-24.42
  Candidate: 2.6.32-24.42
```

---

### Post by howefield on 2010-09-04
> **seldon12 said:**
> See the log file /var/log/vboxadd-install.log
for more details.

So what did the log say ?

---

### Post by seldon12 on 2010-09-05
> **howefield said:**
> So what did the log say ?

The log file is in attachment (I added the extension .txt).

---

### Post by Toz on 2010-09-05
Out of curiosity, how did you get the 2.6.32 kernel onto jaunty? Did you compile your own kernel? I don't have a jaunty install here to check myself, but from what I could see from searching the internet, jaunty only ever used the 2.6.28 kernels. The log file seems to indicate that your system is missing some kernel configuration files.

Also, what does /var/lib/dkms/vboxvfs/2.1.4/build/make.log say?

You might want to try installing the virtualbox additions package from apt as well and see if that works (sudo apt-get install virtualbox-ose-additions).

/ToZ

---

### Post by Dedoimedo on 2010-09-05
You may want to install the build-essential package in the guest os.
Dedoimedo

---

### Post by seldon12 on 2010-09-06
> **Toz said:**
> Out of curiosity, how did you get the 2.6.32 kernel onto jaunty? Did you compile your own kernel? I don't have a jaunty install here to check myself, but from what I could see from searching the internet, jaunty only ever used the 2.6.28 kernels. 

That version of the kernel refers to the guest OS (Lucid), not the host one (Jaunty).


> **Toz said:**
> 
The log file seems to indicate that your system is missing some kernel configuration files.

Also, what does /var/lib/dkms/vboxvfs/2.1.4/build/make.log say?


I attached it.

> **Toz said:**
> 
You might want to try installing the virtualbox additions package from apt as well and see if that works (sudo apt-get install virtualbox-ose-additions).
/ToZ

If you mean on the host OS, that package doesn't exist in Jaunty.

---

### Post by seldon12 on 2010-09-06
> **Dedoimedo said:**
> You may want to install the build-essential package in the guest os.
Dedoimedo

As I said in the initial post, I have already done that ;-)

---

### Post by seldon12 on 2010-09-06
It seems I have managed to solve the problem, simply by installing the package **virtualbox-ose-guest-x11** on the **guest** OS.

Thanks for your help .

---

