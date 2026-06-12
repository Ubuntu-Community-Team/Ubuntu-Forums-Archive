---
title: "shareMan: Easily share on Windows Network using samba [BETA TESTERs NEEDED]"
date: 2008-01-30
forum: The Cafe
---

### Post by applegrew on 2008-01-30
[SIZE="7"][COLOR="Red"]For BETA Testing[/COLOR][/SIZE]
Was the above scary enough? Good.

------------------------------
I have created a set of shell scripts to let users share folders using samba in minimum steps and easily. This script is intended to be used by average users.

**_Requirements_**:-
[LIST=1]
[*]kommander
[*]samba (Check that testparm is installed. It is required. It is in the samba-common package)
[/LIST]

**It is designed for KDE. My aim for creating this script is to let user share his/her folders easily with user authentication if required. Furthermore, I hated KDE's long, winding and sucky method of folder sharing.**

**_smb.conf template_**:-
Below is the settings that shareMan uses to for smb.conf. Please point out possible problems that a user could face with the following settings and provide solutions or workarouns to them (if any).

```

####################################################
#smb.conf created by shareMan a script by AppleGrew#
#Backup of last smb.conf has been saved at         #
#/home/your_username/.smb.conf-backup/smb.conf.2008-01-30_12.27.21
####################################################
[global]
  workgroup = MSHOME
  server string =
  null passwords = Yes
  passdb backend = tdbsam
  username map = /etc/samba/smbusers
  syslog only = Yes
  announce version = 5.0
  name resolve order = wins lmhosts hosts bcast
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
  printcap name = CUPS
  wins support = Yes
  printing = cups
  print command =
  lpq command = %p
  lprm command =

[print$]
  path = /var/lib/samba/printers
  write list = root
  create mask = 0664
  directory mask = 0775
  guest ok = Yes

[your shared folder that requires NO authentication]
  path = /path/to/the/directory
  browsable = yes
  writable = no
  directory mask = 0555
  force user = your_username
  force group = your_username
  guest ok = yes

[your shared folder that REQUIRES authentication]
  path = /path/to/the/directory
  browsable = yes
  writable = no
  directory mask = 0555
  force user = your_username
  force group = your_username
  guest ok = no #<-------- See here
  valid users = samba_username #<-------- any vallid samba user that you create using easysmbconf (see its help)

[Same as above but also has write access]
  path = /path/to/the/directory
  browsable = yes
  writable = yes #<-------- See here
  create mask = 0744 #<-------- See here
  directory mask = 0555
  force user = your_username
  force group = your_username
  guest ok = no
  valid users = samba_username
####################################################
#                End of config file                #
####################################################

```


[SIZE="4"]**_Beta testers please please do read the following..._**
[LIST=1]
[*]Please notify me of any possible pitfalls in the config file the script creates and provide the solution or workaround too.
[*]Please go through the Readme and Install files of the package too. Try to follow the installation tasks as written so that I may know if the instructions is easy enough and correct even for noobs. Furthermore, the Readme consists of some very important notes to introduce you to the scripts. You find there a very potential problem there if you read.
[*]Please *try* to go throught the code, specially shareMan's, and try and find potential problems there.
[/LIST]
[/SIZE]

Download shareMan from the attachment. See the GUI screenshot below in attachment section.

---

### Post by applegrew on 2008-01-31
Bump!

---

