---
title: "Share with us your Xenial (16.04) Upgrade and Installation Experiences"
date: 2016-04-21
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2016-04-21
It's that time again, Xenial (16.04) was released April 21, 2016 Please tell us about your experience upgrading, or doing a fresh install of Xenial Xerus.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

Poll and thread for the previous release:

[http://ubuntuforums.org/showthread.php?t=2300286](http://ubuntuforums.org/showthread.php?t=2300286)

---

### Post by SantaFe on 2016-04-21
First! ;)

Hehehe had to do that.  In my case it worked better than I hoped for.  A week ago, I made the mistake of trying the propitiatory AMD drivers in my Ubuntu-MATE 15.10, which while they worked, it messed it up so I couldn't go back to the open source drivers (unless I liked 1400x1050 screen res & no HDMI audio).  Not only did the upgrade work flawlessly, it fixed the video problem so it's back 100%.  ;)

---

### Post by Irihapeti on 2016-04-21
Install is so easy these days, I have to be careful not to go to sleep while doing it.

---

### Post by fyfe54 on 2016-04-21
Uneventfully upgraded to 16.04 beta about 3 weeks ago and have been installing updates at least daily since then.  Uneventful all the way.

---

### Post by sammiev on 2016-04-21
It was boring with no errors. :(

Please bring on 16.10! :P

---

### Post by tom-bellas3rd on 2016-04-22
Fresh install was flawless. Has there been any updates since yesterday? Usually even though its a brand new version, one or two updates are awaiting. Even a fresh 
install. Anyone have any?

---

### Post by vasa1 on 2016-04-22
> **tom-bellas3rd said:**
> Fresh install was flawless. Has there been any updates since yesterday? Usually even though its a brand new version, one or two updates are awaiting. Even a fresh 
install. Anyone have any?
I'm aware of```
Start-Date: 2016-04-21  05:07:33
Commandline: apt-get dist-upgrade
Requested-By: vasa1 (1000)
Upgrade: cups-filters:amd64 (1.8.3-2ubuntu2, 1.8.3-2ubuntu3), libcupsfilters1:amd64 (1.8.3-2ubuntu2, 1.8.3-2ubuntu3), libfontembed1:amd64 (1.8.3-2ubuntu2, 1.8.3-2ubuntu3), cups-filters-core-drivers:amd64 (1.8.3-2ubuntu2, 1.8.3-2ubuntu3), tzdata:amd64 (2016c-1, 2016d-0ubuntu0.16.04)
End-Date: 2016-04-21  05:07:57

```Depending on when you grabbed your iso, you may already have those updates.

On topic, I upgraded this time. Smooth. The upgrade replaced some of the software I had via ppas if the repos had the same version: conky and geany come to mind.

---

### Post by kerk12gr on 2016-04-22
Hey guys,

The installation was a breeze (as always ;) ), however, right after login unity wouldn't start and compiz kept crashing. It was my GTX 980 driver... After running ```
sudo apt-get install nvidia-361
``` (it's the latest nvidia driver at the time of posting this) and after a reboot, it started up fine.

Now I'm pretty much enjoying it :D.

---

### Post by neutron3 on 2016-04-22
Having a hard time to create USB install sticks from Ubuntu and I don't have any Apple or Windows machines.

Now trying from a 12.04 box.... 
USB Disk Creator, Unetbootin, dd, mkusb,  what else is out there to create an USB install stick (**from within Ubuntu?**)

---

### Post by Frogs Hair on 2016-04-22
Clean installation still in use from beta one . I see no reason to reinstall so far, but probably will after a few weeks.

---

### Post by sammiev on 2016-04-22
> **Frogs Hair said:**
> Clean installation still in use from beta one . I see no reason to reinstall so far, but probably will after a few weeks.

I hear you, but must add that my boot time improved greatly by doing a fresh install.

Boot times are only a few seconds now on Xubuntu and Gnome on my SSD.

---

### Post by markf2 on 2016-04-22
I installed Lubuntu 16.04 (deleting 15.11) and the process seemed less polished than I'm accustomed to the past 4-5 years.

I started a thread [here]("http://ubuntuforums.org/showthread.php?t=2321441&p=13474820#post13474820"), not knowing this thread existed. Just wanted to chime in here.

Basically, 

1. I used unetbootin to create a bootable image of 16.04 on a USB pen drive. 
2. Chose install from GRUB
3. The install dialog did not give me an option to connect to wifi; the "download while installing" option was grayed out; the installed system (when rebooted) presented me with some confusing dialogues about how some stuff still needed to be done. It wasn't a continuation of the install wizard. This was 2002-era stuff that had me unnerved, wondering what went wrong. I assume it was due to not "downloading while installing."

There was also an *enormous* delay between the screen where "download while installing" was grayed out, and the next screen (where it asked me if I wanted to upgrade, or delete and install 16.04 anew.). I often get an annoyingly long delay during booting (since maybe 15.04). But, not that long. If I hadn't already been accustomed to being patient, I don't think I would have waited as long as it took. 

This is a Toshiba C55-B5299 laptop (cheap, year old). I'm happy to provide any details if it will help.

My concern is that Win 10 users are increasingly frustrated with MS's direction (and increasingly willing to try Linux). After my experience with 16.04, I'm less inclined to throw fuel on that fire. That disappoints me because I delight in throwing that fuel on that fire. :)

I regret I didn't contribute some testing before release.

---

### Post by oldrocker99 on 2016-04-22
Installed Ubuntu MATE beta 1 and have had zero problems=d>. **Lots** of updates, but that's how I like it:wink:

---

### Post by cariboo on 2016-04-22
I did a clean Ubuntu install in order to upgrade to Yakkety, UEFI seems to be giving me problems. On trying to install nvidia-340 I had to create a password, and when I got to the login screen it went into a loop. After purging nvidia-340 unity didn't start and there was no launcher or dash. Enabling the compiz unity plugin brought me to a working desktop.

Now on rebooting I get a screen asking me to edit the shim. I'm going to have to investigate this a little further to see if I can solve UEFI problems.

---

### Post by Tanker Bob on 2016-04-22
I upgraded from 15.10 with no problems. My NVidia driver updated correctly and VMWare Workstation 12 even still works. One of the smoothest upgrades ever for me.

---

### Post by cariboo on 2016-04-23
> **cariboo said:**
> I did a clean Ubuntu install in order to upgrade to Yakkety, UEFI seems to be giving me problems. On trying to install nvidia-340 I had to create a password, and when I got to the login screen it went into a loop. After purging nvidia-340 unity didn't start and there was no launcher or dash. Enabling the compiz unity plugin brought me to a working desktop.

Now on rebooting I get a screen asking me to edit the shim. I'm going to have to investigate this a little further to see if I can solve UEFI problems.

After also not being able to install Virtual Box also, I just disabled secure boot in the bios.

---

### Post by wanderer3 on 2016-04-23
I had trouble with creating boot disks. It took repeated attempts at reformatting with gparted and then using the erase disk option in disk creator. Not sure exactly how but eventually managed to create boot boot disks for kubuntu and Ubuntu.

---

### Post by cariboo on 2016-04-23
> **wanderer3 said:**
> I had trouble with creating boot disks. It took repeated attempts at reformatting with gparted and then using the erase disk option in disk creator. Not sure exactly how but eventually managed to create boot boot disks for kubuntu and Ubuntu.

I use Disks with the Restore Disk Image option.

---

### Post by dom134 on 2016-04-23
My upgrade from 14.04 failed and left my computer unable to boot.  Thankfully my root and home are on separate partitions so I just did a fresh install of 16.04.  The OS is working fine now, although the following cannot be installed yet:
[LIST]
[*]Virtualbox 
[*]Jitsi 
[*]Turtlesport (for cycling) 
[*]Bellepoule (for fencing) 
[/LIST]
I am sure these will all come soon

---

### Post by bretcb on 2016-04-24
I upgraded from 15.10, and mysql 5.7 broke.

EDIT: Maheriano had already posted the solution which worked for me; I should have searched first.  [This post]("http://ubuntuforums.org/showthread.php?t=2321413&p=13475037#post13475037") resolved the issue.

---

### Post by yoshii on 2016-04-25
JUNE 2016 EDIT:  This is no longer up to date.  See my updated post later in this thread.  

In summary, I am one of the unlucky AMD Radeon 7 GPU users.  I think it's because of this that the LiveDVD would only boot into a seemingly unresponsive black screen (and the monitor would put itself to sleep with no input).  Luckily, I was later able to enable "nomodeset" at all three necessary stages to get a working installed system (without video hardware acceleration though).  The three stages were:  

1) "expert" & "nomodeset" enabled via F6 at the LiveDVD boot after choosing English as the language.  "---" needed to be deleted from the boot prompt also, yet leaving the spaces remaining!  I also chose to delete "splash" and maybe "quiet".  I can't remember for sure now.  This gets the LiveDVD mode to run without the screen going black.  This way the installation is possible.  

2) After ejecting the LiveDVD, and booting the computer, press SHIFT to get to the GRUB menu.  Add "nomodeset" to the boot string. (explained in detail elsewhere).  Pressed Ctrl-X (or F10) to continue booting.  This makes the screen visible during the whole computer use session.  

3) And finally, sudo mousepad /etc/default/grub   ...to use MousePad to edit grub...  "nomodeset" added to the linux kernel boot options.  sudo update-grub after that to make the changes stick.  (details explained in the link).  

Here are the details of my installation experience:   [http://ubuntuforums.org/showthread.php?t=2322014&p=13477330#post13477330](http://ubuntuforums.org/showthread.php?t=2322014&p=13477330#post13477330)

Overall, the experience was bothersome at first, but then turned out OK.  Because I read the release notes, I knew to turn my SWAP partition off (swapoff) using gParted before running the installer.  So that wasn't a problem.  Really the only problem was the monitor/GPU/graphics driver issue, but luckily as explained above, it was surmountable.  After that, the install was reasonable.  

I didn't like how the installer chose to install into a tiny bit of free space I had for it's coexistant install with my Ubuntu Studio 14.04.3 LTS OS.  I had prepared an empty ext3 partition for it to use, but the installer just ignored it.  So I used gParted to delete everything I didn't want and started again.  It's a bit more complex than that, because I chose to move some partitions around and copy some stuff with gParted, but I made sure that the UUID's in /etc/fstab were valid for booting and got everything working.  

As for the ACTUAL experience of testing 16.04... 

I was disappointed with how the menu editor corrupted the whisker menu.  I think that bug is already documented and in the release notes though.  I was able to do an offline install of Wine (my home computer lacks internet connections).  And I was able to install Cockos REAPER and do all of my normal DAW optimizations (disable unneeded services, etc) and configurations of PulseAudio.  Reaper ultimately seemed to work just like it already does on my 14.04.3 partition.  So that was good news.  The settings manager seems a bit more thorough (in a good way), although I don't really like stuff like MugShot and I never did figure out what OnBoard was for.  

One thing I did like about the installer was the ability to disable installation of so many hundreds of fonts.  The 400some+ freeware fonts from Briant Kent I really don't want.  When I am busy editing something and need to choose fonts, I can't waste all my time scrolling through 600 fonts.  So being able to prevent tons from being installed is a really good option.  

I also did like how Ubuntu Studio keeps both Brasero and XFburn.  Having some kind of disc authoring is a must for some of us.  I was disappointed to see both Xine and Audacious go though.  But I can certainly understand wanting to leave the complexity of configuring Xine.  

Other native linux installs of NeatImageDemo and XnViewMP went just fine.  

In conclusion... 
I chose not to keep the 16.04 install because my 14.04.3 install is still working pretty well and I prefer to have a functional/editable application menu and a better supported graphics system.  I didn't run tests on video playback or authoring.  I just took the technical info at it's word.  Also, the effort to reinstall all my programs and settings isn't quite worth it since really I didn't notice anything much different.  Some of the programs I don't use had more up to date versions, of course.  That's good, such as LMMS.  But I use Reaper instead.  

I was disappointed to see Synaptic missing, but at least that's probably installable for online systems.  Also, I had to use dpkg -i file.deb for offline installs instead of Gnome Software, which reportedly still can't quite handle offline installs.  But dpkg works just fine, so I was able to do my offline installs of debian archived programs.  

I am going to wait for the further AMD GPU driver support before I completely change over to v16 of Ubuntu Studio.  
In the meantime, I might test run AVlinux on the free partition.

---

### Post by bma12 on 2016-04-27
Hi to all

In my case the installation went smoothly, but i had a problem with the wireless connection and i fixed by rebooting from live usb. Now my Xenial working great.

---

### Post by pfeiffep on 2016-04-27
Thus far I have installed released Xenial MATE on 2 machines, and have a test partition on a third.
1) Installed on Dell laptop 64 bit - very smooth all hardware and sodtware works
2) Installed on an Acer netbook 32 bit - grub was misconfigured [didn't display text] - after fiixing works great
3) Test partition on HP tower is working perfectly - I'm waiting for first point release for fresh install on main partition
Specs of systems that [successfully installed]("https://ubuntu-mate.community/t/share-your-system-specs-super-list/4522") Xenial MATE

---

### Post by tony-sales on 2016-04-29
Did a fresh install of 16.04 at work on my desktop computer. Installation went smoothly, but VMware View Client is not available from the official repositories so I had to install this from a downloaded binary and had trouble getting it to run from a unity launcher. Suprised  they had removed Brasero from the default install but otherwise everything else worked as expected. Had a play with the new snap package system, seems simple to use but there are only a dozen or so apps available currently - will try it out again when there are a few more options. Tried updating from 14.04 to 16.04 on my laptop at home and although the install worked it was unable to keep some of the packages I had installed and threw up unresolvable dependancy issues. So now doing a fresh install...

---

### Post by ZoiaGuyver on 2016-05-01
Hmm where to begin?! It sucks!! 

I had nothing to fix, nothing that caused me any real headache and apart from a bug with the installer (that is already well documented and known about) everything just works fine and dandy! that is not Linux!! Linux is meant to be hard, time consuming and give you lots of headaches!

/sarcasm off

Tried both upgrades and fresh installs on my testbench, laptop and desktop all went fine with the only bug being the installer getting stuck (which as I stated above is a well known issue, probably even fixed by now).

---

### Post by Wade_Fogarty on 2016-05-03
I upgraded from 15.10 and other than a long series of "report this error" after the first boot, everything appears to work.  However, I've noticed web pages stalling and failing to completely load across all browsers since the upgrade.  Boot time has more than tripled.  I've backed up and will probably do the clean install that I should have done in the first place.

Update:  Backed up, performed a clean install, restored, and it's working just right.

Further update:  The web stalling wasn't due to the upgrade.  The issue appears to be a problem with IPv6 and AT&T.  Disabling IPv6 corrected the problem.  The only thing resolved by the clean install was correcting the slow boot.

---

### Post by nukedathlonman on 2016-05-05
In my case, I only have one of my three machines upgraded.  I only have two things to address, & I could easily address them in 15.10. My wireless card has a minor bug - before I could just down load the latest from git hub, recompile and install into the kernel... I can't simply do that anymore (Secure Boot and how the latest kernel signatures work).  Yes i know how to work around all that, but it's not the priority.  But the AMDgpu display drivers are a *MASSIVE* headache on this machine...

My oldest computer I'm hesitant to, all Kernels after 4.2.0-25 seem to be bugged (no sound or BT, and very prone to crashing - the one thing that computer is not known for).  I never really debugged or reported this, but that computer is 7 years old and due for retirement (it's over worked, overused, needs a replacement battery that's no longer made, & the screen's starting to go).  This is what the newest of the bunch is supposed to replace - haven't been able to make the full transition as of this time.

The desktop is simply a non-priority at the moment.  I want to get the newest machine going, and not have to worry about two systems being down with the same or similar display driver problems...

---

### Post by albertodallaporta on 2016-05-14
Hi everyone. I would like to share my opinions too. I bought a Dell XPS 15 9550 and tried 4 times to install Ubuntu 16.04 but the installer always failed right after kernel update. I managed to get it installed by running the installer from the Live Version (e.g. instead of select "Install Ubuntu" I selected "Try it without installing" and then I ran the installer from inside the OS. That worked, but.....

1) I have bought the Eth/HDMI/USB3/Vga to Type-C adapter because I always use 2 (or 3 when possible) monitors.. but  it doesn't work, neither the eth nor Vga and USB so the problem is obviously that Ubuntu does not have support for the Type-C port
2) Nvidia proprietary drivers (361) works quite well in general, low power consumption and heating on normal usage, but the screen randomly freezes, it's quite annoying
3) Integrated Bluetooth doesn't work at all, it does not detect any device (mouse, keyboard, phone, headphones, nothing)
4) Networking has various issues: sometimes WiFi disappears from the list of possible networking options and I need to reboot to let the OS detect the Wireless Card again.... sometimes it connects to the WiFi with no problems but, again, the WiFi network disappears yet being connected to a network (example: I am connected to my home WiFi network now, but... [http://imgur.com/I30a1UD](http://imgur.com/I30a1UD) )
5) Suspend breaks Reboot and Shutdown with that annoying message "Transaction is destructive". It has to be addresses asap.. 15 

Everything else works really great so I can wait for the above problems to be fixed for now. But I think that it's something urgent, mainly because it seems that Dell + Ubuntu is going to be the only competitor of Mac Book Pro.. Dell has done his work beautifully (the Dell XPS is really a super machine), while Ubuntu still has work to do to compete with the stability of Apple OS X. Let's see.

---

### Post by poorguy on 2016-06-05
I did three clean installs and two of them work without any problems. The third one had a shutdown problem but I was able to solve that by upgrading my bios to the newest version and all is working as it should be.

---

### Post by Linuxisfast on 2016-06-05
Clean install on multiple machines and hardware, slight glitches but all gone after updates. Only caveat for those using non HP printers and Epson CISS versions, the drivers don't install due to missing LSB that was removed on Debian base. Workaround is to install lsb by adding trusty main repo and the removing the repo.

---

### Post by yoshii on 2016-06-06
UPDATE:  

OK, so I decided to try and install Ubuntu Studio v16.04 LTS again.  And it wen't pretty well.  
As explained earlier, I needed to utilise "nomodeset".  I won't explain that again, since I already explained that.  
Overall, the install was a success.  

I am able to compose my music using Reaper via Wine and PulseAudio with all of my VST instruments and effects.  I was able to do my main offline debian archive installs.  
Video playback is working via the 32-bit Windows version of VLC Media Player.  

Parole crashes on seek/browsing videos even after changing the video mode.  So I don't use Parole at all anymore.  
The Font Manager is non-functional because it freeze/crashes on it's initial scan of all fonts, even after I deleted about 500 fonts.  
Gnome Software doesn't work at all, so I use "dpkg -i *.deb" instead.  
There is a Thunar file manager or Xfce error with renaming files; it crashes during some renames.  
So I started using PCmanFM file manager instead.  It can easily be set as the default file manager and it works just fine.  

There is an issue with Whisker/MenuLibre application menu editing.  
If you edit the layout, then all of a sudden some of the main categories disappear with all the contained links.  
This is a problem in Ubuntu Studio where there are a lot of extra categories.  
Some investigating showed me that the menu configuration files are still on disk and the application *.desktop files are also still available.  
Here is my workaround solution for gettting the menus back:  [http://ubuntuforums.org/showthread.php?t=2327706](http://ubuntuforums.org/showthread.php?t=2327706)

Other than that, everything seems to be working OK.  
I don't do any gaming or 3D rendering, so actually the ATI/AMD Radeon GPU graphics issue doesn't bother me.  
I will just wait for another year for the developers to finish the updated drivers and then transition to those then.  

The only other thing that bothers me is that the Ubuntu Installer (known as Ubiquity) seems to make mathematical errors.  
I use the manual configuration setting (poorly named"Something Else").  

For example:

I use gParted to format exact partition sizes of 4096 MB (4 GB) and 98304 MB (96 GB).  
gParted shows these without any errors graphically and in mathematical formats without any errors.  

However, Ubiquity wrongly shows "4.3 GB" instead of 4 GB, and "103.1 GB" instead of 96 GB.  
It also specifically reports a partition size of "103079 MB" instead of the correct 98404 MB.  

The math is 96 x 1024 = 98304 MB = 96 GB, but the Ubuntu installer doesn't do it this way.  
Similarly, the math is 4 x 1024 = 4096 MB = 4 GB, but the Ubuntu installer fails that.  

I use the 4 GB size for my SWAP area.  

This error has been around several years and it's pretty unnerving once you think about.  
I hope someday the developers will redesign Ubiquity, because that's just sloppy.  

But nevertheless, the install goes OK and you can still run gParted to see what's been done to your system and the actual partition sizes.  
I just wish that Ubuntu's installer installed gParted too since it's already on the LiveDVD.  Kinda odd not to include it in the actual distro.  

But anyways, I'm running my new system just fine.  
And recently I learned how to do offline installs using Synaptic, so now I can upgrade the system even though it's not connected to the internet:  
[http://www.idmforums.com/showpost.php?p=1399953&postcount=1](http://www.idmforums.com/showpost.php?p=1399953&postcount=1)

Happy Linux Computing!

---

### Post by ZoiaGuyver on 2016-06-06
If you want to understand whats going on with the sizes I recommend you go read about [Gibibyte]("https://en.wikipedia.org/wiki/Gibibyte").

1024 is the measurement for 1GB memory sizes.

1000 is the measurement for 1GB in Data Storage.

Some programs use libraries to adjust how the details are read or use different algorithms to give a final output. Until they decide to fix that some programs will read it differently.

---

### Post by yoshii on 2016-06-07
ZoyaGuyver:  Yes, I already know about the differences between MiB and MB, 1024 vs 1000.  
But if you study the math of what I wrote, you'll see that if Ubiquity was using 1000 instead of 1024 as a constant, then the reported sizes would have been smaller, not bigger.  So the math of Ubiquity is very broken.  

And since programs like gParted are able to do all of these calculations clearly and without the errors (even if MB boundaries are set or not), I can only conclude that it was sloppy programming.  

There's really not a whole lot of different algorithms for reporting data size.  It's not like DSP equalization algorithms or statistical windows.  There's not a whole lot of room for creativity either.  Numbers are numbers and when they are right they right, when they are wrong, they are wrong.  It's not even a floating point issue either.  

Attention to detail matters.  They screwed up.

---

### Post by kyphos on 2016-06-12
Downloaded **lubuntu-16.04-desktop-i386.iso** to my MacBook Pro and burned a LiveCD (using an Apple external optical drive).
My little netbox (an old Zotac Zbox ID11) wouldn't boot from it. The BIOS saw the optical drive and tried to boot from it, but no joy.  The optical drive made the familiar sounds of a CD/DVD that can't be mounted (spin-headseek-buzz-beep-spin-headseek-buzz-beep...).

Figured that the DVD burn on the MacBook was bad, so I burned another (on the MBP) and made sure it verified OK.
Same result - it wouldn't boot the Zotac.

Decided that the download of the .iso was bad, so I downloaded it again. And for good measure, verified that the MD5SUM was good just in case the image on the bistro server had somehow become corrupted. Burned another LiveCD
Same result - it wouldn't boot the Zotac.

Booted up 10.04 from the hard drive (that's what's presently installed on the Zotac).  Used it to download **lubuntu-16.04-desktop-i386.iso** for a third time. Then attempted to burn the LiveCD using 10.04 and the Zotac's optical drive (a Plextor).  That failed immediately upon clicking BURN.  The log indicated some sort of a Brasero error.  Now that I think about it, I was never successful burning anything using the Zotac & 10.04.

Three strikes - you're out.  I gave up on Xenial.

Downloaded **lubuntu-14.04.4-desktop-i386.iso** with my MBP. Burned LiveCD. It booted the Zotac just fine and the LiveCD environment appeared. After a short interval evaluating Lubuntu (which I'd never seen before), I deciding I didn't like the Windoesque menu bar across the bottom of the screen.

So I downloaded **ubuntu-14.04.4-desktop-i386.iso**, burned LiveCD, booted it up, then installed it to the Zotac's hard drive. Took over an hour, but the install went smoothly (except I have to unplug-replug the mouse after booting or resuming to get it to work). I'm not sure the Zotac is up to the challenge of Ubuntu 14.04 -- it only has 2GB of RAM and a rather dated Atom CPU.

There's something oddly different about **lubuntu-16.04-desktop-i386.iso **compared to the other two images.

---

### Post by yoshii on 2016-06-13
> **kyphos said:**
> Downloaded **lubuntu-16.04-desktop-i386.iso** to my MacBook Pro and burned a LiveCD (using an Apple external optical drive).
My little netbox (an old Zotac Zbox ID11) wouldn't boot from it. The BIOS saw the optical drive and tried to boot from it, but no joy.  The optical drive made the familiar sounds of a CD/DVD that can't be mounted (spin-headseek-buzz-beep-spin-headseek-buzz-beep...).

Figured that the DVD burn on the MacBook was bad, so I burned another (on the MBP) and made sure it verified OK.
Same result - it wouldn't boot the Zotac.

Decided that the download of the .iso was bad, so I downloaded it again. And for good measure, verified that the MD5SUM was good just in case the image on the bistro server had somehow become corrupted. Burned another LiveCD
Same result - it wouldn't boot the Zotac.

Booted up 10.04 from the hard drive (that's what's presently installed on the Zotac).  Used it to download **lubuntu-16.04-desktop-i386.iso** for a third time. Then attempted to burn the LiveCD using 10.04 and the Zotac's optical drive (a Plextor).  That failed immediately upon clicking BURN.  The log indicated some sort of a Brasero error.  Now that I think about it, I was never successful burning anything using the Zotac & 10.04.

Three strikes - you're out.  I gave up on Xenial.

Downloaded **lubuntu-14.04.4-desktop-i386.iso** with my MBP. Burned LiveCD. It booted the Zotac just fine and the LiveCD environment appeared. After a short interval evaluating Lubuntu (which I'd never seen before), I deciding I didn't like the Windoesque menu bar across the bottom of the screen.

So I downloaded **ubuntu-14.04.4-desktop-i386.iso**, burned LiveCD, booted it up, then installed it to the Zotac's hard drive. Took over an hour, but the install went smoothly (except I have to unplug-replug the mouse after booting or resuming to get it to work). I'm not sure the Zotac is up to the challenge of Ubuntu 14.04 -- it only has 2GB of RAM and a rather dated Atom CPU.

There's something oddly different about **lubuntu-16.04-desktop-i386.iso **compared to the other two images.

Just so you know, I think in all of the Ubuntus and many other versions of Linux, the menu bar across the bottom and/or top or side of the screen can be moved or deleted.  It's called a panel, and there can be more than one.  Each one can be customized.  

You should try booting from a bootable USB drive.  I had similar problems booting up LiveDVD's lately, but bootable USB drives of the same .ISO files seems to work on my system.  This could help you out I hope.

---

### Post by kyphos on 2016-06-13
> **yoshi2 said:**
> Just so you know, I think in all of the Ubuntus and many other versions of Linux, the menu bar across the bottom and/or top or side of the screen can be moved or deleted.  It's called a panel, and there can be more than one.  Each one can be customized.  

You should try booting from a bootable USB drive.  I had similar problems booting up LiveDVD's lately, but bootable USB drives of the same .ISO files seems to work on my system.  This could help you out I hope.

Yoshi,
Thanks for the tip.  I found a good [HowTo]("http://www.theotherinformation.com/2014/04/change-lubuntu-theme-feel-ubuntu.html") describing how to customize Lubuntu desktop (moving menu bar and panels around).  
I'm replacing Ubuntu with Lubuntu 14.04 as I type this.

As it happens, I did try booting from a USB drive. That little detour consumed another hour figuring out how to create a bootable USB (using dd) on my MacBook. The BIOS on the Zotac recognized the USB stick and attempted to boot from it, but immediately reported an error "*isolinux.bin missing or corrupted*".  I verified that the file was on the USB, so at that point I abandoned the effort and returned to LiveCD.

---

### Post by TenPlus1 on 2016-06-13
Installed Xubuntu 16.04, everything worked fine but Thunar seems to close when pressing <enter> when renaming files, or copy/pasting files to a new location ?!?! what gives ?!?!

---

### Post by yoshii on 2016-06-13
@TenPlus1:  Yes, the v16 renaming bug is documented and the fix (if it exists) isn't yet merged into the Ubuntu downloads as far as I know.  
@Kyphos:  So sorry that the boot flash drive didn't work out for you.  I used uNetBootIn, but I don't have a Mac.

---

### Post by leozinho29_eu on 2016-07-08
I had pretty different experiences:

Upgrade from 14.04:

Lubuntu in external HDD: perfect
Lubuntu in notebook: complete disaster (IrDA: script fa...), format required

Installing 16.04: 

Ubuntu in desktop: nearly good but NVidia card makes computer freeze after 20 minutes of use (nouveau being used, help about this would be welcome).
Lubuntu in (same) notebook: very bad, 4 attempts required. Discovered after formatting 3 times that xserver-xorg-video-intel was lacking.
Ubuntu in another desktop: flawless installation.

I don't know what I should vote because my experiences went from perfect to disaster. 

There is one important thing: the Lubuntu ISO image HAVE TO include the xserver-xorg-video-intel package. Most computers which use on-board/integrated graphical processing units use Intel ones. These are the target of Lubuntu: computers with lower specs, which are older and use integrated GPUs, which requires xserver-xorg-video-intel to not get stuck with lightdm crashing endlessly.

I noticed a not so similar issue was cited only one time in this thread, it is a mistake to not include xserver-xorg-video-intel package at Lubuntu ISO. I hope the developers are aware about this.

---

### Post by Bashing-om on 2016-07-08
Upgrade from 15.10; flawless.
PPAs purged/removed prior;
No proprietary drivers in use;
Screensaver disabled .

[INDENT][INDENT]works better than a charm
[/INDENT][/INDENT]

---

### Post by DragonBoy on 2016-07-19
Works great on my System76 Lemur. I have done a clean install with each release since version 14.10. Ubuntu 16.04 release has been great so far. The only issue I have seen is when I launch libreoffice --calc from the terminal window. I get the following warning:

"(soffice:8732): Gdk-WARNING **: gdk_window_set_icon_list: icons too large"

I have looked into this warning and not been able to solve it. Did not get these warnings with version 15.10 and earlier. I do keep my system updated with the "sudo apt-get update/upgrade". Just in hopes that it will get fixed with updates/upgrades. This warning is not the end of the world just a slight annoyance.

I use the following Apps/Software: 
Chromium Web Browser
Firefox Web Browser
Thunderbird Mail
FileZilla
LibreOffice
Terminal (Heavy usage here)
nedit (Heavy usage here. Create Bash & Python scripts.)


I used to be a 100% windows user but over the last 5 years I am 75% Linux and 25% windows.

Happy scripting in Ubuntu everyone!!!

---

### Post by Peter_Horn on 2016-08-03
I run two Ubuntu systems. This one is a laptop, dual-boot with Win10 (previously 14.04LTS / Win7). I repartitioned the disk and did a clean install. No real issues. I'd saved an image of the disk before that, so I could retrieve stuff from ~, such as ssh keys (not something you want to have to retype!)

The other one is a broken old crock of a machine; its main purpose in life is to run Apache httpd to serve a couple of low-volume sites. It has been running on 14.04LTS more or less headless. There is a multitail running on tty1, tailing a few log files. Anything more I want to do on it, I ssh in from one of my other machines. 
Yesterday I bit the bullet and ran the release update to 16.04LTS. Most things survived, but there is one annoying issue. Essentially, the ssh service crashes when I terminate a session, which makes it a bit of a pain to manage.

UPDATE: I tracked down the sshd issue. For some reason best known to whoever did it (not me!), there was an **/etc/default/ssh **containing a line  
**SSHD_OPTS='-d' **which makes sshd start in debug mode. The other outstanding issue is that the auto-login on tty1 has stopped working. I previously had, as the last line of **/etc/init/tty1.conf** the following  
[B]exec /bin/login -f logs < /dev/tty1 > /dev/tty1 2>&1  
[/B]That no longer works, and neither does 
**exec /sbin/getty -8 -a logs 38400 tty1****logs** is of course the username for the multitail.

---

### Post by fromwin2lin on 2016-08-04
Fresh Install: Flawless

Upgrade: Flawless

Canonical did an outstanding job with this release! I can't wait for 16.10! I hope Unity 8 is ready by then.

---

### Post by techyzen101 on 2016-08-10
Installed beside Windows 8.1, and updated everyday.
Had some minor features missing, hotkeys,but still great and fast, as usual :).

---

### Post by johnnyzee on 2016-08-10
I tried to upgrade from 14.04 following prompts on my System 76 Galago Ultrapro. The installation stalled for over an hour so I shut it down thinking it would reboot normally but it booted in 16.04 in terminal. Not sure what happened so I downloaded the iso version using another machine and loaded 16.04 beside the other version and my hard drive is nearly full. So I suppose will now try to retrieve files in terminal mode and reload from the iso file.

---

### Post by Geoffrey_Arndt on 2016-08-13
#3rd upgrade via online process on a System 76 Galago Ultra Pro laptop. . no issues.   Fastest update yet (about 40 minutes in total).   Having a PC with Linux pre-installed makes upgrades and installs a piece of cake (easy).   It also helps that I have a non-UEFI BIOS.

_**How Ironic**_ . . . I just saw "johnnyzee's" post #45 above.   OK, simple reason that upgrade didn't install . .    _Never shut down an upgrade of ANY type before done_.    [B][COLOR=#0000ff]You don't have to get your files via terminal commands (although you can).    Just load a live (try) version of ubuntu or a dedicated "rescue live os" like Parted Magic.
[/COLOR][/B]
For upgrades to process with a higher chance of 100% success, you have to try and make sure your system is as "vanilla" or pristine as possible.   That simply means no 3rd party PPA's enabled (including System76 drivers PPA).    I also recommend uninstalling any VM's you might have on the system, or complex proprietary apps like Skype.   The upgrade algorithms can't cover all these possibilities (including EULA's, etc.).    [COLOR=#0000ff][B]Sometimes the install is not actually hung . . . but there is a EULA window underneath the installer window waiting for user action (as in the case of MS-fonts).   
[/B][/COLOR]
Also, be 100% sure of your internet connection.   Wireless is fine (my upgrades have all been via wireless networks),  but ethernet is even better.

Now, best option in a case like Johnny Zee's is to get all key data offloaded to usb flash stick or cloud, then create a 16.04.1 usb bootable flashstick.   I recommend Etcher for that task.   Then do a full re-install using the full drive.   Should take about 30 - 45 minutes.

---

### Post by sgtaylor5 on 2016-08-13
Hi,

I've been off and on with Linux since about 2008. I needed to keep learning Windows to use it at work, but have been growing steadily disaffected with Microsoft, against my desires, since then. Windows-as-a-Service, especially the Anniversary Edition turning the Pro version too much like the Home version, was the last straw.

About six months ago, I tried to dual-boot install Ubuntu 14.04.3 on my Dell Latitude E6540 laptop. Upgraded to 16.04 and it went to sleep. Never woke up. Had to delete the partitions and stay with Windows 10.

Tried again about two weeks ago and the developers had fixed the kernel problems with Haswell Intel graphics and 16.04.3 works perfectly. Even got a slightly older Windows version of Evernote running with PlayOnLinux! Quietly stunned that everything works as well as it did.

Realized I could setup a small Windows 7 PC with QuickBooks Pro 2013 running on it and remote in. That one program was the reason I didn't switch years earlier; figuring out that solution saved me $300 a year.

Once I had everything setup the way I wanted to, blew away my Windows partitions and switched from Google Drive to MEGA, I blew everything away again a week later and reinstalled with manual partitioning the way I wanted to. (Ubiquity uses logical partitions with an automatic install, even with a GPT disk, and I wanted primary partitions.)

---

### Post by autocrat on 2016-09-05
This was probably the most difficult Linux install I have done in quite a while. The installer had a hard time with my Hard Drives, but in the end it worked out. I must have gotten half a dozen errors. Read write errors, partition issues (even when using GPT :mad:) Very frustrating.I ended up installing on a different drive, and using clonezilla to copy it onto my primary. This worked no problem.

---

### Post by Yeong-Il_Yi on 2016-10-17
First attempt of a clean install was on the day 16.04 was released, and it was a failure - I think it was because the installer didn't like the size of the efi partition. (I always manually partition before the install, because the installer can't partition exactly the way I want. I know, it's the OCD kicking in.)

Second attempt, after I repartitoned, was flawless. Just last week I got a Samsung 950 Pro, so I did a third clean install with 16.04.1, and it was flawless, too. One thing that I keep forgetting how to do is to install Korean input support, but eventually I got it.

Hopefully I'll stick with this install for a while. (Not touching Yakkety Yak, as it is not LTS.)

---

### Post by oygle on 2016-10-18
Fresh Install: Flawless

Rebooted and noticed Kubuntu is now so SLOW.   :(

Video/display problems - [https://ubuntuforums.org/showthread.php?t=2340444](https://ubuntuforums.org/showthread.php?t=2340444)

Mount problems - [https://ubuntuforums.org/showthread.php?t=2340456](https://ubuntuforums.org/showthread.php?t=2340456)

---

### Post by pa1jim on 2016-10-20
Upgraded from 14.04 to 16.04 server. Had a few errors due to old config-files but runs fine now. One strange thing I found: no snaps! 

$snap info gives:
-bash: snap: command not found

~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

~$ uname -r
4.4.0-45-generic


What do I have to do to get snap-support?

Grtz, Jim

---

### Post by bd1886 on 2016-11-02
Just began using Ubuntu again with 16.04 and everything has gone as smooth as silk software wise (for this true beginner) because of the support in general out there. (Still have a couple hardware issues with my Toshiba A665-S5199x laptop's speakers not working and efficient battery support but heck....figure it's a great excuse to get my feet wet.) For someone like me to appreciate this distro says something.....smooth,intuitive and beautiful so far.

---

### Post by jerrylamos on 2016-11-02
Xenial here, booting ubuntu used to give a list of bootable ubuntu images I have 3, now just boots into one with no choice of which.  ?
Used to display list of partitions, diagnostic mode whatever.  Now just boots straight into Xenial no choice.

Thanks, Jerry

---

