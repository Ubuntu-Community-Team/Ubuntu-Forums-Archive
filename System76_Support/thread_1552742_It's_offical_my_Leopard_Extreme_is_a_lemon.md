---
title: "It's offical my Leopard Extreme is a lemon"
date: 2010-08-14
forum: System76 Support
---

### Post by bk7777` on 2010-08-14
[FONT=Times New Roman][SIZE=3]I have been posting in other threads so I will summarize here and provide additional information.[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I have had my Leopard a little over a month. I was not able to really start working with it till about 2 weeks ago.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]In the 2 weeks the system had locked up more times than I can remember. However it was never consistent. It would run for a few days then it would lockup like every 15 min until I reloaded the OS from scratch. Which has been done four times now.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I originally thought that it was a bad hard drive as it was not in the cage with I received it meaning it was banging around inside the case while it was in shipping. I finally put in a 320GB drive which I had in another working computer and it seemed to be fine for a few days till I loaded the NVIDIA driver.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Ian of S76 let me know that there was a known bug and patch for the NVIDIA issue and headed down that path for over a week trying to get the system to stabilize. It never would.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I talked to Tom of S76 a few times on the phone explaining what trouble shooting I was doing and we finally agreed that we would start from scratch and go thru a detailed testing procedure.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]The procedure was to reload the OS from scratch again and slowly activate items on the system to see if we could come up with what was locking up the system.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]The system was reloaded with no NVIDIA driver and set up exactly like it was. The only packages that were loaded above the base install are MIRO and VLC. The system ran for about 2 hours before it locked up.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I talked to a tech friend that was knows Ubuntu better than I and was discussing where to find standalone diag software to stress the system. He informed me that GRUB had one built in called “MEMTEST86”. I tried the one in GRUB and it would not run. Some error about unable to allocate low memory. Then he suggested that I run MEMTEST86 from the Ubuntu live install CD. Which I did and it ran. It did not take 10 seconds before it found 20 RAM errors. I let MEMTEST86 continue to run and complete a first pass about 30 min of time. In the first pass it found over 1,400 RAM errors. It continued to run another 2 or 3 minutes into the second pass before MEMTEST86 locked up. [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I powered off the system and rebooted again and ran a single pass a second time. Again over 1,400 RAM errors. Then I shut it down.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]So now the question is what is the real problem other than hardware. What specific piece or pieces are really bad? Is it the DIMMs, memory slots, mother board or is the CPU having issues?[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I am done trouble shooting. It is up to System76 to make this right. I figure they have two options:[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]1) Ship a complete new system and will call the other system for pickup or 2) give me a complete 100% refund and will call the system for pickup.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I will keep you posted as to which action they take.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Thanks,[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Brian[/FONT][/SIZE]

---

### Post by msrinath80 on 2010-08-14
Thanks Brian :) One thing I don't get however is why there are a good number of posts where such problems are easily attributable to bad shipping choices. Clearly, the company used for shipping is causing more problems for S76 than helping. Why exactly are they continuing to use this courier company (is it UPS?) despite such complaints?

---

### Post by betrunkenaffe on 2010-08-14
> **bk7777` said:**
> [FONT=Times New Roman][SIZE=3]I have been posting in other threads so I will summarize here and provide additional information.[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]I have had my Leopard a little over a month. I was not able to really start working with it till about 2 weeks ago.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]In the 2 weeks the system had locked up more times than I can remember. However it was never consistent. It would run for a few days then it would lockup like every 15 min until I reloaded the OS from scratch. Which has been done four times now.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I originally thought that it was a bad hard drive as it was not in the cage with I received it meaning it was banging around inside the case while it was in shipping. I finally put in a 320GB drive which I had in another working computer and it seemed to be fine for a few days till I loaded the NVIDIA driver.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Ian of S76 let me know that there was a known bug and patch for the NVIDIA issue and headed down that path for over a week trying to get the system to stabilize. It never would.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I talked to Tom of S76 a few times on the phone explaining what trouble shooting I was doing and we finally agreed that we would start from scratch and go thru a detailed testing procedure.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]The procedure was to reload the OS from scratch again and slowly activate items on the system to see if we could come up with what was locking up the system.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]The system was reloaded with no NVIDIA driver and set up exactly like it was. The only packages that were loaded above the base install are MIRO and VLC. The system ran for about 2 hours before it locked up.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I talked to a tech friend that was knows Ubuntu better than I and was discussing where to find standalone diag software to stress the system. He informed me that GRUB had one built in called “MEMTEST86”. I tried the one in GRUB and it would not run. Some error about unable to allocate low memory. Then he suggested that I run MEMTEST86 from the Ubuntu live install CD. Which I did and it ran. It did not take 10 seconds before it found 20 RAM errors. I let MEMTEST86 continue to run and complete a first pass about 30 min of time. In the first pass it found over 1,400 RAM errors. It continued to run another 2 or 3 minutes into the second pass before MEMTEST86 locked up. [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I powered off the system and rebooted again and ran a single pass a second time. Again over 1,400 RAM errors. Then I shut it down.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]So now the question is what is the real problem other than hardware. What specific piece or pieces are really bad? Is it the DIMMs, memory slots, mother board or is the CPU having issues?[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I am done trouble shooting. It is up to System76 to make this right. I figure they have two options:[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]1) Ship a complete new system and will call the other system for pickup or 2) give me a complete 100% refund and will call the system for pickup.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]I will keep you posted as to which action they take.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Thanks,[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Brian[/FONT][/SIZE]

That would likely be a bad stick, contact them, they'll probably get you to ship it back and replace the RAM and then test again to confirm that the errors are gone before sending it back.

Bad RAM gives pretty much every random error under the sun.

---

### Post by gamerchick02 on 2010-08-14
Since it's within the warranty period, System76 should be able to ship you a new system or fix your current one.  I had absolutely NO problems with them when I had an issue with my Pangolian system.

It did take a little bit of time though.

Good luck.

Amy

---

### Post by bk7777` on 2010-08-14
Thank you all for replying,  I do not think it is a shipping issue in my case.  The Hard drive cages are held by soft plastic tabs.  The tabs are fine for a system sitting still but any reasonalbe motion shift could pop the drive free.  I realize they are trying to get away from screws for easy repair but Hard Drives are to important not to be held in place with steel pins of screws. 
 
