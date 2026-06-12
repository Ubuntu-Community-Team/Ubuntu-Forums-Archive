---
title: "The strangeness of the NVIDIA drivers"
date: 2007-06-30
forum: The Cafe
---

### Post by jamyskis on 2007-06-30
I've been using Ubuntu for three years now. In this time there's been a concerted effort on the part of the Ubuntu team to make installing graphic drivers easier. I myself had been using the nvidia-glx (and recently, the nvidia-glx-new) packages for a while. And while they're intended to make things easier, I've never had anything but problems with them. The deb package neglects to run nvidia-xconfig after installation (so I have to do it myself, and it's a good job I know how to do this), and often the kernel modules are mismatched, and so I have to run dpkg-reconfigure to get my nv driver back. Not to mention the hassle I go through with removing nvidia-glx, removing the restricted modules, reinstalling the whole thing and hoping to God it works. Which it usually does after about an hour's work. Envy hasn't really sorted this problem out.

Recently I (re)discovered (I used to do it when I was a Mandrake user) the wonders of the method that was apparently so difficult. Download the NVIDIA driver from the NVIDIA website, /etc/init.d/gdm stop, chmod +x, run the driver, /etc/init.d/gdm restart. If I get a kernel update, I just reinstall, because the driver automatically creates a new kernel module.

Why is Ubuntu putting so much effort into trying to make graphics driver installation easier when the manual method is that simple?

---

### Post by Outrunner on 2007-06-30
Unfortunately, the manual method doesn't work for everyone(read: me), so I guess it's good to have more than one way to do it

---

### Post by ~LoKe on 2007-06-30
Lots of people are afraid of the command line.  The idea behind nvidia-glx is to make it as simple as yet another package installation.  By refining and perfecting this, driver installation would be a breeze.  If you're willing to work past the occasional x server error, manually installing is the best way.  That's how I do it, anyways,  I should note that there are sometimes problems doing it this way, too.

In my case, even after doing the whole DISABLED_MODULES="nv" bit, I still have to reinstall the driver upon reboot.

---

### Post by igknighted on 2007-06-30
> **jamyskis said:**
> I've been using Ubuntu for three years now. In this time there's been a concerted effort on the part of the Ubuntu team to make installing graphic drivers easier. I myself had been using the nvidia-glx (and recently, the nvidia-glx-new) packages for a while. And while they're intended to make things easier, I've never had anything but problems with them. The deb package neglects to run nvidia-xconfig after installation (so I have to do it myself, and it's a good job I know how to do this), and often the kernel modules are mismatched, and so I have to run dpkg-reconfigure to get my nv driver back. Not to mention the hassle I go through with removing nvidia-glx, removing the restricted modules, reinstalling the whole thing and hoping to God it works. Which it usually does after about an hour's work. Envy hasn't really sorted this problem out.

Recently I (re)discovered (I used to do it when I was a Mandrake user) the wonders of the method that was apparently so difficult. Download the NVIDIA driver from the NVIDIA website, /etc/init.d/gdm stop, chmod +x, run the driver, /etc/init.d/gdm restart. If I get a kernel update, I just reinstall, because the driver automatically creates a new kernel module.

Why is Ubuntu putting so much effort into trying to make graphics driver installation easier when the manual method is that simple?

Same thing with the ATI driver.  ATI goes through all this trouble to make a nice GUI wizard to just go *click* *click* through and the driver is installed, but then you never see that installing from the repos.  I think in the end it comes down to choice.  New users don't want to worry about chmod commands, or dropping to runlevel three or anything like that.  They want it to work, with them not needing to know anything.  This is why Ubuntu tries to automate it, but yes, it is a buggy process at times and could certainly be better.

---

### Post by Extreme Coder on 2007-06-30
> **jamyskis said:**
> I've been using Ubuntu for three years now. In this time there's been a concerted effort on the part of the Ubuntu team to make installing graphic drivers easier. I myself had been using the nvidia-glx (and recently, the nvidia-glx-new) packages for a while. And while they're intended to make things easier, I've never had anything but problems with them. The deb package neglects to run nvidia-xconfig after installation (so I have to do it myself, and it's a good job I know how to do this), and often the kernel modules are mismatched, and so I have to run dpkg-reconfigure to get my nv driver back. Not to mention the hassle I go through with removing nvidia-glx, removing the restricted modules, reinstalling the whole thing and hoping to God it works. Which it usually does after about an hour's work. Envy hasn't really sorted this problem out.

Recently I (re)discovered (I used to do it when I was a Mandrake user) the wonders of the method that was apparently so difficult. Download the NVIDIA driver from the NVIDIA website, /etc/init.d/gdm stop, chmod +x, run the driver, /etc/init.d/gdm restart. If I get a kernel update, I just reinstall, because the driver automatically creates a new kernel module.

Why is Ubuntu putting so much effort into trying to make graphics driver installation easier when the manual method is that simple?
You forgot another nice feature Mandriva has which is DKMS([SIZE=-1]**Dynamic Kernel Module Support,**from Dell) From linux.dell.com:
> [/SIZE]  It is designed to create a framework where kernel 			dependent module source can reside so that it is very easy to rebuild modules as you upgrade kernels. 			This will allow Linux vendors to provide driver drops without having to wait for new kernel releases 			while also taking out the guesswork for customers attempting to recompile modules for new kernels.
So, for example, you install dkms-nvidia9700(or any other version), which contains the source for the kernel module. the dkms package depends on the nvidia driver. when both are installed, and then you restart, you will see the module being compiled for your kernel(which happens one time only). If you upgrade your kernel, and then restart, the module will be recompiled, avoiding some of the panics :)

---

### Post by DeadSuperHero on 2007-06-30
Another thing you can do is just take out the card, then put it back in. Doing that did wonders for me when I had problems with it.

---

### Post by beniwtv on 2007-06-30
Well, I don't know if it's me, but I never had problems the people here are talking about.

I use the nvidia-glx (Geforce 4 MX) un my edgy box, and nvidia-glx-new on my Feisty laptop (Geforce Go 6150).

I never had problems with the kernel module mismatch. And I never had problems when a kernel was updated.

Also, I installed Ubuntu for a friend, which has a feisty laptop with a Geforce 7300, and he also never had problems.

I think when you are using a fresh install, from the official release CD, you don't have any problems with that, as the kernel won't be updated that much.

But then it could be me being lucky also...

---

### Post by Polygon on 2007-06-30
> **igknighted said:**
> Same thing with the ATI driver.  ATI goes through all this trouble to make a nice GUI wizard to just go *click* *click* through and the driver is installed, but then you never see that installing from the repos.  I think in the end it comes down to choice.  New users don't want to worry about chmod commands, or dropping to runlevel three or anything like that.  They want it to work, with them not needing to know anything.  This is why Ubuntu tries to automate it, but yes, it is a buggy process at times and could certainly be better.

um, when the kernel gets updated,the updated fglrx drivers are included in the update

---

