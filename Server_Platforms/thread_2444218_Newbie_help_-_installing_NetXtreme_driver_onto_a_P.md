---
title: "Newbie help - installing NetXtreme driver onto a Poweredge with no internet access."
date: 2020-05-26
forum: Server Platforms
---

### Post by ntekniklaus2003 on 2020-05-26
Hi all,
     I have a Dell Poweredge T410, running Server 18.04.4 LTS installed just recently.

It is equipped with a Broadcom NetXtreme II (BCM5716), and I've had so much trouble trying to get this thing working over the time I've had this.

I require the drivers for this, and I am unsure on how to install it. It is currently on a flash drive and mounted to /media/usb-drive. 

I downloaded a file from the link below which I assume is the driver for my network adapter although am unsure.
[http://manpages.ubuntu.com/manpages/trusty/man4/bce.4freebsd.html](http://manpages.ubuntu.com/manpages/trusty/man4/bce.4freebsd.html)


I'm happy to provide further information should you need it.

---

### Post by darkod on 2020-05-27
Can something like this help you?
[https://askubuntu.com/questions/934832/broadcom-netxtreme-ii-bcm5716-ethernet-controller-unclaimed-after-update-to-16-0](https://askubuntu.com/questions/934832/broadcom-netxtreme-ii-bcm5716-ethernet-controller-unclaimed-after-update-to-16-0)

Basically the first answer says yo use that git clone command on your desktop for example, and then copy the bnx2 to /lib/firmware on your server.

Here is something similar but they do it during the install (and you already have the OS installed):
[https://askubuntu.com/questions/1203805/how-to-include-firmware-to-ubuntu-server-install](https://askubuntu.com/questions/1203805/how-to-include-firmware-to-ubuntu-server-install)

---

### Post by ntekniklaus2003 on 2020-05-27
Just did so via sudo cp -avr bnx2 /lib/firmware. I assume I just restart the thing and it should work from there?

edit: Did so and nothing new.

---

### Post by darkod on 2020-05-28
It is very strange such adapters not to work out of the box. They are widely known.

Also we can't be really sure now whether your troubleshooting steps so far have made some kind of conflict, which is possible.

That second link from my post basically says installing (updating) linux-firmware is enough.

If you have at hand some of those basic USB ethernet adapters you can try that too. Get internet working with USB ethernet, then update linux-firmware and see if that helps.

Did you check the name of the module related to that NIC and whether it gets loaded?

---

