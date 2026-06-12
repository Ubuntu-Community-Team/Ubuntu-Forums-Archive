---
title: "How do I undo BIOS for Toshiba Satellite?"
date: 2012-07-03
forum: The Cafe
---

### Post by hanzj on 2012-07-03
Hello,
I upgraded the BIOS on my Toshiba Satellite (using the BIOS updater program, Toshiba Service Station, in Windows 7) to version 2.00. 

Now I'm having problems.

How could I revert to the previous BIOS version?

Toshiba Satellite C655-S5193.

---

### Post by NikTh on 2012-07-03
Can't you download the previous Bios version and install it via BIOS updater program ?

---

### Post by hanzj on 2012-07-03
NikTH,

I don't think that Toshiba keeps older versions. :-(

---

### Post by NikTh on 2012-07-03
> **hanzj said:**
> I don't think that Toshiba keeps older versions. :-(
Motherboard manufacturer maybe ?

I found something disappointing .. i will make a quote here .. 
>  
The same thing happened to me, and when my machine came back from repair, the hard drive was wiped clean, an unnecessary and costly (for me) step.  I wrote a letter to the president of Toshiba America, complaining about the fact that this has gone on for so long; **that they are pushing out a BiOS fix without an "undo"**, or if that is impossible, without a warning that an installation may kill your machine and hard drive contents; and that they are charging $25 to fix a problem that is 110% a Toshiba responsibility.  I ended up speaking on the phone to John Smithson in Corporate Relations, who said that they are no longer pushing out this "upgrade". As to all my other protestations about how Toshiba could be doing this to its customers for six months, he could only say he would pass along my concerns.  He will refund my $25.  And he will refund anyone else's $25 if you so ask for it.       I put this message up previously  in both threads on this problem with the name and address of the president of Toshiba, which is public information, and the phone number of John Smithson, and Toshiba took down both of my messages.  I did that to facilitate people asking for their $25 back, which Toshiba promised me to do for everyone affected.       My email is [EMAIL="mark4432k@gmail.com"]mark4432k@gmail.com[/EMAIL].  We will see if they allow this message to stay.  Nothing in here is factually untrue.  Update as of 3/26/2012: My message is still up and I did finally receive my $25**.**[B] 
[http://forums.toshiba.com/t5/Drivers-and-Utilities/Satellite-L755-S5216-BIOS-2-0-Update-leads-to-quot-VERIFY-ERROR/td-p/203226/page/2](http://forums.toshiba.com/t5/Drivers-and-Utilities/Satellite-L755-S5216-BIOS-2-0-Update-leads-to-quot-VERIFY-ERROR/td-p/203226/page/2)

[/B]So the option for undo or downgrade it seems that not exist.

---

### Post by oldos2er on 2012-07-03
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by mips on 2012-07-03
> **hanzj said:**
> Hello,
I upgraded the BIOS on my Toshiba Satellite...

Please provide the EXACT model of your computer, should find it on a label stuck to the bottom.

---

### Post by hanzj on 2012-07-03
> **mips said:**
> Please provide the EXACT model of your computer, should find it on a label stuck to the bottom.

Mips,
The model is Toshiba Satellite C655-S5193.

---

### Post by youknowme on 2012-07-04
> **hanzj said:**
> Hello,
I upgraded the BIOS on my Toshiba Satellite (using the BIOS updater program, Toshiba Service Station, in Windows 7) to version 2.00. 

Now I'm having problems.

How could I revert to the previous BIOS version?

Toshiba Satellite C655-S5193


UPDATE: The BIOS version 2.00 is online at [http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=3005260&rpn=PSC12U&modelFilter=C655-S5193&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=3005260&rpn=PSC12U&modelFilter=C655-S5193&selCategory=2756709&selFamily=1073768663).
Sadly, the previous version that I had, which did not have this problem -- I can't find online.

That sucks. I own a similar laptop - although i would not dare attempt to update the bios - unless i had a problem with it in the first place. I am not sure what you can do to fix it other than wait for another update. Is your machine still under warranty?

---

### Post by mips on 2012-07-04
> **hanzj said:**
> Mips,
The model is Toshiba Satellite C655-S5193.

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=3005260&rpn=PSC12U&modelFilter=&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=3005260&rpn=PSC12U&modelFilter=&selCategory=2756709&selFamily=1073768663)

