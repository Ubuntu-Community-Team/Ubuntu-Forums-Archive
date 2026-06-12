---
title: "Commonly Used Sudo Commands for (*)Ubuntu/Unity Crash Recovery"
date: 2012-05-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-05-01
Hi All,

 I am just carrying this thread over from the now closed Precise thread with hopes of building on it.

Thanks,
Ventrical

---

### Post by ventrical on 2012-05-01
**Re: Commonly Used Sudo Code for (*)Ubuntu/Unity Crash Recovery**             
                                                                Here are some common codes of interest to help with Precise recovery in the event of a crash.

**H**ow to find your souces.list- this list is used to set   repositories and can be done manually. It is also informative to have on   hand if you decide to do a transitional upgrade from Oneiric Ocelot to   Precise Pangolin, Precise Pangolin to  Quantal Quetzel, Quantal Quetzel to Raring Ringtail, Raring Ringtail to Saucy Salamander, Saucy Salamander to Trusty Tahr, Trusty Tahr to Utopic Unicorn, UU to Vivid Vervet, VV to Wily Werewolf, WW to Xenial Xerus, XX to Yakkety Yak, YY to Zesty Zapus, ZZ to Artful Ardvarrk to Bionic Beaver(current development release).
     ```

     [COLOR=Blue]/etc/apt/sources.list[/COLOR] 
```Trusty Tahr will not install: From initial  boot screen from  LiveCD or LiveUSB you may receive verbose characters or  only purple or  black  screen: 
- check here: [/COLOR][http://ubuntuforums.org/showpost.php...47&postcount=5]("http://ubuntuforums.org/showpost.php?p=11518947&postcount=5")

[COLOR=Green]Your beta version of Firefox is Broken- here are two possible fixes:
[/COLOR][http://ubuntuforums.org/showpost.php...9&postcount=18]("http://ubuntuforums.org/showpost.php?p=11530599&postcount=18")
[http://ubuntuforums.org/showpost.php...0&postcount=19]("http://ubuntuforums.org/showpost.php?p=11530670&postcount=19")
[COLOR=YellowGreen] 
[/COLOR] Here is a list of commonly used Ubuntu/Linux terminal Codes (not  neccessarily in order and open to interperetation) of PP Crash Recovery  Codes -[COLOR=Navy]To be updated:[/COLOR]

1. This command is used to auto edit the sources.list file on a previous install and could be considered as a first step to  converting  to Trusty Tahr. However this and other commands may be  moot after  Alpha .iso are released. You can still play it safe and test  the kernels  but breakage may occur nonetheless. ```

     **sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list** 
```
[COLOR=Blue]2.[/COLOR] This command will update your repositories to BB. ```

     **sudo apt-get update && sudo apt-get dist-upgrade** 
```
[COLOR=Navy]3.[/COLOR]This command is inclusive in #2. but is always good to run after removing or purging stuff. ```

     **sudo apt-get update** 
```
[COLOR=Navy]4.[/COLOR]This command is also included in #2. and upgrades any new files that are set in the repositories. ```

     **sudo apt-get dist-upgrade** 
```
[COLOR=Navy][COLOR=Blue]4.(a)[/COLOR][/COLOR]Update-manager   is a fairly important component of the Ubuntu  distribution. As we are   supposed to be testing during the development  phase, this application   would be helped by testing and bug reporting as  well.You can always   make a judgement call as to whether the changes proposed  by   update-manager seem safe or not. If in doubt I think the best way to    proceed is with aptitude: ```

     aptitude update && aptitude  safe-upgrade 
```
This alleviates the concern when  packages/dependencies may not be  fully  synced in the repos. They will  be held back until dependencies  are  satisfied.

[COLOR=Navy]5.[/COLOR]This command is an essential command if you   are a elementary beta tester as it will upgrade the GRUB bootloader   after changes to the system using other commands, are made (like   upgrading a kernel). If you have tried to carry out a proceedure and   wonder why it had not taken effect on the next boot, it is likely that   you did not  sudo update-grub. ```

     **sudo update-grub** 
```
[COLOR=Navy]6.[/COLOR]This command will give you simple information about your system, most commonly used to discover your video adapter. ```

     **lspci** 
```
[COLOR=Navy]7.[/COLOR]This command  will display  version information of the kernel you are using. ```

     **uname -a** 
```
[COLOR=Navy]8.[/COLOR]This  command will tell you what  Version of Ubuntu you are using. It will  help validate  and document  that the prior commands have worked  properly. ```

     **lsb_release -a** 
```
[COLOR=Navy]9.[/COLOR]This  command will continue to install  packages that may have been broken  during download or if your download  unexpectedly terminated or if you  have had a power-failure. ```

     **sudo -i dpkg --configure -a** 
```
[COLOR=Navy]10.[/COLOR]These  two commands can be used  separately if you are at the terminal prompt  from startup. You can get  to the terminal (if you have no desktop) by  pressing the keys  <Crtl+Alt+F1>   It makes booting and restarting  quicker and more  efficient than if you were in a desktop shell. ```

     **sudo reboot -sudo poweroff** 
```
[COLOR=Navy]11.[/COLOR]One that I have found helpful for fixing broken packages is . ```

     sudo apt-get -f install 
```
[COLOR=Blue]12.[/COLOR]Will  install any packages necessary  to fix the broken package if they  are   available . If some necessary  packages are not available you can  use  this to remove the broken one . ```

     sudo apt-get -f remove 
```
[COLOR=Blue]13.[/COLOR]Do  not rely on any inaccurate  information from the user as to whether he   has (or not) added PPAs to  his install. We just get the PPAs and read   them. Then we parse the  PPAs (from ppa-file-name.list to PPA:razz:paname/package  format - which is the format required by the command ppa-purge) ```

     **if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; **for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; **else echo -e "\n\nEmpty or inexistent PPA directory\n\n";** fi 
```
[COLOR=Blue]14.[/COLOR]Attempts to fix a broken OO Install for NVidia 173 users  ```

     #!/bin/bash ##################################################  # fix_oneiric.sh  # Attempts to fix a broken OO Install for NVidia 173 users  # [EMAIL="Effenberg0x0@Launchpad.net"]Effenberg0x0@Launchpad.net[/EMAIL]  #  ##################################################  #  # Save this file to a known location, such as your Home Folder # Execute  it with sudo chmod +x fix-oneiric.sh && sudo bash  ./fix-oneiric.sh  #  ##################################################  # Assume the env vars we need may be wrong and get them  # from safer sources  ROOT_PARTITION=$(mount | grep -i "on / type" | awk '{ print $1}')  ROOT_FS=$(mount | grep -i "on / type" | awk '{ print $5}')  ROOT_WRITE=$(mount | grep -i "on / type" | awk '{ print $6 }')  FIX_USER=$(cat /etc/passwd | grep 1000 | awk 'BEGIN { FS=":" }; {print $1}') ##################################################  # Checks for a rw filesystem and remounts if needed  if [ $ROOT_WRITE == "(ro)" ]; then        mount -f -o remount,rw -t $ROOT_FS $ROOT_PARTITION /  fi  ##################################################  # Make sure GUI sessions are stopped  service stop lightdm  service kill -s KILL $(pidof lightdm)  service stop gdm  service kill -s KILL $(pidof gdm)  killall -s KILL /usr/bin/X   ##################################################  # Fixes user home permissions and ownership  chown $FIX_USER:$FIX_USER /home/$FIX_USER -R && sudo chmod 750 /home/$FIX_USER -R   ##################################################  # Fixes Xauthority bug  mv /home/$FIX_USER/.Xauthority /home/$FIX_USER/.Xauthority.backup   ##################################################  # Removes all nvidia remains  cd /home/$FIX_USER mkdir nvidia_driver cd nvidia_driver apt-get remove  --purge gdm nvidia-173 nvidia-96 nvidia-cg-toolkit  nvidia-current-updates nvidia-173-dev nvidia-96-dev nvidia-common  nvidia-current-updates-dev nvidia-173-updates nvidia-96-updates  nvidia-current nvidia-settings nvidia-173-updates-dev  nvidia-96-updates-dev nvidia-current-dev nvidia-settings-updates   ##################################################  # Downloads nvidia 173 driver   wget [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.31/NVIDIA-Linux-x86-173.14.31-pkg1.run)   ##################################################  # Exports needed and correct environment variables export DISPLAY=:0.0 export XDG_CURRENT_DESKTOP=Unity export  XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/  export COMPIZ_CONFIG_PROFILE=ubuntu export GDMSESSION=ubuntu export  DESKTOP_SESSION=ubuntu export  PATH=/home/$USER:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games  export XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 export  XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 export  DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path  ##################################################  # Run nvidia installer  chmod +x NV*  ./NV*  ##################################################  # Reinstalls all critical DM/DE packages apt-get install --reinstall --fix-broken --allow-unauthenticated lightdm  lightdm-gtk-greeter unity unity-2d unity-2d-launcher unity-2d-panel  unity unity-2d-places unity-greeter unity-lens-music unity-services  unity-2d unity-2d-spread unity-lens-applications  unity-place-applications unity-2d-launcher unity-asset-pool  unity-lens-files unity-place-files unity-2d-panel unity-common  unity-lens-gwibber unity-scope-musicstores compiz compiz-dev compiz-kde  compiz-plugins-main-default compizconfig-backend-gconf  compiz-fusion-bcop compiz-plugins compiz-plugins-main-dev  compizconfig-backend-kconfig compiz-fusion-plugins-extra  compiz-plugins-default compizconfig-settings-manager  compiz-fusion-plugins-main compiz-plugins-extra compiz-core compiz-gnome  compiz-plugins-main ##################################################  # Makes sure lightdm was not started  service lightdm stop  ##################################################  # Fixes lightm config bug (if needed)  if [ ! -f /etc/lightdm/lightdm.conf ]; then sudo touch  /etc/lightdm/lightdm.conf echo -e  "[SeatDefaults]\r\nuser-session=ubuntu\r\ngreeter-session=unity-greeter"  | tee /etc/lightdm/lightdm.conf   ##################################################  # Fixes default-display-manager bug (if needed)  if [ ! -f /etc/X11/default-display-manager ]; then touch  /etc/X11/default-display-manager echo -e "/usr/sbin/lightdm" | tee  /etc/X11/default-display-manager    ##################################################  # Makes sure compiz/compiz-config settings are resetted gconftool-2 --recursive-unset /apps/compiz-1 gconftool-2 --recursive-unset /apps/compizconfig-1   ##################################################  # Backup of compiz/configconfig settings  mv $FIX_USER/.config/compiz-1/compizconfig  $FIX_USER/.config/compiz-1/compizconfig.old mv  $FIX_USER/.config/compiz-1 $FIX_USER/.config/compiz.old mv  $FIX_USER/.compiz-1 $FIX_USER/.compiz-1.old mv  $FIX_USER/.cache/compizconfig-1 $FIX_USER/.cache/compizconfig-1.old   ##################################################  # Update/upgrade the system and reboot  apt-get update && apt-get upgrade reboot now 
```
[COLOR=Blue]15.[/COLOR]Unsolvable  weird crash messages at  most init procedures, ending in a  "black  screen" (or a console  screen), no DM/DE after many attempts to  fix a  user setup (video  driver, env vars, packages, etc).
A: Check for missing /run, or lack of permissions to write to it.    Happens when users upgrade from old releases (that used /var/run and    /var/lock instead of /run and /run/lock). Somehow the new install misses    the creation of /run and /run/lock. 
Check/Fix:```

     if [ ! -d /run -a -d /var ]; then sudo ln -s /var/run /run && sudo mkdir -p /run/lock; fi 
```
[COLOR=Blue]16.[/COLOR]Unable to run apt-get. "Archive directory /var/cache/apt/archives/partial is missing"
Check/Fix: ```

     if [ ! -d /var/cache/apt/archives/partial ]; then sudo  mkdir -p /var/cache/apt/archives/partial && sudo touch  /var/cache/apt/archives/partial/lock && sudo chmod 640  /var/apt/cache/archives/lock && sudo apt-get clean; fi 
```
[COLOR=Blue]17.[/COLOR]System  mounted in "Read Only" mode.  User is unable to edit config files  or  install any package, so no one  can help him. All requested procedures   will fail until it is set rw  again. Happens when user has   errors=remount-ro in fstab.
Check/Fix: ```

     if [ $(sudo mount | grep -i "on / type" | awk '{ print  $6 }') == "(ro)" ]; then sudo mount -f -o remount,rw -t $(sudo mount |  grep -i "on / type" | awk '{ print $5}') $(sudo mount | grep -i "on /  type" | awk '{ print $1}') /; fi 
```
[COLOR=Blue]18.[/COLOR]Just tried installing Precise for the first time today, using Alpha 1. I have an nvidia gs7600 card.
Installation went fine but on reboot the system repeatedly hung without    booting to the Desktop. The 'nomodeset' option did not help.
Updating the packages from the recovery mode terminal didn't work    either, nor did trying to start lightdm after a terminal log in.
What finally allowed booting to the Desktop was removing all nvidia packages and then reinstalling *nvidia-current* (which also installed nvidia-settings). ```

     sudo apt-get purge nvidia*  sudo apt-get install nvidia-current 
```

                                                                                                                                    *                                              [Last edited by cariboo907]("http://ubuntuforums.org/posthistory.php?p=11556749"); December 22nd, 2011 at 04:09 PM..                                                                   Reason: remove hard to read color formatting                                      *             
                                         [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11556749")                                                                                    [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11556749")

---

### Post by ventrical on 2012-05-01
Here is a most recent fix for a libxfont1 downgrade  from pressureman:)

[http://ubuntuforums.org/showpost.php?p=11894101&postcount=106](http://ubuntuforums.org/showpost.php?p=11894101&postcount=106)

---

### Post by ronacc on 2012-05-01
thanks ventrical  , now if cariboo or someone can make this a sticky .

---

### Post by ventrical on 2012-05-01
> **ronacc said:**
> thanks ventrical  , now if cariboo or someone can make this a sticky .
  Thanks ronacc and Cariboo907 and tekstr1der.

---

### Post by ventrical on 2012-05-01
How to fix a lighdm loop.

[http://ubuntuforums.org/showpost.php?p=11894959&postcount=123](http://ubuntuforums.org/showpost.php?p=11894959&postcount=123)

---

### Post by ventrical on 2012-05-01
Followup to pin libxfont1 problem.

[http://ubuntuforums.org/showpost.php?p=11895595&postcount=131](http://ubuntuforums.org/showpost.php?p=11895595&postcount=131)

---

### Post by ventrical on 2012-05-01
For ATI users:
fglrx uses xorg.conf, but syntax has changed in the past year (a 10.10 xorg.conf will get you a black screen).
So after upgrading, run:
     Code:
      sudo rm /etc/X11/xorg.conf sudo aticonfig --initial

---

### Post by ventrical on 2012-05-01
How to set repository templates for QQ.

[http://ubuntuforums.org/showpost.php?p=11877873&postcount=38](http://ubuntuforums.org/showpost.php?p=11877873&postcount=38)
[]("http://ubuntuforums.org/showpost.php?p=11878025&postcount=39")

---

### Post by ventrical on 2012-05-03
Command to stop the lightdm display manager:
```

sudo service lightdm stop
```Command to start gdm (Gnome Display Manager)
```

sudo service gdm start
```

---

### Post by ventrical on 2012-05-07
Here is a fix that was scrounged up by ronacc for  a very touchy nvidia-graphics-installer problem and the new 3.4.n.-n kernel.

[http://ubuntuforums.org/showpost.php?p=11912598&postcount=33](http://ubuntuforums.org/showpost.php?p=11912598&postcount=33)

---

### Post by ventrical on 2012-06-19
I had some problems zsyncing the quantal alternate iso. I left a message for guitara but I think I got the wrong link. Anyways .. anyone  trying to zsync the quantal-alternate-i386.iso can use this code and URL.

zsync -i ./quantal-alternate-i386.iso [http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso.zsync](http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso.zsync)

Thanks..

---

### Post by ventrical on 2012-07-08
If you want to update  the quantal alternate iso it is better to paste this code to terminal:

```

 zsync -i ./quantal-alternate-i386.iso http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso.zsync

```

---

### Post by pressureman on 2012-07-08
> **ventrical said:**
> If you want to update  the quantal alternate iso it is better to paste this code to terminal:

```

 zsync -i ./quantal-alternate-i386.iso http://cdimage.ubuntu.com/daily/current/quantal-alternate-i386.iso.zsync

```

The "-i <input file>" is not necessary if the URL you are fetching is for an existing copy of the file. Zsync will automatically assume you are updating an existing download, use that as the seed, and backup the original file to *.old when finished updating.

---

### Post by ventrical on 2012-08-01
@pressureman

Thanks:)

*note*

If any are having problems with startup video graphics try hitting <ctrl+F1> at the very start of booting your .ISo and then choose F6 and <nomodeset> . I was just able to resolve a problem with an older nVidia adapter card using this process.

*other note*

My apologies for not adding any extra content to U+1 or here in the forums. Iv'e been just so busy .

regards, ventrical

---

### Post by cariboo on 2012-08-01
> **ventrical said:**
> @pressureman

Thanks:)

*note*

If any are having problems with startup video graphics try hitting <ctrl+F1> at the very start of booting your .ISo and then choose F6 and <nomodeset> . I was just able to resolve a problem with an older nVidia adapter card using this process.

*other note*

My apologies for not adding any extra content to U+1 or here in the forums. Iv'e been just so busy .

regards, ventrical

Just to add a bit of a correction to the above post. Pressing any key will bring up the menu when booting from the iso.

---

### Post by ventrical on 2012-08-02
I stand corrected ! :)

---

### Post by ventrical on 2012-09-02
Code to remove ppas:

remove-

[COLOR=#000000][COLOR=#0000BB]sudo add[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]repository [/COLOR][COLOR=#007700]--[/COLOR][COLOR=#0000BB]remove ppa[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]someppa[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]ppa  

[/COLOR][/COLOR]purge-
[COLOR=#000000][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install ppa[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]purge
sudo ppa[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]purge ppa[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000BB]someppa[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]ppa  [/COLOR][/COLOR]

---

### Post by ventrical on 2012-09-12
Code to blacklist 'nouveau'

**6) Blacklist nouveau**
     Code:
     $ sudo nano /etc/modprobe.d/blacklist.conf 
Add these lines to the end of blacklist.conf:
     Quote:
                                                 # Manually added to avoid conflict with nvidia proprietary module
blacklist nouveau
alias nouveau off      

-------------------------**7) Check for nvidia in blacklists**
Make sure you do not have nvidia blacklisted in other files at /etc/modprobe.d/*
 	Code:
 	$ cd /etc/modprobe.d $ grep -iHnr "nvidia" * 
The commands above should return only this:
 	Quote:
 	 	 		 			 				blacklist-framebuffer.conf:18:blacklist nvidiafb 			 		 	 	 
**8) Create a directory for the driver:**
It's useful to keep the installer at a known place (for eventuall  reinstalls). Create a directory within your user $HOME for the Nvidia  installer:
 	Code:
 	$ mkdir -p $HOME/Downloads/nvidia-drivers && cd $HOME/Downloads/nvidia-drivers 
**9) Get the installer:**
Download Nvidia installer for your architecture (32-bit or 64-bit). 
Run **"uname -a"** if you need to check whether you are using 32-bit or 64-bit. 

**For 32-bit:**
 	Code:
 	wget [ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86/304.43/NVIDIA-Linux-x86-304.43.run) 
**For 64-bit:**
 	Code:
 	wget [ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/304.43/NVIDIA-Linux-x86_64-304.43.run) 
**OBS:** If the direct links above fail, go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) nd get your drivers there.

**10) Check the download:**
Check whether the file was downloaded/saved to the directory we created:
 	Code:
 	$ ls -lha NVIDIA* 
 	Quote:
 	 	 		 			 				-rw-rw-r-- 1 ahsl ahsl  62M Aug 28 05:04 NVIDIA-Linux-x86_64-304.43.run 			 		 	 	 
**OBS:** The result above is for the 64-bit installer. You  might have downloaded the 32-bit version depending on your system  specs/arch. 

**11) Make the installer executable:**
 	Code:
 	$ sudo chmod +x NVIDIA* 
**12) Switch to a Virtual Terminal and stop lightdm/X:**
- Press Ctrl+Alt+F6 and login with your user/pass
 	Code:
 	$ sudo service lightdm stop $ sudo killall -s KILL /usr/bin/X 
**13) Install:**
Run the Nvidia installer:
 	Code:
 	$ sudo ./NVIDIA* 
**OBS:** You should answer YES to ALL questions. The only  question I answer NO is the one about DKMS. I have had some problems  with it. YMMV.

**14) Restart:**
Back to the console prompt, restart the PC:
 	Code:
 	$ sudo reboot now 
**15) (Optional) Sing a happy song during boot:**
I suggest this one: [http://www.youtube.com/watch?v=EcPxszGTCa8](http://www.youtube.com/watch?v=EcPxszGTCa8)

**Problems:**
**1) If you can't see lightdm (stuck in console mode on boot)**
[LIST]
[*] Is nouveau really blacklisted? Is nvidia *not* blacklisted? See steps 6 and 7. Which modules are loaded? Check with:
 	Code:
 	$ lsmod | grep -i nv $ lsmod | grep -i nouveau 
[*] Is anything non-standard being passed to the kernel cmdline at boot  via Grub? See step 3. You only need special parameters if you know what  they do.
[*] Did the install procedure went through with no errors? You can re-run it just to be sure. Repeat steps 12, 13 and 14 only.
[/LIST]
**2) If you can't enter the Ubuntu session (loop back to lightdm):**
[LIST]
[*] Are you using an outdated version of xorg packages? Were they pinned / Hold? Check steps 1 and 5.
[/LIST]
**3) If you have no Dash / Launcher, nothing in Unity:**
[LIST]
[*] Maybe this is a failed install with no GLX support. Try this:
[*] Press Ctrl+Alt+T. If you don't get a terminal, switch to a VT with Ctrl+Alt+F6.
[*] Run these commands to check for glx support:
 	Code:
 	$ sudo apt-get install nux-utils mesa-utils $ /usr/lib/nux/unity_support_test $ glxgears -info 
[*] If you have no support for GLX, you have failed to follow the steps above and should re-do the procedure.
[*]  If you have glx support, the Unity plugin is not loaded. At the terminal / VT run:
 	Code:
 	$ sudo apt-get install compizconfig-settings-manager  $ DISPLAY=:0.0 ccsm 
And activate the Unity plugin.
[/LIST]
**4) If you have a low performance, tearing, artifacts:**
[LIST]
[*]  You might have to disable / enable "Sync to VBlank" in  compizconfig-settings-manager (ccsm) / OpenGL Plugin to increase  performance / avoid tearing depending on how things work for this card.
[*] You might have to disable / enable "Sync to VBlank" in  nvidia-settings / "OpenGL Settings" to increase performance / avoid  tearing, depending on how things work for this card.
[*] You might have to enable "Force fullscreen redraws (buffer swap) on  repaint" on ccsm / Workarounds Plugin to fix tearing / repaint  problems.
[/LIST]
**5) Monitors not configured:**
[LIST]
[*] Maybe the secondary  monitor will be automatically activated, maybe it will not. I don't know  why this is apparently not consistent.
[*] Go to Dash / Nvidia-settings and activate / configure the primary/secondary monitor if needed.
[/LIST]

**OBS:**
- Yes, there are typos above.
- I started typing before you posted the second msg to this thread, so 90% of it does not apply to your problem. Yey :)
- You probably can benefit from steps 4 and 5 in the "Problems" section.  Unless the procedure in Problems/Step 1 shows you not on nvidia but  nouveau or, worse, llvmpipe or something (commands in step 3 can test  that). In which case everything above applies :)
 
Regards,
Effenberg

                

---------------------------------------

(thanks  effenberg)

---

### Post by ventrical on 2012-10-23
**v3.7-rc2-raring**


Here is the best and simple way  to install kernek RCs,

     Quote:
                                                                      Originally Posted by **cecilpierce**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12310844#post12310844")                 
                 [I]I would like to try it, what order do I install the 4 .deb files ?
When I tried it I got a couple errors about vbox and something else, cant remember, dah![/I]
                                 
what i do with new kernel :
- download the required debs (2 headers + 2 images) into an empty folder
- then from that folder:  sudo dpkg -i *

Thanks to dino99

---

### Post by ventrical on 2012-10-23
If you are having problems with nvidia drivers and the new kernel RC  then fooman has the answer.
**v3.7-rc2-raring**


                                  **Re: Kernel 3.7-rc1**             
                                                                lost the  nvidia drivers when i first booted up (GTX480),  no top panel or  unity....had to right-click on desktop to open terminal.  from there i  opened firefox and got the command to install the x-edgers PPA:
   ```

     sudo add-apt-repository ppa:xorg-edgers/ppa 

```ran that,  then opened synaptic from the terminal (sudo synaptic),   updated the repos,  let it install all updates plus the edgers *nvidia-current* (vers. 310.14).  rebooted and all is well:

     Code:
     jackel@jackel-GA-990FXA-UD5:~$ cat /etc/lsb-release DISTRIB_ID=Ubuntu DISTRIB_RELEASE=12.10 DISTRIB_CODENAME=quantal DISTRIB_DESCRIPTION="Ubuntu 12.10"  jackel@jackel-GA-990FXA-UD5:~$ uname -r 3.7.0-030700rc2-generic 
...working great!!  :smile:

---

### Post by ventrical on 2013-03-05
Anyone having problems changing their hostnames or want to rename them (if you did not get a chance to do so during install) then here is an excellent link to achieve that.

[http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html](http://www.webupd8.org/2012/03/how-to-change-hostname-computer-name-in.html)

---

### Post by ventrical on 2013-03-11
If you download a document file (or any other file for that matter) and conventional ways of searching for that file do not work then you can use the gnome-terminal and enter the code:



dpkg -S name_of_downloaded_or_installed_file_here


This will give you the path and directory name as to where the file is.
 For example, if you are searching for the mir-doc files - here are the results 
of that code:

```

mir-doc: /share/doc/mir-doc/html/inherit_graph_89.png
mir-doc: /share/doc/mir-doc/html/inherit_graph_116.map
mir-doc: /share/doc/mir-doc/html/buffer__initializer_8h__dep__incl.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_null_logger__inherit__graph.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_native_client_platform_factory__inherit__graph.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_mir_binder_rpc_channel__inherit__graph.png
mir-doc: /share/doc/mir-doc/html/surfaces_2surface_8h__incl.map
mir-doc: /share/doc/mir-doc/html/android__client__buffer_8h__dep__incl.png
mir-doc: /share/doc/mir-doc/html/mir__binder__rpc__channel_8h__incl.md5
mir-doc: /share/doc/mir-doc/html/registration__order__focus__sequence_8h__dep__incl.png
mir-doc: /share/doc/mir-doc/html/size_8h__incl.map
mir-doc: /share/doc/mir-doc/html/inherit_graph_104.md5
mir-doc: /share/doc/mir-doc/html/search/all_79.html
mir-doc: /share/doc/mir-doc/html/mir__basic__rpc__channel_8h__incl.png
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_client_context__inherit__graph.md5
mir-doc: /share/doc/mir-doc/html/classmir_1_1surfaces_1_1_graphic_region.html
mir-doc: /share/doc/mir-doc/html/structmir_1_1shell_1_1_surface_creation_parameters-members.html

```

etc...

---

### Post by ventrical on 2013-03-30
Command line code on how to tell which video driver you are using:

```


/usr/lib/nux/unity_support_test -p -f


```

Sould give a report somthing like this:

```

ventrical@ventrical-AcerAMD64bitDual:~$ /usr/lib/nux/unity_support_test -p -f
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce G210/PCIe/SSE2/3DNOW!
OpenGL version string:  3.3.0 NVIDIA 304.84

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
ventrical@ventrical-AcerAMD64bitDual:~$ 



```

---

### Post by zika on 2013-03-30
> **ventrical said:**
> For ATI users:
fglrx uses xorg.conf, but syntax has changed in the past year (a 10.10 xorg.conf will get you a black screen).
So after upgrading, run:
     Code:
      sudo rm /etc/X11/xorg.conf sudo aticonfig --initialUser in our LoCo stumbled upon this and (of course since copy&paste is prefered method worldwide...) complained... There should be some divider between these two commands...
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ventrical
sudo aticonfig --initial
```
We use not to r(e)m(ove) file but just m(o)ve it, so, in case of any trouble, file can be easily retreived...

---

### Post by cariboo on 2013-03-30
> **zika said:**
> User in our LoCo stumbled upon this and (of course since copy&paste is prefered method worldwide...) complained... There should be some divider between these two commands...
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ventrical
sudo aticonfig --initial
```
We use not to r(e)m(ove) file but just m(o)ve it, so, in case of any trouble, file can be easily retreived...

Shouldn't the command look like this?


```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ventrical && sudo aticonfig --initial
```

---

### Post by zika on 2013-03-30
> **cariboo907 said:**
> Shouldn't the command look like this?


```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ventrical && sudo aticonfig --initial
```Yes if You want to keep it in one row... De gustibus non est disputandum...
The way the were written originally was a typo... That was the point of my post... To correct an obvious typo...
Do not shoot the messenger... ;)

---

### Post by schragge on 2013-03-30
I wonder why this thread is under *Ubuntu +1*, and not in [Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100). The commands mentioned here so far are not raring-specific, are they?

---

### Post by cariboo on 2013-03-30
> **schragge said:**
> I wonder why this thread is under *Ubuntu +1*, and not in [Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100). The commands mentioned here so far are not raring-specific, are they?

They aren't specific to any +1 version, but we seem to get quite a few new users that have no idea how to solve a problem via the command line, so the thread will stay where it is, to help them on their way to fixing a broken installation.

---

### Post by ventrical on 2013-04-08
> **zika said:**
> User in our LoCo stumbled upon this and (of course since copy&paste is prefered method worldwide...) complained... There should be some divider between these two commands...
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.ventrical
sudo aticonfig --initial
```
We use not to r(e)m(ove) file but just m(o)ve it, so, in case of any trouble, file can be easily retreived...

Yes .. thanks .. I was busy that day , obviously :) My bad.

---

### Post by ventrical on 2013-04-08
> **cariboo907 said:**
> They aren't specific to any +1 version, but we seem to get quite a few new users that have no idea how to solve a problem via the command line, so the thread will stay where it is, to help them on their way to fixing a broken installation.


Thanks.  I have been unbelievably busy. Unfortunately the wiki may suffer from non-updated content as well as  here on the sticky. I  am hoping to have another stretch of spare time come up soon and I have some utility  duties on the list.  This may not be until after the final release of raring .. but I am still  on to getting this updated as soon  as I can. :)

Regards,

Ventrical

---

### Post by cariboo on 2013-04-08
We are discussing bringing back the Tutorial and Tips sub-forum, as for most the wiki experiment has been a dismal failure. I'm also not sure what is going to happen with the U+1 testing team, as Effenberg0x0 was going through some personal probelms, and has seemed to have disappeared.

---

### Post by ventrical on 2013-04-09
> **cariboo907 said:**
> We are discussing bringing back the Tutorial and Tips sub-forum, as for most the wiki experiment has been a dismal failure. I'm also not sure what is going to happen with the U+1 testing team, as Effenberg0x0 was going through some personal probelms, and has seemed to have disappeared.


  I had noticed that users both verteran and new seem to be centered and affixed to Ubuntu-forums. Embedding a message base into the wiki would have been useless duplicity. All the hard, cutting edge action is at ubuntu-forums scratch pad.  effenberg said he would be back . He owns  U+1 wiki. 

 And as for U+1 ... is it not obsoleted?? If so , then the wiki was doomed to failure anyways not by my hands.

---

### Post by ventrical on 2013-04-09
Cleaned out the  U+1 Testers wiki and renamed it Rolling Release in my sig.

Regards,

Ventrical

---

### Post by effenberg0x0 on 2013-04-09
> **ventrical said:**
> I had noticed that users both verteran and new seem to be centered and affixed to Ubuntu-forums. Embedding a message base into the wiki would have been useless duplicity. All the hard, cutting edge action is at ubuntu-forums scratch pad.

effenberg said he would be back . He owns  U+1 wiki.

 And as for U+1 ... is it not obsoleted?? If so , then the wiki was doomed to failure anyways not by my hands.

Hey :) Sorry for disappearing, I had to take some time off and deal with personal stuff... I completely missed this cycle, but I'll be here for the next.
BTW, I own nothing, everything is free as in (free beer|speech) :P
There's a lot to do in testing-documentation, dev. and doc. of testing methods/best-practices, user-oriented documentation, etc. There has always been, there will always be room for contribution and improvement, whatever the development model is (rolling, bumping, jumping, swimming, etc). And we're not even talking seriously about testing in other platforms (mobile, etc). We'll think of something to do next cycle and, obviously, stuff to bother Nick with.

