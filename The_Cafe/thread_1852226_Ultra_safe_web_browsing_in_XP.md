---
title: "Ultra safe web browsing in XP"
date: 2011-09-29
forum: The Cafe
---

### Post by deadfraggle on 2011-09-29
At work, our audio production PC needs XP for a particular version of software we like.  Unfortunately, I find XP to be very prone to malware and virus attacks no matter what preventative measures I employ. So, in order to keep the computer "safe", in the network settings I entered the wrong gateway address, and fake DNS servers.  This gives the PC access to the internal network, but not the internet.

However web access is still handy to have on the PC.  To add the capability, I installed VirtualBox and created an Ubuntu virtual machine with "bridged" network card access.  This in effect made the router see the virtual machine as another different PC, and assigned it it's own IP address.  So now XP is cut off from the internet, but the virtual Ubuntu machine has full access in a fancy sandbox kind of way.  If anything happens to the virtual machine, I can easily restore a snapshot (save state) of when it was functioning properly.

I guess I could have installed XP in VirtualBox, but I find Ubuntu inherently safer in the first place.  At least I have never experienced any malware problems with Ubuntu.  (Do such things exist?)  This also gives me a chance to introduce my colleagues at work to Linux without actually forcing them to use it.

---

### Post by KiwiNZ on 2011-09-29
Why do they need access to the Web? Do they use particular sites? If they are accessing just a few particular sites apply Firewall rules to allow that traffic and that traffic only.

---

### Post by deadfraggle on 2011-09-29
> **KiwiNZ said:**
> Why do they need access to the Web? Do they use particular sites? If they are accessing just a few particular sites apply Firewall rules to allow that traffic and that traffic only.

One example where users would need web access is to get to information off different music artist websites.  Impossible to predict.  Also, I've seen Microsoft sometimes pushing updates even with Automatic Updates off.  And if Automatic Updates are off, XP keeps popping up with a stupid warning.  With XP cut off from the net, Automatic Updates can be on, but with no effect and warnings.

Also, no need for antivirus or other protection software means less overhead and a PC that runs just that much better.

---

### Post by KiwiNZ on 2011-09-29
> **deadfraggle said:**
> One example where users would need web access is to get to information off different music artist websites.  Impossible to predict.  Also, I've seen Microsoft sometimes pushing updates even with Automatic Updates off.  And if Automatic Updates are off, XP keeps popping up with a stupid warning.  With XP cut off from the net, Automatic Updates can be on, but with no effect and warnings.

Also, no need for antivirus or other protection software means less overhead and a PC that runs just that much better.

Running business machines without protection is fool hardy at best.

---

### Post by wirepuller134 on 2011-09-29
I have to agree with Kiwinz here.

---

### Post by Quake on 2011-09-29
> **deadfraggle said:**
> 
Also, no need for antivirus or other protection software means less overhead and a PC that runs just that much better.


BAD IDEA!!!! Having an anti-virus is a must!! Because someone can plug a USB thumb drive or a USB flash disk and infect the computer.

---

### Post by el_koraco on 2011-09-29
> **KiwiNZ said:**
> Running business machines without protection is fool hardy at best.

Well, with the current config, the virtual machine is the protection, since it's the only one exposed, right?

---

