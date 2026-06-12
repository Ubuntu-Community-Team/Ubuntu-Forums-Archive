---
title: "Can I Let Windows 10 Go?"
date: 2020-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2020-11-22
Currently experimenting with win10 on kvm and so far very impressed. I dual boot with win10 but hardly use it so looking to go 100% Linux.  I currently enjoy a Samsung SSD that, when purchased, I upgraded the firmware using a Samsung utility via windows 10.  Eventually I will move to m2 form factor (at the moment nice to have rather then need to have!) and would like to stay with samsung but could go with another supplier.  It seems to me many many manufacturers do not support Linux so I could be stuck not being able to update any hardware if I went 100% Linux.  So perhaps I need to keep my windows partition(s).  If one is 100% Linux and buys say, a year old bit of hardware that has firmware update(s), is there not a big danger that said hardware could not be updated?

---

### Post by oldfred on 2020-11-22
My Samsung NVMe drive has a bootable ISO for firmware updates.
The Samsung Magican is Windows for consumer use.
I found an old Linux version of Magican in commercial area, but never got it to work for updating my old Samsung SATA SSD.

Vendors are adding firmware update support here, but mostly just newer hardware and not all vendors.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by crip720 on 2020-11-22
For general hardware I would recommend having a small Windows partition for bios and firmware updates.  There are usually ways of doing it from Linux, but usually faster and easier just to boot into Windows, do update and then go back to Ubuntu/Linux.  Some hardware/computer makers will have ability to do this from Linux, but each one has to be checked.

---

### Post by mastablasta on 2020-11-23
i was wondering the same thing. i have very old windows XP machine, but i was thinking if maybe it is time to change it as i haven't boot to windows for almost 2 years now. 
if i upgrade the hardware, then windows XP won't work anymore. so i am not sure if i should "upgrade" it (use the good components and replace some with newer stuff) or replace it and continue to use the old machine in some other way.

anyway, i was wondering is it possible to do firmware updates using FreeDOS? what about some windows rescue disk of sorts? and then run it though that?

---

### Post by oldfred on 2020-11-23
Most of my old Windows systems required me to download the update file, perhaps extract it, and run an exe file to update BIOS. But that could be from FreeDos or Windows. Some even had a DOS image with updates, so all you did was create the bootable drive. That may have been back with floppy drive days?

Many new systems now have 3 ways, from Windows, from UEFI reading update file from any FAT32 formatted partition or drive, or the update from a DOS executable. 
Both my 2014 Asus and 2016 Gigabyte update directly from within UEFI, and I make the  FAT32 ESP larger so I can save updates into it. But have to change default permissions in fstab, now to be able to use it.

---

### Post by DuckHook on 2020-11-23
Windows tends to muck up a lot of Linux things. It defaults to hogging the whole disk and does not even pretend to work well with other OSes. It also defaults to secure boot and fast boot, which play havoc with Linux partitions. It just assumes that no one would want any other OS on their system and conducts itself as a self&#8209;absorbed preening princess. Most of all, having it hang around on bare metal when it is not really necessary is a massive additional security risk.

I would understand why a Windows partition is necessary if you game or must use apps that require bare metal access, but if your Windows needs are met by a VM, then to me, it makes no sense to put up with the added complexity and security exposure.

I've never had a problem installing firmware through alternate methods. The most simple one is a DOS&#8209;based USB stick. I've yet to run across a major OEM who does not offer such firmware upgrade alternatives, but I freely admit that my experience is anecdotal and highly limited at that.

I've been running pure Linux boxes now for about a decade and so happy for the simplicity and ease of mind in not having to deal a Windows partition. However, my Windows use is so little as to be insignificant, so it may not be a good reflection of your needs.

---

### Post by TheFu on 2020-11-23
Have a well-known brand of usb3 7-port hub that needed a firmware update to correct some known linux/bsd disconnect problems.  The only update tool ran under 64-bit Windows and required a usb3 port to work.  Usb2 ports and 32-bit Windows don't work, which is what my laptop had.  The vendor understood my issue and offered to provide a patched device, but wouldn't commit to sending **my** hub back, just a similar hub that had been refurbished.

I have an old slide/negative scanner that only works with XP. Fortunately, VM usb2 passthru works for that.

Unfortunately, there are still times when Windows is necessary. and it needs to be on real hardware.  I tried the firmware update using usb3 passthrough, but that failed.

---

