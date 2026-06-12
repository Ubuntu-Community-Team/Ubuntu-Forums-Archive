---
title: "[SOLVED] VMware - free, for me or an organization?"
date: 2008-08-19
forum: Virtualisation
---

### Post by melbs on 2008-08-19
I currently use Virtual Box and it's great. I was wondering if VMware is the same type of program? Also, is it free? I use Virtual Box to work with ubuntu on my windows lap top and to ssh into my desktop computer which is running ubuntu. I hear my boss mention VMware to deal with some server stuff so I was wondering if it is the same concept or program as Virtual Box? thanks yet again :)

---

### Post by HalPomeranz on 2008-08-19
There are multiple versions of VMware.  The basic "Server" and "ESX Server" products are free-- they allow you to create and run simple virtual machines, but lack a lot of the bells and whistles of the commercial "ESXi Server" product.  The "Player" product is also free, but that just lets you run virtual machines that have been created by somebody else.

"Server" is the VMware product most similar to Virtual Box-- it allows you to run stand-alone virtual machines inside of a normal host OS like Ubuntu or Windows.  It's appropriate for a personal machine where you need to occasionally run a virtual machine (like my Ubuntu laptop where I run Windows inside a virtual machine for the occasional Windows-specific task I just can't do in Linux).  "ESX Server" replaces the host OS with a stripped-down kernel that's supposedly optimized for running virtual machines.  You would typically use this in a data-center environment where you're doing server consolidation type applications.

---

### Post by y@w on 2008-08-19
Yes, VMware server is free for personal or business use. Just to clarify, ESXi is the free product, ESX is still pay-for. You then pay for the management tools that go on top of ESXi should you choose to use them. The management tools are where your value is going to come from if you're looking to compare VirtualBox with VMware, but even the free parts of VMware are very solid.

---

### Post by HalPomeranz on 2008-08-19
> **y@w said:**
> Just to clarify, ESXi is the free product, ESX is still pay-for.

Sorry, y@w is right here.  I got the versions backward in my posting above.

---

### Post by melbs on 2008-08-19
So if I have Virtual Box on my machine is that considered a "virtual machine"?

---

### Post by billgoldberg on 2008-08-19
> **melbs said:**
> So if I have Virtual Box on my machine is that considered a "virtual machine"?

The OS you run through virtual box is considered a virtual machine.

Just having virtual box installed doesn't make your os a virtual machine.

---

### Post by y@w on 2008-08-19
> **HalPomeranz said:**
> Sorry, y@w is right here.  I got the versions backward in my posting above.

Yeah, I'm curious to see what the future holds for ESX.. It sounds like ESXi is better than ESX and free, though I probably am missing something.

---

### Post by y@w on 2008-08-19
> **billgoldberg said:**
> The OS you run through virtual box is considered a virtual machine.

Just having virtual box installed doesn't make your os a virtual machine.

The physical machine you are running VirtualBox (or any virtualization software) on is usually referred to as the host or server and the actual instances running inside are referred to as guests.

---

### Post by melbs on 2008-08-19
Okay,  I think I get it - the ubuntu OS I have installed on my Virtual Box is the virtual machine..

Is the only difference between ESXi and ESX is that one costs money and has "more features". Are they the same program but the free version is stripped down?

It sounds like installing the "server" VM product and putting it on my desktop computer is what I'm looking to do. Are the "Server" and "ESX Server" the same type of product? I'm trying to think if I download and get familar with one download - if my work uses another will it benefit me that I have used the other VM product, although different.

---

### Post by y@w on 2008-08-19
> **melbs said:**
> Okay,  I think I get it - the ubuntu OS I have installed on my Virtual Box is the virtual machine..

Exactly.

> **melbs said:**
> Is the only difference between ESXi and ESX is that one costs money and has "more features". Are they the same program but the free version is stripped down?

It sounds like installing the "server" VM product and putting it on my desktop computer is what I'm looking to do. Are the "Server" and "ESX Server" the same type of product? I'm trying to think if I download and get familar with one download - if my work uses another will it benefit me that I have used the other VM product, although different.

I'm not sure about the difference between the two, but both are only going to be supported on certain hardware. You're going to have to get server hardware in order to do it. It'll probably work on other hardware but it will be missing some features. I'd run GSX (VMware Server) on top of a different OS (either Ubuntu or CentOS).

---

### Post by overdrank on 2008-08-19
Moved Virtualization  :)

---

