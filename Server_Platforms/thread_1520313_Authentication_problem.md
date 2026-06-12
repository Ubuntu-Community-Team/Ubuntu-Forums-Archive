---
title: "Authentication problem"
date: 2010-06-29
forum: Server Platforms
---

### Post by Earnol on 2010-06-29
I'm feeling i'll be immediately banned for asking such a stupid question, but i'm really lost and somewhat frightened. 

I'm running Lucid x64 server (samba + apache + transmission-daemon). 
Today when i've tried ssh loging i've got "access denied". I've tried several times and on Nth login attempt it allowed me in. Finally.
Of coz, one can never be too careful as soon one has public (or password protected public, like in my case) open ports.
So i've done less /var/log/auth.log
and found following:
```

Jun 29 13:25:01 SVA1 CRON[13333]: pam_unix(cron:session): session closed for user root
Jun 29 13:26:36 SVA1 sshd[13347]: Accepted password for vladik from 195.209.xxx.xxx port 63112 ssh2
Jun 29 13:26:36 SVA1 sshd[13347]: pam_unix(sshd:session): session opened for user vladik by (uid=0)
Jun 29 13:26:58 SVA1 sudo:   vladik : TTY=pts/1 ; PWD=/home/vladik ; USER=root ; COMMAND=/usr/sbin/megasasctl -stevv a0
Jun 29 13:27:36 SVA1 sshd[13347]: pam_unix(sshd:session): session closed for user vladik
Jun 29 13:28:11 SVA1 sshd[13450]: Accepted password for vladik from 195.209.xxx.xxx port 55788 ssh2
Jun 29 13:28:11 SVA1 sshd[13450]: pam_unix(sshd:session): session opened for user vladik by (uid=0)
Jun 29 13:28:21 SVA1 sudo:   vladik : TTY=pts/1 ; PWD=/home/vladik ; USER=root ; COMMAND=/bin/bash
Jun 29 13:30:01 SVA1 CRON[13609]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 29 13:30:01 SVA1 CRON[13609]: pam_unix(cron:session): session closed for user root
//skip cron spam
Jun 29 17:06:37 SVA1 sshd[15582]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=pik.spbstu.ru  user=vladik
Jun 29 17:06:37 SVA1 sshd[15582]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 29 17:06:37 SVA1 sshd[15582]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 29 17:06:37 SVA1 sshd[15582]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PA
M_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jun 29 17:06:40 SVA1 sshd[15582]: Failed password for vladik from 195.209.xxx.xxx port 50703 ssh2
Jun 29 17:06:46 SVA1 sshd[15582]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 29 17:06:46 SVA1 sshd[15582]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 29 17:06:46 SVA1 sshd[15582]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PA
M_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jun 29 17:06:48 SVA1 sshd[15582]: Failed password for vladik from 195.209.xxx.xxx port 50703 ssh2
Jun 29 17:06:53 SVA1 sshd[15582]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 29 17:06:53 SVA1 sshd[15582]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 29 17:06:53 SVA1 sshd[15582]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PA
M_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jun 29 17:06:55 SVA1 sshd[15582]: Failed password for vladik from 195.209.xxx.xxx port 50703 ssh2
Jun 29 17:06:56 SVA1 sshd[15582]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=pik.spb
stu.ru  user=vladik
Jun 29 17:07:15 SVA1 sshd[15588]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhos
t=pik.spbstu.ru  user=vladik
Jun 29 17:07:15 SVA1 sshd[15588]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 29 17:07:15 SVA1 sshd[15588]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 29 17:07:15 SVA1 sshd[15588]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PA
M_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jun 29 17:07:17 SVA1 sshd[15588]: Failed password for vladik from 195.209.xxx.xxx port 57494 ssh2
Jun 29 17:07:37 SVA1 sshd[15588]: pam_winbind(sshd:auth): getting password (0x00000388)
Jun 29 17:07:37 SVA1 sshd[15588]: pam_winbind(sshd:auth): pam_get_item returned a password
Jun 29 17:07:37 SVA1 sshd[15588]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PA
M_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Jun 29 17:07:40 SVA1 sshd[15588]: Failed password for vladik from 195.209.xxx.xxx port 57494 ssh2
Jun 29 17:07:45 SVA1 sshd[15588]: PAM 1 more authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=pik.spbs
tu.ru  user=vladik
Jun 29 17:08:07 SVA1 sshd[15594]: Failed password for vladik from 195.209.xxx.xxx port 55727 ssh2
Jun 29 17:09:01 SVA1 sshd[15594]: last message repeated 3 times
Jun 29 17:09:01 SVA1 CRON[15600]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 29 17:09:01 SVA1 CRON[15600]: pam_unix(cron:session): session closed for user root
Jun 29 17:09:27 SVA1 sshd[15609]: Accepted password for vladik from 195.209.xxx.xxx port 58154 ssh2
Jun 29 17:09:27 SVA1 sshd[15609]: pam_unix(sshd:session): session opened for user vladik by (uid=0)
Jun 29 17:10:02 SVA1 CRON[15716]: pam_unix(cron:session): session opened for user root by (uid=0)
Jun 29 17:10:02 SVA1 CRON[15716]: pam_unix(cron:session): session closed for user root
Jun 29 17:12:36 SVA1 sudo:   vladik : TTY=pts/1 ; PWD=/home/vladik ; USER=root ; COMMAND=/usr/sbin/megasasctl -stevv a0
Jun 29 17:12:43 SVA1 sshd[15609]: pam_unix(sshd:session): session closed for user vladik
Jun 29 17:12:54 SVA1 sshd[15778]: Accepted password for vladik from 195.209.xxx.xxx port 54640 ssh2
Jun 29 17:12:54 SVA1 sshd[15778]: pam_unix(sshd:session): session opened for user vladik by (uid=0)
Jun 29 17:12:57 SVA1 sshd[15847]: subsystem request for sftp
Jun 29 17:14:16 SVA1 sshd[15778]: pam_unix(sshd:session): session closed for user vladik

```I do not understand how user vladik can temporarily disappear from the system leaving no traces about it's disappearance...
And, yes, i'm sure password was typed correctly always....

