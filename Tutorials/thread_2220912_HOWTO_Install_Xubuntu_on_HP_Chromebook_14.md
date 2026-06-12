---
title: "HOWTO: Install Xubuntu on HP Chromebook 14"
date: 2014-04-29
forum: Tutorials
---

### Post by maddog351 on 2014-04-29
[FONT=verdana]Hey all,

I thought i would post up the steps I used to replace Chrome OS with Xubuntu 13.10 on my new HP Chromebook 14 (Model: 14-Q002TU). *Please note:* This is not a crouton guide, if you wish to run Xubuntu or Ubuntu alongside Chrome OS you'll need a different guide ([Lifehacker Crouton Guide]("http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343")). As with all guides on the internet follow at your on risk, while I try to make sure all information in this guide is correct I am only human and I can forget things or make typos.   

_**Why would I do this?**_ Chrome OS is great if you need a fast, secure and lightweight way of browsing the web or working in the cloud but it does lack most of the features you get from a full Linux desktop environment.

_**What you will need:**_ [/FONT]
[LIST]
[*][FONT=verdana]2 x USB Drives (>= 4GB)[/FONT]
[*][FONT=verdana]HP Chromebook 14[/FONT]
[*][FONT=verdana]USB Mouse[/FONT]
[*][FONT=verdana]Xubuntu 13.10 Image[/FONT]
[LIST]
[*][FONT=verdana]AUS - Internode Mirror [Link]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/13.10/release/xubuntu-13.10-desktop-amd64.iso")[/FONT]
[*][FONT=verdana]EU - Ubuntu Mirror [Link]("http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/13.10/release/xubuntu-13.10-desktop-amd64.iso")[/FONT]
[*][FONT=verdana]USA- Ubuntu Mirror [Link]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/13.10/release/xubuntu-13.10-desktop-amd64.iso")[/FONT]
[*][FONT=verdana]Other Mirrors can be found [Here]("http://xubuntu.org/getxubuntu/")[/FONT]
[/LIST]
[/LIST]
[FONT=verdana]

_**Step 0.5 - Create Bootable USB:**_ Once you have downloaded the Xubuntu 13.10 image you'll need to make one of your USB drives bootable, In windows you can use Win32DiskImager.
  
_**Step 1 - Backup!**_  As we will be replacing Chrome OS I highly advise making a recovery image so you restore Chrome OS in the future. Insert your other USB drive (All data on this drive will be lost so ensure its empty), within Chrome navigate to ```
chrome://imageburner
``` then follow the prompts to create a recovery disk. Once the process is complete store this drive somewhere safe.

**_&#8203;Step 2 - Developer Mode:_**  Enabling developer mode will erase all local data from the machine so make a backup of all data or move it to the cloud. To enable developer mode the machine must be up and running then press and hold the "esc" + "refresh" keys together, then press the power button.

The machine will reboot and the Recovery screen will appear:
[IMG]http://i62.tinypic.com/aosz87.jpg[/IMG]

At this screen press Ctrl+D, Press Enter at the next screen.

The machine will now enable developer mode and wipe all local data, may take up to 10 mins to complete. Once its done the machine will automatically reboot and show the OS Verification error.

[IMG]http://i61.tinypic.com/121pl6t.jpg[/IMG]

Press Ctrl+D again to boot into Chrome OS.

**_Step 3 - Enable Boot from USB & Legacy OS:_** - Once in Chrome OS you'll need to complete the initial setup again, once logged in press Ctrl+Alt+T to bring up a terminal then type shell to get a bash prompt. Enter the following command to enable USB Boot & Legacy OS
```
[COLOR=#000000]sudo crossystem dev_boot_usb=1 dev_boot_legacy=1[/COLOR]
```

Now Insert your USB Bootable drive with Xubuntu and reboot your machine. When the OS Verification screen appears you can now press Ctrl+L to enter the SeaBIOS, press "esc" to open the boot menu and select your USB drive using the relevant number.

**_Step 4 - Install Xubuntu_** - Follow on screen prompts to install Xubuntu as normal, you'll need to connect your USB Mouse as the touchpad wont work (Yet), From here on each time you boot the machine it will display the OS Verification error, you'll need to press Ctrl+L then enter to boot from the hard drive (Technically SSD :P) which will load Xubuntu.

