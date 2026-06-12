---
title: "Permission shared folder owncloud"
date: 2016-03-07
forum: Server Platforms
---

### Post by kambiz2 on 2016-03-07
Hi,
I've installed Owncloud 8.2.2 on a Server Ubuntu 14.04.02 LTS (PHP 5.5.9, Samba: 4.1.6, Apache: 2.4.7)
I've shared a folder, via SMB, with Window's users. All works fine, they can add, write and delete what they want.
The problem is using Owncloud. I can only download files or folders, but I have no permissions to add/create/delete files or folders.
In Owncloud I've configured local external storage. The owner and the group of this shared folder is www-data. Window's users are in www-data group.
In Owncloud Community has tryed to help me. A user suggested me this: sudo -u www-data touch /srv/samba/docs-EBN/test In the folder where I create test file, then works fine, but I can't create this file in every folder. There are a lot, and every day where create more.
Sombody, also, suggest me to use SMB/CIFS external storage. I tried it but there is a mistake in the configuration because it says it's wrong:
- folder: shared
- external storage: SMB/CIFS
- host: 192.168.1.123/owncloud
- share: /srv/samba/docs-EBN
- remote subfolder: ???
- domain: ???
- authentication: I can choose between session credentials or username and password. I if choose session credentials no user and password is asked for. If I user username and password I must write them.

In Owncloud Community has suggested to ask in Ubuntu Community. They think my problem is permissions.

Can anybody help me?. Thanks

---

### Post by howefield on 2016-03-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by mastablasta on 2016-03-07
> **kambiz2 said:**
> 
In Owncloud I've configured local external storage. 

what does that mean? external USB drive on server or a LAN connected NAS?

> 
The owner and the group of this shared folder is www-data.Window's users are in www-data group.


so you would like to access "local external storage" via owncloud. or rather windows users of owncloud should have access to that folder? is that correct? does owncloud have full access to the folder?

---

### Post by kambiz2 on 2016-03-07
Hi mastablasta,
[COLOR=#000000][I]- In Owncloud I've configured local external storage:Owncloud has its default folders. When you configures external storage, you can select a lot of choices. I've select local, this means a local folder in the same server.
- Window's users save the documents in this shared folder ('srv/samba/docs-EBN': this a a folder in my own server). And users via owncloud can access to this folders and files. Windows user's are in www-data group.
You ask if owncloud has full access to this folder. I think so, if not, why when I execute sudo -u www-data touch /srv/samba/docs-EBN/test, the file is created and then all is ok in owncloud, I can create and add folders and files

[/I][/COLOR]

---

### Post by mastablasta on 2016-03-08
ok so the setup is kind of similar to mine only I send files via owncloud client to won cloud. what I have setup is system disk with owncloud and such instaleld on it and then the hard disk where the data is held. the  disk is used for owncloud storage, but I also transfer data there from auto backup via sFTP. now the thing is that when I transfer files via auto backup the files are owned by user and the group is users. unlike in owncloud where the owner and group is www-data. and I don't think owncloud has access to them.

you in a similar way created folders and users would then dump files into them using samba transfer protocol, if I understand correctly. but you would then want to see and modify those files via owncloud, but you can't. you could try by checking the permission settings on the files as well as on folders above them. make sure that on the files www-data group has full access.

---

