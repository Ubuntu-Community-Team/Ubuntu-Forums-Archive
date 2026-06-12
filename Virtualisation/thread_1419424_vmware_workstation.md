---
title: "vmware workstation"
date: 2010-03-01
forum: Virtualisation
---

### Post by davarse on 2010-03-01
hey im not really good at computer, and can anyone help me to install vmware workstation v7 in my notebook. im running ubuntu jaunty at the moment.

---

### Post by pirateghost on 2010-03-01
> **davarse said:**
> hey im not really good at computer, and can anyone help me to install vmware workstation v7 in my notebook. im running ubuntu jaunty at the moment.
i assume you purchased workstation with a license?

---

### Post by mishfit on 2010-03-02
It's a very straightforward install until you get to the configure script...is that what you are having trouble with?

before you get to the configure script, installation is simply a matter of extracting the contents of your installer, reading the text file and following the directions. Run an install script as the super user ("*sudo ./vmware-install.pl*"...a Perl script file. This can be easily done via tar or using the nautilus front end (the explorer equivalent).

at some point you will be asked if you want to configure the installation. You will (one hopes) indicate no (as in, do not configure...yet).

Then go to google and search for "vmware patch ubuntu" (you will find one that matches your kernel, I promise)...any more questions, post 'em here...

As far as the license issue, there's no way for me to verify you have one of your own, I can only hope that you do.

---

### Post by pirateghost on 2010-03-02
> **mishfit said:**
> 

Then go to google and search for "vmware patch ubuntu" (you will find one that matches your kernel, I promise)...any more questions, post 'em here...


i do not recall having to do this in workstation 7, although it has been many months since i installed it on my laptop

---

### Post by mishfit on 2010-03-02
you know what, you are right about that (I don't have experience with workstation 7)...I had to run the patch under workstation 6.5...if that is fixed, then great

---

### Post by HermanAB on 2010-03-02
Well, first of all you got to install the development environment, since VMware needs to compile itself.  You can get that by installing the kernel headers package for your running kernel and hope that everything is OK.  This not guaranteed to work.

Alternatively you can install the kernel source and compile the kernel, install it and reboot, then install VMware.  This latter method takes longer but is guaranteed to work.

---

### Post by TJet1.8 on 2010-03-02
> **pirateghost said:**
> i assume you purchased workstation with a license?

1.) Ditto!!!!  ^^^

2.) So...first ensure you have the build environment installed:
sudo apt-get install gcc build-essential linux-headers-$(uname -r)

3.) While you're at it, make sure your distro is up to date:
sudo apt-get update
sudo apt-get upgrade

4.) Make sure you have execute rights for the VMware installation file:
sudo chmod +x ./VMware-Workstation-Full-7.0.1-227600.i386.bundle

5.) Install VMware Workstation:
sudo ./VMware-Workstation-Full-7.0.1-227600.i386.bundle

6.) Reboot

7.) Enjoy :)

---

### Post by ilhan805 on 2010-08-14
there is no problem to the step five..
./VMware-Workstation-Full-7.0.1-227600.i386.bundle
Extracting VMware Installer...done.
Here, &#305; m folloving the instructions
Finally it asks me to install vmware &#305;m hitting "ok"
Result is "installation was ubsuccessful"
and in terminal it says "File "/usr/lib/vmware-installer/1.1/python/lib/sqlite3/dbapi2.py", line 0
SyntaxError: ('unknown encoding: ISO-8859-1', ('/usr/lib/vmware-installer/1.1/python/lib/sqlite3/dbapi2.py', 0, 0, None)"

So what is the problem?

---