Regards,

---

### Post by ventrical on 2013-04-09
> **effenberg0x0 said:**
> Hey :) Sorry for disappearing, I had to take some time off and deal with personal stuff... I completely missed this cycle, but I'll be here for the next.
BTW, I own nothing, everything is free as in (free beer|speech) :P
There's a lot to do in testing-documentation, dev. and doc. of testing methods/best-practices, user-oriented documentation, etc. There has always been, there will always be room for contribution and improvement, whatever the development model is (rolling, bumping, jumping, swimming, etc). And we're not even talking seriously about testing in other platforms (mobile, etc). We'll think of something to do next cycle and, obviously, stuff to bother Nick with.

Regards,

Good to you you back effenberg! :)

---

### Post by ventrical on 2013-04-09
@effenberg

I pretty well butchered the tester wiki and am preparing it for 'Rolling Release' because the Raring links are all but obsoleted now and can't be zsynced (at least from here).  When you get time .. lemme know where you would like to go with it and/or any other ideas you have.

---

### Post by jerrylamos on 2013-04-12
Curious to see how "rolling release stable" and "rolling release unstable" will be differentiated in Daily Build.  

As I do frequent updates the disk usage as defined by df gets more and more, despite all my efforts to apt-get clean, remove, autoremove, purge, etc.  Since the disk usage grows that means to me more and more code that's not being used especially on amd64 so I do a re-install and may get over 10% disk space back.  In the days of large disks who cares?  I test using multiple stable and unstable partitions, and SSDs of any size are expensive.

