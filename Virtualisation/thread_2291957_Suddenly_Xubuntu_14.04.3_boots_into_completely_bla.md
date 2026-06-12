---
title: "Suddenly Xubuntu 14.04.3 boots into completely black screen as a VirtualBox guest"
date: 2015-08-24
forum: Virtualisation
---

### Post by gojira2016 on 2015-08-24
VirtualBox 4.3.30 r 101610
  Guest OS: xubuntu-14-04.3-desktop-amd64
  Host OS: Mac OS X 10.10.5
   
  I was running Xubuntu under VirtualBox, under Mac OS. Versions please see above. I had no problem whatsoever. I then installed Lyx. When I booted Xubuntu the next time, the screen simply stays completely blank (black).

   
  I do not know if this is related to the fact that I installed Lyx, or if it is related to Xubuntu or VirtualBox in general. Absolutely don't know how to proceed. The screen is completely black, there is no cursor or anything.

   
  (I would be very thankful for any help. The virtual machine is authorized to access a remote machine via ssh, and I have no possibility to log in to the remote machine anymore.)

---

### Post by Bucky Ball on 2015-08-24
*Thread moved to **Virtualisation**.*

Welcome. As things were fine before you installed Lyx I guess the reason for the breakage is reasonably obvious. It has something to do with installing Lyx. Is that all you did?

---

### Post by gojira2016 on 2015-08-24
Yes. I tried to install Lyx with the Xubuntu software manager. This did not work and gave me an error message. I am sorry I do not remember the error message anymore. I then installed via command line ("sudo apt-get install lyx"). I also did "sudo apt-get update". I then tried to start lyx, but it did not start. I then rebooted the virtual machine. It went directly to a black screen as described. Since then, if I try to boot it, it just goes to a black screen. I shut down via the (virtual) ACPI shutdown.

---

### Post by Bucky Ball on 2015-08-24
Without the error message it is hard to know but if there was a problem installing the official version from Synaptic Package Manager then I'd say there is a problem with using it in Virtualbox or some other problem at your end.

---

### Post by gojira2016 on 2015-08-24
My problem is not that I cannot use Lyx. I only mentioned this as a possible reason to track down the error. My problem is that I cannot even log in to Xubuntu anymore at all. It boots into a black screen. I gladly live without Lyx if I could only log in back to that machine.

---

### Post by ajgreeny on 2015-08-24
If we assume that lyx is at the root of the problem, though I do not see why it should be, you could try using Ctrl+Alt+F1 at the Xubuntu login screen to get to a command line, login at that, and from there run ```
sudo apt-get remove lyx
```and see if that solves your problem.  Do you have any other VMs that you can run in VBox to assess if it is that which is at fault?

I suspect, however, that your problem is more likely to be some other cause, perhaps one or more the updates you installed at about the same time, or maybe there is some difference between the VBox versions used in a Xubuntu host and a MacOS host that might cause the problem for you.

I have Xubuntu 14.04.2 with the 3.16.0-48 kernel as a VM in VBox on a Xubuntu 14.04 host which runs fine.  It did not have lyx installed but when I just installed lyx everything was also fine so I don't believe it is lyx that caused your problem.

Seems like a coincidence to me, but I might be wrong.

---

