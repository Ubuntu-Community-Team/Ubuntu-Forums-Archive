---
title: "Impressed so far..."
date: 2008-08-05
forum: Server Platforms
---

### Post by rhynes on 2008-08-05
Have an older Gateway server in the basement, tried different flavors of linux to get it up and running, no success. Suse, RHEL, xandros to name a few, but they always choked on the scsi raid. It's configured for a dual mirror on a megaraid card, on a dual xeon system, nothing spectacular.

Pop in the ubuntu server cd, fired it up and with a bit of input, i'm at the console... The GUI install was so simple and so is the rest of the software... Wow.

I've been playing with linux off and on over the years but never really able to get it into businesses. Yeah, I have a few linux ftp/www servers, and a couple of members but that's it. My clients are tied to windows and i'm not liking it anymore, it's getting worse. 

Been dealing with microsoft for 16 years now and I swear when they start pushing server 2008, i'm going to work at mcdonalds... 

My main question is running MS sql programs, can they be configured in any way with ubuntu? Accounting packages (namely simply accounting) is the biggest thing stopping me. Quickbooks is now running mysql for 2008 but i'm pretty sure it's strictly a windows app.

Thanks.

---

### Post by windependence on 2008-08-05
You may be interested in this:

[http://quickbooksenterprise.intuit.com/resources/linux.jsp](http://quickbooksenterprise.intuit.com/resources/linux.jsp)

-Tim

---

### Post by gtdaqua on 2008-08-05
You could still run Windows Apps in Ubuntu using 'wine'. But cant guarantee that all apps would work.

---

### Post by rhynes on 2008-08-05
I hadn't realized that quickbooks had the capability to run under linux. At least intuit is reaching into the future and shaking hands with mac and linux. 

Sage still isn't doing a thing for cross compatibility.

---

### Post by scorp123 on 2008-08-06
> **rhynes said:**
>  My main question is running MS sql programs, can they be configured in any way with ubuntu? I work for a rather small company in Switzerland and right now we're making a fortune converting companies away from Microsoft. So we see this problem very often: you can't switch a company overnight, you need to give them a smooth transition somehow ... IMHO and what really has proven itself time and time again is VMware Server (formerly known as "VMware GSX"). It's cheap: You can download it for free. And it more or less "just works", meaning whatever Windows software needs to run is 100% convinced of running inside a real Windows PC. The cool thing is that you don't need to emulate anything here (VMware does all the hardware emulation), whatever software you need to run is running inside a real Windows. So if the software works on Windows it should also work inside VMware.

You could also use e.g. "VirtualBox" ... But VMware and its disk formats have become a "de facto" standard and many companies use it and have know-how in this area. So it should be easy to get support and know-how should you need to.

---

### Post by windependence on 2008-08-07
> **rhynes said:**
> I hadn't realized that quickbooks had the capability to run under linux. At least intuit is reaching into the future and shaking hands with mac and linux. 

Sage still isn't doing a thing for cross compatibility.

Well, quickbooks itself does not run under Linux, but you can run the backend database on Linux. That is what they are telling you here.

As the above poster said, virtualization is the way to go, and NOW as of July 28th, VMware ESXi is free! This is VMware's hypervisor and is 100% production ready, so you can run several servers with several operating systems on one box. Like the poster above, we are converting people like crazy to Linux/Unix. Businesses are finally seeing the benefit to OSS.

-Tim

---

### Post by scorp123 on 2008-08-07
> **windependence said:**
>  VMware ESXi is free! Correct me if  am wrong: but you get still charged for the cool goodies such as , "Virtual Infrastructure", "VMotion" and "HA" ... ? :(

---

