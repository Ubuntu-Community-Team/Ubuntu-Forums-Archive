---
title: "Samba Shares Are Not Working In Windows Network"
date: 2007-09-24
forum: Server Platforms
---

### Post by UbuNewbie123 on 2007-09-24
My samba shares used to be working. All of sudden, they do not work. The only difference I made to my Ubuntu server is exim4. I just installed and configured exim4 on my machine.

Here's my samba shares:

[PHP]
[ApacheDocRoot]
comment = Apache Document Root
path = /opt/lampp/htdocs/
valid users = vincent
public = yes
writable = yes
printable = no

[ApacheConfig]
comment = Apache Configurations
path = /opt/lampp/etc
valid users = vincent
public = yes
writable = yes
printable = no

[PHPConfig]
comment = PHP Configurations
path = /opt/lampp/zend/etc
valid users = vincent
public = yes
writable = yes
printable = no
[/PHP]

Here's the stuff I see when I run "dpkg-query -l samba":

[PHP]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  samba                         3.0.24-2ubuntu1.2             a LanManager-like file and printer server for Unix
[/PHP]

The 3 directories are missing from my samba. I have to enter "\\IPADDRESS" into a windows address bar to access my ubuntu server shares. I used to see them but now they are not there.

---

### Post by HermanAB on 2007-09-24
Here is a debug guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by GigaVolt on 2007-09-24
My config:
```
[global]
   log file = /var/log/samba-log.%m
   lock directory = /var/lock/samba
   share modes = yes
   security = share

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750

[freefaler]
   comment = Temporary file space
   path = /storage/2/freefaler
   read only = no
   public = yes
```
Packages:
```
ii  samba                                      3.0.24-2ubuntu1.2                          a LanManager-like file and printer server fo
ii  samba-common                               3.0.24-2ubuntu1.2                          Samba common files used by both the server a

```

---

### Post by UbuNewbie123 on 2007-09-24
In the debug document, it says:

> Ensure that the users have the same usernames and passwords on Linux and Windows. Apart from creating a Linux user with userdrake, you also have to create a Samba password with 'smbpasswd -a username password' for each user. Keep all three usernames and passwords the same and save yourself a whole lot of hair.

Is it absolutely necessary to have the same username and password on my Ubuntu server and Windows XP PCs? I do not think so because I have successfully shared my Ubuntu server files before. I also have a different samba username and password and it connects fine before the current error occurred.

---

### Post by UbuNewbie123 on 2007-09-24
I fixed my problem. It was not an issue with Samba but my Windows ZoneAlarm firewall. I just installed ZoneAlarm and I forgot to add the IP address of the Ubuntu server to my trusted zone. I also had to restart my Windows PC to get it going after making the change above.

---