### Post by DuckHook on 2020-11-23
> **TheFu said:**
> …Unfortunately, there are still times when Windows is necessary. and it needs to be on real hardware.  I tried the firmware update using usb3 passthrough, but that failed.
A good counter&#8209;example to my post above. Were I confronted with this sort of problem, I would take the offending piece of equipment to a friend's or a relative's PC, buy them a beer, and ask them for the favour of the use of their Windows box.

---

### Post by TheFu on 2020-11-23
> **DuckHook said:**
> A good counter&#8209;example to my post above. Were I confronted with this sort of problem, I would take the offending piece of equipment to a friend's or a relative's PC, buy them a beer, and ask them for the favour of the use of their Windows box.

Exactly.  Took it to our weekly LUG meeting and asked someone running Windows to help.

---

### Post by mastablasta on 2020-11-24
ok, but that's external hardware.

Linux is spreading in out house. They way we go about it is - give it a try, see it it fits, if not we will buy&install windows later. We now have for example we now have 4 PC + RaspberryPi + HP home server on linux. 2 of these have windows. one has windows XP, which i haven't really used in a while. another one has Windows 7 Starter (if only it had home i could upgrade the RAM and get a bit more out of this PC).

anyway the external components are the classic mouse, keyboard & speakers, and then we have video cameras (important for online school right now) and printer/scanner. they all had linux support from the start. drivers were in kernel or in some cases were provided by manufacturers.

this install & see if it works out also went surprisingly well so far. since we don't play online much and some older games are just as fun if not more than latest ones (we can't afford latest ones anyway), we managed to install and have fun with a number of native games or via Playonlinux. sometimes there is a lot more work that goes into install, but in the end they work well. i write down the method for next time and move on. i think if *"anticheat" software* issue is resolved in some way so it works on linux, then most online games would work as well. again we don't game online (except a bit of CS:GO), so for now its fine for us.

we had some issues with *"online schooling"* when they sent MS office docs. but we managed to work around that using my work account. it's actually one of the things i miss on linux. a good office application. libre office is just now as friendly and is behind MS office in most areas for about 7 - 10 years. ease of use for us that work with mouse and don't know all the shortcuts is just not there. anyway with strong modern PC and enough disk space, VM would be a very easy solution if i really needed the office apps (e.g. for school). 

government went to OS agnostic signing app, most services are web based and can be accessed from any OS. and also i if really needed windows it could be done via VM.

so the only thing windows would now be needed is is UEFI or some other internal hardware needed a firmware update. which is why - if it works via FreeDOS or other option it is not really an issue as well. in the old days you can do it with DOS floppy drive and some jumper move, but i imagine they have other methods now. i did that only two times. once when i upgraded BIOS on a Pentium II PC with special socket that could hold 1.6 Ghz Celeron and it required a BIOS upgrade and second time  when i had issues with motherboard and was hoping BIOS upgrade would resolve them. it didn't really...

edit: *also windows might be needed to manage NTFS drives (internal/external)- which i have quite a few. windows tools are needed to repair windows file systems. however, maybe windows system repair disk or ultimate boot CD could handle that. there are also Hirens boot CD, SystemrescueCD...*

---

### Post by kurt18947 on 2020-11-25
As others have said, sometimes there is no work around to having Windows. I have a couple devices that require monthly database updates. One is distributed as an .exe file, the other uses a Windows app. I have a laptop that dual boots and so far the only problem I've run into is Windows updates mucking up GRUB. I keep a boot-repair live USB close to the laptop just in case. So far so good. You might be able to shrink your Windows install using Windows tools so it takes up less space, just leave enough room for updates etc.  I also deleted the Windows repair (or whatever it's called) partition.

---

### Post by Quarkrad on 2020-11-27
Interestingly, having just read the Samsung site.  They actually state in their Firmware Update Utility Manual, page 5 (for the 950 PRO NVMe M.2 SSD)

"...Restart the computer in Linux mode with the USB Boot device...."

Their method is download the iso update, burn it to a usb and boot to the usb - so their methodology covers, linux, win and osx.  Not sure what other mainstream manufactures do but this has got to be a positive approx re reliance on Windows.

---

### Post by oldfred on 2020-11-27
With my Samsung NVMe drive, I downloaded the ISO and was able to use grub2's loopmount to boot it & update SSD.
It only had the one update for my NVMe drive  and looked very basic.

---

### Post by poorguy on 2020-11-29
I keep Windows 10 OS around because some websites I need access to only allow Windows 10 OS access and I still ain't figured out the reason for that so in my case I need to keep an up to date working Windows 10 OS around.

