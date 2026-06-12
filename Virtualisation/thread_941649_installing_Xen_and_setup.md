---
title: "installing Xen and setup"
date: 2008-10-08
forum: Virtualisation
---

### Post by Chilliman on 2008-10-08
does any one know how to setup Xen i am doing this remotley also i keep getting and error

system installation failed
please script below


root@snickers:~# xen-create-image --hostname=cleo.sennett.com --size=2Gb --swap=256Mb --ide \
--ip=192.168.0.18 --netmask=255.255.255.0 --gateway=192.168.1.1 --force \
> --ip=192.168.0.18 --netmask=255.255.255.0 --gateway=192.168.1.1 --force \
> --dir=/home/xen --memory=64Mb --arch=i386 --kernel=/boot/vmlinuz-2.6.22-14-xen \
> --initrd=/boot/initrd.img-2.6.22-14-xen --debootstrap --dist=gutsy \
> --mirror=http://de.archive.ubuntu.com/ubuntu/ --passwd
Unknown option: debootstrap

General Information
--------------------
Hostname       :  cleo.sennett.com
Distribution   :  gutsy
Fileystem Type :  ext3

Size Information
----------------
Image size     :  2Gb
Swap size      :  256Mb
Image type     :  sparse
Memory size    :  64Mb
Kernel path    :  /boot/vmlinuz-2.6.22-14-xen
Initrd path    :  /boot/initrd.img-2.6.22-14-xen

Networking Information
----------------------
IP Address 1   : 192.168.0.18
Netmask        : 255.255.255.0
Broadcast      : 192.168.1.255
Gateway        : 192.168.1.1


Creating swap image: /home/xen/domains/cleo.sennett.com/swap.img
Done

Creating disk image: /home/xen/domains/cleo.sennett.com/disk.img
Done

Creating ext3 filesystem on /home/xen/domains/cleo.sennett.com/disk.img
Done
Installation method: debootstrap
Done
System installation failed.  Aborting


any help to solve this would be greatly recived.

cilliman

---

### Post by bodhi.zazen on 2008-10-08
See if this helps :

[https://help.ubuntu.com/community/Xen#Using%20debootstrap](https://help.ubuntu.com/community/Xen#Using%20debootstrap)

---

### Post by Chilliman on 2008-10-10
Hi.
i read the link that you sent. but i am still having the problem is there any body how can walk me throught the setup one step at a time .

chilliman:(

---

### Post by bodhi.zazen on 2008-10-10
I am not an expert in xen, I find it hard to use.

At any rate, your commands do not match the commands listed on the wiki page so I would be guessing.

My guesses are :


[list=number]
[*]You list your interface "--ip=192.168.0.18 --netmask=255.255.255.0 --gateway=192.168.1.1 --force " twice. Perhaps once is enough.


[*]Debootstrap does not typically install a kernel. I am used to chroot into a debootstrap where one could install a kernel (or other packages as needed).


[*]On the wiki page they use the generic kernel for the guest, you are using the xen kernel.


[*]64 mB is very light on the RAM side. Try increasing to 128 or better 256.
[/list]

---

### Post by Chilliman on 2008-10-12
i only copied the information from [http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories-p2](http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories-p2) and just changed what i think needed changing more information would be great, as i am a newbie at this Linux stuff.

thanks chilliman:)

---

### Post by bodhi.zazen on 2008-10-13
I have always found XEN to be difficult. Xen is popular with Fedora so you may wish to see if anyone on the Fedora forums can help.

The only advice I can offer is that you try to follow the advice on the Ubuntu wiki as the method seems to be somewhat different. I would hope the advice is better or more up to date on the wiki.

Other options would include other methods of virtualization.

For example, I like KVM, I run it from the command line though as I am familiar with qemu and the commands are very similar.

Another option would be OpenVZ.

You say you are new to Linux, you may wish to go with something less "bare metal" ie something with all the bells and whistles.

Have you considered VMWare or VirtualBox ?

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

VirtualBox is also nice, IMO you should install the version from Sun rather then the repos.

[Welcome : Links to get started with Virtualization - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=582729")

---

### Post by rickbeton on 2008-10-30
There are quite a few hosting companies offering [Xen]("http://www.xen.org/") or Virtuozzo VPS hosting at reasonable prices (e.g. in the UK [XenVZ]("http://www.netvouz.com/click/4386576314864352997?url=http://www.xenvz.co.uk/specialoffers.php"); [GPLhost]("http://www.netvouz.com/click/31562844929420112?url=http://www.gplhost.co.uk/hosting-vps.html"); [Goscomb]("http://www.netvouz.com/click/1897316522636968649?url=http://www.goscomb.net/services/vps.php")). I'd like to try Xen on one of my Ubuntu Desktops.  I'm not particularly interested in VMWare (which I have already tried) nor virtualbox (ditto).

But the [Xen+Ubuntu instructions]("https://help.ubuntu.com/community/Xen") are for Feisty - not Hardy nor Intrepid.

Do I have to downgrade to Feisty before I can have a play with Xen?

Won't it work with Gutsy/Intrepid?

Rick

---

### Post by bodhi.zazen on 2008-10-30
> **rickbeton said:**
> There are quite a few hosting companies offering [Xen]("http://www.xen.org/") or Virtuozzo VPS hosting at reasonable prices (e.g. in the UK [XenVZ]("http://www.netvouz.com/click/4386576314864352997?url=http://www.xenvz.co.uk/specialoffers.php"); [GPLhost]("http://www.netvouz.com/click/31562844929420112?url=http://www.gplhost.co.uk/hosting-vps.html"); [Goscomb]("http://www.netvouz.com/click/1897316522636968649?url=http://www.goscomb.net/services/vps.php")). I'd like to try Xen on one of my Ubuntu Desktops.  I'm not particularly interested in VMWare (which I have already tried) nor virtualbox (ditto).

But the [Xen+Ubuntu instructions]("https://help.ubuntu.com/community/Xen") are for Feisty - not Hardy nor Intrepid.

Do I have to downgrade to Feisty before I can have a play with Xen?

Won't it work with Gutsy/Intrepid?

Rick

I can not answer your question on Xen on Ubuntu, but I can suggest both OpenVZ and KVM. Both have been very stable fo rme on Ubuntu.

When I think of Xen I think of Fedora / Centos.

---

### Post by rickbeton on 2008-10-31
Thanks for the info.  I really wanted to try Xen and I got it working on Debian reasonably quickly.

It's a shame that Ubuntu doesn't really support it - ISTM that Xen is quite big out there.  But if the advice at the moment is "don't use Ubuntu", that's not what most of us here want to hear.

Rick :)

PS the wiki Howto page describe setting up Xen on Feisty.  This is surely rather out of date now - I tried to find Feisty for download but it has slipped into history it seems.

---

