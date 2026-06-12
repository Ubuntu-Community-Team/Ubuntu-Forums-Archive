---
title: "Getting Xen installed, Ubuntu 10.4"
date: 2010-04-29
forum: Virtualisation
---

### Post by jexxie on 2010-04-29
Fresh install, trying to install xen:
root@host:~# apt-get install ubuntu-xen-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-xen-server: Depends: xen-tools but it is not installable
E: Broken packages

Where can I follow up to get this fixed?

---

### Post by TheFu on 2010-04-30
I was under the impression the last few months that Xen was not on the Ubuntu roadmap and this 10.04 was all about KVM for virtualization. [http://www.ubuntu.com/news/ubuntu-10.04-server-edition](http://www.ubuntu.com/news/ubuntu-10.04-server-edition) Shows Xen in a client position, if I'm reading that correctly.

I expected to switch from Xen to KVM with a 10.04 server install.  I'd really, really, like to be wrong.

---

### Post by OpenTS on 2010-05-01
> **jexxie said:**
> Fresh install, trying to install xen:
root@host:~# apt-get install ubuntu-xen-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-xen-server: Depends: xen-tools but it is not installable
E: Broken packages

Where can I follow up to get this fixed?
Same problem.
even with:

aptitude install ubuntu-xen-serverReading package lists... Done

Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  ubuntu-xen-server 
The following NEW packages will be installed:
  python-dev{a} python-xen-3.3 python2.6-dev{a} xen-docs-3.3 
  xen-hypervisor-3.3 xen-utils-3.3 
The following packages will be upgraded:
  libpython2.6 python2.6 python2.6-minimal 
3 packages upgraded, 7 newly installed, 0 to remove and 329 not upgraded.
Need to get 11.7MB of archives. After unpacking 20.8MB will be used.
The following packages have unmet dependencies:
  ubuntu-xen-server: Depends: xen-tools which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
ubuntu-xen-server [Not Installed]

Leave the following dependencies unresolved:
xen-utils-3.3 recommends libc6-xen
Score is -10081

Accept this solution? [Y/n/q/?]

So Xen is not supported :mad: !!

---

### Post by vru on 2010-05-02
well, Xen 4 was release beginning of April and it supports the current kernel used in Ubuntu 10.4 i thought it would be in by this time, i guess i have to wait until it becomes officially in the mainstream kernel. :(

there is a howto on the xen blog if anybody interested to experiment, its a bit old since it was done with beta release of ubuntu 10.4 and xen release candidate 8 
[http://blog.xen.org/index.php/2010/03/26/steps-to-try-xen-4-0-0-release-candidate-8-on-ubuntu-lucid-10-04-64-bits/](http://blog.xen.org/index.php/2010/03/26/steps-to-try-xen-4-0-0-release-candidate-8-on-ubuntu-lucid-10-04-64-bits/)

---

### Post by jonaternet on 2010-07-16
Hello, the package for debian sid works in ubuntu 10.4, and you can[ get it here]("http://packages.debian.org/sid/all/xen-tools/download") !

---

### Post by sh1ny on 2010-07-17
AFAIK, Xen is not supported on Ubuntu since 9.04 or so ( as dom0 ). KVM is the way to go, if you want to be using ubuntu as virt host.

---

### Post by naelq on 2010-07-17
hi, if i may ask, is there any obvious reason why choosing Xen over KVM now, i mean with the current state of KVM? (of course, besides the fact that you already have the images of the VM's & you want to upgrade to newer ubuntu..)


nael

---

### Post by juancarlospaco on 2010-07-18
*KVM or LXC*

---

### Post by OpenTS on 2010-07-21
> **naelq said:**
> hi, if i may ask, is there any obvious reason why choosing Xen over KVM now, i mean with the current state of KVM? (of course, besides the fact that you already have the images of the VM's & you want to upgrade to newer ubuntu..)


nael

I had a hard time with KVM on ProLiant BL465c G5
The network and the disk  I/O performance gave me the main issues, with Xen instead I've never had any kind of problems at all.

---

### Post by TheFu on 2010-07-21
> **OpenTS said:**
> The network and the disk  I/O performance gave me the main issues, with Xen instead I've never had any kind of problems at all.

I had exactly the same issues with KVM as you. We're still running Xen on Hardy on our production systems while KVM performance matures. I'm cautiously hopeful that KVM performance will improve during the next 6 months to match either ESXi or Xen.

---

### Post by salemboot on 2010-08-07
sudo apt-get install bridge-utils libxen3 linux-image-2.6.32-24-server linux-image server linux-server python-dev python-xen-3.3 python2.6-dev xen-hypervisor-3.3


wget [http://ftp.us.debian.org/debian/pool/main/x/xen-tools/xen-tools_4.2~beta1-1_all.deb](http://ftp.us.debian.org/debian/pool/main/x/xen-tools/xen-tools_4.2~beta1-1_all.deb)

sudo dpkg -i xen-tools_4.2~beta1-1_all.deb


for the adhd like me :)

---

### Post by robotmakesmusic on 2010-08-18
> **salemboot said:**
> sudo apt-get install bridge-utils libxen3 linux-image-2.6.32-24-server linux-image server linux-server python-dev python-xen-3.3 python2.6-dev xen-hypervisor-3.3


wget [http://ftp.us.debian.org/debian/pool/main/x/xen-tools/xen-tools_4.2~beta1-1_all.deb](http://ftp.us.debian.org/debian/pool/main/x/xen-tools/xen-tools_4.2~beta1-1_all.deb)

sudo dpkg -i xen-tools_4.2~beta1-1_all.deb


for the adhd like me :)

Thank you sir, just what the doctor ordered. 

Though I did have to toss a 

sudo aptitude install debootstrap 

into the mix, tell it no to uninstalling xen-tools (don't quit at this point) and go with the second, less recommended option of actually installing debootstrap & related like I had requested. That allowed the dpkg install of xen-tools to install correctly and without errors.

---

### Post by SiggSauer on 2010-10-22
Hey,

We are planning to migrate our Xen vm's to a new server with the latest version of Xen Server. our Name Server runs on Ubuntu Server 10.4.1 x64, at this moment paravirtualization does'nt work and the Xen tools can't be installed. Note it has an EXT4 boot partition atm. 

So do I need to reinstall with the EXT3 file system or can I enable paravirtualization without to much trouble on the new server with EXT4?

---

### Post by agent8131 on 2010-11-27
> **naelq said:**
> hi, if i may ask, is there any obvious reason why choosing Xen over KVM now, i mean with the current state of KVM? (of course, besides the fact that you already have the images of the VM's & you want to upgrade to newer ubuntu..)


The obvious reasons are that Xen can run on older hardware and that Xen has better performance.  Xen has much better performance than KVM, at least on the hardware I've got.  With AMD and Intel optimizing their AMD-V/VT-X instruction sets perhaps this is not as big of a difference in current processors but I do not have the ability to test.

---

### Post by speculatrix on 2011-02-03
> **robotmakesmusic said:**
> Thank you sir, just what the doctor ordered. 

Though I did have to toss a 

sudo aptitude install debootstrap 

into the mix, tell it no to uninstalling xen-tools (don't quit at this point) and go with the second, less recommended option of actually installing debootstrap & related like I had requested. That allowed the dpkg install of xen-tools to install correctly and without errors.

/me too!

thanks, just what I needed!

---

