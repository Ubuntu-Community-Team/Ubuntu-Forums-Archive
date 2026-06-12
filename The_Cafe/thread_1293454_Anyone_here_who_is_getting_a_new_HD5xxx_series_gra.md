---
title: "Anyone here who is getting a new HD5xxx series graphics card?"
date: 2009-10-17
forum: The Cafe
---

### Post by OmegaAI on 2009-10-17
I will be upgraded to a UD3P (has Xfire support which my UD3R does not have) and 2 HD5770s (which will destroy my GTX260 and come close to a 5870).


Are any of you going to be upgrading at all?



Note: With these current graphics cards, AMD/ATI has nvidia by the throat and Big Green knows it, but sadly, they do not even have their Fermi chip out yet! Hell, the Fermi they did have was just a mockup!

---

### Post by nowin4me on 2009-10-17
Is it compatible with AGP?

:lolflag:

If it is I might buy one

---

### Post by BuffaloX on 2009-10-17
I recently bought the Radeon 4770, and I'm quite happy with it.
It has decent 3D and very low power consumption, and is very quiet.

You must have some pretty hefty gaming requirements if you need two 5770.

---

### Post by JDShu on 2009-10-17
I want to mention (again) the awesome progress made by the ati open source drivers :D

Check out the phoronix forums for the latest feedback.

---

### Post by Tipped OuT on 2009-10-17
I wish man, I wish. I would die for one of those. Oh my God, just die. *sigh* 

Anyways, back to my PSP.

---

### Post by Skripka on 2009-10-17
> **OmegaAI said:**
> I will be upgraded to a UD3P (has Xfire support which my UD3R does not have) and 2 HD5770s (which will destroy my GTX260 and come close to a 5870).


Are any of you going to be upgrading at all?



Note: With these current graphics cards, AMD/ATI has nvidia by the throat and Big Green knows it, but sadly, they do not even have their Fermi chip out yet! Hell, the Fermi they did have was just a mockup!

Only if ATi has FIRED their Parker Bros. driver writing team.  Great silicon is WORTHLESS with pathetic driver software.

My GTX260 actually works smoothly and without being noticed-which is more than I can say for any ATi card I have ever tried to run in Linux.

---

### Post by Dimitriid on 2009-10-17
Nvidia will hold their launch until later but is not like ATI can meet demand right now,which tells me they were a bit premature and manufacturing yields are not quite there yet.

Proper driver support is more imporant to me than getting 15% better framerates on games with the possible exception of crysis.

---

### Post by spoons on 2009-10-17
> **Skripka said:**
> Only if ATi has FIRED their Parker Bros. driver writing team.  Great silicon is WORTHLESS with pathetic driver software.

My GTX260 actually works smoothly and without being noticed-which is more than I can say for any ATi card I have ever tried to run in Linux.

As of Ubuntu 9.10 the drivers aren't bad. Not as good as the Nvidia ones, but they seem to be constantly improving. Radeon/RadeonHD is getting there now too.

---

### Post by edin9 on 2009-10-17
Until the drivers work, no.

---

### Post by OmegaAI on 2009-10-17
Guys, the drivers work just fine! ALL the drivers work just fine, well at least when I used them. They have come a long way since the 8.x series drivers. The 9.5 drivers worked really well with my 4770 and HD4850.

---

### Post by speedkreature on 2009-10-26
Have a 5770.  Upgraded from a GeForce 8400GS.  Works great with a single screen, but I'm having dual monitor problems (monitor 2 is a copy of monitor 1).
Haven't got a second 5770 to try see CrossFire support but it's mostly hardware so it should work just fine.

---

### Post by edin9 on 2009-10-26
> **speedkreature said:**
> Have a 5770.  Upgraded from a GeForce 8400GS.  Works great with a single screen, but I'm having dual monitor problems (monitor 2 is a copy of monitor 1).
Haven't got a second 5770 to try see CrossFire support but it's mostly hardware so it should work just fine.

Using Linux or Windows?

---

### Post by speedkreature on 2009-10-26
_Windows Vista Ultimate 64-bit:_ The Catalyst Control Center installed fine as did Hydravision, however the driver won't load.  When I right click on it in Device Manager it tells me this device failed to start.  So back to Ubuntu...
[U]
Ubuntu Karmic Desktop 64-bit:[/U] The Catalyst Control Center installed fine and the driver loads and everything works exactly as it should (i did get my dual monitor display working...error ID10T on my behalf--it was really easy).  HOWEVER, there is a very ugly "AMD Unsupported hardware" watermark on the bottom right corner of both monitors. 
A quick google search revealed it has something to do with the control file.  The device *is* supported, and it works perfectly.  I haven't yet made any attempt to fix this, but I gather it should be pretty easy to do.  I'll post it once I'm done.

---