Other than those few Windows 10 only websites Ubuntu 20.04 and Lubuntu 20.04 work OK as my daily drivers.

---

### Post by kurt18947 on 2020-11-29
I haven't come across any Windows 10 only web sites. I have come across some sites that really only work with Chromium based browsers, I keep Vivaldi for those. I've also found that for sites that seem to be Chromium only, restarting Firefox in safe mode often works.

---

### Post by mastablasta on 2020-12-01
> **poorguy said:**
> 
Other than those few Windows 10 only websites Ubuntu 20.04 and Lubuntu 20.04 work OK as my daily drivers.

impossible. even MS dumped Explorer.

anyway a PXE boot environment in virtualbox would work for those. and with enough ram and CPU running another OS in vbox is not an issue. so even in this case it is not really needed.

so the only need would actually be AAA games or complex specialised GPU software.

---

### Post by poorguy on 2020-12-01
> **mastablasta said:**
> impossible. even MS dumped Explorer.

Please tell that to my state retirement website.

Not all state offices use the latest OS and most don't.

We some have state offices still using Windows 2000 and Windows XP and internet explorer because that's what their old proprietary software programs will run on.

---

### Post by mastablasta on 2020-12-02
voters should do the push to have all systems made for people OS agnostic (how are those with android or iOS/MacOS supposed to connect on them?!?) and not to run critical systems on outdated OS.

NHS learned this was a mistake in a hard way.

i am not saying we have it perfect over here, but every 2 years or so i can see there is a small shift. so we go slow, but they are moving forward.
few examples:
- digital signing component now has a linux version
- websites can be entered without digital signature (password, 2FA)
- websites are moving to responsive ones
- websites get help sections (mouseover the "?" ) that are super easy to follow
- what can be done automatically is. for example people don't file tax returns, instead they are calculated by state and you get a detailed report. and them you can file a complaint if they missed anything or leave it and you get the returns. 

- we can interact for various social help and stuff via web forms
- we can now see our own doctors report/files all online. we can order an appointment on level 2 or they order it for us. depends.

anyway there are even more thing, even so i think we are well behind other EU countries.

---

### Post by Shibblet on 2020-12-02
I only use Windows for Adobe Software.  I purchased a copy of CS6 back in 2013, and it does what I need it to.  But it works great in a Windows 7 VM... so all is well for me.  I would switch to Free / Open Source Software, but some of the replacements aren't really up to snuff.

[LIST]
[*]Adobe InDesign can be replaced with "Scribus."  But Scribus doesn't do 1/4 of the things that you can do with InDesign.  Transparent areas, outer-glow for text, outlining, etc.
[*]Adobe Illustrator can be replaced with Inkscape.  Inkscape is a great vector editing program, but Illustrator has a lot more tools and quick steps that make design work a lot easier.
[*]Adobe Photoshop can be replaced with GIMP.  Gimp can do just about EVERYTHING that you can do in Photoshop... except that Photoshop has Adobe PostScript printer functions for color matching and profiles, screen frequency and angle, and compatibility with commercial printers and print devices.  This is just an industry standard that is required for professionals.  It's not needed for the home-user who just wants to edit some photos.
[*]Adobe Premiere can be replaced with Kdenlive.  Kdenlive is an AMAZINGLY powerful video editor.  Premiere, however, has built in connectivity, compatibility, and data sharing with Adobe After Effects, which can be used for video compositing.
[/LIST]

So, it's not really Windows that I need, it's just Adobe.  If there was an Adobe Creative Suite available for Linux, I may actually look into it... however... For what I am doing, there were really no real advancements in the software since 2013.  I use InDesign, Photoshop, Illustrator, Premiere, and After Effects.  I had all of these programs on the Windows 10 machine at work.  I could literally do the EXACT same work with a program that is 7-8 generations older.

I noticed some feature differences, and backward compatibility, but other than that... Adobe really hasn't changed much over the years.  Except to get people to pay $70 a month instead of buying things outright.

---

### Post by CatKiller on 2020-12-03
> **mastablasta said:**
> voters should do the push to have all systems made for people OS agnostic (how are those with android or iOS/MacOS supposed to connect on them?!?) and not to run critical systems on outdated OS.

