---
title: "I want to set quotas for each user on my server"
date: 2009-07-25
forum: Server Platforms
---

### Post by husskii on 2009-07-25
Hi I just got a new server and set 4user accounts on it,
I want to set quotas for each user so that they cant over kill the server..
is there a command I can use thru putty or another way, to create quotas on a unbuntu..

Im using Ubuntu 8.04 (hardy) advice or a commend would be most appreciated. :)

I found the following command but Im not sure if its the right commend..
xfs_quota  [  -x ] [ -p prog ] [ -c cmd ] ... [ -d project ] ... [ path... ]

if it is correct I dnt know were to put the username etc...

thanks in advance :D

---

### Post by bartos on 2009-07-26
What are the user accounts for? Ftp, Samba or other
Just so we know how best to answer you.

---

### Post by husskii on 2009-12-05
all solved, i learnt of a new tool called webmin lol..
no setting hdd quotas hasnt been easier...

for anyone else with the same problem, just do the following.

1: install webmin 
wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.490_all.deb) 

2: sudo dpkg -i webmin_1.490_all.deb

3: apt-get install quota quotatool

4: open /etc/fstab and find where it mounts /home

5: then nano /etc/fstab

6: now you see /dev/md7 /home ext3 line, change that line so it looks like this 
/dev/md7 /home ext3 defaults,usrquota,grpquota 1 2 /dev/sda5 swap swap defaults 0 0 [preserve the spaces] then save.

7: now go into /home & type, cd /home

8: in your home directory, type,   touch quota.user quota.group

9: now type in,  chmod 600 quota.*

10: then type in,    mount -o remount /home

11: now log into webmin & search 'quota' you should see a result called "Disk Quotas"

12: click on it and press enable quotas on /home

13: now u can create hdd quotas for each user... ;)

---

