---
title: "Optirun broken"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-03-20
Anyone had luck with Optirun in Precise? Not working here :|
Cannot find a usable panel for the Nvidia card.

There is an upstream bug report for this:
[https://github.com/Bumblebee-Project/Bumblebee/issues/88](https://github.com/Bumblebee-Project/Bumblebee/issues/88)

I've already posted there, pasting here just for the sake of completeness:
> My issue seems a bit different.. it looks like it is not able to identify the panel properties (was working properly in Oneiric):

[INFO]Response: No - error: XORG NVIDIA(0): No display devices found for this X screen.
[ERROR]Cannot access secondary GPU - error: XORG NVIDIA(0): No display devices found for this X screen.
[ERROR]Aborting because fallback start is disabled.

Tried to change "AutoAddDevices" and "ConnectedMonitor" but no luck...
this is my xorg.8.log, hope it helps:

[http://paste.ubuntu.com/892295/](http://paste.ubuntu.com/892295/)

---

### Post by dino99 on 2012-03-20
might not be related to your issue, but today i've browse libGl issue on nvnews, and they says that 295.20 is buggy and 295.10 might be used instead.

is your issue with the Precise default packages ? or with the newest kernel + edgers ppa ?

---

### Post by lucazade on 2012-03-20
Thanks Dino for the suggestion.

After half a day of trials I've finally found a solution.. yeah!

nvidia-current 295.20, dependency of bumblebee-nvidia, installs some quirks for notebooks but they were no good for the Dell L702X I use at work.

```
echo 'Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "true"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "true"
    Option "ConnectedMonitor" "DFP"
EndSection' | sudo tee /usr/share/X11/xorg.conf.d/10-nvidia-current-updates-latitude-e6530.conf
```

this fixes the wrong panel detection via DFP and fixes a Xorg crash via AutoAddDevices.

:D

---

### Post by Lekensteyn on 2012-03-20
The only differences in that file is AutoAddDevices (known issue [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/931397](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/931397)) and UseEDID. Do you have an external monitor connected to the machine? Otherwise it's unlikely that UseEDID works.

---

### Post by lucazade on 2012-03-20
> **Lekensteyn said:**
> The only differences in that file is AutoAddDevices (known issue [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/931397](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/931397)) and UseEDID. Do you have an external monitor connected to the machine? Otherwise it's unlikely that UseEDID works.

I believe you're right UseEDID made the difference in detecting the panel, without it I got " No display devices found for this X screen."

Once enabled it I got the xorg crash when using optirun and fixed it via "AutoAddDevices"

well, my brain after all these trials is currently in kernel panic.. 
next thing will be open a bug against nvidia-current for wrong quirks..
other suggestions?

---

### Post by Hanine on 2012-04-09
Ok: Appending the new modified content of** bumblebee nvidia configuration file **to **/usr/share/X11/xorg.conf.d/10-nvidia-current-updates-latitude-e6530.conf **.

the 
   Option "AutoAddDevices" "true" is no more needed to be true. You can revert it to false. as the reltaed xorg bug has been fixed.

---

### Post by sayantandas on 2012-04-13
> **Hanine said:**
> Ok: Appending the new modified content of** bumblebee nvidia configuration file **to **/usr/share/X11/xorg.conf.d/10-nvidia-current-updates-latitude-e6530.conf **.

the 
   Option "AutoAddDevices" "true" is no more needed to be true. You can revert it to false. as the reltaed xorg bug has been fixed.

I still get the same error. nothing's changed.

---

### Post by Hanine on 2012-04-13
> **sayantandas said:**
> I still get the same error. nothing's changed.

Really!?
What are you running? 11.10 or 12.04?
What kernel and what Nvidia card do you have?
Nouveau drivers or proprietary drivers?

```
lspci | grep VGA
```

```
uname -a
```

```
optirun --version
```

```
optirun nvidia-settings -c :8
```

---

### Post by sayantandas on 2012-04-14
> **Hanine said:**
> Really!?
What are you running? 11.10 or 12.04?
What kernel and what Nvidia card do you have?
Nouveau drivers or proprietary drivers?

```
lspci | grep VGA
``````
uname -a
``````
optirun --version
``````
optirun nvidia-settings -c :8
```


Here's the requested outputs

 ```
Vostro-3300:~$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev ff)
``````
Vostro-3300:~$ uname -a
Linux sayantan-Vostro-3300 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
Vostro-3300:~$ optirun --version
optirun (Bumblebee) 3.0
Copyright (C) 2011 The Bumblebee Project
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
``````
Vostro-3300:~$ optirun nvidia-settings -c :8
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): No display devices found for this X screen.

[ERROR]Aborting because fallback start is disabled.
```

---

### Post by Hanine on 2012-04-16
> **sayantandas said:**
> Here's the requested outputs

 ```
Vostro-3300:~$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev ff)
``````
Vostro-3300:~$ uname -a
Linux sayantan-Vostro-3300 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
Vostro-3300:~$ optirun --version
optirun (Bumblebee) 3.0
Copyright (C) 2011 The Bumblebee Project
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
``````
Vostro-3300:~$ optirun nvidia-settings -c :8
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): No display devices found for this X screen.

[ERROR]Aborting because fallback start is disabled.
```

I see.
You should have the same config as me:

in /etc/bumblebee/xorg.conf.nvidia

```
Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "false"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "ConnectedMonitor" "DFP"
EndSection
```

Don't add anything to this.
Then tell me what happens after you apply these changes and reboot.

---

