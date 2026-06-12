---
title: "TIGER: How to"
date: 2011-03-11
forum: Security
---

### Post by buntuser2 on 2011-03-11
From tiger logs: [I]The root user should not have the message capability turned on.
This could lead to inadvertent modification of files with the root user
is logged in.[/I]

I'm trying to find out where to disable or turn this off but it isn't in my group or admin account settings and when you google there is nothing found on it.

Has anyone ever turned it off before or know where the setting for it is?

---

### Post by cariboo on 2011-03-11
If you install an app like logwatch, it will allow root to send email messages when a problem is found. I would suggest that you check to see if anything you installed, also install an email server. A quick way to check is to run nmap against your system, and see if port 25 is open and listening. If it is, I'd check synaptic to see if postfix is installed, as it seems to be the email server of choice for many apps.

---

### Post by buntuser2 on 2011-03-11
Hi all.

So we all know ubuntu comes really secure on a default install, but there are some who like to cover all angles and some who are just OCD (Obsessive compulsive) when it comes to their linux system.

I made this thread for the tiger warnings for myself and others. I'll list each warning and then as people post their responses and how-to I will edit this main post with the how-to for each warning message.


--------------------------------------------


**#1**

--WARN-- [acc006w] Login ID mail's home directory (/var/mail) has group `mail' and world write access. 

**Explanation:** The home directory of the listed login ID has group write permission, world write permission or both enabled.  This allows new files to be added (and existing files potentially removed) by others.  The write permissions should be removed.

[B]
Fix:[/B]   ```
sudo chown root:root /var/spool/mail
```

To change permissions: ```
sudo chown root:root /var/spool/mail
```

To change home directory permissions: ```
sudo chown -R 700 /home/$USER
```


**#2**

--WARN-- [root003w] Root user has message capability turned on.

**Explanation:** The root user should not have the message capability turned on.
This could lead to inadvertent modification of files with the root user is logged in.


[B]
Fix:[/B] 





**#3**
 
--WARN-- [cron005w] Use of cron is not restricted
 
 **Explanation:** Cron allows users to submit jobs for the system to do at a particular,
possibly recurring time.  It can be very useful, but also has a very
real potential for abuse by either users or system crackers.  Users can
be restricted to use cron by creating a /etc/cron.allow (holding only
system administrators) or a /etc/cron.deny file (listing which users are
not allowed access). Depending on the site configuration if none exist
either only root will be able to setup cron tasks or all users will be
permitted. In many systems the default is to allow access to all users.
 
 [B]
Fix:[/B] 





**#4**
 
 --WARN-- [inet003w] The port for service ndtp is also assigned to service pipe_server.
 
 **Explanation:** The indicated port number is assigned to another service.  This indicates
either a misconfiguration in the services database, or a possible sign
of an intrusion. This should be checked and corrected.  If it is not
apparent why it is like this, the system should be checked for other
signs of intrusion.

 
 [B]
Fix:[/B] 






**#5**
 
 --FAIL-- [perm002f] The group owner of /bin/su should be root.
 
 **Explanation:** The group owner of the indicated file is not correct.  With the incorrect
group ownership, a vulnerability may exist.  The group owner of the file
should be corrected.

 
 [B]
Fix:[/B]  ```
sudo chown root:root /bin/su
```





**#6**
 
 --ALERT-- [perm023a] /usr/bin/at is setuid to `daemon'.
 
 **Explanation:** The indicated file has the setuid bit set, but it should not have it.
This should be changed by using 'chmod u-s file' where 'file' is the
indicated file.  The system should be checked for signs of intrusion.

 
 [B]
Fix:[/B] 





**#7**
 
 --WARN-- [perm001w] The owner of /usr/bin/at should be root (owned by daemon). 
 
 **Explanation:**  The owner of the indicated file is not what is considered best for
security reasons.  Unless you have a specific reason for not changing
the ownership, this should be corrected.

 
 [B]
Fix:[/B] 





**#8**
 
 --ALERT-- [perm024a] /usr/bin/wall is setgid to `tty'
 
 **Explanation:** The indicated file has the setgid (group) bit set, but it should not
