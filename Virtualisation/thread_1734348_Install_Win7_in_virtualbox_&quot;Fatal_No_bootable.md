---
title: "Install Win7 in virtualbox &quot;Fatal: No bootable medium found! system halted&quot;"
date: 2011-04-20
forum: Virtualisation
---

### Post by brangkas on 2011-04-20
I am using Ubuntu 10.10 and want to install Windows 7 inside with virtualbox.

everything ran smoothly till when i started the machine, it says "Fatal: No bootable medium found! system halted"

am using CD/DVD drive windows 7 installation drive,
i have ticked the host I/O cache in storage settings
i've ticked the passthrough of IDE controller and directed to host drive optriact (my cd rom)

i am hoping some help, and greet to all Linuxer

i appreciate your help
thanks..

---

### Post by An Sanct on 2011-04-20
Did you set up the boot order to see/use the CD?

It is located under the machine settings (right click on the VM in the list, while it is not working and select "settings"), on the left, select "System", there you have the list of drives.

Alternatively, you can press F12 while booting and select CD from there, this is a one time setting, good enough for the installation.

---

### Post by brangkas on 2011-05-05
I did that... it's not working...
please any other possible mistake i did on the settings??
i got stressfull in here...

---

### Post by tkelito on 2011-05-05
If you have gotten to the point of "No Bootable Medium Found" it is not an issue with the Virtual Machine but an issue with your settings to boot off the CD-Rom.  I would double check everything.

Make sure under system the boot order is set correctly.  Also make sure under Storage Host Drive you click the drop down and choose your CD-Rom.  I do not enable pass through to use a disc in the drive.

---

### Post by brangkas on 2011-05-05
man, i was exited when u said u didn't enable passthrough when use cd-rom becoz i did..
so i disabled and run it again, new fatal error occur...

this time it's

"Fatal Error: Could not read from the boot medium! system halted"

man u make me alive, there is hope in here...
looking forward for ur double check man...
thank you so much..

---

### Post by CharlesA on 2011-05-05
Are you able to see the dvd in the host OS?

---

### Post by An Sanct on 2011-05-05
Okay :) I saw you personal message and am answering to the thread ... so everyone can benefit.

On the first picture (*vm1.png*), you can see VirtualBox 4.0.6 r71344 (the most current right now)
Labels:
A - Architecture, 64bit (if needed ...)
B - **Disk boot order**, this is important, since as I can see, you have booting problems.

On the second picture (*vm2.png*), you can see settings of a specific Virtual Machine. You can get there, if you right click on the list as seen on the first picture and select "settings" in the menu.

The area, that is marked with red, is the "boot order", make sure, that the disk is first.

---

### Post by brangkas on 2011-05-05
> **An Sanct said:**
> Okay :) I saw you personal message and am answering to the thread ... so everyone can benefit.

On the first picture (*vm1.png*), you can see VirtualBox 4.0.6 r71344 (the most current right now)
Labels:
A - Architecture, 64bit (if needed ...)
B - **Disk boot order**, this is important, since as I can see, you have booting problems.

On the second picture (*vm2.png*), you can see settings of a specific Virtual Machine. You can get there, if you right click on the list as seen on the first picture and select "settings" in the menu.

The area, that is marked with red, is the "boot order", make sure, that the disk is first.

oh thank you for that, I appreciate that..
it seems u suggest me to install from hard disk instead of DVD-rom,
but I Tried though, I've followed your instruction but still 
"fatal Error: No bootable medium found! system Halted"
take a look at the screenshot:

---

### Post by brangkas on 2011-05-05
> **CharlesA said:**
> Are you able to see the dvd in the host OS?

Sorry, I'm not sure about what u're saying.
if u meant that the DVD is actually workin, yest it is..
i've use it to install windows 7 to another laptop, 
and i can read it from my ubuntu 10.10 ( host)..

---

### Post by CharlesA on 2011-05-05
Hit F12 when you first see the VirtualBox screen, then select "cd rom"

---

### Post by brangkas on 2011-05-05
> **CharlesA said:**
> Hit F12 when you first see the VirtualBox screen, then select "cd rom"

i've done it boss...
still got the same error....

any other possibilities??

---

### Post by CharlesA on 2011-05-05
Did you create the ISO from the dvd by dragging and dropping the files? Could be that it's not bootable.