More than that, something like [this](https://publiccode.eu/).

---

### Post by CatKiller on 2020-12-03
I haven't used Windows in fifteen years. 

> **Quarkrad said:**
> If one is 100% Linux and buys say, a year old bit of hardware that has firmware update(s), is there not a big danger that said hardware could not be updated?

Linux has the [Linux Vendor Firmware Service](https://fwupd.org/). Don't buy from companies that don't use LVFS.

---

### Post by hk42 on 2020-12-03
Having ,at least,2 OS on a device is a very simple and efficient way
to diagnose between software and hardware problems.
I once disabled BIOS USB support on a a PC with only USB ports.
So I couldn't enter BIOS any more.
1 year later I found a BIOS update that worked from Windows.
Before deleting an OS make sure you can restore it from a backup.
After all you paid for it.

---

### Post by MartyBuntu on 2020-12-04
> **CatKiller said:**
> I haven't used Windows in fifteen years. 




Exactly the same here. My last Windows computer was XP SP2. I didn't hate Windows...I just fell in love with Ubuntu (but to be fair, I originally switched to PCLinuxOS, then Kubuntu 7.04 when I discovered it).

---

### Post by C.S.Cameron on 2020-12-04
I used Rufus to put **Windows-To-Go** on a 15GB USB stick.
A 64GB or 128GB stick would be better.
The make of flash drive makes a big difference in performance.

Oops, I now see the title of this thread is **Can I Let Windows 10 Go?** not [B]Can I get Windows 10 to Go?
[/B]
Well maybe keeping it on a flash drive is good enough.

---

### Post by Quarkrad on 2020-12-06
Thought from the bath:  updating the motherboard and cpu is a very infrequent activity so why not put win10 on an old hd and when an upgrade needs to be done unplug existing storage and plug in the win10 hd.  Upgrade and then put everything back - not going to take long.

---

### Post by mikewhatever on 2020-12-06
> **CatKiller said:**
> I haven't used Windows in fifteen years. 



Linux has the [Linux Vendor Firmware Service](https://fwupd.org/). Don't buy from companies that don't use LVFS.

Hah, easier said then done. Most companies don't for obvious reasons. It's like saying "Don't buy cars with wheels", good luck with that.

---

### Post by oldfred on 2020-12-06
@mikewhatever
Did you look at list?
Most new Dell for several years have been on list. Lenovo started a few months ago adding systems. HP looks like they just started. 
Many other smaller vendors and systems.

Direct link to info, vendors & devices.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)


[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start)
[https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd](https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd)

---

### Post by mastablasta on 2020-12-07
> **oldfred said:**
> 
Most new Dell for several years have been on list. Lenovo started a few months ago adding systems. HP looks like they just started. 


many devices are still off that list. it is good to see HP, Dell and Lenovo there. but the branded PC for example are quite expensive here.

anyway i still think that to do an update a windows 10 boot environment is all that is needed and that can be on DVD or flash drive. so you don't actually need windows installed. if more joined this initiative, then windows 10 would not be needed even for firmware update.

i am surprised Gigabyte is not there, but i guess it is the chip designer that should be (AMD/Intel).

notably missing are various peripheral devices. i.e. Garmin devices, maybe some drones, cameras etc.

---

### Post by CelticWarrior on 2020-12-07
My philosophy is that any firmware update should be OS agnostic. UEFI standards allow and recommend it.

---

### Post by mikewhatever on 2020-12-09
> **oldfred said:**
> @mikewhatever
Did you look at list?
Most new Dell for several years have been on list. Lenovo started a few months ago adding systems. HP looks like they just started. 
Many other smaller vendors and systems.

Direct link to info, vendors & devices.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)


[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-NVMe-SSD-Support-Start)
[https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd](https://www.phoronix.com/scan.php?page=news_item&px=Google-Require-Chromebook-Fwupd)

Well, those are some impressive lists. Unfortunately, none of the devices I've ever owned or used are there. Given the market share and popularity of "Desktop Linux", I hardly expect things to change in the next decade.

Also, your fist link about fwupdate leads to "This project is no longer supported."

---

### Post by mastablasta on 2020-12-10
> **mikewhatever said:**
> 
Also, your fist link about fwupdate leads to "This project is no longer supported."
as the Hitchhikers guide tells us : Don't panic! :)

continue reading... it says it moved to/merged with new project fwupd
[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)

---

### Post by mikewhatever on 2020-12-10
> **mastablasta said:**
> as the Hitchhikers guide tells us : Don't panic! :)

continue reading... it says it moved to/merged with new project fwupd
[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)

That is quite a bit condescending, didn't expect it from you.
I am sure oldfred would be glad to know one of his links is obsolete.

---

### Post by oldfred on 2020-12-10
I do like to know link is not working. 
I should always check before posting.

I have updated my Zim file so I have the correct link now, for the future.

---

