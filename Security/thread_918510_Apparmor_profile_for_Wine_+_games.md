---
title: "Apparmor profile for Wine + games"
date: 2008-09-13
forum: Security
---

### Post by rrfx on 2008-09-13
Hey guys, 

I'm trying create an Apparmor profile to play a game under Wine. This *mostly* works, so i thought i'd share and see what experiences others' have had. 

**Background:** Eve Online comes with a python25.dll file, implying it has an embedded python interpreter. To me, playing a game that can so easily execute arbitrary code, potentially accessing my personal files is a concern. While Eve is a great game, I have been less than impressed with the developers' security record!! (killing boot.ini, leaked sources etc)

The "premium" Windows version of Eve runs fine on Wine v1.0+ on my 64bit ubuntu, with Nvidia drivers etc. This same process would work with CCP's linux version (cedega wrapper), or any other Wine compatible game. 

Apparmor ships with Hardy, it allows individual programs to be completely restricted and then have access permissions whitelisted. 

**Howto: **I started by creating a fresh Wine folder in /opt/games/eve/wine (using WINEPREFIX=/opt/games/eve/wine && winecfg) and then installed the game there (WINEPREFIX=/opt/games/eve/wine && EVE_Premium_Setup_58188.exe).

Next i created a simple bash script called /opt/games/eve/load that fires up the game: 
```
#!/bin/bash
export WINEPREFIX=/opt/games/eve/wine
wine explorer /desktop=Eve,1680x1050 /opt/games/eve/wine/drive_c/Program\ Files/CCP/EVE/eve.exe
```
This is important, since you probably dont want to create a Apparmor profile that restricts all Wine apps! 

There's plenty of howto's describing generating a new profile, 'aa-genprof /opt/games/eve/load' is a good start. After a bit of hand-tuning, i came up with this profile:
```
#include <tunables/global>
/opt/games/eve/load {
    #include <abstractions/base>
    #include <abstractions/nvidia>
    #include <abstractions/fonts>
    #include <abstractions/audio>
    #include <abstractions/nameservice>

    capability ipc_lock,
    capability ipc_owner,

    /opt/games/eve/load r,
    /opt/games/eve/wine/drive_c/Program\ Files/CCP/EVE/eve.exe rmix,

    /bin/bash rmix,
    /usr/bin/wine** rmix,
    /usr/lib32/wine/** mr,
    /etc/localtime r,
    /usr/lib32/libgcc_s.so.1 r,
    /usr/share/wine/fonts** r,
    /usr/share/icons** r,
    /usr/share/X11/** r,

    /home/rrfx/.lpoptions r,
    /var/run/dbus/system_bus_socket rw,
    /var/run/cups/cups.sock rw,
    /etc/cups/lpoptions r,

    /etc/localtime r,
    /etc/fstab r,
    /etc/mtab r,
    /etc/localtime r,

    /opt/games/eve/wine** rw,
    /opt/games/eve/wine/drive_c/windows/system32** mr,

    /home/rrfx/.Xauthority r,
    /tmp/.wine-1000/** rwk,
    /tmp/.X11-unix/** rw,

    /proc/net** r,
    /proc/scsi** r,
    /dev/tty** rw,

}
```
This could probably be simplified, however it should be enough to block the game from having any access to the system/personal files etc.

**Problem:** ...however, while Eve loads under Wine (and only during loading) there are about 100 repeated audit entries in /var/log/syslog like this:
```
audit(1221281703.827:56377): type=1503 operation="file_mprotect" requested_mask="mr::" denied_mask="m::" name=2F6F70742F67616D65732F6576652F77696E652F64726976655F632F50726F6772616D2046696C65732F4343502F4556452F62696E2F45786546696C652E657865 pid=19092 profile="/opt/games/eve/load" namespace="default"
audit(1221281703.827:56378): type=1503 operation="file_mprotect" requested_mask="mr::" denied_mask="m::" name=2F6F70742F67616D65732F6576652F77696E652F64726976655F632F50726F6772616D2046696C65732F4343502F4556452F62696E2F626C75652E646C6C pid=19092 profile="/opt/games/eve/load" namespace="default"
audit(1221281703.827:56379): type=1503 operation="file_mprotect" requested_mask="mr::" denied_mask="m::" name=2F6F70742F67616D65732F6576652F77696E652F64726976655F632F50726F6772616D2046696C65732F4343502F4556452F62696E2F626C75652E646C6C pid=19092 profile="/opt/games/eve/load" namespace="default"
```

Does anyone know how to enable these in a profile? They dont have a full path name like normal audit errors. If they're added to the profile without a leading '/' AppArmor spits "...Found unexpected character: '2'".  

If i enforce the profile anyway, the game doesn't load. I've tried enabling different posix capabilities to no avail. 

Any ideas?

---

### Post by q.dinar on 2010-01-26
2F6F70742F67616D65732F6576652F77696E652F64726976655F632F50726F6772616D2046696C65732F4343502F4556452F62696E2F45786546696C652E657865
means
/opt/games/eve/wine/drive_c/Program Files/CCP/EVE/bin/ExeFile.exe

---

