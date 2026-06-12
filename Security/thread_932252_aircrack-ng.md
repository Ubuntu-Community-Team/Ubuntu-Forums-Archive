---
title: "aircrack-ng"
date: 2008-09-28
forum: Security
---

### Post by guest_user on 2008-09-28
Are the drivers in hardy heron automatically patched when I install aircrack-ng from the repositories because I did airmon-ng start wifi0 (using atheros card) followed by airodump-ng ath0 and it didn't show me any networks although it said that monitor mode was enabled after airmon command, any ideas what could be the problem and how do I solve it?

PS I did not patch my drivers, if it isn't automatically patched, is there a way using the package manager or something to patch the drivers automatically rather than running the shell script so that any changes could be reversed?

Another qn would be which driver patch should I use, the last time I used the patch for madwifi-ng but as I am aware, there is a new driver for the atheros chipset, ath5k, so how do I check which driver patch should I use now?


Any help appreciated, thank you.

---

### Post by sinclair86 on 2008-09-28
Probably not going to be of much help BUT I had something similar happening with hardy. I just got really frustrated removed the madwifi modules that came with hardy and installed madwifi from source. After I did that aircrack suite worked out of the box didnt have to further patch my atheos chip for packet injection or monitoring mode.

are you sure its an atheos chip as well? 

try```
lspci
```just to be sure.

---

### Post by guest_user on 2008-09-28
bump

---

### Post by binbash on 2008-09-29
You have to patch the driver.Default drivers are not patched i guess (at least for my intel).Ok first : 

Before patching the driver lets test it first.

sudo iwlist scan at new terminal and open new one.You will use the wireless list
right click network manager and disable wireless.Then 
sudo iwconfig wlan0 mode monitor
sudo airmon-ng start wlan0 11 (or whatevery channel you gonna do wireless crackin)
sudo airodump-ng -c 11 --bssid essidhere -w /home/blabla/xxx wlan0

At this point you should listen and record the ivs.If you have patched drivers you can run aireplay-ng.If there is some1 connected to the wireless you gonna crack, you dont have to aireplay-ng you can collect the ivs very fast.Of course these are for Wep encryption.Also you have to be close to router to inject packages (aireplay)
for WPA one client must connected to the network also you need john the ripper to crack the pass.etc etc.I have a headache right now, i may miss some commands ;)

---

### Post by sinclair86 on 2008-09-29
and if that doesnt work im being serious. remove the madwifi modules that come with ubuntu. after i got rid of that it didnt give me any more problems

---

### Post by guest_user on 2008-09-30
> **sinclair86 said:**
> and if that doesnt work im being serious. remove the madwifi modules that come with ubuntu. after i got rid of that it didnt give me any more problems

so you mean to say you installed from source thereafter? How do you manage packages that are installed from source and ensure that they do not conflict with existing packages?

btw, do I need to patch my drivers to put them into monitor mode because airodump-ng does not show any networks even after airmon-ng showed that monitor mode was enabled after I do airmon-ng start wifi0, so what's the problem?

---

### Post by binbash on 2008-09-30
that means it is not in monitor mode because your driver is not patched.You gonna patch it.YOU SHOULD check aircrack-ng 's docs and forums because i did the patching there.

---

### Post by sinclair86 on 2008-09-30
@ guest_user yes. you can't really manage packages installed from source. You arent going to have to patch your drivers to monitor madwifi does that. You possibly might have to patch them to do packet injection. 

Also I agree with binbash. make sure network manage is disabled because I found out that after I installed madwifi and and used network manager nothing came when i tried to monitor or even create a virtual ap.

---

### Post by master2010 on 2008-10-02
[http://ubuntuforums.org/showthread.php?p=5893031#post5893031](http://ubuntuforums.org/showthread.php?p=5893031#post5893031)

---

