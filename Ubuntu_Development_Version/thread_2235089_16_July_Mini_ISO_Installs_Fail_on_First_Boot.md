---
title: "16 July Mini ISO Installs Fail on First Boot"
date: 2014-07-18
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2014-07-18
The current mini.iso, from 16 July, installs without error here, but on the reboot the screen goes black and the drive light flashes until my patience runs out. No login prompt, no "Ubuntu 14.10" on screen. Been thru this drill 3 times with 3 images.

Has anyone seen this, as well?

(Later:  Installed from a 14.04 mini ISO, swapped 'trusty' for 'utopic' in sources.list, did a dist-upgrade, and rebooted... into the same thing.)

---

### Post by grahammechanical on 2014-07-18
Mini ISO? I am unfamiliar with it. Is that the same as Ubuntu core? I hope not. I have just been reading about Ubuntu core and I am starting to think that installing Ubuntu core could be used as a punishment for anyone breaking the C.O.C. :)

Can you provide a link to the download page of the Utopic mini ISO? And I will give it a go.

Regards.

---

### Post by kansasnoob on 2014-07-18
> **grahammechanical said:**
> Mini ISO? I am unfamiliar with it. Is that the same as Ubuntu core? I hope not. I have just been reading about Ubuntu core and I am starting to think that installing Ubuntu core could be used as a punishment for anyone breaking the C.O.C. :)

Can you provide a link to the download page of the Utopic mini ISO? And I will give it a go.

Regards.

Netboot:

[http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/)

---

### Post by buzzingrobot on 2014-07-19
Beat me to it.

It's a tiny 37-meg image that allows an install over the net. Contains just enough to boot and set up a DHCP connection, then pulls everything else from the servers. Eventually, it displays a choice of a dozen or so install options, including a server install, "Ubuntu desktop", "kubuntu desktop", etc. I don't select anything and just tab through. That boots to a bare shell and I add on from there.

Quirks:  

1.  I'm not sure if it can handle a wireless connection.

2.  I always manually partition. When I boot it from a USB stick, it labels the stick as /dev/sda, moving the actual install drive to /dev/sdb.  Late in the install, it offers a Yes/No choice on where it will install Grub. "Yes" puts it on /dev/sda -- the USB stick -- so I say "No" and then enter /dev/sdb manually. /etc/fstab identifies drives by UUID so all is well on the reboot.

---

### Post by grahammechanical on 2014-07-19
I would never have guessed it was called netboot. There was me thinking that netboot was for installing over a network. Forgetting that the internet is a network, as wide an area as a Wide Area Network can get. About to try it now. It has been decades since I faced down a text installer that gave such responsibility to the user.

EDIT: First things first. No problems with the re-boot. Loads to the login screen and in to the desktop. Running on Nvidia GT220 on Nouveau.

That was scary. I choose the Install option. I am not up to making decisions today. I thought I was telling it to install into sda5 but It was going to re-format sda10. No. No. That is where I am testing Ubuntu Desktop Next. I finally worked out that <space> to select <enter> to move on to the file system and mount point section and then <enter> to get a selection menu. Phew. I promise to never bad mouth Ubiquity again. :)

I would never recommend the Netboot to anyone who has not installed Ubuntu using the Something Else option. Unless they have got on the wrong side of me. :)

Regards.

---

### Post by buzzingrobot on 2014-07-23
Just to tidy up, a new mini.iso on 21 July shows the same behavior. Can't do anything but power down.

---

