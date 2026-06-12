---
title: "RKHunter Warnings - Warning: The following processes are using deleted files:"
date: 2014-05-09
forum: Security
---

### Post by florence2 on 2014-05-09
Hi I am new to RKHunter but have just run it and I cannot understand the following warnings.

[11:22:07] Info: Starting test name 'deleted_files' 
[11:22:11]   Checking running processes for deleted files    [ Warning ] 
[11:22:12] Warning: The following processes are using deleted files: 
[11:22:12]          Process: /lib/systemd/systemd-logind    PID: 622    File: /lib/systemd/systemd-logind 
[11:22:12]          Process: /usr/sbin/lightdm    PID: 1287    File: /usr/sbin/lightdm 
[11:22:12]          Process: /usr/sbin/lightdm    PID: 1391    File: /usr/sbin/lightdm 
[11:22:12]          Process: /usr/bin/ssh-agent    PID: 1561    File: /usr/bin/ssh-agent 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon    PID: 1639    File: /home/florence1/.local/share/gvfs-metadata/root 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/indicator-datetime-service.dpkg-new    PID: 1829    File: /usr/lib/x86_64-linux-gnu/indicator-datetime-service.dpkg-new 
[11:22:12]          Process: /usr/bin/nautilus    PID: 2141    File: /home/florence1/.local/share/gvfs-metadata/home 
[11:22:12]          Process: /usr/bin/python2.7    PID: 2145    File: /usr/bin/python2.7 
[11:22:12]          Process: /usr/bin/python2.7    PID: 2365    File: /usr/bin/python2.7 
[11:22:12]          Process: /usr/lib/libunity-webapps/unity-webapps-service    PID: 2609    File: /usr/lib/libunity-webapps/unity-webapps-service 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor    PID: 2710    File: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor 
[11:22:12]          Process: /usr/lib/firefox/firefox    PID: 3486    File: /var/tmp/etilqs_JijylJyh26OzKIh 
[11:22:12]          Process: /usr/bin/python3.3    PID: 3663    File: /usr/bin/python3.3 
[11:22:12]          Process: /usr/bin/unity-scope-loader    PID: 4019    File: /home/florence1/.cache/software-center/software-center-agent.db/record.DB 
[11:22:12]          Process: /usr/bin/gnome-terminal    PID: 5027    File: /tmp/vte0B4EFX 
[11:22:12]          Process: /usr/sbin/cups-browsed    PID: 16970    File: /etc/passwd 

Thank you for any help. It just concerns me when I see mentions of my password.

Edit - I have also just noticed even though I am florence1 - this forum shows me as florence2 - would that just be because there is another user with that name?

---

### Post by ant2ne on 2014-05-09
That is odd. I'm not using cups so I don't know if it is normal behavior. Try disabling cups and re-running rkhunter. Also do an ls -l /etc/passwd and see when the last time the file was changed.

---

### Post by florence2 on 2014-05-09
Thanks ant2ne

I have done that and now have:

Info: Starting test name 'deleted_files' 
[16:52:12]   Checking running processes for deleted files    [ Warning ] 
[16:52:12] Warning: The following processes are using deleted files: 
[16:52:12]          Process: /usr/lib/cups/filter/gstoraster    PID: 1323    File: /tmp/0052b53720f4e 
[16:52:12]          Process: /usr/bin/gs    PID: 1329    File: /tmp/0052b53720f4e 
[16:52:12]          Process: /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon    PID: 1622    File: /home/florence1/.local/share/gvfs-metadata/root 
[16:52:12]          Process: /usr/bin/nautilus    PID: 2101    File: /home/florence1/.local/share/gvfs-metadata/home 
[16:52:12]          Process: /usr/bin/unity-scope-loader    PID: 4131    File: /home/florence1/.cache/software-center/software-center-agent.db/record.DB 
[16:52:12]          Process: /usr/lib/firefox/firefox    PID: 6008    File: /dev/pts/0 
[16:52:12]          Process: /usr/lib/firefox/plugin-container    PID: 6162    File: /dev/pts/0 
[16:52:12]          Process: /usr/bin/gnome-terminal    PID: 8988    File: /tmp/vte6D7MFX

