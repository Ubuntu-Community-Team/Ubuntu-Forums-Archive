---
title: "VirtualBox resolution of 1920 x 1080 ?"
date: 2008-03-14
forum: Virtualisation
---

### Post by 01000111 on 2008-03-14
I'm running VirtualBox on Xubuntu v7.10 and have setup a WinXP guest machine so I can watch Netflix streaming video. My PC is connected to a 61" HDTV with a native resolution of 1920x1080. My Xubuntu system uses that resolution and plays HD video perfectly so I know my video card works with 1920x1080. I've installed Guest Additions and have resolution choices of:
800x600
1024x768
1152x864
1280x960
1280x1024
1400x1050 (my current setting which works fine with Netflix except for a lack of full screen video)
1600x1200
1920x1440
2560x1024

Where's 1920x1080? Is this a VirtualBox or Guest Additions limitation? ..or am I just missing something somewhere?

Any assistance is appreciated. 

01000111

---

### Post by Hero of Time on 2008-03-14
Go to the display settings of the virtual machine, select settings > advanced, then under the monitor tab, untick the checkbox 'Hide modes that this monitor cannot display' and it should be available.

---

### Post by 01000111 on 2008-03-14
Thanks, but that checkbox is greyed out.  I think that's because the TV shows up as a generic monitor and I have yet to find a .inf file for it.  Any known registry tweak to fix this instead of using the GUI?

01000111

---

### Post by penguinhugger on 2008-04-01
I had the exact same problem with my widescreen LCD monitor, apparently there are only 4:3 resolutions in the presets  modes.

To get a custom resolution in your Windows guest, start your VM and wait until it has loaded the desktop. Then open a terminal in linux and type this command:

```
VBoxManage controlvm nameofyourVM setvideomodehint width height colordepth
```

In my case for example I used:

```

VBoxManage controlvm winbox setvideomodehint 1920 1200 24
```

Voila, enjoy your full-screen :)

---

### Post by tep200377 on 2008-05-12
Thanks PenguinHugger, that did the trick for me ;)

---

### Post by aggiemarine07 on 2008-09-14
I tried that command it did not do anything to my virtual window.
I have spent hours trying to figure out why I can not get 16:9 resolutions in virtualbox and any help would be greatly appreciated. If there is anything I need to post just reply and I will get back to you with the info.

gw

---

### Post by 01000111 on 2008-09-17
> **aggiemarine07 said:**
> I tried that command it did not do anything to my virtual window.
I have spent hours trying to figure out why I can not get 16:9 resolutions in virtualbox and any help would be greatly appreciated. If there is anything I need to post just reply and I will get back to you with the info.

gw

My final solution was to get xubuntu running in 1920x1080, then start vbox and hit CTRL-F.  That caused it to run in the full screen mode, which used the native mode of xubuntu.

---

### Post by ajhunt on 2008-09-20
> **aggiemarine07 said:**
> I tried that command it did not do anything to my virtual window.
I have spent hours trying to figure out why I can not get 16:9 resolutions in virtualbox and any help would be greatly appreciated. If there is anything I need to post just reply and I will get back to you with the info.

gw

Hi,

I'm running v2.0.2 of VBox and found the following command in Terminal worked for me (although only after closing and restarting VBox itself):

> VBoxManage setextradata winbox CustomVideoMode1 1440x900x24

(Where winbox is the name of my VM. You can setup a number of custom video modes - 15 I think - by incrementing CustomVideoMode*X*)

Hope this helps!

Andy

---

### Post by shaulch on 2009-09-26
> **penguinhugger said:**
> I had the exact same problem with my widescreen LCD monitor, apparently there are only 4:3 resolutions in the presets  modes.

To get a custom resolution in your Windows guest, start your VM and wait until it has loaded the desktop. Then open a terminal in linux and type this command:

```
VBoxManage controlvm nameofyourVM setvideomodehint width height colordepth
```In my case for example I used:

```

VBoxManage controlvm winbox setvideomodehint 1920 1200 24
```Voila, enjoy your full-screen :)

Hi,
i'm using virtual box 3.0.6 , my guest is win7 , the above command doesn't work for me (even worst  before the highest res was 1280x1024 after the command the highest res is 1280x960)
i'm clueless ...

---

### Post by shaulch on 2009-09-26
> **shaulch said:**
> Hi,
i'm using virtual box 3.0.6 , my guest is win7 , the above command doesn't work for me (even worst  before the highest res was 1280x1024 after the command the highest res is 1280x960)
i'm clueless ...

ok , i increased the graphics memory to 128mb and now it works !

thanks all,
Shaul.

---

### Post by mcphranklee on 2011-05-13
Is the command any different if my host machine is Windows 7 and my guest is Ubuntu 10.10 on VirtualBox?
 
My guest machine name is frank-VirtualBox.
 
I have run "$ VBoxManage controlvm frank-VirtualBox setvideomodehint 1920 1080 24" several times, but it doesn't recognize the machine name.
 
Do I have the command wrong for an Ubuntu guest?
 
thanks

---

### Post by linuxmaniack on 2011-05-15
I wouldent try commands, try Installing Guest editions, by going to Devices-Install Guest Editions. (on you virtualbox window) Now go to places, and select the CD drive, which is acturly an iso image. Then Go to no VBoxLinuxAdditions.run and run that. If it comes up with a window, click on run in terminal. (It was a long time since i did this so yeah). If this doesnt Work, go to autorun.sh, and try that. 

After Installing Guest Editions, go to Machine, and then swich to full screen. or, do host+f (host is normally right Ctrl).  

Now, hopefully you should have 1920X1080. 

Hope this helps, 

Linuxmaniack

---

### Post by danomatic on 2011-08-22
I'd like to expand on the above post (just for clarification) as I just resolved this issue using his method. Disregard quotes.

Setup: Kubuntu 11.04 64bit, VirtualBox 4.0.4 with Windows XP SP3 running as a guest. ***The following assumes your Linux host is already setup with the display resolution you like and you want your virtual Windows XP resolution to match ***

1. From Ubuntu, grab "virtualbox-guest-additions" from the repositories and install.

2. You will need an .iso file from the "virtualbox-guest-additions" package.  This is located under /usr/share/virtualbox/VBoxGuestAdditions.iso
   Burn "VBoxGuestAdditions.iso" to a CD and remove it.

3. Using VirtualBox, start a Windows XP session.

4. Using Windows XP, hit START then Run and type in "msconfig.exe"

5. From the "msconfig" program select the "BOOT.INI" tab and select "/SAFEBOOT".

6. Reboot the virtual "Windows XP" session.  You should now be in "safe mode"

7. From the CD you burned earlier start "VBoxWindowsAdditions.exe" 

8. Be sure to select the "D3D" option when installing (this is why we started Windows in SafeMode... can't install D3D with a normal boot).  Once done, remove the CD.

9. In Windows XP, select START then Run and type "msconfig.exe" 

10. From the "BOOT.INI" tab de-select "/SAFEBOOT" 

11. Reboot your virtual Windows XP

12. Once your virtual Windows XP is rebooted, select Right CTRL + F to get your Windows XP screen to "full screen".  There are different methods to get to "full screen" but once there your Windows XP resolution should be whatever you had running in Linux.

---

### Post by gox777 on 2011-12-14
Hey, I'm running a Win XP guest under Linux Mint, and I was having the same problem with getting 1920x1080 in full screen. I did everything mentioned previously in this thread, but what finally fixed it was going to **Machine > Auto Resize Guest Display**. I deactivated it, then reactivated it. After reactivating it, I was able to fullscreen into 1920x1080. (previously, it was only giving me 1280x1024).

Hope that helps someone

---

