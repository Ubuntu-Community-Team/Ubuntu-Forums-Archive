---
title: "Ldap/Samba problem mounting user home dirs"
date: 2009-09-18
forum: Server Platforms
---

### Post by kesai on 2009-09-18
Hello there :) 

I have recently begun building a small computer network and after much reading I have decided to go with ubuntu for a variety of reasons. 

My past experiences have been with Fedora but that was a while back. 

So Server is running Ubuntu 9.04 (x64) Server and Clients are running Ubuntu 9.04 (x86) Desktop.

I have the ldap and samba successfully installed on the server and the clients are successfully authenticating using the server. My first problem after the setup of both was that the new users in the ldap had no home directory and pam would not create one for them. 
After a little search this was solved by adding some lines to the 
/etc/pam.d/common.session :
> session required        pam_unix.so
session required        pam_mkhomedir.so skel=/etc/skel/
session optional        pam_ldap.so
session optional        pam_foreground.so

This worked well, but of course its not a mount of a home dir 
on the server.

I then installed libpam-mount on the client machines and used this 
code in the pam_mount.conf.xml :

> <volume  user=”uid%(USER)&#8243;  fstype=”smbfs” noroot=”1&#8243; server=”192.168.1.5&#8243;  
path=”share” mountpoint=”/home/%(USER)” />

Although this tried to mount something when I logged in one of the
it failed. I then tried to mount by hand from the client using : 
mount -t smbfs -o username=username //192.168.1.5/home/username /home/username

it comes up with error -11, Resource temporarily unavailable. 

I am inexperienced when it comes to linux although I have used it before
so please excuse any horrendous errors I might have done. If anyone has an 
idea of what I have been doing wrong, or a pointer to the right direction
I would be much obliged.

Thanks for your time.

---

### Post by openfly on 2009-09-18
Hey kesai, you might want to try pulling a stack trace on the mount process to see where exactly it's running into the resource unavailability issue.  To do this try:

strace -o /tmp/mount.log <mount command here>

strace is a phenomenal tool for diagnosing these sorts of issues.

---

### Post by kesai on 2009-09-18
Thanks openfly. I ll give it a try first thing in the morning.

---

### Post by jordih on 2009-09-22
> **kesai said:**
> Hello there :) 

I have recently begun building a small computer network and after much reading I have decided to go with ubuntu for a variety of reasons. 

My past experiences have been with Fedora but that was a while back. 

So Server is running Ubuntu 9.04 (x64) Server and Clients are running Ubuntu 9.04 (x86) Desktop.

I have the ldap and samba successfully installed on the server and the clients are successfully authenticating using the server. My first problem after the setup of both was that the new users in the ldap had no home directory and pam would not create one for them. 
After a little search this was solved by adding some lines to the 
/etc/pam.d/common.session :


This worked well, but of course its not a mount of a home dir 
on the server.

I then installed libpam-mount on the client machines and used this 
code in the pam_mount.conf.xml :



Although this tried to mount something when I logged in one of the
it failed. I then tried to mount by hand from the client using : 
mount -t smbfs -o username=username //192.168.1.5/home/username /home/username

it comes up with error -11, Resource temporarily unavailable. 

I am inexperienced when it comes to linux although I have used it before
so please excuse any horrendous errors I might have done. If anyone has an 
idea of what I have been doing wrong, or a pointer to the right direction
I would be much obliged.

Thanks for your time.

Hi Kesai,

Try this:

```
sudo echo auth requisite pam_mount.so >> /etc/pam.d/common-auth
sudo echo session optional pam_mount.so >> /etc/pam.d/common-session
```

---

### Post by kesai on 2009-09-22
Thanks for your help. 

After much reading on forums, guides, wikis I failed to find a solution to my problem. I could see with smbclient -L xx.xx.xx.xx that samba was sharing home dirs, but alas mounting them was not possible. It is very likely I screwed up somewhere with the user uids between samba and the system. 

I managed to solve my problem using NFS. Mounting the whole of the /home directory of the server onto the client pcs. Using ldapscripts I get the right uids for the right directories and it works fine. 

Thanks to both of you for trying to help, much appreciated :)

If I have to install windows machines I guess i ll be back :P

---

### Post by openfly on 2009-09-22
kesai if you ever want to lose your mind integrating a linux environment with windows clients...

take a look at andrew filesystem for windows.  and kerberized nfs...  and cross realm trusts with AD...

>=P

---