Also curious to see how U+1 forum is handled, it's been very useful to me for years.  The general "ubuntuforums" is not nearly so useful since the new stuff is very diluted, scattered, and I'm not expert enough in tips and hints specific searching.

---

### Post by jerrylamos on 2013-04-12
BTW, as Canonical concentrates on smartphones and tablets (smartwatches?), pc's and pc releases are becoming less of interest perhaps occasional rolling release reflects their disinterest....

---

### Post by effenberg0x0 on 2013-04-12
> **jerrylamos said:**
> 
Also curious to see how U+1 forum is handled, it's been very useful to me for years.  The general "ubuntuforums" is not nearly so useful since the new stuff is very diluted, scattered, and I'm not expert enough in tips and hints specific searching.

Me too. I think this subforum has created sort of a community and its own culture and changing its purpose / communication might be a decision we will regret later if things, once again, change. 
We know decisions in FOSS and Ubuntu are sometimes made and later unmade, with or without regret, which is comprehensible: People make them with the information they have in hands and no one can really predict the future with 100% accuracy. 

I'd hate to see this community disappear or lose relevance. And I'm not convinced we'll stick to one development model or another.
We can all agree that we're testers: We'll continue testing/reporting, talking about features and bugs, with the goal of helping development and improvement. Also, some features can't simply be developed and implemented in a rolling model without some very alpha testing to check viability. Adding some very alpha ideas to rolling development will be too dangerous to be pushed to non-technical users updates. What I'm saying is that, to a certain level, testers are always needed, no matter what the development model is.

