---
title: "Chromebooks for running other Linux distros"
date: 2014-06-02
forum: Ubuntu, Linux and OS Chat
---

### Post by sivanes on 2014-06-02
Hi!  I'm learning programming at the moment on a 4 y/o Lenovo powered by  Windows 7. I would like to finally make a switch to Linux (not decided  on which one yet, could be Mint, could be Ubuntu, could be something  else) and have no problem spending around $350 on a laptop that would be  designated mostly for learning Linux and doing development and not much  else. HP's nicest Chromebooks are right in that price range and sound  tempting since they were initially built for Linux, and it seems like  they are now a popular choice for a budget Linux machine. Do they have  any big advantages over regular laptops in the same price range that  come with Windows. Also, if you know of some realistic and reliable  OS-free laptop options in that range for US, aside from xotic, please  let me know.

---

### Post by TheFu on 2014-06-02
I don't have an HP chromebook. I have a newish Acer C720.  Using it now.
If I were doing it all over again, I'd get the 13" Dell with the same CPU in this chromebook.  The Celeron U..... CPU is AWESOME - 8+ hrs of real battery.  I had to upgrade the SSD from 16G to 128G, add a USB3 --> GigE network adapter, and buy a HDMI --> VGA converter so I could do presentations.  By the time I did all the upgrades, I think it cost more than a Dell with more capabilities.

The Dell came with a 500G HDD, which I would much prefer, wired GigE built-in, and a normal keyboard, so I wouldn't keep powering off the netbook because the GD power button is where the DEL key should be.  Idiots whoever designed these chromebook keyboards.

BTW, it has been 3 months and I don't often hit the power key anymore, but for the first month, I was powering off the machine 20-50 times a day by accident.  I was pissed.  Idiots.  Of course, YMMV.


Oh - forgot to ask - which language?  Scripting languages don't need much CPU, but if you are compiling huge projects in C/C++, Java (or any JAVA/Android) then you'll want a Core i7 with 16G of RAM).  Small C/C++ projects (like most 2-3 man teams create) don't need much CPU at all or RAM.  For Android development, I've decided that a remote desktop into a $400 desktop/workstation is the best option over spending $2500 for a capable laptop.

---

### Post by tgalati4 on 2014-06-02
Or, save yourself some money and set up your Lenovo for dual-boot.  Look for a used Thinkpad in the meantime as a linux development machine.

---

### Post by sivanes on 2014-06-02
> **TheFu said:**
> I don't have an HP chromebook. I have a newish Acer C720.  Using it now.
If I were doing it all over again, I'd get the 13" Dell with the same CPU in this chromebook.  The Celeron U..... CPU is AWESOME - 8+ hrs of real battery.  I had to upgrade the SSD from 16G to 128G, add a USB3 --> GigE network adapter, and buy a HDMI --> VGA converter so I could do presentations.  By the time I did all the upgrades, I think it cost more than a Dell with more capabilities.

The Dell came with a 500G HDD, which I would much prefer, wired GigE built-in, and a normal keyboard, so I wouldn't keep powering off the netbook because the GD power button is where the DEL key should be.  Idiots whoever designed these chromebook keyboards.

A 13" Dell Chromebook? All I could find is the 11" one and it's not even going to be out until late July. 

By the way, big question, in Chromebooks I see the Celeron U's and similar CPU's that are significantly slower than something like a Core i3 that you will see in Windows laptops. I understand that that leads to a much longer battery life, but is it powerful enough not for Chrome OS, but for a much bigger Linux distro in which I will code, run PostgreSQL, surf the web, stream media, etc often all at the same time?

---

### Post by sivanes on 2014-06-02
> **tgalati4 said:**
> Or, save yourself some money and set up your Lenovo for dual-boot.  Look for a used Thinkpad in the meantime as a linux development machine.
I am a little hesitant to use the Lenovo I have now. It's a b560, it wasn't that fancy of a laptop to begin with, it has collected a lot of crap and wear and tear over all the years, I would rather not burden it with a whole second OS. So, the ThinkPad is a good brand for the purpose? They must be as only the refurbs fall into my price range, ha.

---

### Post by TheFu on 2014-06-02
> **sivanes said:**
> A 13" Dell Chromebook? All I could find is the 11" one and it's not even going to be out until late July. 

By the way, big question, in Chromebooks I see the Celeron U's and similar CPU's that are significantly slower than something like a Core i3 that you will see in Windows laptops. I understand that that leads to a much longer battery life, but is it powerful enough not for Chrome OS, but for a much bigger Linux distro in which I will code, run PostgreSQL, surf the web, stream media, etc often all at the same time?

