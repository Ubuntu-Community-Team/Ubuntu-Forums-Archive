---
title: "Nvidia HDMI No Sound"
date: 2013-04-17
forum: Ubuntu Development Version
---

### Post by tad1073 on 2013-04-17
I lost hdmi sound after updates, it's not even listed in sound settings. Nvidia 319.12 driver.

---

### Post by MasterMic92 on 2013-04-18
I also just updated and lost all sound. I'm using Nvidia driver version 313.30 (this is not what was updated; it was working fine previously). Running Ubuntu 13.04 which is up to date.

What happened was the HDMI output option disappeared from my sound settings. There is no option for HDMI audio.

---

### Post by pqwoerituytrueiwoq on 2013-04-18
it is cause of a kernel bug, you could use the mainline kernel or boot the the old kernel
i have attached a mainline installer and update checker
install via terminal using the install script

EDIT:
Found a bug in the attachment to patch it after installing run this command:
```
sudo sed "s/'-q'/\"-\$r\"/" -i /usr/local/bin/KernelUpdateScriptGenerator
```

---

### Post by VFStefan on 2013-04-18
I have the same problem. Will they fix this until official 13.04 release?

---

### Post by tad1073 on 2013-04-18
> **pqwoerituytrueiwoq said:**
> it is cause of a kernel bug, you could use the mainline kernel or boot the the old kernel
i have attached a mainline installer and update checker
install via terminal using the install script

What do I do after I have installed it?

---

### Post by MasterMic92 on 2013-04-18
> **pqwoerituytrueiwoq said:**
> it is cause of a kernel bug, you could use the mainline kernel or boot the the old kernel
i have attached a mainline installer and update checker
install via terminal using the install script

Thanks, I ended up reverting to an older kernel and the audio is working again.

---

### Post by pqwoerituytrueiwoq on 2013-04-18
> **tad1073 said:**
> What do I do after I have installed it?

it adds 2 scripts and a startup entry (so when you loin to your system it checks for new kernels)
to check for updates run this command (if accepts one parameter, "-no-rc" it will make it not accept a release candidate kernel)
```
KernelUpdateChecker
```
you will need a notification in the corner of your screen with instructions

---

### Post by tad1073 on 2013-04-19
> **pqwoerituytrueiwoq said:**
> it adds 2 scripts and a startup entry (so when you loin to your system it checks for new kernels)
to check for updates run this command (if accepts one parameter, "-no-rc" it will make it not accept a release candidate kernel)
```
KernelUpdateChecker
```
you will need a notification in the corner of your screen with instructions

Is there a config file for this?

---

### Post by pqwoerituytrueiwoq on 2013-04-19
no, all it does it check the this url for new versions of the kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
it filters the folders to the one for your release (raring/quantal)
then it compares your running kernel version against the listed versions and tells you if there is a new one (you can add -no-rc to exclude release candidates) then it has a install script generated using [FONT=courier new]KernelUpdateScriptGenerator[/FONT]. you can edit the 2 scripts if needed

if you want kernels from a different release edit line 23 of then generator script, change "[FONT=courier new]lsb_release -sc[/FONT]" to "[FONT=courier new]raring[/FONT]" or "[FONT=courier new]qunatal[/FONT]" or which ever release you want
i just found a bug in the generator, here is the new line 29, the edit is in bold
[FONT=courier new]$name2=substr($name,0,strpos($name,**"-$r"**));[/FONT]

