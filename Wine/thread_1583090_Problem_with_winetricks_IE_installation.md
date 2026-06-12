---
title: "Problem with winetricks IE installation"
date: 2010-09-27
forum: Wine
---

### Post by bitteralmond on 2010-09-27
I tried to use winetricks to install Internet Explorer 7, but I got this error in a window during installation:

"The program regsvr32.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience."

Other errors I get on the terminal are:
```
fixme:clusapi:GetNodeClusterState ((null),0x32ec3c) stub!
fixme:advapi:DecryptFileA "c:\\ee1f18359cd3db8050bc81c9674d62\\" 00000000
```How do I fix it?

Update: When I try to install Internet Explorer 8 with winetricks, I get this window:

"Internet Explorer 8 is not supported on this operating system."

Errors on the terminal are:

```
fixme:clusapi:GetNodeClusterState ((null),0x32ebbc) stub!
fixme:advapi:DecryptFileA "c:\\8b63785f1f651630b2787736\\" 00000000
fixme:advapi:RegisterTraceGuidsW (0x6cd15f38, 0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33f898, (null), (null), 0x6cd20188,)

```

---

### Post by Lankster on 2012-02-05
I keep getting this but don't know how to fix the problem. Its like no matter what program I try to install I get this error: 

"The program regsvr32.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience."

It happens when Im in Wine. Is this a Ubuntu problem or a Wine.. Problem??

edit:
Also when I try to close that window it just keeps coming back.... The window will no close...

---

### Post by dino99 on 2012-02-05
rename your actual borked .wine to .wine_old & make a new clean .wine by reinstalling wine

---

### Post by Chutney3k on 2012-03-09
I think I know what the issue is here (at least it is for me)

(Winetricks could benefit from an option to 'reinstall' or clear cache etc. IMO)

Work around:

Close all wine programs. 
rename your .wine folder to .wine_bak (or whatever you'd prefer) then remove all instances of wine AND winetricks under the software center.
Re-install the latest wine which should also install winetricks for you.

Enter wineconfig and ensure that the default operating environment is set to Win XP!!! (IE 8 is designed for XP, not vista/win7).

Run winetricks, select the default prefix and choose 'install a windows component or dll'

scroll to ie8 and check the box, then click OK. 

ie8 should install ok now.

---

