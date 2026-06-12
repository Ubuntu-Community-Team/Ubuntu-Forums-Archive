---
title: "best server distro for virtual machines"
date: 2011-09-12
forum: Server Platforms
---

### Post by chippanfat on 2011-09-12
Hey guys,
I've been having a lot of trouble trying to get vmware server 2 and virtual box working on ubuntu server 11.04, something to do with the headers and what not.

I've been researching about what the best distro is for hosting virtual machines but to no avail :(

so I'm pondering what your opinions are and if any of you people have servers at home hosting virtual machines? and what the best way is to go about getting my self up and running.

cheers.

---

### Post by haqking on 2011-09-12
> **chippanfat said:**
> Hey guys,
I've been having a lot of trouble trying to get vmware server 2 and virtual box working on ubuntu server 11.04, something to do with the headers and what not.

I've been researching about what the best distro is for hosting virtual machines but to no avail :(

so I'm pondering what your opinions are and if any of you people have servers at home hosting virtual machines? and what the best way is to go about getting my self up and running.

cheers.


it should be easy.

and distro doesnt really matter.

Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date) it is a .deb file so when downloaded just double click it

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

sudo usermod -a -G vboxusers username 

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

Edit: oh wait ive just seen you said 11.04 server, so you at CLI ? and not installed GUI (which by the way is not recommened)

and you meant headless i take it ? see here [http://perth.norg.com.au/2011/05/23/virtualbox-40-on-a-headless-ubuntu-1104-server/](http://perth.norg.com.au/2011/05/23/virtualbox-40-on-a-headless-ubuntu-1104-server/)

Have fun

Regards

---

### Post by chippanfat on 2011-09-12
I have the option to the GUI, but atm im using connecting remotely to the server over ssh.

---

### Post by haqking on 2011-09-12
> **chippanfat said:**
> I have the option to the GUI, but atm im using connecting remotely to the server over ssh.


ok yeah take a look at the link i posted.

might help.

---

### Post by dudumomo on 2011-09-12
Don't know if you really want to keep virtualbox, but in my case, on my OVH dedicated server I'm using Debian + Proxmox (Web interface to configure my VM)
And my VM are usually OpenVZ
Quite easy with proxmox. (It will works with Ubuntu of course)

---

### Post by Dangertux on 2011-09-12
My personal opinion, is go with Xen and CentOS. If you want Ubuntu run it is as DomU. 

I kind of gave up hope for decent virtualization in Ubuntu when Canonical dropped support for Xen in 10.04.

---

### Post by HermanAB on 2011-09-13
The distro doesn't matter, but VMware Server 2.x should be shredded, baled and incinerated in a toxic waste furnace...

Rather use VMware Player or VMware Workstation.

---

### Post by chippanfat on 2011-09-15
Another problem I have guys is when I boot centOS off of a usb for an install it requires a password,

but because I have just inserted the usb and chosen install there is no way I could have set a password for the root user.

I've tried

[LIST]
[*]password
[*]root
[*]centOS
[*]centos
[/LIST]
and leaving the field blank when I hit enter, and i've checked the centOS wiki and as of version 5 there is no default password set, is there any way I can get around this?

Cheers.

---

### Post by hawkmage on 2011-09-15
When booting and you get the Grub menu press "e" to edit the Grub command.  

Highlight the Kernel line and press "e" again.

Add the number "1" to the end of the command and press the <ENTER> key.

Finally press "b" to boot.  

This should get you to a command prompt in single user mode as root.  Use the passwd command to change the root password.  Reboot and you should be good.

---

### Post by chippanfat on 2011-09-15
sorry guys,
ignore my last post :)
the usb creator tool I used set the default password as the same one that I use on my laptop, I'm not sure why, but it was a lucky guess.

I've finally got centOS 6 installed and i'll be moving onto openVZ tomorrow :D

---

### Post by rubylaser on 2011-09-16
I use Proxmox primarily.  It supports KVM and OpenVZ, is open source, comes with a web based management interface, and is dead simple for backups and clustering.

---

