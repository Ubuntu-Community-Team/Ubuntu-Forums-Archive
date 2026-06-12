---
title: "Was going to start testing last night. Was a Disaster!"
date: 2012-08-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by irv on 2012-08-09
When 12.04 came out in Alpha 1 in Dec 2011 I started from ground zero. But with 12.10 I waited until Alpha 3. I did a fresh install of 12.04 not even a month ago so I thought I would just do the upgrade. I made sure I had all packages up-to-date and did the upgrade. First boot up after upgrade it would not boot properly. Graphics were messed up. I could go into recovery mode and boot into 2D but 3D would not work.
It was late at night (early morning) and I tried everything I could think of to get it to work, I finely gave up and did another fresh install of 12.04. I am not sure I am going to move up to 12.10, because I am really please with 12.04 LTS, and seeing it is going to be supported for 5 years I think I am going to stick with it.

I enjoy testing, but I need to have something that will at lease works to test it. I am not sure what went wrong. You can see what hardware I was using for testing if you look at my signature.

---

### Post by philinux on 2012-08-09
I would have gone for a clean install of alpha 3 or the daily build.

---

### Post by ventrical on 2012-08-09
> **philinux said:**
> I would have gone for a clean install of alpha 3 or the daily build.

 Oddly enough, alpha 3 and the dailys are working exceptionally well. Just zsynced the alternate yesterday and that is working exceptionally well also.

---

### Post by irv on 2012-08-09
Was wondering how much has 12.10 improved over 12.04. If it is worth it, I will download the 12.10 tonight when I get home and retry with a fresh install. I never did like doing upgrades. I can do a clean install pull all my data back and reload my apps faster then doing a upgrade from an older version.

I keep most of my data online in the cloud and use gmail. This makes it easier to do a fresh install.

---

### Post by ventrical on 2012-08-09
> **irv said:**
> Was wondering how much has 12.10 improved over 12.04. If it is worth it, I will download the 12.10 tonight when I get home and retry with a fresh install. I never did like doing upgrades. I can do a clean install pull all my data back and reload my apps faster then doing a upgrade from an older version.

I keep most of my data online in the cloud and use gmail. This makes it easier to do a fresh install.


The alternate is currently working really well here . They have a lot of video graphics problem ironed out and the initial install is back to snappy Unity 3D!

 I can vouch  for alpha 3 being as fine piece of work. I just udated(zsynced) that (quantaldesktop-i386.iso) today  and will give it a whirl in a little bit.

---

### Post by irv on 2012-08-09
By the way I should have said, I am using the 64bit version.

---

### Post by philinux on 2012-08-09
> **irv said:**
> Was wondering how much has 12.10 improved over 12.04. If it is worth.


See the changes and updates stIcky. Happy reading.

---

### Post by ventrical on 2012-08-09
> **irv said:**
> By the way I should have said, I am using the 64bit version.


Alpha 2 64bit alternate worked well.

  I am going to update  my daily (alternate) on that.

---

### Post by irv on 2012-08-09
I got the iso downloaded and am doing the USB drive with Unetbootin as I post this. I may hold off gotta watch some football right now. [Packers and Chargers]("http://espn.go.com/blog/afcwest/post/_/id/46417/three-things-packers-at-chargers")

---

### Post by VinDSL on 2012-08-09
> **irv said:**
> I may hold off gotta watch some football right now. [Packers and Chargers]("http://espn.go.com/blog/afcwest/post/_/id/46417/three-things-packers-at-chargers")
I'm gonna watch the Midgets and Giants.

Oh, wait, that's pro wrestling, sorry...  :D

---

### Post by irv on 2012-08-09
While I was watching the football game I thought I would just boot into the Live USB. It doesn't look like I will be installing it. Here is what my screen looks like. 
[ATTACH]222490[/ATTACH]
This is why I said it was a Disaster! There is no way I can do any testing. This was the Alpha 3 iso. And this was a good download, and it doesn't look any different then the upgrade did.

---

### Post by effenberg0x0 on 2012-08-09
> **VinDSL said:**
> I'm gonna watch the Midgets and Giants.

Oh, wait, that's pro wrestling, sorry...  :D

Oh, I immediately thought about rolling a D100 or something :P

Regards,
Effenberg

---

