---
title: "Error upgrading to 9.04"
date: 2009-04-26
forum: Server Platforms
---

### Post by kfleten on 2009-04-26
Hi 

I have an Edubuntu 8.10 server, wich I try to upgrade to 9.04.

The upgrade process has stopped, and the terminal window says:

Extracting templates from packages: 100%
Preconfiguring packages ...
moodle failed to preconfigure, with exit status 1
supported_versions: WARNING: unknown ubuntu release 8.10
Extracting templates from packages: 100%
Preconfiguring packages ...

Is it safe to interrupt by pressing Ctrl+C and restart ? What other options do I have ?

Kjetil Fleten

---

### Post by kfleten on 2009-05-30
Now, I have tried to interrupt the upgrade. 
!!! I will NOT recommend that to others !!!
The server still worked, but was only partly upgraded. After trying to install more packages and rebooting, I ran into initramfs problems telling me /dev/disk/by-uuid does not exist and dropping to a shell. Now I'm stock with something similar to this: [http://ubuntuforums.org/showthread.php?t=1120858](http://ubuntuforums.org/showthread.php?t=1120858)

---

### Post by cariboo on 2009-05-30
IF you can start with the proevious kernel, you may be able to save your set up. At the prompt type:

```
sudo apt-get -f install
```

this should install missing dependencies and configure packages that are only partitally installed. Next run

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by kfleten on 2009-05-31
It was possible to start with a previous kernel. Unfortunately, the USB system seems to be broken, so keyboard and mouse does not work. I have tried several different kernels and recovery mode without getting it to work. I have also changed the USB port for both keyboard and mouse, tried a different keyboard, booted without mouse etc.

Now I have inserted a 9.04 server installation CD and launched the rescue system. Now I have a shell prompt. 

Will 
sudo apt-get -f install 
and
sudo apt-get update && sudo apt-get dist-upgrade

owerwrite existing installation when booted from a cd instead of HDD ?

---