have it.  This should be changed by using 'chmod g-s file' where 'file' is
the indicated file.  The system should be checked for signs of intrusion.
 
 [B]
Fix:[/B] 





**#9**
 
 --WARN-- [misc021w] There are no umask entries in /etc/init.d/rcS 
 
 **Explanation:** No umask entries have been found for a shell after reviewing the rc
configuration files it loads.  It is recommended that there are umask
entries set in the configuration file so that users that access the
system through this shell will have a sane default.  Note that even if
set globally through PAM (unless using pam_umask) for login shells it
needs to be defined in a shell by shell casis to cover logins through su,
cron, ssh etc.

 
 [B]
Fix:[/B] 





**#10**
 
--FAIL-- [logf005f] Log file /var/log/btmp permission should be 660
 
 **Explanation:** The log file does not have proper permissions set. It is recommended
that you change the permissions to those suggested for these file.
 
 [B]
Fix:[/B]  ```
sudo chmod 660 /var/log/btmp
```





**#11**
 
 --WARN-- [misc026w] There is no default umask settings for user login shells 
 
 **Explanation:** No umask value has been set globally for all user login shells through
PAM's configuration. Users which use shells for which there is no umask
value defined might be running processes using insecure umask values. As
a consequence, other users in the systems might be able to write to the
files processes work with.
 
 [B]
Fix:[/B] 





**#12**
 
 --WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi.
 
 **Explanation:** Processes that have not been run by root are listening on interfaces open
to the outside. This processes might have been run by root and changed
uids or might be rogue processes.  Confirm if their presence is necessary.
Notice that sometimes services open sporadic UDP listeners to receive
DNS requests, if you receive reports on open UDP services that later on
are closed this might be a false positive.

 
 [B]
Fix:[/B] 





**#13**
  
  
  
  **Explanation:**  Devices that have improper (world) permissions might be accessed by any
system user. This might open security holes if these are shared devices
or hold binaries (disks for example). The administrator should properly
set device access (using group configuration to provide access to a
device to multiple users, for example).
  
  [B]
Fix:[/B] 





**#14**
  
  --WARN-- [embed001w] Path `/etc/mail/Makefile' contains `/etc/mail' which is not owned by root (owned by smmta). Embedded references in: /etc/init.d/sendmail/usr/bin/mailq->/default(PATH)
  
  **Explanation:** The indicated pathname to an executable contains a component which is
not owned by root.  This can enable an intruder to gain unauthorized
privileges if they are able to replace the binary.  See the 'rationale'
explanation for a discussion of the reasons that executables run by root
should be owned by root.

  
  [B]
Fix:[/B] 





[B]#15

[/B]   --WARN-- [path009w] /etc/profile does not export an initial setting for PATH. 
  
  **Explanation:** An initial setting of the PATH variable should be setup in the default
locations for shell login programs (/etc/profile, /etc/csh.login, etc.).

  [B]
Fix:[/B] 





Inlcude the Number (1 through 15) in your reply if you're going to add a fix. I'll update the post as the fixes are submitted.

---

### Post by cariboo on 2011-03-11
> #1

--WARN-- [acc006w] Login ID mail's home directory (/var/mail) has group `mail' and world write access. 

Explanation: The home directory of the listed login ID has group write permission, world write permission or both enabled. This allows new files to be added (and existing files potentially removed) by others. The write permissions should be removed.


Fix: 

On my system the /var/spool/mail directory is owned by root:root, it has permissions of 777, if you change the permissions to 755, it won't be world readable any more. If you change the permissions of /home/user to 700, only the user and root can access the files. To change ownership of /var/spool/mail:

```
sudo chown root:root /var/spool/mail
```

to change permissions:

```
sudo chmod -R 755 /var/spool/mail
```

to change your home directory permissions:

```
sudo chown -R 700 /home/$USER
```

where $USER is your user name. You probably get an error about not being able to change permissions on ~/'gvfs, t's owned by root, so that's normal

> #5

--FAIL-- [perm002f] The group owner of /bin/su should be root.

Explanation: The group owner of the indicated file is not correct. With the incorrect
group ownership, a vulnerability may exist. The group owner of the file
should be corrected.