i made a thread that has a way to patch the old version
[http://ubuntuforums.org/showthread.php?t=2137026](http://ubuntuforums.org/showthread.php?t=2137026)

---

### Post by tad1073 on 2013-04-19
> **pqwoerituytrueiwoq said:**
> no, all it does it check the this url for new versions of the kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
it filters the folders to the one for your release (raring/quantal)
then it compares your running kernel version against the listed versions and tells you if there is a new one (you can add -no-rc to exclude release candidates) then it has a install script generated using [FONT=courier new]KernelUpdateScriptGenerator[/FONT]. you can edit the 2 scripts if needed

if you want kernels from a different release edit line 23 of then generator script, change "[FONT=courier new]lsb_release -sc[/FONT]" to "[FONT=courier new]raring[/FONT]" or "[FONT=courier new]qunatal[/FONT]" or which ever release you want
i just found a bug in the generator, here is the new line 29, the edit is in bold
[FONT=courier new]$name2=substr($name,0,strpos($name,**"-$r"**));[/FONT]

i made a thread that has a way to patch the old version
[http://ubuntuforums.org/showthread.php?t=2137026](http://ubuntuforums.org/showthread.php?t=2137026)

I've already applied your fix.

---

### Post by tad1073 on 2013-04-19
I can't find where to mark this thread as solved.

---

### Post by pqwoerituytrueiwoq on 2013-04-19
edit the OP in advanced mode and change the prefix
edit: if you upgrade to the 3.9 kernel i think virtualbox wont work just so you know

---

### Post by tad1073 on 2013-04-20
> **pqwoerituytrueiwoq said:**
> edit the OP in advanced mode and change the prefix
edit: if you upgrade to the 3.9 kernel i think virtualbox wont work just so you know

I'm sticking with 3.8.8 for the time being. Thanks for your help, I didn't even think of booting to the previous kernel.

---

### Post by pqwoerituytrueiwoq on 2013-04-24
So will we get this bug fixed by tomorrow on the live cd?
no sound (effecting Nvidia GPUs using HDMI) looks bad
IIRC a fix was committed, it is also easy to workaround, but for a new user it could make the change there mind about installing

---

### Post by nortexoid on 2013-04-25
> **pqwoerituytrueiwoq said:**
> it is cause of a kernel bug, you could use the mainline kernel or boot the the old kernel
i have attached a mainline installer and update checker
install via terminal using the install script

EDIT:
Found a bug in the attachment to patch it after installing run this command:
```
sudo sed "s/'-q'/\"-\$r\"/" -i /usr/local/bin/KernelUpdateScriptGenerator
```

This didn't work for me, but I'm running Catalyst drivers, so maybe that's the issue. I had HDMI but lost it upon upgrading to Kubuntu 13.04. What to do?

---

### Post by pqwoerituytrueiwoq on 2013-04-25
> **tad1073 said:**
> Is there a config file for this?
i added more options to the script
i put my script on github
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater) 

```
~$ KernelUpdateChecker -h
This script sends data to KernelUpdateScriptGenerator
This script saves the update script made by the script to a file and gives the user instructions
This is the help info from KernelUpdateScriptGenerator
Options:
    -no-rc sets the script to ignore Release Canidate versions
    -r overrides the release version
        eg: `KernelUpdateScriptGenerator -r raring` 
        Would mean to a only kernels for raring even if you are using quantal
    -v is used to specify version series
        eg: `KernelUpdateScriptGenerator -v 3.8` 
        Would mean to a only accept kernels starting with 3.8 in the version number
```

---

### Post by bmass on 2013-04-26
I'm a little confused about how to apply the fix. I downloaded the tarball and extracted the kernel folder to my home directory. Then I opened a console and typed:

```
sudo apt-get install curl php5-cli
```

Sorry, I'm really new to Linux and just installed Ubuntu 13.04 on my ASUS G74S w/ nVidia GeForce GTX 560M. I can't get any sound through HDMI (there is no option for HDMI in my sound settings for output devices; also using pulse audio but with no hdmi option aswell). After googling I read that it was a video driver issue and I've installed the proprietary drivers through the software sources > additional drivers.

So far this was the only fix I found. Is this correct? Thanks.

---

### Post by nortexoid on 2013-04-26
The following bug appears highly relevant for both nvidia and amd users: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761)

---

### Post by pqwoerituytrueiwoq on 2013-04-26
> **bmass said:**
> I'm a little confused about how to apply the fix. I downloaded the tarball and extracted the kernel folder to my home directory. Then I opened a console and typed:

```
sudo apt-get install curl php5-cli
```

Sorry, I'm really new to Linux and just installed Ubuntu 13.04 on my ASUS G74S w/ nVidia GeForce GTX 560M. I can't get any sound through HDMI (there is no option for HDMI in my sound settings for output devices; also using pulse audio but with no hdmi option aswell). After googling I read that it was a video driver issue and I've installed the proprietary drivers through the software sources > additional drivers.

So far this was the only fix I found. Is this correct? Thanks.
i updated the readme file

