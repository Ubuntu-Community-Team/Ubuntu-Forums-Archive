---
title: "Windows BSOD"
date: 2008-02-22
forum: Windows
---

### Post by tcpip4lyfe on 2008-02-22
So I built a new computer and put windows on it. ( I admin 6 ubuntu servers at work, so I just wanna play COD4 when I get home) Everything was great for about 2 weeks and then I started getting Blue screens.  At first I thought it was a driver error so I took everything out and put Vista on it and things were great for about 2 days.  Vista wouldn't blue screen it would just lock up and reboot. So I got fed up with vista and went back to XP and started debugging the BSOD's. 

Here's some output relevant output:

Debugging Details:
------------------

BUGCHECK_STR:  0x1a_781
CUSTOMER_CRASH_COUNT:  2
DEFAULT_BUCKET_ID:  DRIVER_FAULT
PROCESS_NAME:  System
LAST_CONTROL_TRANSFER:  from 8051a6cd to 804f9c37

...............

IMAGE_NAME:  memory_corruption

-------------------

Ok.  We'll that's easy. I got a bad memory module. So I put 1 module in at a time and ran a memtest.  All the memory would fail in different slot but not all the time.  And it would only fail in the 300MB and 2000MB addresses.  

I replaced the power supply already with a 700 watt one.  So now Im thinking maybe the north bridge on the mobo is tweaked or maybe the CPU. I've tried under-clocking the memory, bios updates, CPU test's and new chip set drivers. Anyone have any other recommendations?

---

### Post by PryGuy on 2008-02-22
Probably wrong forum, eh? ;)

---

### Post by tcpip4lyfe on 2008-02-22
> **PryGuy said:**
> Probably wrong forum, eh? ;)

I suppose so but the windows forums are full of kids that don't know what they are talking about. There's a lot of knowledgeable people on this forum.  Just figured I'd give it a shot.

---

### Post by glupee on 2008-02-22
what are your system specs?

---

### Post by Vitamin-Carrot on 2008-02-22
check to make sure you chipset drivers are upto date
check to make sure it isnt a physicle fault in your hardware
check to make sure you buy a console and play cod4 on that instead while installing ubuntu on your pc

:P

---

### Post by justin whitaker on 2008-02-22
> **tcpip4lyfe said:**
> So I built a new computer and put windows on it. ( I admin 6 ubuntu servers at work, so I just wanna play COD4 when I get home) Everything was great for about 2 weeks and then I started getting Blue screens.  At first I thought it was a driver error so I took everything out and put Vista on it and things were great for about 2 days.  Vista wouldn't blue screen it would just lock up and reboot. So I got fed up with vista and went back to XP and started debugging the BSOD's. 

Here's some output relevant output:

Debugging Details:
------------------

BUGCHECK_STR:  0x1a_781
CUSTOMER_CRASH_COUNT:  2
DEFAULT_BUCKET_ID:  DRIVER_FAULT
PROCESS_NAME:  System
LAST_CONTROL_TRANSFER:  from 8051a6cd to 804f9c37

...............

IMAGE_NAME:  memory_corruption

-------------------

Ok.  We'll that's easy. I got a bad memory module. So I put 1 module in at a time and ran a memtest.  All the memory would fail in different slot but not all the time.  And it would only fail in the 300MB and 2000MB addresses.  

I replaced the power supply already with a 700 watt one.  So now Im thinking maybe the north bridge on the mobo is tweaked or maybe the CPU. I've tried under-clocking the memory, bios updates, CPU test's and new chip set drivers. Anyone have any other recommendations?

Which MOBO and chipset?

---

### Post by sayakb on 2008-02-23
@OP
You very well seem to know that your memory has hardware problems. Why don't you replace your RAM?

---

### Post by tcpip4lyfe on 2008-02-23
> **glupee said:**
> what are your system specs?


CPU: intel quad core q6600 @ 2.4ghz
RAM: 4 gigs of ram (only 2 get reported now that im  looking at it again)
Mobo: Gigabyte p35-ds3l 
GFX: gforce 8800 gtx

---

### Post by tcpip4lyfe on 2008-02-23
> **LinuxIsInnovation said:**
> @OP
You very well seem to know that your memory has hardware problems. Why don't you replace your RAM?

Im not sure it's the memory.  Before I start a RMAing to newegg I want to make sure.  Could be the motherboard or CPU but Im not sure how to test it.

---

### Post by rickyjones on 2008-02-23
Grab some memory that you know will test good and throw it in the motherboard. Test the memory. If you are still getting memory errors then you know that it is an issue with the motherboard.

Obviously since your RAM sticks are having errors you need to rule out memory. Just grab some sticks from a friend or from a local computer store as a test. 

-Richard

---

### Post by sayakb on 2008-02-24
> **tcpip4lyfe said:**
> CPU: intel quad core q6600 @ 2.4ghz
RAM: 4 gigs of ram (only 2 get reported now that im  looking at it again)
Mobo: Gigabyte p35-ds3l 
GFX: gforce 8800 gtx

*wink* That looks like my exact config :D

---

### Post by ikt on 2008-02-26
> **tcpip4lyfe said:**
> All the memory would fail in different slot but not all the time.  And it would only fail in the 300MB and 2000MB addresses.

If you try different memory, does it still fail?

---

### Post by darksidedude on 2008-02-27
try running the ubuntu live CD and see if that crashes? it could be  memory leak in windows, or windows got sick and threw up on your ram:lolflag:
its amazing what a live cd an do, were you trying to use 64 bit windows?
because 32 bit may crash because of the extra ram, 

if using 32 bit
before it crashes, does Physical Address Extention show up under the amount of ram?

if using 64 bit, 
maybe its just windows so see idea #1 try the ubuntu live CD ?

---

### Post by K.Mandla on 2008-02-27
> **darksidedude said:**
> try running the ubuntu live CD and see if that crashes?
That's probably a good idea. That would at least give you an idea if it's something hardware or software-related. I don't know if I would trust Windows not to cause errors and make it look like memory was failing. Provided you can trigger the same errors in Linux, at least you could be sure it was indeed the hardware.

After that, the best suggestion is to start swapping parts. Process of elimination. Have fun with that. ... :p

---

