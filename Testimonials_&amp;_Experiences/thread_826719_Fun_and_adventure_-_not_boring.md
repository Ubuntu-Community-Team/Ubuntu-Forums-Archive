---
title: "Fun and adventure - not boring"
date: 2008-06-12
forum: Testimonials &amp; Experiences
---

### Post by Hanluk on 2008-06-12
I read about Ubuntu in a computer magazine. Over time I thought it might be fun to try another Operating System. I did not want to try VM ware - Dual booting etc. I wanted a seperate box so that I could experiment and play around. The opportunity arose when my eldest son moved out and left all sorts of computer bits about including what was left of his very first PC a Pentium 3 866 Mhz. It still had a mainboard, nvidia geforce 256 graphics card, net-work card, and Creative labs ct4810 sound card. So! Off I go and get a new Optical Drive (Asus 20speed IDE), Hard Drive (Western Digital 160G), and Power Supply (Generic 450 watt). Oh! it also had 384M of SDRAM.

	All the bits went together and then I obtained an .iso of Unbuntu 8.04. Burned to CD and turned on box. Insert CD and voila, it begins to load and then error fd0 and sr0. -expletive- Call my son (my tech support) - What does this mean? Either hard disk is stuffed or optical drive is stuffed. They are both new. Well then, remember google is your friend. So on to the net. Yep fd0 and sr0 are device issues from what I gather. Any way, keep on reading. Minimum system requirements for Ubuntu - maybe I need more RAM. Computer Magazine has a cut down version of XUbuntu on its cover CD. So I knock out a copy of that. Insert and boot up. Well there you go looks great - a bit sparse and awkward to handle - but - it works. Feeling pleased about myself at this point. Um. Forgot to get speakers for it. Plug headphones in - no sound - Hmmmm.

	Google is my friend. Around this point I discover Ubuntu Forums, the ALSA Project, Launchpad, linux forums, and lots of others. I absolutely cracked up over a site called howtogeek. (bookmarked it straight away). Although I could not make much sense of it. I spent hours reading and learning. Still unable to get sound working. Struggling with the concept of root/sudo, terminals and such. I start to notice that this version I have is very restricted as they have cut out everything that might not be needed. So of to the shop and buy some more ram.

	Stick it in. I am comfortably inside the minimum system requirements for Ubuntu now. So, how do I wipe the drive. Oh ! Google is my friend. google format drive. I come across a thread where people are discussing just that. All sorts of ideas. 4 or 5 posts down a genius suggests that the manufacturers of hard drives would provide Diagnostic tools which would enable you to wipe your drive. Ta-dah! I am beginning to be amazed at the resources available. Not only in the Documentation, but in the forums (community).

	So. Stupid me, gets the Diagnostic tools and decides to do a full wipe. 2 hours later......OK, ready to load new OS -- haha - talking in letters now -. In goes the LiveCD ....fd0 sr0 errors again. -expletive- . Try the cut down one again, it boots ok. Whats the difference? The cut down version is based on 7.10 Xubuntu. So I download and create a Ubuntu 7.10 LiveCd. It works. I am leaping around the room. Install. yes . Does it run? yes. will it reboot yes. and features ease of use and available programs, fabulous. What is that? still no sound. Grrrr....

	Well lets get all the updates. 219 updates. Bandwidth is copping a hiding but its OK. Hmm I wonder if I can upgrade to 8.04 with no ill effects. I then went for the upgrade to 8.04. Long story - short, it upgraded fine, rebooted and I was ecstatic. Rebooted a second time. Login screen is grossly inflated - a little over twice my actual screen. Keep in mind here I know nothing about anything. I remembered my old friend Mr Google. So google ubuntu login screen. Lots of stuff but nothing quite like my problem. Until I come across an item by this fellow who had exactly my issue. His article said it had something to do with the xorg.config file - the Virtual screen setting. So fools bravely go ... I did what he said and went into Terminal and looked at the xorg.config file. I found the setting and changed it to my screen resolution. Reboot and .. Hey its still not right. Well I went in again trying to think what setting I should change it to. I then decide to read all the comments at the top.

	It tells me there that this not not a real xorg.config file and I should enter sudo dpkg rubbish stuff and nonsense. Which I duly do. Fools etc. That fixes it. I still don't know what I did but I am getting closer to actually using this system and I can find out all about it. My bookmark folder in Firefox has sub folders galore filled with links for further investigation. I'm new at this and I'm having a lot of fun. Anyway looked around added a few programs, I want to learn C++ , ooh Perl,Python,Ruby. There is a whole world out there. Bookmarks all over the place. Sound still don't work. Can't make sense of it, but give me time.

	Oh! Someone wants his monitor back. Dig an old monitor out of the cupboard. Connect it up. Boot it up. What now! Keyboard does not work. Reboot. Reseat the keyboard plug. Grub error 17. What the hell is that. Look it up with my mate google. Grub does not recognise partition format. OK so rebooting from the login screen has corrupted something. How do we fix. Suggestions revolve around making sure BIOS settings are OK, and getting a liveCD to boot. So muck around in BIOS, for a bit. Achieved nothing. Tried to boot from Ubuntu 8.04 LiveCD errors fd0 sr0 again. Got an Alternate install CD tried that. Used rescue option. Somewhere in there it does not recognise my optical drive. That explains the fd0 and sr0 errors. 

	Tried the 7.10 LiveCD. Success, it booted up. Tried the suggestions about fdisk -l. That worked. Cannot find /boot/grub/menu.list. Odd. Now how can I look at the disk. Tried the partion editor. It did its survey and showed me three partions the big one hda1 - unknown the two small ones - linux and swap.
 
	So here's the thing. If I get gparted to reformat the partion to ext3, I imagine I will lose my installation. So everything I have done so far is lost. Do I just do a fresh install. OH d*** now Ubuntu 7.10 won't boot. Lets try the original cutdown Xubuntu CD. OK, It has booted just fine. tested previous fdisk - decide to copy and paste to a USB stick. Computer freezes.

	Here I am.

	So. Now I have had a huge amount of fun getting to where I am now. However, I have to admit I am back to where I started. I still don't have an operating Linux system. Digging through some of the other rubbish my son has left behind are some newer motherboards SATA . This one was IDE. I know what these mean because Wikipedia has also become my friend. I don't have much in the way of spare cash to buy whats needed, but it looks like I will have to abandon the hardware I have, and just wait until I can afford to build another box.

	Did I say I had fun. If everything had gone as smoothly as some posts I have read I would not Know half as much as I do now.

