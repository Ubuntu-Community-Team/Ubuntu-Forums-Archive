---
title: "Wine+Dreamweaver Mx 2004"
date: 2009-06-21
forum: Wine
---

### Post by Shobuz99 on 2009-06-21
ok. I have upgraded to Jaunty Jacklalope 9.04 and have installed Dreamweaver Mx 2004 (6.0) with only one error that referred to MDAC for Windows. It installed anyway. 
I installed with Wine ver 1.0.8. I also put the two files odbc32.dll and odbcinit.dll in the System and System32 folders of /.wine/drive_c.
DWMX will not load. It gives me an 'untitled file' box and sits there.
Do I need a newer version of Wine? if so, how do I get it? I'm running on a 64 machine.

I can't remember what I did in Hardy 8.04 to get this to work... any suggestions? (other than get DW 8 or CS3)

As always, thank you for any help.

Rick (shobuz99)

---

### Post by NightMKoder on 2009-06-21
1. Use the latest wine. (1.1.24)
2. remove your prefix and install again. according to appdb ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=1810](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1810)) it installs and runs fine since 1.1.0 without any tweaks.

---

### Post by Shobuz99 on 2009-06-21
sorry.. stupid question: how do I "remove your prefix and install again."
Do you mean uninstall from 'add/remove'? 
Once I get latest Wine installed, should I go through the DWMX install from CD again?
Sorry for being so dense.

Rick (shobuz99)

---

### Post by NightMKoder on 2009-06-21
It's alright. Your wine prefix is where all your actual programs/registry are located (add/remove wine doesn't delete it). It is normally stored in your home directory with the name of .wine (which makes it hidden). To delete it, open a terminal and do:

rm -rf ~/.wine

---

### Post by Shobuz99 on 2009-06-21
NightMKoder

rm -rf ~/.wine

ok. Did that. Then I went to Synaptic pkg mgr and 'marked for removal' and removed the wine pkgs (kept wine-doors).. I expected the newer versions to show up, but they didn't. I've forgotten how to grab the new versions. 
I've been away from Ubuntu since Sept.08.. I just upgraded from Hardy 8.10 to Jaunty 9.04 yesterday. Again, sorry for being so dense.
I appreciate your help getting through these steps.
Rick (shobuz99)

---

### Post by Shobuz99 on 2009-06-21
> **Shobuz99 said:**
> NightMKoder

rm -rf ~/.wine

ok. Did that. Then I went to Synaptic pkg mgr and 'marked for removal' and removed the wine pkgs (kept wine-doors).. I expected the newer versions to show up, but they didn't. I've forgotten how to grab the new versions. 
I've been away from Ubuntu since Sept.08.. I just upgraded from Hardy 8.10 to Jaunty 9.04 yesterday. Again, sorry for being so dense.
I appreciate your help getting through these steps.
Rick (shobuz99)

*Update: I think I figured it out. I did some digging and was able to use the instructions from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb). Now all I have to do is get Dreamweaver to work. Unless I need to re-install DWMX from CD.. right?*

Thanks again for your help..
Rick (shobuz99)


[B]**Update 2**
Didn't work. Wine installed fine. Of course the Macromedia folder was removed with the old Wine ver, so I had to re-install Dreamweaver MX from CD. 
Tried it and it failed: error was the "corecomp.ini" failure. Entire error is:
"An installation support file '%systemDrive%\Program files\Common files\InstallShield\engine\6\Intel 32\corecomp.ini' could not be installed (0x8000ffff)"

I'm dead in the water, unless I can fool the install by copying the necessary folders and files (installshield, etc.) from Windows XP on my other system (dual boot). 
I don't think that will work. Any suggestions?

Thanks again for your help..
Rick (shobuz99[/B]

---

