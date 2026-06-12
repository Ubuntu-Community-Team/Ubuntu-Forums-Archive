---
title: "System76 Driver 1.9.95 - Feisty Support and More"
date: 2007-04-18
forum: System76 Support
---

### Post by crichell on 2007-04-18
Hello Everyone,

System76 Driver 1.9.95 will be released tomorrow - Wednesday, April 18.  This update is a major re-write with some new features and Ubuntu 7.04 Feisty support.

See more info at [http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

Version 1.9.95 Changelog

   1. Now supports Ubuntu, Kubuntu, Xubuntu, Edubuntu
   2. Major re-write
   3. Implement System Information tab
   4. Separate drivers and restore task
   5. Bug fixes
   6. Move to GLADE
   7. Add new Wild Dog Professional (wilp3)

---

### Post by AusIV4 on 2007-04-18
Thank you for the Kubuntu support!

I never had time to pick through the code and write a QT version of it, and I was really hoping that for Feisty I could do a clean Kubuntu install on my Gazelle to get rid of the Gnome stuff I never use.

---

### Post by unique on 2007-04-18
Gazelle Performance still has no sound after running this driver in Feisty.

---

### Post by crichell on 2007-04-18
Hi guys - the driver hasn't been passed down yet.  Expect to see it within a couple of hours.

BTW - We didn't create a QT version, the driver does depend on gtk and glade stuff but it's not too heavy for Kubuntu users.

---

### Post by AusIV4 on 2007-04-18
> **crichell said:**
> BTW - We didn't create a QT version, the driver does depend on gtk and glade stuff but it's not too heavy for Kubuntu users.

I assumed it wasn't a QT version, I meant that if i had rewritten the installer, I would have done so using QT. I have no problem installing a few libraries - I use a couple of gtk programs anyway. Does downloading the driver from the system76 repository handle these dependencies?

---

### Post by crichell on 2007-04-18
> Does downloading the driver from the system76 repository handle these dependencies?

Yes it does - in the Debian way - the dependencies are satisfied by the standard Ubuntu repositories.  BTW - I expect it to come down within about an hour.  I'll keep you posted once it hits the our repo.

---

### Post by crichell on 2007-04-18
The new driver is in the System76 repository.  It will come down automatically or if you would like to grab it now simply go to System > Administration > Update Manager.  Click *Check* and then *Install Updates*.

Best, Carl

---

### Post by Nangineer on 2007-04-18
I upgraded to Feisty and had master volume controls, but the master volume control is gone after installing this new driver. This is the same problem I had with the previous driver on Edgy. (silver Gazelle Value)

---

### Post by crichell on 2007-04-19
Hi Nangineer,

The driver doesn't modify sound - actually that model is now fully supported by Ubuntu (and Ubuntu Certified).  See our matrix here:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

Do you have sound but no icon speaker icon at the top of the screen or a red line though the speaker?  Please post the output of:

```
cat /proc/asound/version
```

Thanks

---

### Post by dhawk312 on 2007-04-19
Carl, after upgrading my sound doesn't work at all; I have the sound icon and everything appears normal, i.e. volume is on, alsa is installed and configured for the right sound card, hal is identifying the card properly, etc.  I've used several of the posted fixes in the Feisty forum and Launchpad but none of them have worked.

---

### Post by crichell on 2007-04-19
thanks dhawk,

we have created a bug report here:

[https://bugs.launchpad.net/system76/+bug/107606](https://bugs.launchpad.net/system76/+bug/107606)

I expect to release a fix today.

---

### Post by Nangineer on 2007-04-19
> **crichell said:**
> Hi Nangineer,

The driver doesn't modify sound - actually that model is now fully supported by Ubuntu (and Ubuntu Certified).  See our matrix here:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

Do you have sound but no icon speaker icon at the top of the screen or a red line though the speaker?  Please post the output of:

```
cat /proc/asound/version
```

Thanks

I still have the speaker icon at the top. Let me back up a few steps. When I upgraded the S76 driver to 1.9.9 under Edgy, that icon became the headphone control instead of the master control, and there appeared to be no master control at all. I changed that to control the speaker instead, but in either case the Fn volume controls did nothing (the controls for speaker, headphone, and PCM did work).

I upgraded to Feisty which restored the master control and Fn volume buttons. But yesterday, I installed the new S76 driver; upon reboot, I was back to the same situation I was in after installing the 1.9.9 driver under Edgy: Fn volume buttons displayed volume change on screen but did not actually change volume, and the speaker icon at the top controls the speaker instead of the master volume (there once again appears to be no master control).

Anyway cat /proc/asound/version gives this:
```
Advanced Linux Sound Architecture Driver Version 1.0.14rc3.
Compiled on Apr 18 2007 for kernel 2.6.20-15-generic (SMP).

```
and that kernel is the one I'm running.

---

### Post by crichell on 2007-04-19
I think I misunderstood which system you have.  Can you open the System76 driver and post the System76 Model number displayed on the System Information tab.

Thanks, Carl

---

### Post by Nangineer on 2007-04-19
gazv2

---

### Post by crichell on 2007-04-19
thanks, that clears it up for me.  Please file a bug report for us:

[https://launchpad.net/system76](https://launchpad.net/system76)

A fix will come down ASAP.

---

### Post by Nangineer on 2007-04-19
Thanks. By the way, just for clarification, the headphone control does not affect sound output. Only PCM and Speaker controls do.

---

### Post by thomasaaron on 2007-04-19
We have identified the problem and are working on the fix. Should be out today or tomorrow. 

Best,
Tom

---

### Post by tac-tics on 2007-04-19
I have also lost my sound after the upgrade, but the situation is a bit strange:

- My internal speakers aren't working. No matter what I've tried, I can't get them to make a sound.
- My headphone jack works, but I get static on my headphones. After some investigation, it appears my built-in mic is sending everything it picks up directly to the sound card.


I have a temporary fix where if I mute my MIC volume, I can use my headphones to listen to music, but it is irritating that I pointlessly lost the use of my speakers when I upgraded. Any help with figuring out what's wrong would be greatly appreciated.

---

### Post by crichell on 2007-04-19
Hi tic-tacs - we will be releasing a fixed driver today.  I'll post here once it's released.

Carl

---

### Post by crichell on 2007-04-19
The fixed driver has been released:  Gazelle Performance users please update and run the driver to restore sound:

To get the latest driver: Go to System > Administration > Update Manager. Click Check and then Install Updates.

Run the Driver: 

[LIST=1]
[*]System > Adminsitration > System76 Driver
[*]Choose Install Driver Tab
[*]Click Install
[/LIST]

---

### Post by madcitybrit on 2007-04-19
I installed this driver on my Darter yesterday evening. I'm still running Edgy Eft (saw the driver update and just ran it I'm afraid!). Now I have no sound either. Speaker icon is still present, and all volume controls work, just no sound through the speakers. I haven't tried headphones yet. I figured I would try running the System76 Driver Installer (via Admin menu) just to see if that would fix anything, but unfortunately not.

In the event it helps my system model is daru1. Also I ran cat /proc/asound/version which output the following:

```

Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).

```

Any ideas?

Thanks.

---

### Post by crichell on 2007-04-19
Hi madcitybrit -

```
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
```

This version looks like the driver hasn't been ran or there is an error when it runs.  Can you run the driver from the command line and post the last lines for me (there may be a compile error or something)

Run the driver via

```
system76-driver
```

You'll see the output of what is happening in your terminal

Thanks, Carl

---

### Post by ShdwNova on 2007-04-20
dhawk312, try turning on surround in alsamixer. In a terminal type alsamixer
Hit the left or right arrow keys to get over to Surround. Hit M to turn it on and use the 
up and down arrows to adjust the vol. This magically fixed sound for me.

---

### Post by MorphWVUtuba on 2007-04-20
```
Leaving directory `/opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3/pcmcia'
/sbin/depmod -a 2.6.17-11-generic 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

make -C /lib/modules/2.6.17-11-generic/build M=/opt/system76/system76-driver/src/tifm
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
```


This is my system76-driver command line output.  At this point, I have a blinking cursor but no prompt.  The notification that the install is complete is up with the close button, but that button does not do anything, and the driver installer has hung up.

---

### Post by unique on 2007-04-20
Cool! the new System76 2.0 driver fixed the sound issue on my Gazelle Performance in Feisty. I did have to install build-essential though for it to compile the alsa drivers.

I really like the new driver where you now have the choice of just installing the drivers only or doing a full restore. 

Great work guys!

---

### Post by crichell on 2007-04-20
> I did have to install build-essential though for it to compile the alsa drivers.

That's interesting - we thought build-essential would be a dependency but in our testing we didn't have to install it.  Thanks for noticing we'll take another look.

---

### Post by madcitybrit on 2007-04-20
> **crichell said:**
> Hi madcitybrit -

```
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).
```

This version looks like the driver hasn't been ran or there is an error when it runs.  Can you run the driver from the command line and post the last lines for me (there may be a compile error or something)

Run the driver via

```
system76-driver
```

You'll see the output of what is happening in your terminal

Thanks, Carl

Okay, I ran system76-driver in a terminal and there were indeed errors. Here's the output:

```

grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-11-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a kdelibs4c2a libartsc0 libvorbisfile3 kdelibs-data kdebase-data liblualib50 libpcre3 kicker pptp-linux libkonq4 libavahi-qt3-1
  libxcomposite1 libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
make dep
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
make[1]: Entering directory `/opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3'
find: /tmp/patch: No such file or directory
find: /tmp/patch/alsa-driver-1.0.14rc3: No such file or directory
make[2]: Entering directory `/opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3/acore'
make[2]: Leaving directory `/opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3/acore'
make[1]: Leaving directory `/opt/system76/system76-driver/src/sys76-alsa-1.0.14rc3'
Makefile:5: /tmp/patch/alsa-driver-1.0.14rc3/toplevel.config: No such file or directory
Makefile:6: /tmp/patch/alsa-driver-1.0.14rc3/Makefile.conf: No such file or directory
Makefile:16: /tmp/patch/alsa-driver-1.0.14rc3/alsa-kernel/core/Makefile: No such file or directory
Makefile:28: /tmp/patch/alsa-driver-1.0.14rc3/Rules.make: No such file or directory
make[2]: *** No rule to make target `/tmp/patch/alsa-driver-1.0.14rc3/Rules.make'.  Stop.
make[1]: *** [dep] Error 1
make: *** [include/sndversions.h] Error 2

```

Under /opt/system76 there is only a system76-driver directory. I had re-installed my system a week or so ago and successfully applied the 1.9.9 driver at that point, if that is of any help here.

Thanks.

---

### Post by crichell on 2007-04-21
madcitybrit - for some reason the driver didn't install cleanly for you.  Run the following three commands and the driver should run without error.

```
sudo apt-get remove system76-driver
```

```
sudo rm -r /opt/system76/system76-driver/
```

```
sudo apt-get install system76-driver
```

---

### Post by madcitybrit on 2007-04-21
Hi Carl

I ran the commands you posted and all seemed to go well. I then ran the 'system76-driver' command again and many files were downloaded, but then I got the same errors as before (as posted above).

I noticed in Synaptic Package Manager that I didn't have build-essential installed (as mentioned in unique's post above). So I installed build-essential and re-installed the system76-driver, and hey presto, after re-booting I had my sound back!

Thanks for your help Carl, and unique for his helpful post too.

Can't help but say it, but I am continuing to love my Darter and the great support in these forums! :)

---

### Post by steveneddy on 2007-04-22
I upgraded to Feisty and the card reader works on my Serval performance now!!

How about the onboard web cam?

-SE

---

### Post by thomasaaron on 2007-04-23
We don't have support for Serval's onboard camera yet.
But we are working on it.

---

