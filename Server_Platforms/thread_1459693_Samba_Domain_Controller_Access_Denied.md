---
title: "Samba Domain Controller Access Denied"
date: 2010-04-21
forum: Server Platforms
---

### Post by darkscorpion20 on 2010-04-21
I am attempting to replace our aging and expensive Windows Domain Controller with a Samba Based DC. We do not use roaming profiles or anything special, just authentication.

Before i start, please note i am somewhat new to linux, but i like to dive off the deep end to learn things so here i am.

I have read, among other hours of research, the following 2 guides. The second being the primary guide i followed.
[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)
[https://help.ubuntu.com/community/SettingUpSambaPDC](https://help.ubuntu.com/community/SettingUpSambaPDC)

I currently have 2 users, "administrator", and a mirror of one of our users called "anthonyr". Both have been added to the groups administrators, admin, & users.

**ISSUE: When attempting to join a freshly installed Windows XP workstation to the domain i receive "The user name could not be found." when trying "administrator". When i use "anthonyr" i receive "Access is denied."**

I have added and set the password of both using smbpasswd.

I have mapped the following groups, as well as created the machines group.
sudo net groupmap list
Domain Users (S-1-5-21-216790643-1304523725-3675387884-1001) -> users
Domain Admins (S-1-5-21-216790643-1304523725-3675387884-512) -> administrators

Below is a copy of my smb.conf

If there is any other information that could be helpful please let me know. Also, i am open to other methods so long as the end goal of a DC for user authentication from windows computers is met.

Thanks for any help.

Server: Ubuntu 9.10
Samba: 4.0.0

-------------------------------------------------------------------
[global]
   workgroup = PTBC
   server string = PTBC-DC-01
   netbios name = PTBC-DC-01
   wins support = yes
   dns proxy = no

   log file = /var/log/samba/log.%m
   log level = 1
   max log size = 1000
   syslog = 0

   admin users = administrator
   security = user
   guest account = nobody
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   map to guest = Bad Password
   password level = 0

   add user script = /usr/sbin/useradd -m '%u' -g users -G users
   delete user script = /user/sbin/userdel -r '%u'
   add group script = /usr/sbin/groupadd '%g'
   delete group script = /usr/sbin/groupdel '%g'
   add user to group script = /usr/sbin/usermod -G '%g' '%u'
   add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u' -g machine

   logon path =
   logon home = 

   domain logons = yes
   os level = 64
   logon script = logon.cmd

   socket options = TCP_NODELAY
   time server = yes

[netlogon]
   path = /srv/samba/netlogon
   public = no
   writable = no
   browsable = no
   valid users = @smbusers

---

### Post by darkscorpion20 on 2010-04-27
No one has any thoughts on this?

---

### Post by joeinbend on 2010-05-04
Wow... Crickets, tumbleweeds... :| Hey Darkscorpion, I am in the process of doing the same thing: Replacing my Win2003 PDC with a Ubuntu solution. I'm doing this mainly so i can dump a VM that does nothing but authenticate users, but soaks up 1GB RAM, where I should be able to do the same in a Ubuntu Server 10.04 using only 128MB RAM. I wanted to let you know this is on my radar for today, and I'll post back with my findings.

---

### Post by wrp on 2010-05-05
Hello Darkscorpion, 
I have just started a new thread on this but I think your problem is related to mine. 
You must be root to add a machine account to the Samba PDC but root is disabled by default in ubuntu. 
You can therefore enable root in ubuntu and map your windows admin user to root - this should solve the problem OR - at least according to the server guide you should be able to modify your script to:
add machine script = sudo /usr/sbin/useradd -s /bin/false -d /var/lib/nobody '%u' -g machine
and then make sure that you map your windows user to a unix user with sudo privileges. See the most recent server guide
[https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/9.10/serverguide/C/samba-dc.html) 
Point number 7.
I hope this helps but please post if you get a working solution to the sudo problem because I have not yet seen one
Cheers

---

### Post by lobstar on 2013-01-25
I know this is old subject, but I have the same problems right now just with 12.04.

I tried to follow the help guides but get the same error about not finding the user. 

Did you ever solve this?

---

### Post by lingpanda on 2013-01-25
> **lobstar said:**
> I know this is old subject, but I have the same problems right now just with 12.04.



I tried to follow the help guides but get the same error about not finding the user. 



Did you ever solve this?



Are you using Windows RSAT to administer? I would give that a go if not already.

---

### Post by overdrank on 2013-01-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