So maybe we should keep keep the subforum as "U+1" and operate as usual. 

However, if for any reason we are required to change the name of the subforum, I'd advocate for "Ubuntu Testers". This name would finally acknowledge who we are and what we have been doing here for some years now... It would also present us and our activities properly to the larger Ubuntu Community. As a bonus, it would make our activities (as well as the risks involved in it) clearer to newbies.

I am confident any changes to our subforum name and activities won't be taken by forum admins without a proper discussion. And a proper discussion regarding this subforum is only acceptable if it involves its users - we should be able to express our opinions if any change is to be made. Also, we have many Ubuntu Members and Forum Admins and Moderators using this subforum. These people definitely understand what we do here and I believe they are likely to make thoroughly considered decisions.

(This is IMHO anyway).

Regards,
Effenberg

---

### Post by cariboo on 2013-04-12
> **effenberg0x0 said:**
> 

So maybe we should keep keep the subforum as "U+1" and operate as usual. 



Funny you should mention that, as we were talking about that very thing last week. I plan on putting up a poll in the next couple of days, to see how the tester all feel about whether we should keep closing the sub-forum and changing to the name of the next version, or simply naming it U+1, and continue on as we have.

---

### Post by effenberg0x0 on 2013-04-12
> **cariboo907 said:**
> Funny you should mention that, as we were talking about that very thing last week. I plan on putting up a poll in the next couple of days, to see how the tester all feel about whether we should keep closing the sub-forum and changing to the name of the next version, or simply naming it U+1, and continue on as we have.
Hey Cariboo, 
I never really liked the idea of closing and restarting each cycle. Many bugs persist between releases, some concepts, workarounds, knowledge apply to all releases, etc. I'm very much in favor of not closing it anymore. Hopefully that's what the poll results will indicate. 

