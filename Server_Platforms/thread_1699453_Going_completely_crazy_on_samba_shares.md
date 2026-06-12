---
title: "Going completely crazy on samba shares"
date: 2011-03-03
forum: Server Platforms
---

### Post by gunnarflax on 2011-03-03
I tried getting this solved through askubuntu.com but I doesn't seem to come anywhere. Can anyone help me with the following problem...

I have always had trouble setting up samba shares with ubuntu. In the past I've tried getting it to work by configuring /etc/samba/smb.conf  but never achieved what I wanted. Last time I managed to get it working  by making a share with nautilus built in file sharing (which utilises  samba). Now when I try do it again it doesn't work. (running ubuntu  10.10 Desktop x64)


  What I'm trying to achieve is a share which is available for multiple  users (those who are in the same group) and not just the owner (who  also is included in the group). As it is now I can connect with only the  owner, the others are getting an error when I try to connect with  windows 7. All the users are within the same group and the folder  permissions are 770. The files and folders have the correct group  settings.


  I think there is no restrictions in the User Settings for the other  users blocking them and I marked "make available to other users (or  whatever it says)" in the file sharing dialog.

The file system which i'm trying to share is mounted with the following settings:
```
UUID=[...] /media/Storage ext4 defaults 0 2
```

I was thinking if the problem was the same as discussed in [this]("http://askubuntu.com/questions/4135/group-share-permisssions-to-windows-clients") post. But how do I configure the shares which nautilus makes? I cannot find the entries in /etc/samba/smb.conf.

Please help me make some progress with this problem.
Thank you!

---

### Post by slooksterpsv on 2011-03-03
Samba has some issues, no offense, an NFS share would be better (in my opinion). But, it looks like this is what others are having to do (on the Windows Machines) to get it to work. Also from what I've been reading, it looks like a bug within Windows, Vista had it, but I guess it's fixed, and 7 has it now, but hasn't been fixed. Anyways here's the solution I found (hope it works for you)

