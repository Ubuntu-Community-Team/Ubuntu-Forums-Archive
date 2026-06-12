---
title: "samba: printing without password"
date: 2009-01-21
forum: Server Platforms
---

### Post by grzeslaw on 2009-01-21
Hello

I have configured samba, to use the "user" security mode. I do this, for windows users, to login the samba using login/password to get the sharing folders. Users from samba are synchronize with unix password file. On the basies shares, I ascribe users to unix groups, and make the folders with with the group privileges. So, here's my smb.conf
```

#======================= Global Settings =======================
[global]
########## Main Settings  ####
   workgroup = HYYC
   netbios name = ph2
   server string = DOCUMENTS_STORAGE
   wins support = yes
   dns proxy = no
   name resolve order = lmhosts host wins bcast
#### Debugging/Accounting ####
   log level = 2
   log file = /var/log/samba/log.%m
   max log size = 10000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
####### Authentication #######
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   guest account = smbprint
####### Access Options  #######
   hosts allow = 127.0.0.1 192.168.0.0/24
   hosts deny = 0.0.0.0/0
############ Misc #############
   socket options = TCP_NODELAY
   usershare allow guests = yes
############ Printers #######
   printcap name = cups  
   printing = cups   
   load printers = yes
#======================= Share Definitions =======================
[projects]
   path = /data/projects/
   browseable = yes
   read only = no
   create mask = 0664
   directory mask = 0775
   valid users = @ALL
[printers]   
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 0700   
  guest only = yes   
  guest ok = yes
  use client driver = yes  
  path = /home/smbprint

```

The smbprint user is privilaged to use the printer in cups. 

I want to share printers without password, for all users in network. The [projects] share should be available for users from @ALL group and shoud reqired the unix login/password to log-in.

When I use the config for printers which contains security = share, then all users can print without any problems, but also login to the [projects] share is authenticated by windows guest user. 
When I use the config contains security = user,then everybody in the network need to enter the valid login/password from unix password to access sharename and printer. 

So.. can I use two security modes in one samba config? How can I solve my problem?  

What is your suggestions?

Regards.

---

### Post by cmnorton on 2009-01-22
Is the printer a network printer? If it is, you can setup a network printer from Windows, and bypass Samba altogether. Even though this is not an answer to your question, this certainly would be a  backup plan.

I found this link, but it sounds like you already know about this.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html)

---

### Post by grzeslaw on 2009-01-22
yeahh! After many hours of thinking out, I solve it!
The solution is, to set the following option:
```

map to guest = Bad User

```
Also we should remove from the [printers] section option:
```

guest only = yes 

```

And. If user has the same login in windows and unix, we should synchronize passwords in both systems.

---

### Post by figure002 on 2012-03-27
Unfortunately grzeslaw's solution doesn't work for me with Ubuntu 11.10. The other Ubuntu clients are still asked for a password each time they try to print.

My Samba configuration for printers:
```

map to guest = bad user

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700

```

---

