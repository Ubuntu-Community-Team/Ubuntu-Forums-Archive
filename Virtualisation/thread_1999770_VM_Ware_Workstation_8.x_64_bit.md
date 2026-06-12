---
title: "VM Ware Workstation 8.x 64 bit"
date: 2012-06-08
forum: Virtualisation
---

### Post by Welly Wu on 2012-06-08
I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 1,066 MHz SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive. I installed Ubuntu 12.04 64 bit Long Term Support as my default and primary host operating system.

I paid for VM Ware Workstation 8.x without a support contract with VM Ware last September 2011.

I downloaded and I installed VM Ware Workstation 8.0.3 64 bit. The installation works fine. The problem is when it tries to compile the kernel.

I already downloaded both the third-party patches. VMNet.diffs and the other patch for VM Ware Workstation 8.0.2.

After I patch and it compiles the kernel modules successfully, my guest virtual machines do not have network access. I downloaded and I installed Red Hat Fedora 17 64 bit GNU/Linux and Microsoft Windows 8 64 bit Release Preview from the .ISO files. Using both third party patches, both of my guest operating systems can not connect to any network including the Internet. As a consequence, I had to delete my guest virtual machines and completely remove VM Ware Workstation 8.0.3 64 bit for Ubuntu 12.04 64 bit LTS.

VM Ware supports Ubuntu 11.10 32 and 64 bit. They have not indicated when they will support Ubuntu 12.04 64 bit Long Term Support with the new Linux kernel 3.2.x.

What are my options?

I want to use VM Ware Workstation 8.x 64 bit on Ubuntu 12.04 64 bit Long Term Support without having to resort to third-party patches that have their own networking flaws.

Has anyone else been able to replicate my specific problem?

What was your solution?

---

### Post by Welly Wu on 2012-06-08
In the meantime, I installed Oracle Virtualbox 4.1.16 including the Guest Additions and the Oracle VM Virtualbox Extension Pack. Now, Microsoft Windows 8 64 bit Release Preview and Red Hat Fedora 17 64 bit GNU/Linux work perfectly. My guest operating systems can access the network including the Internet.

This should serve as an example that free and open source software products and services can work in situations where closed source and proprietary software applications that are much more expensive fail to work properly especially when using new operating systems.

I would like to be able to install and run VM Ware Workstation 8.x 64 bit because I paid for it in the near future. However, it will take VM Ware at least another couple of weeks to issue an update or an official patch that will compile successfully with the new Linux kernel 3.2.x that ships with Ubuntu 12.04 64 bit LTS. I don't want to resort to unofficial third-party patches because those people have no idea how to make it work properly with VM Ware software applications.

Is there anyone else that can replicate my specific problem with using both of the unofficial third-party patches for VM Ware Workstation 8.0.2 or 8.0.3 64 bit on Ubuntu 12.04 64 bit LTS? What was your solution?

---

### Post by forrestcupp on 2012-06-08
I don't have experience with VMware Workstation. But I do have experience that VirtualBox is much easier to set up and use than VMware Player, and the performance doesn't seem to be noticeably worse. 

Hopefully, someone can help you with that. But I'd probably just cut my losses and keep using VirtualBox. It's a pretty quality VM software.

---

### Post by Welly Wu on 2012-06-08
I am going to wait and see if VM Ware Workstation 8.0.x (let us say 4 or 5) 64 bit version will officially support Ubuntu 12.04 64 bit Long Term Support and Linux kernel 3.2.0-25 generic or later versions. I am a bit ambivalent about closed source and proprietary hardware and software technologies because I know that I want to avoid expensive support contracts and vendor lock-in especially with my own data. This is why I switched from Microsoft Windows 7 64 bit Ultimate Edition to Ubuntu 12.04 64 bit Long Term Support. I literally ran out of money buying third-party specialized software applications for Microsoft Windows 7 64 bit.

I understand that Ubuntu 12.04 64 bit LTS is relatively new since it was released on April 26th, 2012. I also understand that it will take VM Ware some time to address its technical problems associated with Workstation 8.x 64 bit with Linux kernel 3.2.x. I also understand that I did not purchase an accompanying support contract with VM Ware for Workstation 8.x 64 bit. However, VM Ware is responsible for ensuring that their premiere desktop virtualization software application works with GNU/Linux distributions especially Ubuntu 12.04 64 bit LTS.

