---
title: "CIFS FSTAB mounting issue"
date: 2016-04-01
forum: Server Platforms
---

### Post by scott.bouch on 2016-04-01
[COLOR=#000000]Hi guys,[/COLOR]

[COLOR=#000000]Trying to mount a directory of my server to the MNT directory of mt laptop. I can SSH to it, no problem.[/COLOR]

[COLOR=#000000]Not knowing CIFS, I blindly tried these lines in FSTAB (simply based on copying other working FSTAB mounts) with following mount-a results:[/COLOR]

[COLOR=#000000]//192.168.1.50/var/www/html /mnt/HTML cifs credentials=/root/.6FCcred,rw,nounix,iocharset=utf8,file_mode=0777,d ir_mode=0777[/COLOR]

[COLOR=#000000]$ sudo mount -a[/COLOR]
[COLOR=#000000]Retrying with upper case share name[/COLOR]
[COLOR=#000000]mount error(6): No such device or address[/COLOR]
[COLOR=#000000]Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/COLOR]



[COLOR=#000000]//192.168.1.50/var/www/html /mnt/HTML cifs credentials=/root/.6FCcred[/COLOR]

[COLOR=#000000]$ sudo mount -a[/COLOR]
[COLOR=#000000]Retrying with upper case share name[/COLOR]
[COLOR=#000000]mount error(6): No such device or address[/COLOR]
[COLOR=#000000]Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/COLOR]



[COLOR=#000000]Any other ideas?[/COLOR]

[COLOR=#000000]Cheers, Scott.[/COLOR]

[COLOR=#000000](Sorry, I accidentally posted this also under hardware, which needs erasing)[/COLOR]

---

### Post by darkod on 2016-04-01
If this folder is not shared, you can't mount it simply like that.

If it is shared, it will have its 'sharename' (regardless of what the folder full path is). In such case the mount object in fstab is //192.168.1.50/sharename (not the folder path).

To share a folder you need to use either samba, nfs, iscsi, etc... Your pick. If you are sharing linux to linux you might wanna look into nfs or iscsi. samba is used more for sharing linux server shares to windows clients, however linux clients will mount samba (cifs) share too.

Of course, the exact fstab line will depend on the share type. cifs will be used only for samba shares. For nfs shares you would use something like nfs for the share type, etc.

---

### Post by scott.bouch on 2016-04-01
Ah, yes, I'd copied how my NASdrives are mounted (they are shared volumes).

I'll be waning to access this folder from Linux and Windows machines, so that's why I used CIFS. 

How do I declare a folder on the server as a share?

---

### Post by darkod on 2016-04-01
This is a very simple share but very easy to do to start with:
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

Of course, skip the steps that you don't need (like creating the folder you want to share).

But I see you are planning to share the www/html folder, where website data is kept. You have to be careful and check permissions before you start, and then you have to think who will have permissions to upload files there and how the permissions and ownership of the uploaded files will end up.

Do you really need to share the www folder? I mean, how often and by how many people you do updates there?

A quick way to upload files is scp from linux or WinSCP from windows. You already have ssh working and it doesn't need anything more. Now that process works without sharing any folders, you can browse to any path allowed to be opened by the user you are using and copy files there.

If this is for updating your website I would recommend two step process:
1. Use scp or winscp and copy files in your home folder.
2. Log in by ssh and copy the files from your home folder to the destination you need, like /var/www/html.

Would that work for you?

PS. This is a little more elaborate share procedure if you wanna look at it: [http://www.liberiangeek.net/2014/07/ubuntu-tips-create-samba-file-server-ubuntu-14-04/](http://www.liberiangeek.net/2014/07/ubuntu-tips-create-samba-file-server-ubuntu-14-04/)
There are literally thousands of samba share articles on the internet...

---

### Post by scott.bouch on 2016-04-01
You're absolutely right,

Since my last message, I've been able to access the server from my laptop using sftp, and from my windows machine using Bitvise SSH client.

I think I'll be careful as you say - these methods are good enough for what I want to do.

The server is headless, and lives in a cupboard in my garage. I write my webpages form computers in the house, the above methods are fine for that.

Thank you again for your help, I'm glad I didn't start changing permissions!

---

