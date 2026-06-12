---
title: "samba file server username problem with '\'"
date: 2011-01-23
forum: Server Platforms
---

### Post by mistafeesh on 2011-01-23
Hi,

I currently have to connect to my new samba fileserver using servername\username instead of just username, if that makes sense(!)

I need this to be simplified, as I've had it before on a previous machine, as one of the devices I connect with has a virtual keyboard without a backslash!

Is there a setting for this anywhere? I'm sure I've seen it somewhere before but I've not been able to find it with google!

Thanks,
Dan

---

### Post by CharlesA on 2011-01-23
What OS are you connecting from?

---

### Post by mistafeesh on 2011-01-24
It's mostly for the benefit of wii media centre (running on wii homebrew channel) but I will very occasionally need to connect from a windows 7 machine and also occasional design clients come around with their windows laptops. I've mostly been testing it from my mac and ubuntu laptop as these are the computers I use regularly.

---

### Post by CharlesA on 2011-01-24
If Samba is set up correctly, it shouldn't be asking you to put in the server name before the username unless you have funky set up with LDAP or something like that.

Does it work if you just put the username in?

---

### Post by mistafeesh on 2011-01-24
oh dear, I think today is one of those days... Up until today, I couldn't log in with just the username - I had to enter it in that format. Now I don't seem to be able to connect at all... I installed webmin, so I don't know if that's affected it... running testparm -sp seems to come up with exactly the same settings as before...

I don't even know what LDAP is, so I don't think I've got it running. The servers I have running are:
apache2 with php
mysql
samba
netatalk

I also installed dansguardian with the idea of using it as a proxy server (I work from home and was thinking of  using this to stop my teenagers looking at stupid stuff on the web) but have not set it up yet... could this be causing problems?

your post made me think of starting from scratch with a  default smb.conf, so I'm going to try that, but I'm pretty sure that all I did was add a couple of shares...

if I don't have any joy with that I'll post up the output from testparm -sp

EDIT - I also seem to have BIND and a DHCP server installed. Is this normal? I imagine either of these could be causing my problems...

---

### Post by CharlesA on 2011-01-24
Can you post the output of this:

```
testparm -s /etc/samba/smb.conf
```

---

### Post by mistafeesh on 2011-01-24
Here it is. I've just now overwritten my customised smb.conf with the default one, added my shares on to the bottom and restarted samba, but the situation is still the same...
 
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[www]"
Processing section "[work]"
Processing section "[stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        server string = %h server (Samba, Ubuntu)
        encrypt passwords = No
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[www]
        comment = web server root
        path = /var/www
        read only = No
        guest ok = Yes

[work]
        path = /home/dan/Documents
        read only = No
        guest ok = Yes

[stuff]
        path = /media/STUFF
        read only = No
        guest ok = Yes
```

---

### Post by CharlesA on 2011-01-24
Make sure smbd and nmbd are running:

```
service smbd status
service nmbd status
```

---

### Post by kevinthecomputerguy on 2011-01-24
Make sure your windows 7 box is in the workgroup named "workgroup" (reboot if changing)
 
Then add these lines of code to your smb.conf
 
netbios name = server1
workgroup = workgroup
 
*where netbios name is the name of the samba server.
 
reboot, and try again from Win 7 box

---

### Post by mistafeesh on 2011-01-25
right this doesn't seem right - > dan@ubuntuserver:~$ service smbd status
smbd stop/waiting
dan@ubuntuserver:~$ service nmbd status
nmbd start/running, process 2304

I tried smdb start as I imagine it should be running(?)
and got this> dan@ubuntuserver:~$ service smbd start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.47" (uid=1000 pid=3066 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))


---

### Post by kevinthecomputerguy on 2011-01-25
Have you tried typing "sudo" first, before each command?

and or

Have you tried rebooting the server instead of restarting of the service.

---

### Post by mistafeesh on 2011-01-26
Hi,

the workgroup was already WORKGROUP and I set the netbios name to the same name as the server. Haven't tried connecting the windows 7 yet, as it's being used by someone else, but the main clients I need to connect are variants on the samba client, I think. One is ubuntu10.10 until I get ssh working, which is another issue entirely(and in another thread of its own...) The other client is a wii homebrew which accesses SMB shares. I imagine that is also based on samba.

---

### Post by mistafeesh on 2011-01-29
sorry only just say kevins post. Yeah I sudo'd too, and I've shutdown and started up the computer numerous times since these problems started. Currently I can't connect to the samba server at all from any computer, so I've obviously broken it by fiddling around so much. I'm going to have to try and figure out which backed up config file was the one that almost worked!

---

### Post by CharlesA on 2011-01-29
Are you able to run something like nmap against the machine to make sure port 445 and 139 are open?

---

### Post by mistafeesh on 2011-02-03
nmap says that those two ports are open. I've found  that there are problems with the wifi dongle I'm using on my server. I'm going to try moving the server so I can plug it into the router with an ethernet cable... I'm also moving house rather suddenly, so I may need to come back to this after the big move. I'll just use sneakernet to use the files on my wii !

---

### Post by CharlesA on 2011-02-03
It could be the wireless is messing with it, but I'm not sure.

Hopefully it'll 'just work' after you connect it with a regular ethernet cable instead of wireless.

---

### Post by mistafeesh on 2011-02-08
yup, it does! no problems with samba as soon as it's plugged in properly! Still got something weird going on with ssh but that's in another thread....

EDIT - thanks everyone!

---

