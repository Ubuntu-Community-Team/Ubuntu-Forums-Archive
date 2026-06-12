---
title: "Need help selecting lightweight &quot;flavour&quot; to run on old hardware and replace Windows"
date: 2019-01-13
forum: Ubuntu, Linux and OS Chat
---

### Post by pebkac on 2019-01-13
Hi all,

I don't have a lot of Linux experience. I work at a not-for-profit with a very limited budget. We have 5 old workstations (Dell Optiplex 755) that currently run Windows Vista. These computers are extremely slow and worse, run unsupported software. They are in dire need of being replaced but we don't have the money in our current contract.

Computer stats:
CPU: Intel Core 2 Duo E4500, 2.20 GHz, 2 MB cache, 64-bit
RAM: 1 GB 667 MHz DDR2
Hard drive: 80 GB SATA

I came up with the bright idea to maybe add some cheap RAM to bring them up to 2 GB and then run Linux on them, since at least then the software would be current and far more secure.

Due to our user requirements, though, I am not sure which version of Ubuntu will best serve our needs.

The computers are public workstations and are not only very locked-down with Group Policy, they have Steady State installed on them (a Microsoft offering that essentially reverts the machine to a saved-image state on reboot but allows modifications, such as updates, to the image when logged in as an administrator.)

So, the flavour I am looking for needs to not only be very lightweight to run on our old hardware, it also needs to be user-friendly for the public, and have software that will allow me to restrict the user such that they can't change the desktop, can't install software, can't access settings, etc; while allowing me to maintain full administrative control.

I had considered lubuntu due to the fact that it works well with old hardware but then ruled it out because it doesn't have/allow "lockdown" software (apparently this is a limitation of LXDE?)

Any other recommendations of something that would work well in our scenario?

---

### Post by oldrocker99 on 2019-01-13
Yes, you should bump up the RAM, and up to 4GB if possible.

Linux is perfect for giving new life to an old, decrepit PC.

There are several lightweight Ubuntu flavors: Lubuntu, Xubuntu, and, my favorite, Ubuntu MATE, which is perfect for beginners and power users. Ubuntu MATE is quite lightweight, and very configurable, allowing the top-menu default, or a Windows-like desktop (Redmond), a Mac-like desktop (Cupertino), and even the disgraced and no longer used Unity desktop (Mutiny). It is by far the most powerful and, as I said, 
easily configurable. One thing about Linux is that there are quite a few desktops available, and, if you don't like one, install another, and choose it from the login screen.

As the primary user, you are root, in other words, able to change system settings, install and remove software, and, for that matter, get and install updates. As root, you can make user accounts without that ability, while making everything else work. UNIX and Linux are both built from the ground up to have multiple users, each with their own /home folder, which stores only that user's settings.

I think that's what you mean by "lockdown," but I might be mistaken.

Let me know.

---

### Post by him610 on 2019-01-13
Xubuntu or Lubuntu will run fine on the systems you described. More RAM is better and those machines max out at 4 GB. I have two machines with similar CPUs that have been running Xubuntu ever since I built them about ten years ago.

You should have four memory slots on the motherboard unless you have the Ultra small form factor Computer which only has two. When adding memory, make sure the memory is compatible with the memory already installed. 

