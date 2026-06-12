---
title: "after 18.04 upgrade smbd won't start"
date: 2018-07-28
forum: Server Platforms
---

### Post by PeterK2003 on 2018-07-28
Getting this error when trying to start smbd:

Jul 28 09:14:16 King-Arthur systemd[1]: Starting Samba NMB Daemon...
Jul 28 09:14:16 King-Arthur systemd[1]: nmbd.service: Main process exited, code=exited, status=1/FAILURE
Jul 28 09:14:16 King-Arthur systemd[1]: nmbd.service: Failed with result 'exit-code'.
Jul 28 09:14:16 King-Arthur systemd[1]: Failed to start Samba NMB Daemon.
Jul 28 09:14:16 King-Arthur systemd[1]: Starting Samba NMB Daemon...
Jul 28 09:14:17 King-Arthur systemd[1]: nmbd.service: Main process exited, code=exited, status=1/FAILURE
Jul 28 09:14:17 King-Arthur systemd[1]: nmbd.service: Failed with result 'exit-code'.
Jul 28 09:14:17 King-Arthur systemd[1]: Failed to start Samba NMB Daemon.
Jul 28 09:14:28 King-Arthur systemd[1]: Starting Samba SMB Daemon...
Jul 28 09:14:28 King-Arthur systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Jul 28 09:14:28 King-Arthur systemd[1]: smbd.service: Failed with result 'exit-code'.
Jul 28 09:14:28 King-Arthur systemd[1]: Failed to start Samba SMB Daemon.
Jul 28 09:14:29 King-Arthur systemd[1]: Starting Samba SMB Daemon...
Jul 28 09:14:29 King-Arthur systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Jul 28 09:14:29 King-Arthur systemd[1]: smbd.service: Failed with result 'exit-code'.
Jul 28 09:14:29 King-Arthur systemd[1]: Failed to start Samba SMB Daemon.


My googling hasn't got me anywhere....
The message is pretty generic where can I get some better info about what the issue is?

Thanks in advance,
Peter

---

### Post by darkod on 2018-07-28
How about 'sudo systemctl status smbd'? Does that give you more info?
Or the samba logs?

---

### Post by PeterK2003 on 2018-07-28
I don't think that is any more helpful:

&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2018-07-28 09:14:29 EDT; 2h 34min ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 2195 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 2195 (code=exited, status=1/FAILURE)

Jul 28 09:14:29 King-Arthur.xxx.name systemd[1]: Starting Samba SMB Daemon...
Jul 28 09:14:29 King-Arthur.xxx.name systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Jul 28 09:14:29 King-Arthur.xxx.name systemd[1]: smbd.service: Failed with result 'exit-code'.
Jul 28 09:14:29 King-Arthur.xxx.name systemd[1]: Failed to start Samba SMB Daemon.

---

### Post by Morbius1 on 2018-07-28
It is fairly easy to reproduce that output from sudo systemctl status smbd however.

Run this command:
```
testparm -s
```
Do you get this as the output:
```
WARNING: Ignoring invalid value 'share' for parameter 'security'
Error loading services.

```
If you do, edit /etc/samba/smb.conf, find the line [COLOR=#0000cd]**security = share, **[/COLOR][COLOR=#000000]and either delete it or change it to[/COLOR][COLOR=#0000cd][B] security = user.

[/B][/COLOR][COLOR=#000000]Save the file then restart smbd.[/COLOR]

---

### Post by #&amp;thj^% on 2018-07-28
This has worked for me, this was on upgrade to 17.10:
```

sudo systemctl disable nmbd
sudo systemctl disable smbd
sudo systemctl unmask samba-ad-dc
sudo systemctl enable samba-ad-dc 
```
Also check your permissions on:
```
cd /var/lib/samba/private && ls -la
```
I had noticed that somehow they changed on mine from 755 to 700.and should be @ 755
**EDIT Never mind Morbius1 has the right solution. :)**

---

### Post by PeterK2003 on 2018-07-28
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "announce version"
Ignoring unknown parameter "announce version"
WARNING: The "null passwords" option is deprecated
handle_name_resolve_order: WARNING: Ignoring invalid list value 'hosts' for parameter 'name resolve order'
Error loading services.


So hosts got changed to host?

Also is there any issues connecting from an XP machine to the new version of Samba?

---

### Post by Morbius1 on 2018-07-28
Um .... there's 2 ways we can go from here:

[1] Post the entire contents of /etc/samba/smb.conf and we can go line by line and update / correct it.

[2] Reset yourself to the new default:

Make a copy of the one you have:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.orig
```
Copy the default that is present on you system for times like this:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
Before making changes to it for things like name resolve order, etc run this command again and make sure it's clean:
```
testparm -s
```

---

### Post by PeterK2003 on 2018-07-28
Well lets start with my file:

Thanks again. 

And it is working from Win7 and not from my XP machine....yeah I know i need to upgrade it.

> 
[global]
    ; General server settings
    netbios name = king-arthur
    server string =
    workgroup = xxx
    ;announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    ;null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = host wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes
    follow symlinks = yes
    wide links = yes
    unix extensions = no

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.


[ftp]
    path = /var/ftp/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ftpuser
    force group = ftpuser


---

### Post by Morbius1 on 2018-07-28
Samba doesn't recommend you do the "socket options" thing any longer. Keep it in for now and if there are any issues remove it.

Looks like you fixed the name resolve order problem.

The WinXP client is a problem. I realize that even today there are more WinXP users than Desktop Linux users but Samba has moved on. I'm going to guess that if you add the following to the [global] section it will bring your server to the security level it was back then: 
```
lanman auth = yes
ntlm auth = yes
```
Restart smbd and pray.

---

### Post by #&amp;thj^% on 2018-07-28
> **Morbius1 said:**
> Samba doesn't recommend you do the "socket options" thing any longer. Keep it in for now and if there are any issues remove it.

Looks like you fixed the name resolve order problem.

The WinXP client is a problem. I realize that even today there are more WinXP users than Desktop Linux users but Samba has moved on. I'm going to guess that if you add the following to the [global] section it will bring your server to the security level it was back then: 
```
lanman auth = yes
ntlm auth = yes
```
Restart smbd and pray.

+1
to make Windows XP able to connect to my Samba server I had to add:
```

server max protocol = NT1
lanman auth = yes
ntlm auth = yes
```
and without these lines Android 7 wasn't able to access the share neither.

---

### Post by Morbius1 on 2018-07-28
The only problem with this is Win10:
> server max protocol = NT1
Win10 disables SMB1 ( aka NT1 ) on the client side ( as well as the server side ) so it will not be able to connect to the server - unless you disable WIn10 from updating. It would be nice if it worked without that line.

---

### Post by #&amp;thj^% on 2018-07-28
> **Morbius1 said:**
> The only problem with this is Win10:

Win10 disables SMB1 ( aka NT1 ) on the client side ( as well as the server side ) so it will not be able to connect to the server - unless you disable WIn10 from updating. It would be nice if it worked without that line.

That shows you how long ago "I" used windows of any version. (I dated Myself :D)

---

### Post by PeterK2003 on 2018-07-29
That fixed it.  Thanks all!

and yeah I need to redo my XP desktop as something newer...Its on the list!

---