VM Ware Workstation 8.x is fast. I have an original Intel Core i5-430M CPU which is missing the critical VT-d instruction set for virtualization technology and I can attest to the fact that VM Ware Workstation 8 is fast on my ASUS N61JV-X2 notebook PC on both Microsoft Windows 7 64 bit and Ubuntu 12.04 64 bit LTS platforms. I especially like the capability to encrypt my virtual machines using the industry standard Advanced Encryption Standard in Cipher Block Chaining mode of operation at 256 bits and 14 rounds cipher strength with SHA-512 bits hash algorithm. However, this unique capability is not a must have for me since I use LUKS/LVM with the Serpent cipher in CBC ESSIV SHA-256 mode of operation at 256 bits 32 rounds cipher strength and SHA-512 hash algorithm for full disk encryption of my Intel X25-M 160 GB SSD.

VM Ware is the gold standard in the industry. Workstation is deployed in countless production environments worldwide. Certain enterprises within certain industries mandate VM Ware products.

I plan to upgrade to Ubuntu 12.10 64 bit Quantal Quetzel in October 2012. My concern is that I will have to repeat this same scenario in less than five months from today if I choose to use VM Ware Workstation 8.x 64 bit. I am almost certain that upgrading to a newer version of Ubuntu will break compatibility with third-party closed source proprietary software applications especially if they are designed for Microsoft Windows while using WINE.

I will have to think this over carefully over the next few days to see if I want to retry the two different third-party unofficial patches. The problem is that I simply do not know if future versions of VM Ware Workstation will resolve the VM Ware Network stack kernel compilation problems or if these patches will work with future versions or not. They are designed for VM Ware Workstation 8.0.2 32 or 64 bit only. I think that this is why my 64 bit guest virtual machines could not connect to the network or Internet due to the fact that I upgraded to VM Ware Workstation 8.0.3 64 bit while using a modified version of both of these third-party unofficial patches.

It is really messy.

---

### Post by RikoW on 2012-06-09
Hi,

I'm afraid I can't help you much in solving your problem, except maybe suspecting you applied the wrong patch!?

I'm running VM WS8.0.3 64bit in Mint 13 (which is under the hood just Ubuntu 12.04 LTS. I have as guest OSes XP 32 bit and Win7 64 bit which both run fine with network connections. I did have to patch VMware WS, though, just like anybody else.

It's hard to accept that you buy the supposingly gold-standard in virtualization and have to resort to Google and unofficial patches to get the kernel modules to compile.

Anyway, the essence of the long story and the good news is that in principle it works. I'd suggest to uninstall VMware, install a fresh and make sure you apply the correct patches.

Cheers,
            Riko

PS: This is the patch I applied:
[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/]("http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/")

---

### Post by Welly Wu on 2012-06-09
I plan to purchase Codeweavers CrossOver for Linux with a one year support subscription next Monday. I downloaded and I installed CrossOver from the Ubuntu Software Center and I finally was able to install Intuit Quicken Deluxe 2011 properly. I was able to connect to my Sovereign Santander Bank accounts, download my transactions up to today, and synchronize my bank accounts.

There are only two third-party unofficial patches designed specifically for VM Ware Workstation 8.0.2 32 or 64 bit for Ubuntu 11.10 32 or 64 bit GNU/Linux. I did repeatedly install, patch, and test my guest virtual machines for network access twice using both patches. I made sure to completely remove VM Ware Workstation 8.0.2 and 8.0.3 64 bit before trying each of the two different patches.

I should not have to do this. According to VM Ware, Ubuntu 12.04 32 and 64 bit Long Term Support is not supported yet because of Linux kernel 3.2.0-25 generic is untested by VM Ware for Workstation 8.x. VM Ware is aware of the fact that a small proportion of its customers with support contracts are experiencing similar problems as I have reported herein and they are working to patch and update Workstation 8.x to be fully compatible with Ubuntu 12.04 32 or 64 bit Long Term Support with a future version.