Taken from: [http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

[quote=http://www.tomshardware.com/forum/75-63-windows-samba-issue]
Control Panel - Administrative Tools - Local Security Policy

Local Policies - Security Options



Network security: LAN Manager authentication level
Send LM & NTLM responses

Minimum session security for NTLM SSP
Disable Require 128-bit encryption



my SMB server worked after changing those two options 
[/quote]

---

### Post by gunnarflax on 2011-03-04
I will try that as soon as I can. Does NFS work with windows?

---

### Post by spook1980 on 2011-03-04
> **gunnarflax said:**
> I will try that as soon as I can. Does NFS work with windows?

yeah but u gotta do not sure what, as i have never had to share to windows (all my computers are ubuntu)

but yes there is a way of doing with windows...

[http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)

---

### Post by slooksterpsv on 2011-03-04
> **spook1980 said:**
> yeah but u gotta do not sure what, as i have never had to share to windows (all my computers are ubuntu)

but yes there is a way of doing with windows...

[http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)

Dang it, looks like he would need a 3rd party program to mount NFS volumes. Geeeze Microsoft is so limiting, either you use Samba or you use the Professional (or higher) version of Windows. Microsoft sucks!

With Ubuntu you can mount, Fat16, fat32, ntfs, ufs, nfs, btrfs, reiser, jfs, xfs, ocfs, etc. etc. etc. - networking, pretty much anything.

---

### Post by gunnarflax on 2011-03-04
Ok, the problem doesn't lie in the earlier proposed solution since I got the same problem when trying to connect with another ubuntu computer. The folder being shared has also a parent which is being shared. The parent is only accessible by myself, the owner account. The child is supposed to be accessible by both me and all the others within the group **storage-media**. Both shares are accessible by me, the owner.

When I try to connect with another account within the group to the parent I get rejected because of that the user does not have the right permissions (...I guess since the login screen gets shown again). But when trying to mount the child with the same user account I get the error message:
```
**Unable to mount location**
Failed to mount Windows share.
```Any ideas?

---

### Post by slooksterpsv on 2011-03-04
If you change it to where you have permission to the parent are you able to access the parent and the child? Could be a flow-of-permissions issue.

---

### Post by Vegan on 2011-03-04
SAMBA can be configured fine for multiple servers in a forest.

I suggest reading man pages

```
man samba
```

---

### Post by Demented ZA on 2011-03-05
Uhm, you don't need 3rd party software to use NFS under windows. Just install Services for NFS under "turn windows features on or off".

---

### Post by slooksterpsv on 2011-03-05
> **Demented ZA said:**
> Uhm, you don't need 3rd party software to use NFS under windows. Just install Services for NFS under "turn windows features on or off".

Ok, good to know, I was just reading something where someone said that NFS features weren't available in Home Premium and you had to have Professional or above to get NFS.

---

### Post by Demented ZA on 2011-03-05
> **slooksterpsv said:**
> Ok, good to know, I was just reading something where someone said that NFS features weren't available in Home Premium and you had to have Professional or above to get NFS.

Lol, I didn't know Home Premium didn't have it. Makes sense though. Now I learned something too :D

I'm sure there are workarounds like installing 3rd party software or possibly even porting Services for NFS.

---

### Post by gunnarflax on 2011-03-05
> **slooksterpsv said:**
> If you change it to where you have permission to the parent are you able to access the parent and the child? Could be a flow-of-permissions issue.

I will look into that later today. The strange thing is that I managed to get this set up working before I reinstalled the system.

So you guys are saying that NFS works with windows? How can I activate the feature for both windows and ubuntu? Must I install a package for ubuntu? Is it integrated into nautilus? Will there be any difference with the flow of permissions (if that is the problem). I mean, do you think it is samba related or does it have those problems anyway?

---

### Post by gunnarflax on 2011-03-05
Are you sure that NFS only works with windows professional? :/

---

### Post by Morbius1 on 2011-03-05
I'm not going to get into the NFS vs Samba debate since they are apples and oranges but:

You are using two completely different samba methods to share folders - Usershares and Classic-shares. You are sharing folders within folders which is tricky to pull off and often has unintended consequences. And your references to permissions and ownership have me confused. I would propose supplying us with some facts.

Please post the output of the following commands:
```
testparm -s
```[COLOR=Blue]*That will tell us how Samba is configured and show us how your Samba Classic-shares are defined.*[/COLOR]

```
net usershare info --long
```*[COLOR=Blue]That will tell us how your Usershares ( aka nautilus-shares ) are defined.[/COLOR]*

```
ls -al /path/to/parent/folder
```This will tell us who owns the parent and all the child folders and what permissions.

It could be a simple Linux file permissions problem as [COLOR=Blue]**slooksterpsv **[COLOR=Black]already suggested.[/COLOR][/COLOR]

---

### Post by gunnarflax on 2011-03-06
This is the result from:
```
sudo testparm -s
```
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = ROSENQVIST
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

```

The result from:
```
sudo net usershare info --long
```
```
[media]
path=/media/Storage/Media
comment=Filmer, TV-Serier och Musik.
usershare_acl=Everyone:F,
guest_ok=n

[storage]
path=/media/Storage
comment=Niklas lagring
usershare_acl=Everyone:R,HOME-SERVER\server:F,
guest_ok=n

```

And the result from:
```
sudo ls -al /media/Storage
```
```
drwxrwx--- 15 server server         4096 2011-03-05 18:41 .
drwxr-xr-x  3 root   root           4096 2011-02-28 20:58 ..
drwxrwx---  7 server server         4096 2010-10-27 00:27 Annat
drwxrwx---  8 server server         4096 2011-03-01 17:59 Backup
drwx------  2 root   root          16384 2011-01-12 15:10 lost+found
drwxrwx-w-  4 server storage-media  4096 2011-02-28 21:14 Media
drwxrwx--- 20 server server         4096 2010-12-30 12:59 Program
drwxrwx---  2 server server        12288 2011-02-18 18:48 Random bilder
drwxrwx---  5 server server         4096 2011-02-09 01:12 .Trash-1000
drwx------  4   1004 server         4096 2011-02-14 17:24 .Trash-1004

```
and the folder **Media** is the child folder being shared. Any ideas? Or is there any more information I should share?

---

### Post by gunnarflax on 2011-03-06
Is it better to just share the parent and let all the users connect through that, let them browse /media/Storage but no children except Media?

---

### Post by Morbius1 on 2011-03-06
Let's get rid of the easy problem first while I stall for time to think about the bigger problem. slooksterpsv was right about the path permisions.

The permissions on the parent folder /media/Storage is:
> drwxrwx--- 15 server server         4096 2011-03-05 18:41 .The only user capable of opening that folder to get to what's inside is user:server. Change that:
```
sudo chmod 0775 /media/Storage
```We may end up changing that later depending on how we resole this share-within-a-share issue.

The permissions on the child:
>  drwxrwx-w-  4 server storage-media  4096 2011-02-28 21:14 MediaUm ... assuming all the remote authenticated users are member of the "storage-media" group that just might work as it is. I need to do some testing to see if that will work but it will have to wait a bit until I have more time.

---

### Post by Morbius1 on 2011-03-06
OK, here's the problem and this is what makes shares within shares such a tricky thing to pull off. 

If I as a remote user go through the /media/Storage share I can only read no matter what is permitted on the /media/Storage/Media share because I'm under the control of the storage share authentication. 

If I go through the /media/Storage/Media share directly then I can get write access but only if I'm a member of the storage-media group. 

I think this is going to be too confusing to the user so this is what I would propose:

(1) In nautilus reset the share on /media/storage to "Allow others to create and delete files in this folder".

(2) Still in Nautilus - "unshare" entirely the /media/Storage/Media share.

(3) Nautilus-share automatically modifies the permissions on /media/Storage to 777 so you will have to override this:
```
sudo chmod 0775 /media/Storage
```

So far when the remote user accesses the /media/Storage share he will be allowed to write by samba but prohibited to write by Linux because only user:server and group:server can write to the folder.

The exception to that will be the /media/Storage/Media directory and only if the remote user is a member of the storage-media group. So:

(4) For every remote user that you want to have write access to /media/Storage/Media you need to add them to the storage-media group:
```
sudo gpasswd -a remote-user-name storage-media
```(5) After you add all the users to the storage-media group logoff and login again.

---

### Post by gunnarflax on 2011-03-06
THANK YOU! That solved it! :D

The only thing I did differently was that instead of setting:
```
sudo chmod 0775 /media/Storage
```
I set it to:
```
sudo chmod 0750 /media/Storage
```
Since I don't want others to be able to make changes within Storage but I understand now that they need to be able to navigate it to gain access to /media/Storage/Media which they now do :)

Thank you everyone who have been contributing and especially Morbius1!

---

### Post by slooksterpsv on 2011-03-06
The basics sometimes are the biggest things we miss.

I've got that noted in my KeepNote Notebook so I can try to remember it for future reference. Congrats.

Make sure that you mark the thread as solved under Thread Tools at the top =D

---

### Post by gunnarflax on 2011-03-07
Sorry, almost forgot that :D Thanks again!

---