### Post by szymon_g on 2011-09-29
1. use anti-virus /ms essentials is lightweight and free to use even in commercial situations- but read its EULA/. it is usefull not only for internet, but also when you transfer data to it /like: exchange documents etc/
2. you can always use sandboxie - [http://www.sandboxie.com](http://www.sandboxie.com) to sandbox applications
3. using EMET wouldn't hurt

---

### Post by deadfraggle on 2011-09-29
> **KiwiNZ said:**
> Running business machines without protection is fool hardy at best.

I've been the ad hoc system administrator here for about 10 years, and all the malware infections I've seen have come from the internet.   No antivirus ever stops every stupid user act.  Vista and Win7 with UAC and parental controls have made my job easier, but XP is not so secure.

No files are kept on the production PC, so If something *does* get into it (via a usb key, network, etc.), all I need to do is zap the partition and reinstall.  I'm predicting I'll being doing that much less now with my current setup.

> **el_koraco said:**
> Well, with the current config, the virtual  machine is the protection, since it's the only one exposed,  right?

Yep, only Ubuntu is exposed.

---

### Post by KiwiNZ on 2011-09-29
> **deadfraggle said:**
> I've been the ad hoc system administrator here for about 10 years, and all the malware infections I've seen have come from the internet.   No antivirus ever stops every stupid user act.  Vista and Win7 with UAC and parental controls have made my job easier, but XP is not so secure.

No files are kept on the production PC, so If something *does* get into it (via a usb key, network, etc.), all I need to do is zap the partition and reinstall.  I'm predicting I'll being doing that much less now with my current setup.



Yep, only Ubuntu is exposed.

Is it connected to your Lan when in Virtual machine?

---

### Post by collisionystm on 2011-09-29
> **deadfraggle said:**
> At work, our audio production PC needs XP for a particular version of software we like.  Unfortunately, I find XP to be very prone to malware and virus attacks no matter what preventative measures I employ. So, in order to keep the computer "safe", in the network settings I entered the wrong gateway address, and fake DNS servers.  This gives the PC access to the internal network, but not the internet.

However web access is still handy to have on the PC.  To add the capability, I installed VirtualBox and created an Ubuntu virtual machine with "bridged" network card access.  This in effect made the router see the virtual machine as another different PC, and assigned it it's own IP address.  So now XP is cut off from the internet, but the virtual Ubuntu machine has full access in a fancy sandbox kind of way.  If anything happens to the virtual machine, I can easily restore a snapshot (save state) of when it was functioning properly.

I guess I could have installed XP in VirtualBox, but I find Ubuntu inherently safer in the first place.  At least I have never experienced any malware problems with Ubuntu.  (Do such things exist?)  This also gives me a chance to introduce my colleagues at work to Linux without actually forcing them to use it.
 
Coincidentally I found this today! I think it's just what you are looking for. [http://www.kace.com/products/freetools/secure-browser/](http://www.kace.com/products/freetools/secure-browser/) :P

---

### Post by deadfraggle on 2011-09-29
> **KiwiNZ said:**
> Is it connected to your Lan when in Virtual machine?

It has access to the internet, but it's not part of our workgroup.  No default access to the network shares.  Would it be a problem if it was?

---

### Post by KiwiNZ on 2011-09-29
> **deadfraggle said:**
> It has access to the internet, but it's not part of our workgroup.  No default access to the network shares.  Would it be a problem if it was?

If it directly links to the Web eg it's own router, then the risk is reduced. If the connection is via the Lan to the router, then the is is high. Even if the former applies an infection can occur and if such things as USB drives connected then the risk is elevated further.

Best practice in a Business environment is safety first , experiment last.

---

### Post by deadfraggle on 2011-09-29
> **collisionystm said:**
> Coincidentally I found this today! I think it's just what you are looking for. [http://www.kace.com/products/freetools/secure-browser/](http://www.kace.com/products/freetools/secure-browser/) :razz:

I'm assuming for that browser to work, XP would need internet access, giving defacto internet access to IE, which is undesirable.


> **KiwiNZ said:**
> Best practice in a Business environment is safety first , experiment last.

The production PC has always had Internet access previously, so I see it as more of a lockdown then an experiment.


> **KiwiNZ said:**
> If it directly links to the Web eg it's own router, then the risk is  reduced. If the connection is via the Lan to the router, then the is is  high. Even if the former applies an infection can occur and if such  things as USB drives connected then the risk is elevated further.

The virtual Ubuntu is as if it was like any other computer connected to the network.  (EDIT: The DHCP on the real router assigns an IP to the Ubuntu client.)  I can't see it being any riskier than if I had Ubuntu as the main operating system with the same access.  Safer because it's contained within Virtualbox.  Even if the user downloads a file in the virtual Ubuntu that might be hazardous to XP, there's no easy way for the user to transfer the file to the XP host.

To explain the setup better, both the XP host and the Ubuntu client share the same network card.  This is in contrast with most basic virtual machine setups, where the client uses a virtual network card that piggy backs on the existing network connection.  My XP host however, does not have the information needed (gateway & DNS server addresses) to get on the internet; but the Ubuntu client does.

---

### Post by Dr. C on 2011-09-29
> **KiwiNZ said:**
> If it directly links to the Web eg it's own router, then the risk is reduced. If the connection is via the Lan to the router, then the is is high. Even if the former applies an infection can occur and if such things as USB drives connected then the risk is elevated further.

Best practice in a Business environment is safety first , experiment last.

This is a very valid point. In particular the vulnerability of the host to an infected USB drive, floppy etc. Personally I would have Ubuntu as the host and the locked down XP as the guest as a safer option. 

It is possible to deny Internet access to the host while allowing Internet access to the guest using VirtualBox with the adapter on bridged mode with Ubuntu as the host and either Windows 7 or Windows XP as the guest. I have not tried this the other way around.

---

### Post by deadfraggle on 2011-09-29
> **Dr. C said:**
> This is a very valid point. In particular the vulnerability of the host to an infected USB drive, floppy etc. Personally I would have Ubuntu as the host and the locked down XP as the guest as a safer option. 

Being the ad hoc administrator means I have all the responsibilities, but none of the power.  Having Ubuntu as the main OS would not go over well with the rest of the employees.  I almost had to theaten to quit in order for everyone to switch to Firefox.  Upgrading everyone to Vista and 7 was almost as unpleasant.  (Haha - I love parental controls!  It's set so only authorized programs are allowed to run.  That cut our malware problems done to 0 so far.)

I am confidant with my current setup as far as Internet safety is concerned.  But the USB problem should be addressed.  There's some kind of group control I can activate in XP, but will have to look it up.  Just not tonight.

---

### Post by LowSky on 2011-09-29
That PC doesn't need to be online at all, and it should have a very limited if any access to the network as well.

The idea of requiring internet access from a production machine is almost crazy. Might sound nuts but why have it run on a PC at all.

Why not build a server. Install Windows Virtually and run the application from any of the other PC's in the company. That way the application in question is available to anyone on the network, and virtualization allows you more control over the system.

---

### Post by deadfraggle on 2011-09-30
> **LowSky said:**
> That PC doesn't need to be online at all, and it should have a very limited if any access to the network as well.

The idea of requiring internet access from a production machine is almost crazy. Might sound nuts but why have it run on a PC at all.

Why not build a server. Install Windows Virtually and run the application from any of the other PC's in the company. That way the application in question is available to anyone on the network, and virtualization allows you more control over the system.

Ummm... community radio station, 12 PCs, 3 laptops, no budget.  I do what I can, but much is out of my control.  The production PC needs network access for the common shares containing everyone's production files, documents, and to the music archive.  The users could learn to live without internet, but I felt it could add it safely.  The only time it might be problem is when it was busy and there wasn't enough public PCs to go around.

Will need to install antivirus protection after all to protect from rogue files on the network.  I'll give it proxy access to the internet through another PC so it can stay updated.

---

### Post by Dangertux on 2011-09-30
Silly question that may already have been answered, buthave you considered trying to get the windows app to run in wine? Wine security issues aside it is a much less painful , costly and dangerous proposition in this case. 

Failing that I am in support of windows vm, ubuntu guest. As the current configuration is neither optimal nor really doing much for your security.

---