Question: Let's say people decide to stop closing it. Would we keep the closed ones in the archive, as they are now, or would we merge them back? (is it even possible?)
I mean, if we decide that it makes sense to not restart the sub-forum anymore, maybe it would make no sense to have the sub-forum content of the previous releases archived.

Regards,
Effenberg

---

### Post by cariboo on 2013-04-12
I won't say no to merging the old archives into the U+1, but at this time, I really doubt it, I'll have to bring it up with the forum council first. The way we've always done it, was started before the present forum council, and as such we have so far just followed tradition. We are making some changes that we hope will undo some of the restrictions previous councils have put in place, but we won't be making wholesale changes at any time soon.

---

### Post by ventrical on 2013-04-12
> **cariboo907 said:**
> Funny you should mention that, as we were talking about that very thing last week. I plan on putting up a poll in the next couple of days, to see how the tester all feel about whether we should keep closing the sub-forum and changing to the name of the next version, or simply naming it U+1, and continue on as we have.

  I think this would be a great idea because merging the older threads would in fact be like a rolling model. Other testers would not be then so discouraged to "bump" an older thread up for comparative analisys to the current cycle. There will always be a symbiosis with previous cycles and keeping the U+1 thread a 'rolling' thread may be a good model to experiment with and may even set a template for the eventual rolling distro models to come. If you want to defragment the *knowledge base* then this would be the way to do it.IMO

---

### Post by cariboo on 2013-04-12
We've got 8 development release sub-forums archived, and even though there are some underlying bugs that are still bothersome, much of the information in those sub-forums is nowhere near relevant today. The one big problem I see, is that the archived threads aren't indexed by Google at the moment, and if they are folded back into the U+! sub-forum, we could have quite a few more necromanced threads, than we are seeing already, recently we seem to be seeing 10- 15 threads a day brought back from the dead, that have to be dealt with. We don't want to put so much work on the moderation team with the things they deal with day to day that it isn't fun for them to do what they do any more, so we'll really have to think long and hard on this proposal.

---

### Post by ventrical on 2013-04-12
Yes, that would be a tremendous load, however, suppose  that , for experiemental purposes, it is proposed to the Forum Council to open the most previous archive (Quantal Quetzal)  and put it in it's own forum under Specialized Support under a suggested heading "U+1 Ammendments-Quantal".  I am sure that a small rule can be implied that the forums topics are to be topical for research and ammendments only in relationship  to the current U+1 cycle. So there would always be two back. When '13.10' cycle is ready to roll it would be two back  - to raring and quantal.

ie;

Ubuntu Specialised Support
   Ubuntu +1 (SS)
     Ubuntu +1 Ammendments Raring
       Ubuntu + 1 Ammendments Quantal


It's like being in a library. You have current  research information in front of you but you have to examine an archive. The archive is locked in another room so you have to take an extra step to get there.  After examining the archive material it is found that there is something significant to current or something current that is significant to editing an ammendment into the archive. Since the archive is locked , it cannot be edited. Of course the information can be pointed to in a link, quoted and corrected in the current volume, copy and pasted .. etc.. but would it not be much more efficient to make the ammendment  as an addendum to the topic matter of any particular subject in question?

  I have noticed that people are always referring to " something similar in the last cycle" ... um.. it's sort of like loosing your keys if you get what I mean. This way the knowledge base may be utilized more often and it could save some downtime.

Regards,
Ventrical

---

### Post by effenberg0x0 on 2013-04-12
Maybe U+1 sub-forum (current or archive)  content shouldn't be indexed by Google at all,  as it may provide nontechnical users with dangerous info...  And that is easily doable via robots.txt,  Google's Webmaster Tools,  etc. 

That would free us to merge the archives to current, reduce the risk to nontechnical users created by Google hits to U+1 content and,  given our small traffic in comparison to General Help, it would hardly impact UbuntuForums popularity in Google searches.  


Also,  I believe we could merge the archives while keeping its threads closed,  to avoid necromancy. 

It's something to consider anyway.

---

### Post by PJs Ronin on 2013-04-12
I belong to another site where it is policy that posts for "like issues" are contained in a single sub-forum.   We now have single threads approaching 2,300 pages and 34,000 posts long.   Difficult to read, easy to become confused by outdated issues and almost impossible to follow individual points.

---

### Post by cariboo on 2013-04-12
> **PJs Ronin said:**
> I belong to another site where it is policy that posts for "like issues" are contained in a single sub-forum.   We now have single threads approaching 2,300 pages and 34,000 posts long.   Difficult to read, easy to become confused by outdated issues and almost impossible to follow individual points.

Sort of like the [conky ]("http://ubuntuforums.org/showthread.php?t=281865")thread in the Cafe, 2175 pages and 21,748 replies, and well over 6.4 million views.

I don't think we'll see any of that type of thread here, but I do worry about threads that have old or bad information being brought back to life, until we get the auto-close plugin enabled.

---

### Post by ventrical on 2013-04-18
Anyone know what happened to :

sudo -i  dpkg --configure -a

  I even tried it in Precise and it comes up with an error. 

My follow-up question is;

 Does there actually have to be broken packages for this to work?

 Regards,
Ventrical

---

### Post by zika on 2013-04-18
> **ventrical said:**
> Anyone know what happened to :

sudo -i  dpkg --configure -a

  I even tried it in Precise and it comes up with an error. 

My follow-up question is;

 Does there actually have to be broken packages for this to work?

 Regards,
Ventrical
What error is produced?

---

### Post by stinkeye on 2013-04-18
> **ventrical said:**
> Anyone know what happened to :

sudo -i  dpkg --configure -a

  I even tried it in Precise and it comes up with an error. 

My follow-up question is;

 Does there actually have to be broken packages for this to work?

 Regards,
Ventrical
Doesn't the -i mean install.
Is it just ```
sudo dpkg --configure -a
```

---

### Post by zika on 2013-04-18
> **stinkeye said:**
> Doesn't the -i mean install.
Is it just ```
sudo dpkg --configure -a
```„-i“ is used as a switch for „sudo“...
Let's see what is the error...

---

### Post by ventrical on 2013-04-18
> **zika said:**
> „-i“ is used as a switch for „sudo“...
Let's see what is the error...


Exactly .. it is needed for root permissions. Back over a year ago I was doing an install/update and there was a lightning strike here. The power went out in the middle of while those packakes were being unpacked. I used that command and it worked just perfectly. Now, I guess the only way I can  prove this is to do an update and emulate a power outage.

 Anyways , I was just trying to get some confirmation as there is a discussion about this in another thread.

---

### Post by ventrical on 2013-04-18
> **stinkeye said:**
> Doesn't the -i mean install.
Is it just ```
sudo dpkg --configure -a
```


The -i  is for root, However .. I tired it as you had posted and it just did nothing - no error at all. I think that command is specifically for broken packages. I ised it with the (-i)  over a year ago when there was a power outage in my area and that command successfully fixed all the  broken packages.

---

### Post by zika on 2013-04-18
> **ventrical said:**
> The -i  is for root, However .. I **tired** it as you had posted and it just did nothing - no error at all. I think that command is specifically for broken packages. I ised it with the (-i)  over a year ago when there was a power outage in my area and that command successfully fixed all the  broken packages.Man files are not so far away:
```
--configure package...|-a|--pending              
              Configure a package which has been unpacked but not yet  config&#8208;
              ured.   If  -a  or  --pending  is  given instead of package, all
              unpacked but unconfigured packages are configured.


              To reconfigure a package which has already been configured,  try
              the dpkg-reconfigure(8) command instead.


              Configuring consists of the following steps:


              1.  Unpack  the  conffiles, and at the same time back up the old
              conffiles, so that they can be restored if something goes wrong.


              2. Run postinst script, if provided by the package.

```

---

### Post by ventrical on 2013-04-18
The:

sudo -i dpkg --configure -a

worked perfectly  from terminal (not GUI terminal) [alt +F1 terminal]. I had dowloaded 75MB of updates and pulled the plug  just as synaptic was starting to unpack  the updates. Of course all packages were then updated with that command.

---

### Post by ventrical on 2013-04-18
> **zika said:**
> Man files are not so far away:
```
--configure package...|-a|--pending              
              Configure a package which has been unpacked but not yet  config&#8208;
              ured.   If  -a  or  --pending  is  given instead of package, all
              unpacked but unconfigured packages are configured.


              To reconfigure a package which has already been configured,  try
              the dpkg-reconfigure(8) command instead.


              Configuring consists of the following steps:


              1.  Unpack  the  conffiles, and at the same time back up the old
              conffiles, so that they can be restored if something goes wrong.


              2. Run postinst script, if provided by the package.

```


 My bad ..

 It's 

sudo -i dpkg --configure -a

not 

sudo dpkg -i --configure -a

thanks

---

### Post by zika on 2013-04-18
> **ventrical said:**
> My bad ..

 It's 

sudo -i dpkg --configure -a

not 

sudo dpkg -i --configure -a

thanks
It was like that in Your original post and we (re)solved that in prevoius posts...

---

### Post by ventrical on 2013-04-18
> **zika said:**
> It was like that in Your original post and we (re)solved that in prevoius posts...