[IMG]http://ompldr.org/vZW5lcQ/Screenshot%20-%2004072012%20-%2022:19:25.png[/IMG]

And you will get,

[IMG]http://ompldr.org/vZW5ldg/Screenshot%20-%2004072012%20-%2022:27:54.png[/IMG]

---

### Post by hanzj on 2012-07-04
Mips, Thanks for  indicating that older BIOS versions are available on Toshiba's website.

I'm very sad to say that the program will not install another version of the BIOS if the program detects an older BIOS version installed.

I thought I was clever by opening up Registry Editor and changing
[LIST]
[*] HKEY_LOCAL_MACHINE/Description/System/BIOS/BIOSVersion from "2.0" to "1.0"
[*]HKEY_LOCAL_MACHINE/Description/System/BIOS/BiosMajorRelease from "0x00000002" to "0x00000001"
[*]HKEY_LOCAL_MACHINE/Description/System/BIOS/ECFirmwareMajorRelease from "0x00000002" to "0x00000001"
[/LIST]
 but the BIOS install program still detects version 2.0.

What can I do to outsmart the BIOS Update program?

---

### Post by hanzj on 2012-07-04
Youknowme,
No, my laptop is one month out of warranty.

---

### Post by mips on 2012-07-05
You could try the bios manufacturers dos utility for flashing the bios. You gonna have to do some googling.

WARNING: Playing with bios tools 'could' brick your laptop if you are not familiar with what you are doing.

---