I wonder are there are any additional log files i can examine to understand why user temporarily disappeared?

---

### Post by cdenley on 2010-06-29
You're using pam_winbind to authenticate the user? What is it authenticating against?

---

### Post by BobVila on 2010-06-29
Yeah, looks like the machine wasn't able to communicate with whatever you're attempting to authenticate against. Thus, it thought that vladik wasn't a real user.

---

### Post by Earnol on 2010-06-29
Thank you! 
Stright to the point!
pam_unix AND pam_winbind
pam_unix as i understand, is normal unix /etc/passwd with shadow prrotection. Basically it is what i want.
pam_winbind is something neither expected nor desired, i do not want to use and have no idea why ssh is using it. Basically network is workgroup where linux is sambaserver.
pam_winbind has some relation to samba, and i guess it is ok, but for what reason sshd is started using it and how to fix this problem is missing my brain.

---

### Post by cdenley on 2010-06-29
> **Earnol said:**
> Thank you! 
Stright to the point!
pam_unix AND pam_winbind
pam_unix as i understand, is normal unix /etc/passwd with shadow prrotection. Basically it is what i want.
pam_winbind is something neither expected nor desired, i do not want to use and have no idea why ssh is using it. Basically network is workgroup where linux is sambaserver.
pam_winbind has some relation to samba, and i guess it is ok, but for what reason sshd is started using it and how to fix this problem is missing my brain.

Pam is configured to authenticate against winbind, and sshd uses PAM for authentication. Did you want users to be authenticated against winbind when logging in locally?

---

### Post by capscrew on 2010-06-29
> **cdenley said:**
> Pam is configured to authenticate against winbind, and sshd uses PAM for authentication. Did you want users to be authenticated against winbind when logging in locally?

More to the point, Winbind is used to map Samba users to Windows users in either a NT or AD based situation or as acting as a PDC. If the OP is logging in locally then Winbind should be removed.

In this particular situation, when Winbind is removed the OP will have to check that the PAM references to Windbind are indeed also removed.  Maybe [FONT="Courier New"]**[COLOR="Blue"]apt-get purge winbind[/COLOR]**[/FONT] is appropriate here.

---

### Post by Earnol on 2010-06-30
Very nice.
Removal winbind seems have sorted problem out.  I just do not understand how it was installed in the first place. It seems to me it came with samba, but still i have not installed winbind explicitly...

PS: How to mark thread as solved?

---

### Post by capscrew on 2010-06-30
> **Earnol said:**
> Very nice.
Removal winbind seems have sorted problem out.  I just do not understand how it was installed in the first place. It seems to me it came with samba, but still i have not installed winbind explicitly...

I'm sure that when you installed all the Samba packages you selected it.  But, not to worry; it's solved now! > 
PS: How to mark thread as solved?
At the top of the threat under "thread tools" is a link to marking the thread solved.

---

