---
title: "RKHUNTER Query - Warnings"
date: 2012-02-06
forum: Security
---

### Post by Buckie_Bhoy on 2012-02-06
Hi All,
 
looking for some advice on the following entries in the rkhunter log after running it, am running 11.10, the only thing i've done recently is update and upgrade. Also used sudo apt-get dist-upgrade recently too, would this cause these issues, or something more sinister?
 
```

[FONT=Courier New][FONT=Courier New][FONT=Courier New][FONT=Courier New][21:59:30] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:30] File: /usr/bin/last[/FONT]
[FONT=Courier New][21:59:30] Current hash: 018cfae45a835d788d767027fce39aa2241184fe[/FONT]
[FONT=Courier New][21:59:30] Stored hash : 1b690fa0c9450449f3c9b27b26479de7e28939b3[/FONT]
[FONT=Courier New][21:59:30] Current inode: 131312 Stored inode: 131671[/FONT]
[FONT=Courier New][21:59:30] Current size: 18824 Stored size: 18816[/FONT]
[FONT=Courier New][21:59:30] Current file modification time: 1323931210 (15-Dec-2011 06:40:10)[/FONT]
[FONT=Courier New][21:59:30] Stored file modification time : 1310620264 (14-Jul-2011 06:11:04)[/FONT][/FONT]
 
 
[FONT=Courier New][FONT=Courier New][FONT=Courier New][FONT=Courier New][21:59:33] /usr/bin/size [ Warning ][/FONT]
[FONT=Courier New][21:59:33] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:33] File: /usr/bin/size[/FONT]
[FONT=Courier New][21:59:33] Current inode: 135473 Stored inode: 136488[/FONT]
[FONT=Courier New][21:59:33] Current file modification time: 1324658040 (23-Dec-2011 16:34:00)[/FONT]
[FONT=Courier New][21:59:33] Stored file modification time : 1319720971 (27-Oct-2011 14:09:31)[/FONT]
 
[/FONT][/FONT]
 
[FONT=Courier New][FONT=Courier New][21:59:33] /usr/bin/strings [ Warning ][/FONT]
[FONT=Courier New][21:59:33] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:33] File: /usr/bin/strings[/FONT]
[FONT=Courier New][21:59:33] Current inode: 135482 Stored inode: 136491[/FONT]
[FONT=Courier New][21:59:33] Current file modification time: 1324658040 (23-Dec-2011 16:34:00)[/FONT]
[FONT=Courier New][21:59:33] Stored file modification time : 1319720971 (27-Oct-2011 14:09:31)[/FONT]
 
[/FONT]
 
[FONT=Courier New][FONT=Courier New][21:59:35] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: a /usr/bin/ruby -w script text executable[/FONT]
 
[/FONT]
 
[FONT=Courier New][FONT=Courier New][21:59:36] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:36] File: /sbin/ifdown[/FONT]
[FONT=Courier New][21:59:36] Current hash: 05d07aa366cd368b0216bed59b7a392eff802ba8[/FONT]
[FONT=Courier New][21:59:36] Stored hash : cb26862c330e54da9e106d4ec83cb0ebc5358f35[/FONT]
[FONT=Courier New][21:59:36] Current inode: 131627 Stored inode: 130830[/FONT]
[FONT=Courier New][21:59:36] Current file modification time: 1327049674 (20-Jan-2012 08:54:34)[/FONT]
[FONT=Courier New][21:59:36] Stored file modification time : 1316028273 (14-Sep-2011 20:24:33)[/FONT]
 
[FONT=Courier New][21:59:37] /sbin/ifup [ Warning ][/FONT]
[FONT=Courier New][21:59:37] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:37] File: /sbin/ifup[/FONT]
[FONT=Courier New][21:59:37] Current hash: 05d07aa366cd368b0216bed59b7a392eff802ba8[/FONT]
[FONT=Courier New][21:59:37] Stored hash : cb26862c330e54da9e106d4ec83cb0ebc5358f35[/FONT]
[FONT=Courier New][21:59:37] Current inode: 131627 Stored inode: 130830[/FONT]
[FONT=Courier New][21:59:37] Current file modification time: 1327049674 (20-Jan-2012 08:54:34)[/FONT]
[FONT=Courier New][21:59:37] Stored file modification time : 1316028273 (14-Sep-2011 20:24:33)[/FONT]
 
[FONT=Courier New][FONT=Courier New][21:59:38] /sbin/sulogin [ Warning ][/FONT]
[FONT=Courier New][21:59:38] Warning: The file properties have changed:[/FONT]
[FONT=Courier New][21:59:38] File: /sbin/sulogin[/FONT]
[FONT=Courier New][21:59:38] Current hash: 30a2dd9a31b34d399192b4c97b9251613deb87cc[/FONT]
[FONT=Courier New][21:59:38] Stored hash : 2dffbead0e88b8ca1c81158cca931da1caa2bcb6[/FONT]
[FONT=Courier New][21:59:38] Current inode: 130837 Stored inode: 131172[/FONT]
[FONT=Courier New][21:59:38] Current file modification time: 1323931210 (15-Dec-2011 06:40:10)[/FONT]
[FONT=Courier New][21:59:38] Stored file modification time : 1310620264 (14-Jul-2011 06:11:04)[/FONT]
 
[/FONT][/FONT][/FONT][/FONT][/FONT]
```[FONT=Courier New]
 
[/FONT]

---

### Post by Buckie_Bhoy on 2012-02-06
OK, found the following link [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656437](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=656437) after posting message :p
 
As suggested I ran sudo rkhunter --propupd then ran rkhunter again, and only warning I am now left with is
 
[FONT=Courier New]```
 
[FONT=Courier New][21:59:35] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: a /usr/bin/ruby -w script text executable
[/FONT]

```[/FONT]

---

### Post by Dangertux on 2012-02-06
I would not say that these are indication of a compromise based on the fact that you did a distro upgrade. In the future make sure you know that doing propupd with rkhunter resets the baseline to your current file set and will override any warnings given. 

Hope this helps.

---

### Post by Buckie_Bhoy on 2012-02-06
Many thanks for the info DangerTux 
 
For anyone else reading, I also found the following via Google
 
As for your warning, rkhunter simply informs you the unhide.rb executable
located in /usr/bin/ is a ruby script. It is perfectly normal in that case
and you can whitelist it in rkhunter.conf{,.local}.

---