---

### Post by wildmanne39 on 2011-05-06
I problem I ran into installing windows was that I was trying to use a disc that came with my system, and the company that made my system made it so I could not use the windows disc, except for reinstalling on my system and I got the same error.

---

### Post by An Sanct on 2011-05-06
The windows 7 ISO you have has to be bootable.

If you select your Ubuntu ISO, can it boot if you press F12 on startup?

PS. I attached the "F12 boot menu", just to make sure, we are looking at the same thing...

---

### Post by An Sanct on 2011-05-06
I noticed a warning in post #8 in your screenshot (in red, on the bottom)! 
Make sure to follow it, because the host operating system has to run normally for the guest to run normally!

---

### Post by YesWeCan on 2011-05-06
Yes, it may be your w7.iso file is duff. Also, you may want to tick the CD in the boot order section of System. Also, when you have started the VM check in the Devices menu CD submenu that the w7.iso is ticked.

---

### Post by An Sanct on 2011-05-06
The first screenshot in reply [#8]("http://ubuntuforums.org/showpost.php?p=10775416&postcount=8") shows, that the CD/DVD is "inserted" ... so my guess is, that the ISO is not bootable ...

---

### Post by brangkas on 2011-05-09
Guys... you are right, it was the DVD which not workin.. am sorry i didn't check it becoz it was ridiculous that was since i used it to install 2 laptops before, but apparently that's the ridiculous problem..

Thank you so much guys for the help I really appreciate that...

---

### Post by An Sanct on 2011-05-09
No problem :)

Please mark the thread as solved (under "thread tools" in the forum menu)

---

### Post by Cyrilalto on 2012-05-10
Hello every one... I'm afraid the theme is not solved... I got some  very similar problem... I would be very happy if someone kind person could help me...

I installed Ubuntu server 12.04 to my old computer Celeron 1800 and 384 Ram.. It's not much but I don't need more because server is just for torrents and file sharing. anyway I wanted to set a virtualbox to server with phpVirtualBox... I did it but when I'm trying to install windows2000 inside virtualbox I see the error named "FATAL: No bootable medium found! System halted."

I checked for hundred times all bootable options, I checked with different ISO, even with the same iso of installed ubuntu 12.04.

HELP ME PLEAAAAASSSEEEE!!!!!

---

### Post by CharlesA on 2012-05-10
> **Cyrilalto said:**
> Hello every one... I'm afraid the theme is not solved... I got some  very similar problem... I would be very happy if someone kind person could help me...

I installed Ubuntu server 12.04 to my old computer Celeron 1800 and 384 Ram.. It's not much but I don't need more because server is just for torrents and file sharing. anyway I wanted to set a virtualbox to server with phpVirtualBox... I did it but when I'm trying to install windows2000 inside virtualbox I see the error named "FATAL: No bootable medium found! System halted."

I checked for hundred times all bootable options, I checked with different ISO, even with the same iso of installed ubuntu 12.04.

HELP ME PLEAAAAASSSEEEE!!!!!
Make sure the VM is booting off the cd. Start it up, hit F12 and select cd.

Sidenote: Running VMs on a box with 384MB of RAM is probably not going to work out very well.

---

### Post by Cyrilalto on 2012-05-10
> **CharlesA said:**
> Make sure the VM is booting off the cd. Start it up, hit F12 and select cd.

Sidenote: Running VMs on a box with 384MB of RAM is probably not going to work out very well.


Well... for some reason my server crashed down... I'm new with linux server, and I like to experimenting...  after reinstalling ubuntu server, virtual box works properly... so.. I don't know what was a reason and seems I will don't know...

thanks a lot for the answer!

Sidenote: I know that 384mb is not much... but server use nearly 210 mb, then 128 for win2k should be ok. I can use team viewer with windows 2000. and by it get the access from the Internet to my network. I do not know how I could connect to the server from the internet without this strange way. The problem is I can't use VPN or SSH, because I've no static IP. Do you know some similar service like team viewer but for linux?

---

### Post by CharlesA on 2012-05-10
Set up bridged networking instead of NAT.

Altho I suggest not allowing Windows 2000 access to the internet at all, it hasn't received security updates in a few years.

---

### Post by ChrisInNevada on 2013-02-09
I'm having the same issue here.  Tried the F12 boot and already had CD #1 in boot order.

---

