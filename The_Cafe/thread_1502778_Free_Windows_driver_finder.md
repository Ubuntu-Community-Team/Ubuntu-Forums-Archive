---
title: "Free Windows driver finder?"
date: 2010-06-06
forum: The Cafe
---

### Post by Nick_Jinn on 2010-06-06
I am installing a dual OS system on a computer and I am looking for a driver finding and installing program that is free for windows. Any suggestions? Cheap is good to. I would pay $10, but I dont want to pay $30. Most of the cracked ones are fake or dont work.


Also, the "language" disk in windows is computer languages, right? Not like french and spanish?

I dont have sound on one of my laptops in either OS.

---

### Post by Frak on 2010-06-06
Windows update.

---

### Post by dtfinch on 2010-06-06
After verifying that you didn't get malware from one of the fake/cracked update programs, I'd check the manufacturers' websites for drivers.

---

### Post by juancarlospaco on 2010-06-06
*Get Ubuntu.*

---

### Post by Frak on 2010-06-06
> **juancarlospaco said:**
> *Get Ubuntu.*
IIRC, Ubuntu doesn't come with a Windows driver finder.

---

### Post by cariboo on 2010-06-06
If you go to the computer manufacturer's web site, you can get the drivers for free. For laptops check for a model number on the bottom, for an OEM system check the back or side for a model number. For a white box/screwdriver guy system pull off the left side panel and look for a model number on the motherboard.

---

### Post by paydaydaddy on 2010-06-06
I can't recommend a "free" drivers finder, but I will tell you of my recent experience. I decided to put 64bit win7 on a computer that was several years old. I spent about 3 days trying to find all the drivers I needed by going to manufacturer's website, doing google searches, and perusing various forums. I also read a number of reviews of driver searching software. Based on the reviews and in consideration of the value of my time I finally shelled out $30.00 US for DriverDetective in hopes of finding the final few drivers to enable all of the features of the motherboard and, in effect, the computer. I found DriverDetective to be easy to use and within an hour of installation I had found and installed all the drivers I needed plus a couple of upgrades to some previously installed drivers. All I am saying is if you have the time, patience, and persistence you can save yourself a few $s. On the other hand, if you're willing to spend a few $s you can save yourself some time and headaches. Good Luck!

---

### Post by 3rdalbum on 2010-06-06
> **Nick_Jinn said:**
> I am installing a dual OS system on a computer and I am looking for a driver finding and installing program that is free for windows. Any suggestions? Cheap is good to. I would pay $10, but I dont want to pay $30. Most of the cracked ones are fake or dont work.

Most of the ones you pay money for are fake and don't work, and give you viruses.

It only takes an hour to find drivers for Windows. Yeah I know you don't need to spend that hour on Ubuntu :-)  But there's not a lot of things that actually require drivers; just your sound, graphics, network card, wifi, and mobile broadband (if you have it).

---

### Post by Frak on 2010-06-06
Again, Windows Update has a good track record of auto-installing drivers for common hardware.

---

### Post by TwoEars on 2010-06-06
> **Nick_Jinn said:**
> I am installing a dual OS system on a computer and I am looking for a driver finding and installing program that is free for windows. Any suggestions? Cheap is good to. I would pay $10, but I dont want to pay $30. Most of the cracked ones are fake or dont work.


Also, the "language" disk in windows is computer languages, right? Not like french and spanish?

I dont have sound on one of my laptops in either OS.
It should be fine by default, you shouldn't need to look far, especially not with a laptop, Windows Update should be fine. As long as you're going with Vista/7

What language disk? And no, from the sounds of it, it is human languages, not computer languages. Why on earth would they give you a disk of computer languages? That's sort of... impossible. It'd be a disk of compilers. And if so, then it's a Visual Studio disk. If it's not a visual studio disk, it's 100% human languages for sure.


Sound doesn't work in either? Then it's probably a hardware problem, not a software problem. It might be something as simple as using the little volume-rolly thing and rolling it so you can hear it.

---

