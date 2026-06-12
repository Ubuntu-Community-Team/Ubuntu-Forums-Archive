---
title: "What privileges must a user have to access a Samba share"
date: 2011-12-02
forum: Server Platforms
---

### Post by FiftyOneFifty on 2011-12-02
I've installed Ubuntu Server 10.04 to  build a home server.  I've created shared Samba folders in the home  folder of the user I created during installation (hereafter referred to  as FirstUser).  Thinking better of using a user name and password that  can be elevated just to access shares from a client machines, I created  another user called "Shares".  I made Shares a member of the FirstUser  group, so it would have rwx access to files in /home/FirstUser, but  Shares is not a member of admin so it can't run sudo.  I also added  Shares to plugdev since /home is mapped to an external drive.

---

### Post by Morbius1 on 2011-12-02
This is how I understood your post:

* You created a folder in your home directory that you want to share. Let's call it "Shared" So at that point you have a folder at:

** /home/firstuser/Shared**

With permissions of:
** drwxr-xr-x firstuser firstuser**

* Then you created another user named: shares and included him in firstusers group.
> I made Shares a member of the FirstUser group, so it would have rwx access to files in /home/FirstUser.One does not follow from the other. Although firstuser can access the folder because he is the owner, other members of the firstuser group can only read. If you want other members of the firstuser group to have write access to the share itself you need to change the permissions on the shared directory:
```
sudo chmod 0775 /home/firstuser/Shared
```Now the permissions on the shared directory are:
[B] drwxrwxr-x firstuser firstuser

[/B]This will allow "shares" to add, delete, and even rename individual files within the "Shared" directory but it won't allow them to actually edit individual files because they have permissions of 644 (rw-r--r--). It's not clear from your post if by "write" you mean write to the "Shared" directory or write to an individual file within "Shared". It's also not clear if you want firstuser to have write access to any files saved by user "shared".

---

### Post by gordintoronto on 2011-12-02
If all you want to do is set up a file server, it's about 500% easier if you install Ubuntu Desktop. Then you can use Nautilus to share folders.

Ubuntu Server is nice for setting up a "headless" computer running a busy web site, but there's a huge productivity hit for anything else.

---