---

### Post by armandh on 2008-06-12
I would not know where to start
every P-III that I have done has been wham bam good to go.
as I recall.....
from the live disk...
I installed and selected "use whole disk"
or for a dual boot I first vacated part of the drive with a partition utility and 
from the live disk install selected "use largest unpartitioned space"

it just worked, but if it does not work for you.... 

I suspect there may be some reason the P-III  carcass was left behind

or

as noted below both bad down loads and bad cd burn are problematic.
use quality CDs and a good drive or slow speed for the burning.

---

### Post by stalkingwolf on 2008-06-12
I have gotten the fd0 error several times.  But only on laptops
where I use the same slot for floppy and cd drives.  When I have
both connected I dont get it.

I have several P3's running 7.04 and 7.10 quite well. One is a
700mz with 256mb ram.

Did you burn your CD at the lowest speed? I use 4x.

---

### Post by hyper_ch on 2008-06-12
I like the "google is my friend" part of the story :)

But the error seems strange... how about trying the xubuntu hardy heron alternate cd for installation? That might be better?

When does that sd0 error actually appear? before it start booting from the cd? Maybe you need to explicitly set the harddisk to master and cd drive to slave or connect them to different IDE cables....

---

### Post by Hanluk on 2008-08-31
Well I am back. I have picked up a new??er box and have loaded Ubuntu - and am loving it. No problems - I even have sound.

I am glad I decided to make this post as I can look back at it and see what I had been investigating whilst I was having problems with the other box. Because when your system works fine, you have no reason to discover stuff.

I thought I might wrap up my deductions about the problems I was having.

The fd0 and sr0 error.
    I think this was largely the fault of the BIOS - It was so old that it did not recognise the specific make of the optical drive. So it was treating it purely as an ATAPI drive. Part of the way through the install process there must be a moment when the operating system kicks in and then starts to extract more information from the CD. This was the point at which I was getting the failure. I discovered this when I tried to use the alternate CD. It got to a point at which it no longer recognises that the drive exists at all. It does however know that it is looking for data and then freaks... resulting in the above errors.

As for the rest of it - just crappy hardware that was on its last legs anyway. 

Now that I getting more confident in using this - eg. playing with partitions, learning to use Terminal etc. I have decided to build myself a really nice box. So that I can use all the features that my current video card does not support. 

Um... if anyone has any recommendations about high-end video cards that work very well with Linux. I would like to hear about them, so that I can make an informed decision about components for this new box.

This system is becoming my default system.

---

### Post by wolfen69 on 2008-09-01
great to hear. although most people would have given up after what you went through. but at least you were smart enough to try it on some better equipment and see how good linux really is. when i tell people that they have equipment that is in the minority and probably wont work with linux, they dont want to hear it and move on, saying "ubuntu sucks". glad to hear you stuck it out. time to reap the rewards! welcome aboard.

---

### Post by Martje_001 on 2008-09-01
I should wait a few months, the ATI/AMD drivers will be very good by then (better than the Nvidia one's)! But if you have to buy a card right now, I would say Nvidia.

---

