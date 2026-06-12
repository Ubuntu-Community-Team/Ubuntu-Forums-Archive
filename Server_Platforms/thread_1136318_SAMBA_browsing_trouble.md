---
title: "SAMBA browsing trouble"
date: 2009-04-24
forum: Server Platforms
---

### Post by dallasg on 2009-04-24
I am using ubuntu server 8.10 on an x86-64 arch.  Here is my smb.conf:

[global]
   workgroup = WORKGROUP
   server string = %h
   wins support = no
   dns proxy = no


# Debugging and Accounting

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


# Authentication

   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes


#Domains

   /var/lib/samba -s /bin/false %u


# Share Definition

[homes]
   comment = Home Directories
   browsable = no

[data]
   comment = BBT Data
   path = /home/data
   guest ok = no
   browseable = yes
   writeable = yes
   create mask = 0755
   directory mask = 0755


I am not able to browse to my shares through network viewers like Explorer on Windows or Linux workstations.  I can see the server listed in the available servers list but when I attempt to access it, I get an error from windows that tells me "the network path was not found".

I can, however, connect directly to the share via UNC path '\\1.2.3.4\share' and using smbclient from a linux workstation 'smbclient //1.2.3.4/share' so I know the SAMBA share is set up correctly.

Has anyone seen this or experienced it before?  I've been scouring the Internet for two days now and have run dry.

Thanks.

---

### Post by doas777 on 2009-04-24
I'm sorry that this won't be helpful, but i think you will find that many a fellow ubuntian has had this problem.

at this point i have a standard config file that i tweak for all my hosts, and i would say most hosts are visible in the browser about 30% of the time each. all of them can, at one time or other, see everyone of the others, but it is a rare day that any one of them can see all the others at the same time. the wins server i set up, is visible all the time, but thats about it.

every time i really dig into the issue, i get it working almost perfectly, and that lasts for a few days, before problems begin again. I just map "bookmarks" to my most common shares, or type the address into nautilus manually as you do.

---

### Post by kamaji792 on 2009-04-25
Bit of a long shot.

Are all the computers on an appropriate IP address?

Like 192.168.0.x

Are they all set with the same workgroup name?

I has similar problems that seemed to go once I had set the workgroup name.

I would have suggested setting up a Wins server as I thought this did 'name resolution'  i.e. did the translation of computer names to IP addresses. I have never set one up because I never had a big issue and doas777 implies it does not work.

All the best

---

