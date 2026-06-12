---
title: "Upgrade Instructions for Ubuntu 9.10"
date: 2009-10-29
forum: System76 Support
---

### Post by thomasaaron on 2009-10-29
It's here, and it's slicker than... well, it's just really slick!

Make sure you back up any important files before upgrading! While the upgrade process seems to be going smoothly, there is always potential for problems. (On release day, Ubuntu's upgrade servers tend to get busier than a one-armed wallpaper hanger!)

STARLING USERS: The wireless driver for Karmic is requiring a complete re-write. We're almost finished with it, but we would like for you to wait until the next 2.3.* driver is released. It shouldn't be long... maybe another week. We'll post here when it is ready.

EVERYONE ELSE: To perform an online upgrade directly from Jaunty to Karmic, please follow the instructions here...

[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

---

### Post by thomasaaron on 2009-10-30
Keeping it bumped to the top for now...

---

### Post by thomasaaron on 2009-10-30
So far, upgrades seem to be going pretty well. I wonder if Ubuntu upped their server capacity.

---

### Post by mpwoodward on 2009-10-31
I'd like to do a clean install on my Serval Pro so I can format the drive to ext4. After a clean install do I just download the System76 driver? I'd also need the Nvidia application to switch screen setup (since I do that a lot). Are there other apps/drivers I'd need after doing the install? Any other caveats to doing a clean install?

Thanks.

---

### Post by ewg on 2009-10-31
I did a pre-upgrade install check and noticed there was nothing listed under "third party software' sources. I did add the planet 76 repository but was not sure I should, or need to, add the canonical ubuntu jaunty repositories before I upgrade. If i do need them, what is the specific line I should use?

Going from 9.04 to 9.10

Thanks,

---

### Post by HotShotDJ on 2009-10-31
> **mpwoodward said:**
> I'd like to do a clean install on my Serval Pro so I can format the drive to ext4. After a clean install do I just download the System76 driver? I'd also need the Nvidia application to switch screen setup (since I do that a lot). Are there other apps/drivers I'd need after doing the install? 

After the clean install, make sure you upgrade the system (using Upgrade Manager).  Make sure you reboot after this, even if there are no upgrades and/or the system doesn't tell you to.  Now, go to System -> Administration -> Hardware Drivers and select the recommended NVidia driver (185) and then click on the "Activate" button.  If no drivers show up in Hardware Drivers, you'll need to reboot again to get them to show up. You'll need to reboot after this.  I also recommend that that after you reboot, you go to a terminal (Ctrl + Alt + F1) and run "sudo nvidia-xconfig" and reboot again (I know, all this rebooting feels kind of Windows-like... ugh!)

Now you are ready for the System76 Drivers.  Download the latest System76 driver from [http://planet76.com/repositories/](http://planet76.com/repositories/) ([http://planet76.com/repositories/system76-driver-2.3.9.deb](http://planet76.com/repositories/system76-driver-2.3.9.deb)).  Just double click on it to install. Once it is installed, go to System -> Administration -> System76 Driver, click on the "Restore System" tab and then click on the "Restore" button.  And, alas, one more reboot. It worked perfectly on my PanP5.

And, YES, I believe a clean install is worth the trouble if only for the benefits of ext4.  I've seen no downside to doing this.  I even backed up my HOME partition and had the installer format /home to ext4 and then copied back the files from the external drive.  If you use Evolution, make sure you create a backup file of your settings (in evolution, File -> Backup Settings) and copy the backup file to your external drive.  You can then very easily restore Evolution after your clean install.  To get your Firefox settings back will depend on what version of Firefox you were using in Jaunty.  If you were using the default version (3.0) then it should be a straight-forward copying of the .mozilla folder back to your new home directory.  However, if you were using version 3.5, it is a little different.  Let me know if you need help with that.

---

### Post by HotShotDJ on 2009-10-31
> **ewg said:**
> I did a pre-upgrade install check and noticed there was nothing listed under "third party software' sources. I did add the planet 76 repository but was not sure I should, or need to, add the canonical ubuntu jaunty repositories before I upgrade. If i do need them, what is the specific line I should use?Don't manually add the System76 repositories to the "Other Software" tab.  Run the latest System76 driver that you can download (see my previous post to this thread).  That will get you fixed up.

---

### Post by cmnorton on 2009-10-31
> **thomasaaron said:**
> It's here, and it's slicker than... well, it's just really slick!

Make sure you back up any important files before upgrading! While the upgrade process seems to be going smoothly, there is always potential for problems. (On release day, Ubuntu's upgrade servers tend to get busier than a one-armed wallpaper hanger!)

STARLING USERS: The wireless driver for Karmic is requiring a complete re-write. We're almost finished with it, but we would like for you to wait until the next 2.3.* driver is released. It shouldn't be long... maybe another week. We'll post here when it is ready.

EVERYONE ELSE: To perform an online upgrade directly from Jaunty to Karmic, please follow the instructions here...

[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

I've got a main topic on no sound -- [http://ubuntuforums.org/showthread.php?t=1308393](http://ubuntuforums.org/showthread.php?t=1308393), but I do not have a third party tab after upgrade, so I cannot follow these instructions. 

I did remember to reload the system76 driver.

---

### Post by HotShotDJ on 2009-10-31
> **cmnorton said:**
> I've got a main topic on no sound -- [http://ubuntuforums.org/showthread.php?t=1308393](http://ubuntuforums.org/showthread.php?t=1308393), but I do not have a third party tab after upgrade, so I cannot follow these instructions. 

I did remember to reload the system76 driver.Did you remember to run System -> Administration -> System76 Driver -> System Restore after installing the new System76 driver?  Also, the "third party" tab is now called "Other Software." Do you have that tab?

---

### Post by cmnorton on 2009-10-31
Yup! I got the planet76 repository restored, reloaded software from that, re-installed the system76 driver, and I still have no hardware in my sound.

---

### Post by HotShotDJ on 2009-10-31
> **cmnorton said:**
> Yup! I got the planet76 repository restored, reloaded software from that, re-installed the system76 driver, and I still have no hardware in my sound.Unfortunately, I can't help much with that.  The sound worked "out-of-the-box" with Karmic on my PanP5 -- actually, it was better than in Jaunty -- so I haven't fiddled with the sound stuff.  I'm sure when Tom gets to work on Monday, he'll be able to better help you in you other thread.  I'm sorry I couldn't be more helpful to you.

EDIT:  Check out this thread: [http://ubuntuforums.org/showthread.php?t=1306773](http://ubuntuforums.org/showthread.php?t=1306773)  You might find some help in there.

---

### Post by mpwoodward on 2009-10-31
Thanks all--worked like a champ. Just for future reference here's what I did:

1. Backed up all my files (duh, but thought I better list it as a step)
2. Installed Ubuntu 9.10 and formatted drive (hence step 1!)
3. Ran normal Ubuntu updates (which there were some) and rebooted
4. Installed proprietary Nvidia drivers (System -> Administration -> Hardware Drivers) and rebooted
5. Installed System76 drivers and rebooted
6. Ran System76 drivers, did system restore. Rebooted.

---

### Post by HotShotDJ on 2009-10-31
> **mpwoodward said:**
> 5. Installed System76 drivers and rebooted
I'm pretty sure that this particular reboot wasn't necessary, but it certainly didn't hurt anything.  Congrats on a flawless reinstall!

---

### Post by mpwoodward on 2009-10-31
Sorry, that should have been "applied System76 system restore and rebooted," which it indicated I needed to do after it finished the restore (if I remember correctly). This solid state drive with ext4 is amazingly fast!

---

### Post by mpwoodward on 2009-10-31
Never mind--I see what you're saying now. :-)

---

### Post by HotShotDJ on 2009-10-31
> **mpwoodward said:**
> Never mind--I see what you're saying now. :-)Full Disclosure:  I'm an "old school" Linux guy.  When I first started using Linux in the late 90's, rebooting was considered a sign of weakness.  Old habits are hard to break for me. :p

---

### Post by riseringseeker on 2009-11-01
> **HotShotDJ said:**
> If you use Evolution, make sure you create a backup file of your settings (in evolution, File -> Backup Settings) and copy the backup file to your external drive.  You can then very easily restore Evolution after your clean install.  

Good point!  I did **not** do this and thought I had lost all my contact info!  I had/have a complete rsync of the /home partition though, and was able to get it all back.  I would recommend doing the back up as you say, but if someone forgets, or that backup gets hosed, here's what I had to do:

After installation, first shutdown evolution:

```
sudo evolution --force-shutdown
```

Then, remove a couple of directories in your user directory.

```
rm -R ~/.evolution
```
```
rm -R ~/.gconf/apps/evolution
```

Bring in the saved directories from your rsync'd backup.

```
rsync -avv <path to backupdisk>/home/<user>/.evolution/ /home/<user>/.evolution
```

```
rsync -avv <path to backupdisk>/home/<user>/.gconf/apps/evolution/ /home/<user>/.gconf/apps/evolution
```

After a reboot, evolution will be restored - and yes, you must reboot, or at least logout (though I did not try a logout) for evolution to "see" the new directories

This worked for me, YMMV though, I do not guarantee this will work for you!

---

### Post by ewg on 2009-11-02
Upgraded, not clean install, with no problems. I'm always confused by questions asking to replace or keep customized config files so I always keep them. 

I waited 'till after the upgrade to add the new sys76 driver, but I suggest adding the driver first. After the upgrade the system said driver was not compatible. I added the driver from synaptic, with no trouble so it's just a minor issue. 

Nice that the annoying beep at shutdown is gone.

---

### Post by Random201801 on 2009-11-12
*bumps*

any news about the update?

i'm not patient :(, it's a horrible trait of mine.

---

### Post by thomasaaron on 2009-11-12
```
any news about the update?
```

update?

---

### Post by Random201801 on 2009-11-12
excuse me, for the wireless driver for karmic. sorry hah.

---

### Post by thomasaaron on 2009-11-13
I'll be talking to our driver dev on that a little later today. I'll post back here as soon as I do.

---

### Post by thomasaaron on 2009-11-13
ATTEN: STARLING NETBOOK OWNERS RUNNING UNR 9.10
RE: INTERIM FIX

There is a new System76 Driver available. It is version 2.4.0.
If you establish a wired Internet connection and check for updates via Update Manager, it should be there.

If it is not there, you can download it from...
[http://planet76.com/repositories](http://planet76.com/repositories)
It will be the second link from the bottom of the page. Download it to your "Downloads" folder. Double-click it to install.

Once it is installed, go to Administration > System76 Driver and click the Install tab and the Install button. Then reboot your computer when the driver is finished running.

This should activate your wireless and allow you access up to about 30 or 40 feet.

We are working as quickly as possible on the long range fix and expect to have it done next week. We understand how badly you need it and will produce another System76 Driver very soon with the permanent fix.

Thank you for your patience.

---

### Post by dlavi1976 on 2009-11-13
Will it affect either in a good way or a bad way if I applied the driver on my Starling which is still running 9.04?

---

### Post by jbraswell on 2009-11-14
Hmm, I downloaded and installed the package, but when I try to install the drivers, the "Installing drivers" graphic never goes away.  I left it overnight, and it still didn't finish.  Any ideas?

Thanks

---

### Post by Eyore15 on 2009-11-14
> **jbraswell said:**
> Hmm, I downloaded and installed the package, but when I try to install the drivers, the "Installing drivers" graphic never goes away.  I left it overnight, and it still didn't finish.  Any ideas?

Thanks

I'm at 7 hours + a tad trying to install 2.4.0.  Perhaps it's a problem with their server?  No matter, I don't care for it.

This has been the first bad experience I've had with System76.  I wish they had just come out and said "don't upgrade till we give you an OK.

---

### Post by mwiktowy on 2009-11-14
> **jbraswell said:**
> Hmm, I downloaded and installed the package, but when I try to install the drivers, the "Installing drivers" graphic never goes away.  I left it overnight, and it still didn't finish.  Any ideas?

Thanks

The previous version (2.3.9) broke my wireless completely.
I successfully installed this new version (2.4.0) and it brought me back to the same performance as the stock install of UNR 9.10 ... i.e. not very good but functional if you are sitting right beside your AP.

---

### Post by theorysavage on 2009-11-14
The reason the "installing drivers" message wasn't progressing...

I ran the program from command line and found that it was getting hung up on grub. I installed grub2 instead of grub (not sure at what point that got changed on my system...but that was definitely my problem).

see the following...

levy@system76-netbook:~$ sudo system76-driver -d
options snd-hda-intel model=acer-aspire
cp: cannot stat `/etc/default/grub': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/system76-driver", line 50, in <module>
    main()
  File "/usr/bin/system76-driver", line 38, in main
    driverscontrol.installDrivers()
  File "/opt/system76/system76-driver/src/driverscontrol.py", line 910, in installDrivers
    acpi.star1()
  File "/opt/system76/system76-driver/src/acpi.py", line 114, in star1
    for line in grub_menu:
  File "/usr/lib/python2.6/fileinput.py", line 253, in next
    line = self.readline()
  File "/usr/lib/python2.6/fileinput.py", line 322, in readline
    os.rename(self._filename, self._backupfilename)
OSError: [Errno 2] No such file or directory


Then I installed grub2.


levy@system76-netbook:~$ sudo system76-driver -d
options snd-hda-intel model=acer-aspire
Generating grub.cfg ...

... and so on... then I restarted and played with the little button on the front a bit and wireless started working again! Thanks!

---

### Post by Eyore15 on 2009-11-14
> **theorysavage said:**
> The reason the "installing drivers" message wasn't progressing...

I ran the program from command line and found that it was getting hung up on grub. I installed grub2 instead of grub (not sure at what point that got changed on my system...but that was definitely my problem).


Then I installed grub2.



I'm not much of a CLI kinda guy, but I think I understood most of that.

I installed grub2 through synaptic, then went back and used the GUI to install the system76 2.4.0 driver.  Since the Starling is currently sitting six feet from the AP, it's working fine.  It will be a problem tomorrow when I try to use it at school though.  Hope they get it fixed soon.

Sort of OT ... what's the big deal with grub2.  I hear people in the forums get all excited about how much better grub2 is, but I'm not seeing anything special.  In fact, whether it be grub2 or 9.10, I think I'm booting slower on the Starling than I was before. 9.10 is certainly loading slower than 9.04 did.
mcm

---

### Post by jbraswell on 2009-11-15
OK, thanks.  grub2 worked for me.

---

### Post by nadamsieee on 2009-11-16
The System76 Karmic instructions refer to a "Third Party Software" tab. The tab is labeled "Other Software" on my machine (post Karmic upgrade).

Also, the instructions refer to a [2.3.9 driver]("http://planet76.com/repositories/system76-driver-2.3.9.deb"), but there is now a [2.4.0 driver]("http://planet76.com/repositories/system76-driver-2.4.0.deb") available in the [repository]("http://planet76.com/repositories/").

---

### Post by nadamsieee on 2009-11-16
The System76 Karmic upgrade instructions should probably prefer that the user simply click **System -> Administration -> Update Manager** after they configure their Software Sources. Manually downloading and installing the driver should only be done as a last resort.

---

### Post by thomasaaron on 2009-11-16
Good point. Thanks.

Could you please file a bug on that one at launchpad.net/system76 and i'll make sure it gets fixed.

---

### Post by thomasaaron on 2009-11-17
ATTEN STARLING OWNERS:

We've sent our R&D guy to the Ubuntu Developers Summit, and he will be talking with some developers about getting the Starling's wireless driver permanently fixed and integrated into the kernel.

---

### Post by thomasaaron on 2009-11-18
Starling owners, for further information on a wireless fix for 9.10, please subscribe to...

[http://ubuntuforums.org/showthread.php?t=1330531](http://ubuntuforums.org/showthread.php?t=1330531)

---

### Post by earrame on 2009-11-18
I just upgraded to 9.10. Flawless. This is a really slick distro.

After installing the latest System76 driver, running the restore and doing a reboot this is the only new addition to the software sources:

[http://planet76.com/repositories/](http://planet76.com/repositories/) ./

I don't see the other source that shown in the Karmic upgrade wiki. Is that correct?

---

### Post by thomasaaron on 2009-11-19
You may need to enable the various repositories on the Ubuntu Software and the Updates tabs. (I probably would not enable backports and proposed.)

---