### Post by Nick_Jinn on 2010-06-06
> **paydaydaddy said:**
> I can't recommend a "free" drivers finder, but I will tell you of my recent experience. I decided to put 64bit win7 on a computer that was several years old. I spent about 3 days trying to find all the drivers I needed by going to manufacturer's website, doing google searches, and perusing various forums. I also read a number of reviews of driver searching software. Based on the reviews and in consideration of the value of my time I finally shelled out $30.00 US for DriverDetective in hopes of finding the final few drivers to enable all of the features of the motherboard and, in effect, the computer. I found DriverDetective to be easy to use and within an hour of installation I had found and installed all the drivers I needed plus a couple of upgrades to some previously installed drivers. All I am saying is if you have the time, patience, and persistence you can save yourself a few $s. On the other hand, if you're willing to spend a few $s you can save yourself some time and headaches. Good Luck!



Would you be willing to share with me if I pitch in $5? I just need a validation.

And dont worry. I am not going to be putting it up on torrent. I dont want it to be taken down because I would like to use it myself for the rest of the year. I would really appreciate it. There is no way I can afford to dump $30 on this right now with all the added expenses this month.

I already have Ubuntu. For those of you who can read you know that I was building a dual OS desktop for family members.

Windows updates is not sufficient. Neither is the manufacturers website when you are dealing with a custom build.

---

### Post by Nick_Jinn on 2010-06-06
> **TwoEars said:**
> It should be fine by default, you shouldn't need to look far, especially not with a laptop, Windows Update should be fine. As long as you're going with Vista/7

What language disk? And no, from the sounds of it, it is human languages, not computer languages. Why on earth would they give you a disk of computer languages? That's sort of... impossible. It'd be a disk of compilers. And if so, then it's a Visual Studio disk. If it's not a visual studio disk, it's 100% human languages for sure.


Sound doesn't work in either? Then it's probably a hardware problem, not a software problem. It might be something as simple as using the little volume-rolly thing and rolling it so you can hear it.



I should have made myself more clear. I need the drivers for a custom DESKTOP, unrelated to the laptop. This is a custom buil which means there is no manufacturers page for it and windows updates wont find it. 

And its not a hardware issue. I plugged in bluetooth and it still didnt get sound in the ear pieces. The speakers are fine.

The volume controls are on full blast. There is no sound on either OS. 



But I would be willing to give a donation for a working validation code....I would especially like to donate up to $10 to a site that sells free or affordable driver updaters, but I cant afford $30 for a single program. Thats ridiculous. $10 is the limit for an accessory like that.

---

### Post by gradinaruvasile on 2010-06-06
I never seen a driver finder that actually worked - besides many are just BS, spyware etc.
Use lspci.
I install/maintain Windows boxes and laptops for a living.
Firs i boot the computer from Ubuntu, open a terminal, do a "lspci" > /path/lspci.txt command, copy the file somewhere.
Then i check the manufacturers site of course for drivers.
If there are problems with the drivers (they do sometimes) or the computer has some unrecognized/not working devices in Windows, i check the lspci.txt i saved and try to find the drivers on the original (part manufacturer) site.
For example a Toshiba laptop touchpad drivers wouldnt work (no perceivable change after install and no option for customize settings) so i downloaded the driver directly from synaptics because i knew that was a Synaptics touchpad from lspci.
Same goes for its wifi that wouldnt work with its original drivers, so i downloaded the Intel 3945 Windows drivers from Intels site that worked.
lspci is a godsend. I just dont know why Windows doesnt have a built in similar feature, it would help tech guys a lot - you are essentially blindfolded in Windows, you only see some "SMBUS device" or the like in the Hardware tab with a big yellow question mark on it. And the Windows XP automatic driver thing is a joke - only once found and installed a driver that didnt work lol. Windows Vista/7 seem to find and update drivers, but still do not show the hardware name before the driver is installed for it.

---

### Post by Nick_Jinn on 2010-06-06
Thnaks for the tip.


However, my experience with the driver apps has been different from yours. Some of them work awesome.

My time is worth something. Searching for drivers is about the least enjoyable type of tinkering I can think of. I would rather be customizing the look and theme and installing apps than spending all afternoon looking for drivers.



If you do it for a living, you would save hours of your time if you had something like driver detective or driver genius....I just dont want to spend 30 bucks for something I might use twice. 


If they had a 99 cent 1 time cloud/remote service, I bet they would make as much money. 99 cents per run, or maybe $1.99 per run is something people will pay. If they use it 5 times thats $10...from a lot of people who never would have paid $30. 


But if anyone wants to help me out that would be great.

---

