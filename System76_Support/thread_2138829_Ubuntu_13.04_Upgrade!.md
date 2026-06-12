---
title: "Ubuntu 13.04 Upgrade!"
date: 2013-04-25
forum: System76 Support
---

### Post by isantop on 2013-04-25
Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]Fresh installs and online upgrades with Software Updater are good to go.
[*]Don't forget to install the System76 Driver after installation! Just go to [http://planet76.com](http://planet76.com) and click the download link to automatically grab the latest version!
[*]The 3.2.7 version of the System76 Driver does include fixes for Bluetooth and Wireless on our current lineup of laptops.
[*]If you have a GazP8 and find yourself stuck without wireless, you can suspend the machine with Fn+F4 then resume to restore wireless until the next boot. You can then run the Restore function in the driver to make the fix permanent.
[/LIST]

That should be everything. The direct upgrade instructions are located at: [Ubuntu 13.04 Upgrade](http://knowledge76.com/index.php/Version_Upgrade).

---

### Post by matthewpetty on 2013-04-25
Will following the instructions here ([http://knowledge76.com/index.php/Version_Upgrade](http://knowledge76.com/index.php/Version_Upgrade)) keep my user data, or will it completely overwrite the whole installation?

Obviously a backup is a good idea either way.

---

### Post by isantop on 2013-04-25
If you're using Software Updater, it will preserve your data. If you use a disk, then be sure to choose "Upgrade Ubuntu 12.10 to 13.04", which will also keep your data.

Obivously, the safest route is to back up in either case, but these should save you from having to restore as well.

---

### Post by b3d on 2013-04-25
> **isantop said:**
> Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]Fresh installs and online upgrades with Software Updater are good to go.
[*]Don't forget to install the System76 Driver after installation! Just go to [http://planet76.com](http://planet76.com) and click the download link to automatically grab the latest version!
[/LIST]

That should be everything. The direct upgrade instructions are located at: [Ubuntu 13.04 Upgrade](http://knowledge76.com/index.php/Version_Upgrade).

Unless you use the Chrome browser. If you use Chrome it's a good idea to wait a few more days until Google can push out an update to Chrome that is still in the testing phase.

---

### Post by zhogan85 on 2013-04-26
Just wanted to report a seamless upgrade, and with a couple hours of moderate usage last night, everything seems to be working. 

And to b3d's point about Chrome, the issue is with missing dependecies, installing [https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325788/+files/libudev0_175-0ubuntu19_amd64.deb](https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325788/+files/libudev0_175-0ubuntu19_amd64.deb) , for 64 bit, or [https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325790/+files/libudev0_175-0ubuntu19_i386.deb](https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325790/+files/libudev0_175-0ubuntu19_i386.deb) for 32 bit should fix the dependency issue. Or you can just use Chromium, which doesn't have this issue.

Cheers!

---

### Post by dkhinkle on 2013-04-26
I purchased a Gazp8 with 1TB HDD at the turn of the year, and 12.10-64bit with whole disk encryption worked fine.  After a number of updates, the /boot partition filled up, and some of the old kernels had to be removed manually before subsequent updates would be successful.  (I didn't encounter this problem before on my old PC with previous versions of Ubuntu.)  Unfortunately, this is what caused my 13.04 upgrade to fail somewhere in the middle.

So, I decided to do a clean install from a USB-key (again enabling whole disk encryption), followed by running the Software Updater, and finishing up with the new System76 Driver.  Everything seemed to install properly, but I needed (and still need) a physical ethernet connection, since WiFi (and BT) cannot be turned on.  And, the screen brightness cannot be changed.  Has anyone else encountered this?  Does anyone know the root-cause?

---

### Post by tonyr2k8 on 2013-04-26
I have the same system (gazp8). I'm having the same problem. I went back to old version (12.10), so everything would work again. Will try the new version when a fix is made.

---

### Post by flatlander119 on 2013-04-28
Im having the same troubles with the Bluethoot, I can turn it on from the FN+F12 or from system settings, also i can user the fn+f11 i cant turn on the wireless as well, by default I has able the wireless but i use my ethernet cable for mor speed .....
I ask to tech support and the just keep saying ilogical things, even they say to do a fresh install,,, but that doesnt works either..... I think they didnt know this isusses.... so im wondering how they install the version 13.04 in the new machines....
Right now im using 13.04, so I used a live cd of 12.10 (to test) and the bightness keys doesnt work but with the SYSTEM 76 DRIVER in the INstall Drivers seccion if you press it you will see Enable brightness hot keys and that drivers  make works the birghtness keys, in 13.04 the SYSTEM 76 drivers secctions doesnt say something about bluethoot or wireless drivers.....
Im not a hitech guy but just traying to understand this...

I HOPE TO SYSTEM 76 FIX THIS ISSUE......

---

### Post by flatlander119 on 2013-04-28
> **dkhinkle said:**
> I purchased a Gazp8 with 1TB HDD at the turn of the year, and 12.10-64bit with whole disk encryption worked fine.  After a number of updates, the /boot partition filled up, and some of the old kernels had to be removed manually before subsequent updates would be successful.  (I didn't encounter this problem before on my old PC with previous versions of Ubuntu.)  Unfortunately, this is what caused my 13.04 upgrade to fail somewhere in the middle.

So, I decided to do a clean install from a USB-key (again enabling whole disk encryption), followed by running the Software Updater, and finishing up with the new System76 Driver.  Everything seemed to install properly, but I needed (and still need) a physical ethernet connection, since WiFi (and BT) cannot be turned on.  And, the screen brightness cannot be changed.  Has anyone else encountered this?  Does anyone know the root-cause?

Im having the same issue with the bluethoot and wireless.....
did you contact tech support????

---

### Post by tonyr2k8 on 2013-04-28
When I contacted support I was told it was bad burn or I had hardware problems, but when I went back to a prior version 12.10, the problems went away. A clean install was done.

I also found out that when I go into suspend, and then come out of suspend my internal mic stops working. I have to insert an external mic and then remove it, and then the built in mic works again.

I was able to get wirless to work by going in a shutting my laptop lid, and then re-open it, then the wireless would work. Could never get bluetooth to work.

Going to use the prior ubuntu version till a fix is found.

**Noticed a new build of the driver 3.2.7 was released on the 27th, can some tell me if the recent fixed the problems? The changelog on the wiki only covers up to the version 3.2.1. Thank you.**

---

### Post by RedRat on 2013-04-28
Just wondering. I have the Serval Pro running 10.04LTS and wonder if I can make the upgrade to 13.04 or just stay at 12.04. I am not a big fan of the new interface in 12.04 so I switched it back to what I am comfortable with. Can this be done with 13.04 or are you stuck with the Unity interface.

---

### Post by jdwaugh on 2013-04-28
I am pretty sure you can use whatever DE you like, be it KDE, Gnome3, XFCE, etc.  But I am not sure you can go from 10.04 to 13.04 directly as a distribution upgrade.

---

### Post by philbert on 2013-04-28
I tried the upgrade on my GP7, bought wiht 12.04, and upgraded to 12.10.and it took at least two hours, and I notice a file not found message when booting. I suspect it came from the GRUB loader. I backed up my files, download an 13.04 iso, and reinstalled, along with reinstalling the filesystem, in under 30 minutes. Shoud have done that first. thanks to tonyr2k8 for posting the news on the 3.2.8 driver as it was not there Saturday when I last checked System 76. I have it installed now.

---

### Post by fredsea on 2013-04-28
> **isantop said:**
> Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]Fresh installs and online upgrades with Software Updater are good to go.
[*]Don't forget to install the System76 Driver after installation! Just go to [http://planet76.com](http://planet76.com) and click the download link to automatically grab the latest version!
[/LIST]

That should be everything. The direct upgrade instructions are located at: [Ubuntu 13.04 Upgrade](http://knowledge76.com/index.php/Version_Upgrade).

Well, that was a bummer! I ran the Ubuntu upgrade option on my Lemur, and when the system tried to reboot it came up with a "file not found" error and that's the end of the boot :( No further info showing (at best, I got a grub menu and choosing "ubuntu" brought the "error: file not found.hit any key to continue" message  - hitting any key did not produce any visible effect). Obviously, I'll have to do a fresh install, as I don't even know how to identify what file might be missing in the first place (and I don't se how I could find that out, even by booting from a live CD/DVD). I'll do that as soon as I get an ISO of 13.04, AND I have the time, but it would be nice if there was  a simple solution...

---

### Post by RedRat on 2013-04-28
> **philbert said:**
> I tried the upgrade on my GP7, bought wiht 12.04, and upgraded to 12.10.and it took at least two hours, and I notice a file not found message when booting. I suspect it came from the GRUB loader. I backed up my files, download an 13.04 iso, and reinstalled, along with reinstalling the filesystem, in under 30 minutes. Shoud have done that first. thanks to tonyr2k8 for posting the news on the 3.2.8 driver as it was not there Saturday when I last checked System 76. I have it installed now.

My take home lesson here then is to probably download the 12.04 iso and upgrade from that disk onto my Serval Pro, then download the System76 driver, eh? I am not terribly interested in these in-between versions, I prefer to stick with LTS releases. I think I may go that route. Any observations?

---

### Post by fredsea on 2013-04-29
Well, even though I am not as put off by Unity as I was at first, I'd still much rather use KDE, Cinnamon, or LXDE, depending on the system - no need to use Unity at all: this is not Windows, you know - you can choose whatever interface works for you!

---

### Post by tonyr2k8 on 2013-04-29
I originally had the 3.2.6 driver installed. Did a new clean install and used the 3.2.7 package. The keys now work.

Thank you System76

---

### Post by Alan.Brown on 2013-04-29
When I use **Software Updater** I get the following window - **Failed to Download Repository Information - Check your Internet Connection**  My connection is very good.

I have several problems since upgrading to 13.03 three days ago and I am concerned I am missing on updates to fix them.

_**OK - I have fixed the problem now**_

---

### Post by dkhinkle on 2013-04-30
I've moved back to 12.04 LTS as well for the time being.  It (along with the latest System76 Driver) installs and works flawlessly.

---

### Post by isantop on 2013-05-01
> **dkhinkle said:**
> I've moved back to 12.04 LTS as well for the time being.  It (along with the latest System76 Driver) installs and works flawlessly.

We do recommend running the latest version, and we now have a fix for the WiFi and Bluetooth issues on your Gazelle.

---

### Post by DVDFortyTwo on 2013-05-03
Wifi works poorly after the upgrade on my Serval Professional (ser-p7).  It is intermittent and goes out frequently, and the only way I've found to reconnect is to reboot the machine.  A window pops up as shown here [http://img703.imageshack.us/img703/6609/badwifi.png](http://img703.imageshack.us/img703/6609/badwifi.png), but clicking the connect button doesn't do any good.  I run a lot of automated scripts on here that need a reliable internet connection, so this is a show stopper for me until it's fixed.  I've never had a problem with it before, and I've already tried the "restore" function on the 3.2.7 driver, which didn't do any good.  I've had to reboot it twice in the last 24 hours to restore the connection.

---

### Post by isantop on 2013-05-03
Does this happen for you only on battery, or is it happening while the system is plugged in too?

---

### Post by DVDFortyTwo on 2013-05-03
> **isantop said:**
> Does this happen for you only on battery, or is it happening while the system is plugged in too?
It's only happened so far twice when it's plugged in, but i just upgraded about 24 hours ago.  Of course it hasn't happened since I posted about it.  I'm hoping maybe it was just a fluke somehow.

---

### Post by DVDFortyTwo on 2013-05-05
> **DVDFortyTwo said:**
> It's only happened so far twice when it's plugged in, but i just upgraded about 24 hours ago.  Of course it hasn't happened since I posted about it.  I'm hoping maybe it was just a fluke somehow.
It's happened two more times in the last 48 hours, so I doubt it's a fluke anymore.  :(

---

### Post by isantop on 2013-05-06
Is it happening with the system is plugged in, or only when it's on battery?

---

### Post by DVDFortyTwo on 2013-05-06
> **isantop said:**
> Is it happening with the system is plugged in, or only when it's on battery?
It's happened so far when I've had it plugged in.  It hasn't happened while on battery yet, but I haven't had it on battery very much either recently.

---

### Post by isantop on 2013-05-06
This sounds like a failing wireless card to me. You'll want to open a support ticket on our website to get a replacement.

---

### Post by fredsea on 2013-05-08
> **fredsea said:**
> Well, that was a bummer! I ran the Ubuntu upgrade option on my Lemur, and when the system tried to reboot it came up with a "file not found" error and that's the end of the boot :( No further info showing (at best, I got a grub menu and choosing "ubuntu" brought the "error: file not found.hit any key to continue" message  - hitting any key did not produce any visible effect). Obviously, I'll have to do a fresh install, as I don't even know how to identify what file might be missing in the first place (and I don't se how I could find that out, even by booting from a live CD/DVD). I'll do that as soon as I get an ISO of 13.04, AND I have the time, but it would be nice if there was  a simple solution...

Just wanted to add that reinstalling from a 13.04 DVD I opted to "reinstall" the 13.04 version that was already on disk (and which would not boot as described in the original message), and this time things went fine, including preserving both the /home part of the file system and keeping all applications that were added to 12.10 via apt.

---

### Post by FoundmyTux on 2013-05-10
I own a Leopard-extreme. Ubuntu12.04 works perfect on it, but when I try to either upgrade or direct install to 12.10 or 13.04, I receive the following message on boot up:
     
    EDAC sbridge: ECC is disabled. Aborting
    EDAC sbridge: Couldn't find mci handler

Is this something I need to worry about? For now i'm sticking with 12.04 until I can fine an answer to what is causing this.

---

### Post by roegel on 2013-05-13
Hello,

I have recently purchased a System 76 lemur ultra with Ubuntu installed.
All seemed to work fine. Today I have decided to upgrade to 13.04. It also seemed
to work seamlessly, but after rebooting, the login page has my login, but does not
accept my previous password. How can I solve that problem?

Thanks,

Denis

---

### Post by roegel on 2013-05-13
In fact, I was wrong, my password is recognized, but as soon as I log in, I am almost instantly rejected
to the login screen. I can log in in console mode with CTRL-ALT-F1, and my data is there, but how can I fix
the graphical login problem?

Thanks,

Denis

---

### Post by isantop on 2013-05-13
It looks like your upgrade didn't go smoothly. You should reinstall Ubuntu from a live disk.

---

### Post by kend650 on 2013-05-15
> **isantop said:**
> Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]Fresh installs and online upgrades with Software Updater are good to go.
[*]Don't forget to install the System76 Driver after installation! Just go to [http://planet76.com](http://planet76.com) and click the download link to automatically grab the latest version!
[*]The 3.2.7 version of the System76 Driver does include fixes for Bluetooth and Wireless on our current lineup of laptops.
[*]If you have a GazP8 and find yourself stuck without wireless, you can suspend the machine with Fn+F4 then resume to restore wireless until the next boot. You can then run the Restore function in the driver to make the fix permanent.
[/LIST]

That should be everything. The direct upgrade instructions are located at: [Ubuntu 13.04 Upgrade](http://knowledge76.com/index.php/Version_Upgrade).


Things I learned from the 13.04 upgrade on my Bonobo 5.

First:  You can't just upgrade the System 76 drivers from the System Settings page.  You must first go to [http://planet76.com](http://planet76.com), download the lastest System76 app/drivers, then install it via the Software Center app or dpkg cli.  Then go to the System Settings and upgrade the System 76 drivers, then reboot.

Second, I am still getting these errors at boot time, and have to reboot several times, going into the advanced boot settings and fixing broken packages until I get a 'clean' boot.

[   95.054864] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
  99.000944] NVRM: GPU at 0000:01:00: GPU-ad25e052-3c8f-d86a-7df7-d92c2d9f64ab
[  101.469846] wlan0: authenticate with 00:30:44:11:e3:ef
[  101.480121] wlan0: send auth to 00:30:44:11:e3:ef (try 1/3)
[  101.495163] wlan0: authenticated
[  101.499105] wlan0: associate with 00:30:44:11:e3:ef (try 1/3)
[  101.502915] wlan0: RX AssocResp from 00:30:44:11:e3:ef (capab=0x411 status=0 aid=2)
[  101.522377] wlan0: associated
[  101.522440] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

and 

[  14.802003] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.44  Wed Mar 27 14:51:30 PDT 2013
[   16.362503] usb 3-2.1: device descriptor read/8, error -110
[   16.538451] usb 3-2.1: new high-speed USB device number 4 using xhci_hcd
[   21.552850] usb 3-2.1: device descriptor read/8, error -110
[   26.671334] usb 3-2.1: device descriptor read/8, error -110
[   26.847259] usb 3-2.1: new high-speed USB device number 5 using xhci_hcd
[   31.861544] usb 3-2.1: device descriptor read/8, error -110
[   36.979904] usb 3-2.1: device descriptor read/8, error -110
[   37.155938] usb 3-2.1: new high-speed USB device number 6 using xhci_hcd
[   42.170376] usb 3-2.1: device descriptor read/8, error -110
[   47.288864] usb 3-2.1: device descriptor read/8, error -110
[   47.392673] hub 3-2:1.0: unable to enumerate USB device on port 1

so I am guessing that there is some usb 3.0 issues.  But the drives eventually show up in the Launcher.

If anyone has recommendations on how to 'fix' these two errors, and what is causing them, I would be appreciate any advice.

Thanks,
kend650

---

### Post by ccrs8 on 2013-05-25
I was having a ton of bootup and shutdown problems similar to what kend650 described with my Wild Dog since I upgraded it from Xubuntu 12.10 to 13.04.  The new kernel that was pushed out via software updater yesterday morning (3.8.0-22) fixed my issues.  Other threads, both at Ubuntu Forums and elsewhere, said that the updated kernel would fix the problems, but I didn't want to activate the proposed software repo so I waited it out until the new kernel was released to the general public.  Anyway, hopefully the updated kernel will fix these problems for others as well.

---

### Post by jaylittle on 2013-05-27
> **isantop said:**
> This sounds like a failing wireless card to me. You'll want to open a support ticket on our website to get a replacement.
If his wireless card is an Intel one, it's probably an issue with the Intel drivers.  Intel's Linux drivers have had a few issues for awhile now, but about three months ago they got really bad.  They also got bad on the Windows side.  Intel doesn't seem to care regardless of whether it's Linux or Windows users complaining either.

[Here is a link to a thread about the issues found in Windows](http://communities.intel.com/thread/31090?start=0&tstart=0).
[Here is a link to the open bug on the issue for Arch Linux](https://bugs.archlinux.org/task/32249).

This very issue is actually preventing me from using Linux on my bonx6 right now as the wireless adapter is totally useless at my primary client's site because the connection will drop within an hour and require a reboot before it will come back (running dmesg | tail -n 50 will show you lots of firmware related issues).  So back to Windows I went so I can get my work done (without upgrading the drivers to a more recent version from Intel as that is what leads to problems on the Windows side).  Sad but true.  But let's be clear:  This is not the fault of System76 - but rather it is Intel's fault.  Note: The issues here seem to vary based upon the wireless router in use.  For instance at home I have exactly zero issues with these drivers while at certain client sites - it is practically unusable.

As for why Ubuntu is suddenly experiencing these issues, I presume it's because 13.04 moved them onto the 3.8 kernel which contains these really buggy drivers from Intel.  Up until 12.10 Ubuntu had been working off a 3.5 kernel which didn't have these issues.

---

### Post by isantop on 2013-05-28
We haven't been seeing this issues on our test-systems here in the shop. If he has the latest version of Ubuntu installed and the System76 driver is up to date, he can try running the Install function there. Otherwise, this is definitely a bad card.

---

### Post by fredsea on 2013-05-28
Ouch! I am having the same issues with my Lemur, and can't (and won't) go back to Windows! Is there any hope that System76 might be able to fix this driver problem - or that the kernel folks will? It''s not my only machine, but it's a pain in the neck....

---

### Post by isantop on 2013-05-28
There aren't driver problems; there's an issue with power saving mode which is fixed with the System76 Driver application. If there are other issues they're likely hardware problems warranting replacement of the wireless card.

---

### Post by fredsea on 2013-05-28
> **isantop said:**
> We haven't been seeing this issues on our test-systems here in the shop. If he has the latest version of Ubuntu installed and the System76 driver is up to date, he can try running the Install function there. Otherwise, this is definitely a bad card.

I had missed this message when I replied to the previous one in the thread (I have a Lemur). I believe I installed the latest driver (as drom Planet76), but, just to make sure, I went through the procedure again (it worked without problems for my Starling netbook), but no improvement at all. Like you say, it might be a flaky card, but this mess is new to 13.04, and it's strange that so many people are discovering their card is suddenly bad, after upgrading.

---

### Post by isantop on 2013-05-28
Starlings have a different, Realtek Wireless card. It's likely a flaky card or a touchy router.

---

### Post by fredsea on 2013-05-28
Well, if so, what should I do? The router is not the best, I suppose, but the Lemur is the only one having trouble, so this should point to the card (which worked all right before the upgrade, by the way).

---

### Post by isantop on 2013-05-28
Sorry about that, I thought you were having trouble on your Starling.

Try unplugging the router for a few minutes. This will clear its RAM and often helps when a single machine will not connect well.

If it still won't connect, then you'll want to open a support case.

---

### Post by jangat on 2013-05-31
I have a first generation Starling currently running 10.04. Are there any issues with doing a clean install of 13.04? I've seen a posting on this forum suggesting that 12.04 should work well, but I haven't seen anything regarding 13.04.

Thanks.

JG

---

### Post by isantop on 2013-05-31
13.04 should work better than 12.04 (it's noticeably faster), but that all said, Unity may be a bit too much for your Starling to handle comfortably. That said, if you're comfortable with doing a fresh install, 13.04 would be a better version to go to, and you should be able to go back (though, 10.04 is no longer supported).

---

### Post by Pobega on 2013-08-31
I'm running 13.04 on a Galago Ultrapro (fresh install) and I'm getting a version error when running the System76 driver from the command line.

[http://i.imgur.com/VrYnTE9.png](http://i.imgur.com/VrYnTE9.png)

Edit: Nevermind, installed from the PPA.

---

