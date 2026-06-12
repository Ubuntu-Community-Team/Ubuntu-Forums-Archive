---
title: "Samba share not visible from Windows 7 PC, even though UNC authentication works"
date: 2013-12-21
forum: Server Platforms
---

### Post by JordanRieger on 2013-12-21
I'm running XBMCBuntu 12.10 on an HTPC with the server hostname "SCREEN", and trying to setup Samba to allow access to a share called "Movies" by mapping username/password credentials to a unix user account (I don't want to allow guest access.) The name of the user is "user". I am able to log into the samba server from my Windows 7 PC's via the UNC path \\192.168.1.103 or via \\SCREEN. I am prompted for the the username and password, and when I enter them, it accepts them. (I set this up via smbusers, mapping the password via passwd.) I know the security settings are correct because if I use incorrect credentials at the prompt, it gives me an error.

**The problem is that I can't see the shared folder that I have defined in smb.conf. **I.e. I just get a blank window in Explorer with no error. And if I try browsing directly to the share via \\192.168.1.103\Movies, it just says "Windows cannot access \\192.168.1.103\Movies - Error code: 0x80070035 The network path was not found.". I have a few other observations that might be relevant:


[LIST]
[*]The config file in /etc/samba/smb.conf is blank. The one that seems to be applicable is in /usr/share/samba/smb.conf.
[*]"sudo testparm -s smb.conf > smb.conf.good" fails with "-bash: smb.conf.good: Permission denied"
[*]The /var/log/samba/log.smbd doesn't seem to contain any errors:
[/LIST]

```
[2013/12/20 21:35:28,  0] smbd/server.c:1053(main)
  smbd version 3.6.6 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/12/20 21:35:28.852983,  0] smbd/server.c:1109(main)
  standard input is not a socket, assuming -D option

```

My smb.conf:

```

[global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   username map = /usr/share/samba/smbusers
   usershare prefix deny list = /
   encrypt passwords = no
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
[Movies]
   path=/home/user/Movies
   browseable = yes
   guest ok = no
   read only = no
   create mask = 0777
   directory mask = 0777
   writeable = yes
   valid users = user

```

---

### Post by volkswagner on 2013-12-21
I have a hunch this is a Windows 7 authentication issue.  My guess is your windows user/pwd does not match SAMBA's.

I suggest creating a user on your Win7 box called 'user' with the password matching that of your samba user.

See if the behavior changes.

---

### Post by JordanRieger on 2013-12-21
@[**[COLOR=#000000]volkswagner[/COLOR]**]("http://ubuntuforums.org/member.php?u=288711"):  I don't think it's a simple username/password authentication issue,  because if I try to login to the UNC share \\SCREEN with the wrong  credentials, I get an error message, but if I login with the correct  credentials, I don't get an error. The problem is that after logging into that share, I don't see the Movies share folder, I just get a blank window.

Just  to be sure, I tried your suggestion, but the behavior didn't change,  except that I was not prompted for the username and password when I  browsed to \\SCREEN, which makes sense since the client and server match  at that point.

---

### Post by volkswagner on 2013-12-21
Well I'm not sure.  Couple things to  try:

In your share definition there is no spaces on either side of the '=' for the path directive. >> grasping at straws here...

Also is this your complete smb.conf file???  Do you have the [homes] directive enabled??? This would conflict with your share inside /home.

When you created the Windows account 'user', did you use lowercase 'u'?

Comparing your smb.conf to mine, there is not much different, other than mine is located at /etc/samba/smb.conf

I do have the netbios directive in global section.  You may try adding the following to your global section:

```
netbios name = SCREEN
```

also what are the file permissions for your share:

```
ls -al /home/user/Movies
```

---

### Post by JordanRieger on 2013-12-21
OK so I solved the original problem, which was basically caused by the config file /etc/samba/smb.conf being blank. I overwrote it with the config file from /usr/share/samba/smb.conf and then restarted Samba:

```
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo service smbd restart

```

Now I have a different problem (authentication). When I browse to \\192.168.1.103 or \\SCREEN, or \\Screen\Movies, I can no longer authenticate successfully. I get "Access is denied" after entering my credentials.

Yes, the windows username is "**user**" in lowercase. I added the **netbios name = SCREEN** line to my config, but it didn't help, so I removed it. I also checked on the spaces in the path name, and it looks like it has one space before and after the **= **sign, which is what we want, right?

```

ls -al /home/user: 
(ommitted all but the Movies directory for brevity):
drwxr-xr-x  7 user user      4096 Dec  8 16:14 Movies

```

Yes, that is my whole config file, except for one strange thing: I noticed that my **log level = 2** line is omitted by the testparm summary:

```
user@SCREEN:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Movies]"
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
        username map = /usr/share/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare prefix deny list = /
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb

[Movies]
        path = /home/user/Movies
        valid users = user
        read only = No
        create mask = 0777
        directory mask = 0777
user@SCREEN:~$

```

---

### Post by JordanRieger on 2013-12-21
**SOLVED IT!** :p

I changed the line

```
encrypt passwords = no
```

to

```
encrypt passwords = yes
```

I guess this was necessary because I was using smbpasswd to add the username/password manually and also had the setting:
```

passdb backend = tdbasm

```
Thanks for your help **volkswagner**!

---

