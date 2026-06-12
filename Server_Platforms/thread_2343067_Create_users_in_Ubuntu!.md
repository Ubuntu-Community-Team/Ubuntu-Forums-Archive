---
title: "Create users in Ubuntu!"
date: 2016-11-12
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-12
Hi


Just installed Ubuntu 16.04 LTS on my machine with the intent to use as a file and media server for home purposes. This has 3 disks - one SSD with OS on it and 2 HDD's one dedicated to media files and one dedicated to data files.

My understanding of Ubuntu/Linux user and Samba user is quite limited. I am assuming here that they are both different and sever different functions. I am trying to understand how to create user accounts so that these users can log in to a Samba share on the Ubuntu machine from their Windows machines.

My understanding is that I can create users with either the "adduser" or "useradd" commands. Either way, when I create an user account and assign them a password, I, as the administrator, will know their password, which I believe I shouldn't.  So,how do I create a valid Ubuntu user account so that only the user knows their password to connect to the server as a valid user and then be able to access their home directories and other directories if they have been granted permissions to do so. Also, preferably they should have the ability to change their login passwords at will and be able to continue to connect to the Ubuntu machine and access the relevant Samba shares to which they have been granted access.

Just to keep the post short and relevant, I haven't provided the share details yet but will do so once I know how to create users so that the above need is met.


Best regards


Deeapk

---

### Post by wildmanne39 on 2016-11-12
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-11-12
If a user logs in with ssh session, they can change their password with:
```
passwd
```

If you don't want them to log in using ssh command line, I don't know of another way to have them change their password unless you implement something like AD or LDAP. Besides, knowing or not their password doesn't matter much since you as administrator have total control over their files and their shares...

The samba user is different from the linux user and there is a way to sync the passwords, so that they have the same password without creating the same user twice. You should be able to add the linux user to samba users with something like:
```
sudo smbpasswd -a <username>
```

---

### Post by agarwaldvk on 2016-11-12
Hi


Just to let you know, the version of Ubuntu that I have used is not the server edition - it is the Desktop version - does it also then needs to be in the "Server Platform" section.


Best regards


Deepak

---

### Post by wildmanne39 on 2016-11-12
Given what you want to set your computer up to do I think this is probably the best place for it.

---

### Post by agarwaldvk on 2016-11-12
Hi darkod

Thanks for your response.

Do I not need to first create a Linux/Ubuntu user using the following command :-

sudo adduser test
mypasswd
mypasswd

and then create the Samba user (probably using the same username and password) using the appropriate commands, which I do not know yet, and then link the two.

Or doing just this :-
sudo smbpasswd -a test
mypasswd
mypasswd


will create a Linux/Ubuntu user and also make it a Samba user and then link  the two with the same passwd.

Whichever way, once that happens, are their access to Samba shares (I will provide the details of the shares later as its best to have one issue addressed per post - so is my understanding) dictated by the share specifications or user profile details?


Best regards


Deepak

---

### Post by darkod on 2016-11-13
Yes, first create the linux user with adduser, and then link it to the samba user with smbpasswd. I'm not sure if the smbpasswd will ask you to enter the passwords again, you will see...

User access to samba shares will be controlled by the options you set in smb.conf for the shares.

---

### Post by agarwaldvk on 2016-11-13
Hi darkod


Thanks a lot. That worked. I did first create a linux user with the "adduser" command - didn't ask for password.

Then added this user to Samba user by "smbpasswd -a <thisusername> - required password.

All good!

I will now create new post(s) - following the "1  post per issue" theme -  to seek help for defining shares and assigning share permissions.


P.S. Whilst I have marked this thread as 'Solved', could you please point to references to help me get a little better understanding of the "implementing something like AD or LDAP" - just for my academic interest.


Best regards


Deepak

---

### Post by darkod on 2016-11-13
Something like this to start with:
[https://help.ubuntu.com/lts/serverguide/network-authentication.html](https://help.ubuntu.com/lts/serverguide/network-authentication.html)

There are many tutorials for creating AD with Samba. Linux servers can also be joined to AD created by Windows.

---

