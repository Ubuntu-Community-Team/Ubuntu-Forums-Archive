---
title: "virtualbox USB not working"
date: 2011-04-23
forum: Virtualisation
---

### Post by noworldorder on 2011-04-23
So I got the USB working on virtualbox. I am using Ubuntu 10.10 and have an XP virtual machine.  The USB was working fine but now it is not.  The USB hardware shows up under Devices but it is greyed out.  This is confusing as I have changed nothing on my system.  I have rebooted and checked the USB settings in virtualbox and it should work.

Help...  thanks...

---

### Post by shaoxiao on 2011-04-23
try this;then reboot

```
if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi
```

---

### Post by GridLynx on 2011-04-23
> try this;then reboot

if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi     Hey there Shao

I am having the same problem as the creator of the post... if i hover the cursor ove the USB devices it will say unavaiable.. but.. if i connect a device which drivers are not recognized by Ubuntu, i can use it freely on the Guest... any idea?

---

### Post by noworldorder on 2011-04-23
did I do this right?

> chris@chris-HP-G60-Notebook-PC:~$ if [ "`grep vboxusers /etc/group|grep $USER`" == "" ] ; then sudo usermod -G vboxusers -a $USER ; fi
chris@chris-HP-G60-Notebook-PC:~$ 

there was no change

---

### Post by shaoxiao on 2011-04-23
> **noworldorder said:**
> did I do this right?



there was no change
Yes, then reboot and see if it works

---

### Post by noworldorder on 2011-04-23
> Yes, then reboot and see if it works

thanks but no change after reboot

---

### Post by shaoxiao on 2011-04-23
> **GridLynx said:**
> Hey there Shao

I am having the same problem as the creator of the post... if i hover the cursor ove the USB devices it will say unavaiable.. but.. if i connect a device which drivers are not recognized by Ubuntu, i can use it freely on the Guest... any idea?
 Hi GridLynx, your problem sounds weird .I never face this situation before. :(

---

### Post by shaoxiao on 2011-04-23
> **noworldorder said:**
> thanks but no change after reboot
:confused: noworldorder, check this out. System->Admin-> Users and Groups-> Manage Groups
and see if your account name is in vboxusers and disk group. Don't worry, i faced this problem before.
It must be caused by the permission problem if you have installed the extension pack.

---

### Post by shaoxiao on 2011-04-23
> **noworldorder said:**
> thanks but no change after reboot
It is my fault. Try this command instead.
```
sudo usermod -aG vboxusers <your username>
```
replace <your username> with your login name

ps: editing the group should use super authorith.  i am sorry for my poor English.

---

### Post by noworldorder on 2011-04-23
> It is my fault. Try this command instead.
sudo usermod -aG vboxusers <your username>
replace <your username> with your login name

thanks but no luck

---

### Post by shaoxiao on 2011-04-23
[FONT=monospace]Can you post the output of the command below? BTW your virtualbox version? Mine is 4.04
```
grep -E "vboxusers|disk" /etc/group
```
[/FONT]

---

### Post by noworldorder on 2011-04-23
Could any of the following be the cause?

Also, I added and deleted a couple virtual machines today - could that be related?

[IMG]http://img821.imageshack.us/i/screenshot1sx.png/[/IMG][IMG]http://img268.imageshack.us/i/screenshot3pxz.png/[/IMG]
*[IMG]http://img215.imageshack.us/i/screenshot1ze.png/[/IMG](trying to fugure out how to upload images)*
[IMG]http://img827.imageshack.us/i/screenshot2sb.png/[/IMG]

[IMG]http://img268.imageshack.us/i/screenshot3pxz.png/[/IMG]

---

### Post by shaoxiao on 2011-04-24
> **noworldorder said:**
> Could any of the following be the cause?

Also, I added and deleted a couple virtual machines today - could that be related?

[IMG]http://img821.imageshack.us/i/screenshot1sx.png/[/IMG]

[IMG]http://img827.imageshack.us/i/screenshot2sb.png/[/IMG]

[IMG]http://img268.imageshack.us/i/screenshot3pxz.png/[/IMG]
I don't think so. noworldorder look this link. It may help.
[http://forums.virtualbox.org/viewtopic.php?f=7&t=39231&start=0&sid=1a0bf3a021d222a40116939cfb11da3f](http://forums.virtualbox.org/viewtopic.php?f=7&t=39231&start=0&sid=1a0bf3a021d222a40116939cfb11da3f)

---

### Post by dcstar on 2011-04-24
So what do they say in the Virtualization forum which is specifically for issues like this?

---

### Post by shaoxiao on 2011-04-24
> **dcstar said:**
> So what do they say in the Virtualization forum which is specifically for issues like this?
Hi dcstar, I think the problem they discuss is as same as this thread. Their methods is more advanced. But the method i think that really helped me is just i posted above.

---

### Post by noworldorder on 2011-04-24
chris@chris-HP-G60-Notebook-PC:~$ grep -E "vboxusers|disk" /etc/group
disk:x:6:
vboxusers:x:1001:chris

---

### Post by shaoxiao on 2011-04-24
> **noworldorder said:**
> chris@chris-HP-G60-Notebook-PC:~$ grep -E "vboxusers|disk" /etc/group
disk:x:6:
vboxusers:x:1001:chris
err.. i found some guys also suggest to add account to disk(I don't know why) so
```
sudo usermod -aG disk chris
```
Then reboot or logout.

---

### Post by noworldorder on 2011-04-24
> noworldorder, check this out. System->Admin-> Users and Groups-> Manage Groups
and see if your account name is in vboxusers and disk group.

Thanks but this was not the issue

I am not sure if there could be a connection but today I added and removed 2 virtual machines.  This is the only thing I have done since the time USB was working properly.

---

### Post by noworldorder on 2011-04-24
> So what do they say in the Virtualization forum which is specifically for issues like this?

I missed that forum - is there a way to move this thread over there?

---

### Post by shaoxiao on 2011-04-24
> **noworldorder said:**
> Thanks but this was not the issue

I am not sure if there could be a connection but today I added and removed 2 virtual machines.  This is the only thing I have done since the time USB was working properly.
Good luck, noworldorder

---

### Post by noworldorder on 2011-04-24
> Good luck, noworldorder

LOL that's it?  I usually post in Absolute Beginner.  I am depending on you guys  :)

---

### Post by lisati on 2011-04-24
*Thread moved to **Virtualization**.*

---

