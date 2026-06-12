---
title: "Testing Ubuntu Vivid Vervet 2nd Installation (LVM): Post Installation Sequence"
date: 2015-04-03
forum: Ubuntu Development Version
---

### Post by MikeMecanic on 2015-04-03
[FONT=Liberation Mono]April 3rd  2015.  Testing Vivid Vervet AMD64 alone.  USB ISO Installation using this application [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb). Default installation with the LVM Option.[/FONT]

[FONT=Liberation Mono]Post-installation sequence:[/FONT]

[FONT=Liberation Mono]1) Enable firewall: [/FONT][FONT=Liberation Mono]**sudo ufw enable**[/FONT]
[FONT=Liberation Mono]2) Disable Vino: [/FONT][FONT=Liberation Mono]**sudo apt-get remove vino**[/FONT]
[FONT=Liberation Mono]3) remove Guess Session: 1)[/FONT]**sudo apt-get install gksu 2) **[FONT=Liberation Mono]**gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf / 3) **[/FONT][FONT=Liberation Mono]When the file opens, add this line at the end of file and save it: [/FONT][FONT=Liberation Mono]**allow-guest=false**[/FONT]
[FONT=Liberation Mono]4) Reboot[/FONT]
[FONT=Liberation Mono]5) System Settings/ software and updates /other software: check Canonical Partners and Canonical Source Code / United State Server /  Updates: check Pre release Updates (vivid Proposed). Reload[/FONT]
[FONT=Liberation Mono]6)Software Updater: Apply a long list of updates[/FONT]
[FONT=Liberation Mono]7) Via Software Center:Opera 28 stable, Google Chrome 41 stable and Synaptic 0.81.3 and Network Tools 3.8.1[/FONT]
[FONT=Liberation Mono]8)Install VLC Media Player: [/FONT][SIZE=4][COLOR=#333333][FONT=Monaco]s**udo apt-get install vlc**[/FONT][/COLOR][/SIZE]
[FONT=Liberation Mono]9) Visualize startup Applications:  enter command line one by one : [/FONT]
**mkdir -p ~/.config/autostart**
**cd ~/.config/autostart**
**cp /etc/xdg/autostart/*.desktop .**
**sed -i "s/NoDisplay=true/NoDisplay=false/g" *.desktop**

Open Startup Applications and disable the following boot-up applications: 1-Backup Monitor 2- Chat 3- Desktop Sharing 4- GPG Password Agent 5- Onboard 6 &#8211; Ocra Screen Reader 7- Personal File Sharing 8- UpdateNotifier 

10)  Updating via the terminal: **sudo apt-get update && sudo apt-get upgrade**

11)  Version of Ubuntu Install: **lsb_release -a**

                           ***

HP Laserjet Printer 1020 not working and hp-doctor not recognizing the printer. **Would strongly appreciate having the new boot-up image, the grey scale one**. A jewel of creativity: it rejuvenate my brain and is helpful for black screen.  **_We have the same one since 10.LTS_**.  For the rest, itl ooks good.  Will do a third installation: Partitioning Ubuntu During Installation later...

---

### Post by zika on 2015-04-03
> **MikeMecanic said:**
> ```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf /
```[SIZE=7]>[/SIZE]```
gksu gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf 
```Just not to get C&P people (since we are in U+1 section I do hope there are not many of those here) in trouble...
Several more comments later if I get enough spare time... ;)
[SIZE=1]Code tabs are here for a reason... ;)[/SIZE]

---

### Post by aljosa2 on 2015-04-03
Here's my way how to be happier with Ubuntu:

**Remove guest session: **

> sudo sh -c 'printf "[SeatDefaults]\nallow-guest=false\n" >/usr/share/lightdm/lightdm.conf.d/50-no-guest.conf'

**Visualize startup Applications:**

> sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

**SSD drive optimization**

> gksudo gedit /etc/fstab*Add "noatime" to the line for your root partition and your other Linux partitions. Not to the line for the swap partition!*

> # / was on /dev/sda2 during installation
UUID=da571e57-f1af-49b1-95ba-206e95c86cec /               ext4    noatime,errors=remount-ro 0       1

sudo update-grub then reboot

**Optimize swap usage**

> gksudo gedit /etc/sysctl.conf*Add the following lines at the very end of the existing text in that file:*

> # Sharply reduce swap inclinationvm.swappiness=1
# Improve cache management
vm.vfs_cache_pressure=50

**Add ‘Click to Minimize App’ option to Unity launcher**

> dconf write /org/compiz/profiles/unity/plugins/unityshell/launcher-minimize-window true

**Disable overlay scrollbars**

> gsettings set com.canonical.desktop.interface scrollbar-mode normal

---

### Post by zika on 2015-04-03
> **aljosa2 said:**
> Here's my way how to be happier with Ubuntu:
**Remove guest session: **
**Visualize startup Applications:**
**SSD drive optimization**
*Add "noatime" to the line for your root partition and your other Linux partitions. Not to the line for the swap partition!*
**Optimize swap usage**
*Add the following lines at the very end of the existing text in that file:*
**Add &#8216;Click to Minimize App&#8217; option to Unity launcher**
**Disable overlay scrollbars**1. Change in /etc/fstab does not call for update-grub.
2. ```
[COLOR=#000000][I]# Sharply reduce swap inclination 
vm.swappiness=1[/I][/COLOR]
[COLOR=#000000]*# Improve cache management*[/COLOR]
[COLOR=#000000]*vm.vfs_cache_pressure=50*[/COLOR]
```[COLOR=#000000][I](missing CR)
[/I][/COLOR]Suggested after that is```
sudo sysctl -p
```
...

---

### Post by aljosa2 on 2015-04-03
Thanks zika.
What do you guys use to get "Open as Root/Administrator" and "Open In Terminal" functions?

Also, does "auto-hide launcher" works well for you? I need to install "compizconfig-settings-manager" and change "reveal edge respons" to 1.1267, and "launcher reveal pressure" to 3.

---

### Post by MikeMecanic on 2015-04-03
@Zika To remove guess session You first do the this command line: **sudo apt-get install gksu**
 /  Made the correction above.  Sorry for the error.

---

### Post by zika on 2015-04-04
> **MikeMecanic said:**
> @Zika To remove guess session You first do the this command line ```
sudo apt-get install gksu
```
 /  Made the correction above.  Sorry for the error.That was a typo (habit) of mine, about gksu(do)... ;)
I love this typo of Yours: &#8222;guess session&#8220;... ;)

---

