---
title: "Help in Filing Bug - Upgrade of LibC, Breaks PowerShell Snap Package"
date: 2020-03-15
forum: Ubuntu Development Version
---

### Post by macevic040 on 2020-03-15
I've been testing Ubuntu Focal on various machines and am new at filing bugs.
Sat 14th March AM, and upgraded my system.
PowerShell snap was throwing an error with librt.so (Sorry I didn't save output).
I reverted to an earlier ZFS Snapshot and all was OK.

Sun 15th March updates were automatically installed. (I know because the Plymouth spinner had changes).
PowerShell was throwing the error again, so reverted to earlier snapshot again.
I have held back the following with 'apt-mark'
```
apt-mark showheld
libc-bin
libc-dev-bin
libc6
libc6-dbg
libc6-dev
libcc1-0

```
Perforned an apt update, upgrade and also rebooted. And found all was OK.
Proposed Updates is not enabled.
Is this the correct place to notify of this type of bug? If not can you point me in the correct direction.

Thanks for Wimpy and Popey for their excellent Youtube/LBRY Videos. They've really piqued my interest ;)
I'm enjoying testing and want to contribute to the Ubuntu Community.

---

### Post by guiverc on 2020-03-15
Bugs generally should be reported on launchpad ([https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))

The best way to do it is `ubuntu-bug <package>`.   When you're not sure though, asking on a site such as this is a really good idea. 

Myself, I'd look in your /var/crash/ folder for details of the last bug, eg. on my system I can see the following

```
guiverc@d960-ubu2:~/temp$   ls -la /var/crash
total 5348
drwxrwsrwt  2 root    whoopsie    4096 Mar 14 23:26 .
drwxr-xr-x 16 root    root        4096 Nov 29  2018 ..
-rw-------  1 root    whoopsie  519416 Mar  9 13:21 ubuntustudio-wallpapers-focal.0.crash
-rw-r-----  1 guiverc whoopsie 3793826 Mar 14 23:27 _usr_lib_ibus_ibus-ui-gtk3.1000.crash
```

and in this example I'll pick on the last (the _usr-lib one), in your case I hope you'll recognize your own crash by filename (ie. crash package, if not the date/time of crash). 

To file my own issue with _usr_lib_ibus_ibus-ui-gtk3.1000.crash

```
guiverc@d960-ubu2:~/temp$   ubuntu-bug /var/crash/_usr_lib_ibus_ibus-ui-gtk3.1000.crash 
```

and I window appears on my system (a Lubuntu desktop system) so I just follow prompts.

I'd hope you can recognize the .crash file in your /var/crash, and I'd suggest the first step is to `ubuntu-bug` that .crash file...

---

### Post by macevic040 on 2020-03-15
Thanks for your quick reply - useful info.
I will do as you suggest.

---

### Post by guiverc on 2020-03-15
And I just noted

```
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev locales python-pil
7 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

on my own system and instantly remembered back to this post... maybe I'll get a chance to experience whatever you did...  we'll see..   then again maybe these are fixes :)

---

### Post by macevic040 on 2020-03-15
guiverc - I'm working on PowerShell Koans at the moment (useful for work), so I'll leave the packages on hold for a few days, then try upgrading them again.
There was nothing in my /var/crash folder, so I asked a question on launchpad about this bug.
I'd mark this as solved if i knew how, because i just wanted to notify someone of this issue.
Thanks again for your replies.

---

### Post by macevic040 on 2020-03-15
huh found the thread tools :) Solved!

---

### Post by macevic040 on 2020-03-16
FYI: The error received...
```
$ pwsh
Failed to load &#65533;V^, error: /snap/powershell/104/opt/powershell/../../lib/x86_64-linux-gnu/librt.so.1: undefined symbol: __clock_nanosleep, version GLIBC_PRIVATE
Failed to bind to CoreCLR at '/snap/powershell/104/opt/powershell/'
Failed to create CoreCLR, HRESULT: 0x80008088
```

---

