---
title: "Getting into linux"
date: 2016-03-18
forum: Ubuntu, Linux and OS Chat
---

### Post by paulkoning on 2016-03-18
Hello Forum,

I have been trying to get into linux for quite a while now but for some reason my laptop has had issues with all of the distro's I have tried so far. I have tried the following distro's: Ubuntu 15.04, Debian 7, Linux Mint 17.2, Elementary OS and Fedora. 

With all of these distro's I have had the same issues, kernel panics. And since it's a proper lock-up it doesn't show anything in the logs. So you might be wondering, have I tried a crash kernel? Yes I have, but for some reason it never switches to the crash kernel after crashing, it simply remains frozen and can only be the only thing I can do is hard reset the machine. 

Then I thought it might have something to do with display drivers so I installed the latest opensource intel drivers, which didn't fix anything at all. Now i've given up and I'm back on windows 10. Trying to debug the os and asking around for help was taking up too much of my time.

Are there any tips you guys could give me?


Yours sincerely,

Paul

Specifications:
i5 4200u(intel hd graphics 4400)
2x 4Gb ddr3-800mhz dual channel 
240gb transcend SSD

---

### Post by edu6 on 2016-03-18
Hi, pauloning.

First, I'm not an expert. Second, sorry about my english.

My first try it would be to update my BIOS. I think that it's always a good practice. The second, disable UEFI on the BIOS. Considering your SSD, I think that [this link]("https://sites.google.com/site/easylinuxtipsproject/ssd") it's a good thing.

How are you installing? Live DVD? USB stick? Dual boot?

I think that you may forget about the video drivers.

[]'s
Edu

---

### Post by Rocky_Bennett on 2016-03-20
I think it is a VERY bad idea to update your BIOS.

---

### Post by deadflowr on 2016-03-20
> **Rocky_Bennett said:**
> I think it is a VERY bad idea to update your BIOS.
What's your reasoning behind that?

---

### Post by Rocky_Bennett on 2016-03-20
From experience and from reading, many more things can go wrong with updating a BIOS than can be fixed. Why would anyone update a BIOS? What would one hope to accomplish?

---

### Post by SantaFe on 2016-03-20
> **Rocky_Bennett said:**
> From experience and from reading, many more things can go wrong with updating a BIOS than can be fixed. Why would anyone update a BIOS? What would one hope to accomplish?


[LIST]
[*]You can gain BIOS support needed for newer hardware.
[*]A bug in the existing BIOS firmware is fixed with the update.
[*]You can gain additional functionality or increased performance.
[/LIST]

To list just 3 off the top of my head. ;)

---

### Post by ian-weisser on 2016-03-21
Need elaboration:
When do kernel panics occur? At boot? After login? When using a specific application? Randomly after two hours of use?
How do you know it's a kernel panic? What do you see when you get a kernel panic? GUI frozen? Mouse still moves? GUI crashes and you get console? What does it say?

---

### Post by oldfred on 2016-03-21
What brand/model system.
Is Windows in UEFI boot mode or BIOS boot mode. You would want Ubuntu in same boot mode.

And back with 15.04, the Intel i5-4200 would have been a newer system and software, kernels, & drivers may not have caught up with new hardware yet.

Have you tried current versions 15.10 or 14.04.4? 
Or even tested 16.04, which will not be released until the end of April, but currently seems to work. Still resolving bugs, and may break, so best not to use 16.04 as main install until after released.

---

### Post by paulkoning on 2016-03-22
I have tried 15.10 15.04 and 14.04LTS. I have also switched kernels but it didn't help.

edit:
I also tried installing the opensource Intel graphics drivers. My reasoning behind this was an experience I had when i bought the laptop.

When I first bought the laptop the intel HD (windows) driver was freezing my up windows the exact same way. But this was solved by manualy updating the drivers with the newest ones straight from intel.

Brand is acer E1-572
Windows is in UEFI bootmode.

Edit:
My apologies for posting in the wrong section, although I don't remember posting this in the chat section.

---

### Post by paulkoning on 2016-03-22
The kernel panics occur randomly, be it 17 minutes or 2 hours. The gui freezes, but not only that. When I the kernel panic everything freezes up. Absolutely no possible input. The only way to get out of it is to force reset with the hardware powerbutton.

edit:
It always occurs within 2-3 hours.

---

### Post by paulkoning on 2016-03-22
Check earlier reply for the driver mention. Installing via usb. 
I don't see how the UEFI vs BIOS would impact stability when windows is running stable. I would guess that BIOS related issues would present regardless of the OS.

---

### Post by oldfred on 2016-03-22
Other Acer
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09](http://members.iinet.net/~herman546/2014_02_09) - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop.html 

But does this model Acer have Bay Trail CPU?

 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by paulkoning on 2016-03-22
> **oldfred said:**
> Other Acer
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09](http://members.iinet.net/~herman546/2014_02_09) - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop.html 

But does this model Acer have Bay Trail CPU?

 Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

The BIOS info does not really help my case unless it really matters if I run UEFI or legacy. Mind you, I had already installed the OS.
The baytrail series of cpu's does not include i3's i5's or i7's. I have an i5-4200u, so no it's not a baytrail cpu.

---

