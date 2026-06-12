---
title: "No sound on Karmic. Any ideas?"
date: 2009-10-30
forum: System76 Support
---

### Post by tomasterisk on 2009-10-30
Does anyone else have this problem with no sound on Karmic? It seems that my options aren't even there, just "dummy output". At the risk of sounding like the "dummy" is there something basic I am overlooking?

Thanks in advance.

---

### Post by tecknomage on 2009-10-30
EXACTLY the same problem I have.
 
"Dummy Output" volume control & if you look at the preferences, there is no hardware listed in the "Hardware" tab.
 
I've tried numerous suggested solutions, but none worked.
 
Here's what's odd. If I open GNOME Mixer, enable the mic, I get a squeal from the speakers on my Notebook. The Grome Mixer is using Realtek ALC227 (?) Audio Codec not a sound card.
 
My on-board sound card is an Intel HD.
 
[SIZE=3]**We both still need a fix :(**[/SIZE]

---

### Post by SlugSlug on 2009-10-30
I've tried 
sudo apt-get remove pulseaudio
and installed esound

sounded better but had not controls in notification area,

I've seen this so will try later / tomorrow..

[http://ubuntuforums.org/showthread.php?t=1306679](http://ubuntuforums.org/showthread.php?t=1306679)

---

### Post by vgrisham on 2009-10-30
Which System76 computers are you guys running? I'm wondering which sound cards it is happening with. I haven't made the plunge with my Pangolin, but I haven't had any sound issues with my non-System76 tower which uses an NVIDIA CK804 onboard sound controller (on an AMD64 ASUS A8N-SLI Deluxe motherboard). Other Karmic bugginess abounds on this box, however.

---

### Post by tomasterisk on 2009-10-30
> **vgrisham said:**
> Which System76 computers are you guys running? I'm wondering which sound cards it is happening with. I haven't made the plunge with my Pangolin, but I haven't had any sound issues with my non-System76 tower which uses an NVIDIA CK804 onboard sound controller (on an AMD64 ASUS A8N-SLI Deluxe motherboard). Other Karmic bugginess abounds on this box, however.

I have a Ratel Value. It had been performing great the last few months in Jaunty. With this upgrade, so far, I have noticed two problems: This one mentioned here and a problem with the  down scroll button in Firefox (which may be strictly a Firefox prob.)

---

### Post by -=hazard=- on 2009-10-30
I have sound problem too, immediately after upgrade. And if I open Alsa Mixer it doesnt recognise the sound card and if I try to open the configure it just crash. [Here the bug report.]("https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/465723")

---

### Post by vgrisham on 2009-10-30
> **tomasterisk said:**
> I have a Ratel Value. It had been performing great the last few months in Jaunty. With this upgrade, so far, I have noticed two problems: This one mentioned here and a problem with the  down scroll button in Firefox (which may be strictly a Firefox prob.)

Do you know which sound card the Ratel uses? If not, pop a terminal and code 'lspci'.

---

### Post by krul on 2009-10-30
I have also problems with pulseaudio in Karmic. Sometimes one of my sound devices disappear in padevchooser. After a reboot it's back again. I have a intel onboard and a SoundBlaster Live

---

### Post by tomasterisk on 2009-10-30
> **vgrisham said:**
> Do you know which sound card the Ratel uses? If not, pop a terminal and code 'lspci'.

OK. I did that just now.This what's under the hood:

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
tom@system76-pc:~$

---

### Post by tomasterisk on 2009-10-30
Having read[ this page]("https://help.ubuntu.com/community/SoundTroubleshooting"), I fired up the terminal as directed and found the following:

"no soundcards found"

Well, now we are getting somewhere (I think).

Any ideas from this point? I obviously *do* have sound card, having listened to music just the previous day.

---

### Post by mcallenSchmee on 2009-10-30
Something went wrong during my upgrade on my Gazelle ultra and I had the same problem, among others. I did a fresh install and the problem is gone now. This command worked for me to fix it before I did a fresh install:```
sudo alsa force-reload
``` It has to be run every time you reboot though, so it is only a temporary fix.

---

### Post by michaelzap on 2009-10-31
I what may be the same problem on my Lenovo Y530 (no sound device reported in the Sound Control Panel, no sound input or output, and random crashes). I removed the proprietary driver for my internal modem (which it turns out is a sub-element of my Intel sound card) and suddenly I had sound and the device is visible in the Sound Control Panel (and so far I've had no more crashes). It's too early for me to be sure that the issue is resolved, but I'm happy not to use my modem if my system will be stable and have sound.

---

### Post by _rex on 2009-10-31
there's another thread on this subject with a lot of help. 

[http://ubuntuforums.org/showthread.php?t=1304710](http://ubuntuforums.org/showthread.php?t=1304710)

i had the same problems with no sound cards being recognized.
mine worked after upgrading grub, then alsa. see thread for an explanation, i'm in no way confident i could get you through what i did.

---

### Post by riseringseeker on 2009-10-31
I had read these posts and heard from Tom that there were quite a few reports of sound problems.  I did a clean install of 9.10 last night on my DU1, and both from the live CD and after the install the sound worked fine, system sounds from the live CD (only thing I tested),  and everything, including Skype after the install.  (Sound doesn't work from the live CD on the Wild Dog I have, but it's update will not be done for a day or so.)

Rebooting this morning after having installed all the additional programs I usually put on, the sound was gone, and like others in this thread I had the "Dummy Output Stereo" list in hardware.

Searching around, I saw a few people removed the hardware driver for the software modem.  I had nothing to lose, and though I was looking forward to finally being able to fax from this little box, since I hadn't had it before, I wouldn't miss it.  (I *have* gotten so I can send faxes from the Wild Dog, but that's fodder for another thread.

I went to System->Administration->Hardware Drivers and removed the driver.  Problem solved (at least for me on this machine.) 

I would suggest that if you enabled the proprietary software modem driver, that be the first attempt to get your sound back.  (and, yes, it works even after a reboot.)

---

### Post by tomasterisk on 2009-10-31
I've tried all the pertinent suggestions here and still no sound.

I'll look into this more,but now I am wondering if I shouldn't just go back to Jaunty and wait till Karmic proves more reliable.

---

### Post by marshmallow1304 on 2009-10-31
Edit: Nevermind; I removed the software modem driver and all is good.  I never should have doubted the mastery of S76 and their driver. :P


----------------------

Is it possible that the S76 driver borked it?  I had sound before I installed the driver and rebooted.

---

### Post by Jeroboam7 on 2009-11-01
I dumped the modem driver and now I have sound as well. Oh well I did not need all those wasted hours anyway.:o

---

### Post by tomasterisk on 2009-11-01
> **riseringseeker said:**
> I had read these posts and heard from Tom that there were quite a few reports of sound problems.

If this is the case this makes me think that  Ubu wasn't quite ready to release their upgrade.

If I wanted to spend the time - which I do not have - on twiddling & tweaking on this new version I would have volunteered to be a beta tester. As it is I don't see any difference than with what Bill Gates does, converting all buyers, de facto, into beta-testers. We are not *buying* here, yes, but we - at least many of us, I have noticed - *are* *spending* time we don't really have.

This is the absolute last time I brag on Ubuntu to people. *There just isn't that much difference* in my experience.

---

### Post by HotShotDJ on 2009-11-01
> **tomasterisk said:**
> If I wanted to spend the time - which I do not have - on twiddling & tweaking on this new version I would have volunteered to be a beta tester...

...This is the absolute last time I brag on Ubuntu to people. *There just isn't that much difference* in my experience.I assure you that I understand your frustration.  At the same time, I don't think your conclusions are entirely fair.  ANY major software upgrades can cause issues, since it is impossible for any software vendor (proprietary or open source) to test for every problem on every possible (and infinity variable) hardware configuration.  For me, Jaunty was a complete disaster on my Dell E1505, but it worked perfectly on my Pangolin Performance (PanP5).

(EDIT)  Actually, perfectly is a strong word.  There was a minor issue regarding the detection of battery discharge and charge rates that persist in Karmic.  But the problem is mostly cosmetic, with the functional problems corrected by switching from time based thresholds to percentage based thresholds in gconf-editor. (end EDIT)

Unlike Microsoft, almost every Linux distribution, including Ubuntu, has the option to test the software via a LiveCD.  By testing your personal hardware this way before doing your upgrades, you can avoid any number of problems.  Also, Ubuntu doesn't force upgrades on its users.  Hardy (8.04 LTS) is still fully supported, as is Intrepid (8.10) and Jaunty (9.04).  If, after testing the LiveCD, a user finds that the new version is problematic, he or she is free to opt out of the new version.

One of the foundational dogmas of software upgrade cycles (and one that is routinely ignored by end-users) is "test, test, test!" before performing any upgrades.  No matter how wonderful a software vendor's testing program and quality assurance, it is impossible for them to guarantee compatibility with all possible hardware configurations.  Ultimately, it is the responsibility of the end-user to make sure any software will work on their hardware before committing the changes to their hard drive.  And, unlike Windows, Linux in general, and Ubuntu specifically, make this testing very easy.

One thing I'd love to see added to the Upgrade Manager in Ubuntu is a simple check box: "Have you tested this upgrade from a LiveCD?" whenever it offers an upgrade to a new version of Ubuntu.  If the user answers "No" then it should present a very scary warning in big red letters that it is unwise to perform the upgrade until the user has tested the new version first.  Of course, because Ubuntu is not a dictatorship, there should be two options in the warning.. "Continue Anyway At Your Own Risk" and "Cancel."

Just my 2 cents. :)

---

### Post by kevin11951 on 2009-11-01
too all having sound problems, please run:
```
sudo alsa force-reload
```

and let me know if it worked...

---

### Post by tomasterisk on 2009-11-01
> **HotShotDJ said:**
> I assure you that I understand your frustration.  At the same time, I don't think your conclusions are entirely fair.  ANY major software upgrades can cause issues,
...

Just my 2 cents. :)

Thanks for the feedback. 

To me, not having sound at all is a core defect. It is a major feature that is missing. And, as I am increasingly discovering, a large number of upgrade users are having this same problem. 

To me an "issue", by comparison, is how the arrow scrolls no longer move down incremently, but continue on down (beyond my control)  to the bottom of the page. 

Oh well.

New question. What is the safest way to reload Jaunty, still keeping my personal data files. Should I just use my 9.04 CD?

Thank you for taking the time to write.

---

### Post by tomasterisk on 2009-11-01
> **kevin11951 said:**
> too all having sound problems, please run:
```
sudo alsa force-reload
```and let me know if it worked...

I tried this also,but to no avail. Thanks anyway.

---

### Post by HotShotDJ on 2009-11-01
> **tomasterisk said:**
> To me, not having sound at all is a core defect. It is a major feature that is missing. And, as I am increasingly discovering, a large number of upgrade users are having this same problem. I agree.  This is a problem that many people are having and needs fixing.  I hope you didn't feel that I was being dismissive of the issue as that certainly was not my intent.
> **tomasterisk said:**
> New question. What is the safest way to reload Jaunty, still keeping my personal data files. Should I just use my 9.04 CD?That is what I would do.  I suggest that you do a full backup of your /home directory:```
sudo rsync -ap  --delete-excluded --delete --progress --stats /home /media/disk/Backup
```Change that last bit (/media/disk/Backup) to match the path to your external drive and the directory you want the backup to go into.  And remember -- after you do the backup, comply with the foundational dogma of "test, test, test!" by going into the backup you just created and make sure everything that is important to you was properly backed up.

Also, if you use evolution, you'll want to back up your settings (in evolution, go to File -> Backup Settings and copy the file it creates to your external drive; after you reinstall, you can just run evolution and point it to that file to restore evolution).

Now you can safely reinstall using the Jaunty CD.  Make sure you reformat your partitions to ext3 -- ext4 has been buggy in Jaunty and IMHO is not worth the risk to your data.

Once you've reinstalled, you can just copy your files back to your home directory.  I usually don't copy most of the hidden files and directories, opting to reconfigure my settings from the fresh install.  This is probably not necessary when upgrading, but when downgrading, I think it is the safest bet.  I do, however, copy my .mozilla folder to retain my firefox settings.

Of course, don't forget to install the System76 Driver and run restore.

Let me know if you need any further help with this.

---

### Post by keyrunner on 2009-11-01
sudo alsa force-reload

This suggestion worked for me -- ATI IXP SB4x0 sound card.  Now how do I make it permanent?

---

### Post by riseringseeker on 2009-11-02
> **tomasterisk said:**
> I tried this also,but to no avail. Thanks anyway.

I feel your pain.  I spent all day Friday trying to get 9.10 installed and running decently on a Asus 900 netbook we have.  Sound wasn't the issue there, but responsiveness.  I finally took it back to 9.04.

That said, most reports of installs (including on Asus netbooks) have been nothing short of glowing.  It'll get better for me as well, I am sure, and I may try again at a future date.

I don't know if you've ever done a windows install from scratch, but I have done so several times.  Even with the problems I am having on the netbook, it went as well or better than a couple of those windows installs.  

I guarantee, if System76 had installed 9.10 for you, everything would work on the Starling.  Tom tells me they are not seeing the same problems that **some** users are having on the ones they have in house.  This makes it more difficult for them to troubleshoot the problem, but I also know they are working hard on fixing whatever problem crops up.  I never meant to imply this is a huge problem, just that there have been reports by some users - but given how many machines they have out it is a minority.

This does not mean that having no sound is not a huge problem for **you** and I don't think anyone is arguing that your not having sound is a big deal for you.  It would be for me as well, as I use skype constantly to stay in touch with friends and family as I travel all over the world.

Having downgraded myself, I would give a +1 to HotShotDJs recommendations.  I always back up using rsync, a really neat tool - it can be done to a remote site even!  

I use slighty different command line arguments than he does (-avv instead of -ap) as I believe the "a" includes the "p" and I want to see more of what it's doing (the "vv" portion).

If you have installed a number of apps not included with a fresh install, I would recommend you get a list of all installed programs as well.  I find myself adding programs for time to time during a release cycle, and often forget about them until I need them again.  Having a list is handy, you can just read through and remind yourself what you installed.  You can get a list with this command:
```

dpkg --get-selections | grep -v deinstall >> <path you want it on>/installed-packages.txt
```

Again, I am sorry you are having troubles.  If there is anything we as a community can do to help - well, if you've been in the forums for a while, you know there are very helpful and knowledgeable people willing to help out most anyone.

---

### Post by Eyore15 on 2009-11-02
> **riseringseeker said:**
> I feel your pain.  I spent all day Friday trying to get 9.10 installed and running decently on a Asus 900 netbook we have.  Sound wasn't the issue there, but responsiveness.  I finally took it back to 9.04.

How do you go "backwards";  all I can find is how to download an older version and do an install.  I just want to do a "downgrade' and keep everything else the way that it is.

TIA

mcm

---

### Post by jpongin on 2009-11-02
I have the same problem.  No sound after the Karmic upgrade.  No hardware was detected.

My rig: Serval, 4GB, Quadecore Q9000, 1920x1200

Tried forcing the reload on the drivers like so as mentioned in previous posts:
```
sudo alsa force-reload
```

This worked for me, but like many others it's a temporary fix.  

Where are the System76 support reps with the official permanent solution?

---

### Post by destmars on 2009-11-02
I had to disable the software modem from the System -> Admin -> hardware drivers utility.

Updated my alsa drivers, libs, utils following the steps listed in the below link.

[http://ubuntuforums.org/showthread.php?t=1292587](http://ubuntuforums.org/showthread.php?t=1292587)

I had tried the steps from here first, [https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63), and discovered I was missing xmlto.  The steps here are similar to the above link with check for xmlto as well.

This worked for me on a hp tx 2000 tablet pc.

---

### Post by jdb on 2009-11-02
> **Eyore15 said:**
> How do you go "backwards";  all I can find is how to download an older version and do an install.  I just want to do a "downgrade' and keep everything else the way that it is.

TIA

mcm

The best way to go backwards is to restore a backup from before the upgrade.

jdb

---

### Post by tecknomage on 2009-11-02
Found cause of no sound with Ubuntu 9.10 installed.

There are 2 symtoms:


[LIST=1]
[*]No sound even though sound card drivers are correctly installed
[*]The **Volume Control** tool-tip says "**Dummy Output**"
[/LIST]
Under **System, Administration, Hardware Drivers**, see if there is a _Modem driver_ installed.

Remove this driver, reboot, and see if your sound is back :D

The **Volume Control** tool-tip should say something like "**Internal Audio Analog Sterio**."

---

### Post by tomasterisk on 2009-11-02
> **tecknomage said:**
> Found cause of no sound with Ubuntu 9.10 installed.

There are 2 symtoms:


[LIST=1]
[*]No sound even though sound card drivers are correctly installed
[*]The **Volume Control** tool-tip says "**Dummy Output**"
[/LIST]
Under **System, Administration, Hardware Drivers**, see if there is a _Modem driver_ installed.

Remove this driver, reboot, and see if your sound is back :D

The **Volume Control** tool-tip should say something like "**Internal Audio Analog Sterio**."

In my case there is no modem driver to remove. There is nothing to remove- according to that dialog box.

---

### Post by thomasaaron on 2009-11-03
Hi, Tom.

I responded to your other post.

---

### Post by tomasterisk on 2009-11-03
> **thomasaaron said:**
> Hi, Tom.

I responded to your other post.

Thanks anyway, Tom, but I decided to just go back to Jaunty. I'll wait until the next stable version comes out.

---

### Post by jdb on 2009-11-03
> **tomasterisk said:**
> Thanks anyway, Tom, but I decided to just go back to Jaunty. I'll wait until the next stable version comes out.

Sometimes waiting a few months before upgrading saves a few headaches.

jdb

---

### Post by tomasterisk on 2009-11-04
> **jdb said:**
> Sometimes waiting a few months before upgrading saves a few headaches.

jdb
Yes indeed. 

Now I am back to very frequent window freezes. Any ideas? I have windoweffects turned off.

---

### Post by Eyore15 on 2009-11-04
> **tecknomage said:**
> Found cause of no sound with Ubuntu 9.10 installed.

There are 2 symtoms:


[LIST=1]
[*]No sound even though sound card drivers are correctly installed
[*]The **Volume Control** tool-tip says "**Dummy Output**"
[/LIST]
Under **System, Administration, Hardware Drivers**, see if there is a _Modem driver_ installed.

Remove this driver, reboot, and see if your sound is back :D

The **Volume Control** tool-tip should say something like "**Internal Audio Analog Sterio**."

What's the recommendation when there is no hardware driver loaded, nothing about a modem.l or any other kind.

---

### Post by jdb on 2009-11-04
> **tomasterisk said:**
> Yes indeed. 

Now I am back to very frequent window freezes. Any ideas? I have windoweffects turned off.
If you have another computer you can use it to ssh into the offending one.
If you're not familiar with ssh you can google "tutorial ssh".
Then when the offending one freezes you can do a
```
ps -ef

```
to see whats running and then run
```
top
```
to see if anything is hogging the cpu.
You can use the man command to learn about these commands:
```
man ps
man top
man ssh
```

jdb

---

### Post by tomasterisk on 2009-11-04
> **jdb said:**
> If you have another computer you can use it to ssh into the offending one.
If you're not familiar with ssh you can google "tutorial ssh".
Then when the offending one freezes you can do a
```
ps -ef

```to see whats running and then run
```
top
```to see if anything is hogging the cpu.
You can use the man command to learn about these commands:
```
man ps
man top
man ssh
```jdb
OK. Thanks. Will give that a try.

---

### Post by tc7 on 2009-11-05
I attempted to remove the Software Modem from Admin --> Hardware Drivers.
It took some time (5min), and now (going back into Hardware Drivers) I notice the green indicator is back on - so the uninstall failed.

However I found:
sudo alsa force-reload

Did the trick. I now have an Internal Audio device (hardware tab of Sound Preferences).

Sound now works better than Jaunty. I no-longer have to manually switch the internal speakers on/off (I think this was peculiar to my laptop HW). The mixer now allows volume control per (running) application which is pretty cool. And I can increase volume beyond 100% - which is great if you happen to have a quiet sound source.

The major upgrade issue I faced was the new kernel not being added to the boot menu (so I was running kernel 2.6.28-16 rather than 2.6.31-14). This caused a few weird side effects such as SHMConfig wouldn't load - no synaptics mouse pad (external mouse only). I also had trouble with a bluetooth keyboard (Logitech) - it would pair successfully, just wouldn't work at all.

Now Karmic 64 is working reasonably on my MSIGX620 laptop (although I haven't tested Skype properly / VMWare Player 3 yet).

---

### Post by joris1977 on 2009-11-08
No sound, removed the modem under hardware drivers and sound is there after reboot. 

Unbelievable thanks for the advice! :popcorn:

Is there a bugreport of this already?

Oh this is with:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by Eyore15 on 2009-11-08
> **tc7 said:**
> I attempted to remove the Software Modem from Admin --> Hardware Drivers.
It took some time (5min), and now (going back into Hardware Drivers) I notice the green indicator is back on - so the uninstall failed.

However I found:
sudo alsa force-reload

Did the trick. I now have an Internal Audio device (hardware tab of Sound Preferences).

Sound now works better than Jaunty. I no-longer have to manually switch the internal speakers on/off (I think this was peculiar to my laptop HW). The mixer now allows volume control per (running) application which is pretty cool. And I can increase volume beyond 100% - which is great if you happen to have a quiet sound source.

The major upgrade issue I faced was the new kernel not being added to the boot menu (so I was running kernel 2.6.28-16 rather than 2.6.31-14). This caused a few weird side effects such as SHMConfig wouldn't load - no synaptics mouse pad (external mouse only). I also had trouble with a bluetooth keyboard (Logitech) - it would pair successfully, just wouldn't work at all.

Now Karmic 64 is working reasonably on my MSIGX620 laptop (although I haven't tested Skype properly / VMWare Player 3 yet).

I tied this "sudo" command; didn't get any audio although I do have a sound >> preferences >>hardware entry now.

This is getting really frustrating.

---

### Post by riseringseeker on 2009-11-09
> **Eyore15 said:**
> I tied this "sudo" command; didn't get any audio although I do have a sound >> preferences >>hardware entry now.

This is getting really frustrating.

I don't know why they are not installed with ubuntu by default, but you might want to add a couple of controls for pulse, esp if you want to change where the audio goes and comes from from app to app.

sudo apt-get install padevchooser pavucontrol

The first allows you to change what application uses what audio (though on Skype you cannot have the ringer over the speakers and the conversation through a headset, at least not yet), and the second controls the volume for each app.

There is one more I haven't have a chance to play with yet, "paprefs" which should give the ability to stream audio from one machine to an other.

---

### Post by PeterJamesRye on 2009-11-09
I installed 9.10 today, also no sound.  Then I checked Sound Preferences (System -> Preferences -> Sound under the Gnome desktop menu), and found the installation had set the sound volume setting to "Mute".  - pretty simple to fix, but a pretty dumb thing for the upgrade installation to do!

---

### Post by ravenax on 2009-11-17
The new kernel(2.6.31) gave me a black screen('cause of intel chipset... grr) with karmic so I had to login using a lower version(2.6.30) :( sound and desktop effects din seem to work with that. I can be without desktop effects but can't be without SOUND. So after a bit of searching I found this thread and found [this]("http://ubuntuforums.org/showthread.php?t=1306679") and did as told by *ghost*.

Then I tried the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and the output I got from the first step was - NO SOUNDCARD. But then I proceeded with the steps anyway and they installed the kernel image 2.6.31 - with which I had trouble earlier(kept getting a dumb black screen), but still i installed it(again)!! A restart window popped up but I gave "restart later".

After that i found [this]("http://ubuntuforums.org/showthread.php?t=1304727&page=2") thread and did as told by *tim.hamels* in reply #14.

then...

restarted -> got a login screen instead of a black one -> me:D -> opened gnome alsamixer -> unmuted and increased the volume -> SOUND!!:guitar::guitar:

well.... that was what worked for me!! (don't know what all steps to omit n all but, I got karmic working beautifully after aallllll this)

anyway hope this helps!

---

### Post by vgrisham on 2010-02-19
Oy vey. Now I'm getting this "dummy hardware" problem. There is no modem driver installed (at least it's not listed under Hardware Drivers). 

Thomas, et. al, what is the offending modem driver called in Synaptic? My laptop is a Pangolin Pan4pn.

---

### Post by vgrisham on 2010-02-19
I think I found it. I uninstalled a file called "modemmanager" through Synaptic, rebooted and now have sound. 

I'm wondering why this popped up now, two months after finally installing the ironically named Karmic?

---

### Post by thomasaaron on 2010-02-19
I just ran into this last night trying to configure a US Robotics dial-up modem dongle.

The modem wasn't recognized until I removed modemmanager.

If you go to System > Administration > Hardware Drivers and disable the "Modem Software" driver, that restores sound. I *think* that is modemmanager.

---

### Post by vgrisham on 2010-02-19
So far, deleting modemmanager via Synaptic has solved the problem. The odd thing is that the modem driver has never appeared under Hardware Drivers.

---

### Post by bro brian on 2010-02-19
> **thomasaaron said:**
> I just ran into this last night trying to configure a US Robotics dial-up modem dongle.

The modem wasn't recognized until I removed modemmanager.

If you go to System > Administration > Hardware Drivers and disable the "Modem Software" driver, that restores sound. I *think* that is modemmanager.
[COLOR=DarkRed]**That was it! That worked. Whew!**[COLOR=Black]
  Thanks, Tom. The only thing I would change in your instructions; Where you said, "disable the Modem Software", actually it would be (at least with mine) Highlight "Software Modem" and click the "Remove" tab. This disables the Software Modem.
  The only reason I brought this up is because I kept looking for a "Disable" prompt, but it wasn't there. I finally had to just man up, and click the "Remove" tab. It actually didn't "remove" Software Modem, but disabled it.
[/COLOR][/COLOR]

---

### Post by vgrisham on 2010-02-22
The problem persists. Despite having removed the modem driver, I get no sound unless I force a restart of ALSA on every login. There's just no end to the joy with Karmic. I sure hope Lucid squashes all of Karmic's bugginess. I used to love Ubuntu, but I'm getting seriously tired of the effort needed to get through basic things without repeatedly having to resolve problems (flash, alsa, pulseaudio). Sorry for venting. Back on topic...

Anybody know why ALSA needs to be restarted every time I boot up in order to have sound?

---

### Post by thomasaaron on 2010-02-22
Not off the top of my head. But you can go to System > Prefs > Startup Applications and create a start-up command to start ALSA when you log in.

---

### Post by vgrisham on 2010-02-22
Will that work with a root command? sudo alsa force-reload?

---

### Post by vgrisham on 2010-02-22
I created a startup item, alsa force-reload (without the sudo), rebooted, and I have sound. Thanks.

---

### Post by vgrisham on 2010-02-23
Nevermind. That doesn't work. I still have dummy sound until I force an ALSA restart.

---

### Post by thomasaaron on 2010-02-23
What does dummy sound mean?

Try using "start" instead of "force-reload".

---

### Post by vgrisham on 2010-03-17
I've been running Lucid Lynx for the past four days on my Pangolin. It's quicker than Karmic, quieter (less fan noise) and the battery life seems longer (which I guess comes from less fan use). 

On the downside, the modemmanager/sound conflict persists in Lucid. I was about to file a bug against modemmanager, but I'm not sure 1. if that's the package to file against or 2. if any of you on this thread have already filed a bug. I'd be interested in feedback on this.

---

### Post by vgrisham on 2010-03-18
I *think* [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500?comments=all") is our bug.

---

### Post by thomasaaron on 2010-03-18
Had you not removed modemmanager, I *think* you would have found an item called "Modem Software" in Hardware Drivers. And if you would have disabled it, that would've fixed sound.

We first started noticing this after the upgrade from 9.04 to 9.10. I think Ubuntu is noticing the phone jack and automatically applying that driver. 

Modem software depends on ALSA and has a history of screwing up sound.

---

### Post by speedkreature on 2010-03-19
I'm searching for the solution I used currently.  It involved using ALSA back-ports to alter the way ALSA and PulseAudio communicate.  No startup scripts are required...though for some time I did use the method that has been suggested here.

I have a Pangolin, by the way, but the work around I'm using resolved the lack of sound for several Intel HDA bugs posted in Launchpad.  Unfortunately, Launchpad has become inundated with bugs on this and related issues so it is very difficult to track.

Unfortunately, this method is not supported and will be lost when/if you upgrade to Lucid.

Now if I could just find that blasted blog posting...

---

### Post by speedkreature on 2010-03-19
This isn't the exact posting I found previously, but I believe the procedure is the same.

[http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala](http://www.unixmen.com/linux-tutorials/525-resolve-nosound-problem-on-ubuntu910-karmic-koala)

I should have been a good community member and posted the solution when I found it. :(

---

### Post by edc80 on 2010-03-28
I'm no Ubuntu expert, but I've had this problem twice, once when upgrading from 8.04 to Karmic 9.10, and again today when downgrading to Jaunty 9.04 (for other reasons).  Both times, the root cause was the same.

Here's how I got my sound back (and it stayed):

1: Left click on the speaker icon that's in the upper right corner of my screen.

2: In the little window that opens up, left click "Volume Control".

3: In the volume control box, left click "Preferences" and add a check-mark to every single thing on the list that shows up, then close that little pop-up box.

4: Go across the tabs in the open Volume Control box and click on "Switches."

5: Remove the check-mark from "External Amplifier."

6: Close all open boxes.

I'm not sure why this works, but it has worked twice now, so I thought I should share it.

With thanks,
-Ed.

---
To Jesus through Mary

---

### Post by thomasaaron on 2010-03-29
Yeah, for some weird reason, Ubuntu decides it's best to automatically activate a connection to an external amplifier. That one has been around for a while.

The only one of our systems I've seen this bug on is the older Gazelles.

---

### Post by sullam on 2010-04-02
This isn't working. I have it set to maximize window and it still does the default which is rollup and unrollup.

---

### Post by listerdl on 2010-04-03
I like you all have the same no sound issue.

A previous post mentioned to disable the Modem Software Driver. When I try and do this I get a message that says "no proprietary drives are in use on this system."

Is that bad you reckon?

---

### Post by thomasaaron on 2010-04-05
listerdl, what System76 computer are you using?

---

