---
title: "Cloud Solutions"
date: 2011-12-16
forum: Server Platforms
---

### Post by techbonacci on 2011-12-16
My name is Michael, I have my A+ and CCNA certification. I've been in the IT field about 4 years. The company I work for a small (a mere 4 technicians including me). We had a cloud solution for business customers that was simply. It made digital copies of all workstations in the office (Windows XP to Windows 7) every hour. If something went wrong, we could literally do a bare-bone restore to a specific computer using a digital copy the prior hour. Perfect in the event of software/OS corruption or viruses. Or we could extract a single file from 3 days prior that was accidentally deleted today. Everything worked until it came to trying to virtualize that digital copy. How it was supposed to work was when that physical computer dies, we load up the latest digital copy into the cloud, the customer jumps on another computer, and boots to PXE, where the cloud server would allow the customer to continue working on it as if the physical computer never failed. That was what our cloud solution was supposed to do and it didn't. After a month of trial and error, along with over 200 logged hours of phone conversations with the engineers who designed the hardware and software, we decided to give up on this company. (I will not say who, but the above describes what it offered). I've been using Ubuntu Desktop for over 2 years now. I've used Ubuntu Server OS several times, I even have a computer at home running this, but hilariously all I use it for is disk space and as a DNS Server. I want to know if there is a free software solution out there for Linux that would allow us to do the above described and if someone can point me in the right direction to study up on so I may test drive a cloud solution with virtualization at home. Please keep in mind the guest OS will be Windows-based, not Linux based, and if it makes a difference, the host OS will be Ubuntu Server 64-bit and I will need to virtualize a guest OS Windows 32-bit (and be accessible by any other computer within the network). Any help is greatly appreciated, Thank you in advance.

---

### Post by HermanAB on 2011-12-16
rsync

---

### Post by techbonacci on 2011-12-16
> **HermanAB said:**
> rsync

rsync will allow for that digital backup, including incremental backups, but offers nothing for virtualization. Like I said before, what I need to do is be able to fully virtualize a "backup" in a private cloud, making it accessible by any other workstation within the network. Our long-term goal is to be able to replace all physical workstations with nothing more than a terminal that boots to the cloud server, hosting the virtualized workstations.... along with that perfect failover in the event of something as simple as the customer deleting a file by mistake to a intranet-wide malicious attack. Providing failover protection against something physical like a natural disaster will be easily guaranteed by providing offsite storage of the "backups".

---

### Post by HermanAB on 2011-12-17
First of all you need rsync, since you cannot save a complete copy of a machine every hour over a network.  There are a plethora of front-ends for it.

If you want to do netboot, then you need a DHCP and TFTP server.

---

### Post by SeijiSensei on 2011-12-17
> **techbonacci said:**
> Our long-term goal is to be able to replace all physical workstations with nothing more than a terminal that boots to the cloud server, hosting the virtualized workstations.... along with that perfect failover in the event of something as simple as the customer deleting a file by mistake to a intranet-wide malicious attack.

Isn't this a description of how [Citrix]("http://www.citrix.com/English/ps2/products/product.asp?contentID=2304708&ntref=prod_top") works?  Have you looked at that solution?

One idea you can consider is having the workstations run Linux hosting Windows in a VirtualBox VM.  Taking a snapshot of the VM should be all you'd need to restore the system.

---

### Post by aaronccrow on 2012-01-21
You are wanting a Citrix environment.  Citrix is an application that runs on a Microsoft Terminal Server that the allows clients to login using PCs or even dumb terminals to a "desktop" that would be the same no matter where they sat or what equipment they were using, it saves all data on the server farm and keeps data backed up from the server however you set it up...  [http://www.citrix.com/lang/English/aboutCitrix.asp?ntref=hp_promo1_US](http://www.citrix.com/lang/English/aboutCitrix.asp?ntref=hp_promo1_US)

---

