---
title: "Let the crash begin..."
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-02-08
After an awesome run of stability with 12.04, I'm experiencing the biggest crash yet.

After downloading the latest batch of dist updates, and restarting my PC, I find I can get to my log-in screen fine and log in. Then I get this pale grey screen with the cursor in the middle.
A few seconds later, grey gives way to my chosen background, but nothing else happens. Then after a short while I get failure messages, where I can send crash reports to launchpad (which I have a few times since rebooting).

The crash reports are entitled:

"Nvidea settings" and "Unity test settings" 

I can't get any further. Unity fails, I just have a background pic.

My other puter (from which I write this) had a plymouth failure after installing the same dist. upgrades. It does not have Nvidia drivers, so I can still get full access to my 12.04.

Both puters have kernel 3.2.0-14 installed.

When there is a fix to this (as I'm sure I'm not the only Nvidia user who will experience this), how will we update again if we can't get past after the login screen?

Cheers.

Edit: I find I can right click on the desktop which allows me access to the settings panel, via 'Change desktop background'. But won't be able to update from there because there is no 'Update Manager' setting there.
I have just re-installed the nvidia drivers using "Additional Hardware", to no avail.

Logging into Unity 2D doesn't help either.

---

### Post by effenberg0x0 on 2012-02-08
> **Baldrick_NZ said:**
> After an awesome run of stability with 12.04, I'm experiencing the biggest crash yet.

After downloading the latest batch of dist updates, and restarting my PC, I find I can get to my log-in screen fine and log in. Then I get this pale grey screen with the cursor in the middle.
A few seconds later, grey gives way to my chosen background, but nothing else happens. Then after a short while I get failure messages, where I can send crash reports to launchpad (which I have a few times since rebooting).

The crash reports are entitled:

"Nvidea settings" and "Unity test settings" 

I can't get any further. Unity fails, I just have a background pic.

My other puter (from which I write this) had a plymouth failure after installing the same dist. upgrades. It does not have Nvidia drivers, so I can still get full access to my 12.04.

Both puters have kernel 3.2.0-14 installed.

When there is a fix to this (as I'm sure I'm not the only Nvidia user who will experience this), how will we update again if we can't get past after the login screen?

Cheers.

Edit: I find I can right click on the desktop which allows me access to the settings panel, via 'Change desktop background'. But won't be able to update from there because there is no 'Update Manager' setting there.
I have just re-installed the nvidia drivers using "Additional Hardware", to no avail.

