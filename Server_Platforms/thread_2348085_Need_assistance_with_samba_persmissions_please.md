---
title: "Need assistance with samba persmissions please"
date: 2016-12-31
forum: Server Platforms
---

### Post by biggyk on 2016-12-31
Iv been messing around with ubunutu server as my home media server for while but I seem to always be fighting with Samba file permissions.

Basically I want for now is a separate share for each user in the house and then an open (guest only) folder for media. The media folder is the easy part and have no problems with sharing movies with plex or Kodi.

When it comes to the user level shares there always seems to be a problem with permission. All my computers are windows. I typically use webmin to navigate with a little ssh. 

I would create a user then create a folder not in home but usually made the path /smb/user. I set the folder to 700 because I only want the user and no group to access the share. In samba I set the same permissions but then when I try to delete a file for example it wont let me or I am able to access another users share without using a password. 

Do I have the right idea or is there a better way to do this? I hope I made sense. Please let me know if you need more information.

Thanks.

---

### Post by darkod on 2016-12-31
Since there will be separate share for each user this should be easy.

You said you changed the permissions on the folder to 700 but did you change ownership too? The folder will be owned by the user that first created it (either your first admin user or root), so in addition to changing permissions you also need to change ownership to user:user.
And the parent path needs to be open to all because it is important when sharing a folder. So in your case set /smb to 777. Just that folder, not the subfolders. The subfolders will be 700 with correct ownership per user.

Also in each share defintion use the parameter 'valid users' (check if that was the correct name) and the correct username only for that share. That should prevent any other users from opening that share. Plus the correct permissions...

Of course don't forget to restart smbd and nmbd (samba) after each cnage to the smb.conf.

PS. If possible use ssh. Don't trust webmin. It is not supported and not recommended, so if you get strange results from using it don't complain. :) Webmin does not modify all the files correctly all the time, even though it might look to you like a nice tool...

---

### Post by biggyk on 2016-12-31
> **darkod said:**
> Since there will be separate share for each user this should be easy.

You said you changed the permissions on the folder to 700 but did you change ownership too? The folder will be owned by the user that first created it (either your first admin user or root), so in addition to changing permissions you also need to change ownership to user:user.
And the parent path needs to be open to all because it is important when sharing a folder. So in your case set /smb to 777. Just that folder, not the subfolders. The subfolders will be 700 with correct ownership per user.

Also in each share defintion use the parameter 'valid users' (check if that was the correct name) and the correct username only for that share. That should prevent any other users from opening that share. Plus the correct permissions...

Of course don't forget to restart smbd and nmbd (samba) after each cnage to the smb.conf.

PS. If possible use ssh. Don't trust webmin. It is not supported and not recommended, so if you get strange results from using it don't complain. :) Webmin does not modify all the files correctly all the time, even though it might look to you like a nice tool...


Thank you.

I have been changing the ownership with the user but I always had nogroup. I will try that when I have a chance and check back in.

---

### Post by darkod on 2016-12-31
Since you want 700 the group ownership is not very important. It should have worked with nogroup too. But check out the full parent path too, starting from /, because as I said I have seen many samba experts here mention it is needed to have permissions on all levels above too, not just the folder being shared.

---

### Post by biggyk on 2016-12-31
> **darkod said:**
> Since you want 700 the group ownership is not very important. It should have worked with nogroup too. But check out the full parent path too, starting from /, because as I said I have seen many samba experts here mention it is needed to have permissions on all levels above too, not just the folder being shared.

But it wouldnt be safe to make / use 777 permissions right?

---

### Post by darkod on 2016-12-31
If you use it reasonably, there is no problem using 777. In fact, you have to use it on higher levels because on lower levels you will have folders owned by different users, so how else can they all have access to the full path?

For example, you have /smb/user. The /smb folder contains only the user folders, no other files or sensitive data. So if you use 777 on /smb, everyone can open it. But once open, what can they do? Nothing, because the user folders inside smb will have 700 and only their owner can open them.

This might be why your setup is failing. Try temporarily 777 on /smb and see how it goes.

---

### Post by Morbius1 on 2016-12-31
> **biggyk said:**
> share. In samba I set the same permissions but then when I try to delete a file for example it wont let me or I am able to access another users share without using a password. 
THat doesn't sound right. Please post the output of the following commands so we can see how your shares are set up:
```
testparm -s
```
```
net usershare info --long
```
Side note: Samba provides a special share definition called "homes" that does exactly what you want. By default it automatically points to the users home directory but you can modify it to point anywhere. It would look something like this:
```
[homes]
comment = Home Directories
path = /smb/%S
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = No
```
As an example let's say I am a user on your network. in that case "%S" becomes morbius so samba will create a share "on the fly" that looks something like this:
> [homes]
comment = Home Directories
path =** [COLOR=#0000cd]/smb/morbius[/COLOR]**
valid users = [COLOR=#0000cd]**morbius**[/COLOR]
read only = No
create mask = 0700
directory mask = 0700
browseable = No
Only morbius can access the shared folder of /smb/morbius. If you have another user called agnes then agnes is another %S and an additional share will be created for her at /smb/agnes .....

EDIT: Shutting down for the night and I just wanted to make clear how to use the [homes] share.

** You would in the example above need to make the /smb/morbius folder.
** THen change ownership to morbius:
```
 sudo chown morbius:morbius /smb/morbius
```
Samba will create the share but not the folder.

---

