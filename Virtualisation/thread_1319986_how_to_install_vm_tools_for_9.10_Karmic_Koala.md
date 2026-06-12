---
title: "how to install vm tools for 9.10 Karmic Koala"
date: 2009-11-08
forum: Virtualisation
---

### Post by calamus300 on 2009-11-08
how can i install vm tools for ubuntu 9.10 Karmic Koala

---

### Post by Scunizi on 2009-11-08
If you're talking about virtualbox and an Ubuntu guest, then mount the vbox guest additions iso and then open Appliicatons>Accessories>Terminal .. in terminal type "cd /media/cdrom0" .. once there type "ls" and hit enter to see the files.  type "sudo ./<right name of file>" and hit enter.  The right file would be the linux version x86 for 32bit and amd64 for 64 bit.  Just depends on which version of ubuntu you've installed.  Restart the guest and all should work. Mouse should now move smoothly from inside the guest to the outside.

---

### Post by calamus300 on 2009-11-09
thanks Scunizi for response and reply
i'm using vmware workstation ACE edition version 6.0.0 45731
failed to work
also i tried it on ububntu 7. previous release since a time 
and worked for me but 9.10 ??
i hope some one help me

---

### Post by Scunizi on 2009-11-09
Ah. vmware.. perhaps this will help [http://www.howtoforge.com/vmware_tools_on_linux](http://www.howtoforge.com/vmware_tools_on_linux) .

---

### Post by fjgaude on 2009-11-09
I think we are dealing with a bear cat when it comes to 9.10... especially the net manager aspects of it. Some many changes with 9.10 over 9.04... who will come to our recue?

---

### Post by calamus300 on 2009-11-10
thanks Scunizi
for reply
i tried some like that and failed but 
I'll retry for new kernel of 9.10 Karmic Koala

---