I used ls -l /etc/passwd and it says the file was changed May  9 12:48 /etc/passwd


I'm not sure what that means though!

Any further thoughts?

---

### Post by Habitual on 2014-05-09
last modified date of /etc/passwd:
```
stat -c%y /etc/passwd
```

---

### Post by florence2 on 2014-05-09
I didn't actually change my password at May  9 12:48 - I am wondering what this may mean. I changed my password at later at about 4:00pm - I am rather confused!

---

### Post by sandyd on 2014-05-09
> **florence2 said:**
> Hi I am new to RKHunter but have just run it and I cannot understand the following warnings.

[11:22:07] Info: Starting test name 'deleted_files' 
[11:22:11]   Checking running processes for deleted files    [ Warning ] 
[11:22:12] Warning: The following processes are using deleted files: 
[11:22:12]          Process: /lib/systemd/systemd-logind    PID: 622    File: /lib/systemd/systemd-logind 
[11:22:12]          Process: /usr/sbin/lightdm    PID: 1287    File: /usr/sbin/lightdm 
[11:22:12]          Process: /usr/sbin/lightdm    PID: 1391    File: /usr/sbin/lightdm 
[11:22:12]          Process: /usr/bin/ssh-agent    PID: 1561    File: /usr/bin/ssh-agent 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon    PID: 1639    File: /home/florence1/.local/share/gvfs-metadata/root 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/indicator-datetime-service.dpkg-new    PID: 1829    File: /usr/lib/x86_64-linux-gnu/indicator-datetime-service.dpkg-new 
[11:22:12]          Process: /usr/bin/nautilus    PID: 2141    File: /home/florence1/.local/share/gvfs-metadata/home 
[11:22:12]          Process: /usr/bin/python2.7    PID: 2145    File: /usr/bin/python2.7 
[11:22:12]          Process: /usr/bin/python2.7    PID: 2365    File: /usr/bin/python2.7 
[11:22:12]          Process: /usr/lib/libunity-webapps/unity-webapps-service    PID: 2609    File: /usr/lib/libunity-webapps/unity-webapps-service 
[11:22:12]          Process: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor    PID: 2710    File: /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor 
[11:22:12]          Process: /usr/lib/firefox/firefox    PID: 3486    File: /var/tmp/etilqs_JijylJyh26OzKIh 
[11:22:12]          Process: /usr/bin/python3.3    PID: 3663    File: /usr/bin/python3.3 
[11:22:12]          Process: /usr/bin/unity-scope-loader    PID: 4019    File: /home/florence1/.cache/software-center/software-center-agent.db/record.DB 
[11:22:12]          Process: /usr/bin/gnome-terminal    PID: 5027    File: /tmp/vte0B4EFX 
[11:22:12]          Process: /usr/sbin/cups-browsed    PID: 16970    File: /etc/passwd 

Thank you for any help. It just concerns me when I see mentions of my password.

Edit - I have also just noticed even though I am florence1 - this forum shows me as florence2 - would that just be because there is another user with that name?

There is no florence1 user. If you have had an account (other than this one) here before, see [http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)
Otherwise, see [http://ubuntuforums.org/showthread.php?t=1178721](http://ubuntuforums.org/showthread.php?t=1178721)

---

### Post by jensmaucher on 2014-05-11
Out of sheer curiosity... do run the test on a server or on a desktop?

---

### Post by bashiergui on 2014-05-12
```
[11:22:12] Process: /usr/sbin/cups-browsed PID: 16970 File: /etc/passwd 
```cups-browsed is a daemon that would have a user account associated with it, just as all daemons do. So this entry is telling you that the cups-browsed program modified or created an account, probably its own. This would be expected if you just installed or updated cups-browsed or changed permissions for using/installing a printer. 


You can easily confirm this by looking at the /etc/passwd file for the cups-browsed user. 


Or did you maybe print something using cups-browsed and you had to enter the root password.

---

