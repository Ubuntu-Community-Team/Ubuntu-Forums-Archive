---
title: "meerkat live usb = no boot"
date: 2011-08-09
forum: System76 Support
---

### Post by Docaltmed on 2011-08-09
I've been trying for two days to get my meerkat to boot from a Live USB.

By hitting F2 on start, I have gone into the BIOS and enabled the USB boot option.

I have tried the following images:

Kubuntu 11.04 downloaded by torrent and USB created by Kubuntu's live usb creator.

Kubuntu 11.04 downloaded from server and USB created by Kubuntu's live usb creator.

Kubuntu 10.04 downloaded and live usb created by unetbootin.

I figure one of these ought to work. It is not that the USB is not being recognized. The USB is recognized, and then I get the following message: boot error.

If I press any key, it will then proceed to boot off of the hard disk to my previously-installed Ubuntu 9.10.

What is wrong?

---

### Post by Docaltmed on 2011-08-09
Ok, I've now verified that the problem lies with the Meerkat, as I have used multiple USB sticks and multiple ISOs, and created Live USBs that are capable of booting multiple other computers.

I have also tried multiple USB ports in the Meerkat itself, all with the same result:

**Boot Error**

Kinda running out of ideas, here. If I can't update the computer via a USB port (it has no optical drive), it's pretty much a brick.

---

### Post by Docaltmed on 2011-08-10
Hmm...it would seem that there is no upgrade path from 9.10 to 10.04, so I can't just upgrade via the 'net.

---

### Post by Docaltmed on 2011-08-10
Have now tried all available USB ports with live USBs containing 10.04 and 11.04, both of which were used to boot other computers. 

Still no joy.

---

### Post by isantop on 2011-08-11
Have you tried pressing F10 repeatedly during the BIOS splash page? That will bring up a boot menu you can use to tell the computer explicitly you want to boot off of the USB drive.

---

### Post by Flyers2391 on 2011-09-03
I am having the same problem.  Ubuntu 11.04 on a live USB (known working on other computers) and it shows in the BIOS, but after hitting F10 for boot devices, only the hard drive is listed.

---

### Post by dmoconnell on 2011-09-03
First let me throw out my "I'm New" warning. Now for the real stuff. I've heard that you need to flag a usb key to be bootable (using Gnome partition editor you can do just that) Could it be that usb creater is for some reason not marking it bootable? I've used that program and have never had a problem but things happen.
Try simple going into Gpartion editor 
Select your USB from the upper right corner drop down then in the main window right click and select flags - select boot
Hope this helps
Dm

---

### Post by Flyers2391 on 2011-09-04
> **dmoconnell said:**
> First let me throw out my "I'm New" warning. Now for the real stuff. I've heard that you need to flag a usb key to be bootable (using Gnome partition editor you can do just that) Could it be that usb creater is for some reason not marking it bootable? I've used that program and have never had a problem but things happen.
Try simple going into Gpartion editor 
Select your USB from the upper right corner drop down then in the main window right click and select flags - select boot
Hope this helps
Dm

thanks for the response, but I know it is working on other computers.  I tested to ensure (in case something happened to it since a week ago when I booted to it on a Dell) it still booted on my non-System76 laptop.

I tried every option change in the BIOS I thought COULD change what would happen but I got nowhere.  The most promising thing to happen was the drive would light up like it was being read and then the screen would show "boot error".  The drive boots fine on other computers but not on any ports on the ment1 :(

---

### Post by macpj on 2011-09-05
I was having the same problem with my Meerkat. I put a fresh image on a USB flash drive I had and ran into the same problem. USB worked & showed up on other machines, however would not show up in boot list. Finally I decided to try a new USB flash drive. I bought a RocketFish 4GB USB flash, installed the image & was able to boot the machine from it. I don't know what the issue was, but the new drive worked for me..

---

### Post by Docaltmed on 2011-12-27
Ok, I'm at a total loss. I have tried multiple flash drives, multiple images, everything boots just fine on multiple other computers...

Then I plug it into my System76 and all I get is still boot error.

I have even tried using Netbootin to create a minimal install partition on the hard drive. But when I boot using the Unetbootin option from the Grub menu, I get an Error 15 file not found error.

I've traded emails endlessly with System76, they are out of ideas. 

One last chance before I chuck this piece of garbage in the trash. Any suggestions? Anything?

---

### Post by macpj on 2011-12-28
I had a similar problem with my Meerkat. I had a 1GB flash drive, a Kingston I think. I formatted it and loaded on 10.10, machine would not boot. Download another image of 10.10, put it on the flash drive, tried it again, machine would not see the flash drive. I went on like this for 2-3 days. I tried 2 different flash drives & neither would work.
For the hell of it I bought a brand new flsh drive, a Rocketfish 8GB drive. I put a 10.10 image on it and the machine finally saw it and did boot up. Why, all of a sudden with the new drive ? Who the hell knows, but it did work and I could install 10.10 on my internal drive.

---

### Post by Docaltmed on 2011-12-30
> **macpj said:**
> I had a similar problem with my Meerkat. I had a 1GB flash drive, a Kingston I think. I formatted it and loaded on 10.10, machine would not boot. Download another image of 10.10, put it on the flash drive, tried it again, machine would not see the flash drive. I went on like this for 2-3 days. I tried 2 different flash drives & neither would work.
For the hell of it I bought a brand new flsh drive, a Rocketfish 8GB drive. I put a 10.10 image on it and the machine finally saw it and did boot up. Why, all of a sudden with the new drive ? Who the hell knows, but it did work and I could install 10.10 on my internal drive.

Great story! I guess some computers like mustard, some like ketchup...

Anyway, I finally licked the problem. Found on a wiki somewhere instructions on how to install Ubuntu directly from the internet. I plugged in the Ethernet cable and started the process (which involves some minor-league messing around with Grub). 

In the middle of it, the screen went blue. Man, that is ugly, I haven't seen a BSOD for a while. I threw my hands up in disgust and wandered off to drown my sorrows in a large order of fries. I was so frustrated, I didn't even bother to shut down. I think I was secretly hoping the thing would blow itself up.

I come back from lunch, and low and behold, there's an installer asking me what time zone I was in! From that point on, things rolled in like kegs at a frat party, and an hour later I was up and running again with a modern OS. Sweet. 

I guess the trick on this machine is going to be to not let it get so far behind the curve again.

---

