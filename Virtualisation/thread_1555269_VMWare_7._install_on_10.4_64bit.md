---
title: "VMWare 7.? install on 10.4 64bit"
date: 2010-08-17
forum: Virtualisation
---

### Post by psycdoc on 2010-08-17
Ok I just discovered Ubuntu and am a totally newbie to the OS. I want to install VMWare version 7.?. I am having problems with the install and most likely this is because I am totally new to this. Can anyone provide detailed instructions on how to install it.

Thanks in advance for your assistance...

---

### Post by TJet1.8 on 2010-08-17
Well...it's kinda hard to help you without some explanation of error messages and/or symptoms.

"I am having problems with the install..." doesn't give us alot of information to go on...:lolflag:

As you are new to Ubuntu, I would have to guess that you haven't installed all the required components in Ubuntu to compile the VMware modules.

So...let's try this. In order for VMware to compile the modules, you need to have the C compiler, Linux Header files, and build essential components installed in Ubuntu.

Run the following commands in a terminal window:

sudo apt-get install gcc build-essential kernel-headers-$(uname -r) dkms

Once installed, try installing VMware Workstation again in a terminal window:

sudo ./VMware-Workstation-Full-7.1.1-282343.x86_64.bundle (or whatever version of VMware Workstation install file you have).

Good Luck :popcorn:

---