All NVidia machines working just fine here with all available updates on this kernel.
If I were you I would:
- Purge PPAs. Add them back later if you want. Use my script posted **_[COLOR=Red][here]("http://ubuntuforums.org/showpost.php?p=11530911&postcount=57")[/COLOR]_** to list the PPAs and the explanation **_[COLOR=Red][here]("http://ubuntuforums.org/showpost.php?p=11531216&postcount=59")[/COLOR]_** to remove them if you wish.
- Switch to a VT and kill all instances of X. ```
sudo service lightdm stop && sudo kill -s KILL $(pidof X)
```-- If you're using NVidia Proprietary binary installer: Reinstall with the -K option (rebuild VGA kernel module)
-- If you're using NVidia from repos, reinstall it. ```
sudo apt-get install --reinstall nvidia*
```- Get plymouth off your life. This is Ubuntu testing, you need to see error messages. It makes no sense to use Plymouth unless you're testing Plymouth. 
```
sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT: Remove quiet and splash
GRUB_CMDLINE_LINUX: Remove quiet and splash
sudo update-initramfs -u
sudo update-grub
sudo reboot now
sudo apt-get update && sudo aptitude safe-upgrade
```Regards,
Effenberg

---

### Post by Baldrick_NZ on 2012-02-08
> **effenberg0x0 said:**
> All NVidia machines working just fine here with all available updates on this kernel.
If I were you I would:
- Purge PPAs. Add them back later if you want. Use my script posted **_[COLOR=Red][here]("http://ubuntuforums.org/showpost.php?p=11530911&postcount=57")[/COLOR]_** if you wish.
- Switch to a VT and kill all instances of X. ```
sudo service lightdm stop && sudo killall -s KILL $(pidof X)
```-- If you're using NVidia Proprietary binary installer: Reinstall with the -K option (rebuild VGA kernel module)
-- If you're using NVidia from repos, reinstall it. ```
sudo apt-get install --reinstall nvidia*
```- Get plymouth off your life. This is Ubuntu testing, you need to see error messages. It makes no sense to use Plymouth unless you're testing Plymouth. 
```
sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT: Remove quiet and splash
GRUB_CMDLINE_LINUX: Remove quiet and splash
sudo update-initramfs -u
sudo update-grub
sudo reboot now
sudo apt-get update && sudo aptitude safe-upgrade
```Regards,
Effenberg

Thanks for that. But unfortunately, I can't even get far enough to bring up terminal. Any ideas?

I've since noticed (on my PC that does work) that the pulse audio updates have also screwed around with my music player of choice. It was working well before the update, but now you have to click on the 2nd song in the playlist for it to work.

Bizzare.

---

### Post by effenberg0x0 on 2012-02-08
> **Baldrick_NZ said:**
> Thanks for that. But unfortunately, I can't even get far enough to bring up terminal. Any ideas?

I've since noticed (on my PC that does work) that the pulse audio updates have also screwed around with my music player of choice. It was working well before the update, but now you have to click on the 2nd song in the playlist for it to work.

Bizzare.

Press Ctrl+Alt+F6 in your keyboard and login with user and password.
F1 to F6 are VTs (Virtual Terminals). 
The desktop session uses F7. so Ctrl+Alt+F7 returns to the desktop.

PS: The problems you are facing are not related to PP. You can use any Ubuntu tutorial / HowTo / Documentation to fix them in case you go searching for info. You basically need to purge your PPAs, reinstall your NVidia VGA Drivers and reinstall your NVidia VGA Kernel Module, perform a clean apt update and upgrade and reboot. Regarding audio, you have to use apt to install --reinstall pulseaudio/alsa, dpkg-reconfigure pulseaudio/alsa and then check **_[COLOR=Red][here]("https://wiki.ubuntu.com/Audio/UpgradingAlsa")[/COLOR]_** if you still get problems.

Regards,
Effenberg

---

### Post by Baldrick_NZ on 2012-02-08
Thanks for your help so far,

When I
```
sudo apt-get install --reinstall nvidia
```

I get this
```
E: Unable to locate package nvidia
```

I tried with -k at the end of the command, but it returned with "-k is unknown"

Any other ideas?

Cheers.

---

### Post by mdhollis on 2012-02-08
I believe it's nvidia-current assuming you want the current driver 

By any chance do you have the gnome3 and ricotz ppa's installed?

---

### Post by Baldrick_NZ on 2012-02-08
> **mdhollis said:**
> I believe it's nvidia-current assuming you want the current driver 

By any chance do you have the gnome3 and ricotz ppa's installed?

It liked that more. Thanks.

Although when I do
```
sudo aptitude safe-upgrade
```
as suggested, I get
```
sudo: aptitude: command not found
```

When I restart the PC, I get the same familiar grey screen as before. Unity doesn't seem to load.

Meanwhile, the other PC (the one I'm writing from) still has audio issues, even with Rhytmbox. This after I reinstalled and reconfigured pulseaudio. I'm attempting a restore from late Jan to see whether that fixes the audio prob...

Nope, didn't work either.

Oh well, looks like two puters are going to be wiped of 12.04. It's a pity they didn't test, test, test then test again before releasing updates. The old saying applies, if it ain't broke - don't fix it. Both puters were working well before the 'upgrades' now both are, well pretty much useless as is. I might come back again when they're more stable.

Thanks though for all your help guys, much appreciated!

---

### Post by arpanaut on 2012-02-08
> Oh well, looks like two puters are going to be wiped of 12.04. It's a  pity they didn't test, test, test then test again before releasing  updates. Both puters were working well before the 'upgrades' now both  are, well pretty much useless as is. I might come back again when  they're more stable.

LOL what did you expect...
This Alpha software we are testing here.

Yeah that's right; we are the testers!
One should be prepared to reinstall at any time in the development cycle.

Sorry to be so forward, but you might want to reevaluate your expectations from Alpha grade software.

---

### Post by kaldor on 2012-02-08
Really, this is alpha. It is **not even beta quality**. What were you expecting? If you choose to run early testing releases of any OS you should not expect to survive a reboot.

---

### Post by VMC on 2012-02-08
> **arpanaut said:**
> LOL what did you expect...
This Alpha software we are testing here.

Yeah that's right; we are the testers!
One should be prepared to reinstall at any time in the development cycle.

Sorry to be so forward, but you might want to reevaluate your expectations from Alpha grade software.

That's the problem of having Testing on the front page for all to see and try, instead of how it use to be on "Development & Programming".

I realize there are warnings on the halls and walls, but when someone comes along and see's it on the front page, they might say, hey let me try this out, without reading the warning labels.

---

### Post by cariboo on 2012-02-08
> **Baldrick_NZ said:**
> 

Oh well, looks like two puters are going to be wiped of 12.04. It's a pity they didn't test, test, test then test again before releasing updates. The old saying applies, if it ain't broke - don't fix it. Both puters were working well before the 'upgrades' now both are, well pretty much useless as is. I might come back again when they're more stable.

Thanks though for all your help guys, much appreciated!

If you were subscribed to the ubuntu-devel mailing list, you would have seen that alsa is expected to be a problem for a couple of days.

> On Wed, Feb 08, 2012 at 07:16:51PM EST, Luke Yelavich wrote:
> Hey folks,
> Just a heads up that I am in the process of getting ALSA 1.0.25 into precise. I am checking as thoroughly as I can to make sure I don't break anything, but if you find your audio is broken in the coming days, please let me know, particularly ARM folks.
In light of being reminded about our need for testing, I have put alsa-utils v1.0.25 into the Ubuntu Audio Dev PPA for precise, [https://launchpad.net/~ubuntu-audio-dev/+archive](https://launchpad.net/~ubuntu-audio-dev/+archive). Alsa-lib is already in precise since I jumped the gun a bit, so any issues you find can be filed in launchpad against alsa-lib. Please test alsa-utils, and file a bug in launchpad with your issue, noting the version of alsa-utils in the description.

Thanks

Luke

This means you are the one that's supposed to test, test , then test again, and report bugs.

---

### Post by Baldrick_NZ on 2012-02-08
Well, yeah. More fool me.

I guess it was stable for me for so long that I started treating as, well, stable. My bad. Learning curve accepted.

In as far as reporting bugs go, I have reported many through the automated reporting mechanism, particularly today with the nVidia problems. I have also filed quite a few recently when apps fail to launch, etc... 
I've been as keen as the next guy on this list to see this version be all it can be. As a former Unity detractor, I'm loving the way it's coming along now. Just a bit annoyed that all of a sudden I get some decent-sized issues - all at once. ;-)

---

### Post by effenberg0x0 on 2012-02-08
This is absurd. Alpha, Beta, RC, Precise, Dapper, Ubuntu or Debian, it wouldn't make a difference: Look at the reported problem. Look at my instructions. Look at the performed commands. The errors are evident. It's not the OP's fault, but it would be great if "General Help / Absolute Beginners" could jump in in such cases. There are many cake recipes for installig NVidia drivers in General Help threads, Ubuntu documentation, Google. I wrote a few, so I know this. I think it's useless to let this thread proceed. The time spent doing the "General Help / Absolute Beginners" work should be spent browsing launchpad and fixing real PP problems.

But to fix the OP problem:

- Press CTRL + Alt + F6 to go to the VT
- Paste this:
```
sudo service lightdm stop && sudo kill -s KILL $(pidof X)
```- Paste this:
```
sudo -s
```- Paste this:
```
apt-get remove nvidia nvidia-173 nvidia-cg-toolkit nvidia-173-dev nvidia-common nvidia-173-updates nvidia-current nvidia-173-updates-dev nvidia-current-dev nvidia-96 nvidia-current-updates nvidia-96-dev nvidia-current-updates-dev nvidia-96-updates nvidia-settings nvidia-96-updates-dev nvidia-settings-updates
```- Paste this:
```
if [[ -d /etc/apt/sources.list.d && $(ls -l  /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir  exists and is not empty\n\n"; for PPA_FILE in $(ls  /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed  -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e  's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e  's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list; done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi
```- Paste this:
```
apt-get install ppa-purge
```- Paste this:
```
for PPA in $(cat $HOME/ppa-sources.list); do /usr/sbin/ppa-purge $PPA; done 
```- Paste this:
 ```
cd
mkdir -p $HOME/Downloads/nvidia_drivers
cd $HOME/Downloads/nvidia_drivers
```- Paste this:
```
if [[ $(uname -a | awk '{FS=" "} {print $12}') -eq "x86_64" ]]; then echo "Downloading NVidia Driver 290.10 for x86_64" && wget http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/NVIDIA-Linux-x86_64-290.10.run; else echo "Downloading NVidia Driver 290.10 for x86" && wget  http://us.download.nvidia.com/XFree86/Linux-x86/290.10/NVIDIA-Linux-x86-290.10.run; fi
```- Paste this:
```
exit
sudo chmod +x NVIDIA-Linux-x86*290.10.run
sudo ./NVIDIA-Linux-x86*290.10.run
```(Answer yes to _**[COLOR=Red]all[/COLOR]**_ questions)
- Paste this:
```
sudo apt-get update && sudo apt-get upgrade
sudo reboot now
```Regards,
Effenberg

---

### Post by jerrylamos on 2012-02-09
> Originally Posted by Baldrick_NZ View Post

Oh well, looks like two puters are going to be wiped of 12.04. It's a pity they didn't test, test, test then test again before releasing updates. The old saying applies, if it ain't broke - don't fix it. Both puters were working well before the 'upgrades' now both are, well pretty much useless as is. I might come back again when they're more stable.

Thanks though for all your help guys, much appreciated!

That's what we're for.  There's such a myriad of hardware and installation variations out there that the developers can't run 8it all - it's up to us.

Having said that, sometimes I wonder if the developers are listening when there are dozens and dozens of people subscribed to a launchpad bug and no response.

Anyway, unstable development being exactly what it is, I expect to re-install and recover several times during alpha, beta, and even release candidate.  The forum helps a lot on recovery.

For that matter, I'll deliberately re-install just to see if ubiquity is still buggy (it is) and also after a bunch of updates the disk space used gets bigger and bigger full of left over junk even though I do autoremove, synaptic remove old linux images & headers, etc. etc.

Jerry

---

### Post by ventrical on 2012-02-09
> **kaldor said:**
> Really, this is alpha. It is **not even beta quality**. What were you expecting? If you choose to run early testing releases of any OS you should not expect to survive a reboot.


 I put a script in my sig to remind myself. :)

---

