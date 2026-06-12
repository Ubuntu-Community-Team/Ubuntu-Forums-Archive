---
title: "Don't have permission to run X server?"
date: 2009-04-07
forum: Wine
---

### Post by mrblondeisback on 2009-04-07
So I'm trying to run WoW in it's own X, because I keep hearing that it improves performance.  I set up this script to do it:
```
#!/bin/sh
 
X :3 -ac & nvidia-settings --load-config-only  # Launches a new X session on display 3 
 cd "/home/zaphodb2002/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 WINEDEBUG=-all wine "C\:Program Files\World of Warcraft\wow.exe" -opengl # Launches WoW
```

But whenever I run it it tells me I don't have permission to run X.  How can I give myself the appropriate permission?

---

### Post by mrblondeisback on 2009-04-07
I also tried running the script with a sudo, it opens a new x, but not WoW.  Any help would be appreciated.

---

### Post by krakk2k on 2009-04-07
ok a few things what:~

version of ubuntu?

version of wine?

graphics card?

driver number?
(for nvidia cards type "nvidia-settings" into terminal, wait for the control panel to come up and look under "System Information" for NVIDIA Driver Version: xxx.xx)

(for ati type "amd:cccle or amdcccle" and click "Information", then look at the right hand side at the second section titled "Software" and then "Driver Version". You should see something like 8.39.4)

---

### Post by cogadh on 2009-04-07
You need to modify the /etc/X11/Xwrapper.config file. Open it with a text editor, look for an entry that says &#8220;allowed_users=console&#8221; and change it to &#8220;allowed_users=anybody&#8221;. After that, you should be able to run the script normally, without using sudo.

---

