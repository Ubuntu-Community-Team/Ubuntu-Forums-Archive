---
title: "Samba unix password sync not working"
date: 2008-10-21
forum: Server Platforms
---

### Post by greggus on 2008-10-21
Hi there!

Can anybody tell me how to make Samba REALLY sync password with system?
It worked long time ago, but now it's broken somehow...

I use Ubuntu 8.10 Server (beta) but in 8.04 I had the same problem.
The adequate part of smb.conf below...

```
####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   passwd chat = *password:* %n\n *password:* %n\n *password*
   pam password change = yes
   map to guest = bad user

```

As you can see, I've even tried to simplify passwd chat to the limits. Still with no success.

What is wrong?
How can I investigate what is going on during smbpasswd USER operation?
auth.log nor log.smbd not showing any passwd operation.

BTW I can't make any of Ubuntu, Fedora or CentOS to do this for me.

P.S. Please, excuse my any mistakes as english is not my native language. Hope you can understand me well enough.

---

### Post by richard_snickers on 2009-01-29
Hi,

I am having an almost exactly similar problem in Gentoo (used to work, no longer does). No chats get written to log.smbd, even with this smb.conf:
```

enable privileges = yes
[global]
   workgroup = ~~~~~~~~~~
   netbios name = ~~~~~~~~~~~~~~
   server string = Domain Controller
   wins support = yes
   dns proxy = no
   name resolve order = wins host bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 10
   security = user
   domain logons = yes
   passdb backend = tdbsam
   obey pam restrictions = yes
   guest account = samba
   map to guest = Bad User
   unix password sync = yes
   passwd program = /bin/passwd %u
   #Gentoo 9/2007 specific
   passwd chat = *new*password* %n\n *new*password* %n\n *successfully*
  passwd chat debug = yes
  log level = 101
...

```

 Did you ever figure it out?

---

### Post by greggus on 2009-01-29
I've found out that the passwords are correctly changed when users do it via 'change password' dialog in Windows but not if using smbpasswd on the server (as root).
So, check if the passwords are synced when changing samba password from Windows box?

---

### Post by richard_snickers on 2009-01-29
Thanks!

That does appear to be the case here as well. I was doing all my testing with smbpasswd. Setting from windows is the important part anyway, so this will be just an occasional inconvenience. If this is a long term change then I suppose I will experiment with an expect script that calls both passwd and smbpasswd for using from the server side.

I can't even remember if sync ever worked with smbpasswd.

---

