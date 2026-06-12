---
title: "can't use shared folder in VirtualBox with Ubuntu Server"
date: 2015-08-13
forum: Virtualisation
---

### Post by stupidquestion on 2015-08-13
I installed a new instance of Ubuntu Server 14.04 in VirtualBox, but I can't get the shared folder functionality to work. I can't see the shared folder even though it's supposed to be automounted. The Guest Additions may not have installed correctly: I checked using "modprobe vboxadd" and "modprobe vboxvfs", but these returned "modprobe: FATAL: Module vboxadd not found" and "modprobe: FATAL: Module vboxvfs not found". 

I followed this instruction:
- Start the Ubuntu Server VM and insert the Guest Additions CD image (*Devices* menu, *Install Guest Additions*).
- $ sudo mount /dev/cdrom /media/cdrom
- $ sudo apt-get install -y dkms build-essential linux-headers-generic linux-headers-$(uname -r)
- $ sudo /media/cdrom/VBoxLinuxAdditions.run
(from [http://en.ig.ma/notebook/2012/virtualbox-guest-additions-on-ubuntu-server](http://en.ig.ma/notebook/2012/virtualbox-guest-additions-on-ubuntu-server) )

I also tried:
sudo apt-get install virtualbox-guest-utils
as well as:
sudo apt-get install --no-install-recommends virtualbox-guest-utils && sudo apt-get install virtualbox-guest-dkms

But none of these worked for me. 

One page suggested to load the vboxvfs kernel module. I put vboxvfs as well as vboxsf in /etc/modules, but that didn't work.

Any other ideas would be appreciated, thanks.

---

### Post by howefield on 2015-08-13
Have you added the user to vboxsf in the Ubuntu guest ?

---

### Post by stupidquestion on 2015-08-13
I now see that the vboxsf group is required for access to the auto-mount feature. 

I tested it again and I think I also missed at least one step:

apt-get install virtualbox-guest-dkms  
^ this successfully installed the vboxsf module

mkdir share
^ the mounting folder had to be created

mount -t vboxsf share share
^ specifying auto-mount in VirtualBox wasn't enough, I had to do this step manually (unless I joined the vboxsf group)

The folder mounted successfully after these steps were done in conjunction.

---

### Post by TheFu on 2015-08-13
So - if [solved], please mark the threat as such to help others.

---

