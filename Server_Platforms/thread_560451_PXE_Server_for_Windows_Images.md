---
title: "PXE Server for Windows Images"
date: 2007-09-26
forum: Server Platforms
---

### Post by Stormspace on 2007-09-26
I want to use PING (PartImage is not Ghost) to make images of my Windows XP PC's, only I want to use my ubuntu server to host the images. can anyone point me to some documentation on how to do this?

I already have these installed in the process but don't know how to set up the images so they are seen from the PC's.

tftp - set up and configured(Currently for hosting Cisco configs)
lftp
netkit-inetd

---

### Post by wirelessmonkey on 2007-09-26
I use sysrescdd to run partimage, then mount a samba share to the server, then create the image using the mounted server directory as the store location.  PXE, however, I have never been able to use without a Windoz server as the image host.

---

### Post by Stormspace on 2007-09-26
Ok. I decided to use Systemrescue CD and use the samba share on the network. I did have one issue with validation, but the following fixed it.

Boot with the PartImage CD in the Drive (Note: You may have to enter the boot menu to enable this, Dell PC's use the F12 key to get to the boot menu)

Press enter once the CD boots 

At the prompt type
"net-setup eth0" <enter>
Specify wired network and allow DHCP for IP assignment. If it fails you'll be prompted for manual settings.

At the prompt type
"mkdir /mnt/network" <enter> 
"mount -t smbfs -o rw,username=PartImage,password=mypassword //10.10.20.220/PartImage /mnt/network"
((I had a problem here because I didn't know what the default user was on the PartImage CD and the root passwd on the server wasn't working. My solution was to create a user on the samba server and give it write permissions. Now my network share is mounted in /mnt/network))

---

### Post by HermanAB on 2007-09-26
Here is something:
[http://www.aeronetworks.ca/ris-howto.html](http://www.aeronetworks.ca/ris-howto.html)

Cheers,

Herman

---

