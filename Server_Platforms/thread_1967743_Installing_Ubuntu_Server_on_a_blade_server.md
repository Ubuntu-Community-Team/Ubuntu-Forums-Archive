---
title: "Installing Ubuntu Server on a blade server"
date: 2012-04-28
forum: Server Platforms
---

### Post by JasonMarquez on 2012-04-28
I will be buying a blade server to learn how to use them and experiment with them. How would I install the linux operating system on it if there is no monitor or keyboard attached to it?

---

### Post by CharlesA on 2012-04-28
You'd have to hook up a monitor and keyboard to it?

Unless it's a VPS, you'd have to do it from the console.

---

### Post by SeijiSensei on 2012-04-28
As Charles said, just put the server on the bench and use a keyboard and mouse to install Ubuntu.  Once everything is running as you like, you just disconnect the peripherals and slide the box into the rack.  From then on, it's SSH all the way.

If the device doesn't have a CD/DVD drive, you'll need to boot from a [USB pendrive]("https://help.ubuntu.com/community/Installation/FromUSBStick").  Also if the server has a hardware RAID controller, you'll need to check and make sure it's supported in Ubuntu.  I had good luck with the PERC controllers on Dells since the driver was written by RedHat and is included by default in both the CentOS and Ubuntu kernel images.  I'm running CentOS 6 on a Dell [R410]("http://www.dell.com/us/highered/p/poweredge-r410/pd"), and the installer detected the card and installed the driver without any additional effort on my part.  I had similar success when I tested Ubuntu Server 10.04 on the same hardware.

---

### Post by CharlesA on 2012-04-28
> **SeijiSensei said:**
> As Charles said, just put the server on the bench and use a keyboard and mouse to install Ubuntu.  Once everything is running as you like, you just disconnect the peripherals and slide the box into the rack.  From then on, it's SSH all the way.

That's pretty much what I do with my server. The only thing hooked up to it now is power and network. SSH is quite useful. :)

---

