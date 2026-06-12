---
title: "ThinkPad T60 wireless unclaimed problem"
date: 2014-08-07
forum: Ubuntu Studio
---

### Post by madcarrswu on 2014-08-07
I'm sort of new to Linux.  I have successfully installed Lubuntu on a Dell and running well for a year.  Recently I have been trying to solve a ThinkPad T60 wireless problem.  I've loaded it with Unbuntu Studios 14.04 but can't get the wireless working.  I've searched the forums for a few days and maybe I'm just missing something.  Can someone walk me through this?  Thanks

---

### Post by chili555 on 2014-08-07
Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by madcarrswu on 2014-08-07
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)

---

### Post by chili555 on 2014-08-07
Exactly the same wireless as in my T60 and it works beautifully! Let's do some additional diagnostics:```
rfkill list all
sudo modprobe iwl3945
dmesg | grep iwl
```Thanks.

---

### Post by madcarrswu on 2014-08-07
Wow.  The notification for the wireless popped up after I typed in sudo modprobe iwl3945.

[267677.069883] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[267677.069890] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[267677.069962] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[267677.126599] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[267677.126607] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[267677.126684] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[267677.284075] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[267679.413719] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

---

### Post by chili555 on 2014-08-07
Let's make certain it isn't blacklisted:```
cat /etc/modprobe.d/blacklist.conf
```And let's get it to load automagically on boot:```
sudo -i
echo iwl3945  >>  /etc/modules
exit
```You should be all set.

---

### Post by madcarrswu on 2014-08-07
I'm not sure what happened when I rebooted.  I ran the commands then rebooted. The wireless hasn't started yet.

---

### Post by madcarrswu on 2014-08-07
Thanks so much for your help.  I went back through your steps and just copied and paste the commands in case I had it wrong.  Apparently I typed something in wrong.  My wireless is now working.  Big thanks.  Now I'm trying to research the audio problem.  If you have a fix for that already I would appreciate it.

---

### Post by chili555 on 2014-08-07
> **madcarrswu said:**
> Thanks so much for your help.  I went back through your steps and just copied and paste the commands in case I had it wrong.  Apparently I typed something in wrong.  My wireless is now working.  Big thanks.  Now I'm trying to research the audio problem.  If you have a fix for that already I would appreciate it.Glad it's working.

Sorry, I know nothing about audio except that mine works. I suggest you post a new thread and give as much information as possible including your audio device details:```
sudo lshw -C multimedia
```

---