### Post by irv on 2012-08-09
OK I thought I would try the 32 bit Alpha 3, but it does the same thing.
[ATTACH]222493[/ATTACH]
With any of the releases in the past I never had any video issues, but this release there were some changes made to the video to cause this to happen. Maybe I will be waiting until the Beta release and try again.

---

### Post by alphacrucis2 on 2012-08-10
> **irv said:**
> OK I thought I would try the 32 bit Alpha 3, but it does the same thing.
[ATTACH]222493[/ATTACH]
With any of the releases in the past I never had any video issues, but this release there were some changes made to the video to cause this to happen. Maybe I will be waiting until the Beta release and try again.

Were you running a proprietary video driver?

---

### Post by VinDSL on 2012-08-10
> **irv said:**
> Maybe I will be waiting until the Beta release and try again.
At least, it's booting for you.  :)

I haven't been able to log into a 3D session (Unity, GS) nor use Firefox/TB for several weeks.

Stuff like this usually gets sorted by Beta 1.  We'll see...

---

### Post by irv on 2012-08-10
> **alphacrucis2 said:**
> Were you running a proprietary video driver?

No, In all the other releases I never had to do a thing with video driver. I do have a process I need to do to get my wifi going but never had video issues. That is why I say that there were changes made to the video support for my dell Inspiron 1521.
What command do I need to run to see what chip set I am running on the on board video card?

---

### Post by dino99 on 2012-08-10
> **irv said:**
> No, In all the other releases I never had to do a thing with video driver. I do have a process I need to do to get my wifi going but never had video issues. That is why I say that there were changes made to the video support for my dell Inspiron 1521.
What command do I need to run to see what chip set I am running on the on board video card?

lshw might help

