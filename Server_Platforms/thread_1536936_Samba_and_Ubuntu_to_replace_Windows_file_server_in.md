---
title: "Samba and Ubuntu to replace Windows file server in active directory"
date: 2010-07-22
forum: Server Platforms
---

### Post by smmj on 2010-07-22
Hello,

We have a couple of Windows file servers that just share files. It is all they do. We'd like to use Ubuntu on two replacement servers allowing Windows XP and Windows 7 clients to access the files. 

Our network is active directory based due to Exchange and homegrown .NET apps, so it is important that active directory is used to authenticate the clients. Samba doesn't need to be a pdc or bdc, but provide pass through authentication. 

I understand that Samba can communicate with active directory through security-ads and security-domain. 

 Here are my questions to see if I should proceed:

1) Folder permissions: If we move all our files to the Ubuntu server how do we set folder permissions and will we see the active directory accounts when we do this?

2) Skipping ubuntu accounts: I know the domain and ads allow you to skip creating ubuntu accounts, right? If not, how do you keep the passwords synchronized?

3) Easiest way? Is there a very easy way to pull this off that I've missed? My goal is to eliminate the Windows based file servers while ensuring the admin part of it is as easy as possible. 

To date I've been able to get the sharing to work with an ubuntu account mirroring the active directory account. I've been able to get Samba to talk to the pdc, but not successfully through domain security. ADS security was a complete cluster with winbindd. Samba and Kerberos worked, but I couldn't get winbindd to connect. lol

If you have experience doing this I appreciate your sharing the experience. 

Thanks in advance.

---

### Post by rslrdx on 2010-07-23
Although its been a few months, i tried some of this things , and i think i can sugest to you with quite a bit of confidence that your best shot is actually freenas !

its really symple to install, use, opensource, already has some tools to integrate with windows, and its all done through a webinterface. not to mention that its rock solid and doesnt eat up your resources.

1) Folder permissions: If we move all our files to the Ubuntu server how do we set folder permissions and will we see the active directory accounts when we do this?

if i'm not mistaken, freenas would use whatever set of permissions the domain user had to his files etc etc...


2) Skipping ubuntu accounts: I know the domain and ads allow you to skip creating ubuntu accounts, right? If not, how do you keep the passwords synchronized?

again, freenas just uses the domain users, so no need to create users on both...


3) Easiest way? Is there a very easy way to pull this off that I've missed? My goal is to eliminate the Windows based file servers while ensuring the admin part of it is as easy as possible. 

This was also my goal, specially because some of the techs I had at work didnt really know much about administrating servers, and haveving something that pretty much works by clicking Next>>Next>>Finish made it all that symple. 

It feels like you are configuring a home router but with lots of advanced options. 

Dont get me wrong, i love ubuntu, but it seems to me that you are looking more for a easy and practical way to manage something at work rather then spend a few weeks working scripts to get samba to work right.

EDIT: The one thing about freenas that concernd me was that it doesnt use EXT3 or EXT4, it uses UFS, freeBSD native formating, which to me meant that if the system crashed, i could not just grab the HD and read data off of it with a live linux cd. Like, ubuntu doesnt suport that formating and it cant read it. You would need another freenas box to mount it on or some freebsd box.

---

### Post by rslrdx on 2010-07-23
another option you have if openfiler, while i have done little things with it (meaning: no production use) there are some idications that it works even better with AD

here is a link to help. not my documentation btw.
[http://dwimorberg.hopto.org/usr/openfiler/index.html](http://dwimorberg.hopto.org/usr/openfiler/index.html)

---

### Post by smmj on 2010-09-10
Hey guys ... I wanted to let you know FreeNAS was the best solution for this. 

There were a couple of things we learned going through this:

1) Active directory integration through Samba will not work if the admin password has dollar signs in it. lol

2) When you create the shares for use on a Linux/freenas box you need to create them from the PDC/BDC logged in as the domain admin. So, we remoted into our PDC and then mapped a drive over to the freenas box to create directories to use for shares. Why? Well, the permissions. If we tried to create the directories directly on the freenas box, active directory didn't like it. 

3) Permissions. Ugh. I couldn't find any method to move permissions from the windows servers to the freenas box. I had extended attributes on, etc. No go at all. If we started from scratch, no problems, but we couldn't find a way to copy existing permissions.

---

