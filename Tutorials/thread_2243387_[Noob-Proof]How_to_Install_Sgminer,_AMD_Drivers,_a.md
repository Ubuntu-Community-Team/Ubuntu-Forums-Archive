---
title: "[Noob-Proof]How to Install Sgminer, AMD Drivers, and Mine Darkcoin under Linux/Ubuntu"
date: 2014-09-08
forum: Tutorials
---

### Post by GreenRaccoon on 2014-09-08
***This guide shows how to set up [COLOR=#008000]sgminer[/COLOR] (GPU miner) on [COLOR=#008000]64-bit Linux[/COLOR] when your computer has an [COLOR=#008000]AMD/ATI[/COLOR] GPU or APU.*** This is targeted for Ubuntu, Xubuntu, etc. users. [s]I can't get it to work for Linux Mint or Arch Linux.[/s]  I figured out how to run sgminer on Linux Mint and Arch Linux. See the *NOTE* after step 26.

I've spent a ridiculous amount of time trying to figure all of this out, so I've made this guide ridiculously *DETAILED* to prevent any more headaches. This guide looks [COLOR=#800000]daunting [/COLOR]:shock:, but it's just because I tried to cover every single base I could think of. Even if you're a Linux noob, you should be able to do this fine. :biggrin:


[LIST]
[*]Note: This won't work for every AMD GPU, but it should work for the most common ones used for mining (as of the time this thread was posted). Your computer probably won't turn into a nuclear bomb if something goes wrong, but BACK UP beforehand just in case. Be on the safe side so it's not the end of the world if something odd happens and you have to reinstall Ubuntu. :shock: (I had to reinstall Ubuntu 3 times trying to figure all this out, hence the reason why I'm making this guide.)
[/LIST]
[B]-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[SIZE=3]*****UPDATE*****[/SIZE][/B]
I've written some scripts for you guys. :biggrin: If you'd rather run some scripts than copy and paste every single step below, you have the option to do that now.
*13 Nov-14: Updated the scripts. Only a couple minor changes, but I also made a sweet ascii image.* 8-)
Here's how to copy and run them:

