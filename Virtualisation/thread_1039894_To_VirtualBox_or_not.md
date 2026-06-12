---
title: "To VirtualBox or not"
date: 2009-01-15
forum: Virtualisation
---

### Post by GuiGuy on 2009-01-15
Hi all,
I'm more or less retired these days but need to continue to maintain windows code for an application that I've developed over the last twenty or so years. These days I use Codegear's Delphi for that on the one and only Windows box in my house. (Linux everywhere, right? ;))

Anyway, the Windows Box died today. I'd been looking at running WinXP and Delphi 2007 out of Virtualbox on my office Ubuntu PC. However, its an AMD AM2 X2, 3800+ with 3G RAM and I found the experience too slow. From time to time WinXP also crashes due to memory paging errors.

To my point; is anyone here using Virtualbox to run their Windows development system and compiler? If so, what level of hardware would be needed to get reasonable & reliable performance, if it's at all possible?

I'd really appreciate your feedback before I spend the hard earned on a super computer :D

Cheers

---

### Post by HermanAB on 2009-01-15
Here is Virtualbox running Windows XP on my Eee PC 701:  [http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)

In my measurements, Virtualbox and VMware has about 3% overhead, so you won't notice any slowdown and can run it on pretty much anything with enough RAM.

Cheers,

Herman

---

### Post by ushimitsudoki on 2009-01-15
I run VirtualBox in XFCE and sadly I have to do some Microsoft Office development (maintenance) in there from time to time. Not quite the same as compiling; these are large legacy databases and spreadsheets.

The performance is acceptable for me: I have 8G ram (2G for VM) and quad core. It helped a bit I thought to add the RAM and make sure that the VT-x/AMD-V option was enabled - I also set the swap up to a shared folder because if I left it at the windows default I kept having out of memory problems.

That being said, the performance I enjoy under VirtualBox on this machine is superior to that of the machine I was working on previously that had Windows installed natively.

---

### Post by GuiGuy on 2009-01-15
> **HermanAB said:**
> Here is Virtualbox running Windows XP on my Eee PC 701:  [http://aeronetworks.ca/eeepc-mdv-howto.html](http://aeronetworks.ca/eeepc-mdv-howto.html)

In my measurements, Virtualbox and VMware has about 3% overhead, so you won't notice any slowdown and can run it on pretty much anything with enough RAM.

Thanks for that. I'm seeing the same for virtualbox when I open WinXP on it. Performance is fine at this point. But when it comes to loading something like COdegear Delphi 2007 and then a large project (about 800,000 lines of code), the system really starts to slow down. Compiling the application takes much longer than I am usually prepared to wait for.

To qualify my question, if I installed ubuntu on the a current state of art processor and say 4G RAM, could i expect a corresponding performance increase or would it only be a minor improvement?

In the meantime, I'm going to read some of the stickies at the top of this forum. 

Thanks

---

### Post by GuiGuy on 2009-01-15
> **ushimitsudoki said:**
> The performance is acceptable for me: I have 8G ram (2G for VM) and quad core. It helped a bit I thought to add the RAM and make sure that the VT-x/AMD-V option was enabled - I also set the swap up to a shared folder because if I left it at the windows default I kept having out of memory problems.

That being said, the performance I enjoy under VirtualBox on this machine is superior to that of the machine I was working on previously that had Windows installed natively.

Excellent. Noted. 

Cheers

---

