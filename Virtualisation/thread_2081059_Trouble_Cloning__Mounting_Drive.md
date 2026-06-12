---
title: "Trouble Cloning / Mounting Drive"
date: 2012-11-05
forum: Virtualisation
---

### Post by Greg Roberts on 2012-11-05
Hi
 
I have a vmware ubuntu v9.1 VM. It has a 2nd /var drive of 120G. It uses the LVM2 format and type Ext4 . This drive is fully allocated even though only 19G is in use.
 
I want to reduce the disk size to 25G, I created a new Ext4 drive and copied the /var to the /new_var 
 
I then want to create the new drive the new /var and then delete the 120G drive. 
 
However, after adjusting the area names and ftstab, a reboot does not work...
 
I get issues reported with /var/lock, /var/lock 
It seems like there is some artefacts in these tied to the old drive ? 
 
>> I am a novice here, but if someone knows the simple missing step, i would appreciate it.
>> I am not sure if the new Ext4 area needs to be LVM2, i.e. part of /dev/mapper/xxx
OR
Ubuntu will be completely happy looking for /var as long as it is mounted, whether on the old /dev/mapper/xxx or /dev/sdc1
 
This is the link to the screen pictures of what is happening.
 
[https://skydrive.live.com/redir?resid=8539AF5388FDFCBE!188&authkey=!AHfBQEI6N1CeO8Q](https://skydrive.live.com/redir?resid=8539AF5388FDFCBE!188&authkey=!AHfBQEI6N1CeO8Q)
 
Many thanks

---

