---
title: "Questions about virtualization"
date: 2008-10-08
forum: Virtualisation
---

### Post by AreonEpta on 2008-10-08
**_Edit: Original problem solved. New problem found in my next post._**

Disclaimer: Nope, didn't read ANY faqs cause I'm at work and have like two minutes to get this going. Please have mercy on my soul. You can reply with links to faqs, or with sarcasm, or with answers; all will be appreciated (or tolerated, ^^ ).

So I just bought a brand new HP DV5-1000us (specs below). I'm about to stick me some Ubuntu on it and I want to have a fully functional emulated Windows on it for primarily software development (computer science major) but also for a lot of gaming too. I have been reading webpage after webpage for the last few months in free time, and have gotten no difinitive answer. I want a virtualization tool with the following:

3d acceleration
64 AND 32 bit support
a GUI (preferably)
ability to stick the required guest OS files in their own partition

If this is at all possible, I'd love to know my options, and then how in the world to go about prepping my fresh system for it. I don't require a huge explanation if there are already how-to's and faqs, but I'll always welcome information tailored to my needs. Thanks in advance.

Areon



Specs:
2.0 Ghz Intel Core 2 Duo, 1066 Mhz, 3 MB cache
4 Gigs of 800 Mhz DDR 2
250 GB, 5200 RPM hard drive
cool stuff
more cool stuff
aids

---

### Post by bradmkjr on 2008-10-08
Well you are probably home from work, but just wanted to give you some solid answers to your questions:

You CPU is [http://processorfinder.intel.com/details.aspx?sSpec=SLB53](http://processorfinder.intel.com/details.aspx?sSpec=SLB53) Which does have Intel Virtualization technology. This is needed for 64bit virtual guest operating systems.

The request for 3d acceleration is tricky, because most virtualization software uses generic or low level virtual hardware, ie 2d video cards. 

I looked at the details of [http://www.parallels.com/products/workstation/features/](http://www.parallels.com/products/workstation/features/) but didn't think it was a good match for you.

I think VMware workstation will be your best match. It offers everything you where asking about:

[http://vmware.com/products/ws/new.html](http://vmware.com/products/ws/new.html)
Support for DirectX 9.0c with Shader Model 2 3D graphics
Supports both 32-bit and 64-bit host and guest operating systems

---

### Post by AreonEpta on 2008-10-11
Thanks alot bradmkjr. This helped alot. I was leaning towards VMWare Workstation for awhile, but was not aware that it supported DirectX 9.0c. That was excellent news. Any idea if it runs games even close to native speeds? Will it tend to work better than wine? Cause I've had some bad luck with wine.

Also, since you seem to be so knowledgeable, I'm having some difficulty getting my Wi-fi and Intel Graphics to work right.

Wi-fi: Broadcom 4321
Graphics: Intel G45 Series

I have no idea how to get the drivers I need for them to work right. Tips from you or anyone else?

---

