---
title: "[Ubuntu server 20.04 lts] Ubuntu goes to sleep"
date: 2022-11-26
forum: Server Platforms
---

### Post by johndid on 2022-11-26
Hi,
I installed Ubuntu server 20.04 LTS on one of my laptops. It works great and fits my little needs for my Home Lab, but I noticed that it seems to go to sleep after a few hours (maybe).
I still haven't figured out if it has something to do with the system itself or the laptop (as far as I know it could be its network card as well).
Anyway, when it happens, I even can't connect to it via ssh, and I need to send commands directly on the machine to "wake it up".
Could you please help me fix it? 

Thanks

---

### Post by MAFoElffen on 2022-11-27
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and select upload to pastebin. Please pot the URL to the pastebin.

Ubuntu Server, by default, during a default install should not have a GUI, nor anything that should implement a suspend or any sleep settings, though... If you had selected to install third party drivers during the install, if the hardware is NVidia or equivalent, It will sometimes install a video driver or XServer by mistake.

The report from the 'system-info' script should show what is going on there...

EDIT:
Please also post the results of:
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target

```

---

### Post by johndid on 2022-11-27
> **MAFoElffen said:**
> Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and select upload to pastebin. Please pot the URL to the pastebin.

Ubuntu Server, by default, during a default install should not have a GUI, nor anything that should implement a suspend or any sleep settings, though... If you had selected to install third party drivers during the install, if the hardware is NVidia or equivalent, It will sometimes install a video driver or XServer by mistake.

The report from the 'system-info' script should show what is going on there...


There it is:

[https://pastebin.com/vfzisxGX](https://pastebin.com/vfzisxGX)


> 
EDIT:
Please also post the results of:
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target

```


ok

```

Id=sleep.target
Names=sleep.target
Wants=grub-common.service grub-initrd-fallback.service
Before=grub-initrd-fallback.service grub-common.service
Documentation=man:systemd.special(7)
Description=Sleep
LoadState=loaded
ActiveState=inactive
SubState=dead
FragmentPath=/lib/systemd/system/sleep.target
UnitFileState=static
UnitFilePreset=enabled
StateChangeTimestampMonotonic=0
InactiveExitTimestampMonotonic=0
ActiveEnterTimestampMonotonic=0
ActiveExitTimestampMonotonic=0
InactiveEnterTimestampMonotonic=0
CanStart=no
CanStop=yes
CanReload=no
CanIsolate=no
StopWhenUnneeded=yes
RefuseManualStart=yes
RefuseManualStop=no
AllowIsolate=no
DefaultDependencies=no
OnFailureJobMode=replace
IgnoreOnIsolate=no
NeedDaemonReload=no
JobTimeoutUSec=infinity
lines 1-30...skipping...
Id=sleep.target
Names=sleep.target
Wants=grub-common.service grub-initrd-fallback.service
Before=grub-initrd-fallback.service grub-common.service
Documentation=man:systemd.special(7)
Description=Sleep
LoadState=loaded
ActiveState=inactive
SubState=dead
FragmentPath=/lib/systemd/system/sleep.target
UnitFileState=static
UnitFilePreset=enabled
StateChangeTimestampMonotonic=0
InactiveExitTimestampMonotonic=0
ActiveEnterTimestampMonotonic=0
ActiveExitTimestampMonotonic=0
InactiveEnterTimestampMonotonic=0
CanStart=no
CanStop=yes
CanReload=no
CanIsolate=no
StopWhenUnneeded=yes
RefuseManualStart=yes
RefuseManualStop=no
AllowIsolate=no
DefaultDependencies=no
OnFailureJobMode=replace
IgnoreOnIsolate=no
NeedDaemonReload=no
JobTimeoutUSec=infinity
JobRunningTimeoutUSec=infinity
JobTimeoutAction=none
ConditionResult=no
AssertResult=no
ConditionTimestampMonotonic=0
AssertTimestampMonotonic=0
Transient=no
Perpetual=no
StartLimitIntervalUSec=10s
StartLimitBurst=5
StartLimitAction=none
FailureAction=none
SuccessAction=none
CollectMode=inactive



```

Maybe this can be useful to help me fix another problem as well.

I should get this line on my laptop screen at the end of the boot process:

```
*Web console: https://server:9090/ or https://192.168.10.10:9090/*
```

Which means that I can connect to its web console (I installed cockpit on ubuntu) via another pc's browser.

But it often happens that I can see only its hostname: [B][I][https://server:9090/](https://server:9090/) 

[/I][/B]In this case, I can't connect to it via browser nor start a ssh connection via putty from my PC. Thus, I only can reboot hoping that it will show its IP next time.
Could you help me fix this too?[I]

Thanks
[/I]

---

### Post by MAFoElffen on 2022-11-27
Well... LOL

When I run
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target

```
The output is 347 lines long... Which means yours only ran on sleep.target. If you ran it with a filter like this
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target | grep 'ActiveState='

```
It should have 4 lines, that end with 'inactive'.

FIX:
You should do
```

sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

```
...which will create symlinks to send the signals for that to device /dev/null, and...

Since it is a laptop... Edit file /etc/systemd/logind.conf and add
```

HandleLidSwitch=ignore

```
That will turn off the signal from the lid switch, that tries to trigger a suspend...

---

### Post by johndid on 2022-11-28
> **MAFoElffen said:**
> Well... LOL

When I run
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target

```
The output is 347 lines long... Which means yours only ran on sleep.target. If you ran it with a filter like this
```

sudo systemctl show sleep.target suspend.target hibernate.target hybrid-sleep.target | grep 'ActiveState='

```
It should have 4 lines, that end with 'inactive'.


Yes, it has 4 lines that end with 'inactive' now.

> 
Since it is a laptop... Edit file /etc/systemd/logind.conf and add
```

HandleLidSwitch=ignore

```
That will turn off the signal from the lid switch, that tries to trigger a suspend...


It was set to 'ignore' already. I must have set it this way when I installed Ubuntu maybe.

Ok, My ubuntu server is running now. I'll let it this way without using any service or shell and see what happens.

Thank you very much.

ps: I'm going to open another topic about the problem about the missing IP at the startup

---

### Post by MAFoElffen on 2022-11-28
If this is resloved, then please go to the "Thread Tools" link on the upper right and mark this as "Solved" so others can find your solution. (This gets asked lots)

---

### Post by johndid on 2022-11-28
> **MAFoElffen said:**
> If this is resloved, then please go to the "Thread Tools" link on the upper right and mark this as "Solved" so others can find your solution. (This gets asked lots)

Yes, I think it is ok now. It hasn't gone to sleep anymore so far.
Thanks agains

---