The shipping box was in good shape when I received it.  No damage to the box.  It was just the bumps, turns and handling that popped it loose.  Not a good thing but feel it is a failure of the case manufacture.
 
I totally agree that RAM can cause random lockups.  It would just be nice to get some kind of bios error message.  What ever happed to the bios doing memory checking at boot time before it passes control to the OS?
 
All my P4 computers still do that check.  I did look to see in the bios if it could be turned on but did not find anything.
 
Amy,  I trust that S76 will do the right thing.  I just can not believe that they did not want me to do a system integrity check out of the gate instead of wasting all this time and energy.
 
Thanks,
Brian
 
](*,)

---

### Post by gamerchick02 on 2010-08-14
I understand the frustration.

Hope you can get everything fixed in a timely manner.

Amy

---

### Post by robtg on 2010-08-14
> **msrinath80 said:**
> Thanks Brian :) One thing I don't get however is why there are a good number of posts where such problems are easily attributable to bad shipping choices. Clearly, the company used for shipping is causing more problems for S76 than helping. Why exactly are they continuing to use this courier company (is it UPS?) despite such complaints?

It's funny you should mention that.  The day my Panp5 arrived, I saw the UPS driver actually drop the shipping carton on the floor of the truck.  The laptop was packed well so it didn't cause any problems.  I don't know if it's a UPS thing or not but I wish I hadn't seen that.

Rob

---

### Post by jbelmonte on 2010-08-15
Hi Brian,

I can see that you are frustrated. It is never fun when a new computer misbehaves. System76 will make this right I am sure.

In the meantime, have you tried re-seating the memory? If the memory sticks were bumped by the loose hard drive they could have come loose (or gotten damaged). It would be useful to know if re-seating them will address the memory issues.

Good luck.
John

---

### Post by bk7777` on 2010-08-15
Yes I thought the same thing.  I did pull and reseat the DIMMs.  Made no difference.
 
I did that between the two MEMTEST86 runs stated above.  
 
Not sure this is revelent but one thing I did notice was MEMTEST86 stated that bank 0 had one slot filled and bank 1 had both filled.  Since this is triple channel memory not sure if that means anything.
 
Bank 0
Slot 0   2GB
Slot 1   empty
 
Bank 1
Slot 0   2GB
Slot 1   2GB
 
The short of it is looking physically the slot closes to the processor is empty.
 
Thanks for the thought,
Brian
 
](*,)

---

### Post by betrunkenaffe on 2010-08-16
> **bk7777` said:**
> 
I totally agree that RAM can cause random lockups.  It would just be nice to get some kind of bios error message.  What ever happed to the bios doing memory checking at boot time before it passes control to the OS?

Disabled to speed up boot times, would take minutes to check RAM with current sizes.

---

### Post by bk7777` on 2010-08-17
While I agree it would slow down posting before it was handed off to the OS.  It should still be an options to enable or disable.  If it is enabled and you are in a hurry there is / was always the ESC key to cancel the test and move on.
 
Thanks,
Brian

---

### Post by bk7777` on 2010-08-17
I talked with TOM at S76 today and he research on how I should test the system and get back to him.
 
The short answer it 1 of the 3 DIMMs is bad.  Makes no difference which slot the bad DIMM is in.  It fails.  
 
The system is currently running on the 2 good DIMMs waiting on a replacment.
 
Here is what I sent Tom via e-mail.
 
 
[SIZE=2][FONT=Courier New]Tom,[/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]Per our conversation I did the testing as requested and it is a single bad memory DIMM.  The testing required that I have 2 DIMMs in at a time.  I labeled the DIMMs 1, 2 & 3.  No matter what slot DIMM #1 was in memtest86 thru all kinds of errors.  When DIMMs 2 & 3 were alone and no matter which memory slots were filled it passed everytime.[/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]Based on the testing I will assume that you need to get shipped ASAP a 2GB DIMM.[/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]I also loaded the OS again from scratch to insure everything was fresh and new and no problems so far.  [/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]I have not loaded the NVIDIA drivers yet.  Should I proceed to do so?  If yes with or without the x-server reset patch?[/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]I look forward to hearing from you.[/FONT][/SIZE]
[FONT=Courier New][SIZE=2] [/SIZE][/FONT]
[SIZE=2][FONT=Courier New]Thanks,[/FONT][/SIZE]
[FONT=Courier New][SIZE=2]Brian[/SIZE][/FONT]

---

### Post by betrunkenaffe on 2010-08-17
Can't see any reason you couldn't use the comp as  you would normally (just short 2GB RAM). Install the nvidia drivers as you normally would.

---

### Post by bk7777` on 2010-08-18
That is what I am doing running the system on 4Gb vs. 6GB.  The system ran solid for 24 hours.
 
I just installed the nvidia driver and will see what it does.
 
Thanks.
Brian

---

