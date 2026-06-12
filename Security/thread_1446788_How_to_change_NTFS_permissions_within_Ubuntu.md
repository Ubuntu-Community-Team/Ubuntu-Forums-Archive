---
title: "How to change NTFS permissions within Ubuntu?"
date: 2010-04-04
forum: Security
---

### Post by Resilldoux on 2010-04-04
Hi there,

I was just wondering, how does one change permissions on an NTFS partition within Ubuntu? I noticed chmod and chown didn't do the trick, so I decided to use ACLs, but that failed as well...

Below is the line I added to **/etc/fstab** (notice the "_,acl_"). The partition mounted just fine after a reboot and I was still able to read and write files on the partition.
```

/dev/sdb5       /media/DATA     ntfs-3g defaults,acl    0       0
```I installed acl (sudo apt-get install acl) and tried to create an ACL using the this command: ```
setfacl -m u:resilldoux:rwx /media/DATA/Music/Resilldoux
```But I keep getting this message: ```
setfacl: /media/DATA/Music/Resilldoux: Operation not supported
```What am I doing wrong, or is Ubuntu also incapable of creating ACLs on NTFS partitions? I'd really like to configure permissions on NTFS partitions within Ubuntu. I'd rather not format my partitions to ext4 since I also would like to access these partitions in Windows.

---

### Post by bodhi.zazen on 2010-04-04
> **Resilldoux said:**
> Hi there,

I was just wondering, how does one change permissions on an NTFS partition within Ubuntu? I noticed chmod and chown didn't do the trick, so I decided to use ACLs, but that failed as well...

Below is the line I added to **/etc/fstab** (notice the "_,acl_"). The partition mounted just fine after a reboot and I was still able to read and write files on the partition.
```

/dev/sdb5       /media/DATA     ntfs-3g defaults,acl    0       0
```I installed acl (sudo apt-get install acl) and tried to create an ACL using the this command: ```
setfacl -m u:resilldoux:rwx /media/DATA/Music/Resilldoux
```But I keep getting this message: ```
setfacl: /media/DATA/Music/Resilldoux: Operation not supported
```What am I doing wrong, or is Ubuntu also incapable of creating ACLs on NTFS partitions? I'd really like to configure permissions on NTFS partitions within Ubuntu. I'd rather not format my partitions to ext4 since I also would like to access these partitions in Windows.

NTFS does not support linux permissions or acl, if you want these features use a linux filesystem such as ext3/4 .

To set permissions on a ntfs partition use uid=xxx, gid=yyym,umask=zzz, and similar options, see man mount, under the ntfs section.

These permissions are then set to ALL files and directories and can not be set in they way you are wanting.

---

### Post by Resilldoux on 2010-04-04
> **bodhi.zazen said:**
> NTFS does not support linux permissions or acl, if you want these features use a linux filesystem such as ext3/4 .

To set permissions on a ntfs partition use uid=xxx, gid=yyym,umask=zzz, and similar options, see man mount, under the ntfs section.

These permissions are then set to ALL files and directories and can not be set in they way you are wanting.

Thanks for replying on such a short notice.
That's a bummer, so it seems I'll just have to live with it. :roll:

---

### Post by TheMusicGuy on 2010-05-18
> **bodhi.zazen said:**
> NTFS does not support linux permissions or acl, if you want these features use a linux filesystem such as ext3/4 .

To set permissions on a ntfs partition use uid=xxx, gid=yyym,umask=zzz, and similar options, see man mount, under the ntfs section.

These permissions are then set to ALL files and directories and can not be set in they way you are wanting.

That's not completely true.

While NTFS does not support *Linux* ACLs or permissions, it *does* have its own version of those features, and those can be utilized by Linux when the correct packages are installed and configured correctly--however, I'm still experimenting with this and have not yet been successful.

According to [this article]("http://pagesperso-orange.fr/b.andre/permissions.html"), there is a specification to allow Linux to make use of NTFS ACLs. It requires that you create a special file called **/(NTFSPART)/.NTFS-3G/UserMapping** , where (NTFSPART) is the location of the root directory of your NTFS partition mounted in the file system.

There are other details that need to be completed as well, but I suggest you read the article for more information.

---

### Post by bodhi.zazen on 2010-05-18
> **TheMusicGuy said:**
> That's not completely true.

