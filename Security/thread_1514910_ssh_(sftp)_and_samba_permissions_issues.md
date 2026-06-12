---
title: "ssh (sftp) and samba permissions issues"
date: 2010-06-21
forum: Security
---

### Post by redstarmachineworks on 2010-06-21
I've never found an answer to this, but when searching I see that this seems to be a very common problem.

Short story: I've built up a fileserver using Ubuntu 10.4 and installed and configured Samba and OpenSSH. My plan is to have clients upload files to a folder via SFTP. Those files could then be accessible via a Samba share for access by local Windows and Mac workstations.

My plan was to create a user account for each client and have them upload files to an "upload" folder, which I think should be set up as a symbolic link to a share folder not located in their home folder.

What happens is that I can upload files via SSH into the upload folder, which is a link to a share at /media/storage. So the link looks like this:

/home/user/upload > /media/storage

That works so far. I can upload files. From the Windows network I can browse to and create files on this shared folder. 

But then things break. When I upload files via SFTP, the permissions are set to -rw-r--r--, thus rendering all the files on the shared folder to read-only.

How can I maintain permissions here?

Here's a copy of my smb.conf file:

#======================= Global Settings =======================

[global]
  workgroup = WORKGROUP
  server string = %h server (Samba, Ubuntu)
   dns proxy = no
follow symlinks = yes
wide links = yes
unix extensions = no

log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

[storage]
	comment = Welcome aboard, Citizen!
	path = /media/storage
	browsable = yes
	guest ok = yes
	read only = no
	create mask = 0755
	writeable = true

---

### Post by doas777 on 2010-06-21
I believe you need the Directory Mask line in your smb.conf

```

create mask = 0644
directory mask = 0755

```
tweak the values as needed, and put them in the global section. you may have to choose between a global create mask, and one defined on the share as you have shown.

for my samba shares, i add users to the group 'users'. then I set my samba folder to be owned by <a user>:users (it doesn;t matter what the user is, it's the group that is key). last I set the permissions on the folder to 2765 which turns on SetGID for the folder. this causes all files created in the folder to use the ownergroup listed on the folder. 

since all my users are in the 'users' group, they all get access to the folders.

---

### Post by redstarmachineworks on 2010-06-21
Some progress here, but no joy yet.

I'm not quite getting the permission parity that I want to get, but at least userx can upload files and then same userx can browse for and modify them on the local network.  This will probably get to be a problem when I have many local network users modifying the same file.

I created a group called sambausers and added my two test accounts into that group. Also, running a chmod 2765 /media/storage doesn't work. It prevents the sftp userx from copying files into the upload folder. The permissions it creates is:

drwxrwSr-x  4 root sambashare 4096 2010-06-21 11:05 storage

thanks!

---

