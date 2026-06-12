---
title: "UMR Empathy contacts not shown in people tab"
date: 2009-12-13
forum: Ubuntu Moblin Remix
---

### Post by mozzwald on 2009-12-13
After a fresh install of Ubuntu Moblin Remix my empathy contacts are not showing under the "People" tab. At first boot up, I added my Google Talk account and the contacts were there, but at next boot up they were gone and have not come back since. I removed my account and re-added it which did nothing. I am unable to remove and reinstall empathy as the "ubuntu-moblin-remix" package depends on it. Any suggestions?

EDIT: So it seems if I delete my account from empathy, reboot and add the account again it works until I reboot.

---

### Post by jsaturno on 2009-12-19
Same problem here with a msn account.

---

### Post by mozzwald on 2009-12-20
It appears that during startup empathy is run after the moblin panel applications and then they will not connect to empathy if run in that order. I wrote a script that runs during startup which starts empathy and restarts the moblin-panel-people and moblin-panel-status. This is probably not a good or right way to fix the problem, but it works.

Place this code into a file in your home directory. (ie empathy-fix.sh) 
```
#!/bin/bash

# start Empathy then kill/restart moblin-panel-people and moblin-panel-status

empathy &
sleep 3 ; kill `pidof moblin-panel-people` ; kill `pidof moblin-panel-status`

exit
```

Open up a terminal and make the file executable.
```
chmod +x ~/empathy-fix.sh
```

I tried adding the script to the Startup Applications located in the Settings Menu. For some reason it would not run at startup when added there. I manually had to add it. 
```
sudo gedit /etc/xdg/autostart/empathy-fix.desktop
```

This is the code that will be placed in the file. Make sure that the "Exec" filename matches the filename you created above.
```

[Desktop Entry]
Type=Application
Exec=~/empathy-fix.sh
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=empathy-fix.desktop
Name=Empathy Startup Fix
Comment[en_US]=
Comment=
```

Reboot and the script will run and your contacts will appear under People.

---