You can find the Dell manual for those machines at [https://www.dell.com/downloads/global/products/optix/en/opti_755_techspecs.pdf]("https://www.dell.com/downloads/global/products/optix/en/opti_755_techspecs.pdf")

Good luck, and I hope you are successful.

---

### Post by Geoffrey_Arndt on 2019-01-14
pebkac . . . I "assume" that you are aware these 5 machines running Vista will not run the familiar Windows programs in Linux.   For example, if running MS-Office, now will run LibreOffice or similar with the associated learning curve.  Any specialized Windows software may not even be available in Linux.  A VM will not work with these machines at 2gib ram (further, WINE is not a good option either).   So, I'm not saying to change your plan(s), but be prepared to deal with issues from OS training to software training.

---

### Post by mastablasta on 2019-01-14
> **pebkac said:**
> 

The computers are public workstations and are not only very locked-down with Group Policy, they have Steady State installed on them (a Microsoft offering that essentially reverts the machine to a saved-image state on reboot but allows modifications, such as updates, to the image when logged in as an administrator.)



i believe the guest account could do that. 

or are you looking for some kind of Kiosk OS? : [https://www.how2shout.com/tools/free-open-source-linux-kiosk-distros-browsers.html](https://www.how2shout.com/tools/free-open-source-linux-kiosk-distros-browsers.html)

you did not say what kind of applications you need to run or what the users use. if the OS users use only browser then 2 GB of ram will do. note that poor GPU could limit the experience as well.
new ddr2 RAM could be expensive, so you should get your hands on some used one.
these PCs do not seem 5 year old to me. this tech is more than 11 years old.

---

### Post by clicktek1 on 2019-01-14
I have saved many old laptops with XFCE (Xubuntu) and LXDE (Lubuntu).
I personally prefer XFCE between the two. I also think it will play nice(r) with your users. *-my opinion*
As others have said, if you can add RAM go for it. 

I'd throw Xubuntu on one and see how it goes.

---

### Post by MartyBuntu on 2019-01-14
> **pebkac said:**
> I work at a not-for-profit...

The computers are public workstations...


What are your expectations that a presumably large group of people are going to be willing to accept an unfamiliar operating system on old hardware?

Sorry, I don't mean to be a Danny Downer...and I also realise I'm not familiar with your organisation's case uses. Being a non-profit, your group might be eligible for a deep discount for Windows licenses...if not even free...then offer an introduction to Ubuntu and Linux as a "club".

Of course, I might be completely wrong. That has been the case for me in the past...I'm told!

---

### Post by mastablasta on 2019-01-15
> **MartyBuntu said:**
> What are your expectations that a presumably large group of people are going to be willing to accept an unfamiliar operating system on old hardware?


that's why it depends on the use case. if they offered only browser on the PC (internet access) then it will work. operating system shouldn't matter. also it depends what kind of apps they are using . if they used LO until now then again the new OS won't matter to the users etc.

---

### Post by jdeca57 on 2019-01-15
> **MartyBuntu said:**
> What are your expectations that a presumably large group of people are going to be willing to accept an unfamiliar operating system on old hardware?


But Windows 10 isn't Vista so some flexibility will always be necessary. It will be different, even browsers change over time. The only worry is response time. And with an additional GB that will be better, no matter if you would use Wndows 10 or Ubuntu. I use XFCE in Xubuntu. Open the menu and choose Web Browser and you get... Firefox. For me, having used different browsers that's no problem. But I know of people needing a lot of help in order to overcome small differences. And what about mail?

---

### Post by pebkac on 2019-01-16
Wow, what an interesting discussion this has turned into! Thanks everyone who took the time to reply.

I'd like to address some of the questions.

What I mean by "locked down" well, the users are members of the general public; as in, anyone can just walk up to a computer and sit down and use it. The users do not have individual computer accounts as we do not require registration. On our existing set up, there is one administrative account and one user account. The user account can't change the desktop, settings, or install applications nor can they save documents except on a removable drive. I accomplish this via Group Policy and Steady State in Windows. I don't know how to do this in Linux but I imagine it would not be part of a standard Linux installation. Something that would be used to "lock down" a school computer lab might be appropriate.

There are 5 workstations i need to update (not 5 years old; just 5 total. They are from around 2006 or so). They are in a lab containing a mix of computers as we replace them in small batches as we have budget. We also have a few Windows 7 and 10 computers, so users can choose which computer they would like to work on as long as there is availability. Generally, people only work on these ancient dinosaurs if the newer ones are already taken.

Software required: They need to run an Internet browser preferably Chrome or Firefox - probably Firefox since it might be less resource-intensive. An office program that's compatible with MS Office documents, so they can open documents created in Office and also so they can use these documents on a Windows PC. I believe LibreOffice can do this. Be able to print to our 2 IP photocopier/printers. That's basically it. There is no email (people use their personal Gmail or whatever they have). Staff is available to assist anyone who needs help. But we already have Chrome and Firefox on the other computers as well. Oh, and I do allow people to use basic programs that come with the computer (such as calculator, notepad, etc) so it doesn't need to be a kiosk per se, although I suppose that is one option we could look at.

The computers are are the SFF (Small Form Factor) model, and they support 64-bit architecture and up to 8 GB of RAM, although with our budget we will most likely upgrade to 2 GB (or if we get a cheapo brand, possibly 4 GB). Thanks to the person who provided a link to the manual. Very helpful!!
Yes, we do qualify for Windows licenses for cheap being a not-for-profit. However, the computers themselves (hardware) will not run well with a newer, supported, version of Windows. They can barely even run Vista anymore. It takes over 5 minutes just to boot up and one minute to open a browser. And we are not able to replace these machines for at least another year (and even then it might not be all 5 of them).

I have some experience with Linux, but not much. I've never been a "Linux Administrator" before so I want to make sure I have thought everything through as much as possible before diving in.

What I am getting from all of you is that I'm on the right track considering Linux/Ubuntu and I should be looking at a MATE, XFCE or LXDE version - though the LXDE might not support the user restrictions I need (and now I can't find where I read that...)

TL;DR - Computers have a single user account shared by all users that needs to be locked down so no changes can be made.

All further suggestions welcomed.

---

### Post by mastablasta on 2019-01-17
> **pebkac said:**
> 
[COLOR=#000000]What I mean by "locked down" well, the users are members of the general public; as in, anyone can just walk up to a computer and sit down and use it. The users do not have individual computer accounts as we do not require registration. On our existing set up, there is one administrative account and one user account. The user account can't change the desktop, settings, or install applications nor can they save documents except on a removable drive. I accomplish this via Group Policy and Steady State in Windows. I don't know how to do this in Linux but I imagine it would not be part of a standard Linux installation. Something that would be used to "lock down" a school computer lab might be appropriate.[/COLOR]

...

[COLOR=#000000]Software required: They need to run an Internet browser preferably Chrome or Firefox - probably Firefox since it might be less resource-intensive. An office program that's compatible with MS Office documents, so they can open documents created in Office and also so they can use these documents on a Windows PC. I believe LibreOffice can do this. Be able to print to our 2 IP photocopier/printers. That's basically it. There is no email (people use their personal Gmail or whatever they have). Staff is available to assist anyone who needs help. But we already have Chrome and Firefox on the other computers as well. Oh, and I do allow people to use basic programs that come with the computer (such as calculator, notepad, etc) so it doesn't need to be a kiosk per se, although I suppose that is one option we could look at.[/COLOR]


that's basically "Kiosk mode". there are some OS out there that offer this functionality out of the box or at least are easy to administer via GUI. the mdoe itself can also be achieved in any *buntu. last time i saw it was i think 9.04 in an internet cafe, long time ago.

Firefox or Chrome can both be installed and they are not an issue.

Libre office can read MS docs, however the formatting can be off. same goes if you save in libre office and then open the text in MS word for example.
Not sure where WPS office currently stands and what their licence is in this use case. it is free for home use.

notepad, calculator... are standard or can be added (so many to choose from).

what kind of printer model are they? you will need drivers for them. HP, brother, samsung and i believe Epson (not sure since i haven't used one of those in a while) are not an issue. most of them have drivers in kernel and they would load them on boot.

you can test the OS live without install, see how well it works. ther eis an issue with USB "burning" software it seems. out of so many out there, only few support latest version of linux (despite their claim). they would produce an error on boot. look slike rufus is the one that can do a live USB well in windows and is suggested by Ubuntu. but you will need win7 or later to make it work.


finally - win10 should be faster than Vista, which was a mess anyway. but without knowing the specs it is hard to say. the free *speccy* utility in windows will provide them to you easilly, while in linux you can get specs form terminal:

lshw -sanitize
or install and run 
inxi -F

there is also an option to load windows 10 compability checker : [https://answers.microsoft.com/en-us/windows/forum/windows_other-windows_install/windows-7-81-10-compatibility-testing-for-windows/310e06a4-b181-45ec-ae6d-ee93a1632932](https://answers.microsoft.com/en-us/windows/forum/windows_other-windows_install/windows-7-81-10-compatibility-testing-for-windows/310e06a4-b181-45ec-ae6d-ee93a1632932)


finally, having done upgrade and tried to get old machines to run with small investment - the slowness could be due to old hard disk rather than lack of ram. make sure you test the disk with the makers' SMART software before investing in RAM. because it could be that the disks need the upgrade not RAM. 

Light linux desktops will *fly *even on 1 GB ram. but if hard disk has issues or if it is a slow one, you will get slow system even on linux. 

i upgraded RAM and CPU (single core 1.2 ghz with dual core 2.4 Ghz or something like that on old 1,3 GB ram machine upgraded to 2 GB (form DDR to DDR2). the PC should be at least 4x faster. however, the performance increased but not as much as i wold hope. only slightly. system still felt a bit sluggish and due to some other issues and after a smart disk test, i decided, once i had the money, to replace the IDE drive with a new SATA. the perfomance improvement was like night and day. so old hard disk was the main bottleneck it seems. moral of the story - check your hard disk health and output.

---

### Post by pebkac on 2019-01-30
@mastablasta Thanks for the detailed reply. I hadn't thought of testing the hard drives. I did test them and 3 of them passed fine (using [http://hddscan.com/](http://hddscan.com/)) one had slow responses and one took an entire day to finish the test!

Him610 posted the machine's tech specs manual (I think the 2nd reply). According to your link, only the Windows 8 compatibility assistant will run on Windows Vista, but as I have recently discovered that Microsoft Office is a requirement, that will likely be our only option.

I am thinking that I may still install XUbuntu with guest mode on one of the machines if it runs faster than W10, that will be our Internet-only computer :) That way if someone doesn't need to use Office, they can use a faster computer.

I appreciate everyone's responses; they were very helpful.

---

### Post by mastablasta on 2019-01-31
> **pebkac said:**
>  According to your link, only the Windows 8 compatibility assistant will run on Windows Vista, but as I have recently discovered that Microsoft Office is a requirement, that will likely be our only option.



8 & 10 are very very similar in their hardware requirements.

If the full office is not needed, the MS office 365 works in any browser. otherwise for MS office you really need windows. last version that worked well in wine (Word, Excel & Power point) was 2010 or 2013, can't remember exactly...  there was only a minor issue with SmartArt. it could on occasion crash the office suite. other than that it worked well. but then new version came and they no longer work in Wine as far as i know.

---

### Post by pebkac on 2019-01-31
@mastablasta - yeah, Office 365 in a browser won't meet our needs for a handful of reasons. We already have licences for Office 2016 but you can use those licenses for earlier versions like 2013, so if you have ever tried out MS office in wine, I would be interested to know how it ran. Slow? Error-prone? Effortless? Can Office be set up as a shortcut on a desktop that you can click to launch it, so it would work the same as in Windows?

---

### Post by wildmanne39 on 2019-01-31
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by mastablasta on 2019-02-01
> **pebkac said:**
> @mastablasta - yeah, Office 365 in a browser won't meet our needs for a handful of reasons. We already have licences for Office 2016 but you can use those licenses for earlier versions like 2013, so if you have ever tried out MS office in wine, I would be interested to know how it ran. Slow? Error-prone? Effortless? Can Office be set up as a shortcut on a desktop that you can click to launch it, so it would work the same as in Windows?

2016 (365) installer is Silver, so depends what you need... [https://appdb.winehq.org/objectManager.php?sClass=version&iId=35527](https://appdb.winehq.org/objectManager.php?sClass=version&iId=35527)
2013 installer is gold [https://appdb.winehq.org/objectManager.php?sClass=version&iId=26323](https://appdb.winehq.org/objectManager.php?sClass=version&iId=26323)


When checking the individual apps some gave it gold other platinum with newer WINE version. so i guess it is worth to try maybe. looks like 2013 has better working rate.

office in wine that we had installed ran fine. yes it runs like in windows with double click on desktop icon (for example in Kubuntu). wine stands for "wine is not an emulator". it's a compatibility layer that makes it run somr libraries and programs on linux. since it is not an emulator it often doesn't perform any worse than native install. of course it depends on the app and the libraries they use, but for example sometimes games in wine run even better than under windows. in emulator or virtualization (e.g. virtualbox) programs will always run at least a bit slower if not a lot slower than on native install.

 this was one of the requirements for my father at the time to keep linux, so we made it work. my wife also had it. the only issue i had was smart art causing occasional crash on one time but other time it worked. since i haven't needed the function i didn't get too bothered with this. also we only used MS Word, Excel and Powerpoint. so no onenote and other stuff.

lately we touched it less and less. for docs from work i use office 365 in browser and to write at home or make spreadsheets i use LO (still like MS more). i tried WPS but wasn't that impressed.

maybe in the future kids will need MS office. if so, we will probably install it in wine or we would need a windows PC or to run it in vbox on some "Black edition" of windows.

---

### Post by kurt18947 on 2019-02-01
Any idea why MSO is *required?* Libreoffice can be set to use MS file formats by default. I work in a very Microsoft-centric office and though I have no need to work with heavy duty financial stuff I have no problems with file compatibility. I do sometimes use the older .doc and .xls rather than their *X counterparts when sending. Receiving *X documents hasn't proven an issue. Someone else mentioned KingSoft office. That supposedly has excellent MSO file compatibility. Your situation seems like an excellent one for *buntu. Put word processor and web browser icons on the desktop - "click here to..." Guest session seem like it might work, log out and current session data is forgotten. I don't know which *buntu flavors support guest sessions by default, Xubuntu16.04 does I know.

---

### Post by SagaciousKJB on 2019-02-02
I wonder if a Live distribution and using Google Docs would be sufficient. I have basically replaced my need for LO with Google Docs (including Slides and Sheets). Meanwhile the live form factor means no changes to the disk will be persistent. That can be both beneficial and inconvenient.

Live installations have become extremely well populated with common apps so it's likely you could run them with out needing to install anything at all, and have everything you need. There are a few which are even heavily cloud oriented like Peppermint, but I don't know how it would run on your hardware.

Perhaps the ultimate in breathing new life into ancient hardware is Puppy Linux. To give some perspective, I recently installed it on a 800Mhz Celeron with 256MB of ram. Puppy is designed to be ran from CD or USB media, but also contains tools to help make user configurations persistent.

I can tell you from personal experience that your CPUs are not that outdated, and your main bottleneck is RAM. You will be able to eek by with 2GB with what you have described, but would be better off with at least 3. However if there is any chance at sourcing some SSDs, that will significantly boost performance. Otherwise you may find them a bit sluggish even with lots of free memory.

---

### Post by lammert-nijhof on 2019-02-09
I re-installed Linux on a Pentium 4 HT. With respect to hardware I have two (three) suggestions, that saved my day with my 2003 PC:

[LIST]
[*]Use 2 x 1 GB and enable hyper-threading in the BIOS. Why? It will increase your CPU speed with ~25% and you have more space for Apps and especially CACHING.
[*]Try to find free or cheap 40 or 80 GB disks and give each PC two disks 2 x 40 GB or 2 x 80 GB. Why? You could increase your disk IO speed with a factor 3 - 4 to around 200 MB/s. It makes the PC feel significantly faster.
[*]Nowadays you can buy new 128 GB SSDs for less than $25. I bought recently a &#65279;Silicon Power Ace A55 of 128 GB for $22,05 from Newegg. I assume you have SATA-2 interfaces, so the speed would be limited to 300 MB/s instead of > 500 MB/s, but that is still 4 - 5 times faster than those old 80 GB disks.
[/LIST]
My newer 2008 PC boots Ubuntu Mate in ~ 25 seconds  from SSD. My Pentium PC boots Peppermint from two compressed 40 GB IDE disks in 45 seconds.  I'm sure, that is faster than your more modern PCs with one disk. I expect, that you can fetch a coffee during booting. 

I think you should try to give the machine as much as possible the Windows look and feel, so I propose:
[LIST=1]
[*]Peppermint 9 Respin, a sexy sister of Lubuntu based on Lubuntu. It has that Windows look and feel out of the box. I used it on my Pentium and idle it is happy with ~310 MB.
[*]Xubuntu 18.04, You need to tweak the user interface a little bit, move the panel from the top to the bottom and add some launchers for frequent used programs next to the Menu/Start button. I use it on my i5 laptop. It will be happy with ~380 MB in idle.
[*]Ubuntu Mate 18.04, which has a "Redmond look and feel" as option in Mate Tweak. I use Mate on my heavy upgraded 2008 HP dc5850. It will be happy with ~450 MB in idle.
[/LIST]
I would use the standard Guest user of those Linux distros, the Guest can use all facilities of the OS. They can't modify anything in the system. They can store data, but all that data is erased, if they logout. They can save that data on an USB stick before logging out.

I would use the BTRFS file system, because it allows you to use those recommended two disks together in a kind of RAID-0, doubling the disk speed. It also allows you to use compression (LZO) and that will improve your disk speed with a factor 1.7, also for one disk. These two measures reduced my boot time from a couple of minutes to 45 seconds. This BTRFS file-system also uses a lot of caching and that improves your disk IO even more. On my Pentium PC I load Firefox in ~1 second, only the first time after booting it takes 5 seconds.

Linux also supports Chromium out of the box and even Google Chrome is available, but I prefer Chromium or Firefox, just try both and look which one works best on your PCs. You could even install both and let the user choose.

For office work use the Peppermint Cloud facility for Microsoft Office as already installed. For the other Oses, they can use it through the web browser. If that cloud service costs too much or is insufficient, use LibreOffice and have pamphlets or a big sheet on the wall with an explanation, how you can save the document in the correct MS-Office formats. **Make sure that you have installed the Microsoft fonts to avoid formatting misalignment!!** It will work for 99% of the cases. While still working in 2009-2010, I even saved colleagues twice, who had problems with MS-Office and documents in Word format. I loaded those complex Word documents (hundreds of pages) in LibreOffice and saved them in the preferred Word format version.

---