### Post by hanzj on 2012-07-05
Thanks, Mips,
The BIOS Updater could work if I put the program onto a DVD. (Though I haven't yet tried to see whether booting from DVD is also busted.)
-----------------
To all other Toshiba users:
Do you know how I can make Toshiba think that I _currently_ have an older version installed, so that I can install version 1.90 even if I have version 2.00 installed?

---

### Post by mips on 2012-07-05
> **hanzj said:**
> Thanks, Mips,
The BIOS Updater could work if I put the program onto a DVD. (Though I haven't yet tried to see whether booting from DVD is also busted.)


[http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-windows/](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-windows/)
[http://derek.chezmarcotte.ca/?p=340](http://derek.chezmarcotte.ca/?p=340)

Create a bootable DOS memory stick, copy the flashing util & bios image over to it, restart and boot off the usb stick.

---

### Post by hanzj on 2012-07-05
Mips,
In this thread, I did not say why I want to revert to an older BIOS.

The reason is because I can't boot off USB (and maybe not off the DVD either). [http://ubuntuforums.org/showthread.php?t=2013495](http://ubuntuforums.org/showthread.php?t=2013495)

---

### Post by mips on 2012-07-05
> **hanzj said:**
> Mips,
In this thread, I did not say why I want to revert to an older BIOS.

The reason is because I can't boot off USB (and maybe not off the DVD either). [http://ubuntuforums.org/showthread.php?t=2013495](http://ubuntuforums.org/showthread.php?t=2013495)

Lol, then my previous post is useless :biggrin:

Did you go into the bios and check all the settings related to booting?

Try a freedos cd image then (if the drive works)

---

### Post by hanzj on 2012-07-05
Mips,

Yes, I did go into the BIOS's boot order and made USB the first bootable media.


If only there was a way to trick the Insyde Flash program to think that I  don't have BIOS 2.00.
Where does the BIOS Updater program look to see what the current BIOS version is? If I knew its source, I can probably edit that source code and make that source code say "BIOS Version 1.00" instead of "BIOS version 2.00".

If anyone has expertise with code, please see the foler that the BIOS Updater temporarily installs on my hard drive at 
[https://www.dropbox.com/sh/z5gw1jkr5keok2x/RsnnEYRgiD/sc01v190](https://www.dropbox.com/sh/z5gw1jkr5keok2x/RsnnEYRgiD/sc01v190)

---

### Post by mips on 2012-07-06
Have you tried booting from the optical drive yet (even with a livecd)?

Most bios utils I know off check the actual image located in the bios itself.

I would really try and boot from dos based media and use the dos based utility.

Can you post a picture of the bios screen when the laptop boots up and one from when you have gone into the actual bios just after bootup where it shows the bios type and current image.

Do you have a spare hard drive you can put in the laptop or can you resize your existing partitions and create a new partition? DO you have access to another computer (desktop)? I'm asking this as there might be another viable option.

---

### Post by hanzj on 2012-07-09
[COLOR="blue"]Mips words in red. [/COLOR]

[COLOR="Red"]Have you tried booting from the optical drive yet (even with a livecd)?

[/COLOR]
Not yet. Will try to do so this week.

[COLOR="Red"]
Can you post a picture of the bios screen when the laptop boots up and one from when you have gone into the actual bios just after bootup where it shows the bios type and current image.
[/COLOR]
Please see the four attached photographs.
[COLOR="Red"]

Do you have a spare hard drive you can put in the laptop or can you resize your existing partitions and create a new partition? 
[/COLOR]
Does the spare hard drive have to fit inside the laptop? Does the spare hard drive have to be an internal hard drive?
Yes, I can resize the existing partitions, but isn't it better to adjust partitions from a LiveUSB or LiveCD?

[COLOR="Red"]
DO you have access to another computer (desktop)? I'm asking this as there might be another viable option.
[/COLOR]
Yes, I think I can borrow another computer.

---

### Post by mips on 2012-07-10
From the Toshiba link I provided above,
> 
Package:	WinRAR 32-bit self-extracting ZIP file includes both Windows-based and **diskette based BIOS update installation** options. See the included documentation for details.

We wanna try and use the dos based utility.


> **hanzj said:**
> [COLOR="blue"]Mips words in red. [/COLOR]

[COLOR="Red"]Have you tried booting from the optical drive yet (even with a livecd)?

[/COLOR]
Not yet. Will try to do so this week.

Well try this first before we do anything else. If you can boot from the optical drive then we need to make you a bootable FreeDOS cd with the DOS utility and BIOS on it. This way you can try and boot from the CD and flash via the DOS utility.



> **hanzj said:**
> 
[COLOR="Red"]
Can you post a picture of the bios screen when the laptop boots up and one from when you have gone into the actual bios just after bootup where it shows the bios type and current image.
[/COLOR]
Please see the four attached photographs.
[COLOR="Red"]

Ok, so your laptop uses InsydeH2O UEFI BIOS. I've no experience with this manufacturer so I'm not sure if the DOS base utility will allow you to roll back to a older version but it's worth a shot.


> **hanzj said:**
> 
Do you have a spare hard drive you can put in the laptop or can you resize your existing partitions and create a new partition? 
[/COLOR]
Does the spare hard drive have to fit inside the laptop? Does the spare hard drive have to be an internal hard drive?
Yes, I can resize the existing partitions, but isn't it better to adjust partitions from a LiveUSB or LiveCD?

Yes it has to be internal. Thinking of installing FreeDOS from another PC onto the drive and then plugging it into the laptop to boot off so you can run the util. Another option would be to repartition your existing drive with about 20MB of free space, install FreeDOS assuming you can boot of optical media, update GRUB and then boot Freedos to run the utility.


> **hanzj said:**
> 
[COLOR="Red"]
DO you have access to another computer (desktop)? I'm asking this as there might be another viable option.
[/COLOR]
Yes, I think I can borrow another computer.

Relates to the above post in case you can't boot off the optical media.

Do you not have a option in the BIOS itself (Advanced menu maybe?) to load a new bios/firmware version. There usually is such an option but like I said I'm not familiar with InsydeH2O UEFI BIOS.

---

### Post by mips on 2012-07-10
Also have you tried to enable or disable USB Legacy Emulation?

Click Start, All Programs, TOSHIBA, Utilities, and then HWSetup, or click the TOSHIBA Hardware Settings icon in the Optimize tab of TOSHIBA Assist.

---

