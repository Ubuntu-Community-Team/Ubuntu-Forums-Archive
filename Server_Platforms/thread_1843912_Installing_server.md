---
title: "Installing server"
date: 2011-09-14
forum: Server Platforms
---

### Post by Delb on 2011-09-14
Hi there,
 
im trying to set up a basic file server that can be accessed across the web so that all data is in one place. I have installed ubuntu server 64bit on a amd athlon 64 and when rebooting it does nothing.
 
Wasnt sure what to install so installed all.
 
There is a flashing cursor on top left, then goes blank, error:no such disc
 
then flashing cursor, then a quick flash of a message, looks like 
graphics card data, then screen says no signal and turns off..
 
 
Any help gratefully received.
 
I installed as F6 free software if that helps
 
 
Del

---

### Post by arrrghhh on 2011-09-14
Have you made sure the hardware is good?  Are you able to boot successfully with a LiveCD?  I don't think there are any LiveCD's of the Server Edition, but it would at least ensure that the hardware is OK and at least somewhat works with Linux :p.

This might be it too - it almost sounds like it's trying to find the disc - did you check the boot order in the BIOS?  Make sure the hard disk you have Ubuntu installed is in the boot order.  Some motherboards you can choose which device to boot from by hitting F12 or something similar - perhaps this 'boot menu' could ensure you are in fact booting from the correct device...?

---

### Post by HugoSerrano on 2011-09-14
Does the server got RAID Hardware? Probably it's not detected by Ubuntu. Check on BIOS something related with raid and see if you can disable, just to test.

---

### Post by Delb on 2011-09-14
I cant see that it has araid on the drives, it is booting from Hard drive first and still no good. Will download a live disc and see if that is any good
 
Thanks

---

### Post by Delb on 2011-09-14
Hi guys, I have made a ubuntu 11.04  live disc and is working ok, just going to install and see if it works from main drive.

---

### Post by Delb on 2011-09-15
Hi managed to get server 11.04 installed, may i just ask a question i installed it as a samba system, is this correct for a basic file server? or is there a gui system that is easier? im at a bit of a loss now. 
 
Any help gratefully received.
 
Del

---

### Post by Entilza on 2011-09-15
Good stuff, File server is samba yes.

You're almost there just edit /etc/samba/smb.conf  and add your share.  You don't even have to restart the service it's dynamic.

---