No zika...

Please see  the correction here:

[http://ubuntuforums.org/showthread.php?t=2136435&p=12607444#post12607444](http://ubuntuforums.org/showthread.php?t=2136435&p=12607444#post12607444)

which was pasted from my post here:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

my bad :)

---

### Post by schragge on 2013-04-18
Sorry, but what is the purpose of **-i** here? I mean why do you need to cd to */root* and execute */root/.profile*? Wouldn't just
```
sudo dpkg --configure -a
``` be enough?
```
sudo -i dpkg --configure -a
``` is equivalent to
```
sudo su -lc 'dpkg --configure -a'
``` which in turn is roughly the same as
```

sudo bash -lc 'cd /root; dpkg --configure -a'

```

---

### Post by zika on 2013-04-18
> **schragge said:**
> Sorry, but what is the purpose of **-i** here? I mean why do you need to cd to */root* and execute */root/.profile*? Wouldn't just
```
sudo dpkg --configure -a
``` be enough?
```
sudo -i dpkg --configure -a
``` is equivalent to
```
sudo su -lc 'dpkg --configure -a'
``` which in turn is roughly the same as
```

sudo bash -lc 'cd /root; dpkg --configure -a'

```No obvious (to me) reason... You're just completely right... As far as I know...

---

### Post by zika on 2013-04-18
> **ventrical said:**
> No zika...

Please see  the correction here:

[http://ubuntuforums.org/showthread.php?t=2136435&p=12607444#post12607444](http://ubuntuforums.org/showthread.php?t=2136435&p=12607444#post12607444)

which was pasted from my post here:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

my bad :)You've got me... I'm unable to follow this circulus vitiosus...

---

### Post by schragge on 2013-04-18
> **zika said:**
> No obvious (to me) reason... You're just completely right... As far as I know...
I can still see the purpose of it with *apt-get* if you are behind a proxy and */root/.profile* contains
```
export http_proxy=http://example.com:3128
```, although I'd prefer to specify the proxy in */etc/apt/apt.conf*, but with *dpkg*?

---

### Post by ventrical on 2013-04-18
@zika

Don't worry about it.

@ cariboo907

Could you please edit this post.

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

It is #9. on the list where it's states  'sudo dpkg -i --configure -a'  It should be 'sudo -i dpkg --configure -a

Thank you.

@all

  Most of the commands in this thread are copied and pasted Looks like one slipped through the net.

---

### Post by ventrical on 2013-04-18
> **schragge said:**
> Sorry, but what is the purpose of **-i** here? I mean why do you need to cd to */root* and execute */root/.profile*? Wouldn't just
```
sudo dpkg --configure -a
``` be enough?
```
sudo -i dpkg --configure -a
``` is equivalent to
```
sudo su -lc 'dpkg --configure -a'
``` which in turn is roughly the same as
```

sudo bash -lc 'cd /root; dpkg --configure -a'

```

  I just copy and paste them as they come. When I first used this command I was told that I needed to be root (which is the -i). I had tried to  use just the dpkg  with out the sudo -i but it did not work at that time.

---

### Post by zika on 2013-04-18
> **ventrical said:**
> I just copy and paste them as they come. When I first used this command I was told that I needed to be root (which is the -i). I had tried to  use just the dpkg  with out the sudo -i but it did not work at that time.That must have been before 8.04... Since then it worked for me like a clock...

---

### Post by schragge on 2013-04-18
To temporarily gain root privileges, just *sudo* would be enough:
```
sudo dpkg --configure -a
```
The *-i* option is only needed if you also want to execute */root/.profile* to set up environment for root user. But if the only way to become root is through *sudo* as it is on Ubuntu then this could (and IMHO should) be done by editing */etc/sudoers*.

---

### Post by ventrical on 2013-04-18
> **schragge said:**
> To temporarily gain root privileges, just *sudo* would be enough:
```
sudo dpkg --configure -a
```
The *-i* option is only needed if you also want to execute */root/.profile* to set up environment for root user. But if the only way to become root is through *sudo* as it is on Ubuntu then this could (and IMHO should) be done by editing */etc/sudoers*.

Yes .. zika had pointed that out to me some time ago and I made the correction at the wiki but I cannot make the correction here as I do not have moderator privlidges. That's my whole point.

---

### Post by ventrical on 2013-04-18
> **zika said:**
> That must have been before 8.04... Since then it worked for me like a clock...


Actually it was during the Oneric Ocelot cycle. I'll see if I still have that install and check for logs/history.

---

### Post by zika on 2013-04-18
> **ventrical said:**
> Actually it was during the Oneric Ocelot cycle. I'll see if I still have that install and check for logs/history.
I do not have such install but a brief search gives:
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)
In accordance with my loyal old notebook... One of the first entries... ;)

---

### Post by ventrical on 2013-04-18
> **zika said:**
> I do not have such install but a brief search gives:
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)
In accordance with my loyal old notebook... One of the first entries... ;)

Just beautiful :)   Now I  have the bug to search down the thread where I got that sudo -i from:)

---

### Post by ventrical on 2013-04-18
@cariboo907

Thanks .. ummm but one thing .. you forgot the -a

sudo -i dpkg --configure -a

:)

.. and if you think it best to drop the '-i' then please do so.

Thanks again.

;)

---

### Post by Elfy on 2013-04-18
I added the a

Not getting involved in a circular argument about -i :)

I might 

```
sudo -i
```

then do 

```
dpkg --configure -a
```

If I had a whole bunch of other stuff to do - but I'd only use 

```
sudo dpkg --configure -a 
```

if that was all I was doing ;)

---

### Post by ventrical on 2013-04-18
Thanks very much Elfy.

---

### Post by ventrical on 2013-04-25
If anyone is having problems with gksu and password authentication then please check out this link for the fix.

