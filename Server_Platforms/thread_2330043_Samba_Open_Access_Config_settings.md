---
title: "Samba Open Access Config settings"
date: 2016-07-07
forum: Server Platforms
---

### Post by Altin on 2016-07-07
Hi

I'm running Ubuntu Server 14.04 and have installed Samba to use it as a file server. I've set my /etc/samba/smb.conf file as below, but find that when I browse to \\192.168.1.100\files using Windows File Explorer, I get a pop up box asking me for a username and password. If I enter the name of the user on the Ubuntu machine, and not the password, I can access the share. 

I want to have this share set up as an open access share, without needing users to log on. I have run 'chmod -R 777 /srv' in case permissions were the problem, but the issue persists. How can I stop this pop up happening? My smb.conf file is:

[files]
comment = Network Files
path = /srv
writeable = yes
guest only = yes
guest ok = yes
create mask = 0777
directory mask = 0777
browseable = yes
public = yes

---

### Post by howefield on 2016-07-07
Thread moved to the "*Server Platforms*" forum for a better fit.

---