* my C720 runs Ubuntu 14.04 fine. The CPU is like a Core i5 from 3 yrs ago - plenty powerful for non-Java stuff.
* The lack of RAM on most chromebooks is an issue. Other laptops don't have that limitation.
* Dell 13" inspiron - NOT a chromebook.  It was $280 over Xmas as a "slickdeal". You'll have to be good to find it. 2 Dell chat-drones claimed it didn't exist, then I found it on their site for $350. If you have time, use bensbargains and slickdeals to watch for a deal on these. It has been a few months since I looked, so I don't know the status - you'll need to be careful about the CPU - if battery life matters to you.

The CPU (really the GPU) in the C720 handles video easily. Since you last got a laptop/computer, the world has changed for non-flash video. It is all decoded in hardware now.

So ... if you need more than 2G of RAM ... ever ... do not get a chromebook. The RAM is soldered to the MB - no upgrades. The only reason I got one was that I'd been running ubuntu 12.04 on a 2G Atom netbook for a few years and never had RAM issues with my workloads.  My C720 runs Ubuntu 14.04 (stripped down with LXDE), so it handles that fine. Still - for someone unsure, it probably isn't a good idea to go too cheap.

Found that Dell I was mentioning. "Dell Inspiron 11 i3137-3751sLV"  used ones are $270 on Amazon today or new on NewEgg for $350. It uses the Celeron 2955U, which gives the extra long battery life and reasonable performance. It that isn't important, a Core i3/i5 system would provide much more CPU.  My travel-in-car laptop is a Core i5 1080p 15inch monster. I only use the chromebook for airplane travel stuff where size, weight and battery life matter much more than performance.

---

### Post by tgalati4 on 2014-06-03
When I see "linux development" that can mean a lot of things.  I interpret that to mean testing code in multiple environments and that means virtual machines and that means lots of RAM.  I also interpret that to mean compiling code, possibly the kernel, which can take a couple of hours on a powerful machine.  So a business-class Thinkpad, $2k when new, $300 used, can be repurposed with maxed out RAM, a new hard disk or SSD and that would make a suitable "linux development" machine.  

Has anyone compiled the kernel on a Chromebook or on a Dell 13" Inspiron?  How long did it take?

Compiling the kernel on a Thinkpad T43p (2006 vintage, single core Centrino, 2.18 GHz, 2GB RAM, which cost me $250 in 2009, new 320GB fast disk $100) took just over 2 hours.

If you are just surfing the web and not compiling anything, then a Chromebook would be sufficient.

---

### Post by monkeybrain20122 on 2014-06-03
With $350 you can get a refurbished laptop with very decent specs instead of a Chrome book (which is a rather limited machine to my mind) My main laptop is a Dell core i5 intel with 4G of ram which does everything I need and unity is smooth as butter, costs me only $300 (could have gotten it cheaper if I shopped around a bit more or bargained with the store. :) But the guy charged me nothing to replace the hard disk with a bigger one and sold me a webcam for < $10)

---

### Post by Tar_Ni on 2014-06-03
Just go on Craiglist or Ebay and look for a second-hand laptop. 350$ should allow you to get a decent laptop in good condition. Then you can easily turn it into a Linux machine. Ubuntu does support a wide range of hardwares out-of-the-box. That's what I did, I got a nice 15'' screen Asus laptop with 4GB RAM AMD vision proc and 320GB hardrive. Ubuntu Trusty Tar runs great on it.

Go Green and save money!

---

### Post by sivanes on 2014-06-05
Ok, thank you all so much for your input. Off I go searching for a refurb. 

> **TheFu said:**
> 
Oh - forgot to ask - which language?  Scripting languages don't need much CPU, but if you are compiling huge projects in C/C++, Java (or any JAVA/Android) then you'll want a Core i7 with 16G of RAM).  Small C/C++ projects (like most 2-3 man teams create) don't need much CPU at all or RAM.  For Android development, I've decided that a remote desktop into a $400 desktop/workstation is the best option over spending $2500 for a capable laptop.
I'm studying Python and the Django framework at the moment. And yes, I will be learning how to test code in separate environments, compiling and all that other good stuff on this machine that I will end up getting.

---

### Post by TheFu on 2014-06-05
Python and Django don't need much CPU.   No compiling involved.  It is only if you plan to learn Java that RAM and CPU become important. A minimal system today comes with enough for C/C++/Fortran/Pascal/whatever work already. It is just Java languages that suck the CPU/RAM.

I'd go with that low-end Dell 11inch netbook still for under $340. Check the deal websites. Just be careful about the CPU and RAM upgrades.  More powerful CPUs suck power and claimed 5+ hrs of battery when new turns into 2-3hrs in a few years.  I have a Core i5 laptop that cannot make it 2 hrs on battery now.  However, the Celeron 2955U can go and go and go like a tablet.  Check the CPU comparison websites to see that it is about as fast as a Core i5 from 3 yrs ago - not really giving up much performance for so much more efficiency.

So - you have all the info.

---

