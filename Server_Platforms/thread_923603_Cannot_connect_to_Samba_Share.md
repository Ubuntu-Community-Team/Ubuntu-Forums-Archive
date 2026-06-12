---
title: "Cannot connect to Samba Share"
date: 2008-09-18
forum: Server Platforms
---

### Post by vegas588 on 2008-09-18
Trying to connect to Samba share from XP workstation.

jamesc@UbuntuServer1:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        comment = Home Directories
        invalid users = root
        valid users = %S
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes
jamesc@UbuntuServer1:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ]
 * Starting Samba daemons                                                [ OK ]
jamesc@UbuntuServer1:~$


I have set these basic options:
security = user
username map = /etc/samba/smbusers
comment = Home Directories
browseable = yes
read only = no


I am simply typing in from my XP machine \\ipaddress\username

What additional steps can I take to resolve this?

---

### Post by jamesrfla on 2008-09-18
You need to go to Start>My network places. Then view workgroup computers and you should see if your Ubuntu computer is in the same workgroup.

---

### Post by vegas588 on 2008-09-18
I am in a Domain. So, no I do not see it in My Network Places.

---

### Post by vegas588 on 2008-09-18
How can I verify that the share even exists on the Ubuntu server? I have not mounted anything, so do I need to do that first? Also, what about enabling a rule on the Ubuntu server to allow connections from my subnet? 

Thanks.

---

### Post by jamesrfla on 2008-09-18
Try mapping it. Right click my computer and select map network drive. Click browse and then select the workgroup instead of the domain. Also try smb://workgroup/ in firefox.

---

### Post by cariboo on 2008-09-18
Your testparm output doesn't show any shared directories. You will have to include a directory to share in your smb.conf. Have a look at this document, it runs through setting up a small network to a large one:

[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf)

Jim

---

### Post by kamaji792 on 2008-09-19
> **vegas588 said:**
> I am simply typing in from my XP machine \\ipaddress\username


I have a public share Called **Data** on Server called **Jim**.

To see the share I use **\\Jim\Data**

In a command shell (cmd) on winXP **dir \\Jim\Data** works.

Hope this might help.

---

### Post by vegas588 on 2008-09-19
After some additional reading and playing around, I actually got it working on a basic level. I can connect to the Ubuntu machine via my xp workstation by entering in  \\ip_address\share. Below is my current config. I still don't know if I have correctly set up a "samba share" though. What I really want to do is set up a share under a directory that I already have called /data1. Based on what I have read, it looks like I need to add a line under the [homes] section path = /data1/sharename

Can anyone confirm this?

jamesc@UbuntuServer1:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = MYDOMAINNAME.COM
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        hosts allow = 192.168.110.0/24

[homes]
        comment = Home Directories
        valid users = %S
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
jamesc@UbuntuServer1:~$

---

### Post by Aeonsies on 2008-09-19
I believe that's correct.

You should have an entry at the end of your smb file that looks something like this:

[name of your shared directory on server]
     path = /path to the folder (usually in the /media directory)
     browseable = yes
     read only = no
     guest ok = no
     create mask = 0644
     directory mask = 0755
     force user = user account name you have on the server

Hope that helps.

---

