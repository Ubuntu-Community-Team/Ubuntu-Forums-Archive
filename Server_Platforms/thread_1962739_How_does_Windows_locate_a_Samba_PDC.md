---
title: "How does Windows locate a Samba PDC?"
date: 2012-04-21
forum: Server Platforms
---

### Post by bakegoodz on 2012-04-21
I have a interesting problem. I've created a Samba Primary Domain Controller, but when I try to join with Windows XP or Win7 (with all the compatibility stuff set in the registry) it says "It can't find the Domain controller" until I set the Windows Client's network WINS setting to the Samba PDC's IP address. The strange thing is that I took the Samba PDC server to another network the Windows client joined with just a standard DHCP settings. Both networks don't a WINS server setup or listed in the DHCP lease. The network requiring the WINS setting is running DD-WRT router running DNSmask. The network that Windows Client joins with plain DHCP has a DHCP3 and BIND services on a 10.04 server, and again no WINS setup in those configs. I don't know why the Windows client can't find the PDC. I've done some packet analysis when the problem happens. The Windows client does a browse with a broadcast packet on the subnet's broadcast address (ex 192.168.10.255) and the Samba server responds, but then Windows says it can't find it. So I think it should work on a completely static IP set LAN with no DHCP or DNS. Any ideas?

smb.conf

```
[global]

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CLOUD
   netbios name = MUSHROOM

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

   dns proxy = no

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 1

[global]

   workgroup = CLOUD
   netbios name = MUSHROOM
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 1

####### Authentication #######

   security = user
   encrypt passwords = true
   passdb backend = tdbsam

   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user

   admin users = smbmach

   guest account = nobody

   invalid users = root

########## Domains ###########

   domain logons = yes
   logon path = \\%N\%U\.windows_profile

   logon drive = U:

   domain master = yes
   local master = yes
   preferred master = yes
   os level = 80

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0600
   directory mask = 0700

   valid users = %S


```

---

### Post by bakegoodz on 2012-04-24
I talked to a SysAdmin and he says that Netbios is obsolete and unreliable. He says to always setup WINS in smb.conf and dhcp3.conf.

I went to do it and I see there is multiple lines for WINS. How exactly would you modify smb.conf to enable WINS?

---