### Post by markbuntu on 2009-10-26
I am not going to buy any new ATI card until I can watch HD with gpu hardware acceleration. The libs have been in the driver for over a year now......

---

### Post by markbuntu on 2009-10-26
The unsupported hardware watermark is to let you know that the driver may not work properly with that particular hardware since the driver was not specifically targeted for it and may not have been fully tested. Usually the next driver release will have fully tested support and the watermark will go away.

---

### Post by speedkreature on 2009-10-26
It is my understanding ATI's driver version 9.10 is supposed to have 5XXX series cards in it.  The issue most commonly appears on systems with AM3 CPU's.  It's looking like we may actually have to wait until the next release for this to be fixed.
The original instructions for fixing the watermark were:
1) run the ATI driver installer with the --extract switch  (i.e. ati-driver-installer-9-10-x86.x86_64.run --extract)
2) cd into the directory created (fglrx-install.######) and copy ./common/etc/ati/control to /etc/ati/

That, however, doesn't work currently as the issue that was intended to fix has already been resolved; "control" is copied correctly during install.  There isn't any mention of this problem in the ATI forums that I can find so far, though there are a few threads for the 4XXX series scattered throughout the Ubuntu forum.  As a whole, Linux users on the ATI forum are hopping mad about a number of other issues though.

From what I understand though, it's fairly common for users of Windows Vista and 7 to have the issue I described earlier where the device fails to start, so we're not alone.

Looks like AMD/ATI put the cart before the horse.  With any luck, they'll resolve this shortly.  In the mean time, between performance and stability issues on the 5850 and 5870, and driver problems on the 5770, if you don't already have a 5XXX series card, I'd hold out.

---

### Post by BaffledMollusc on 2009-11-03
I've got a Radeon 5770, and initially also had the "unsupported hardware" watermark when I used the proprietary fglrx driver that comes with Ubuntu 9.10.

I think the issue was that the pre-release fglrx driver AMD delivered to Canonical had a cut off period just before the driver was qualified for the 5770 and 5750 cards, but after the 5870 and 5850 were qualified, which is why the latter don't have the watermark. The 5700 series seem to work fine with Catalyst 9.10, though, it's just that they aren't "official".

Anyway, simple instructions on how to remove the watermark can be found in this thread: [http://www.phoronix.com/forums/showthread.php?t=19875](http://www.phoronix.com/forums/showthread.php?t=19875)

The fix hacks the binary .so file to remove function calls that display the watermark. It's pretty ingenious and worked for me.

Edit: Realised that what I call "simple instructions" may seem a bit impenetrable to some people! So here are more step-by-step instructions:

Right click on the desktop and choose Create Document -> Empty File
Call it something like "remove_watermark.sh"
Double click on the file you've created to open it in the text editor
Paste the following text into the text editor

#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

Save the file and close the text editor
Right click on the desktop icon you've created and choose "Properties->Permissions"
Tick the box "allow executing file as program"
Close the properties dialog
Open a terminal (Applications -> Accessories -> Terminal)
Type the following two lines into the terminal, pressing enter after each line

cd Desktop
sudo sh remove_watermark.sh

Now enter your login password when prompted

Finally log out and back in and the watermark will hopefully be gone!

---

### Post by stathiz on 2009-11-09
I have a HD5750 and ubuntu 9.10 and was having the unsupported hardware watermark problem. 
Issue resolved using the instruction from the phoronix forums, 
thanks BaffledMollusc for the instructions.

The card otherwise seems to be working fine with compiz enabled although some things are not very smooth.The only game I 've tried on ubuntu is nexuiz and it runs fine at 2048x1152 resolution.

As far as the card is concerned I am very happy with it, excellent value for money.

---

### Post by 3rdalbum on 2009-11-09
ATI doesn't support video decode and display acceleration; by contrast, Nvidia's VDPAU is very stable and mature, and the only way I can watch Blu-ray footage smoothly enough on Linux.

I can also watch said video while running Compiz, which is more than I can say for ANY video on ATI.

Why put yourself through the hassle of buying the world's fastest video card, when you're going to get worse performance than a GTX260 on Linux?

---

### Post by userfriendly on 2009-12-17
I'm considering to buy a HD 5750, specifically for running 3 monitors at home (at work I have 3 monitors hooked up to 2 cards, which was a pain in the **** to set up and it still doesn't work quite right: [http://ubuntuforums.org/showthread.php?p=8349285](http://ubuntuforums.org/showthread.php?p=8349285) ...well, it works, sort of, but I'd really like to avoid such hassle next time).

My question is, do I have to wait for AMD to release the Catalyst driver with Eyefinitiy support for Linux? I don't plan on using the Single Large Surface thingy anyway, I'd like my windows to maximise to only the screen they're on. A simple extended desktop setup across 3 monitors is what I want - is that possible with this card on Linux already?

---

### Post by NoaHall on 2009-12-17
Well, I've got three great,highest-end nvidia cards, but I'm looking into the 5970 as a option. GDDR5 and 3200 processors - sounds awesome to me.

---

### Post by LinuxFanBoi on 2009-12-17
> **OmegaAI said:**
> Are any of you going to be upgrading at all?

not until ATI proves to me that they give more than half a fart about their Linux customers. clearly they don't because they are leaving it up to us to make working drivers, rather than investing in the development of proprietary drivers that can take advantage of all their hardware's features. They would also have to prove to me that support for those drivers will last longer than 18 months like the last ATI card I owned. Until then I have to give a big **[bleeped]** to ATI.

---

### Post by PurposeOfReason on 2009-12-17
I have an ATI 5850, love it to death. Drivers work great, I don't use compiz though I do pass all the checks if I wanted to. Waiting on my third monitor for eyefinity with Windows. For all you who say the drivers are so terrible, I've yet to see a nvidia app that you can visually drag you monitors around and rotate them so what you see on the picture for how your monitors will be arranged is how they are after an X restart. That just blew my mind away to be able to do in linux.

---

### Post by LinuxFanBoi on 2009-12-17
> **PurposeOfReason said:**
> I have an ATI 5850, love it to death. Drivers work great, I don't use compiz though I do pass all the checks if I wanted to. Waiting on my third monitor for eyefinity with Windows. For all you who say the drivers are so terrible, I've yet to see a nvidia app that you can visually drag you monitors around and rotate them so what you see on the picture for how your monitors will be arranged is how they are after an X restart. That just blew my mind away to be able to do in linux.

It's not that I think their drivers are bad it's that my past experience ATI bailed on driver support for my X1950 GT just as the X.org that came with 9.04 broke it.  It was plainly obvious that ATI just threw  their hands up and said "you're on your own, we don't care enough about you to fix the driver for your card."

This left a very bitter taste in my mouth, and what was worse when I sent their developers an e-mail expressing my issues, their response was, "If you would like active support for an ATI Card,  we recommend that you purchase one from our HD line of adapters."  This actually made me angry enough to go out and buy a GTS 250 from XFX take a digital picture of myself holding the new card up whilst giving ATI the bird and e-mailing it back to them with a caption that read,  "I will spend my money on a quality product! since you no longer offer one, I'm buying from your competitor."

It's really hard for me to put into words how angry I was, and still am at ATI for the whole fiasco!

---

### Post by Gizenshya on 2009-12-17
I'm not going to be upgrading for a while.

My system (in my sig) is matched up very well atm.  If I had any more GPU, my processor couldn't keep up, and vice versa.  I'll have to do a complete new system when I upgrade.

But this system handles everything I throw at it very well.  I run all the latest games on high at 1280x1024 without any problems (except with Crysis I disable AA).

Windows will have to step up to the plate also.  I am not going to get another one until they either stop their stupid rule about not letting XP do DX10+, OR until they actually get decent drivers/support in Vista or 7 that won't crash every 3-5 mins on basically all games.  XP does great on every game I have (which is a lot), and rarely crashes.  When it does crash it is usually from OCing too much or forgetting to change fan speeds, but those are easily fixed.

---

### Post by PurposeOfReason on 2009-12-17
> **Gizenshya said:**
> I'm not going to be upgrading for a while.

My system (in my sig) is matched up very well atm.  If I had any more GPU, my processor couldn't keep up, and vice versa.  I'll have to do a complete new system when I upgrade.

But this system handles everything I throw at it very well.  I run all the latest games on high at 1280x1024 without any problems (except with Crysis I disable AA).

Windows will have to step up to the plate also.  I am not going to get another one until they either stop their stupid rule about not letting XP do DX10+, OR until they actually get decent drivers/support in Vista or 7 that won't crash every 3-5 mins on basically all games.  XP does great on every game I have (which is a lot), and rarely crashes.  When it does crash it is usually from OCing too much or forgetting to change fan speeds, but those are easily fixed.
That isn't a "stupid rule", it's limitations that would require a huge workaround to get it working. I don't care who you are, XP came out in 2001. It is old and thus should be getting dropped like it is. I've had (though I understand it is easily possible) no issues with 7.

However, at that resolution you'll find you won't need to upgrade for at least another year.

---

### Post by MooPi on 2009-12-17
I've been dreaming of the new ATI gpu's but not for my Linux rigs. Only Nvidia for my Linux boxes due wasted time and money with ATI and trying to get them to work properly. But the ATI cards rock my windows gaming rig. I've got two ATI 3870 in crossfire and they never miss a beat. Used to be an Nvidia  man through and through until I noticed my nephews gaming set-up. It ran cooler and had a better fps  per game. Nvidia's product just seems to mesh better with Linux.

---

