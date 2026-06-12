---
title: "Confused on user:group membership + Samba Share"
date: 2015-02-06
forum: Server Platforms
---

### Post by forums-etarq on 2015-02-06
This is a home environment, no business security needs here.  I have several Samba Shares off of my linux "server".  I have all the Windows machines map drives to several of the shares off the Ubuntu server. Every computer can read/write to the shares. It works great! But now I'm trying to change something and am having trouble.  Current SMB.conf below:

```

[global]workgroup = WORKGROUP
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[documents]
common = Documents
path = /media/4tb/documents
public = yes
writeable = yes
create mask = 0664
directory mask = 0777
follow symlinks = yes
force user = username1
force group = username1

```


What I am now doing, is I have installed "Owncloud" and it is working great. However, instead of having the Owncloud agent running on the desktop computers, I have the "owncloud" data directory configuration pointed toward /media/4tb/documents/owncloud - a sub directory of the "Documents" share shown above in the Samba config.

So as it stands now...

1. All my windows PCs can read/write perfectly via the samba shares with the current settings.
2. Owncloud users can read/write perfectly via the web gui and the agent to /media/4tb/documents/owncloud

So here's my problem:
1. When a windows user tries to open the folder /media/4tb/documents/owncloud via the SMB share, they get an access denied message.
2. The ownership of everything in /media/4tb/documents/* has always been:
```
drwxr-xr-x 20 username1 username1  4096 Feb  3 10:52 documents
```
3. The ownership of /media/4tb/documents/owncloud *must be*
```
drwxrwx---  4 www-data    www-data     4096 Feb  3 09:41 owncloud
```

Do I need to change the r/w/x of the Owncloud folder so more than just www-data can read/write to it?
I tried adding username1 to the www-data group and vice versa but that didn't seem to work. I assumed that I could do Active Directory type "Security Group" theory to the www-data group by adding my username1 to that www-data group.

Any tips to what I am doing wrong are welcomed! Hopefully this makes sense to someone what I am trying to do.

---

### Post by volkswagner on 2015-02-06
Do realize own cloud is not obeying settings in the share because it's writing to filesystem directly.

Two things come to mind. Either point own cloud directory at the share //localhost/share or add all your users to the www-data group.

---

### Post by forums-etarq on 2015-02-06
> **volkswagner said:**
> Do realize own cloud is not obeying settings in the share because it's writing to filesystem directly.

Two things come to mind. Either point own cloud directory at the share //localhost/share or add all your users to the www-data group.

Yes, I did notice during testing that when I add files to Owncloud, they are 'owned' by www-data user and www-data group.

```
/media/4tb/documents/Owncloud/files/Temp$ ls -l
total 7056
-rw-r--r-- 1 www-data www-data 7208328 Feb  6 12:16 Redwood National Park.pdf
-rw-r--r-- 1 www-data www-data      94 Feb  6 13:40 Redwoods.txt

```

I don't have multiple users, I just have essentially one user "Username1" and one group "Username1" that has full rights to the document folder and is 'forced' by the Samba share setting.

I did add "Username1" to the group www-data and it didn't seem to make a difference.

I will see if owncloud will allow me to add a network path of \\server\documents for writing files that way.

Thank you!

---

### Post by volkswagner on 2015-02-06
Did you log Username1 out and back in again for group to take affect?

What's output of:
```
groups Username1
```

If you only have one user, there's no need for the force user/group:
```
force user = username1
force group = username1
```

You may want something like:
```
valid user = Username1, @www-data
```

If Username1 is part of www-data group he should have read access to \\server\documents\Owncloud

Is your windows username and password matching your SAMBA and Linux username/pwd?
When the windows user writes a file to documents, what do the permissions look like?
```
ls -al /media/4tb/documents
```


What's the output of:
```
ls -al /media/4tb/documents/Owncloud
```

---

### Post by volkswagner on 2015-02-06
Also check out this umask fix.

[https://forum.owncloud.org/viewtopic.php?f=8&t=3954](https://forum.owncloud.org/viewtopic.php?f=8&t=3954)

---

### Post by forums-etarq on 2015-02-06
Output of "groups Username1" is


```
username1 : username1 adm cdrom sudo dip www-data video plugdev mythtv sambashare lpadmin vboxusers
```


You are correct, the first time I was trying this all out, I had not logged out/logged back into my SSH session.


Without me fiddling with permissions (chmod's), Username1 was able to *read* the contents of /media/4tb/media/documents/Owncloud just not write or make changes. When I fiddled with the x/w/r permissions then Username1 could make changes to contents. However, the Windows side access could still not read or write the contents.


The windows usernames and passwords are not the same as Username1, in fact all the Windows devices just log in with a username and a blank password.


With the current setup if I create a text file via \\server\documents it looks like this:


```
-rw-rw-r-- 1 username1 username1 14 Feb  6 19:16 test_file.txt
```


Output of ls -al /media/4tb/documents/Owncloud is:


```
lrwxrwxrwx 1 username1 username1 17 Feb  3 10:46 /media/4tb/documents/Owncloud -> ../owncloud/mark/
```


and the code to the actual location is:


```

drwxrwxrwx  4 www-data www-data 4096 Feb  3 09:41 .
drwxr-xr-x  8 root     root     4096 Feb  3 09:04 ..
-rw-r--r--  1 www-data www-data  268 Feb  1 16:40 .htaccess
-rw-r--r--  1 www-data www-data    0 Feb  1 16:40 index.html
drwxr-xr-x 11 www-data www-data 4096 Feb  3 09:00 mark
-rw-r-----  1 www-data www-data  412 Feb  3 09:09 mount.json
-rw-r--r--  1 www-data www-data    0 Feb  1 16:40 .ocdata
-rw-r-----  1 www-data www-data 5983 Feb  3 09:32 owncloud.log
drwxr-xr-x  2 www-data www-data 4096 Feb  1 16:53 updater_backup

```


It's not the symlink causing the problems is it?  Owncloud actually puts the files I create via the web gui or sync app in the mark/data/files location.


I will have to test out removing the 'force user' function in the smb.conf to see how it behaves with your suggestion of valid user...but is it safe to assume that those 'valid users' are the unix accounts, and not my windows accounts?


Lastly, I can try the umask 'fix' mentioned in the owncloud forum.

I never doubted I was doing something wrong, that's for sure. Thank you for your help.

---

### Post by volkswagner on 2015-02-06
As you can see www-data group does not have write access to the linked location.

```
drwxr-xr-x 11 www-data www-data 4096 Feb  3 09:00 mark
```

---

### Post by forums-etarq on 2015-02-17
Been out of town for work, but took a look at this again tonight.  I tried making my "owncloud" directory that I was trying to access from my Documents Samba share into its own Samba share with the following in my smb.conf:

```

[Owncloud]
common = Owncloud
path = /media/4tb/owncloud/mark
public = yes
writeable = yes
create mask = 0664
directory mask = 0777
force user = www-data
force group = www-data

```

For the short term, this is working. From my windows PCs I can access the this samba share with read/write permissions no problem, without entering any usernames or passwords. This will work for now. It seems the 'force user/group' makes all the difference when setting my samba shares. If I remove the force user/group options I cannot access any of the shares from Windows.  I assume this is because all the windows workstations log in without passwords, and I have never created samba accounts, so the force user/group flag is taking care of 'logins'?

---

### Post by bab1 on 2015-02-17
> **forums-etarq said:**
> 
For the short term, this is working. From my windows PCs I can access the this samba share with read/write permissions no problem, without entering any usernames or passwords. This will work for now. It seems the 'force user/group' makes all the difference when setting my samba shares. If I remove the force user/group options I cannot access any of the shares from Windows.  I assume this is because all the windows workstations log in without passwords, and I have never created samba accounts, so the force user/group flag is taking care of 'logins'?

The force user only comes into play AFTER the user is logged in.  If you the user is not part defined (no smbpasswd -a has been performed for that user) then the user could be logged in as the user "nobody" and the group "nogroup".  The *force user* parameter is used to define the user that creates files and directories in that share on behalf of all users of the share.

---

### Post by forums-etarq on 2015-02-18
> **bab1 said:**
> The force user only comes into play AFTER the user is logged in.  If you the user is not part defined (no smbpasswd -a has been performed for that user) then the user could be logged in as the user "nobody" and the group "nogroup".  The *force user* parameter is used to define the user that creates files and directories in that share on behalf of all users of the share.

Thank you. Is there a way to tell from the Ubuntu box what users are connected to the shares?

---

### Post by volkswagner on 2015-02-18
You can list open files with:
```
smbstatus
```

---

### Post by bab1 on 2015-02-18
> **forums-etarq said:**
> Thank you. Is there a way to tell from the Ubuntu box what users are connected to the shares?

There is a command line tool to check the connections to a Samba server.  It is called ***smbstatus***.  But if all your connections are by anonymous users then the connections will most likely show up as the user *"nobody".*

---

