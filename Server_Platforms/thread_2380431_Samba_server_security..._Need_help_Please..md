---
title: "Samba server security... Need help Please."
date: 2017-12-17
forum: Server Platforms
---

### Post by l1t7l3ph0o7 on 2017-12-17
I have a fresh install of Ubuntu 16.0.4 server LTS and I'm trying to configure security in samba, but I am having much difficulty getting it to work correctly.
I installed SAMBA during the installation of the OS as well as LAMP

I am trying to access my shares from a windows 10 client (I don't have anything else to use).

I Followed this guide and created a share that I can access WITHOUT authentication:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

everything works until I want to add authentication into the mix, I continued onto this section of the guide:
[https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/lts/serverguide/samba-fileprint-security.html)

Here is where I run into problems, I edit /etc/samba/smb.conf

I changed my share section from this:
[testshare]
        comment = test
        path = /home/backend/share
        browseable = yes
        guest ok = yes
        read only = no
        create mask = 0755

to this:
[testshare]
        comment = test
        path = /home/backend/share
        browseable = yes
        security = user
        guest ok = no
        read only = no
        create mask = 0755

Then restart samba, Then from my windows 10 client I can browse to the server. 
I get a list of all the shares, and when I click on one, a box pops up asking for username and password. (Great, I want this to happen)
The problem is, I type in the username and password for my account on my Ubuntu server, and I get "Access is Denied" 

I then read somewhere about needing to create a separate samba password to access samba with so I entered this command:
sudo smbpasswd -a <user> 
and created a password for the same user I'm trying to use.

But I still get "Access is denied" when trying to access the share, I have tried my user account password as well as my samba password, and I've tried setting my samba password the same as my account password, but I get the same result every time.

I'm at a loss here, I don't think the permissions on the directory are the problem because I can access the share when I change: 
guest ok = yes 

I'm fairly new to this so I'm sure I'm missing something simple, but I'm a bit frustrated as I've been working this for a few days now and this just shouldn't be that hard.

I am willing to post any logs or configurations, just tell me where to find them as I don't already know.
 
Any and all help for this will be very much appreciated.

---

### Post by howefield on 2017-12-17
Thread moved to the "*Server Platforms*" forum.

---

### Post by Morbius1 on 2017-12-17
Two questions:

[1] What are the permissions of the target folder:
```
ls -al /home/backend/share
```
[2] Is "backend" an actual Linux user name or is it just a folder that happens to be in the /home directory?

[COLOR=#0000cd][I]BTW, those two HowTo's you referenced really should be removed. THe first one will break the instant you create a share requiring authentication. The second one is both way over-engineered and factually incorrect:
> security = share: allows clients to connect to shares without supplying a username and            password. 
Nope. "security = share" will actally disable samba from running since it's no longer a legitimate option.[/I][/COLOR]

---

### Post by l1t7l3ph0o7 on 2017-12-17
[COLOR=#000000][FONT=&quot]1. ls -al /home/backend/share[/FONT][/COLOR]:

> backend@UBIserver:~$ ls -al /home/backend/share
total 8
drwxrwxr-x 2 nobody  nogroup 4096 Dec 17 10:44 .
drwxr-xr-x 5 backend backend 4096 Dec 17 13:20 ..

2. Yes the username is backend

---

### Post by Morbius1 on 2017-12-17
Change this:
> [testshare]
        comment = test
        path = /home/backend/share
        browseable = yes
        security = user
        guest ok = no
        read only = no
        create mask = 0755 
To this:
> [testshare]
        comment = test
        path = /home/backend/share
        browseable = yes
guest ok = no
        read only = no
        force user = nobody
[COLOR=#0000cd][I]Note: you don't need to add "security = user" since the defaults ( which is not in smb.conf ) already handles it - and you wouldn't add it to the share definition anyway - it's a [global] parameter.

[/I][/COLOR][COLOR=#000000]Now restart smbd:
```
sudo service smbd restart
```

Can your Win10 client now write to the share. If not we need to dig deeper.
[/COLOR]

---

### Post by l1t7l3ph0o7 on 2017-12-17
I made the changes but unfortunately it seems to have no effect

---

### Post by Morbius1 on 2017-12-17
Does your user name show up when you run this command:
```
sudo pdbedit -L
```

Is your home directory by any chance encrypted?

If it is either move your shared folder outside of /home entirely or:

Change ownership of the folder to you:
```
sudo chown backend:backend /home/backend/share
```
And change you share definition to force the user to you:
> [testshare]
comment = test
path = /home/backend/share
browseable = yes
guest ok = no
read only = no
[COLOR=#0000cd]**force user = backend**[/COLOR] 


If that desn't work either I need to see the whole smb.conf:
```
testparm -s
```

---

### Post by l1t7l3ph0o7 on 2017-12-17
I ran [COLOR=#000000][FONT=&quot]sudo pdbedit -L
It does show my username there.

My home directory is not encrypted

I changed ownership and changed force user to backend, as you suggested, but I'm still unable to access the share.
here is the output from testparm -s:
[/FONT][/COLOR]> backend@UBIserver:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[testshare]"
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
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
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb




[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[testshare]
        comment = test
        path = /home/backend/share
        force user = backend
        read only = No


[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by l1t7l3ph0o7 on 2017-12-17
Just noticed something...
I have a static ip set, if i switch it back to dhcp, I can access the share. what gives?

---

### Post by Morbius1 on 2017-12-17
Noting wrong with any of that. I noticed on the second HowTo reference to apparmour which I never mess with. Did you do anything with that?

EDIT: Didn't see your last post ... um ... maybe you have another machine that has your static ip address supplied by DHCP?

---

### Post by l1t7l3ph0o7 on 2017-12-17
I did nothing with apparmour.

the address Can't be assigned from dhcp to any other client, my pool assigns between 100-200, but I have added a static assignment for the time being so that I get the correct address on the machine.

---

### Post by l1t7l3ph0o7 on 2017-12-17
it can't be another machine by dhcp because the address is outside the pool, but I did have a machine with that address (no longer online).

Actually after rebooting my client and the router on the network seemed to do the trick.  Thank you for all your help.

---