**1-** Run this as **one,** **single** **command **(to download, extract, and make executable):
```
cd ~ &&
wget "https://raw.githubusercontent.com/GreenRaccoon23/sgminer-install-scripts/master/INSTALL" &&
chmod +x INSTALL &&
./INSTALL
```
**2-** Run the first script:
```
sgminer1.in
```
**3-** The script will tell you when to run the next ones.
**-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**
[B][SIZE=3]_Second Option: Step-by-Step Instructions_[/SIZE]
1[/B]- **Update** your computer and **install dependencies**. Open up Terminal with ctrl+alt+t. Then copy (ctrl+c) and paste (ctrl+SHIFT+v) this:
```
sudo aptitude update
sudo aptitude upgrade -y
sudo aptitude install -yr git curl unzip automake autogen yasm autoconf dh-autoreconf build-essential pkg-config openssh-server screen libtool libcurl4-openssl-dev libtool libncurses5-dev libudev-dev xserver-xorg-core xserver-xorg-video-ati gdebi gedit execstack dh-modaliases lib32gcc1 dkms
```
[SIZE=3]_**Set Up AMD Drivers**_[/SIZE]
**2- Check **which** driver** you're using. Open up Terminal with ctrl+alt+t and type this in:
```
fglrxinfo
```
**3-** If that command **_[COLOR=#B30000]wasn't[/COLOR]_ found**, **[COLOR=#B30000]skip to step 6[/COLOR]** because you're not using an fglrx driver. :biggrin: If that command **_[COLOR=#006633]did[/COLOR]_ give** **you something**, that's ok, but it means you need to do more work, sorry. #-oYou're going to need to **[COLOR=#006633]switch drivers[/COLOR]**. Run this command.
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
**4- **If that worked, great. If it didn't, it should be ok too. **In either case, do this next**. 
```
sudo aptitude purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo rm /etc/X11/xorg.conf
sudo aptitude reinstall -yr xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo aptitude update
sudo aptitude upgrade -yr
```
**5- Reboot**. (If you _can't_ login to your computer after rebooting, [post 3]("http://ubuntuforums.org/showthread.php?t=2243387&p=13117769#post13117769") of this thread might help.)
**6-** **Download **the AMD **14.9 Catalyst driver**:
```
cd ~/Downloads
``````

curl -o driver.zip http://www2.ati.com/drivers/linux/amd-catalyst-14-9-linux-x86-x86-64.zip --referer http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx
```
**7-** **Install** the **Catalyst driver**. (Don't change the *'s.)
```
unzip driver.zip
``````

cd fglr*
chmod a+x *.run
sudo sh *.run
```
**8-** The **installation application** will now launch. Soon, a a screen should pop up with the two options '[COLOR=#0000ff]Install Driver 14.20...[/COLOR]'' or '[COLOR=#0000ff]Generate Distribution Specific Driver Package[/COLOR]'.
[LIST]
[*]If an [COLOR=#ff0000]error screen[/COLOR] pops up instead, use this command to open up the log
```
sudo gedit /usr/share/ati/fglrx-install.log
```
[*]Then install the packages it tells you that it needs:
```
sudo apt-get install ...
```
[*]Then run:
```
sudo sh ~/Downloads/fglr*/*.run
```
[/LIST]
**9-** Once you can get the application open to the screen with the two options '[COLOR=#0000ff]Install Driver 14.20...'[/COLOR]' or '[COLOR=#0000ff]Generate Distribution Specific Driver Package[/COLOR]', follow these steps:

[LIST]
[*]First, choose '[COLOR=#008000]Generate Distribution Specific Driver Package[/COLOR]' and click '[COLOR=#008000]Continue[/COLOR]'.
[*]Next, choose '[COLOR=#008000]I agree[/COLOR]' (if you agree).
[*]Next, scroll down and choose '[COLOR=#008000]Build package for detected OS: Ubuntu/trusty[/COLOR]', then click '[COLOR=#008000]Continue[/COLOR]'.
[*]Next, it'll look like it has crashed. It actually IS running; it just takes forever. Seriously, forever--like up to 15 minutes.
[*]Once it's FINALLY done, click '[COLOR=#008000]Exit[/COLOR]' to close.
[*]**[COLOR=#ff0000]***IMPORTANT!***[/COLOR]** Next, something will pop up. [COLOR=#ff0000]DO NOT CHOOSE 'YES.'[/COLOR] **[COLOR=#008000]CHOOSE 'NO[/COLOR]'**. (If you accidentally hit 'yes', it shouldn't be a big deal though. Just keep going.)
[/LIST]
**10- **Then, **install** the new packages:
```
sudo gdebi *.deb
```
**11- [B]BEFORE you reboot, r**un these commands.[/B]
```
sudo aptitude update
sudo aptitude upgrade -y
sudo aticonfig --adapter=all --initial
sudo aptitude install -yr boinc-amd-opencl opencl-headers mesa-utils libglu1-mesa libgl1-mesa-glx libgl1-mesa-dri
```
**12- Reboot.**
**13-** Now install the **APP SDK**:
```
cd /tmp
curl -o amd-app-sdk.tgz http://blog.truepps.com/downloads/AMD/AMD-APP-SDK-v2.9-lnx64.tgz
sudo mkdir amd-app-sdk
sudo mv amd-app-sdk.tgz amd-app-sdk
cd amd-app-sdk
sudo tar -zxvf amd-app-sdk.tgz
sudo tar -zxvf AMD-APP-SDK-v2.9-RC-lnx64.tgz
cd AMD-APP-SDK-v2.9-RC-lnx64
sudo cp -pv lib/x86_64/* /usr/lib/
sudo rsync -avl include/CL/ /usr/include/CL/
cd ..
sudo tar -zxvf icd-registration.tgz
sudo rsync -avl etc/OpenCL/ /etc/OpenCL/
sudo ldconfig
sudo perl default-install_lnx_64.pl
sudo aticonfig --adapter=all --initial
```
**14- Reboot**.
[SIZE=3]_**Install Sgminer**_[/SIZE]
**15-** The hard part's over (yay!). **Copy/git** **sgminer's files** to your computer:
```
cd ~/
git clone https://github.com/sgminer-dev/sgminer.git
```
**16-** Sgminer needs three files from the **AMD ADL SDK**:
```
cd ~/Downloads
curl -o adl_sdk.zip http://blog.truepps.com/downloads/AMD/ADL_SDK_6.0.zip
mkdir adl_sdk
mv adl_sdk.zip adl_sdk
cd adl_sdk
unzip adl_sdk.zip
cp ~/Downloads/adl_sdk/include/* ~/sgminer/ADL_SDK
```
**17-** Compile, make, and **install** it.
```
cd ~/sgminer
git submodule init
git submodule update
autoreconf -i
CFLAGS="-O2 -Wall -march=native" ./configure
make
sudo make install
```
**18-** **Check** to make sure it worked
```
sgminer -n
```
**19-** If it [COLOR=#006600]does detect[/COLOR] your GPU('s), [COLOR=#006600]go to step 20[/COLOR]. If it [COLOR=#FF0000]does not detect[/COLOR] your GPU('s) run "sudo aticonfig --adapter=all --initial" and then reboot.

---

### Post by GreenRaccoon on 2014-09-08
[SIZE=3][COLOR=#141414]**_[B]Configuring Sgminer**_[/B][/COLOR][/SIZE]
[COLOR=#141414]**20-** Now make a **script** that you'll use whenever you want to launch sgminer. This script saves your mining preferences. It's pretty handy.[/COLOR]
```
cd ~
gedit darkgpu
```
[COLOR=#141414]**21-** An empty file should pop up. Copy and paste this in there:[/COLOR]
```
#!/bin/bash
cd ~/sgminer
export DISPLAY=:0
export GPU_MAX_ALLOC_PERCENT=100
export GPU_USE_SYNC_OBJECTS=1
./sgminer -k x11mod -o # -u # -p # --no-submit-stale -I # 
```
[COLOR=#141414]**22-** Now you can fill in your **sgminer configuration**. [COLOR=#B35900]*Always keep the first 5 lines the same,*[/COLOR] but you'll want to replace the "#" signs with something else. If you have no idea what to put for "#", keep reading. If you know what to put, then skip to step 25.[/COLOR]

[LIST]
[*][COLOR=#141414]**"-o"** stands for your pool's address and port. "[COLOR=#0000FF]stratum+tcp://address.com:####[/COLOR]" Find that on your pool's website (usually under "Help" and then "Getting started"). This is what mine is:
[/COLOR][COLOR=#141414]```
./sgminer -k x11mod -o stratum+tcp://darkcoin.stonedpuppy.com:9902
```[/COLOR]
[*][COLOR=#141414]**"-u"** stands for your personal username that you use on your pool's website. BUT "-u" also includes a worker name that you have to create on your pool's website. On your pool's website, you can have ONE username but MANY different workers. Think of it this way. The "username" represents "you" and the "workers" are the "slaves" that work for you. [/COLOR]:shock:[COLOR=#141414][IMG]https://darkcointalk.org/styles/default/xenforo/clear.png[/IMG] Your username identifies you, and each worker represents each computer that's mining for you. You create a name for each one of your workers on your pool's website. This is what it looks like when you type it after "-u": "[COLOR=#0000FF]username.worker[/COLOR]". So if the username on my pool is "GreenRaccoon23," and I created a worker on there named "chucknorris," it would look like this:
[/COLOR][COLOR=#141414]```
./sgminer -k x11mod -o stratum+tcp://darkcoin.stonedpuppy.com:9902 -u GreenRaccoon23.chucknorris
```[/COLOR]
[*]**"-p"**[COLOR=#141414] stands for your [/COLOR][COLOR=#0000FF]password[/COLOR][COLOR=#141414]: your WORKER'S password, NOT your username's password. You set this up on your pool's website. So if the password for my worker "chucknorris" is "knowsvictoriassecret," this is what it would look like:
[/COLOR][COLOR=#141414]```
./sgminer -k x11mod -o stratum+tcp://darkcoin.stonedpuppy.com:9902 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret
```[/COLOR]
[*]**"-I"**[COLOR=#141414] stands for "intensity," and you type it as a number. [/COLOR][COLOR=#0000FF]18[/COLOR][COLOR=#141414] is probably a good starting point. If you make it too high, sgminer will just whine that something's not right. For my Radeon HD7970, mine's set to 25. Start out low and work your way up one number at a time until sgminer starts to whine. Here's our final result of a basic config:
[/COLOR][COLOR=#141414]```
sudo ./sgminer -k x11mod -o stratum+tcp://darkcoin.stonedpuppy.com:9902 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret -I 25
```[/COLOR]
[*][COLOR=#141414]You can look at these two documents for more ideas:
[/COLOR][https://github.com/djm34/sph-sgminer_x11mod/blob/master/doc/GPU](https://github.com/djm34/sph-sgminer_x11mod/blob/master/doc/GPU)
[https://github.com/djm34/sph-sgminer_x11mod/blob/master/doc/MINING.md](https://github.com/djm34/sph-sgminer_x11mod/blob/master/doc/MINING.md)
[*][COLOR=#141414]To give you some reference, here's [/COLOR]**my own darkgpu file**[COLOR=#141414] for my Radeon HD7970 (except the personal stuff, of course). I run sgminer (GPU miner) and minerd (CPU miner) at the same time, and this is as fast as I can make sgminer run without my computer crashing:
[/COLOR]```
#!/bin/bash
cd ~/sgminer
[COLOR=#141414]export DISPLAY=:0
[/COLOR][COLOR=#141414]export GPU_MAX_ALLOC_PERCENT=100
[/COLOR][COLOR=#141414]export GPU_USE_SYNC_OBJECTS=1
[/COLOR][COLOR=#141414]./sgminer -k x11mod -o stratum+tcp://darkcoin.stonedpuppy.com:9902 -u GreenRaccoon23.chucknorris -p knowsvictoriassecret --no-submit-stale --auto-fan --auto-gpu --gpu-fan 25-75 --gpu-memclock 850 --thread-concurrency 8192 -I 23[/COLOR]
```
[/LIST]
**23- Save**.
**24- Make** the script **executable**.
```
chmod +x darkgpu
```

[SIZE=3][COLOR=#141414]**_Run Sgminer_**[/COLOR][/SIZE]
[COLOR=#141414]**25-** Running sgminer is easy once you make that "darkgpu" script explained above. [/COLOR]Just go to your home directory (the default)[COLOR=#141414] and **run the script**:[/COLOR]
[COLOR=#141414]```
cd ~
./darkgpu
```[/COLOR]
[COLOR=#141414]**26-** [COLOR=#336600]IT IS ALIVE[/COLOR]. When you want to stop it, press "q" or "ctrl+c". To run it again, redo step 25. To change sgminer's settings, go through steps 20-23 again.[/COLOR]

***NOTE:*** If you ever have a problem running the darkgpu script (where it starts and then stops right away), it means that sgminer has already saved your settings. Instead of running "[COLOR=#a52a2a]./darkgpu[/COLOR]", run "[COLOR=#008000]sgminer -k x11mod -I 23[/COLOR]". Replace "23" with whatever number you'd like for intensity.

[COLOR=#141414]Sources:[/COLOR]
[COLOR=#141414][https://forums.chunkypools.com/t/guide-compiling-sgminer-for-x11-coins-in-ubuntu/28](https://forums.chunkypools.com/t/guide-compiling-sgminer-for-x11-coins-in-ubuntu/28)[/COLOR]
[COLOR=#141414][https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)[/COLOR]
[COLOR=#141414][https://github.com/djm34/sph-sgminer_x11mod](https://github.com/djm34/sph-sgminer_x11mod)[/COLOR]
[COLOR=#141414][https://bitcointalk.org/index.php?topic=658411.0](https://bitcointalk.org/index.php?topic=658411.0)
[/COLOR][http://ubuntuforums.org/showthread.php?t=2234408](http://ubuntuforums.org/showthread.php?t=2234408)
[http://www.distrogeeks.com/install-cgminer-3-7-2-ubuntu/](http://www.distrogeeks.com/install-cgminer-3-7-2-ubuntu/)
[https://wiki.archlinux.org/index.php/AMD_Catalyst](https://wiki.archlinux.org/index.php/AMD_Catalyst)
[s][http://darkcoin.stonedpuppy.com/index.php?page=gettingstarted](http://darkcoin.stonedpuppy.com/index.php?page=gettingstarted)[/s] (site has been taken down)

*(If you want to install cpuminer for CPU mining also, I have another guide: [http://ubuntuforums.org/showthread.php?t=2243386](http://ubuntuforums.org/showthread.php?t=2243386))*

---

### Post by GreenRaccoon on 2014-09-08
[COLOR=#141414]**If you got stuck on step 5**, this might help you login.[/COLOR]
[COLOR=#141414]Press **ctrl+alt+f1** to get to the Terminal, aka "black screen of death" (jk [/COLOR];-)[COLOR=#141414][IMG]https://darkcointalk.org/styles/default/xenforo/clear.png[/IMG]). Type in your **username** (the name of your Home folder) and then your **password**. Then type this in:[/COLOR]
```
sudo aptitude update
sudo aptitude upgrade -yr
sudo amdconfig --adapter=all --initial
sudo service lightdm stop
rm ~/.config/dconf/user
sudo reboot
```
[COLOR=#660000]**If you STILL see just a blank screen**[/COLOR], don't worry! It's ok! :smile: Press **ctrl+alt+f1** to get to the Terminal. Type in your **username** and then type in your **password**. Now just go back up to **step 6** under [post 1]("http://ubuntuforums.org/showthread.php?t=2243387&p=13117766#post13117766") of this thread and continue the guide. Once you install the AMD driver, you SHOULD be able to login normally again. :biggrin:

---

### Post by senoird on 2014-11-09
After following step by step here is what happens for me:

dean@dean-ubuntu:~$ sgminer -n
[10:50:30] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:50:30] CL Platform name: AMD Accelerated Parallel Processing                    
[10:50:30] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:50:30] Platform devices: 1                    
[10:50:30] 	0	Tahiti                    
[10:50:30] Number of ADL devices: 1                    
[10:50:30] ATI ADL Overdrive5 API found.                    
[10:50:30] ATI ADL Overdrive6 API found.                    
[10:50:30] Found 6 logical ADL adapters                    
[10:50:30] ADL index 0, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 assigned: iAdapterIndex:0 iPresent:1 strUDID:256:26522:4098:31056:5445 iBusNumber:1 iDeviceNumber:0 iDrvIndex:0 iFunctionNumber:0 iVendorID:4098 name:AMD Radeon HD 7900 Series                     
[10:50:30] ADL index 1, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 2, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 3, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 4, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 5, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 AMD Radeon HD 7900 Series  hardware monitoring enabled                    
[10:50:30] ADL GPU 0 is Adapter index 0 and maps to adapter id -1919074896                    
[10:50:30] GPU 0 BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] Failed to ADL_Overdrive5_FanSpeed_Get for default value                    
[10:50:30] 1 GPU devices max detected                    
dean@dean-ubuntu:~$ export DISPLAY=0
dean@dean-ubuntu:~$ export GPU_MAX_ALLOC_PERCENT=100
dean@dean-ubuntu:~$ export GPU_USE_SYNC_OBJECTS=1
dean@dean-ubuntu:~$ sgminer -n
[10:51:01] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:51:01] CL Platform name: AMD Accelerated Parallel Processing                    
[10:51:01] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:51:01] Error -1: Getting Device IDs (num)                    
[10:51:01] clDevicesNum returned error, no GPUs usable                    
[10:51:01] 0 GPU devices max detected

Any ideal of what is wrong?

---

### Post by GreenRaccoon on 2014-11-13
> **senoird said:**
> After following step by step here is what happens for me:

dean@dean-ubuntu:~$ sgminer -n
[10:50:30] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:50:30] CL Platform name: AMD Accelerated Parallel Processing                    
[10:50:30] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:50:30] Platform devices: 1                    
[10:50:30]     0    Tahiti                    
[10:50:30] Number of ADL devices: 1                    
[10:50:30] ATI ADL Overdrive5 API found.                    
[10:50:30] ATI ADL Overdrive6 API found.                    
[10:50:30] Found 6 logical ADL adapters                    
[10:50:30] ADL index 0, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 assigned: iAdapterIndex:0 iPresent:1 strUDID:256:26522:4098:31056:5445 iBusNumber:1 iDeviceNumber:0 iDrvIndex:0 iFunctionNumber:0 iVendorID:4098 name:AMD Radeon HD 7900 Series                     
[10:50:30] ADL index 1, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 2, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 3, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 4, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 5, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 AMD Radeon HD 7900 Series  hardware monitoring enabled                    
[10:50:30] ADL GPU 0 is Adapter index 0 and maps to adapter id -1919074896                    
[10:50:30] GPU 0 BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] Failed to ADL_Overdrive5_FanSpeed_Get for default value                    
[10:50:30] 1 GPU devices max detected                    
dean@dean-ubuntu:~$ export DISPLAY=0
dean@dean-ubuntu:~$ export GPU_MAX_ALLOC_PERCENT=100
dean@dean-ubuntu:~$ export GPU_USE_SYNC_OBJECTS=1
dean@dean-ubuntu:~$ sgminer -n
[10:51:01] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:51:01] CL Platform name: AMD Accelerated Parallel Processing                    
[10:51:01] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:51:01] Error -1: Getting Device IDs (num)                    
[10:51:01] clDevicesNum returned error, no GPUs usable                    
[10:51:01] 0 GPU devices max detected

Any ideal of what is wrong?
You know, I had this same problem and couldn't figure out what the problem was. Oddly enough, I think all it is is that the export strings need to be enclosed in quotes. So:
```
export DISPLAY=":0"
export GPU_MAX_ALLOC_PERCENT="100"
export GPU_USE_SYNC_OBJECTS="1"
```
I'm in the process of modifying these scripts a bit, and I'll put those single quotes in.

---

### Post by GreenRaccoon on 2014-11-29
> **senoird said:**
> After following step by step here is what happens for me:

dean@dean-ubuntu:~$ sgminer -n
[10:50:30] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:50:30] CL Platform name: AMD Accelerated Parallel Processing                    
[10:50:30] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:50:30] Platform devices: 1                    
[10:50:30]     0    Tahiti                    
[10:50:30] Number of ADL devices: 1                    
[10:50:30] ATI ADL Overdrive5 API found.                    
[10:50:30] ATI ADL Overdrive6 API found.                    
[10:50:30] Found 6 logical ADL adapters                    
[10:50:30] ADL index 0, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 assigned: iAdapterIndex:0 iPresent:1 strUDID:256:26522:4098:31056:5445 iBusNumber:1 iDeviceNumber:0 iDrvIndex:0 iFunctionNumber:0 iVendorID:4098 name:AMD Radeon HD 7900 Series                     
[10:50:30] ADL index 1, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 2, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 3, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 4, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] ADL index 5, id -1919074896 - BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] GPU 0 AMD Radeon HD 7900 Series  hardware monitoring enabled                    
[10:50:30] ADL GPU 0 is Adapter index 0 and maps to adapter id -1919074896                    
[10:50:30] GPU 0 BIOS partno.: 113-XXXXX-XXX  , version: 015.025.000.007.000000, date: 12/18/13 19:11                    
[10:50:30] Failed to ADL_Overdrive5_FanSpeed_Get for default value                    
[10:50:30] 1 GPU devices max detected                    
dean@dean-ubuntu:~$ export DISPLAY=0
dean@dean-ubuntu:~$ export GPU_MAX_ALLOC_PERCENT=100
dean@dean-ubuntu:~$ export GPU_USE_SYNC_OBJECTS=1
dean@dean-ubuntu:~$ sgminer -n
[10:51:01] CL Platform vendor: Advanced Micro Devices, Inc.                    
[10:51:01] CL Platform name: AMD Accelerated Parallel Processing                    
[10:51:01] CL Platform version: OpenCL 1.2 AMD-APP (1411.4)                    
[10:51:01] Error -1: Getting Device IDs (num)                    
[10:51:01] clDevicesNum returned error, no GPUs usable                    
[10:51:01] 0 GPU devices max detected

Any ideal of what is wrong?
I figured it out!!! I made a mistake writing the script. ](*,) "export DISPLAY=0" is incorrect. It's supposed to be "export DISPLAY=:0".

It's always some little, dumb thing like that haha. I can't believe it took me this long to see it. :oops: Hopefully that fixes the problem.

---

### Post by aquechipa on 2014-12-17
I'm not being able to mine with all my GPU's, only with one. Even when I run "sudo aticonfig --adapter=all --initial" and reboot it still detects only one. When I run "lspci" it only detects the GPU that is connected to the monitor. Do you know what could be the problem?

---

### Post by GreenRaccoon on 2015-01-02
> **aquechipa said:**
> I'm not being able to mine with all my GPU's, only with one. Even when I run "sudo aticonfig --adapter=all --initial" and reboot it still detects only one. When I run "lspci" it only detects the GPU that is connected to the monitor. Do you know what could be the problem?
I'm not familiar with running sgminer on multiple GPU's unfortunately. I do know that many people have trouble figuring out how to run sgminer with multiple GPU's though. Usually, it boils down to the fact that AMD/ATI drivers can be really buggy. If I were you, I'd try posting on darkcointalk.org or bitcointalk.org to see if someone who's gone through this before can share some advice.

---

### Post by wellfried on 2015-01-06
> **aquechipa said:**
> I'm not being able to mine with all my GPU's, only with one. Even when I run "sudo aticonfig --adapter=all --initial" and reboot it still detects only one. When I run "lspci" it only detects the GPU that is connected to the monitor. Do you know what could be the problem?

Not sure if you've already tried this, but it could be that your video cards are "going to sleep".  Here is a quote the other helpful fury mammal crypto enthusiast (Crypto Badger), which I followed and I've never had a problem running multiple cards.  I bought my adapters for about $10 (I had HDMI ports, so these instructions didn't work), but if you still have a Radio Shack around that might work too: [http://www.cryptobadger.com/2013/04/build-a-litecoin-mining-rig-hardware](http://www.cryptobadger.com/2013/04/build-a-litecoin-mining-rig-hardware)

"Important: you may also need to create dummy plugs for each of your GPUs. Some operating systems will idle video cards that do not have an active monitor connection, which will obviously kill your mining performance. Dummy plugs “trick” your OS into thinking a monitor is connected, thus preventing attached GPUs from being idled. You just need a few resistors ($1-2 at Radio Shack if they’re not available at Amazon) and [these instructions]("http://www.overclock.net/t/384733/the-30-second-dummy-plug") to create your own plugs."

And thanks Greenraccoon for building this script - was having a tough time getting sgminer to work on my linux rigs and this has worked well for me. :)

---

### Post by gadha1998 on 2015-03-15
After step7, this happens

error: Detected X Server version 'XServer 1.17.1_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib32:XServer 1.17.1_64a:none:3.19.0-7-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.ET7LFY


now what?

---

### Post by clintar on 2015-05-22
> **gadha1998 said:**
> After step7, this happens

error: Detected X Server version 'XServer 1.17.1_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib32:XServer 1.17.1_64a:none:3.19.0-7-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.ET7LFY


now what?
Try using: 
```
curl -o driver.zip http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip --referer http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx
```

I don't know if that will work, but it's newer.

---

### Post by mike350 on 2015-08-20
Is there away to undo all this i knew i should have imaged disk 1st. Now my GPU is maxing out but nothing is running. is here a script to uninstall and reset my settings?

---

### Post by badger-badgerclan on 2015-09-04
Was having problems trying to install in 15.04 because of already modified system. Did a fresh install of 15.04 without adding any proprietary software. Added aptitude and followed the manual directions. Downloaded the latest software from ATI except I used the AMD-APP-SDK-v2.9 instead of 3.0. Did not use blog.truepps.com. Several of the scripts become irrelevant since original instructions. Then saved the img of the OS after allowing the software update to a USB stick just in case. Running two R9 270 cards.:D
--no-submit-stale -I 18 -g 2 -w 256 --thread-concurrency 12000 --lookup-gap 2 --vectors 1 --auto-fan --auto-gpu --gpu-memclock 975 --gpu-fan 25-75

badgerclan

---

### Post by amazing2 on 2015-10-15
Using: curl -o driver.zip [http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip](http://www2.ati.com/drivers/linux/amd-catalyst-omega-14.12-linux-run-installers.zip) --referer [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)
has given me the same error message, after Step 7.  

> error: Detected X Server version 'XServer 1.17.1_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib32:XServer 1.17.1_64a:none:3.19.0-30-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.7FJnGk

---

### Post by p.callan on 2016-03-05
I am assuming no, but does this guide work the same for nvidia GPUs? Is there another guide for this perhaps? Thank you so much, I love your detailed guide. Not even I can mess it up :)

---

### Post by lewdposter on 2016-03-08
So is darkcoin still viable to be mined on a single personal computer?

---

