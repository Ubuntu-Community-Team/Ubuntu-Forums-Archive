---
title: "Virtual box ose - modprobe vboxdrv?"
date: 2010-06-09
forum: Virtualisation
---

### Post by chihwahli on 2010-06-09
Dear Ubuntu users,

I am clueless about installing Virtualbox ose from the Ubuntu package respository.
What I did so far is:

I only have one kernel running, other kernels are removed by using synaptic.
I am running Xubuntu 10.0.4 LTS 32 bit kernel version 2.6.32-22-generic-pae
 64 bit Intel core duo

$ apt-get install virtualbox-ose-dkms
$ apt-get install virtualbox-ose

I see during the install of the package 'virtualbox-ose' that it compiles for i686 architecture.

When I try to run a virtual machine I get error screens:

window 1:
failed to open a session for virtual machine window7
virtual machine window7 has terminated unexpectedly during startup
details: 
result code: NT_ERROR_FAILURE (0x80004005)
component: machine
interface: Imachine {9904f50-dd10-40d3-889b-ddf79f1e95e}

window 2:
kernel driver not installed (rc=-1908)
Please install the virtualbox-ose-dkms package and execute 'modprobe vboxdrv' as root

window3:
I tried $ sudo modprobe vboxdrv
Then I get the error 'FATAL: VBOXDRV not found' 

What can I do to run virtual box?? I am really clueless...:confused:

---

### Post by TheFu on 2010-06-09
You may want to use aptitude or synaptic to be certain all the  dependencies were installed too.

If that doesn't fix the issue, I had a post-install error that prevented vbox from doing anything useful, but it still let me use the GUI. My issue was with the OSE on a 64-bit Ubuntu 10.04 install.  It turned out the installation didn't create the userid or vboxusers group or add my uid to that group. Since you've already run vbox already, the best answer is to wipe your ~/.Virtualbox/ directory, then create the group and user, then add yourself to the group and try again.  Here's a blog entry with more details [http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid](http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid) .

Good luck.

---

### Post by sanderh79 on 2010-06-11
Try this:
 
sudo insmod /lib/modules/2.6.32-22-generic-pae/updates/dkms/vboxdrv.ko
sudo modprobe vboxdrv
sudo modprobe vboxnetflt
 
Replace the 2.6.xx for whatever you have. You might also want to try:
 
sudo vboxmanage startvm window7 --type headless
 
I use this then rdp into the xp machine in the event it crashed or shutdown improperly.

---

### Post by chihwahli on 2010-06-15
> **sanderh79 said:**
> Try this:
 
sudo insmod /lib/modules/2.6.32-22-generic-pae/updates/dkms/vboxdrv.ko
sudo modprobe vboxdrv
sudo modprobe vboxnetflt
 
Replace the 2.6.xx for whatever you have. You might also want to try:
 
sudo vboxmanage startvm window7 --type headless
 
I use this then rdp into the xp machine in the event it crashed or shutdown improperly.

I do not have ../updates directory.
I did a $ find / -name 'vboxdrv.ko'  It cannot find this file.

---

### Post by chihwahli on 2010-06-15
> **TheFu said:**
> You may want to use aptitude or synaptic to be certain all the  dependencies were installed too.

