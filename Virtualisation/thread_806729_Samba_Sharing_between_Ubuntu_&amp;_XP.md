---
title: "Samba Sharing between Ubuntu &amp; XP"
date: 2008-05-25
forum: Virtualisation
---

### Post by Kiri on 2008-05-25
Hey, I'm wondering if someone could tell me how I go about setting up samba sharing of hard disks so I can use them in my Ubuntu (host) and windows XP (guest) at the same time?

I already have XP running as a guest using virtualbox 1.6.0 on ubuntu 8.04 host. But have no idea about using samba sharing as I have never done so.

Using the inbuilt sharing feature in virtualbox works, but seems to be really slow in accessing the disks... so I want to try the samba way

---

### Post by diablo75 on 2008-05-25
Check this out:  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by fbroce on 2008-05-25
I will make it real easy for you. Here is a smb.conf file (/etc/samba/smb.conf) that will work. Make sure you chmod 777 your shares folders and change the printer names to your actual printers if you want to have samba printers available for windows. Change the local IP addresses as necessary (make sure the interfaces IP is your IP on the linux box). The paths for your samba drives should be the actual location for your shared folders. Fix the file for your setup, restart samba. In XP, go to my computer and add shared folder on your local drive. You should see the samba share easily. If not, add your local IP to your windows host file (I think it's in windos/system/etc..search for it.

smb.conf

# Global parameters
[global]
        workgroup = YOUR WORKGROUP NAME ON YOUR XP BOX
        server string = Your host name for your linux box
        interfaces = 192.168.0.48 127.0.0.1/24
        bind interfaces only = Yes
        security = SHARE
        smb ports = 139
        password server = None
        log file = /var/log/samba/log.%m
        max log size = 50
        os level = 65
        dns proxy = No
        wins support = Yes
        comment = share
        read only = No
        guest ok = Yes
        hide dot files = No
        hosts allow = 192.168.0.
[ipc$]
        path = /tmp
        guest ok = Yes
        valid users =
        hosts allow = 127.0.0.1/24, 192.168.0.0/24
[public]

        comment = Public
        path = /usr2
        create mask = 0660
        directory mask = 0777

[data]
        comment = Data
        path = /usr/sambadata
        create mask = 0660
        directory mask = 0777

[dj895]
        path = /tmp
        printable = Yes

[okilj]
        path = /tmp
        printable = Yes

---

### Post by Ocxic on 2008-05-26
try GSAMBAD from the repos

---

### Post by Kiri on 2008-05-26
Thanks for all the replies guys. I'm reading through the links you posted and getting somewhat overwhelmed.. I didn't realize this would be so complicated :(

---