[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

this should fix the hdmi issue you are having

---

### Post by Zewbie on 2013-04-26
I ran the script but it only downloaded 3 of the 4 needed files.  When I type 'sudo update-manager' I recive this error:
```
~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 114, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
    self.options and self.options.use_proposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
    self.flavor_name = get_ubuntu_flavor_name()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
    pkg = get_ubuntu_flavor_package(cache=cache)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-3.9.0-030900rc8-generic needs to be reinstalled, but I can't find an archive for it.

```

should I rerun the script?

---

### Post by pqwoerituytrueiwoq on 2013-04-26
> **Zewbie said:**
> I ran the script but it only downloaded 3 of the 4 needed files.  When I type 'sudo update-manager' I recive this error:
```
~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 114, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
    self.options and self.options.use_proposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/MetaReleaseGObject.py", line 44, in __init__
    MetaReleaseCore.__init__(self, useDevelopmentRelease, useProposed)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 90, in __init__
    self.flavor_name = get_ubuntu_flavor_name()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 447, in get_ubuntu_flavor_name
    pkg = get_ubuntu_flavor_package(cache=cache)
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/utils.py", line 437, in get_ubuntu_flavor_package
    cache = apt.Cache()
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python3/dist-packages/apt/cache.py", line 151, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package linux-headers-3.9.0-030900rc8-generic needs to be reinstalled, but I can't find an archive for it.

```

should I rerun the script?
when there are missing packages it tells you how to ignore and install them, use that command
there are now only 3 required, i just updated the script to support that [[change log](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/commit/ecc3c0d7f0dbed48fa7c21d2ec444ea23e9c501e#KernelUpdateScriptGenerator)]


given that error you probally had a bad download
run this command
```
sudo dpkg-reconfigure linux-headers-3.9.0-030900rc8-generic
```
if that does not work run this command
for 64bit:
```
cd /tmp;wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/linux-headers-3.9.0-030900rc8-generic_3.9.0-030900rc8.201304211835_amd64.deb;sudo dpkg -i linux-headers-3.9.0-030900rc8-generic_3.9.0-030900rc8.201304211835_amd64.deb
```
for 32bit:
```
cd /tmp;wget  http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/linux-headers-3.9.0-030900rc8-generic_3.9.0-030900rc8.201304211835_i386.deb;sudo  dpkg -i  linux-headers-3.9.0-030900rc8-generic_3.9.0-030900rc8.201304211835_i386.deb
```

---

### Post by Zewbie on 2013-04-26
that fixed it...  I'll see if I have sound after reboot...  Thanks

---

### Post by pqwoerituytrueiwoq on 2013-04-26
i also updated the script again, this will apply the update:
```
sudo wget https://raw.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/master/KernelUpdateScriptGenerator -O /usr/local/bin/KernelUpdateScriptGenerator
sudo wget https://raw.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/master/KernelUpdateChecker -O /usr/local/bin/KernelUpdateChecker
```

---

### Post by Zewbie on 2013-04-26
worked, now running 3.9 cheers

---

### Post by QDR06VV9 on 2013-04-26
I have this problem ever since pulse audio was introduced on karmic.
Heres what works for me(creative audigy2 platiumz series)

You’ll need a terminal window open.
1. Find out what your default sound card is. You can simply do this by firing up alsamixer. The card that
shows upon opening it is your default sound card for Alsa.
2. sudo alsamixer
3. Next list the names of your sound cards. It should show two cards, and their “index”. The one with index 0
is your default one. In my case it was “snd_hda_intel”
4. cat /proc/asound/modules
5. Take note of the name of the card you don’t want to be the default. As mentioned mine was
“snd_hda_intel”. You then need to open up the Alsa base configuration file.
6. sudo gedit /etc/modprobe.d/alsa-base.conf
7. Look for the line “# Prevent abnormal drivers from grabbing index 0&#8242;&#8242;, then above it you want to put the
following...
8. options snd_hda_intel index=1
9. In the above line I’ve set the currently default card (the one I don’t want as the default) to an index of 1.
This will force the other card to become index 0 and hence the default.
04/26/2013 
Kudos to Robert Beal for the fix!

---

### Post by bmass on 2013-04-26
> **pqwoerituytrueiwoq said:**
> i updated the readme file

[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

this should fix the hdmi issue you are having

I followed the instructions for the GUI install and it seemed to go fine but did not solve the issue. I then used the wget install, here is my terminal output:

```
trippy@Peace-Hammer:~$ cd /tmp
trippy@Peace-Hammer:/tmp$ git clone git://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
trippy@Peace-Hammer:/tmp$ wget https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/archive/master.zip -O Ubuntu-Mainline-Kernel-Updater.zip
--2013-04-26 17:01:36--  https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/archive/master.zip
Resolving github.com (github.com)... 204.232.175.90
Connecting to github.com (github.com)|204.232.175.90|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://codeload.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/zip/master [following]
--2013-04-26 17:01:37--  https://codeload.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/zip/master
Resolving codeload.github.com (codeload.github.com)... 204.232.175.86
Connecting to codeload.github.com (codeload.github.com)|204.232.175.86|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4892 (4.8K) [application/zip]
Saving to: ‘Ubuntu-Mainline-Kernel-Updater.zip’

100%[======================================>] 4,892       --.-K/s   in 0s      

2013-04-26 17:01:37 (692 MB/s) - ‘Ubuntu-Mainline-Kernel-Updater.zip’ saved [4892/4892]

trippy@Peace-Hammer:/tmp$ unzip Ubuntu-Mainline-Kernel-Updater.zip
Archive:  Ubuntu-Mainline-Kernel-Updater.zip
618a6fcdbed35be0c743e3da0b66a0b7d395f81d
replace Ubuntu-Mainline-Kernel-Updater-master/KernelUpdate.desktop? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdate.desktop  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdateChecker  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdateScriptGenerator  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/README.md  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/install  
trippy@Peace-Hammer:/tmp$ bash Ubuntu-Mainline-Kernel-Updater-master/install
Need a couple dependencies
[sudo] password for trippy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version.
php5-cli is already the newest version.
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
mkdir: cannot create directory ‘/home/trippy/.config/autostart/’: File exists
Install Complete
Updates will be checked for 60 seconds after login
If you want Release Candidates you will need to edit the new startup entry.
trippy@Peace-Hammer:/tmp$ KernelUpdateChecker -no-rc
trippy@Peace-Hammer:/tmp$ sudo sed "s/'-q'/\"-\$r\"/" -i /usr/local/bin/KernelUpdateScriptGenerator
```

I restarted my computer after both installs. I still have no sound through HDMI and no option for HDMI in my sound controls under Output Devices. Is there something else I'm supposed to do? I feel like I might be missing a major part of this fix. I'm just doing exactly the steps on the readme. Is there a command I'm supposed to run after I install? Thanks.

---

### Post by pqwoerituytrueiwoq on 2013-04-26
> **bmass said:**
> I followed the instructions for the GUI install and it seemed to go fine but did not solve the issue. I then used the wget install, here is my terminal output:
I restarted my computer after both installs. I still have no sound through HDMI and no option for HDMI in my sound controls under Output Devices. Is there something else I'm supposed to do? I feel like I might be missing a major part of this fix. I'm just doing exactly the steps on the readme. Is there a command I'm supposed to run after I install? Thanks.

what does the command [FONT=courier new]uname -r[/FONT] give you?

---

### Post by bmass on 2013-04-26
> **pqwoerituytrueiwoq said:**
> what does the command [FONT=courier new]uname -r[/FONT] give you?

```
peace-hammer@Peace-Factory:~$ uname -r
3.8.0-19-generic

```


I actually did something that screwed my Ubuntu install so I just reinstalled. This is literally every single thing I did following the install (not that much).

Plugged in my HDMI cable (from TV to laptop)
Plugged in USB for external audio adapter


installed proprietary graphics drivers using the following code:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

restarted laptop

downloaded (from Ubuntu software centre): restricted extras, vlc, pulse audio volume controller, chromium web browser

used pulse audio to tell Ubuntu the external audio adapter outputs in 5.1

transferred a video from external harddrive to /home/videos to test sound/vlc/other media related stuff

downloaded the .zip from your link
extracted the folder in the archive to /tmp
opened a console and typed the following:

```
peace-hammer@Peace-Factory:~$ cd /tmp
peace-hammer@Peace-Factory:/tmp$ wget https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/archive/master.zip -O Ubuntu-Mainline-Kernel-Updater.zip
--2013-04-26 21:04:34--  https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/archive/master.zip
Resolving github.com (github.com)... 204.232.175.90
Connecting to github.com (github.com)|204.232.175.90|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://codeload.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/zip/master [following]
--2013-04-26 21:04:35--  https://codeload.github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/zip/master
Resolving codeload.github.com (codeload.github.com)... 204.232.175.86
Connecting to codeload.github.com (codeload.github.com)|204.232.175.86|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4892 (4.8K) [application/zip]
Saving to: ‘Ubuntu-Mainline-Kernel-Updater.zip’

100%[======================================>] 4,892       --.-K/s   in 0s      

2013-04-26 21:04:35 (755 MB/s) - ‘Ubuntu-Mainline-Kernel-Updater.zip’ saved [4892/4892]

peace-hammer@Peace-Factory:/tmp$ unzip Ubuntu-Mainline-Kernel-Updater.zip
Archive:  Ubuntu-Mainline-Kernel-Updater.zip
618a6fcdbed35be0c743e3da0b66a0b7d395f81d
replace Ubuntu-Mainline-Kernel-Updater-master/KernelUpdate.desktop? [y]es, [n]o, [A]ll, [N]one, [r]ename: A
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdate.desktop  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdateChecker  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/KernelUpdateScriptGenerator  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/README.md  
  inflating: Ubuntu-Mainline-Kernel-Updater-master/install  
peace-hammer@Peace-Factory:/tmp$ bash Ubuntu-Mainline-Kernel-Updater-master/install
Need a couple dependencies
[sudo] password for peace-hammer: 
Sorry, try again.
[sudo] password for peace-hammer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  curl php5-cli php5-common
0 upgraded, 3 newly installed, 0 to remove and 24 not upgraded.
Need to get 3,211 kB of archives.
After this operation, 9,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ raring/main php5-common amd64 5.4.9-4ubuntu2 [431 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ raring/main curl amd64 7.29.0-1ubuntu3 [149 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ raring/main php5-cli amd64 5.4.9-4ubuntu2 [2,631 kB]
Fetched 3,211 kB in 4s (664 kB/s)     
Selecting previously unselected package php5-common.
(Reading database ... 158178 files and directories currently installed.)
Unpacking php5-common (from .../php5-common_5.4.9-4ubuntu2_amd64.deb) ...
Selecting previously unselected package curl.
Unpacking curl (from .../curl_7.29.0-1ubuntu3_amd64.deb) ...
Selecting previously unselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.4.9-4ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up php5-common (5.4.9-4ubuntu2) ...

Creating config file /etc/php5/mods-available/pdo.ini with new version
Setting up curl (7.29.0-1ubuntu3) ...
Setting up php5-cli (5.4.9-4ubuntu2) ...

Creating config file /etc/php5/cli/php.ini with new version
update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode
Install Complete
Updates will be checked for 60 seconds after login
If you want Release Candidates you will need to edit the new startup entry.
peace-hammer@Peace-Factory:/tmp$ KernelUpdateChecker -no-rc
peace-hammer@Peace-Factory:/tmp$ 

```

restarted my computer and ran the code you just told me to give the output of my current kernel version. Still no sign of an HDMI option in my audio controls for an output device. Thanks for the help so far.

---

### Post by pqwoerituytrueiwoq on 2013-04-26
you are still using the old kernel you have not used the update script made you just installed it
run these commands
```
~$ KernelUpdateChecker -no-rc
#then run
~$ /tmp/kernel-update
```

---

### Post by ppjdee on 2013-04-26
So simply updating to the 3.9 kernel will fix most hdmi sound issues with nvidia or ati?

---

### Post by pqwoerituytrueiwoq on 2013-04-26
> **ppjdee said:**
> So simply updating to the 3.9 kernel will fix most hdmi sound issues with nvidia or ati?
not sure about ati, there are some intel hdmi issues as well it fixes, no harm is trying it and finding out

---

### Post by ppjdee on 2013-04-27
> **pqwoerituytrueiwoq said:**
> not sure about ati, there are some intel hdmi issues as well it fixes, no harm is trying it and finding out

Just rebooted. Seems it fixed it, rocking out to badcompany now lol.
edit: the script made it so simple thanks.

---

### Post by seba74 on 2013-04-27
With my alc888 and nvidia gt 218 ob my twitech, your [COLOR=#4183C4][FONT=Helvetica][B][Ubuntu-Mainline-Kernel-Updater]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater") worked thanks.

[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)[/B][/FONT][/COLOR]

---

### Post by bmass on 2013-04-27
> **pqwoerituytrueiwoq said:**
> you are still using the old kernel you have not used the update script made you just installed it
run these commands
```
~$ KernelUpdateChecker -no-rc
#then run
~$ /tmp/kernel-update
```

Thank you. This fixed the issue upon restart.

---

### Post by rpdayton on 2013-04-28
ok so I tried ubuntu 13.04 rarring ringtail and I got no sound now on my tv which is a hdmi.
i tryed a new hdmi cabel which was shorter because i guess that might make a problem.
and then i got a dvd player with hdmi because the man at best buy said that if the hdmi port is bad it wont work with a dvd player but it does so it is a good port.
then i take my tv down from the wall and put it in the basement where my other computer is the one with windows and i got another hdmi cabel and hooked it up and it worked fine so i put it back upstairs and tryed all 3 hdmi cabels and none of them is working so it must be this sound card right?
so i went to cincinnati and got a new sound card a pny geforce that is supposed to be really good and put it in.
so then i got a new download from the ubuntu sight and put it on a new dvd and installed it again and told it to get rid of everything and do a fresh install and whipe away everything else and ut-oh still no sound.
so then i looked on here and found a lot of people saying it was fixed and so i thot to try this.
So I read this and it says it is fixed but I can't get it to work.
there is lots of things posted and then there are edit to the things that are posted and then other things to try and a whole lot of people saying i tried this and then i tried that and then there is another script on the next page with more options and then a hole lot of commands about alsa and more edits to the script.
all i am getting is 2 same sound cards if i use [COLOR=#000000]cat /proc/asound/modules and i don't know how to figure out what is the default.
and all i get when i install the script (first one or any of the others to.) is that there is a missing file ("operand") and then it says to use --help but that give a hole lot of things about makeing backups and binaries and selinux security
and all i get when i try KernelUpdateChecker with any of the minuses that are posted is that now its not found.
so what i want to know is with all the different things on here that is to try, which one is the one to make it fixed? if it is fixed then why are so many different things to try and which ones are the real ones to use.[/COLOR]

---

### Post by pqwoerituytrueiwoq on 2013-04-28
Here is the kernel update checker install guide:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

### Post by brianary on 2013-04-28
The script worked very well, and now **uname -r** returns **3.8.9-030809-generic**. (I was worried, because when I tried to perform the upgrade manually yesterday, things did not go as well.)
To complicate matters, I'm using a network adaptor that is [an enormous pain to install and maintain]("http://bernaerts.dyndns.org/linux/229-ubuntu-precise-dlink-dwa160-revb2") (the dkms instructions have never worked for me), and freezes the machine all too frequently, often beyond the ability of the magic REISUB SysReq magic to force a reboot.
Thankfully, that's still working (as well as it ever does) after the mainline upgrade and a recompile of the driver.

However, I still have no HDMI volume controls in alsamixer.

** aplay -L** returns:

```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC662 rev1 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```

Running **cat /proc/asound/card1/eld#1.0** indicates that's what my TV is plugged into, which corresponds to card 1, device 7 (according to [HDMI Audio on NVIDIA GPUs]("http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html")).

alsamixer defaults to card0, but when I use F6 to switch to card1, this is all I get:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.25 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                     F1:  Help               &#9474;
&#9474; Chip: Nvidia GPU 0b HDMI/DP                          F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                        &#9474;
&#9474;                       &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                        &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                        &#9474;
&#9474;                    < S/PDIF >S/PDIF 1 S/PDIF 2 S/PDIF 3                      &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

What am I missing?

---

### Post by brianary on 2013-04-28
Nevermind. Despite the alsamixer, I have sound now.

---

### Post by tonezone on 2013-07-14
Thank you for creating this update script. It has been awhile since the last post but the issue still remains. I encountered an error you may wish to address in the readme. After extracting the script from the .zip archive and trying to run it, it said permission denied. I used chmod +x to correct the issue, but this might be hard to a newbie to figure out. I believe that zip archives do not retain file permissions, you may wish to address that issue in the readme, or remove the .zip entirely and have people use other methods. 

After using this script my computer got back to the same state that it was in before I updated. The front left and right speakers work, but the rest of my 5.1 system does not.

---

### Post by pqwoerituytrueiwoq on 2013-07-14
> **tonezone said:**
> Thank you for creating this update script. It has been awhile since the last post but the issue still remains. I encountered an error you may wish to address in the readme. After extracting the script from the .zip archive and trying to run it, it said permission denied. I used chmod +x to correct the issue, but this might be hard to a newbie to figure out. I believe that zip archives do not retain file permissions, you may wish to address that issue in the readme, or remove the .zip entirely and have people use other methods. 

After using this script my computer got back to the same state that it was in before I updated. The front left and right speakers work, but the rest of my 5.1 system does not.executable permissions are not required it you use bash/sh in front of the /path/to/script part, these are bash scripts which is how th readme says to do it
```
chad@M4A79XTD-EVO:/tmp/test$ echo -e '#!'"/bin/bash\necho Hello World" > ./script
chad@M4A79XTD-EVO:/tmp/test$ bash ./script
Hello World
chad@M4A79XTD-EVO:/tmp/test$ ls -l
total 4
-rw-rw-r-- 1 chad chad 29 Jul 14 11:51 script
```

---

### Post by bmass on 2013-09-07
> **pqwoerituytrueiwoq said:**
> Here is the kernel update checker install guide:
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

So I had an ASUS ROG G74Sx when I first installed Ubuntu 13.04 and updated to latest proprietary nVidia graphics drivers via Software Sources > Additional Drivers and got no hdmi sound (I don't remember whether I had sound before updating the drivers but I know they were up to date with working sound in the end). Then I came here and ran the script (before I had sound working; posting as bmass, and before you made the guide in this quote) and updated the kernel and my sound worked fine. It also fixed some other multi-monitor issues I was having. This would have been around April or May when Raring Ringtail first came out (and you can check the time from my posts as bmass).

Now I've just got a new ASUS N56VZ and unfortunately it has nVidia Optimus technology. I have high hopes that this will work a little better in Saucy Salamander (as I've read that it is supposed to) but for right now I have yet to find an nVidia driver update that doesn't completely break Unity (as in after login there is nothing but the wallpaper, no launcher or menu bar); so if anyone happens to know how to update nVidia drivers for Asus N56VZ without breaking Unity I would love to hear it either in a reply or personal message to keep the thread from going off topic. THE POINT is that I'm using the Nouveau drivers for my GeForce GT 650M as I haven't found any nVidia drivers that are acceptable.

Why am I mentioning all this video driver stuff? Some people have indicated that their ability to get audio out of an hdmi cable seems to be related somewhat to their graphics drivers. I don't know if it is for me.

I did manage to install Bumblebee with nVidia-304 drivers WITHOUT breaking Unity... but then I get no output through hdmi at all (no video, no audio, no detection from the cable period). From what I understand this is a known issue with a workaround here: [http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html) but it involves runnig two simultaneous DEs and they aren't exactly connected the way two monitors are in a normal HDMI setup. SO IN THE END I ABANDONDED THIS SETUP.

Why am I including this information? If someone managed to get the setup working with Bumblebee and HDMI output for GT 650M or similar cards I would greatly appreciate any help or information.

For right now I understand that everything is running off my intel integrated graphics card which only has 64mb of memory. As far as I can tell, there is no good way for me to make use of my dedicated graphics card in Ubuntu 13.04. My best option for improved graphic performance is to increase the amount of video memory in the BIOS. Maybe 256mb or 512mb? Any suggestion?



Sorry if all that video information is very off-topic but I know sometimes nVidia controls audio and video which is why I imagine some people's setups were affected by video drivers. I just want to clarify that I have no proprietary drivers. Here is some info:
```
peacehammer@peacefactory:~$ lspci -k | grep -iA2 vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. N56VZ
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M / GTX 660M LE] (rev a1)
    Subsystem: ASUSTeK Computer Inc. N56VZ
    Kernel driver in use: nouveau
peacehammer@peacefactory:~$ 

```

I am also kinda asking video advice in the hope that if I get nVidia drivers installed in a way that allows HDMI output that the sound might also work.




END OF SLIGHTLY OFF-TOPIC
===========================
MAIN QUESTION:



So I'm running the Asus N56VZ with practically a vanilla install. I followed the guide you made in the quote and it seemed to carry out everything successfully. I updated to (what I assume to be) the latest kernel version and removed the old one. I rebooted successfully but there is still no option for HDMI output in the sound settings. Only Digital Ouput, Speakers, Analog Output


When I updated to the latest kernel with the G74Sx it was a few months ago and so I imagine a different kernel version. I have also seen that some people have solved their hdmi output problems by rolling back to an earlier kernel release. Is it the case that it was fixed and got broke again and that I need to try and rollback to a specific kernel release? Before carrying out the instructions in your guide I downloaded and installed the following packages in an effort to fix the issue as recommended by some other guides (which is why I said practically vanilla Ubuntu installtion):

linux-headers-3.8.8-030808_3.8.8-030808.201304170248_all.deb
linux-headers-3.8.8-030808-generic_3.8.8-030808.201304170248_amd64.deb
linux-image-3.8.8-030808-generic_3.8.8-030808.201304170248_amd64.deb
linux-image-extra-3.8.8-030808-generic_3.8.8-030808.201304170248_amd64.deb
oem-audio-hda-daily-dkms_0.201309071535~ubuntu13.04.1_all.deb

I have two of these laptops and the other one is currently running a completely vanilla Ubuntu 13.04 so I will follow the quoted instructions once more on that laptop (exact same laptop) and let you know if there is any difference in the results. Thanks again. Sorry for the off-topic video stuff.... I hope it actually turns out o be relevant or useful in some way and let me know if I can provide any more information. I'm also a lot more linux proficient than when I was posting as bmass :P

EDIT: Synaptic is showing my current kernel version to be 3.8.0 after running your script. I have no option for hdmi sound in sound settings or pulseaudio volume coontrol. I'm going to restart and try kernel version 3.8.8 again and restart. If it doesn't work I'll give the latest 3.10.5 a try and let you know if any of that works. Meanwhile I'll try your script on my vanilla Ubuntu to see if it was something else I did that borked this system. Thanks for reading.

---

### Post by cariboo on 2013-09-07
There a couple things that I see, that may be a part of your problem, the default kernel in Saucy is 3.11.0-4, and the default nvidia driver is 3i9.32.

Have you tried the upstream kernel, to see if the problem still exists? They are available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/").

---

### Post by bmass on 2013-09-09
> **cariboo907 said:**
> There a couple things that I see, that may be a part of your problem, the default kernel in Saucy is 3.11.0-4, and the default nvidia driver is 3i9.32.

Have you tried the upstream kernel, to see if the problem still exists? They are available [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/").

So I just noticed this thread is in the Ubuntu +1 board. That means its for development and that I should be using the daily builds of Saucy Salamander or whatever the next upcoming release of Ubuntu is? I never realized this when I was posting back in April. Should I post for support in the Ubuntu General Help board or continue posting here? I am currently running Ubuntu 13.04 Raring Ringtail with kernel version 3.11.0-031100-generic

I am not trying to help develop the next Ubuntu release (yet, but hopefully in a few months to a year when I get a better grasp on things), I'm just trying to get my new laptops running the latest stable Ubuntu (13.04 for the next month and then Saucy when it's out and ready) with my dedicated graphics card (hopefully) and working HDMI output with video and audio. So please let me know if I should post in another board or continue posting here.

As far as the nVdia 319.32 driver (I just saw 319.49 on nVidia's website was released a couple weeks ago also), if I install any proprietary nVidia driver currently it breaks unity (this can be repaired be restarting unity with compiz and resolving conflicts with gnome-something i can't remeber-package but I'm not sure everything is working dandy) except when using Bumblebee but either way there is not even video output from HDMI. I only have video ouput with a basically vanilla install of Ubuntu. No nvidia drivers.

Still no sound output through HDMI (no option in sound settings) with any of the kernels. And again let me now if I should post in another board. Thanks.

P.S. I am still doing reading on how to best configure video drivers (with and without Bumblebee) with my N56VZs but one of the HDMI outputs completely crapped out (tried in Ubuntu 13.04, Mint 15, Windows 7), TVs are detected in Displays but just no video output; stupid refurbished laptops... but $1200 down to $650, who could resist? Anyway, I'm down to both finding a way to get HDMI sound to work with Nouveau drivers and trying to get HDMI video to work with nVidia drivers but down to one laptop. Sending the other one back for replacement. Got a S56CM that worked with HDMI sound on vanilla Ubuntu 13.04 install. I don't know if that information is relevant or helpful... they are pretty different systems except GPUs are both are GeForce 600M series with Optimus. Thanks btw.

---

