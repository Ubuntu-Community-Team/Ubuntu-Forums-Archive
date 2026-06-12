---
title: "Applications and PAM"
date: 2006-09-27
forum: Server Platforms
---

### Post by Sge on 2006-09-27
I'm trying to get Wifi-Radar to run with root permissions when I log on. I have tired to follow these instructions:

 3. put wifi-radar.py in /usr/local/bin
        4. ln -s /usr/bin/consolehelper /usr/local/bin/wifi-radar **this returns symbolic link <paths>: file exists***
        5. vi /etc/security/console.apps/wifi-radar **the console.apps directory didnt exist so i created it***
                USER=root
                PROGRAM=/usr/local/bin/wifi-radar.py
                SESSION=true
        6. vi /etc/pam.d/wifi-radar **Created this file as well**
                #%PAM-1.0
                auth       sufficient   pam_rootok.so
                auth       sufficient   pam_timestamp.so
                auth       required     pam_stack.so service=system-auth
                session    required     pam_permit.so
                session    optional     pam_xauth.so
                session    optional     pam_timestamp.so
                account    required     pam_permit.so
        7. check the permissions
                # ls -lh /etc/security/console.apps/wifi-radar /etc/pam.d/wifi-radar
                -rw-r--r--  1 root root  /etc/pam.d/wifi-radar
                -rw-r--r--  1 root root  /etc/security/console.apps/wifi-radar
        8. add launcher
                a. right click on panel
                b. select 'add to panel'
                c. click on 'custom application launcher'
                d. options for 'create launcher'
                name : wifi-radar
                command : /usr/local/bin/wifi-radar
                icon : /usr/share/pixmap/wifi-radar.svg
        9. click on the icon, enter the root password, away you go

I don't get prompted for a root password and wifi-radar just hangs whne it tries to run the dhcp client and doesnt have sufficient permissions. If anyone could point me in the right direction of how to let an app run as root or sudo I'd appreciate it. Having to run sudo everytime i want to use wifi-radar is getting to be annoying.

---

### Post by dannyboy79 on 2006-10-03
dude, all you have to do is open up alacarte menu editor. then find your wifi-radar application, then modify the properties, where it lists the command, simply put gksudo in front of it.
so if it was /usr/bin/wifi-radar before 
then you would make it /usr/bin/gksudo wifi-radar and it'll run as sudo but you will have to enter your sudo password though.

---