**_Step 5 - Fixing Touchpad_** - Once installation is complete we need to fix the touchpad, Open a terminal and run the following command to ensure your system is fully up to date
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Once the updates are complete download Benson Leung's Touchpad Fix to your downloads folder: [https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh)
We'll need to make a small change to the script to correctly fix the touchpad, First we need to determine the current Linux kernel version by running:
```
uname -r
```

It should display something like "3.11.0-20-generic", That is your current version.

Open the script and find the following section

```
# Grab Ubuntu kernel source
apt-get source linux-image-$mykern
cd $mykernver
```

replace it with

```
# Grab Ubuntu kernel source
wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.11.tar.xz
tar -xJf linux-3.11.tar.xz
cd linux-3.11
```

_Note the change to the URL & Directories to reflect your Linux kernel version_

Save the changes and run the script with the following command

```

sudo sh ~/Downloads/cros-haswell-modules.sh

```

Once the updates have been made reboot the machine. The touch pad should now work but its not very responsive. We'll need to tweak the settings to increase responsiveness. Open a terminal and enter

```
cd /usr/share/X11/xorg.conf.d
```

Then edit the following file

```
sudo nano 50-synaptics.conf
```

Below "MatchIsTouchPad "on" add
```
Option "FingerLow" "10"
Option "FingerHigh" "16"

```


Exit nano and save the file (Ctrl+X, save changes Y) then reboot. 

