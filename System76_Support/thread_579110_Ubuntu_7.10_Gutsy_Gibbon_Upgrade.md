---
title: "Ubuntu 7.10 Gutsy Gibbon Upgrade"
date: 2007-10-18
forum: System76 Support
---

### Post by crichell on 2007-10-18
Hello Everyone - The Gibbon is in the wild (or very close to breaking out).  For this release a wonderful Gibbon dons our homepage:

[www.system76.com](www.system76.com)

Tonight we released the new System76 Driver 2.1.0 with full Gutsy support and we created an upgrade How To.

Upgrading Your System76 Computer - [http://knowledge76.com/index.php/GutsyUpgrade](http://knowledge76.com/index.php/GutsyUpgrade)

Feel free to contact us if you have any trouble upgrading.  Testing was very positive overall.  Nonetheless make sure to let us know if you experience any regressions.  We'll patch them up quickly.

Cheers,

Carl Richell
System76

--------------------------

Change Log for System76 Driver 2.1.0

Version 2.1.0

   1. Complete Ubuntu 7.10 Gutsy support for all computers
   2. Add support tab and create log archive
   3. Add new gutsy release models and support 
   4. Add new Gazelle Value (gazv5) model
   5. Add uvc camera driver for new Gazelle Value (gazv5)
   6. Fix some file permissions problems (menu icon)
   7. Add SD card reader support for Pangolin (panv3) and Gazelle (gazv5)

---

### Post by Rowan187 on 2007-10-18
Very very nice. I'm upgrading my System76 driver now! I'm excited :D Good work!

---

### Post by Rowan187 on 2007-10-18
Alrighty all upgraded and everything seems to be running fine except... sound doesn't seem to work. It can't find any "Default Mixer Track" and when trying to change volume it says 
No volume control GStreamer plugins and/or devices found.

panv2 by the way. Help :S

---

### Post by tedrampart on 2007-10-18
booted up fine on my gazp3, camera works, sound works, network (wired tested so far) works, bluetooth works, wireless picks up a signal, but I'm atwork, and can't connect to it..

didn't seem to break anything, though when I restarted after installing the driver, it hung after the status bar had finished..it hadn't done that before the driver installation.. but it was also after a suspend (which hardly worked anyhow..)

I don't have a card to test the card reader but it worked natively in gutsy anyhow, so I doubt it'll be broken.  I'm about to burn a dvd, so if there's an issue, I'll post that.. and when I get home and restore after hibernating I'll see if that works again too..

I was expecting this on friday.. glad to see it sooner than later.. great job guys!

---

### Post by steveneddy on 2007-10-18
I upgraded last night. Bluetooth finally works great.

:popcorn:

---

### Post by thomasaaron on 2007-10-18
Rowan187.

Run the restore function on your System 76 driver and reboot your machine.
If that doesn't work, did you download the newest driver?

---

### Post by crichell on 2007-10-18
> **Rowan187 said:**
> Alrighty all upgraded and everything seems to be running fine except... sound doesn't seem to work. It can't find any "Default Mixer Track" and when trying to change volume it says 
No volume control GStreamer plugins and/or devices found.

panv2 by the way. Help :S

Hi Rowan,  Did you run the System76 Driver?  It should restore sound.  If not please post the output of:

```
cat /proc/asound/version
```

---

### Post by pak33m on 2007-10-18
Hey guys,

Thank you for the hard work.

I will be upgrading my Gazelle Value 4 to gutsy tonight at the Ubuntu Florida gutsy Release Party.  Wish i could have gotten the System76 flyer done for us in time for the party, but I did not follow up.

[https://wiki.ubuntu.com/FloridaTeam/Projects/GutsyReleaseParty](https://wiki.ubuntu.com/FloridaTeam/Projects/GutsyReleaseParty)

I am armed with the 2.10 driver and ready for action.  I will post with any info I have about the upgrade.

I heart my System76 laptop!

Thanks again,

Jimmy (pak33m)

---

### Post by theologian aaron on 2007-10-18
I have the same problem as rowan187, except I am on a daru2.
output of cat /proc/asound/version on mine is  
[I]
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct 18 2007 for kernel 2.6.22-14-generic (SMP).[/I]

I've been running gutsy for a couple weeks, and sound did work until now.

---

### Post by thomasaaron on 2007-10-18
theologian aaron,

It looks like you DID run the 2.1.0 version of the system 76 driver, right?
System >Admin> System 76 Driver (click the about button to determine the version)
Click the install tab and install button to run.


If this does not work, please post the output of:

cat /etc/modprobe.d/alsa-base | tail -5




Best,
Tom

---

### Post by theologian aaron on 2007-10-18
[I]# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig
options snd-hda-intel model=targa-dig[/I]

ran the driver twice, and the restore once.

When I click on the speaker icon I get:
[I]
The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/I]

---

### Post by crichell on 2007-10-18
theologian - The output you posted looks correct.  Run the following command and reboot.  This should restore sound.  We'll try to determine why you're loosing sound when you run the driver.

> sudo apt-get install --reinstall linux-image-2.6.22-14-generic

---

### Post by mstager on 2007-10-18
I just upgraded my gazv1 to Gutsy Gibbon. It went well - sound, wireless, printing all seem to work. 

One thing I noticed is that the CPU frequency monitor is saying that frequency scaling is unsupported and reports 798Mhz. Any thoughts what might be going on?

Also seems like suspend/hibernate not working seem to go into suspend but when waking up screen remains black and system will not receive any keyboard or mouse input. Have to hold down power button to reboot.

 By the way, when I installed the System76 driver it said "all drivers are provide by Ubuntu..." which I think was expected.

---

### Post by AusIV4 on 2007-10-18
I did a clean install on my gazv3 (on an extra partition, just for testing). After running the driver, that partition won't boot. It hangs with a tiny sliver of a bar on the Ubuntu loading screen.

It reminds me of past experiences when Grub's menu.lst pointed to the wrong UUID for the kernel, but this time it seems to be correct.

Any ideas?

---

### Post by Rowan187 on 2007-10-18
Well at first i ran the install and it didn't work, now the Restore is taking forever.. its been like half an hour, usually it doesn't take that long.. so i'm still waiting for that to be good. but anyways, after the Install i got this 

rowan@Misfit:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc3.
Compiled on Oct 17 2007 for kernel 2.6.22-14-generic (SMP).

Other than the sound I think everything else is okay.

Edit: I also tried the sudo apt-get install -reinstall (linux driver version here)
did nothing :(

---

### Post by crichell on 2007-10-18
> After running the driver, that partition won't boot. It hangs with a tiny sliver of a bar on the Ubuntu loading screen.

Can you chroot into the Gutsy partition and run the following commands:

```
sudo rm /etc/modprobe.d/blacklist-ata
```
```
sudo nano /etc/initramfs-tools/modules
```

remove "piix" from the file

```
sudo update-initramfs -u
```

Reboot.  Let me know if you need help chrooting into the Gutsy partition.  I'll be sending down a new driver in a few minutes so the bug doesn't snag others.

---

### Post by crichell on 2007-10-18
System76 Driver 2.1.1 has just been released.  This release fixes the Gutsy upgrade for gazv3 customers.

---

### Post by AusIV4 on 2007-10-18
> **crichell said:**
> Can you chroot into the Gutsy partition and run the following commands:
...
Reboot.  Let me know if you need help chrooting into the Gutsy partition.  I'll be sending down a new driver in a few minutes so the bug doesn't snag others.

I got a bunch of errors when I ran those commands, relating to the non-existance of /dev/null as a result of using chroot.

When I tried to boot, the splash image didn't show up, and there were a bunch of errors related to the splash image, and it still didn't boot.

Unless you have any other ideas, I'll just re-install from the CD once the update comes through. As I say, it was a clean install on a spare partition, so there's nothing really lost.

---

### Post by crichell on 2007-10-18
> **Rowan187 said:**
> Well at first i ran the install and it didn't work, now the Restore is taking forever.. its been like half an hour, usually it doesn't take that long.. so i'm still waiting for that to be good. but anyways, after the Install i got this 

rowan@Misfit:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc3.
Compiled on Oct 17 2007 for kernel 2.6.22-14-generic (SMP).

Other than the sound I think everything else is okay.

Edit: I also tried the sudo apt-get install -reinstall (linux driver version here)
did nothing :(

Your Alsa version info looks correct.  We'll have to test tomorrow morning.  Unfortunately I don't have that model at home.

I have one idea to try first.  Run the following command and then run the System76 Driver (Install from the Drivers tab - don't have to run restore)

```
sudo rm -r /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3
```

What we're doing is removing the panv2 alsa version from the file system.  The driver will then download a fresh copy from our server and install the driver.

---

### Post by crichell on 2007-10-18
> **AusIV4 said:**
> I got a bunch of errors when I ran those commands, relating to the non-existance of /dev/null as a result of using chroot.

When I tried to boot, the splash image didn't show up, and there were a bunch of errors related to the splash image, and it still didn't boot.

Unless you have any other ideas, I'll just re-install from the CD once the update comes through. As I say, it was a clean install on a spare partition, so there's nothing really lost.

Fresh install will be best.  I released the updated driver (2.1.1) so you're good to go.  Thanks for reporting this one early.

---

### Post by theologian aaron on 2007-10-18
Can I just remove the sys76 driver altogether?  Is so, how?  Most things worked fairly well without it.  Sound is certainly more important to me than battery monitor, or any other little thing.

---

### Post by Rowan187 on 2007-10-18
> **crichell said:**
> Your Alsa version info looks correct.  We'll have to test tomorrow morning.  Unfortunately I don't have that model at home.

I have one idea to try first.  Run the following command and then run the System76 Driver (Install from the Drivers tab - don't have to run restore)

```
sudo rm -r /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3
```

What we're doing is removing the panv2 alsa version from the file system.  The driver will then download a fresh copy from our server and install the driver.

Gave that a try too, No luck. I can wait till tomorrow or whenever, luckily I finished all my audio projects a few days ago, and there's always my windows partition (ewww)

---

### Post by theologian aaron on 2007-10-19
I have tried everything suggested so far, and I still have no sound.  When I remove the driver it still does the same thing.  This is very frustrating.  Unlike the other fella, I really do need sound to work.

---

### Post by thomasaaron on 2007-10-19
NOTICE: Wow! This thread has become a bit of a free-for-all. It is becoming increasingly difficult to track. Let's take this to email, so that I can keep everybody straight.

Send email to support(at)system76(dot)com with the following information: 

1. Model of your System 76 Computer.
2. What you have tried already.
3. Output of: cat /proc/asound/version
4. Output of: cat /etc/modprobe.d/alsa-base | tail -5
5. If you are using anything other than 32-bit Gutsy, please say so.

Thanks,
Tom

---

### Post by MarkID on 2007-10-19
> **AusIV4 said:**
> I did a clean install on my gazv3 (on an extra partition, just for testing). After running the driver, that partition won't boot. It hangs with a tiny sliver of a bar on the Ubuntu loading screen.

It reminds me of past experiences when Grub's menu.lst pointed to the wrong UUID for the kernel, but this time it seems to be correct.

Any ideas?

Something similar happened to me.  I upgraded from Feisty on my Daru1 and it hangs on boot with nothing happening on the status bar.  I did a verbose boot and booted up using an earlier kernel (2.16) and it booted fine.  Gutsy works fine except for:  Hibernate doesn't work.  Hibernate does a complete shutdown, and since it won't reboot automatically, I need to boot up with the earlier kernel, etc.  Also, desktop effects don't work.  Beryl worked fine under Feisty, but the supposed built in Compiz effects in Gutsy don't work, or I just haven't figured out how to activate them.

Sound, suspend, network, wireless, all work fine.

---

### Post by thomasaaron on 2007-10-19
MarkID,

Are you saying that going from Feisty to Gutsy via Ubuntu's servers did not work, but a fresh install from a CD did?

---

### Post by steveneddy on 2007-10-19
> **thomasaaron said:**
> MarkID,

Are you saying that going from Feisty to Gutsy via Ubuntu's servers did not work, but a fresh install from a CD did?

There are a few posts out there saying the same thing.

---

### Post by MarkID on 2007-10-19
> **thomasaaron said:**
> MarkID,

Are you saying that going from Feisty to Gutsy via Ubuntu's servers did not work, but a fresh install from a CD did?

Know I didn't use a CD.  Rather, when Grub starts I hit ESC and I can choose to boot a different kernel.  That's what works.

---

### Post by rwecker on 2007-10-19
> **MarkID said:**
> Know I didn't use a CD.  Rather, when Grub starts I hit ESC and I can choose to boot a different kernel.  That's what works.

i have the same problem with my darter (white)  the gutsy kernels just hang on boot.

---

### Post by jerry47 on 2007-10-20
First, thanks to all the System76 folks for my Serval Performance Laptop. Great machine and support. In particular want to thank Tom and Carl. Best support in the industry.

Upgraded the Serval without issue, Really prefer clean install as opposed to an upgrade. But, so far, not much to complain about.

Also, congratulations to all the people at Canonical for job well done for the version  upgrade. Huge task with very good results.

Upgraded both a desktop with Asus 845 chipset and ATI Radeon 9000 graphics adapter and the Serval Performance. No issue, as has been posted on the Ubuntu website about the title bar missing using the desktop effects. The Serval does exhibit the missing title bar behavior, however. 

I am sure that in time, Ubuntu will find the solution to this small problem.

I am new to the Linux OS, but the learning experience is fun to research and implement. 

All the hard work is appreciated.

Thanks,

Gerald Rozner

---

### Post by danns on 2007-10-20
One thing I noticed on my Serval upgrade was that it booted the 2.4.22-14-i386 kernel but the retricted modules were installed for the 2.4.22-14-generic kernel.  I tried all those steps posted previously to get the system76 driver to re-enable what was missing to no avail.  It was not until I noticed the prior discrepancy and chose to boot into the generic kernel at grub that everything was back to normal.  Give that a shot!

---

### Post by lhgreene on 2007-10-31
Taking you up on the invitation to contact you if we have any trouble upgrading to Gutsy Gibbon. 

We have a system76 Notebook, model S96FM, which had been running Feisty, with no problems before the upgrade to Gutsy Gibbon.

After the upgrade - we no longer have any wireless. The wireless light on the front of the notebook no longer lights, we don't see wireless as a choice in Knetwork Manager or Network Manager (just ethernet eth0 and modem), though options in Knetwork Manager provides a "Disable Wireless" option and in Settings.of Knetwork Managerunder Wireless Networks it does list all the wireless networks that had previously been connected to prior to the Gutsy upgrade - but with no way to connect to them.

We have followed the instructions for Gutsy Upgrade - Knowledge76, and re-enabled the [http://planet76.com/repositories/](http://planet76.com/repositories/).  We've got version 2.1.1 of the System76 driver. We ran the System76 Driver, clicked Install Drivers and Install - it said it installed the drivers and instructed us to reboot - which we did. But we still have no wireless. Ethernet connections are working however.

FYI - our /etc/network/interfaces file contains:

         # The loopback network interface
         auto lo
         iface lo inet loopback

so that seems normal and wouldn't appear to be the problem. 

So what do we have to do, to get wireless functioning under Gutsy?

---

### Post by thomasaaron on 2007-11-01
1. Make sure your wireless router is working. You might want to try the computer out with a different known-good router.
2. Try the Fn-F2 key combination.
3. Right-click on the network manager icon and select enable wireless.

I've not seen any regressions with networking in Gutsy. So, it is probably a setting somewhere.

---

