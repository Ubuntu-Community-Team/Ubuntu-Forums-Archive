---
title: "Windows 7 on domain cant connect to samba share"
date: 2014-02-04
forum: Server Platforms
---

### Post by mike139 on 2014-02-04
I have spent weeks and hours looking on Google and cant figure this out!!!

I can connect to the samba share with a windows 7 computer that is not connected to our domain but any windows 7 computer that are on the domain will not let me map the share!

I get the network path was not found!

I am trying to map it with the static ip address of the server to eliminate any possible dns issues but still cant connect. I can map the drive on both windows 7 and Ubuntu if its not on the domain.

---

### Post by JnPson on 2014-02-04
Can you post you smb.conf here?

---

### Post by mike139 on 2014-02-04
[global]
    workgroup = MAIN.LAN
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins server = 10.1.10.32
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[opt_pcbin]
    comment = opsi depot share
    path = /opt/pcbin
    invalid users = root
    read only = No
    oplocks = No
    level2 oplocks = No

[opsi_depot]
    comment = opsi depot share (ro)
    path = /var/lib/opsi/depot
    invalid users = root
    oplocks = No
    level2 oplocks = No

[opsi_config]
    comment = opsi config share
    path = /var/lib/opsi/config
    invalid users = root
    read only = No

[opsi_workbench]
    comment = opsi workbench
    path = /home/opsiproducts
    invalid users = root
    read only = No
    create mask = 0660
    directory mask = 0770

---

### Post by mike139 on 2014-02-04
I would assume that i could remove all lines that are commented out to make this more clean?

---

### Post by JnPson on 2014-02-05
That would be better. Copy your smb.conf ```
cp smb.conf smb.conf.master
```Use the command ```
testparm -s smb.conf.master > smb.conf 
``` to clean up the smb.conf file

---

### Post by mike139 on 2014-02-05
Ok I did that it said rlimit_max: increasing rlimit_max (1024) to minimum windows limit

Warning you may have some share names that are longer than 12 characters these may not be accessable to some older clients

---

### Post by mike139 on 2014-02-05
That cleaned up the conf file!! but didn't change the issue! Still cant connect!

---

### Post by mike139 on 2014-02-05
I noticed this in the logs log.nmdb under /var/log/samba/
Samba name server HBOPSI is now a local master browser for workgroup MAIN.LAN on subnet 10.3.10.7
  
  *****
[2014/02/05 07:35:21,  0] nmbd/nmbd_browsesync.c:351(find_domain_master_name_query_fail)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MAIN.LAN<1b> for the workgroup MAIN.LAN.
  Unable to sync browse lists in this workgroup.

---

### Post by JnPson on 2014-02-05
Is your server e member of the domain? Is it a domain controller for this domain? If so, how did you create your domain? Is there a windows domain controller in your network? Is it just a Ubuntu client acting as a Ubuntu server?
I think more information is needed. 
I'm no expert on Samba but your smb.conf look correct. 

What version of samba do you use?

---

### Post by mike139 on 2014-02-05
This is running on a windows 2008 domain! I didn't add the server to the domain I was trying to set it up as a stand alone pc. 

Like I said windows 7 computers that are on the network but not added to the domain could connect but windows 7 computers that are joined to our domain cannot connect to the samba share! I tried to connect with the Ubuntu server and it will map its drive. 

I don't know what else to try anymore!!!!! I would have thought that I could setup a samba server that is not joined to the domain and when you map the drive I  select connect using different credentials I figured this would work like any other windows computer!!!

---

### Post by mike139 on 2014-02-05
Samba version 3.6.3

---

### Post by JnPson on 2014-02-05
I would put in
```
guest ok = yes
```
if security wasn't important.

---

### Post by volkswagner on 2014-02-05
Normally it's easiest to set
```
security = user
```

Do your users have unix and SAMBA accounts on the Ubuntu server?

I think when the win7 is joined, it's sending username including domain ie:  domain\user1
Try forcing the username to MAIN.LAN\user1 when mapping.

Is  your Windows domain name "MAIN.LAN"?  If you are not joining Ubuntu to the domain, perhaps it would be best to create a new workgroup name???

Also is there a domain policy preventing this?  Can you create a share on a win7 machine not joined to the domain and map the share from a joined client?

---

### Post by mike139 on 2014-02-06
This is so frustrating!!!!

I created a new virtual machine and reinstalled it again to see if I missed something!!! I have the first setup and now this setup and still no luck!! So confusing I get this account is not authorized to log in from this station if I put in a wrong username and password but if I put in a user id and password that is setup for samba I get 2 messages that are hit or miss one will tell me "The specified server cannot perform the requested operation" or I get the specified network name is no longer available" I am mapping user ip and I can ping and tracert to the server without any problems!!!!

---

### Post by mike139 on 2014-02-06
I can create a share on a windows 7 computer and access it fine with another its something specific to samba or Ubuntu!!! I was reading about share require security and windows but still cant get it to work by changing require security under hkey_local_maching\system\currentcontrollset\services\lanman\Workstation\perameters

---

### Post by JnPson on 2014-02-06
Do an```
ls -l
``` on the disks where your shared folders is and post it here for other to see?

---

### Post by mike139 on 2014-02-06
root@HBOPSI:/var/lib/opsi# ls -l
total 12
drwxrwx--- 7 opsiconfd pcpatch 4096 Feb  6 07:45 config
lrwxrwxrwx 1 root      root      18 Feb  6 07:45 depot -> /opt/pcbin/install
drwxrwx--- 2 root      pcpatch 4096 Feb  6 10:27 ntfs-images
drwxrwx--- 2 opsiconfd pcpatch 4096 Feb  6 10:27 repository

---

### Post by mike139 on 2014-02-06
OK I think i got it working!!!

I added 
client lanman auth = yes
client ntlmv2 auth = no
client use spnego = no
server signing = auto

I can connect with both windows 7 that are joined to the domain and windows 7 that is not! I will do some more testing and let you know!

what is client use spnego = no mean?

---

