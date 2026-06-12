---
title: "Folder permissions across the network"
date: 2012-10-03
forum: Security
---

### Post by kwinsw on 2012-10-03
Hi,

I'm not sure if this belongs in here, or the networking forum. Apologies if I made the wrong choice.

I've set up our home network to have shared folders on an Ubuntu server. Each folder can only be accessed by specific user accounts on the server. None of the folders them are have 777 permissions and none is owned by nobody.nogroup.

This works fine with Samba. My Windows machines log in, prompts me for a username and password, which I tell Windows to cache, and they have access to the share.

How do I do the same for NFS on the Ubuntu Desktop clients? Currently, my NFS shares have a "lock" symbol on them and I can't find a way to enter any credentials.

Many thanks

kwsinw

---

### Post by SeijiSensei on 2012-10-03
Unless you want to get into the mechanics of ID mapping, the simplest solution is to ensure that the UIDs and GIDs on the clients are identical to their values on the server.  This can be tricky since a fresh Ubuntu installation will assign the initial user the same IDs (1001, I believe).  You'll need to manually change the IDs on the clients to match the server.  You could use NIS instead, but that makes authentication tricky if the client machines are not permanently connected to the network.

I use "no_root_squash" as a server option and mount the exported directory in /etc/fstab.  Suppose, for instance, you export /home on the NFS server with no_root_squash and mount it as /mnt/home on the client in fstab.  If all the remote user directories have 700 permissions, users will only be able to access their own directories as long as the UIDs and GIDs match.  The behavior is no different than the access the users would have if they were logged into the server itself.

---

### Post by Morbius1 on 2012-10-03
This is more a side question since I know nothing of NFS but why aren't you using samba shares for your Linux clients as you are with your Windows clients?

---

### Post by kwinsw on 2012-10-03
Thank you, SeijiSensei! That gives me loads to go on. I shall try it all tonight. 

I'll post here to let you know how it goes.

Cheers

kwinsw

---

### Post by kwinsw on 2012-10-03
Thank you, that worked a treat. I used:

*chown -R newuserID:newgroupID folder_name*

to change the UID and GID of the directories to match those on the server and everything works fine.

One question, though, what do I do when I have more than one user account on the Ubuntu clients? 

Presumably then the UID at least won't be same on all the client accounts as it is on the server?

---

### Post by LewisTM on 2012-10-05
For using NFS optimally, all UIDs need to match across machines.
To quickly change the UID of a given user, as well as update the file ownerships in his/her home directory, run
```
sudo usermod -u <newID> username
```
If you want to grant to more than one user access to the same files, you will have to specify group permissions and add these users to the appropriate groups.

If you have complicated needs where you would want to access files from multiple users while being logged in as a different (remote) user, you better use Samba or SSH/SFTP. Authentication methods for these protocols are built into Ubuntu file managers.

Cheers!

---

### Post by kwinsw on 2012-10-06
Hi Lewis,

Thanks for the further advice. I had already clocked that my original fix, (above) was only really half a fix. I had access to the folders, but everything I copied to them from any of the Windows PCs had root access only, so the users on the Ubuntu desktop system can't edit those files. I'm not sure why.

All the UIDs and GIDs now match across both the Ubuntu Desktop and the Ubuntu server machines. But I still have the problem - anything created on the Windows system and copied or saved to the server has a padlock symbol on it when viewed from the Ubuntu Desktop machine. When you check the permissions, it's root only.

I suspect in the end, I will go for Samba or SSH across both platforms. But I'd like to get this working, just because I want to know how to do it.

Anyway, thank you again very much for the help.

Cheers

kwinsw

---