Once rebooted the touch pad should now be much better, you can tweak the settings above if your not happy.
[B][U]
All Done!! [/U][/B]:D
Enjoy your new Chromebook, If i've made any mistakes please let me know.
[/FONT][FONT=verdana]
[B][I]
References: 
[/I][/B][/FONT]
[LIST]
[*][FONT=verdana][Lifehacker Guide]("http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343")[/FONT]
[*][FONT=verdana][http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14](http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14)[/FONT]
[*][FONT=verdana][https://wiki.debian.org/InstallingDebianOn/HP/Chromebook%2014#fnref-db54ab93b28d0bc0a5ce4ed87b617659fc920cca](https://wiki.debian.org/InstallingDebianOn/HP/Chromebook%2014#fnref-db54ab93b28d0bc0a5ce4ed87b617659fc920cca)[/FONT]
[/LIST]

---

### Post by Dane_Jorgensen on 2014-05-05
Thank you!  I've been stuck trying to get this to work.

---

### Post by Poochlookers on 2014-06-10
I have completed everything, however the only thing that bothers me is the OS Verification Failed screen that pops on each and every boot. 

Is there anyway to remove that, I do not care for the Chrome OS am 100% certain I will never be returning to it. 

Thanks !

---

### Post by maddog351 on 2014-08-08
Cool glad all worked well for you. I did some research in the past about removing the Verification screen on boot up and if I remember correctly you need to open the laptop and manually reflash the locked BIOS.

However I can't seem to find the page again

---

### Post by Mohamed_Aly on 2014-11-11
I can't boot to "real worked" shell on developer mode..even i'm sure i'm on the developer channel but the ctr+alt+t gives me black terminal i write shell and then start the sudo commands
but no result appears all give errors "invalid parameter name dev_boot_sdb"

and even i tried to do chrome and ubuntu side by side with crouton but also gives bad command errors 

what's the problem with my chromebook any suggestions??

---

### Post by andrea48 on 2014-11-14
Hi, total noob speaking: first of all thanks for the guide, it's awasome running Ubuntu on Chromebook!
Now here is my question: i installed Ubuntu instead of Xububntu and when it comes to change replace the script i didn't change anything, as i had a different distro and kernel. So i ran the script as it is, and now the Chromebook is working well, but my question is: what did i do running the script without changing it? 

Is it normal that Ubutnu take a long time too boot? (i mean have the same distro installed on a Dell Studio xps13 and it's much faster)

Thanks.

---

### Post by DesertShadow on 2014-12-16
^ Unfortunately Step [#5]("https://github.com/eyecreate/ubuntu-chromebook-installer/issues/5")  no longer seems to work for Intel Chromebook 14. It throws compilation  errors. Tested in Linux Kernel 3.16.0-28-generic Ubuntu 14.10

---

### Post by andrea48 on 2015-01-19
> **DesertShadow said:**
> ^ Unfortunately Step [#5]("https://github.com/eyecreate/ubuntu-chromebook-installer/issues/5")  no longer seems to work for Intel Chromebook 14. It throws compilation  errors. Tested in Linux Kernel 3.16.0-28-generic Ubuntu 14.10

On kernel 3.17 you don't need #5 anymore, just refresh the kernel (it worked on my HP14): you still have to set up the touchpad for responsiveness.
With the new kernel, even if the laptop will work properly, the boot will be slower and it will give you an error : "usb 2-4: string descriptor 0 malformed (err = -61)". I don't know what this mean, and i am trying to find someone with a solution for this error (it will not prevent you from using the laptop, but still it is a pain in the ass).

> **Poochlookers said:**
> I have completed everything, however the  only thing that bothers me is the OS Verification Failed screen that  pops on each and every boot. 

Is there anyway to remove that, I do not care for the Chrome OS am 100% certain I will never be returning to it. 

Thanks !

I am not any computer expert (actually a total noob) but maybe [this]("http://www.newchromebook.com/guide/c720-permanent-linux-laptop-turorial-1-of-3/")  would do the trick? It says "without pressing any key". The tutorial is  actually about the C720, but maybe working on the HP14 as well?

---

### Post by gustavo321oo on 2015-01-22
Hi,

Thank you very much for this article! It is the light at the end of tunnel I have been looking for quite a while...
unfortunatelly I did all the procedures and no luck at the step 3. I keep pressing CTRL + L and nothing happens.
Do you have any idea why this is happening?
If you can help me, I will appreciate very much as I am regret to buy a chromebook, I miss linux :)
My laptop is HP Chromebook 14 4GB memory and ssd.

Kind regards
Gustavo

---

### Post by mobilemeneer on 2015-01-28
Thank you for this good information. I have a question though. Could you please help me get rit of the screen where you have to push ctrl+l everytime to boot ubuntu? i want my hp 14 chromebook always to boot to ubuntu instead of having to press ctrl+l everytime. And i want to totally remove chromos because i need the space completely. Could you please help me with that?

---

### Post by rob125 on 2015-03-17
You can change some of the flags in the HP Chromebook 14 seabios using the gbb utility. This enables default boot in legacy mode and a minimal time at the chromeos white screen.
See the links here:
[http://johnlewis.ie/how-to-make-seabios-the-default-on-your-acer-c720/](http://johnlewis.ie/how-to-make-seabios-the-default-on-your-acer-c720/)
 and end of page here:
[https://wiki.archlinux.org/index.php/HP_Chromebook_14](https://wiki.archlinux.org/index.php/HP_Chromebook_14)

Also someone complains about a long boot time and usb something something error messages. A little googling suggests this is a misleading message and can be fixed by addressing the suspend (UEFI) issue like so: ( from [http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14](http://realityequation.net/installing-elementary-os-on-an-hp-chromebook-14) among other places). Sorry, I lost my main sources for this error rebooting trying to address the issue.


[LIST=1]
[*]Edit */etc/default/grub*, comment out the line with*GRUB_CMDLINE_LINUX_DEFAULT* and add this instead:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic"&#65279;
[/LIST]

Hope this helps. I know your post is a little old at this point.

---

### Post by vk2gpz on 2015-03-29
Thanks so much :)

---

### Post by dannidrengen on 2015-07-28
I have problems in step 4. When i press ctrl+L i only get some bib sounds and nothing else happens. what to do?

---

### Post by drkPu1se on 2015-11-21
**I know I'm reviving an old thread, but I'd like to make a pointer. When I updated after this worked for me (several weeks actually) I believe a kernel update kind of broke my trackpad. What I personally did was just follow Step 5 again and it worked. That's all. Oh and it's worth noting that for me changing how the script gets the kernel source didn't seem to work for me particularly, so I left it how it came in the script and it worked completely flawlessly for me.**

---

