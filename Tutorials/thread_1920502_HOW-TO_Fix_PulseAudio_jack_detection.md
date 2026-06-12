---
title: "HOW-TO: Fix PulseAudio jack detection"
date: 2012-02-04
forum: Tutorials
---

### Post by rectec794613 on 2012-02-04
_**[COLOR="DarkOrange"]Contents[/COLOR]**_
[B][LIST=1]
[*]Introduction
[*]Background
[*]Fixing
[*]Reverting changes
[*]Final Notes
[/LIST][/B]
[CENTER]**[COLOR="DarkOrange"]_[SIZE="3"][Introduction][/SIZE]_[/COLOR]**[/CENTER]
I have seen a couple people with this problem. If one unplugs their headphones and re-inserts them afterwards, the audio is muted and cannot be unmuted. I went through this problem on [[COLOR="DeepSkyBlue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1902918"). This tutorial aims to solve this problem by installing an alternate version of PulseAudio with fixed jack detection. 

[COLOR="DarkOrange"]**_[CENTER][SIZE="3"][Background][/SIZE][/CENTER]_**[/COLOR]
PulseAudio, or simply "Pulse", is the default sound server on Ubuntu. A sound server is a service that runs in the background and helps deliver and manipulate audio. The reason this problem occurs is because the headphones "mode" that Pulse has is broken. It won't unmute. So when you plug in your headphones, and Pulse switches to that mode, it won't produce audio. In the next section we'll get to (hopefully) the solution.

[CENTER]**_[COLOR="DarkOrange"][SIZE="3"][Fixing][/SIZE][/COLOR]_**[/CENTER]
The easiest way to fix this is by installing the fixed PulseAudio sound server. First I'll give a short version for experienced users with a list of commands, then I'll give a step-by-step version for newer users with more details.

_[COLOR="DarkOrange"]Short Version[/COLOR]_
Enter these commands in a terminal. Ensure you have no programs open to prevent data loss. Use the first command 
```
sudo add-apt-repository ppa:diwic/jack-detection
sudo apt-get update && sudo apt-get upgrade
sudo reboot
cp -r ~/.pulse/presets ~/Desktop
rm -rf ~/.pulse
sudo reboot
cp -r ~/Desktop/presets ~/.pulse
```
If this is hard to understand, give the long version a shot.

_[COLOR="DarkOrange"]Long version[/COLOR]_

**_Step 1: Open a terminal_**
Open a terminal emulator with this key combo: CTRL+ALT+T. Alternatively, depending on your desktop environment, you can either click on the application menu, go to accessories and click on "Terminal", or press the "Super" (Windows key or Command) key and type "Terminal."

**_Step 2: Add PPA and install new Pulse_**
For this next step you must add a PPA, or Personal Package Archive. A PPA is a repository hosted on the Internet that contains packages. Type this command in the terminal to add this PPA:
```
sudo add-apt-repository ppa:diwic/jack-detection
```
Now we must update the package lists and "upgrade" to the new PulseAudio. As a side-effect it also upgrades any other packages that need it, so be aware!
```
sudo apt-get update && sudo apt-get upgrade
```
Now you must reboot. Make sure you aren't working on anything, as we'll be rebooting several times during this process.

**_Step 3: Reconfigure PulseAudio_**
You may notice that the audio isn't working. The reason for this is Pulse hasn't been configured to work with the new version you've just installed. To rectify this problem, enter these commands.

If you've installed pulseaudio-equalizer and have set custom presets, you should back them up if you want to keep them:
```
cp -r ~/.pulse/presets ~/Desktop
```
This copies the presets folder to your desktop for safe-keeping. Now we have to delete PulseAudio's configuration so it can generate a new one:
```
rm -rf ~/.pulse
```
Now restart the computer. You can do this from the terminal with: *sudo reboot*
The audio should be working and hopefully the jack detection works. To get your presets back:
```
cp -r ~/.pulse/presets ~/Desktop
```
And you can do what you want with the copy on your desktop. I hope that this fixed your problem! If it didn't, we can undo the changes in the next section.

[CENTER]**_[COLOR="DarkOrange"][SIZE="3"][Reverting Changes][/SIZE][/COLOR]_**[/CENTER]
You can undo the changes you made and be back to normal by entering these  commands in the terminal, as always, make sure you're not working on anything:
```
cp -r ~/.pulse/presets ~/Desktop
sudo apt-get install ppa-purge
sudo ppa-purge ppa:diwic/jack-detection
sudo reboot
rmdir ~/.pulse
sudo reboot
cp -r ~/Desktop/presets ~/.pulse
```

**_[COLOR="DarkOrange"][CENTER][SIZE="3"][Final Notes][/SIZE][/CENTER][/COLOR]_**
So there's my guide! If it worked, I'm glad I could help. If it didn't, I hope the reversal guide did. Feel free to contribute to this tutorial. Leave suggestions, improvements, and ask for help if you need to. Thanks for reading!

---

### Post by aitortxo on 2013-03-03
This didn't work for me, but i found another solution on one of the bugs reported for this problem:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1104565](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1104565)

"2) Use the latest drivers https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS"

---

### Post by rectec794613 on 2013-03-03
> **aitortxo said:**
> This didn't work for me, but i found another solution on one of the bugs reported for this problem:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1104565](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1104565)

"2) Use the latest drivers https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS"

Hey aitortxo. This guide is a bit outdated. I've already discussed this with the owner of the PPA, David Henningsson, (an Ubuntu audio developer who works for Canonical) when I was notified that it hadn't been updated for Quantal. He said this problem was fixed starting with Precise. But if you still get the problem, he said you can 
> just edit /etc/pulse/default.pa and comment out the row that says "load-module module-switch-on-port-available".

I'm not sure how well this workaround works, as I don't use the laptop that gave me this jack detection problem anymore. Sorry if I can't help you more.

---

### Post by rectec794613 on 2013-03-03
P.S. If there are enough people with this problem still, I think that would warrant a guide on the community wiki.

---

