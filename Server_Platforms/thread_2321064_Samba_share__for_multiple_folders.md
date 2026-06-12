---
title: "Samba share  for multiple folders"
date: 2016-04-20
forum: Server Platforms
---

### Post by gardenair on 2016-04-20
hi,
       Reference to my old post  " [http://ubuntuforums.org/showthread.php?t=2305658](http://ubuntuforums.org/showthread.php?t=2305658) " the management said me to create a new folder under " /pdc share " which is a common share where all users keep their files in his/her  respective  folders.  The GM said to create a new folder called "pdc events" where he may keep his some of his file. I have create a new user,assign him group  "pdc"  and give rights . 

The issue is that for "GM" folder he can do any thing but when he enter into the "PDC Events" folder and try to create a file or folder samba say permission "You need permission to perform this action".

The password for connecting the "GM" folder and  "PDC Events" are both  same.   Using "# smbpasswd -a <user name>

By default to connect "GM " folder windows ask for user name and passwd then it  works file.Same thing for "pdc events ". Both works file with this respective user name and password.  Is it possible that the GM (General Manager) can access both folders at a time though his passwd is same. Is it windows limitation to connect one user in one time in a single machine ?  Is there any way to use both folders with one user at the same time. Yes one way I know is 777 for all then no issue for me or i give him a laptop with windows 7  to access that folder and it will do.That is a bad practice i think. :) 

Note:- All users have their rights drwx r- x r-x 

Kindly guide me.
thanks

---

### Post by darkod on 2016-04-20
It will be much more complex to control permissions if the folder is inside another share. The best option would be to create the folder outside of any other share, and set it up as separate share. Then in the share options you can set only that user to have access.

Otherwise, you need to double check the ownership of the new folder. What are the permissions of "/pdc share/pdc events"? Maybe all is good on samba end but linux permissions are limiting it.

---

### Post by gardenair on 2016-04-21
Thanks for your kind reply. Well the permission for "pdc share" is 

```
drwxr-xr-x 15 root pdc  4096 Apr 20 10:54 pdc-share

```



the permission of "pdc-events" is

```
drwxr-xr-x  2 pdc-events              pdc    6 Apr 20 12:40 PDC-Events
```

Thanks.

---

### Post by darkod on 2016-04-21
There you go. The "pdv events" is owned by user pdc-events and group pdc. But the group permissions are r-x which means only Read. Your GM is part of the pdc group but these group permissions allow him only Read.

If you want the whole pdc group to be able to create files inside "pdc events" you need to add Write permissions. For example something like (adjust it for the real path of pdc events):
```
sudo chmod g+w "/pdc share/pdc events"
```

That will add write for the whole pdc group.

The same applies for pdc share folder. If you expect the group to be able to write there, you have only permissions r-x, no write. In fact, for this to work I think you have to give write permissions to all path previous to the pdc events folder... So you might need to adjust the parent folders permissions.

---

### Post by gardenair on 2016-04-22
Thanks for your prompt reply. Appreciate you. Well I have use the following command  to give the permission for write 

```
 # cd /mnt/pdc-share

# chmod g+w PDC-Events
```

By using this method all the users including "GM" user can add and delete  the  file or folders inside the "PDC-Events"  folder which is not  secure.Any person in the group can delete the delete inside the "PDC-Events" folder.

What I need is [U]only "GM" user may add or delete files or folders inside the "PDC-Events" folder,rest of the people only have read permission in this folder.
[/U]

Thanks for guiding me.

---

### Post by darkod on 2016-04-22
In that case simply change the owner of PDC-Events keeping the permissions rwxr-xr-x.
```
cd /mnt/pdc-share
chown GM PDC-Events
```

That way the owner of the folder (GM) will have rwx access, the pdc group will have r-x (read only) and everyone else outside the pdc group also r-x.

---

### Post by volkswagner on 2016-04-22
I have found this article invaluable for understanding and implementing advanced file permissions and share permissions.
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by gardenair on 2016-04-25
Thanks " [COLOR=#000000]darkod" for your kind reply. Really appreciate you :) Many many thanks for helping me. Yes now it works fine according to to my desire. 
One thing more I want to know that just like we can see the user n side 

"#cat /etc/passwd
#cat /etc/group"


[/COLOR]```
cd /mnt/pdc-share
chown GM PDC-Events
```
[COLOR=#000000]
How may I see in a file that "GM" is also has a ownership of  "[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]PDC-Events" folder. Yes any file where I may see it ...?

Thanks once again[/FONT][/COLOR]

---

### Post by darkod on 2016-04-25
That ownership is not in any file. You can check it with 'ls -l' command but you already know that since you must have used it, you posted ownership and permissions of the folders.

When you want to know specific folder or file ownership and permissions, you simply go to that path and run the 'ls -l' to get the details.

---

### Post by gardenair on 2016-04-26
Thanks once again.One thong more regarding to the permission i want to discus  that before changing the ownership  the permission was as following. In this case the user "pdc-events" was the owner of his own folder.

```
drwxr-xr-x 11 gm                           pdc 4096 Apr 20 12:44 GM


drwxr-xr-x  3 pdc-events                      pdc   98 Apr 25 11:43 PDC-Events

```


Yes after changing the permission according to my desire  is as following

```
drwxr-xr-x 11 gm                    pdc 4096 Apr 20 12:44 GM


drwxr-xr-x  3 gm                    pdc   98 Apr 25 11:43 PDC-Events

```

Well now the user "gm" is the owner of the folder "PDC-Events" ,if the user "pdc-events" also want to access the same folder then in that situation what Linux will do?  _In simple words one folder with multiple users access_ . Is it possible  or their is a limitation in Linux for such condition?

thanks.

---

### Post by darkod on 2016-04-26
There can be only one user owner and one group owner. If you want identical permissions for two persons on the same folder, you will have to create a group and put those two persons as members. Then set that group to own the folder in question and modify if necessary the group permissions (like giving write, g+w).

---

### Post by volkswagner on 2016-04-26
While is true you can only have one user-owner and one group-owner, there's always more than one way to accomplish your goal (especially with Linux).

If simple owner/group/everyone permissions are not granular enough or if it forces you to make complex groups, nested groups, etc.... you can
do a lot with ACLs.

The link I provided earlier give a great explanation about ACL's. A lot of it has to do with being part of a domain, but [ACLs]("https://help.ubuntu.com/community/FilePermissionsACLs") can exist without being
joined to a domain.

---

### Post by gardenair on 2016-04-28
I a really soo much thankful to you "[COLOR=#000000]darkod" and "[/COLOR][COLOR=#000000]volkswagner". Well regarding to ACL ,in my case there is no Domain controller connected with Samab server. So in this case after installaing ACL it will work proper without  a Domain controller ?

2- ACL will work with my  current  Linux  permissions or it will override the permissions ?

Thanks once again.[/COLOR]

---

