---
title: "need help with shares"
date: 2007-05-15
forum: Server Platforms
---

### Post by willough on 2007-05-15
Hi,
I need help.  I know my problem is something simple but I can't get it.  I just bought a new server to act solely as a file server for Windows computers in our small business. I installed Feisty Fawn.  Everything went smoothly.  I installed Webmin and Samba, no problems.  

I set up two folders on the server and put some Excel files in it to test.  
   Problems:  
   1) Whenever I open the files they are always in Read Only. I cannot change or save them.
   2) I can use the Webmin file manager tool to upload files to the file server but I cannot move or copy files from another computer.  I get an access denied message "Make sure the disk is not full or write-protected...".


This is what I am trying to accomplish:
I want to set up two shared folders.  One 'private' that can only be accessed by my partner and I - group called 'onlyus'.  The other 'common' folder to be shared by all employees as well as us.  In both cases the group members should be able to browse and write.

What simple thing am I doing wrong?  How should I set up the shares as described above?

Thanks in adnance for any help.

---

### Post by benzies on 2007-05-16
What kind of permissions do you need for the folder.  

Do you want everyone to be able to access them and write to them etc

Or just Read 

bla bla

---

### Post by willough on 2007-05-16
I want the member of the group that can access the folder to be able to read and write to the files within.

---

### Post by benzies on 2007-05-17
ohhh terminal time >: D

So open up your terminal.

location\ /of\ /folder$sudo chgrp <yourgroup> <foldername>


location\ /of\ /folder$sudo chmod 777  <foldername> <--- this means everyone has control!!!!

memory is a lil rusty at the moment.  Should fix it fine.

Just be warned though, what the 777 means is this. The first 7 if i remeber is 'root' second 7 is 'users' and the third 7 is 'other' (meaning the world or somthing)  how it works out to be  is  rwx (read write execute).

r == 1
w == 2
x == 4

so 1 + 2 + 4 = 7

0 = off

so if it was 770 only local users and administrators can -rwx- the folder and stuff. 
if it was 707 then admins and others can rwx

if it was 711 then admins can do whatever they want. The rest can only read.

Good luck!

---

### Post by layer_923 on 2007-05-17
I am having similair problem, i have double checked the settings all are 777, please find below my config;

What i want is a full read & Write access to users on shared folder, at the moment i see it and i can map to it but wont let me put any files from a XP machine, 

cheers in advance

#======================= Global Settings =======================

[global]


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = T&F

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

   wins support = no
   dns proxy = no

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   security = share

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

# passdb is changed.
;   unix password sync = no


;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# 'passwd program'. The default is 'no'.
;   pam password change = no


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

#======================= Share Definitions =======================

;[homes]
;   comment = Home Directories
   browseable = yes

;   valid users = %S


  writable = yes


  create mask = 0777


  directory mask = 0777

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no


[Samba]
comment = Public
path = /home/weo-server/Samba
available = yes
read only = no
browsable = yes
public = yes
writable = yes
create mask = 777
directory mask = 777
force user = nobody
force group = nogroup

---

### Post by willough on 2007-05-17
I have mostly resolved my issues.  Though I had enough experience to complete the Ubuntu server install and install and configure Samba and Webmin, I lacked some basic Linux / Ubuntu knowledge which I am now filling in.  I urge others to do the same.  I did not understand the fundamental difference between root and user.  All my experience is on Windows which is so different in this regard.  I was trying to accomplish changes in directory permissions while user, but the changes required being root, at least briefly.  I found this article from a forum member very helpful and have since read a number of other tutorials:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I have set up the 'private' directory on the server and can now read and write to it.  I am changing permissions to keep it more secure.  I'll be testing the server over the next few days before becoming completely dependent on it.  

My thanks to all who contributed replies.

---

