---
title: "vbox, no usb printing"
date: 2012-06-08
forum: Virtualisation
---

### Post by th1bill on 2012-06-08
I've got a new MSI board with 4 gig of DDR3 and Ubuntu 12.04.  I downloaded the latest virtual box from te web site and installed win xp for a couple of programs that will not run on wine but I need to earn income.

I have an Epson Workforce 310 that prints without a hitch from the Precise side but I am totally unable to even find it in the vbox driven windoze install.  I have fopund, by googling that I need to network the guest to the host but have found no hint of how to go about this and to get the printer to work.

any help?

---

### Post by Habitual on 2012-06-09
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by th1bill on 2012-06-09
> **Habitual said:**
> [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

I already have te extention pack installed but thank you for the assist.

---

### Post by westie457 on 2012-06-09
Have you enabled a USB Filter in the settings menu for the virtual machine. Also have you added yourself to the 'vboxusers' group (this will enable you to access usb devices). Not on my Ubuntu box atm so cannot explain in more detail what I mean

---

### Post by th1bill on 2012-06-09
> **westie457 said:**
> Have you enabled a USB Filter in the settings menu for the virtual machine. Also have you added yourself to the 'vboxusers' group (this will enable you to access usb devices). Not on my Ubuntu box atm so cannot explain in more detail what I mean

Yes, I have a blank usb filter and I am on the group.  Thanks for the assist.

---

### Post by CharlesA on 2012-06-09
Install the guest additions already?

---

### Post by th1bill on 2012-06-10
Yes, I did that right off.

---

### Post by mbarland on 2012-06-10
What you need to do is share your printer in Precise, then connect to the network share in Windows. In my experience, you'll need to set the network adapter to "bridged" mode in vbox.

---

### Post by th1bill on 2012-06-11
> **mbarland said:**
> What you need to do is share your printer in Precise, then connect to the network share in Windows. In my experience, you'll need to set the network adapter to "bridged" mode in vbox.

Thank you, that works.

---

