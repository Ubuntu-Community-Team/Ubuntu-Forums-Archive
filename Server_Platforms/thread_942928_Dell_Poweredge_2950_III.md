---
title: "Dell Poweredge 2950 III"
date: 2008-10-09
forum: Server Platforms
---

### Post by cjkeeme on 2008-10-09
I am minutes away from purchasing a Dell Poweredge 2950 III to run as a terminal server. I have attached an image of the proposed purchase.

Can anyone tell me if everything will be compatible with my LTSP installation of Ubuntu 8.04? I am particularly concerned about the hard drive controller and the network adapter. Thank you. 

[IMG]http://www.keeme.net/files/2950.jpg[/IMG]

---

### Post by lykwydchykyn on 2008-10-09
Can't say for sure; I have a 2950 at work running Debian Etch and the hardware works apart from one annoying problem.  There is some kind of built-in USB flashmedia drive that holds windows drivers for the SCSI or something like that, and it confuses the grub-update script.  So whenever I update the kernel, I have to go back in and edit the /boot/grub/menu.list or else it won't boot.

I'm not sure if you'll have that problem under Ubuntu; I also have SLES10 running on some 2950's and it doesn't have that problem (though it's dirt slow compared to Deb).

---

### Post by gtdaqua on 2008-10-10
Config looks compatible. Though dell does not officially support Debian-based linux on their servers, they sure work. We went on a saga to upgrade the megaraid_sas drivers for Linux on Dell-PE Servers 1950/2950/2970. Support is not very good on linux (unless you use RHEL or SUSE).

Some recommendations: Why SATA? Its not advised on a server that will be continually accessed. Go for SAS if you can - greater performance and reliability. Also, this model has only 8 ranks for RAM and you are using them all! An upgrade might impair your ability to do so. Last question is why Dell when it wont support debian or others? HP does support and certifies its servers for debian distros. But usually dell is cheaper!

---

### Post by thomson2008 on 2008-10-10
Dell’s most versatile server, the PowerEdge 2950 III offers superior 2-socket virtualization performance combined with optional, factory integrated virtualization capabilities. Dell continues to Simplify Virtualization by streamlining virtualization deployment and providing ease of use in virtual infrastructures. By factory integrating VMware® ESXi 3.5, customers receive VMware capabilities and migration of virtual machines within a few clicks of a mouse.
___________________________________________________________
[Find a florist in Phoenix](http://www.florist-flowers-roses-delivery.com/arizona/phoenix_az.html) [cheapest loans](http://www.cheaponline-loans.co.uk/) [casas vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [ringtone downloads](http://www.myringtoneshub.com/)

---

