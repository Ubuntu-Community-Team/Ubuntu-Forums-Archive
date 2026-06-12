---
title: "Virtualization in 10.04"
date: 2010-04-08
forum: Virtualisation
---

### Post by Synchro on 2010-04-08
I'm currently looking at 10.04 to act as a virtualization host on servers. To start with I just want to play with some images on a manually maintained setup, but longer term I'm planning a roll-out of a private cloud using UEC. Ideally I'll be able able to migrate the images from one environment to the other when I upgrade. I gather I need to be using qemu-kvm to use UEC so my choice of emulation engine is made. So far I've not found anything on virtualization in 10.04 other than that I read that its' 'greatly improved' (except for the docs I guess); in fact I notice that there are no docs for 10.04 at all on help.ubuntu yet.
I'm not interested in desktop integration, USB devices, graphical management, or guest OSs other than Ubuntu, just some straightforward CLI stuff to set up and run guest OSs.
Given that there are lots of images available for EC2, UEC etc, I'd like to use these if possible - but every guide I've found only covers installing from scratch using regular installation images, which is just far too time consuming and impractical to automate.
Can anyone point me at some good info?

---

### Post by Synchro on 2010-04-09
I've made some progress on this, but it's not good.
I found [the official docs on virtualization in 10.04]("http://doc.ubuntu.com/ubuntu/serverguide/C/virtualization.html"). While that's informative, it seems to document some mythical version of vmbuilder and kvm that actually works. Several options to vmbuilder just don't work (tmpfs, firstboot, firstlogin) and there are outstanding bugs for them, so none of the documented examples work either (looks like they're just copied from the older 8.04 docs). Eventually I got a built JeOS VM image, which took several hours (even though I have a fast connection). Next I tried to boot it using the generated run.sh file. It opens the VM in an X window, but then takes a riciculous amount of time to do anything (even though I'm running it on a quad-core xeon with VMX, 10G RAM, no other apps) - displaying all kinds of 'stuck cpu' and "worker unexpectedly returned with status 0x0100" errors. After about 40 mins it eventually gets to a login prompt. When I type a user name it takes about 15 mins to respond to *each* keystroke, and found the keyboard mapping is completely screwed - I typed 'user' as the user name and it shows 'j,,,'!

With the VM running, virsh doesn't seem to see it at all.

Does anyone have this working at all? Anyone even testing?

---

### Post by TheFu on 2010-04-09
I've been playing with 9.10 KVM virtualization for a little over a month. My intent was to get a head start on migration from Xen/8.04 to KVM/10.04 in the lab.  From what I've seen so far, that migration isn't a viable solution for our needs due to poor VM performance. Sadly, I don't have time to wait for KVM to mature and will be performing a migration off Xen.  It appears at this point that ESX is the best answer for us, in the available time frame. **We don't need or want a GUI for management.**  I haven't looked at any 10.04 alpha or beta releases, but will when the release is official. We'll have to make a decision in just a few days.

I'm so very, very sad about going commercial. It pains me greatly.

---

### Post by dcstar on 2010-04-10
> **Synchro said:**
> I'm currently looking at 10.04 to act as a virtualization host on servers.
........

There is little point in just wanting to use a new release for hosting VMs, older - proven - releases will work just as well, if not better.

If you just want a good, stable platform to run VMs that doesn't require fancy graphics then install VMware server 1.0.10 on a 9.10 or 9.04 host.

---

### Post by TheR on 2010-04-11
> **Synchro said:**
> I'm currently looking at 10.04 to act as a virtualization host on servers. To start with I just want to play with some images on a manually maintained setup, but longer term I'm planning a roll-out of a private cloud using UEC. Ideally I'll be able able to migrate the images from one environment to the other when I upgrade. I gather I need to be using qemu-kvm to use UEC so my choice of emulation engine is made. So far I've not found anything on virtualization in 10.04 other than that I read that its' 'greatly improved' (except for the docs I guess); in fact I notice that there are no docs for 10.04 at all on help.ubuntu yet.
I'm not interested in desktop integration, USB devices, graphical management, or guest OSs other than Ubuntu, just some straightforward CLI stuff to set up and run guest OSs.
Given that there are lots of images available for EC2, UEC etc, I'd like to use these if possible - but every guide I've found only covers installing from scratch using regular installation images, which is just far too time consuming and impractical to automate.
Can anyone point me at some good info?


Looks like something I have been doing for last two months. I have three diskless server booting from usb key on 10.04 and running VM's from iscsi server also on Ubuntu 10.04. So far it works fine. Windows and Linux guests no problem. Live migration mostly works. 
 
Why bother installing images. Basic Ubuntu image installs in about 15 minutes. After that you can just create new logical volume, dd from original image (4GB image is copied in 20 seconds). Mount image, update /etc/hostname, /etc/network/interfaces (new ip), and remove lines from /etc/udev/rules.d/60_persistent_network_rules (NIC recognition). There is my shine new computer in about two minutes. Than I just Install software that I need. Basic machine boots in just three seconds. From shutdown -r now to login prompt.

I was also able to transfere (just by dd) images from (Cytrix) Xen server 3.2 to this server and make a succesfull boot. Of course Windows images need reregistration, but otherwise work just fine.


by
TheR

---

### Post by whit on 2010-08-09
> **TheR said:**
> 
Why bother installing images. Basic Ubuntu image installs in about 15 minutes. After that you can just create new logical volume, dd from original image (4GB image is copied in 20 seconds). Mount image, update /etc/hostname, /etc/network/interfaces (new ip), and remove lines from /etc/udev/rules.d/60_persistent_network_rules (NIC recognition). There is my shine new computer in about two minutes. Than I just Install software that I need. Basic machine boots in just three seconds. From shutdown -r now to login prompt.
Sounds good. But too terse to really follow your steps. And vmbuilder is seriously broken, as mentioned above, with many features not working as documented. Did you use it, or install in a different way?

---

### Post by sh1ny on 2010-08-10
Use virt-install ! :)

---