This is my problem. I plan to upgrade to Ubuntu 12.10 64 bit Quantal Quetzel in October 2012 by performing an upgrade using the Update Manager. My biggest concern is that doing so will break compatibility with VM Ware Workstation 8.x 64 bit and I will have to repeat this whole charade all over again.

On the other hand, Oracle Virtualbox is fully supported with Ubuntu 12.04 64 bit Long Term Support and it will continue to be fully supported with future Ubuntu releases with little to no problems. If I stick with Oracle Virtualbox, then I can continue to work with my guest virtual machines uninterrupted without any problems as I am doing so today.

VM Ware Workstation is a premiere desktop software application and it is quite expensive. I purchased the academic version without a support contract. I have some financial difficulties right now in my life and it will be quite challenging for me to be able to continue to upgrade to future versions of VM Ware Workstation even if they offer me a deep discount as an existing customer. I know that current VM Ware Workstation 7.x users can upgrade to Workstation 8 for $99.00 USD or $79.00 USD for academic customers.

To be quite honest and truthful, I plan to spend $70.00 USD to purchase WiTopia personal VPN PRO service for one year in the next two weeks. I already subscribe to WiTopia personal VPN basic for $5.99 USD per month. I need access to a VPN service provider because I connect to 802.11 B/G/N public Wi-Fi Hot Spots regularly. I have a lot of unique, critical, and confidential heavily encrypted data. Accessing an unsecured public Wi-Fi hot spot is a security risk and it puts your identity, network traffic, and data available to anyone connected to the same wireless network.

In the meantime, I am going to wait for VM Ware to fix their VM Ware Network Stack kernel compilation errors regarding Linux kernel 3.2.0-25 generic or later versions. Resorting to unofficial, third-party, patches is another security risk. I am convinced that both patches fail to fix the network access problems in guest virtual machines because the authors do not know what they are doing.

I was able to replicate this on another computer running an identical Ubuntu 12.04 64 bit Long Term Support disk image as mine. So, I ruled out the question about defective PC hardware. It is definitely the authors of these patches that I have pinpointed as the source of my problems associated with no network access for my guest virtual machines. If you read their posts in various forums, they do not test their patches with live production guest virtual machines thoroughly with specific, well-documented, case studies.

---

### Post by Welly Wu on 2012-06-09
I will re-download VM Ware Workstation 8.0.3 64 bit for GNU/Linux and I will re-download the specific patch that you posted tonight. I will work on this once again tomorrow. It is entirely possible that my problems with network access for my guest virtual machines could be resolved tomorrow. However, I am not optimistic. We shall see.

---

### Post by RikoW on 2012-06-09
May I asked why you don't just stick to Virtualbox, since it works for you and money is obviously an issue?

I use VMware because I like the way their unity mode integrates into the linux desktop. And since my employer pays for the license I might as well get what I want.

From your long response I would recommend to forgetting about VMware in particular, which each new Ubuntu release you'll probably face the same problem. I went through that since a few update cycles already.

Maybe you get your money back (probably depends on how long ago you purchased).

All the best,

               Riko

---

### Post by Welly Wu on 2012-06-09
I paid $120.00 USD for VM Ware Workstation 8.x last September 2011. I can not get a full refund at this time from VM Ware.

I paid for it. I have a genuine and valid license key. It is designed to work with GNU/Linux platforms including Ubuntu 11.10 32 or 64 bit. I want to be able to use what I paid for.

I also paid for Microsoft Office 2010 Professional Plus 64 bit. It is important software. My copy entitles me to install it on as many computers without the need for a genuine product key. It is a special academic version for New Jersey Institute of Technology students and faculty.

I want to use the software products that I paid for in Ubuntu 12.04 64 bit Long Term Support. That's my bottom line.

As far as VM Ware Workstation 8 is concerned, I just want to test if my guest virtual machines will have access to the Internet or not using this unofficial third-party patch. If not, then I will have to wait for VM Ware to patch and update Workstation 8 to work right out of the box with Ubuntu 12.04 64 bit Long Term Support. I do not plan to use VM Ware to run guest virtual machines in a production environment. I will use Oracle Virtualbox to do that.

Switching from Microsoft Windows 7 64 bit Ultimate Edition to Ubuntu 12.04 64 bit Long Term Support has been challenging at best. There are some specific Windows software applications that I still need to use which I already mentioned. My original Intel Core i5-430M CPU is showing its age since it is missing the critical VT-d instructions to support virtualization technology with hardware acceleration. So, this is why I am seriously considering Codeweavers CrossOver for Linux as an alternative.

