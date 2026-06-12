---
title: "Folder permissions"
date: 2017-08-14
forum: Server Platforms
---

### Post by marta2 on 2017-08-14
Hi, I'm new in Ubuntu. I've got a problem with the permissions of some folders and I can't understand what happens.
I've got the administrator group with 2 users: administrator and user
I've got another group: costumer
I've added these 3 users: administrator, user and costumer to samba

The permissions of the folders are these:
administrator administrator    /srv/samba/docs: drwxrwxr-x
administrator administrator    /srv/samba/docs/costumer:  drwxrwxr--
administrator administrator    /srv/samba/docs/costumer/files: drwxrwxrwx
administrator administrator    /srv/samba/docs/costumer/files_company: drwxrwxr--
administrator administrator    /srv/samba/docs/company: drwxrwx--

I want:
- administrator and user: do what they want where they want
- costumer: do what they want in folder files, only read folder files_company, and folder company invisible

Is it ok? I use Owncloud and user can't access to folder costumer. Can anybody tell me why?
Thanks.

---

### Post by ajgreeny on 2017-08-14
What permissions does the folder **/costumer** have?  Show us the output of ```
ls -l /path/to/costumer
```using the proper full path to /costumer, of course, not as I show it.

---

### Post by marta2 on 2017-08-14
Thanks for your answer. 
drwxrwxr-- 5 administrator administrator

---

### Post by ajgreeny on 2017-08-14
If **user** is a member of group **administrator** it appears that **user** should be able to read/write to that customer folder which is owned by adminstrator, so I'm afraid I am a bit baffled here.  

Perhaps I am missing something obvious, but wait for more replies and bump the thread after 12 - 24 hours if no-one else appears to try to help you.

EDIT:
I think I have slipped up with that suggested command as you need to run the **ls -l** command on the folder that contains the /customer folder in order to see the permissions of /customer.

---

### Post by darkod on 2017-08-15
I also can't see anything wrong in the permissions if you have posted them correct for us.

You should also check out share settings on samba level because permissions in samba are a combination of the share settings in samba (permissions you give to users) and the linux folder permissions.

---

### Post by marta2 on 2017-08-15
Thanks for your answer, I've tried to reproduce the configuration I've got in this image:

[IMG]http://www.tepui.cat/foro/avui.png[/IMG]

This is what I need
-administrador and usuario: they have all permissions in all folders
-Userowncloud:
[LIST]
[*]he has all permissions in folder1
[/LIST]
    
[LIST]
[*]he only can read files in folder2
[/LIST]
    
[LIST]
[*]he can&#8217;t see folder company
[/LIST]

I've assigned this permissions:
[COLOR=#000000][FONT=Arial]sudo chmod -R 775 /srv/samba/docs[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo chmod -R 777 /srv/samba/docsEBN/client1/folder1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo chmod -R 774 /srv/samba/docsEBN/client1/folder2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo chmod -R 770 /srv/samba/docsEBN/company

With this configuration administrador and usuario have no problem. But userowncloud can't access anywhere.
I'm new in ubuntu, and there should be something wrong. 
Thanks for your help[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by darkod on 2017-08-15
I really can't see anything wrong, except one small thing that will matter only for folder2. You use 774 permissions on it but you need 775 because for a user to be able to open the folder at all and look at content it has to have r-x, not only r--.

I would also try using a specific folder created only for the data shares, like for example /data or /sambadata. You are using /srv but that has already system permissions of its own and I have heard here on the forum that Samba can sometimes depend on permissions up in the tree, not only of the shared folder.

So I would create /data making it 777, then /data/samba or /data/docs making that also 777. That will make sure all users have all permissions up in the tree until they reach the shared folder. Think good about your folder structure too, keep it simple, only the necessary things you need. Control the permissions on the last level of folders, all above might need to have 777.

Why do you have /srv/samba/docs and /srv/samba/docsEBN? I would create something very simple like /data/customer* without big folder structure in between. But that depends on you too, how you want to organize it and which folders to share in samba.

Also, could this be an issue with owncloud too? We are looking at samba and linux permissions only but if users are accessing over owncloud I have no idea if anything additional is needed.

---

### Post by marta2 on 2017-08-15
Hi darkod, we have a lot of costumers and information of every one of them. We work under windows. In samba folder we have a folder for each costumer, and every costumer have 2 subfolders, one only for us (company) and the other for costumer, where they can see and modify depending.
We can't separate shared or not shared information, it'd be heave for windows users and daily job.
We use ubuntu server to save all our information and we want to share some documents with our costumers.

The real problem is the userowncloud, he is not a member of administrador group, so I'd believe that he has the permissions of other.
Thanks

---

### Post by marta2 on 2017-08-16
Ok, topic solved. The problem was in samba's configuration. I've added in valid users the users of owncloud, and that's all

---