If that doesn't fix the issue, I had a post-install error that prevented vbox from doing anything useful, but it still let me use the GUI. My issue was with the OSE on a 64-bit Ubuntu 10.04 install.  It turned out the installation didn't create the userid or vboxusers group or add my uid to that group. Since you've already run vbox already, the best answer is to wipe your ~/.Virtualbox/ directory, then create the group and user, then add yourself to the group and try again.  Here's a blog entry with more details [http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid](http://jdpfu.com:82/2010/05/23/installation-of-virtualbox-ose-3-1-x-on-ubuntu-10-04-lucid) .

Good luck.

My pwd is /usr/bin
In here is a file an executable file named 'virtualbox' 
If I execute it I get the error message:

the character device /dev/virtualboxdrv does not exist 
pleasae install the virtualbox-ose-dkps package and the appropiate headers, mostliky
linux-headers-generic

I then did $ apt-get install linux-headers-generic .... rebooting.... does not work yet...
I tried the dep file from virtual.org and let my package manager open it...But it does not work also.
Does someone know how to fix this? Or know a virtual machine that let's me install a guest OS inside linux without much problems?

---

### Post by sanderh79 on 2010-06-16
I just updated and the vboxdrv.ko appears to be missing after that. I couldn't load my vm's getting the well known error message. 
I did this to correct the problem:
 
- using synaptic, remove all virtualbox packages
- wget [http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb) (or whatever is the latest version)
- dpkg -i <tab or virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb>
 
Start Virtualbox using Applications -> System Tools -> Oracle VM Virtualbox and my xp/server2k3 vm's were up and running again.

---

### Post by chihwahli on 2010-06-16
> **sanderh79 said:**
> I just updated and the vboxdrv.ko appears to be missing after that. I couldn't load my vm's getting the well known error message. 
I did this to correct the problem:
 
- using synaptic, remove all virtualbox packages
- wget [http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb]("http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467%7EUbuntu%7Elucid_i386.deb") (or whatever is the latest version)
- dpkg -i <tab or virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb>
 
Start Virtualbox using Applications -> System Tools -> Oracle VM Virtualbox and my xp/server2k3 vm's were up and running again.


Thanks for trying so far. I am getting the error:

cannot find kernel 2.6.32-22-generic-pae at:
/lib/modules/2.6.32-22-generic-pae/build or
/lib/modules/2.6.32-22-generic-pae/source

It seems I am missing kernel files....what files should I copy?

---

### Post by sanderh79 on 2010-06-17
> **chihwahli said:**
> Thanks for trying so far. I am getting the error:
 
cannot find kernel 2.6.32-22-generic-pae at:
/lib/modules/2.6.32-22-generic-pae/build or
/lib/modules/2.6.32-22-generic-pae/source
 
It seems I am missing kernel files....what files should I copy?
 
Have you tried:
apt-get install linux-headers-generic-pae ? I think you need build-essential for it as well. Reading back it appears you tried the generic headers while you use the generic-pae kernel if I'm not mistaken.

---

### Post by chihwahli on 2010-06-17
> **sanderh79 said:**
> Have you tried:
apt-get install linux-headers-generic-pae ? I think you need build-essential for it as well. Reading back it appears you tried the generic headers while you use the generic-pae kernel if I'm not mistaken.

I am using the pae kernel version you are right. I executed :
apt-get install linux-headers-generic-pae 
again. No change.

I am looking in /dev/ and cannot see the device mentioned as vboxdrv.
I cannot execute successfully: /etc/init.d/vboxdrv install setup
The command is not found.

---

### Post by chihwahli on 2010-06-19
I added the group and added my myself to this group.
Does this group needs rights to a specific directory?

I am trying to install after apt-get update, After installing the package "virtualbox-ose" 
I still see the error :

stopping virtual kernek modules ok
starting virtualbox modules ok
no suitable modules for running kernel found fail
 Maybe i am missing the vboxdrv, but i have no clue where to get this

---

### Post by chihwahli on 2010-06-23
It's really difficult to install Vbox onto a Xubunto host. I tried with help from Virtualbox.org forum and here, but no positive results. I still get the error when I try to start a virtual machine. That I need to instal the virtual-ose-dkms package then do $ sudo modprobe vbox setup, but the thing is this file is not installed with all the packages I had to install. It's nowhere!  But it's already installed a 'billion times' and i cannot find the vboxdrv  Yesterday I was reading linux pro magizine and read about various virtualization programs, wrote a few doen to give them a try. I installed 2 packages with apt-get install: qemu-launcher qemu-common qemu-kvm  And this program works right after installing.  Don't understand why it's so hard to get virtualbox working on some linux hosts, it should work with the right packages, everything mentioned I installed.   If anyone know's how to fix virtualbox in my situation, pls do tell.

---

### Post by TheFu on 2010-06-24
> **chihwahli said:**
> It's really difficult to install Vbox onto a Xubunto host.

**Did you try to follow the instructions in my post from about 2 weeks ago?**  I provided a link. I have xubuntu running virtualbox. The installation was not trivial, but it isn't this hard either.

---

### Post by chihwahli on 2010-06-24
@theFu  I could not open your link.

---

### Post by sanderh79 on 2010-06-26
The past week I got myself some new hardware and did a fresh install of Ubuntu 10 (64bit), my former setup was over 2 years old, upgraded from 8. While virtualbox doesn't seem to work out of the box it took me just a few commands to get it up and running.
 
So just checking but did you download linux-source-2.6.32? When you run /etc/init.d/vboxdrv setup you need them. That's basically all I did, download the .deb, select the kernel source from synaptic, then running the vboxdrv setup followed by
 
sudo insmod /lib/modules/2.6.32-21-generic/updates/dkms/vboxdrv.ko (didn't need to: File exists)
sudo modprobe vboxdrv
sudo modprobe vboxnetflt
 
and it works. This weekend I'll try using different kernels for testing purposes, so if you need help post your output here.

---

### Post by TheFu on 2010-06-26
Some simplistic corporate firewalls block non-port 80/443 HTTP/HTTPS traffic. **Sorry you were impacted. **I've printed it to PDF format and placed it here: [http://jdpfu.com/vbox-ose-3.1.x_on_Ubuntu.pdf](http://jdpfu.com/vbox-ose-3.1.x_on_Ubuntu.pdf)  The PDF will be removed in a month.

I hope it helps you.

For others with something that read as a similar issue to me, these directions [http://ubuntuforums.org/showthread.php?t=1163811&page=6](http://ubuntuforums.org/showthread.php?t=1163811&page=6) seemed to help.

---

### Post by d3v1150m471c on 2011-03-15
it's a problem with the kernel headers, at least that's what it was for me. update to the latest kernel and make sure linux-headers-generic is installed from your repositories. I did a botched update a while back and somehow the headers weren't installed. installing them fixed it. hope that helps. 

ps - you'll probably need to reboot after re/installing them

---

### Post by conualfy on 2011-05-25
It's not only on Xubuntu, it's on Ubuntu 11.4 also. Just as someone else said, the solution is to uninstall the version you got from Ubuntu repository and to download the last VirtualBox for Natty/etc. from **[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) **

It all worked well on program start.

---

### Post by KingYaba on 2011-05-26
> **conualfy said:**
> It's not only on Xubuntu, it's on Ubuntu 11.4 also. Just as someone else said, the solution is to uninstall the version you got from Ubuntu repository and to download the last VirtualBox for Natty/etc. from **[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) **

It all worked well on program start.

I feel a bit silly; I didn't even think about downloading VirtualBox from the website. This solved the problem I was having as described in the 1st post.

---

### Post by dmelo on 2011-07-13
I had a similar problem. I solved it by installing another kernel. Only after installing another kernel I was able to install virtualbox-ose-dkms and load the module. Here goes the full description of my steps [http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root]("http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root")

---

### Post by Golgothen on 2011-09-23
> **sanderh79 said:**
> I just updated and the vboxdrv.ko appears to be missing after that. I couldn't load my vm's getting the well known error message. 
I did this to correct the problem:
 
- using synaptic, remove all virtualbox packages
- wget [http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/3.2.4/virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb) (or whatever is the latest version)
- dpkg -i <tab or virtualbox-3.2_3.2.4-62467~Ubuntu~lucid_i386.deb>
 
Start Virtualbox using Applications -> System Tools -> Oracle VM Virtualbox and my xp/server2k3 vm's were up and running again.
I just tried this and all worked fine...

Removed all VBox packages using Synaptic, then reinstalled:
VirtualBox-ose
Virtualbox-ose-dkms
Virtualbox-guest-additions

---

### Post by chihwahli on 2011-09-23
Thanks for the effort. It has been some time ago that I tried Xubuntu. I am using Ubuntu with vmplayer. Works well.

---

### Post by dmelo on 2011-10-17
I had this problem a while ago (i use Ubuntu 11.04). I posted the solution here [http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root]("http://diogomelo.net/blog/11/please-install-virtualbox-ose-dkms-package-and-execute-modprobe-vboxdrv-root")

---

### Post by interval1066 on 2011-10-28
Virtualbox users may want to consider using vmware if possible instead of vb; I just read an article on /. this morning about the complaints from the kernel developers about vb and how bad the code is.

---