I still need to run guest virtual machines to support my family and friends on their computers. I am CompTIA A+, Network+, Security+, and (ISC)2 CISSP CBK certified. I have worked as a Help Desk and Support Technician in the past. This is why I want to try to make VM Ware Workstation 8 work on Ubuntu 12.04 64 bit Long Term Support because it is the industry standard and it has much better performance. I have to support Microsoft Windows XP, 7, and Ubuntu 12.04 64 bit Long Term Support at a minimum for the next three years. I will also have to support Microsoft Windows 8 when it is released sometime this October 2012.

The VM Ware Workstation 8 Unity feature is nice especially in Ubuntu Unity. It offers a seamless full screen support for multiple guest operating systems. My screen resolution is only limited to 1366 X 766 pixels so the VM Ware Workstation Unity feature is important. Certain Windows software like ETS' GRE Power Prep II software which I need to install and run to prepare for my Graduate Record Examination this fall 2012 require 1024 X 768 resolution or they won't run at all.

It's just a damn shame that VM Ware is slow to fully support GNU/Linux platforms with their premiere Workstation software.

---

### Post by Welly Wu on 2012-06-09
Riko,

Did you modify the patch file in any way to make it work with VM Ware Workstation 8.0.3?

If so, then please post what you modified so that I can replicate your results.

Thank you.

---

### Post by Welly Wu on 2012-06-09
VM Ware Workstation 8.0.3 64 bit for Ubuntu 12.04 64 bit Long Term Support works. I just loaded Red Hat Fedora 17 64 bit GNU/Linux in a 64 bit guest virtual machine and everything works right out of the box including network access including Internet access.

Riko,

Thank you for your patience and help.

This is solved...for now.

---

### Post by RikoW on 2012-06-10
Glad to hear, that VM WS works for you now.

To get back to your earlier question, I did not modify the patch in any way. The only thing I did was *not* use the script included in the download archive but applied the patch "by hand".

Take care,
 
              Riko

---

### Post by Welly Wu on 2012-06-11
Why does VM Ware Workstation 8.0.3 64 bit always ask me to read and accept the End User License Agreement every time that I launch this software application? After I launch it, it does not list my existing VM Ware Workstation virtual machines. I have to find them and open them manually. How do I solve these problems?

---

### Post by Welly Wu on 2012-06-15
I had another major problem trying to uninstall VM Ware Workstation 8.0.3 64 bit and it consistently failed. Then, I followed the official VMWare how-to remove VM Ware Workstation. I tried to install VMWare Workstation 8.0.4 64 bit for GNU/Linux and it keeps telling me that the VMWare installer can not continue if there are running virtual machines. I did a search on Google for this specific error message and there was a solution. However, the solution does not work. Now, I can not install any VMWare software products on my Ubuntu 12.04 64 bit Long Term Support GNU/Linux host operating system.

I am done with VMWare.

I refuse to use VMWare software products and services in the future. Furthermore, I can not afford to keep upgrading to newer versions because I live on a fixed monthly budget and I need to keep my bills to a bare minimum.

I am going to have to waste the $120.00 USD that I spent to purchase VMWare Workstation 8 and throw it in the garbage where it belongs.

I switched to Oracle Virtualbox. It works. It is fully supported in Ubuntu GNU/Linux. I have no problems with my guest virtual machines. It is available for free and it is open source software virtualization technology.

This thread is solved. I stopped using VMWare software products as of today and in the future.

---

### Post by dcstar on 2012-06-16
> **Welly Wu said:**
> 
........
I am done with VMWare.

I refuse to use VMWare software products and services in the future. Furthermore, I can not afford to keep upgrading to newer versions because I live on a fixed monthly budget and I need to keep my bills to a bare minimum.

I am going to have to waste the $120.00 USD that I spent to purchase VMWare Workstation 8 and throw it in the garbage where it belongs.

I switched to Oracle Virtualbox. It works. It is fully supported in Ubuntu GNU/Linux. I have no problems with my guest virtual machines. It is available for free and it is open source software virtualization technology.

