---
title: "Does anyone have a factory original Acer Aspire SA10?"
date: 2014-10-13
forum: The Cafe
---

### Post by MibunoOokami on 2014-10-13
I was given an Acer Aspire SA10 desktop pc yesterday and was told it only needs an HDD and a VGA cable. I opened the tower to have a look inside and to clean any dust that may be in there and there are about 13 plugs attached to cables that aren't connected to anything. I have absolutely no idea about how things should look inside a desktop tower but I can't imagine an HDD requiring 13 plugs. After spending half a day searching the net for service manuals or tutorials and whatnot only to come up empty handed, I thought I'd ask for help here.

If anyone has an Acer Aspire SA10 that is factory original, would you mind taking some photos of inside the tower and perhaps label what all the plugs/cables are connected to. Or if you have a service manual I could use that too would be appreciated.
The reason I say factory original is that is likely easier for me to understand as opposed to a customised one.

Thanks.

---

### Post by user1397 on 2014-10-13
what would be quite helpful for those of us who don't have that exact computer but still want to help you, is for you to take pictures of the inside and show them to us :P

---

### Post by MibunoOokami on 2014-10-13
> **ubuntuman001 said:**
> what would be quite helpful for those of us who don't have that exact computer but still want to help you, is for you to take pictures of the inside and show them to us :P

Good point. I jut went to add one but apparently images must have a url extension

---

### Post by oldfred on 2014-10-13
If using a camera, best to shrink them to screen shot size first. Forum did not allow large files to be attached. And they need to be .jpg type.

I think this is the older version of the forum, but it still works the same, just looks different.
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

And if you use advanced editor you can easily attach screen shots or small photos with the paperclip icon.

Usually vendor systems do not have extra cables except perhaps for added drives. But I just built a new system and power supply has many cables and various connectors for hard drives, motherboard, video cards etc.

Bit older now, there are newer youtube and hardware sites with lots of details.
[http://arstechnica.com/gadgets/2011/04/how-to-build-your-own-computer-ask-ars-diy-series-part-i/](http://arstechnica.com/gadgets/2011/04/how-to-build-your-own-computer-ask-ars-diy-series-part-i/)

---

### Post by MibunoOokami on 2014-10-13
I had been trying to use the icon of a picture to upload them.

Working from right to left, first is the entire inside of the tower, next is a few of the plugs, the middle picture is a plug that has no room to move and there's no socket for it to plug into. The fourth image is of a cable with a tag saying something about USB (I forgot to write it down). The last image I'm guessing is the actual HDD ribbon with about 3 plugs on it.

If these plugs don't need to connect anywhere and all that's missing is the HDD, I have a quick question. I have a spare laptop HDD which I'm to understand I could buy an adaptor to use it in the desktop, but I'm wondering if I could get away with an even cheaper option and run the desktop using and external USB drive?

[ATTACH=CONFIG]257188[/ATTACH][ATTACH=CONFIG]257189[/ATTACH][ATTACH=CONFIG]257190[/ATTACH][ATTACH=CONFIG]257191[/ATTACH][ATTACH=CONFIG]257192[/ATTACH]

I forgot to add, the only additional devices(?) on this machine are a DVD writer and SD card reader, both of which appear to be connected.

---

### Post by oldfred on 2014-10-13
Your first is a parallel cable.
       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

I think all the others are your power plugs.
Power supplies may be classified as modular, semi-modular or not. Your looks like it is not modular or just has all its cables. Modular power supplies have plugs at both ends of cable, one into power supply. Semi has some permanent and some that you plug in.

Your connections on power supply look like most are for SATA drives, but you should have connectors for your PATA/IDE drive. Much better to use SATA drives if possible. The old wide PATA/IDE cables restrict air flow and are harder to work with. You may have to check that jumpers are correctly set on drive and you have 80 conductor cable. You may have the old 40 conductor cable, possibly from an old CD/DVD drive. Do not use 40 conductor cable.

---

### Post by MibunoOokami on 2014-10-14
After reading the info contained in the links you provided, I think I have an 80 conductor cable. I base that on a blue plug connected to a board in the machine which is hard to see in the photo and then the grey and the black plugs. As I understand it a 40 conductor cable would have only grey plugs.

Having said all that, the rest is quite over my head. If the other plugs are power plugs, should they be connected to something? The majority of them are female plugs and there doesn't appear to be any male connectors. Or is it that the plugs won't be used unless adding additional drives/devices? 

Are you or anyone else able to tell from the photos whether or not I can use the machine in its current condition? That is, can I power it up, change the BIOS setting to boot from USB device and run the machine from an external drive?
I suspect the answer will be without physically seeing the machine there's no way to tell but I thought I'd ask anyway.

---

### Post by oldfred on 2014-10-14
The power supply just has all the cables for all the potential extra drives, DVD drive, video card or other devices. Only the devices you have need power, the rest just should be neatly bundled and tucked away.

If you scroll almost all the way down is a photo comparing a modular power supply to a non-modular one. Yours just has all the cables.
[http://en.wikipedia.org/wiki/Power_supply_unit_%28computer%29](http://en.wikipedia.org/wiki/Power_supply_unit_%28computer%29)

You should even be able to boot without any drive into UEFI/BIOS. That was how I tested that I had motherboard, power supply and video card correctly configured before I screwed motherboard into case. Then I plugged in hard drives. But you could just use a bootable flash drive to test.

I hated the old PATA/IDE drives with the tiny jumpers. Before cable select you had to set master, slave or now cable select with the really tiny jumpers. And then when ever I opened case I would manage to bump the wide Parallel cables just enought that they might be partially connected. System might show drive but not work. Open case push on connector and it would work.
Did I mention I really hate those tiny hard drive jumpers.  (old eyes and clumsy fingers do not help). :)

I converted all drives to SATA drives as soon as they were only $10 more than PATA drives. Now they are the same price or cheaper. Not many systems still use the older PATA/IDE drives.

---

### Post by MibunoOokami on 2014-10-15
Oh my, I get the feeling you hate those tiny hard drive jumper things there oldfred ;),

Thanks for your help oldfred I wasn't sure whether or not they needed to be plugged in. I energised the desktop the way it is and it seems to work fine. Now I just have to find the USB cable for my external drive and get the machine to move.

---

