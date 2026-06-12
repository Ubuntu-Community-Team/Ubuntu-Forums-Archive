---
title: "System Program Problem detected - Report Problem"
date: 2016-11-20
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2016-11-20
For several .iso's after every Zesty boot I get one or two or three "System Program Problem" on both my pc's.  Yes I select: Report problem, I have no clue what this is or if I'm the only one?

Thanks, Jerry

---

### Post by cariboo on 2016-11-20
Many of the errors you run into, get sent to [https://errors.ubuntu.com/](https://errors.ubuntu.com/), without any intervention by the user. To check what errors your system is creating, have a look in /var/crash.

---

### Post by Smask on 2016-11-21
These two?

smbd crashed with SIGABRT in talloc_get_size()
nmbd crashed with SIGABRT in talloc_get_size()

I get the smbd one twice and the nmbd once every time I reboot my computers. The error dialogs popup even before the desktop loads. Only the last smbd crash gets to the authentication bit, I click on the send button and no lookup on Launchpad. Is apport broken? I couldn't find smbd on errors.ubuntu.com, unless I filter on 17.04.

---

### Post by jerrylamos on 2016-11-21
Last one in /var/crash is

_usr_sbin_smbd.0.crash

Does that mean anything to anyone?

Thanks

---

### Post by dino99 on 2016-11-21
That's what happen with each cold boot; and is reported in the background:
[https://errors.ubuntu.com/?release=Ubuntu%2017.04&period=day](https://errors.ubuntu.com/?release=Ubuntu%2017.04&period=day)      As you can see 'samba' trust the top list.

As usual 'apport' is deactivated in the early days/weeks of a new release project (devs does not want being flooded by useless reports; as their attention is already catched by the reports above)

---

### Post by Smask on 2016-11-21
> **dino99 said:**
> As usual 'apport' is deactivated in the early days/weeks of a new release project (devs does not want being flooded by useless reports; as their attention is already catched by the reports above)

Ah, OK. I started to wonder since I've getting these errors for about two weeks now

---

### Post by mc4man on 2016-11-21
Typically when choosing the 'report' option on these popups there would be an apport .uploaded file created in /var/crash for that crasher. Then one shouldn't be bothered again.
That doesn't appear to be happening. 

Also, at least here, many actions are prevented for at least 60 sec.'s or so after login, certainly those that require policykit & related.
(i.e. - boot up, log in & try to immediately  open synaptic from Dash or launcher, won't happen. Same for any other polkit functions & likely 'reporting' root owned crashers.

---

### Post by corradoventu on 2016-12-03
I have the same 2 crash. I choose 'report' in the popub but In /var/crash both _usr_sbin_nmbd.0.uploaded and _usr_sbin_smdb.0.uploaded are empty. If I try to start samba I have:
```
corrado@corrado-zesty2:~$ sudo service samba start
[sudo] password for corrado: 
Failed to start samba.service: Unit samba.service is masked.
corrado@corrado-zesty2:~$ sudo systemctl unmask samba.service
corrado@corrado-zesty2:~$ sudo service samba start
Failed to start samba.service: Unit samba.service is masked.
corrado@corrado-zesty2:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version (2:4.4.5+dfsg-2ubuntu6).
0 upgraded, 0 newly installed, 0 to remove and 108 not upgraded.
corrado@corrado-zesty2:~$ inxi 
CPU~Dual core Intel Core i3-4130 (-HT-MCP-) speed/max~802/3400 MHz Kernel~4.9.0-1-generic x86_64 Up~1:08 Mem~998.4/7862.7MB HDD~1000.2GB(1.6% used) Procs~232 Client~Shell inxi~2.3.4  
corrado@corrado-zesty2:~$ uname -a
Linux corrado-zesty2 4.9.0-1-generic #2-Ubuntu SMP Mon Nov 14 21:43:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-zesty2:~$
```

---

### Post by zika on 2016-12-03
> **corradoventu said:**
> I have the same 2 crash. I choose 'report' in the popub but In /var/crash both _usr_sbin_nmbd.0.uploaded and _usr_sbin_smdb.0.uploaded are empty. If I try to start samba I have:
```
corrado@corrado-zesty2:~$ sudo service samba start
[sudo] password for corrado: 
Failed to start samba.service: Unit samba.service is masked.
corrado@corrado-zesty2:~$ sudo systemctl unmask samba.service
corrado@corrado-zesty2:~$ sudo service samba start
Failed to start samba.service: Unit samba.service is masked.
corrado@corrado-zesty2:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version (2:4.4.5+dfsg-2ubuntu6).
0 upgraded, 0 newly installed, 0 to remove and 108 not upgraded.
corrado@corrado-zesty2:~$ inxi 
CPU~Dual core Intel Core i3-4130 (-HT-MCP-) speed/max~802/3400 MHz Kernel~4.9.0-1-generic x86_64 Up~1:08 Mem~998.4/7862.7MB HDD~1000.2GB(1.6% used) Procs~232 Client~Shell inxi~2.3.4  
corrado@corrado-zesty2:~$ uname -a
Linux corrado-zesty2 4.9.0-1-generic #2-Ubuntu SMP Mon Nov 14 21:43:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-zesty2:~$
```Is this 17.04? 
You have to commit yourself to use only SystemD. You are using UpStart and SystemD at the same time. Not that it will make a problem but a big part of UpStart is being removed form ubuntu and only relicts are there... If You want to reinstall Samba You should use reinstall switch to trigger that. Did You try to start Samba from rc.local? It is not quite contemporary to SystemD but that should work and looks to me as the fastest way to get it running... Since I do have very long living installs that are up to the latest in daily and some few steps more I do not have hands-on experience with daily of 17.04.

---

### Post by Yellow Pasque on 2016-12-05
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1639962](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1639962)

---

### Post by corradoventu on 2017-01-23
@zika: You mean the commamd 'sudo service samba start' is for UpStart? what command should i use for SystemD? Thanks.

---