and downgrade xserver-xorg-core (ant the likes) to the precise version
[https://launchpad.net/ubuntu/+source/xorg-server/](https://launchpad.net/ubuntu/+source/xorg-server/)

but take care of the removed packages, to reinstall them before rebooting (xorg/ubuntu-desktop)

---

### Post by irv on 2012-08-10
> **dino99 said:**
> lshw might help

and downgrade xserver-xorg-core (ant the likes) to the precise version
[https://launchpad.net/ubuntu/+source/xorg-server/](https://launchpad.net/ubuntu/+source/xorg-server/)

but take care of the removed packages, to reinstall them before rebooting (xorg/ubuntu-desktop)

My Video card information from lshw:
> *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:42 memory:e0000000-efffffff memory:fe9f0000-fe9fffff ioport:ee00(size=256) memory:fea00000-feafffff


---

### Post by timmillwood on 2012-08-10
I had an issue with just a black screen after upgrading, I had to remove the closed source ATI drivers and use the open source ones instead, after that all has been fine.

---

### Post by madjr on 2012-08-10
> **irv said:**
> My Video card information from lshw:

> *-display
description: VGA compatible controller
product: RS690M [Radeon X1200 Series]
vendor: Hynix Semiconductor (Hyundai Electronics)
physical id: 5
bus info: pci@0000:01:05.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=64
resources: irq:42 memory:e0000000-efffffff memory:fe9f0000-fe9fffff ioport:ee00(size=256) memory:fea00000-feafffff

I had that problem with older versions when testing on an older laptop with that same video card, that is a graphical bug so please report it now that is early in the cycle.

Type and follow instructions 
```
ubuntu-bug
```

to report other bugs follow this:
[https://help.ubuntu.com/community/ReportingBugs/](https://help.ubuntu.com/community/ReportingBugs/)

---

### Post by ventrical on 2012-08-10
My 64bit Acer Extensa 4420 with ATI Radeon works just excellent with Unity 3D. I just updated a while ago. The 3.5.0-9 kernel is just singing and it runs cool as a cucumber.

 Now, off to update my own Dell Inspiron laptop:)

---

### Post by irv on 2012-08-10
> **madjr said:**
> I had that problem with older versions when testing on an older laptop with that same video card, that is a graphical bug so please report it now that is early in the cycle.

Type and follow instructions 
```
ubuntu-bug
```

to report other bugs follow this:
[https://help.ubuntu.com/community/ReportingBugs/](https://help.ubuntu.com/community/ReportingBugs/)

OK I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437").

---

### Post by irv on 2012-08-10
> **ventrical said:**
> My 64bit Acer Extensa 4420 with ATI Radeon works just excellent with Unity 3D. I just updated a while ago. The 3.5.0-9 kernel is just singing and it runs cool as a cucumber.

 Now, off to update my own Dell Inspiron laptop:)

Post here how the update goes on your Dell. Are you going to do the Alpha 3 update?

---

### Post by ventrical on 2012-08-10
> **irv said:**
> Post here how the update goes on your Dell. Are you going to do the Alpha 3 update?

Yes.. that is a (quantal) install back from Alpha1 to be updated. Had no problems so far with that install either. The Quantal ISOs have worked exceptionally well on my Dell Inspiron B130. In fact, all Ubuntu flavors and versions seem to be made for Dell's.

 Umm.. back to topic .. I was just wondering if you were to try the  quantal-alternate.amd64.iso - to see if that would work.

  There were a lot of video graphis problems with A1 and A2 but the trick was to wait for Ubiquity to come up and it would finish the install even with all the fuzzy background graphics.  Alpha 3  completely eliminated those graphics problems, especially  with the quantal-desktop-i386.iso distro.

  Back during Preicise testing I had big problems having my ATi card being detected in 64bit mode , but everything worked in 32bit mode. I am just wondering if your laptop would work with 32bit??

 I will get back with Dell update. It is currently updating an early install of Precise... then i will switch hdds to one which has the quantal install on it and update .. but , as I said, no probs with installs from USB on the Dell.

---

### Post by ventrical on 2012-08-10
Running this from live quantal-desktop-i386.iso daily burned yesterday.

it initially had a broken screen but Ubiquity showed and I chose 'Try Ubuntu'. On yesterdays daily there seem to be a regression at startup screen, but all is well otherwise.

But, naturally this is a Dell with Intel chipset.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ubuntu@ubuntu:~$ 

```

---

### Post by ventrical on 2012-08-10
Began a fresh install (on Dell) of yesterdays daily and got a partitoner bug :(

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1034954](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1034954)

---

### Post by ventrical on 2012-08-10
Zsynced the (quantal-desktop)daily and will try that now on the Dell.

---

### Post by irv on 2012-08-10
> **ventrical said:**
> Yes.. that is a (quantal) install back from Alpha1 to be updated. Had no problems so far with that install either. The Quantal ISOs have worked exceptionally well on my Dell Inspiron B130. In fact, all Ubuntu flavors and versions seem to be made for Dell's.

 Umm.. back to topic .. I was just wondering if you were to try the  quantal-alternate.amd64.iso - to see if that would work.

  There were a lot of video graphis problems with A1 and A2 but the trick was to wait for Ubiquity to come up and it would finish the install even with all the fuzzy background graphics.  Alpha 3  completely eliminated those graphics problems, especially  with the quantal-desktop-i386.iso distro.

  Back during Preicise testing I had big problems having my ATi card being detected in 64bit mode , but everything worked in 32bit mode. I am just wondering if your laptop would work with 32bit??

 I will get back with Dell update. It is currently updating an early install of Precise... then i will switch hdds to one which has the quantal install on it and update .. but , as I said, no probs with installs from USB on the Dell.

I tried the 64 and 32 bit versions, also tried an upgrade from 12.04. All with the A3 and all had the same results.
Back in Dec 2011 I started with 10.04 A1 and worked into the final release with no issues at all. Now for the past month or so I been having problems with 12.04 locking up. So far I have done two complete fresh installs and it still continues to lockup. But that is another issue I am working on. As soon as the Beta comes out I will try it. Meanwhile I have a bug report filed.

---

### Post by madjr on 2012-08-10
> **irv said:**
> OK I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437").

Hi Irv,

Not sure if you filed it correctly.

your bug report says Precise 12.04, has the old kernel and I don't see any of the automatic data from your graphics driver and apport.


did you file it from precise ?

try doing the "ubuntu-bug" command again but from the quantal usb if you don't have it installed.

---

### Post by ventrical on 2012-08-10
btw .. I just did an install from yesterdays daily quantal-alternate-i386 on my Dell Inspiron B130 and it went just fine.

---

### Post by irv on 2012-08-11
> **madjr said:**
> Hi Irv,

Not sure if you filed it correctly.

your bug report says Precise 12.04, has the old kernel and I don't see any of the automatic data from your graphics driver and apport.


did you file it from precise ?

try doing the "ubuntu-bug" command again but from the quantal usb if you don't have it installed.
Yes I tried from precise.
That's the problem I can't even run the OS from the USB, it comes up with this graphics so I can't even move around with in it.
Maybe I will try Ctrl/Alt F1 and get to a prompt and then try to file the bug report if that works.

---

### Post by irv on 2012-08-11
> **irv said:**
> Yes I tried from precise.
That's the problem I can't even run the OS from the USB, it comes up with this graphics so I can't even move around with in it.
Maybe I will try Ctrl/Alt F1 and get to a prompt and then try to file the bug report if that works.

OK. I tried to file the bug report from the prompt. The first time it didn't work because I did not have a network connection. So I got on the wire, made a connection and tried again. It worked up to the point where it wanted me to open a browser so I believe it did not get filed. I am not sure how I am going to file this bug report until I can at least get on.
I have one other option. I will need to install a different hard drive in my laptop (which I have) load up the OS and boot into the 2D and then file the bug report.
Just for the record I have been using Ubuntu since 2005 and have never had a graphic problem before. If we are working with a new kernel in this release, I am wondering if this might be the problem?

---

### Post by irv on 2012-08-11
OK I installed the other Hard Drive booted from the USB and checked for errors. There were none so I started the install, Even the install screen was corrupt. I did a short .mov file and put it on my server. See the link below.
This was the 32bit install. I did get the 64 bit install to at least install. I will see if I can get that to work so I can install it.
[Here is the MOV file.]("http://wabasha-server.net/Screen_Shots/Ubuntu%2012.10%20install%20screen.MOV")

---

### Post by ventrical on 2012-08-11
> **irv said:**
> OK I installed the other Hard Drive booted from the USB and checked for errors. There were none so I started the install, Even the install screen was corrupt. I did a short .mov file and put it on my server. See the link below.
This was the 32bit install. I did get the 64 bit install to at least install. I will see if I can get that to work so I can install it.
[Here is the MOV file.]("http://wabasha-server.net/Screen_Shots/Ubuntu%2012.10%20install%20screen.MOV")


Can't get that to play.

---

### Post by madjr on 2012-08-11
> **irv said:**
> OK. I tried to file the bug report from the prompt. The first time it didn't work because I did not have a network connection. So I got on the wire, made a connection and tried again. It worked up to the point where it wanted me to open a browser so I believe it did not get filed. I am not sure how I am going to file this bug report until I can at least get on.
I have one other option. I will need to install a different hard drive in my laptop (which I have) load up the OS and boot into the 2D and then file the bug report.
Just for the record I have been using Ubuntu since 2005 and have never had a graphic problem before. If we are working with a new kernel in this release, I am wondering if this might be the problem?

ok, I see.

If it's unity 3d that has the issue (or 3d in general), than you can try a spin with a non-3d desktop like xubuntu or lubuntu 12.10 alpha3 to default to a desktop you can use, then install unity on it.

just look for the package (recommended in the synaptic package manager):

"Ubuntu-desktop" (should install the full ubuntu desktop for you) or just install "unity" 3d/2d.

---

### Post by irv on 2012-08-11
> **ventrical said:**
> Can't get that to play.

It plays just fine on my laptop. All it is is a .MOV file.
At this very moment I am making another USB with the 64bit version. I know I can get that one to install and will install it on the other HD. I will try running it in 2D and then re-file the bug report. One way or the other I am going to get this to work.
I think it called persistence.
EDIT: try right clicking on the file and and save as.
[http://wabasha-server.net/Screen_Shots/]("http://wabasha-server.net/Screen_Shots/")
It is the Ubuntu 12.10 file.

---

### Post by madjr on 2012-08-11
> **ventrical said:**
> Can't get that to play.

save link as ?

> I think it called persistence.

rock on !

---

### Post by ventrical on 2012-08-11
> **irv said:**
> It plays just fine on my laptop. All it is is a .MOV file.
At this very moment I am making another USB with the 64bit version. I know I can get that one to install and will install it on the other HD. I will try running it in 2D and then re-file the bug report. One way or the other I am going to get this to work.
I think it called persistence.
EDIT: try right clicking on the file and and save as.
[http://wabasha-server.net/Screen_Shots/](http://wabasha-server.net/Screen_Shots/)
It is the Ubuntu 12.10 file.

Irv,

 The various quantal  dailies work just great here. I used yesterday's daily desktop 32bit , alternate and amd64-alternate and they are working just great on several different machines. Sometimes I have to use <nomodeset> right at the beggining of the boot on certain graphics adapters.

Other than this I can't see why you can't get your screen to work.

To get to the option where you can use <nomodeset> just keep hitting F1 when you are booting from USB. Then F6 - <nomodeset>

---

### Post by ventrical on 2012-08-11
> **madjr said:**
> save link as ?



rock on !

thanks..

---

### Post by irv on 2012-08-11
I am just spinning my tires. So far I have tried to install Ubuntu 32 and 64 bit versions and Xubuntu 64, and I am getting the same results with them all. here are some screen
[ATTACH]222560[/ATTACH]  [ATTACH]222561[/ATTACH]  [ATTACH]222562[/ATTACH]  [ATTACH]222563[/ATTACH]
These were all from the installs. The other I posted earlier were of the live OS. This is the first release where I can't even get the install to work on any of *ubuntu's. Did the installer get changed that it is not working with my graphics?

It is going to be impossible for me to issue a bug report if I can't get past the installer or get it to book with the live OS.

[COLOR="Red"]**EDIT:**[/COLOR] I am going to try the Alpha 2 release and create a USB. Also I am going to try burning a DVD with Alpha 3 to make sure it is not something while I am creating the USB with Unetbootin.

---

### Post by ventrical on 2012-08-11
I don't know Irv.. I'm doing yet another install with live daily from yesterday.

Here it is in action.


[http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be](http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be)

Did you try <nomodeset>?

---

### Post by irv on 2012-08-11
> **ventrical said:**
> I don't know Irv.. I'm doing yet anothe install with live daily from yesterday.

Here is in in action.


[http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be](http://www.youtube.com/watch?v=7OtY9y2F_XI&feature=youtu.be)

Did you try <nomodeset>?
Mine does not look like this. I'm about 40% done with the A2 USB and I have the DVD burned with the A3. When the USB is complete I will try both and see what happens. I have downloaded 3 different iso files and check them all for errors and they all come up error free. Will keep you posted.

---

### Post by irv on 2012-08-11
OK, tried the A2 on the USB with same results. Tried the DVD with A3 same results.
Not the only way I will be able to get Ubuntu installed will be to first install 12.04 on spare HD do the updates and then install 12.10. I should be able to get it to boot in 2D so I can run a bug report. I have never had to jump throw this many hoops before to get an OS to install. Now this next one will take me the rest of the day. I was wondering what I was going to do with my day, and now I know.
Will be back later.

---

### Post by ventrical on 2012-08-11
> **irv said:**
> OK, tried the A2 on the USB with same results. Tried the DVD with A3 same results.
Not the only way I will be able to get Ubuntu installed will be to first install 12.04 on spare HD do the updates and then install 12.10. I should be able to get it to boot in 2D so I can run a bug report. I have never had to jump throw this many hoops before to get an OS to install. Now this next one will take me the rest of the day. I was wondering what I was going to do with my day, and now I know.
Will be back later.


 Well .. your work is not wasted because I did find a Ubiquity bug with the daily-live desktop i386 .. so on some machines .. it will take you half way and then crash. Although it is not related to your bug it is basically a watse of time atm to try and isntall the daily-desktop-i386 on  my Dell opti , <nomodeset> or not.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1035698)

---

### Post by madjr on 2012-08-11
> **irv said:**
> I am just spinning my tires. So far I have tried to install Ubuntu 32 and 64 bit versions and Xubuntu 64, and I am getting the same results with them all. here are some screen
[ATTACH]222560[/ATTACH]  [ATTACH]222561[/ATTACH]  [ATTACH]222562[/ATTACH]  [ATTACH]222563[/ATTACH]
These were all from the installs. The other I posted earlier were of the live OS. This is the first release where I can't even get the install to work on any of *ubuntu's. Did the installer get changed that it is not working with my graphics?

It is going to be impossible for me to issue a bug report if I can't get past the installer or get it to book with the live OS.

[COLOR="Red"]**EDIT:**[/COLOR] I am going to try the Alpha 2 release and create a USB. Also I am going to try burning a DVD with Alpha 3 to make sure it is not something while I am creating the USB with Unetbootin.

Hi Irv,

I updated your bug report so is easier for the quantal devs to see and not confuse it with a 12.04 bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437)

you can go ahead and add more screenies.

Then once you are able to report from quantal (with all the extra info from apport), we can just mark the old bug as duplicate.

cheers and thanks for taking the time to help test. :guitar:

---

### Post by irv on 2012-08-11
> **madjr said:**
> Hi Irv,

I updated your bug report so is easier for the quantal devs to see and not confuse it with a 12.04 bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035437)

you can go ahead and add more screenies.

Then once you are able to report from quantal (with all the extra info from apport), we can just mark the old bug as duplicate.

cheers and thanks for taking the time to help test. :guitar:

I am at the point where I have 12.04 installed on spare HD did all the updates and ran update-manager -d with everything set to do the upgrade. It is in the process of do the upgrading to version 12.10. This is the slow way to do it, (much easier to do a fresh install) but when it is done I should be able to boot, if not in 3D but 2D so I can re-issue the bug report with 12.10. Thanks for all your help on this also. I guess the only way to get to the bottom of this problem is to get this bug report filed.

---

### Post by GreatDanton on 2012-08-11
irv +1 for your patience. You moved from fully functional system to buggy one :).

---

### Post by madjr on 2012-08-11
> **irv said:**
> I am at the point where I have 12.04 installed on spare HD did all the updates and ran update-manager -d with everything set to do the upgrade. It is in the process of do the upgrading to version 12.10. This is the slow way to do it, (much easier to do a fresh install) but when it is done I should be able to boot, if not in 3D but 2D so I can re-issue the bug report with 12.10. Thanks for all your help on this also. I guess the only way to get to the bottom of this problem is to get this bug report filed.

Yes, but don't worry take your time, there's still plenty till the betas and final release, and am sure is probably something relatively minor that needs fixing once they look into it. :P

---

### Post by irv on 2012-08-11
> **GreatDanton said:**
> irv +1 for your patience. You moved from fully functional system to buggy one :).

It's a good thing I have a couple of extra HD laying around for testing. I find it an easy way to do this. (remove a few screws swap out drive load OS). When I am done testing I can switch back to my fully operating system an am back running in only a few minutes.

---

### Post by irv on 2012-08-11
OK, finally got the bug report filed. Could not run 12.10 in 3D. Screen was corrupt so got it to run in 2D and filed the bug report @
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035737]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1035737")

Everyone, thanks for your help.

EDIT: Two snap shots of 3D screen in 12.10
[ATTACH]222574[/ATTACH]  [ATTACH]222575[/ATTACH]
Sorry about the reflection. The Sun Light was at my back coming in the window. Not MS windows! My house has windows but my computers don't.

---

### Post by madjr on 2012-08-15
maybe this is part of the problem:

[http://ubuntuforums.org/showthread.php?t=2042780](http://ubuntuforums.org/showthread.php?t=2042780)

---

### Post by irv on 2012-08-15
> **madjr said:**
> maybe this is part of the problem:

[http://ubuntuforums.org/showthread.php?t=2042780](http://ubuntuforums.org/showthread.php?t=2042780)

madjr, thanks for the heads up. I don't think this was my problem because 12.04 that I am running right now works with 3D, I have never used 2D before but was force to boot to it to file bug report, which I did. Very interesting though.
Yesterday I installed Black Opal which is based on Ubuntu 12.04 with OZ Unity Remixes. It is very nice distro but it is heavy on special effects. I had to shut down some of them so I could get my laptop running faster. I need to wait until this bug is fixed before I can go to 12.10. If I can't get the live DVD/USB to work I can't install.

---

### Post by madjr on 2012-08-15
> **irv said:**
> madjr, thanks for the heads up. I don't think this was my problem because 12.04 that I am running right now works with 3D, I have never used 2D before but was force to boot to it to file bug report, which I did. Very interesting though.
Yesterday I installed Black Opal which is based on Ubuntu 12.04 with OZ Unity Remixes. It is very nice distro but it is heavy on special effects. I had to shut down some of them so I could get my laptop running faster. I need to wait until this bug is fixed before I can go to 12.10. If I can't get the live DVD/USB to work I can't install.

Irv, have you tested today's unity updates ?

see if there is any change or improvements.

---

### Post by irv on 2012-08-15
> **madjr said:**
> Irv, have you tested today's unity updates ?

see if there is any change or improvements.

No I haven't but I can do a download and give it a try. I will post back later when I do.
EDIT: Not fixed. It is still corrupt. It is doing the same thing. I did a small video and downloaded it to my server but it doesn't play right, but take my word it is not fixed.

---