I am aware of the supplemental information you are adding. This is something that is in development, but has not been implemented as of yet.

Thus, the information I posted is correct, your information is supplemental.

---

### Post by HermanAB on 2010-05-19
Yup, the only solution at this point is to install XP in a VM.

---

### Post by drewsus on 2010-06-06
> **HermanAB said:**
> Yup, the only solution at this point is to install XP in a VM.

How is that so? I can't change the permissions for a *shared* NTFS drive/folder using a Linux *host* and XP *guest* in VirtualBox. It behaves the exact same way as if I used *chmod* in Ubuntu on the same partition. 
Unless you can enlighten me, for which I will be very greatful. 

Drewsus

---

### Post by bodhi.zazen on 2010-06-06
> **drewsus said:**
> How is that so? I can't change the permissions for a *shared* NTFS drive/folder using a Linux *host* and XP *guest* in VirtualBox. It behaves the exact same way as if I used *chmod* in Ubuntu on the same partition. 
Unless you can enlighten me, for which I will be very greatful. 

Drewsus

What are you wanting to do ?

In the first post of this thread I showed you how to set the permissions of a NTFS partition.

NTFS does NOT support Linux permissions, for that you need to use a linux native file system.

NTFS does have a system of setting ACL, as suggested by TheMusicGuy. To use those features yo need to install Windows somewhere and Linux support for such permissions is, IMO, experimental at best.

---

### Post by drewsus on 2010-06-08
> **TheMusicGuy said:**
> That's not completely true.

While NTFS does not support *Linux* ACLs or permissions, it *does* have its own version of those features, and those can be utilized by Linux when the correct packages are installed and configured correctly--however, I'm still experimenting with this and have not yet been successful.

According to [this article]("http://pagesperso-orange.fr/b.andre/permissions.html"), there is a specification to allow Linux to make use of NTFS ACLs. It requires that you create a special file called **/(NTFSPART)/.NTFS-3G/UserMapping** , where (NTFSPART) is the location of the root directory of your NTFS partition mounted in the file system.

There are other details that need to be completed as well, but I suggest you read the article for more information.

While setting up a home theatre system for a friend with various unique requirements I found that I needed to be able to have read/write permission on external and internal NTFS HDD amongst other things (ie. Media scaping). 
Setting this up following TheMusicGuy's suggestions proved to be fairly simple. 
As the article from NTFS-3G's page details, a file named "UserMapping" has to be created in a hidden folder called ".NTFS-3G" placed in the root directory of the NTFS hard drive you want to have permissions for. 

The article suggests the use of a small utility called ***usermap*** found here: [http://pagesperso-orange.fr/b.andre/usermap.html](http://pagesperso-orange.fr/b.andre/usermap.html)
Examples are given, but essentially you have to unpack and run the program usermap.exe in command prompt within WINDOWS. 
This will generate the content of "UserMapping" mentioned above with the exception that you have to manually enter the user and group UIDs. 
Here is mine after manually editing it: 
```
# Generated by usermap for Windows, v 1.1.2
# For Windows account "Administrator" in domain "EXPERIEN-BA7F32"
# Replace "user" and "group" hereafter by matching Linux login
1000::S-1-5-21-448539723-706699826-839522115-500
:1000:S-1-5-21-448539723-706699826-839522115-513
```
The forth line is for the user and the fifth is for the group. 
Now, when you mount your NTFS drive it will actually mount it if you had given all the contents "chmod -R 777" to **root**.
This is easily changed by these two commands applied to whatever folders you like:
```
sudo chown -R 1000 <desired folder>
sudo chgrp -R 1000 <desired folder>
```
where, of course **<desired folder>** is the folder that you want to change user and group ownerships recursively.

From here, you can use *chmod* like you would normally expect. 

I'm sure that there is a bit of tweaking I can do (so it doesn't initial set ownership to root), but I am on time constraints at the moment and this works peachy keen for me for now and I wanted to share while I am scraping media. 

If you have any questions feel free to ask as I wrote this fairly fast. 

Regards, 
Drewsus

ps - its also encouraged to READ **[>> the article <<]("http://pagesperso-orange.fr/b.andre/permissions.html")** and the usermap examples. Knowledge is power!

---