[http://ubuntuforums.org/showthread.php?t=2138386&p=12616119#post12616119](http://ubuntuforums.org/showthread.php?t=2138386&p=12616119#post12616119)

---

### Post by ventrical on 2013-04-30
+1

Make sure that the sources.list text has this added info.

[http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169](http://ubuntuforums.org/showthread.php?t=2138987&p=12619169&viewfull=1#post12619169)

---

### Post by ventrical on 2013-07-01
Just some notes on the btrfs file system.

Btrfs can be downloaded from the saucy repositories.

```

sudo apt-get install apt-btrfs-snapshot

```

*note* You have to have your file system formatted to btrfs when you are doing an install from Ubiquity. apt-btrfs-snapshot can only be run from the #root terminal. If you get no desktop  after an upgrade and cannot access a terminal you can get to a terminal by holding down the <shift> key (or any key) which will bring up the GRub menu.

From the GRuB menu you can choose <Recovery Mode> option, then <root>. Once you have dropped to root# you can enter:

```

mount -o remount,rw /

```

then , if you type in <exit> it will bring you back to the recovery GUI with the option to choose an @apt-snapshot.

The other way is to enter all the information at the cli and then reboot from there.

```

root_name#> apt-btrfs-snapshot set-default @apt-snapshot_name_of_snapshot

```

This is a great recovery tool to learn how to use , especially if you are experimenting with 'mir' server ppa or other  cutting edge Ubuntu tools.

---

### Post by ventrical on 2013-09-01
How to tell your current graphics adapter card and driver:

```

sudo lshw -C display

```

---

### Post by ventrical on 2013-09-24
Other desktop enviroments downloaded&installed from the repos or Ubuntu Software Center can and will overwrite data to  a file:

/etc/lightdm/lighdm.conf and/or /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf

The new lightdm.conf file will look like this after installing KDE Plasma Desktop:

```

[SeatDefaults]
user-session=kde-plasma
greeter-session=lightdm-kde-greeter

```


To restore your original greeter you have to edit : /etc/lightdm/lightdm.conf in this way:

```

[SeatDefaults]
user-session=unity-greeter
type=unity

```

regards..

---

### Post by ventrical on 2013-09-24
How to reduce disk space usage using the command line.

You can reduce disk space usage, by cleaning out /var/cache/apt/archives using apt-get clean.

Before:

   ```

     df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.9G  2.2G  77% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home 

```

After:

   ```

     df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.3G  2.7G  71% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home 

```

I just cleaned the archive directory out last week, so there isn't a great difference, but I did gain about 500MiB.                                                                                                                                

as per .. 

[http://ubuntuforums.org/showthread.php?t=2174436&page=7&p=12797824#post12797824](http://ubuntuforums.org/showthread.php?t=2174436&page=7&p=12797824#post12797824)

---

### Post by zika on 2013-09-24
> **ventrical said:**
> How to reduce disk space usgae using the command line.

You can reduce disk space usage, by cleaning out /var/cache/apt/archives using apt-get clean.

Before:

   ```

     df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.9G  2.2G  77% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home 

```

After:

   ```

     df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       9.5G  6.3G  2.7G  71% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            992M  4.0K  992M   1% /dev
tmpfs           201M  2.7M  198M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none           1001M  780K 1001M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdb3       218G   83G  124G  40% /home 

```

I just cleaned the archive directory out last week, so there isn't a great difference, but I did gain about 500MiB.                                                                                                                                

as per .. 

[http://ubuntuforums.org/showthread.php?t=2174436&page=7&p=12797824#post12797824](http://ubuntuforums.org/showthread.php?t=2174436&page=7&p=12797824#post12797824)
It depends very much on options You choose for apt... I'm not sure what are defaults but that is simple enough to check...Most of the time You don have even to think about clean/autoclean:```
:~$ ll /var/cache/apt/archives/total 116
drwxr-xr-x 4 root root 57344 Sep 24 21:25 ./
drwxr-xr-x 3 root root  4096 Sep 24 21:25 ../
drwxr-xr-x 2 root root 49152 Sep 24 21:01 apt-fast/
-rw-r----- 1 root root     0 Jun 24 22:57 lock
drwxr-xr-x 2 root root  4096 Sep 24 21:20 partial/
:~$ ll /var/cache/apt/archives/apt-fast/
total 108
drwxr-xr-x 2 root root 49152 Sep 24 21:01 ./
drwxr-xr-x 4 root root 57344 Sep 24 21:25 ../
:~$ ll /var/cache/apt/archives/partial/
total 60
drwxr-xr-x 2 root root  4096 Sep 24 21:20 ./
drwxr-xr-x 4 root root 57344 Sep 24 21:25 ../

```No clean/autoclean in months/years...
No sense keeping something You're goint to erase anyway...

---

### Post by ventrical on 2013-09-24
Thanks for the addendum.

;)

---

### Post by zika on 2013-09-24
> **ventrical said:**
> If you download a document file (**or any other file for that matter**) and conventional ways of searching for that file do not work then you can use the gnome-terminal and enter the code:



dpkg -S name_of_downloaded_or_installed_file_here


This will give you the path and directory name as to where the file is.
 For example, if you are searching for the mir-doc files - here are the results 
of that code:

```

mir-doc: /share/doc/mir-doc/html/inherit_graph_89.png
mir-doc: /share/doc/mir-doc/html/inherit_graph_116.map
mir-doc: /share/doc/mir-doc/html/buffer__initializer_8h__dep__incl.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_null_logger__inherit__graph.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_native_client_platform_factory__inherit__graph.map
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_mir_binder_rpc_channel__inherit__graph.png
mir-doc: /share/doc/mir-doc/html/surfaces_2surface_8h__incl.map
mir-doc: /share/doc/mir-doc/html/android__client__buffer_8h__dep__incl.png
mir-doc: /share/doc/mir-doc/html/mir__binder__rpc__channel_8h__incl.md5
mir-doc: /share/doc/mir-doc/html/registration__order__focus__sequence_8h__dep__incl.png
mir-doc: /share/doc/mir-doc/html/size_8h__incl.map
mir-doc: /share/doc/mir-doc/html/inherit_graph_104.md5
mir-doc: /share/doc/mir-doc/html/search/all_79.html
mir-doc: /share/doc/mir-doc/html/mir__basic__rpc__channel_8h__incl.png
mir-doc: /share/doc/mir-doc/html/classmir_1_1client_1_1_client_context__inherit__graph.md5
mir-doc: /share/doc/mir-doc/html/classmir_1_1surfaces_1_1_graphic_region.html
mir-doc: /share/doc/mir-doc/html/structmir_1_1shell_1_1_surface_creation_parameters-members.html

```

etc...Often method proposed gives less than complete answer to a question/query posed...
There is (installed by default) better tool. Just use```
locate string_You_want_to_find
```
To refresh database that is being queryied by command given above simply use```
sudo updatedb
```
Examples that I could think of are giving lengthy output so I do not want to burden Forum by quoteing them, You could try it for Yourself```
[COLOR=#000000]dpkg -S locate
locate locate[/COLOR]
```[COLOR=#000000]...
&#8222;Your&#8220; method has one advantage: it gives the name of the package that brought a file to Your machine, but that is also the source of its disadvantage I'm writing about...
It simply does not fullfill promised: I've bol-ed that in qoute of Your message...[/COLOR]

---

### Post by MalcolmW on 2013-10-01
Thanks, something solved my login problem for Ubuntu 13.04. Mal

---

### Post by ventrical on 2013-10-23
*note*  This post deals with an experiment I was trying randomly in hopes of finding a more expeditious way to 'roll' or upgrade to the next development release (which is currently Trusty Tahr - 14.04)

The most commonly used standard and conventional method is to sudo sed...

```

sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list


```

and then 


```


sudo apt-get update && sudo apt-get dist-upgrade


```

then

sudo apt-get update
sudo apt-get dist-upgrade

with the caveat of editing the Ubuntu.info file at /usr/share/python-apt/templates/ubuntu.info


Some members, including myself, commented at how rather slow   this method was.

 I then decided to rename the 'saucy-desktop-i386.iso' to 'trusty-desktop-i386.iso' and then zsync the file to see if it would work.

```


zsync -i ./trusty-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-i386.iso.zsync


```

and for some reason ,as which with Ubuntu never ceases to amaze me, the zsync worked, installed to USB using SCD and successfully installed to hdd with the Ubuntu.info file being updated afterwards:

sudo apt-get update
sudo apt-get upgrade

 Although my experiment was not very complicated it proved out that the development release can be appended to the last  .iso release (or for that matter and previous iso release) and this makes  for a very economic and expeditious way of updating/upgrading saving a tremendous amount of downtime and bandwidth. 

 This method of renaming is experimental. Although it may appear to be rock solid from my standpoint it may not be rock solid from the varying veiws or observations of others -so, as always, as is with development , this may bork your system.

regards..

---

### Post by ventrical on 2013-12-02
How to get rid of :KVM disabled by BIOS: message in Trusty.

[http://askubuntu.com/questions/263179/get-rid-of-kvm-disabled-by-bios](http://askubuntu.com/questions/263179/get-rid-of-kvm-disabled-by-bios)

---

### Post by ventrical on 2013-12-30
EDIT:

Special Note about Mir.

Development of Mir will not happen until April 2016 cycle  (16.04). If you install Mir components or Unity8 there is a good probability that you will bork your system.

[http://en.wikipedia.org/wiki/Mir_%28software%29](http://en.wikipedia.org/wiki/Mir_%28software%29)

Old reminder note about Mir.

 [URL="https://wiki.ubuntu.com/Mir/Installing"]https://wiki.ubuntu.com/Mir/Installing 
[/URL]
There is a serious carfunkle here. After reading this link: (The link is no longer current
  or updated).<I took it upon myself to edit the page with pertinent updates>

[http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)

it shows that many of the lighdm.conf files are no longer current with the data included in the wiki:

> 
If you want to temporarily switch back to using X.org on your system, run following commands: 
$> sudo vi  /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf 
 
and add a comment to the second line: 
[SeatDefaults] 
 #type=unity


This has now been changed to represent to correct directory. I could find no current Mir or unity-system compositor web-sites with the new instructions.

Now here  [https://wiki.ubuntu.com/Mir/Installing#preview](https://wiki.ubuntu.com/Mir/Installing#preview)

---

### Post by ventrical on 2014-04-25
New info on lighdm.conf files and directory changes and some how to's.

[http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)

---

### Post by ventrical on 2014-04-25
Edit: Note that Mir and/or Unity8 will most likely break your system. Development of Mir has ceased until 16.04 cycle so install Mir  or Unty8 at your own risk.

[http://en.wikipedia.org/wiki/Mir_%28software%29](http://en.wikipedia.org/wiki/Mir_%28software%29)

New method to install mir.

```


sudo apt-get install unity-system-compositor

```


```

sudo apt-get install ubuntu-desktop-mir

```
  


The new location for the new compositor.conf file is:

```

/usr/share/lightdm/lightdm.conf.d/10-unity-system-compositor.conf

```

or here

  [https://wiki.ubuntu.com/Mir/Installing#preview](https://wiki.ubuntu.com/Mir/Installing#preview)

---

### Post by ventrical on 2014-10-17
Here is a really  streamlined and reliable way to make a bootable USB disk with an (*)ubuntu image.

> 

[LIST=1]
[*]Download the ISO
[*]Insert your USB stick in the knowledge that it’s going to get wiped
[*]Open the “Disks” application
[*]Choose your USB stick and click on the cog icon on the righthand side
[*]Choose “Restore Disk Image”
[*]Browse to and select the ISO you downloaded in #1
[*]Click “Start restoring”
[*]Wait
[*]Boot and select “Try Ubuntu….”
[*]Done *
[/LIST]

---

### Post by ventrical on 2014-10-18
How to boot with SystemD

courtesy of elfin post :)

> 
to boot with systemd in utopic is simple

boot, edit the boot line - find the '*linux* line and add init=/lib/systemd/systemd then F10 will boot with systemd instead of upstart

when you're sure all is ok you can edit grub and add it there

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd "

don't forget to update grub after changing that 				


---

### Post by zika on 2014-10-18
Two more ways to go over the fence and fully/completely adopt SystemD:
1.```
sudo apt-get install systemd-sysv
```
2.```
sudo apt-get purge upstart
```
Use with caution (changes are reversible in almost all the cases, AMD mostly, NVidia might be tricky) and only if You're really determined. I was and still am and have no regrets. To the contrary.
Read appropriate thread to get more details about problems with NVidia etc.

---

### Post by ventrical on 2014-10-18
> **zika said:**
> Two more ways to go over the fence and fully/completely adopt SystemD:
1.```
sudo apt-get install systemd-sysv
```
2.```
sudo apt-get purge upstart
```
Use with caution (changes are reversible in almost all the cases, AMD mostly, NVidia might be tricky) and only if You're really determined. I was and still am and have no regrets. 

Thanks zika.

So it's not as easy as editing grub back to it's default and re-installing upstart?

I'm just asking ?

Regards..

---

### Post by zika on 2014-10-18
> **ventrical said:**
> Thanks zika.
So it's not as easy as editing grub back to it's default and re-installing upstart?
I'm just asking ?
Regards..> **zika said:**
> *Two **more** ways* to go over the fence and fully/completely adopt SystemD:
1.```
sudo apt-get install systemd-sysv
```
2.```
sudo apt-get purge upstart
```
Use with caution (*changes **are** reversible* in almost all the cases, AMD mostly, NVidia might be tricky) and only if You're really determined. I was and still am and have no regrets. To the contrary.
**Read appropriate thread** to get more details about problems with NVidia etc.
In these &#8222;two more ways&#8220; there is not any change in /etc/default/grub needed as I've written in a thread mentioned. Change back, as I wrote is a &#8222;simple&#8220; (mind the caveat I explained) purge of systemd-sysv or install of upstart since devs have done a good job and those two simply do not coexist together but do ask for other one when removed.

---

### Post by zika on 2014-10-18
> **ventrical said:**
> The only caveat is that **I had to edit out**```
init=/lib/systemd/systemd
```from grub menu. So it is very well automated.As I wrote in message You've quoted, because You've put it there. Rarely clean job that dev(s) have done.

---

### Post by ventrical on 2014-10-18
> **zika said:**
> As I wrote in message You've quoted, because You've put it there. Rarely clean job that dev(s) have done.

I asked elfy to move it there. That it would be more topical there in systemd experience.

But I'll put the link here  for reference.

[http://ubuntuforums.org/showthread.php?t=2224798&page=14&p=13146459#post13146459](http://ubuntuforums.org/showthread.php?t=2224798&page=14&p=13146459#post13146459)

Thank you elfy.

Thank you zika.

---

### Post by ventrical on 2014-10-27
Upgrading to a new development cycle: Notes:

  The rules remain the same but the speed of information is dynamic and can sometimes often collide. This 15.05 Vivid Vervet Cycle came very quickly, as expected by some, as a continuance of the anticipated rolling release philology.

  Also, there is a certain order or 'flowchart' to follow when executing this proceedure. There are several diffirent methods that seem to work well for some and not so well for others.  Mistakes will be made and systems will break - but for the most part the rolling releases have been designed to present us testers with somewhat of a fucntioning desktop experience (or a least a working X terminal).

  There are basically two main files that have to be edited and updated. The first file is  sources.list which can be found here :

```

/etc/apt/sources.list

```

and the Ubuntu.info file which can be found here:

```

/usr/share/python-apt/templates/Ubuntu.info


```


  These two files are very different from each other but are essential for the proper update/upgrade to the new development cycle.


 When the command:

```

sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list

```

is executed followed by:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

and

```

sudo apt-get update
sudo apt-get upgrade

```

 it will convert the sources.list text to the current repositories for (vivid)  but it will also convert the templates  in Ubuntu.info to /devel/

  This may seem to be very confusing.  Back a few cycles ago we were able to use /devel/ verebose to change our sources.list and get updates/upgrades but now it does not seem to work so , in this cycle, it is more prudent to use the first part of the release cycle name. Again , in this case that is /vivid/.

  Cariboo907 has detailed the proceedure to insert the new template for the /vivid/ cycle here at this link:

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

  Make sure to append this info at the top of the Ubuntu.info file.

  There is a changelog URL. It can either be left in or commented out.  Some say it is useful (and probably is) but it still reported errors on one of my installs. Surf the pertinent echos in Ubuntu Development Release and decide for yourselves. Try different things.  It's free :)


 Also some will have the proposed repositories turned on. Other would beg to differ to have them disabled. It is most surely if you have them enabled that you will bork your desktop and network , unless, of course , you are an advanced user.

Regards..

---

### Post by ventrical on 2014-11-13
If you are having problems with apport reporting random bugs you can always turn it off.

Buckyball reported this: [http://ubuntuforums.org/showthread.php?t=2251463&p=13160868#post13160868](http://ubuntuforums.org/showthread.php?t=2251463&p=13160868#post13160868)

and zika reported this: [http://ubuntuforums.org/showthread.php?t=2251463&p=13160964#post13160964](http://ubuntuforums.org/showthread.php?t=2251463&p=13160964#post13160964)

Regards..

---

### Post by ventrical on 2014-11-18
Startup Disk Creator is not working correctly, loaded with bugs and will bust  a persistent  ver 3.0 USB ISO when it is updated. However, that USB will work on ver 2.0 hardware but not version 3.0 hardware. Then , after sitting over night in off state it will not boot up at all and is not recognized by ver 3.0 hardware. It will make it appear that you ver 3.0 USB has a hardware brick, which , in fact, is no the case. If you have a similar bust then  remove your partition from USB flash _drive, create a new partition and mark it ext4 and then try below.

 Here is a method already posted that will fix that.

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

---

### Post by cariboo on 2014-11-18
We seem to be straying away for command line solutions here, so, another way to create a bootable live usb drive, is to use Disks->Restore disk image, there's no persistence, but at least it's more reliable than than the current boot disk creation utility.

---

### Post by ventrical on 2015-02-25
How to get popular vlc dvd player running with the sudo commands at this link.

[http://ubuntuforums.org/showthread.php?t=2266654&p=13234289#post13234289](http://ubuntuforums.org/showthread.php?t=2266654&p=13234289#post13234289)

---

### Post by ventrical on 2015-07-07
This is the best current sudo command to get snappy working in a kvm:

 ```

dale@ventrical-MS-7798:~/Downloads$ kvm -m 512 -redir :8090::80 -redir :8022::22 ubuntu-15.04-snappy-amd64+generic.img

```

---

### Post by ventrical on 2017-04-21
Precise 12.04 end of life April 25, 2017 --upgrade your Precise systems--

```

sudo do-release-upgrade -m server

```

---

### Post by ventrical on 2017-05-09
jbicha mentioned to put this in a sticky post. Not sure if this is the right place as there does not seem to be a fix for it.

It has to do with unattended - upgrades and apt-update-service taking a long time in bootup sequence.
The bugs are being worked on.

Here is one link:

[https://ubuntuforums.org/showthread.php?t=2346439&p=13582859#post13582859](https://ubuntuforums.org/showthread.php?t=2346439&p=13582859#post13582859)

and here is the bug posted by harry:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1686470)

It looks like it is being worked on.

..so stand by..

regards..

---

### Post by ventrical on 2017-09-12
Here is a sudo helper for upgrading from 17.04 to 17.10 from wgarcia .

> 

I just updgraded to Ubuntu 17.10 from 17.04, and of course after restart  I got gdm3  and only the option to start the Gnome desktop. To go back  to Unity I had to issue
 	Code:
 	sudo dkpg-reconfigure lightdm 
to set up lightdm again as manager, and there I had the option to  start Unity, which was still configured exactly as I left it in 17.04.  The only bug I got so far is:

[https://bugs.launchpad.net/ubuntu/+s...s/+bug/1703046]("https://bugs.launchpad.net/ubuntu/+source/indicator-printers/+bug/1703046")

So now I'm in the ship of testing Unity along Gnome in 17.10. 				



---

### Post by ventrical on 2017-10-13
There has been lots of problems with nvidia/gdm during 17.10 cycle, freezing on plymouth . etc.. Here is a workaround that worked for me:

We have been having lots of problems with RC and beta etc on PCs with nVidia.

Here is what I did as workaround/fix. I downgraded my nVidia card (changed it) to see if there was hardware problem.

1.Start the PC that has just had the daily/current hard installed.
2. Hold down the shift key while booting.
2.(a) Wait for Grub screen.
2.(b) Choose <advanced options> THEN
2.(c) Choose Recovery option.
3.Wait till all verbose code runs.
4 .Click "resume". Don't do anything!
5. Wait for reboot. It may boot into weird gdm resolution with no gdm Cog-Wheel.
6.Enter password and it should load up ubuntu on xorg. (it did on mine because old nVidia does not support wayland)
7. There might be fuzzy resolution. Don't worry about it.
8. Restart from panel.
9. Go through normal boot and it should boot up to gdm screen with proper resolution.
10. Log on and you will have proper resolution of gnome desktop.

You will notice that it loaded with the old vesa driver which is just  too awesome!:smile:

my old nVidia card on gnome3 with xorg.

Regards..

---

### Post by ventrical on 2017-10-24
Bump:

For 18.04 cycle.

1. This command is used to auto edit the sources.list file on a previous  install and could be considered as a first step to  converting  to  Trusty Tahr. However this and other commands may be  moot after  Alpha  .iso are released. You can still play it safe and test  the kernels  but  breakage may occur nonetheless. ```

     **sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list** 
```
[COLOR=Blue]2.[/COLOR] This command will update your repositories to BB. ```

     **sudo apt-get update && sudo apt-get dist-upgrade** 
```
[COLOR=Navy]3.[/COLOR]This command is inclusive in #2. but is always good to run after removing or purging stuff. ```

     **sudo apt-get update** 
```
[COLOR=Navy]4.[/COLOR]This command is also included in #2. and upgrades any new files that are set in the repositories. ```

     **sudo apt-get dist-upgrade** 
```

Regards..

---

### Post by ventrical on 2017-10-26
P-I-H shares with us that this is an easier way to upgrade to new develoment cycle, avoiding software-properties-gtk crash.

```


sudo sed -i 's/artful/bionic/g' /etc/apt/sources.list
sudo sed -i 's/artful/bionic/g' /usr/share/python-apt/templates/Ubuntu.info
sudo apt-get update
sudo apt-get upgrade
sudo reboot


```


Regards..

---

