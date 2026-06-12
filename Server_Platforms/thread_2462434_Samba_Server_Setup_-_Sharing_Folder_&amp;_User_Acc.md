---
title: "Samba Server Setup - Sharing Folder &amp; User Access"
date: 2021-05-20
forum: Server Platforms
---

### Post by ecronic on 2021-05-20
Hi All,

I'm a very basic user of Linux OS (Always used Ubuntu). Recently, I have purchased a HP Pro 3500MT G2 for installing Ubuntu 20.04 for setting up a media server. I would like to keep my collection of movies on this PC and access it via my Plex Server on the Nvidia Shield TV. I will be installing qtorrent on the PC and access it remotely via my Windows PC to download the torrents.

Here's the PC HDDs setup:

**/mnt/sda1 -** 1 x 500gb HDD completely dedicated to the OS (Single OS - Ubuntu 20.04)
**/mnt/sdb1 -** 1 x 3TB HDDs for media storage - movies, animations, files, backup etc...

I read through the online guide of how to install the Samba server, setup Workgroup name, setup netbios name create a private/public share, create a samba user, create a system user etc. Now after all this, when tried accessing the folder via the Windows PC I got the error "Make sure the folder name is spelt correctly." I don't understand where I've gone wrong or whether I missed a step somewhere?

I'd really appreciate any help in this issue.

Thanks in advance for your time.

Ecronic

---

### Post by wildmanne39 on 2021-05-20
Moved to Server forum.

---

### Post by TheFu on 2021-05-21
Samba isn't needed.  Plex will stream the videos using DLNA.  If you want to have remote file access for managing the files from other computers, use NFS for all the Unix-based systems. Only use Samba for Windows clients.

Assuming the storage all uses native Linux file systems like ext4, then you can use these steps:
[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) to setup permissions that let a few different users have the needed access. Samba doesn't care about permissions, which is good and terrible.

Also, it is best to no allow any funny characters or spaces in the names for any media. This is because scripts have to get all their quoting perfect to ensure those funky characters are handled correctly. Additionally, the characters allowed by Unix are different than those allowed by Windows. With Unix, we **can** use any character, but then the funky ones need to be correctly quoted/escaped everywhere in the code.

So ... with this new information, you have some choices to make, almost certainly.  For example, is the 3TB HDD using a native Linux file system?
Do you have backup storage for those files?

---

### Post by rsteinmetz70112 on 2021-05-21
Assuming you're trying to share file with Windows
How did you set up Samba, there are 2 different ways, using an AD-DC and using what Samba calls NT style. Which did you use?
Can you post your smb.conf or at least the share definition?

---

### Post by TheFu on 2021-05-21
> **rsteinmetz70112 said:**
>  
Can you post your smb.conf or at least the share definition?

**testparm** output would be helpful.  That shows what samba is actually using - better than what smb.conf shows.

---

### Post by rsteinmetz70112 on 2021-05-22
> **TheFu said:**
> **testparm** output would be helpful.  That shows what samba is actually using - better than what smb.conf shows.

Yes it is very useful, but it doesn't always show errors in the smb.conf that prevent samba form working correctly.

---

