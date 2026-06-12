---
title: "xfce4-power-manager1.2.0 recognizes lid events, but only in debug mode"
date: 2014-12-25
forum: Ubuntu Studio
---

### Post by Rijul_Ahuja on 2014-12-25
Hello, I am using Ubuntu Studio 14.04 LTS. I intend to set it up to lock the screen when lid is closed, for which I have done the settings in the xfce4-power-manager GUI, and added the *HandleLidSwitch=ignore* in */etc/systemd/logind.conf* and restarted it. However, putting the lid down does not do anything, unless I kill the xfce4-power-manager process and run it in debug mode.

Some command outputs (portions I deemed relevant) are below. acpid and pm-utils both are installed, xflock4 works fine.
```

$ dmesg | grep -i lid
[    1.734924] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.738722] ACPI: Lid Switch [LID]

$ cat /etc/systemd/logind.conf
[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
Controllers=blkio cpu cpuacct cpuset devices freezer hugetlb memory perf_event net_cls net_prio
ResetControllers=
#InhibitDelayMaxSec=5
HandlePowerKey=ignore
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
HandleLidSwitch=ignore
HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleAction=ignore
#IdleActionSec=30min

$ while true; do cat /proc/acpi/button/lid/LID/state ; sleep 3; done
state:      open
state:      open
state:      closed
state:      open

$ xfce4-power-manager --debug
TRACE[xfpm-manager.c:354] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_LOCK_SCREEN)
TRACE[xfpm-power.c:1170] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_ALWAYS)
TRACE[xfpm-power.c:1134] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:381] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_LOCK_SCREEN)

$ xfce4-power-manager -V
Xfce Power Manager 1.2.0

$ acpi_listen 
button/lid LID close
button/lid LID open

```

This may be unrelated and could warrant another thread, but using the command *xfce4-session-logout* logs me out of the session without a prompt. Similar symptoms are observed when choosing the "Log Out.." menu item from the power menu in the Actions Buttons item of the panel.

Help is appreciated.

---

### Post by Rijul_Ahuja on 2014-12-26
As a temporary workaround, I have made a startup script in Session & Startup with the following contents.
```
killall xfce4-power-manager
xfce4-power-manager --debug &
```

Cheers!

---

### Post by brainwash on 2015-01-02
You could just run "xfce4-power-manager --no-daemon" instead of using the debug mode. Also, this issue should be fixed in version 1.4 (Ubuntu 14.10 or later).

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1347272](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1347272)

---