Fix: 

The owner of /bin/su on my system is root, if you've changed it to something else fix it:

```
sudo chown root:root /bin/su
```

> #10

--FAIL-- [logf005f] Log file /var/log/btmp permission should be 660

Explanation: The log file does not have proper permissions set. It is recommended
that you change the permissions to those suggested for these file.


Fix: 

On my system the permissions on /var/log/btmp are 660, to fix:

```
sudo chmod 660 /var/log/btmp
```

> #12

--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi.

Explanation: Processes that have not been run by root are listening on interfaces open
to the outside. This processes might have been run by root and changed
uids or might be rogue processes. Confirm if their presence is necessary.
Notice that sometimes services open sporadic UDP listeners to receive
DNS requests, if you receive reports on open UDP services that later on
are closed this might be a false positive.



Fix: 

If you don't need network discovery, for example if you have a network printer, and you want it to be auto detected during installation, you need avahi. If you don't need avahi you can remove it, first you need to stop the service:

```
sudo apt-get purge avahi-daemon
```

What did you do to your file permissions and ownerships? 

I've also merged your two threads, because they about the same problem.

---

### Post by buntuser2 on 2011-03-11
Alright I added them to the main page.

Hope some others will fill in the rest!

---

### Post by unspawn on 2011-03-12
> **cariboo907 said:**
> If you install an app like logwatch, it will allow root to send email messages when a problem is found. I would suggest that you check to see if anything you installed, also install an email server. A quick way to check is to run nmap against your system, and see if port 25 is open and listening. If it is, I'd check synaptic to see if postfix is installed, as it seems to be the email server of choice for many apps.
No, here "message capability" means 'man 1 mesg' (see tiger/scripts/check_root). 

Fix: Add the line '/usr/bin/mesg n' to the resource file that gets sourced on shell login.

---

### Post by buntuser2 on 2011-03-12
> **unspawn said:**
> No, here "message capability" means 'man 1 mesg' (see tiger/scripts/check_root). 

Fix: Add the line '/usr/bin/mesg n' to the resource file that gets sourced on shell login.

Where is the resource file usually located and how do you identify it?

---

### Post by cariboo on 2011-03-12
> **unspawn said:**
> No, here "message capability" means 'man 1 mesg' (see tiger/scripts/check_root). 

Fix: Add the line '/usr/bin/mesg n' to the resource file that gets sourced on shell login.

Thanks unspawn, I still learn something new, almost daily. :)

---

### Post by unspawn on 2011-03-12
> **cariboo907 said:**
> I still learn something new
As do I, as do I...


> **buntuser2 said:**
> Where is the resource file usually located and how do you identify it?
'echo $SHELL', usually BASH: ~/.bash_profile (also see 'man 'bash' the *invocation* part).

---

### Post by buntuser2 on 2011-03-12
I found /bin/bash but it will not let me open it with text editor. I tried clicking and through the terminal commands...what the heck?

---

### Post by cariboo on 2011-03-13
I'm running Natty, but I'm sure it's the same in Lucid and Maverick, the file you are looking for is in your home directory, look for ~/.profile

---

### Post by buntuser2 on 2011-03-14
Anyone know #3, #4, or #9 ?

---

### Post by unspawn on 2011-03-15
> **buntuser2 said:**
> I found /bin/bash but it will not let me open it with text editor.
/bin/bash is a binary (run 'file '/bin/bash'): in the case of BASH, the default shell on most Linux distributions instead see 'man bash', the "invocation" part for locations and files the shell sources.


> **buntuser2 said:**
> Anyone know #3, #4, or #9 ?
#3 is CFB: using /etc/cron.deny is a blacklist type so it will always be out of date unless you update it on adding users: pipe allowed user account names into /etc/cron.allow instead.

#4 should be reviewed locally: if you don't run ndtp but (RPC?) pipe_server then reflect those changes in /etc/services (I don't need to talk about making backups of configuration fils, right?).

#9 depends on how and where the system sets the umask. For a distribution-agnostic view of things at least check shell invocation (again 'man bash', the "invocation" part) and /etc/login.defs (and umask in 'man login.defs') too.

---

