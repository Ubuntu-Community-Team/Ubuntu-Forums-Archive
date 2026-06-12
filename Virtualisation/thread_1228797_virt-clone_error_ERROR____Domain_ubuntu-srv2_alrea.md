---
title: "virt-clone error: ERROR    Domain ubuntu-srv2 already exists"
date: 2009-08-01
forum: Virtualisation
---

### Post by Koraq on 2009-08-01
I created a vm with jaunty, and I want to clone it as another ubuntu install. This is the command I ran:

virt-clone -o "ubuntu-srv1" -n "ubuntu-srv2" --connect=qemu:///system  -f HD/ubuntu-srv2.img

I have copied the first disk image to a file with the name HD/ubuntu-srv2 and thought that would just erase the old one. 

First time I tried it, I had included an option which shouldn't be there and I erased the result and tried again. Then I got the error:

Disk /home/ante/Virtualise/HD/ubuntu-srv2.img is already in use by another guest!
Do you really want to use the disk (yes or no)?  yes
ERROR    Domain ubuntu-srv2 already exists

What the heck does that last thing mean? I used grep -r to see if there was anything refering to ubuntu-srv2 anywhere but couldn't find it. 

How can I find/disable this invisible domain?

---

### Post by Koraq on 2009-08-02
I'm going to reply to myself and give some more info.

I removed the old disk image, and remade it without any relation to the old vm I'm cloing. Explain this error to me! I'm very confused by this:

root@zareason:~/Virtualise# dd if=/dev/zero of=./HD/ubuntu-srv2.img bs=8 count=268435456
268435456+0 records in
268435456+0 records out
2147483648 bytes (2.1 GB) copied, 626.566 s, 3.4 MB/s
root@zareason:~/Virtualise# virt-clone --debug -o "ubuntu-srv1" -n "ubuntu-srv2" --connect=qemu:///system  -f HD/ubuntu-srv2.img
Sun, 02 Aug 2009 00:51:42 DEBUG    start clone with HV qemu:///system
Sun, 02 Aug 2009 00:51:42 DEBUG    Using libvirt URI connect 'qemu:///system'
Sun, 02 Aug 2009 00:51:42 DEBUG    Detected storage as type 'file'
This will overwrite the existing path '/home/ante/Virtualise/HD/ubuntu-srv2.img'!
Do you really want to use this disk (yes or no)? yes
 Disk /home/ante/Virtualise/HD/ubuntu-srv2.img is already in use by another guest!
Do you really want to use the disk (yes or no)?  yes
Sun, 02 Aug 2009 00:52:18 DEBUG    Detected storage as type 'file'
Sun, 02 Aug 2009 00:52:18 DEBUG    Validating original guest parameters
Sun, 02 Aug 2009 00:52:18 DEBUG    Original paths: ['/home/ante/Virtualise/HD/ubuntu-srv1.img']
Sun, 02 Aug 2009 00:52:18 DEBUG    Original sizes: [2147483648]
Sun, 02 Aug 2009 00:52:18 DEBUG    Original types: [True]
Sun, 02 Aug 2009 00:52:18 DEBUG    Original idxs: [1]
Sun, 02 Aug 2009 00:52:18 DEBUG    original guest status: 5
Sun, 02 Aug 2009 00:52:18 ERROR    Domain ubuntu-srv2 already exists
Sun, 02 Aug 2009 00:52:18 DEBUG    Traceback (most recent call last):
  File "/usr/bin/virt-clone", line 215, in main
    design.setup()
  File "/usr/lib/python2.6/dist-packages/virtinst/CloneManager.py", line 341, in setup
    self.setup_original()
  File "/usr/lib/python2.6/dist-packages/virtinst/CloneManager.py", line 236, in setup_original
    raise RuntimeError, _("Domain %s already exists") % self._clone_name
RuntimeError: Domain ubuntu-srv2 already exists

root@zareason:~/Virtualise#

---

### Post by Koraq on 2009-08-02
Anyone?

---

### Post by jocampo on 2009-08-03
I use VirtualBox as vm solution so can't help very much. That said, I know we have an xml file on VirtualBox which keep track of the existing VMs. It is not a binary or hard drive, it is just a plain text file or similar which VirtualBox reads during a VM creation. Sometimes, if you deleted the hard drive but still there is a machine reference there you can get a similar error 'cause VirtualBox is not smart enought to recognize that the virtual hard drive does not exist anymore of you are just creating a new machine. So, deleting that orphaned entry inside the xml file, fix the error.

Sorry, just trying to help a bit

---

### Post by Koraq on 2009-08-04
Doing a:
virsh --connect qemu:///system list --all

Will list all virtual domains.

Doing that I found that I had indeed two domains, and could remove the unneeded one by:
virsh --connect qemu:///system undefine ubuntu-srv2

Where is that information stored? God knows, but I realized that I had actually started a sudo bash, so maybe it ended up in root's home directory.

---

### Post by Koraq on 2009-08-04
Many thanks to Cole Robinson at RedHat for that solution!

---

