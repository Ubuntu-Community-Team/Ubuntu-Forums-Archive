---
title: "About to create users and groups - am I doing it right?"
date: 2016-12-09
forum: Server Platforms
---

### Post by keith30 on 2016-12-09
My existing setup comprises of an Ubuntu 14.04 server acting as a file server to a number of Win 7 PC’s in a small office. Until now we have had no need to limit access to shared folders so all shares have been ‘guest ok = yes’ with create mask and directory mask = 0777. All Win clients have been open with no user login/password required. This setup has worked fine for us but I would now like to introduce some security so that not all users will be able to access all shares.
 
To this end I have started by creating user names and passwords on each client PC and now need some guidance as to how to set up the users and groups on the server. I understand user names and passwords need to be the same on the clients as the server.
 
Having read various on-line guides and numerous forum posts I have summarised what I think I need to do but would like some confirmation from those with experience before I take the plunge. My sequence is:-
 
Create Users:
sudo useradd –s /bin/true keith
sudo passwd –L –a keith
sudo smbpasswd –L –e keith
 
Create Group:
sudo groupadd –g 5000 surveyor
(check /etc/group for unused group number)
 
Add User to Group:
sudo usermod –G –a surveyor keith
 
Edit smb.conf:
[global]
security = user
encrypt passwords = yes
smb passwd file = /usr/local/samba/private/smbpasswd
 
[folder]
valid users = @surveyor
force group = @surveyor
(remove guest = ok)
 
What should I do about ownership of the existing shared files and folders. 

Is there anything I have missed or should also consider?

Thanks in advance.

---

### Post by volkswagner on 2016-12-09
In your example for keith I'd like to point out the following.

#smbpasswd
I'm not certain what Local mode does, and I've never used it.
The "-e" switch is probably not necessary if it's a new user and will likely be ignored.
You should use "-a" indicating append the password file thus adding the user.

In smb.conf share definition, force group creates an oddity. You should use (see recent [thread]("https://ubuntuforums.org/showthread.php?t=2345076")):
```
force group = +surveyor
```

You may or may not have to change file permissions.

If you do, I've used the following to recursively change files and folders:

```
# To recursively set permissions only on directories!
sudo find /path/to/base/dir -type d -print0 | xargs -0 chmod 775 


# To recursively set permissions only on files!
sudo find /path/to/base/dir -type f -print0 | xargs -0 chmod 664 
```

You can modify the above to be more restrictive by changing "everyone" to 0 (folders 770, files 660).
You may also want to recursively set the group to surveyor.

---

### Post by keith30 on 2016-12-09
Thanks for your comments and advice volkswagner. 

Presumably I have nothing to lose by adding users and groups to the server as nothing will materially change until I remove guest=ok from smb.conf.

---

