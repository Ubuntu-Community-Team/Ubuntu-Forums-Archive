---
title: "problems connecting to samba pdc"
date: 2008-02-13
forum: Server Platforms
---

### Post by beaker15 on 2008-02-13
Hi, 
I have a samba PDC and have about 8 XP clients and an Ubuntu client. I'm trying to get them all to join the domain but neither will. First off, the XP machines:
I go to join the domain the usual way, it prompts for username/password with permission to join the domain and comes up with a message 'Welcome to the domain'. After restarting i get the logon screen and select to login to the domain but after putting the correct username/password in it shows an error message saying the Server may be offline or unavailable or there is no machine account. There is definitely a machine account on the Samba server, it is not this. the logfile from /var/log/samba: for the client show lots of 'Can't become connected user' messages. I can post the whole thing if requested.

On the ubuntu client, this is what i get:

colin@cycle-12:~$ sudo net join -W CYSOL -U frc
[sudo] password for colin:
Connection failed: NT_STATUS_LOGON_FAILURE
Password:
Could not connect to server SRV-01
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE

both machines definitely have machine accounts on samba.
Any ideas would be much appreciated

thanks in advance

---

### Post by kyriakos1977 on 2008-02-14
did you smbpasswd -a "username" ?

---

### Post by beaker15 on 2008-02-14
yeah, they exist as users too. Its frustrating because I've been able to log in to the domain before, it was working fine, now its not. All thats changed is some shares have been added

---

### Post by beaker15 on 2008-02-14
Some more info from the samba log account of the XP client i'm currently using (I've not posted all of it, just some lines of interest):

libsmb/ntlm_check.c:ntlm_password_check(344)
ntlm_password_check: NT MD4 password check failed for user colin

check_winbind_security: Not using winbind, requested domain [CYSOL] was for this SAM.
auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [Colin] -> [Colin] FAILED with error NT_STATUS_WRONG_PASSWORD
smbd/error.c:error_packet(146)
  check_ntlm_password:  Checking password for unmapped user []\[]@[CYCLE-13] with the new password interface
[2008/02/14 13:09:09, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [CYSOL]\[]@[CYCLE-13]
[2008/02/14 13:12:58, 3] smbd/error.c:error_packet(146)
  error packet at smbd/sesssetup.c(99) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE

---

### Post by kyriakos1977 on 2008-02-14
ok if it was working before 
"All thats changed is some shares have been added"
check again for some erros with testparm

I've never worked a domain in samba but i'm sure that you should have some settings like
domain master = Yes
encrypt password =Yes

---

### Post by astrotech226 on 2008-02-14
This isn't right.  It's trying to authenticate your local user "colin" and you are passing "frc" as the user to join the domain with.  Try this.  Become root:

```
sudo su -
```

Then try to join the domain:

```
# net join -W CYSOL -S <Insert PDC Name> -U <user with uid #0 rights>
```

I am pretty sure that the user you use needs to be administrator or root.  You need UID 0 to be able to add the machine account to whatever database backend you are using.

When you go through the process of joining the domain from a Windows computer, what user did you use to join the domain?  Use that same user here in Linux.

---

### Post by rlross4455 on 2008-02-15
You first try restarting the Samba Server: sudo /etc/init.d/samba restart.

---

