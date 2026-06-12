---
title: "Virtualbox OSE and USB...."
date: 2008-06-26
forum: Virtualisation
---

### Post by diablo75 on 2008-06-26
I'm new to Virtual Box, coming from the VMware Server crowd.  How do I get Virtual Box to attach to a USB device?

---

### Post by flytripper on 2008-06-26
ose does not have usb support.. you need to remove and download the .deb installer from the virtual box website 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

On the whole i found virtual box to be better than vmware server and i am a convert

---

### Post by nnamdi on 2008-06-26
it is possible you could try the link below cos it worked for me but i use ubuntu gusty 7.10

[http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)

---

### Post by forger on 2008-06-26
> **nnamdi said:**
> it is possible you could try the link below cos it worked for me but i use ubuntu gusty 7.10

[http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)

That's not virtualbox-ose from the ubuntu repositories, that's virtualbox from virtualbox.org :)

---

### Post by diablo75 on 2008-06-26
> **flytripper said:**
> ose does not have usb support.. you need to remove and download the .deb installer from the virtual box website 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

On the whole i found virtual box to be better than vmware server and i am a convert

Well I've managed to get the new version installed using the above link, but when I went to edit the USB settings, it doesn't show any devices.  I'm sorry to admit there was an error message screen that showed up when I went to edit my system settings, and it said that a certain file, pertaining to USB connectivity, may not be present on the host machine.  I accidentally clicked "Do not show me this again", so I don't know how to reproduce the same error message box.

Here's my usb settings:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75420&stc=1&d=1214514254[/IMG]

What should I do to get USB device connectivity?

---

### Post by Doji on 2008-06-26
[www.virtualbox.org/download/1.6.0/UserManual.pdf]("www.virtualbox.org/download/1.6.0/UserManual.pdf")

Download and go to the USB support section.

The general idea is that you'll have to add the devices you want the virtual machine to see to the filters area.

---

### Post by diablo75 on 2008-06-26
Using this guide:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

I opened a config file and uncommented four lines of text.  That was all I needed to do to get it to work correctly.

---