This thread is solved. I stopped using VMWare software products as of today and in the future.

The Virtualization forum has threads on how to patch VMware Workstation/Player to install on 12.04. I - and many others - successfully use this software in 12.04 without any issues.

---

### Post by howefield on 2012-06-16
Thread moved to the "*Virtualization*" forum.

---

### Post by Welly Wu on 2012-06-16
The VMWare Workstation 8.0.4 64 bit installer keeps telling me that the VMWare installer can not continue if there are running or suspended virtual machines. It wants me to shut down or power off those virtual machines in order to continue to install. I already did a search on Google about this specific error and the solution does not work. I do not have an /etc/rc.d/init.d folder to delete my vm* folders and files. Thus, I can not install VMWare Workstation.

This is what I have already told you previously. This is why I can not use VMWare Workstation 8 64 bit anymore on my Ubuntu 12.04 64 bit Long Term Support GNU/Linux host platform.

I plan to upgrade to Ubuntu 12.10 64 bit in October 2012. It will ship with the new Linux 3.5.x or even the 3.6.x kernel. This means that if I do manage to install VMWare Workstation 8.x 64 bit, then it will break once I upgrade to Ubuntu 12.10 64 bit. This means that I will have to wait until someone else codes a patch for that future version of VMWare Workstation 8.x to work with Ubuntu 12.10 and Linux kernel 3.5.x or 3.6.x.

What this really means is that I will have to keep repeating this cycle every 6 months as I continue to upgrade Ubuntu 64 bit.

Why should I do this?

Oracle Virtualbox is in the Ubuntu Software Center and it is fully supported. I have no problems using it. My guest virtual machines work perfectly. It is free and open source software. I can upgrade to future versions of Ubuntu 64 bit and it will continue to work properly without any errors or problems because it is fully supported.

I just can not afford to keep upgrading VMWare Workstation for $99.00 USD as an existing customer in the future years. At most, I can afford to spend upwards of $70.00 USD for annual subscriptions for software products or services. That's it. In fact, I am about to cut my third monthly bill for WiTopia personal VPN basic at $5.99 USD per month by switching over to their personal VPN PRO service for $70.00 USD annually to save more money and to get 256 bits VPN over SSL through their OpenVPN protocol.

I am done with VMWare products and services. I am not going to continue to be their customer anymore. I just can not afford it and there are legitimate technical reasons why I don't want to play this dicey patch and upgrade charade anymore.

Oracle Virtualbox works right out of the box and it is free. I have no problems with it at all. This is what I am going to use in the future.

By the way, my best friend will give me another financial gift to purchase Microsoft Windows 8 PRO 64 bit and Office 2012 Professional Plus 64 bit. Montclair State University requires its students, faculty, and staff to use the latest version of Microsoft Windows and Office for their degree and certificate programs. I already checked with the Graduate school and the Graduate English Department.

I plan to use Oracle Virtualbox to install Microsoft Windows 8 PRO and Office 2012 Professional Plus 64 bit after my best friend gives me the money to purchase it on my own this October 2012.

Don't get me wrong. VMWare makes good products and services. Workstation 8 is a solid product. It just has finicky support issues with Ubuntu 12.04 64 bit Long Term Support. Officially, VMWare has not yet included it on its list of supported platforms. This is why people have to resort to unofficial, third-party, patches to make it work properly. This represents a security risk even though these patches are safe to use. It is for this reason that I decided to switch to Oracle Virtualbox permanently.

---

### Post by Welly Wu on 2012-06-22
I finally got VMWare Workstation 8.0.4 64 bit for Ubuntu 12.04 64 bit Long Term Support GNU/Linux working properly. How I did it was to follow the official VMWare manual removal of VMWare Workstation 8 on GNU/Linux. Then, I could install VMWare Workstation 8.0.4 64 bit for GNU/Linux properly. I modified the patch file to reflect Workstation and Player 8.0.4 and 4.0.4 respectively and I applied the patch. I entered in my license key. Now, it works properly.

This took me the better part of almost one week to figure out the solution.

I do not plan to use VMWare Workstation 8.x 64 bit. I will continue to use Oracle Virtualbox because it works properly and it is fully support in Ubuntu.

This is solved again.

---

