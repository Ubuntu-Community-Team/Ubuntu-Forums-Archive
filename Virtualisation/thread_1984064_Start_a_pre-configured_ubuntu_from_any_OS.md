---
title: "Start a pre-configured ubuntu from any OS"
date: 2012-05-21
forum: Virtualisation
---

### Post by whitegecko on 2012-05-21
Hello,
I have a customized ubuntu system with a server setup and want to work with this setup together with a group of people (mac, win and linux users) during a workshop.
I would like to give them a usb-stick with a virtual box (or any other virtual machine) which they can start on there system by double clicking something to see the ubuntu.
Does anybody of you know something to have a pre-configured virtual machine with a ubuntu which can be started from every (win, mac, lin) OS?

---

### Post by raja.genupula on 2012-05-21
its something sounds like remote access of your Ubuntu Machine . something similar to your issue , [http://serverfault.com/questions/240223/best-practices-for-remote-gui-access-to-ubuntu-server](http://serverfault.com/questions/240223/best-practices-for-remote-gui-access-to-ubuntu-server)

---

### Post by whitegecko on 2012-05-21
@raja.genupula thank you for your answer. But I really mean a standalone instance of ubuntu running on each of the machines locally booted from a usb pen-drive in a virtual machine.

---

### Post by Lars Noodén on 2012-05-21
For the VM route to be viable, the target machines must have the exact same VM installed and running.  As popular as Virtual Box is, it is unlikely that it will be everywhere.

What you might try instead is installing the Live CD to the USB stick.  That way they can still boot Ubuntu from the USB stick but the harddrive is left alone.  With some extra effort, you can [roll your own edition of the Live CD](https://help.ubuntu.com/community/LiveCDCustomization).

Or you could try installing to the USB stick directly and just run Ubuntu from there.  That might be the easiest way to show off customizations.

---

### Post by thatguruguy on 2012-05-21
> **Lars Noodén said:**
> For the VM route to be viable, the target machines must have the exact same VM installed and running.  As popular as Virtual Box is, it is unlikely that it will be everywhere.

What you might try instead is installing the Live CD to the USB stick.  That way they can still boot Ubuntu from the USB stick but the harddrive is left alone.  With some extra effort, you can [roll your own edition of the Live CD]("https://help.ubuntu.com/community/LiveCDCustomization").

Or you could try installing to the USB stick directly and just run Ubuntu from there.  That might be the easiest way to show off customizations.

This. Any changes you make to the Live CD session on a USB stick will still be there the next time you run the session. You can modify it on one USB stick, and then copy the contents of that USB stick to as many others as you need.

---

### Post by whitegecko on 2012-05-21
> **thatguruguy said:**
> This. Any changes you make to the Live CD session on a USB stick will still be there the next time you run the session. You can modify it on one USB stick, and then copy the contents of that USB stick to as many others as you need.

Thank you. This sounds good. How can I create a bootable USB-stick from within debian? (I'm running debian at the moment.)

---

### Post by raja.genupula on 2012-05-21
[http://mohan43u.wordpress.com/2010/11/04/howto-bake-persistent-live-usb-debian-way/](http://mohan43u.wordpress.com/2010/11/04/howto-bake-persistent-live-usb-debian-way/)

---

### Post by whitegecko on 2012-05-22
Is there a possibilitiy to directly convert a running ubuntu installation into a live cd? Because we have it all pre-configured in a ubuntu running in virtual box.

---

### Post by Dave_in_MD on 2012-05-28
> **whitegecko said:**
> Is there a possibilitiy to directly convert a running ubuntu installation into a live cd? Because we have it all pre-configured in a ubuntu running in virtual box.

I may be missing something but it sounds like the path of least resistance would be to export the VM you would like to use copy the exported VM and the VM installer on the USB stick.  Have each participant install the manager and import the VM. everyone matches.

---

### Post by Lars Noodén on 2012-05-28
Would [bootcd](http://manpages.ubuntu.com/manpages/precise/en/man1/bootcd.1.html) do it?

[http://packages.debian.org/stable/utils/bootcd](http://packages.debian.org/stable/utils/bootcd)

---

### Post by Dave_in_MD on 2012-05-28
> **whitegecko said:**
> Hello,
I have a customized ubuntu system with a server setup and want to work with this setup together with a group of people (mac, win and linux users) during a workshop.
I would like to give them a usb-stick with a virtual box (or any other virtual machine) which they can start on there system by double clicking something to see the ubuntu.
Does anybody of you know something to have a pre-configured virtual machine with a ubuntu which can be started from every (win, mac, lin) OS?

I may have found your solution as long as they have internet connectivity 
[http://www.vbox.me/](http://www.vbox.me/)

---

### Post by dcstar on 2012-05-31
> **whitegecko said:**
> 
.........
Does anybody of you know something to have a pre-configured virtual machine with a ubuntu which can be started from every (win, mac, lin) OS?

A client VM is not the issue, all it has to be is 32-bit to ensure worst case hardware compatibility with the CPU.

The issue is a VM host that is required to be installed for the various environments. No boot device can handle more than one type of hardware (PC or Mac).

---

