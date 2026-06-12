---
title: "QQ Install &amp; Setup Notes"
date: 2012-06-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by buzzingrobot on 2012-06-10
Well, sometimes you just get bored with things "just working".  It's that kind of day here, so I burned a QQ Alpha 1 64-bit ISO, swapped in my PS/2 keyboard and swapped out my Marble Mouse,  and jumped into the install. 

I use an Nvidia 550ti card, which requires special kernel option magic to boot with a 3.2/3.3 kernel. That also applies to install images.  So, I wanted to see if the install ISO would boot "as is" with its 3.4 kernel..  The answer:  Yes.  (Good!  Getting into the Grub menu and adding options until I could install the Nvidia driver was a pain.)

The machine has multiple disks so I opt for manual partitioning. (Someday partitioners will offer to do something useful with multiple disks.) The current boot disk is /dev/sda, but the partitioner picks /dev/sdb.  That's been a frequent occurrence during installs. Change it back to /dev/sda, an SSD.

Watching the install now.  Usual color scheme of black and purplish-orange. (Shuttleworth's favorites?)

Hmm, in the 'Any Questions" part of the slideshow, seeing blocks and random patterns instead of text.  Fonts missing?

No problems on first reboot.

Click "Additional Drivers" to install Nvidia.  It says no proprietary drivers in use. It's using the "nvidia Riva/TNT/GeForce" driver. Nouveau, huh? Several other non-video drivers are also listed.  That's new.  I tell it to activate the post-release Nvidia driver.  It says I'm not authorized.  Hmmm. First time in a while I can use Nouveau, tho.

sudo apt-get update, sudo apt-get upgrade. Lots of Gnome 3.5.2 stuff going in. Reboot.

Back in Additional Drivers. Ah, it prompts me for a password this time. Nvidia install seems to work.  Reboot. a check shows its using the Nvidia driver, but Additional Driver still show all the other drivers activated.

"Details" does not identify the Nvidia card.  Calls it 'Unknown".  It always has.  Wants me to "Install Updates".  I click.  It says "Not all Updates Can Be Installed".  I go ahead with a "Partial Upgrade". It complains something else has got the lock.  Wait a minute.  Click again.  Now it's happy. Shows me estimated download and install times.  That's nice. 

The "Partial Update" completes successfully.  Still shows "Install Updates".  Click that and it says I'm up to date. So does "apt-get update". (It reports a 404 on packages from extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources and the "binary/i-386" directory of same.)

"System Settings" seems to crash (disappears) when I click "Displays". (I use a Dell U2410.  Ubuntu always identifies it as a "laptop".)  Restart "Systems Setting". Nothing else in the panel will open.  Doesn't disappear, but does rearranges icons. Can't quit it, either.  Log off. Reopen "Systems Settings".  Same behavior when I click "Display" but I can quit it. Other settings work as usual.

Printer setup is the exception, as usual.  I have an HP 1102w, which wants the HP proprietary driver. Printer setup happily installs a Foomatic PPD, but it won't work.  So, open Software Center and install the "HPLIP Toolbox".  HPLIP is already installed. Try to run the toolbox and let it download the right HP driver. Looks like it crashed. Lots of white boxes on screen.  Not responding to the mouse. Open a console and reboot. Open HP Toolbox.  Crashes again. Another reboot.

Open a terminal and run "hp-setup".  It downloads the driver install file and then says that failed.  Been there, done that. It's lying.  Sure the "run" file is here somewhere but can't find it. Kill crashed hp-setup from System Monitor.

hp-check says I need to be in group "lp". Add myself.  hp-setup crashes.  Reboot.

hp-setup now crashes every time.  Doesn't actually take the system down, but everything is very, very, slow.  Reboot and I'll wait till this is fixed. Printers are evil.

Install Dropbox from Software Center. As in 12.04, it complains it's installed in an "unsupported location".  Remove it and go to Dropbox site and install from there.

Add the Dell's ICC profile, which is stored in Dropbox.  Move over and add my favorite wallpaper.

Install ubuntu-restricted-extras. ttf-microsoft-installer stalls downloading files from sourceforge.Try again. Works.  Why are kdelibs, kde-runtime, etc., installed?

I'm sure versions are out of synch and this is foolish, but I try to install "gnome".  Yep. Doesn't work. epiphany-extensions is the wrong version.

That's enough for now.  Going outside.

---

### Post by balloons on 2012-06-11
> **buzzingrobot said:**
> Well, sometimes you just get bored with things "just working".  It's that kind of day here, so I burned a QQ Alpha 1 64-bit ISO, swapped in my PS/2 keyboard and swapped out my Marble Mouse,  and jumped into the install. 

I use an Nvidia 550ti card, which requires special kernel option magic to boot with a 3.2/3.3 kernel. That also applies to install images.  So, I wanted to see if the install ISO would boot "as is" with its 3.4 kernel..  The answer:  Yes.  (Good!  Getting into the Grub menu and adding options until I could install the Nvidia driver was a pain.)

The machine has multiple disks so I opt for manual partitioning. (Someday partitioners will offer to do something useful with multiple disks.) The current boot disk is /dev/sda, but the partitioner picks /dev/sdb.  That's been a frequent occurrence during installs. Change it back to /dev/sda, an SSD.

Watching the install now.  Usual color scheme of black and purplish-orange. (Shuttleworth's favorites?)

Hmm, in the 'Any Questions" part of the slideshow, seeing blocks and random patterns instead of text.  Fonts missing?

No problems on first reboot.

Click "Additional Drivers" to install Nvidia.  It says no proprietary drivers in use. It's using the "nvidia Riva/TNT/GeForce" driver. Nouveau, huh? Several other non-video drivers are also listed.  That's new.  I tell it to activate the post-release Nvidia driver.  It says I'm not authorized.  Hmmm. First time in a while I can use Nouveau, tho.

sudo apt-get update, sudo apt-get upgrade. Lots of Gnome 3.5.2 stuff going in. Reboot.

Back in Additional Drivers. Ah, it prompts me for a password this time. Nvidia install seems to work.  Reboot. a check shows its using the Nvidia driver, but Additional Driver still show all the other drivers activated.

"Details" does not identify the Nvidia card.  Calls it 'Unknown".  It always has.  Wants me to "Install Updates".  I click.  It says "Not all Updates Can Be Installed".  I go ahead with a "Partial Upgrade". It complains something else has got the lock.  Wait a minute.  Click again.  Now it's happy. Shows me estimated download and install times.  That's nice. 

The "Partial Update" completes successfully.  Still shows "Install Updates".  Click that and it says I'm up to date. So does "apt-get update". (It reports a 404 on packages from extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources and the "binary/i-386" directory of same.)

"System Settings" seems to crash (disappears) when I click "Displays". (I use a Dell U2410.  Ubuntu always identifies it as a "laptop".)  Restart "Systems Setting". Nothing else in the panel will open.  Doesn't disappear, but does rearranges icons. Can't quit it, either.  Log off. Reopen "Systems Settings".  Same behavior when I click "Display" but I can quit it. Other settings work as usual.

Printer setup is the exception, as usual.  I have an HP 1102w, which wants the HP proprietary driver. Printer setup happily installs a Foomatic PPD, but it won't work.  So, open Software Center and install the "HPLIP Toolbox".  HPLIP is already installed. Try to run the toolbox and let it download the right HP driver. Looks like it crashed. Lots of white boxes on screen.  Not responding to the mouse. Open a console and reboot. Open HP Toolbox.  Crashes again. Another reboot.

Open a terminal and run "hp-setup".  It downloads the driver install file and then says that failed.  Been there, done that. It's lying.  Sure the "run" file is here somewhere but can't find it. Kill crashed hp-setup from System Monitor.

hp-check says I need to be in group "lp". Add myself.  hp-setup crashes.  Reboot.

hp-setup now crashes every time.  Doesn't actually take the system down, but everything is very, very, slow.  Reboot and I'll wait till this is fixed. Printers are evil.

Install Dropbox from Software Center. As in 12.04, it complains it's installed in an "unsupported location".  Remove it and go to Dropbox site and install from there.

Add the Dell's ICC profile, which is stored in Dropbox.  Move over and add my favorite wallpaper.

Install ubuntu-restricted-extras. ttf-microsoft-installer stalls downloading files from sourceforge.Try again. Works.  Why are kdelibs, kde-runtime, etc., installed?

I'm sure versions are out of synch and this is foolish, but I try to install "gnome".  Yep. Doesn't work. epiphany-extensions is the wrong version.

That's enough for now.  Going outside.

Fun stuff! Thanks for your willingness to encounter breakage and help out! First, I would ask you to report your installation on the iso tracker -- here's a wiki on how-to do it. Ask questions if needed:

[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

Second, let's talk about them bugs! I can report I had the same displays bug in the control center -- it's reported here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1010537](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1010537)

The other bugs should get some bug reports. Utilize ubuntu-bug PACKAGENAME and file them! Sadly devs are not yet mind readers and may or may not know about all the brokenness you experienced. Sucks, I know. The good news is that I've historically had pretty good success on the nasty bugs I experience and care about provided I follow up on the bug report as needed.

Dev releases are fun aren't they? \\:D/

---

### Post by buzzingrobot on 2012-06-11
Thanks. I moved some things around and reinstalled, setting 12.10 on its own drive to dual boot with 12.04. I'll get an account and go from there.

---

