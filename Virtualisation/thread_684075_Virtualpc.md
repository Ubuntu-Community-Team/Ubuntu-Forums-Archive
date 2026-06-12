---
title: "Virtualpc?"
date: 2008-01-31
forum: Virtualisation
---

### Post by VVAW on 2008-01-31
Hi guys new to linux I am a windows guy that wants a change.
I am installing ubuntu on xp with either vmware vpc2007 VirtualBox etc
What oneis the best 

Also is there any utube videos to learn linux how the basics.  
Thanks Guys..:)

---

### Post by VVAW on 2008-01-31
bump

---

### Post by stalker145 on 2008-01-31
> **VVAW said:**
> Hi guys new to linux I am a windows guy that wants a change.
I am installing ubuntu on xp with either vmware vpc2007 VirtualBox etc
What oneis the best 

Also is there any utube videos to learn linux how the basics.  
Thanks Guys..:)

I haven't done any virtualization on Windows, so I can not answer your first question. I, personally, have been using VirtualBox on Ubuntu for the simplicity.

As for your second question, I also don't know about YouTube vids helping out with 'Nix, but I have heard good things about the [Ubuntu Screencast Project]("http://screencasts.ubuntu.com/"). Maybe you'll find what you need there.

Oh, and please wait at least 24 hours before bumping. It makes it more difficult for people to find your post if you bump. A lot of us search for unanswered posts and a bump counts as an answer taking it out of that listing.

---

### Post by bodhi.zazen on 2008-01-31
On windows you can use VMWare (more mature), Virtual Box (very nice, but be careful, I have seen virutal box disable usb mouse on Windows, don't know if they solved that bug yet), or qemu.

See the stick on this forum for further info, although it is geared to Ubuntu / Linux

---

### Post by aysiu on 2008-01-31
Here's a little tutorial I made on installing Ubuntu as a virtual OS inside Windows XP using VirtualBox:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by VVAW on 2008-01-31
Thanks all I ended up install VPC 2007 but having error message
V machine using a video mode that it to large try changing settings to no avail

---

### Post by VVAW on 2008-02-02
OK I having problems I can't seem to get the picture good 
on vpc2007 can't see anything
on vbox to small to even go through the setup
Tried several res to no avail any suggestions thanks

---

### Post by allquixotic on 2008-02-03
> **VVAW said:**
> OK I having problems I can't seem to get the picture good 
on vpc2007 can't see anything
on vbox to small to even go through the setup
Tried several res to no avail any suggestions thanks

It doesn't surprise me that Microsoft Virtual PC 2007 doesn't support a Linux distribution. Microsoft has [historically opposed Linux adoption](http://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/) and I seriously doubt if they have performed any testing of VirtualPC with Linux. On top of that, I'd like to dissuade you from using an additional Microsoft product (on top of Windows) just on principle.

I would suggest trying VMware Server 1.0.4. It is currently the best professional solution for virtualizing Linux. Qemu is good, but performance and compatibility are diminished compared to VMware, due to the smaller scope and available developers investing time into Qemu. 

VMware Server is freeware with no expiration date or limitations. Register for a free license key, then visit their unsubscribe website to have them take you off their newsletter distribution list. Don't worry, they don't share your email with third parties. Then install the software and go from there.

You should keep in mind that fancy desktop animation effects, 3d-accelerated games, and any other applications that use 3d hardware accelerated graphics will not work properly through virtualization. VMware is working hard to enable 3d graphics acceleration through VMs, but it is a difficult problem.

Only their commercial VMware Fusion, which runs on Macs only, supports hardware acceleration. 

VMware Workstation supports it **experimentally**, but it's also an expensive purchase. 

Finally, VMware Player has the same experimental 3d graphics support as VMware Workstation, but you can't create VMs with VMware Server, and you can't have Player and Server installed at the same time. If you want to generate your own Ubuntu VM and then use 3d graphics with it, you have to install VMware Server, install Ubuntu, uninstall VMware Server (preserving your VM itself), install VMware Player, and play the VM through it.

Perhaps **easiest of all**, you could just install VMware Player and download a pre-built Ubuntu Gutsy Gibbon virtual machine from VMware themselves: [click here](http://www.vmware.com/appliances/directory/1068).

Keep in mind that, for general desktop use, you will notice **performance slow-downs** and **slightly limited features** by using virtualization. Keep this in mind when you are evaluating Ubuntu through virtualization. Plug-and-play USB and 3d graphics are the two weakest areas of virtual hardware support; but, you should be able to start up Ubuntu and browse the Internet, compose documents, email, edit pictures, instant messaging, etc.

Regards,

Sean

---

### Post by VVAW on 2008-02-03
Thanks Sean I am a newbi3 so I am just learning so before I make a switch i will need to play and learn the basics.
I will give the server a go tomorrow thanks..

---

