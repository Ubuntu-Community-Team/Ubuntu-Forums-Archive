---
title: "Multiple users using same folder"
date: 2008-06-25
forum: Security
---

### Post by frediE on 2008-06-25
hope this is quick and easy and maybe i just missed something about linux security permissions on files and folders....

"Folder" has security permissions 770
owner is root
group is family
the family group has user1 and user2


when user1 writes creates a file in the "Folder" user2 does not have full access?  i feel like i need to keep resetting the permissions -R to the folder and files to keep everyone happy.

the new file is set to owner user1 read write / group family readonly / other readonly.


++ basically i would like a Folder, that is locked down for ONLY the family, they can create files in that Folder, and the other family members will have full access to those files. ++

thanks for the help, understanding, guidance, wisdom, or what ever i can get.  :-)

---

### Post by HalPomeranz on 2008-06-25
Your problem is that when one person creates a file in the "Folder" the file won't automatically be owned by the "family" group.  Instead it will end up being group-owned by whatever group that user is assigned to in /etc/passwd (under Linux, this is normally a personal group that nobody else is a member of).

However, you can change this behavior by setting the "set-GID" bit on your folder ("sudo chmod g+s Folder").  When set-GID is set on a directory, then any time a file is created in this directory it ends up inheriting the group ownerships of the directory rather than the group owner of the user creating the file.  This is exactly what you want in this case.

---

### Post by frediE on 2008-07-03
not to take it up a notch, but is there a way to do this on the whole disk?  its my second drive for data.

---

### Post by HalPomeranz on 2008-07-03
> **frediE said:**
> not to take it up a notch, but is there a way to do this on the whole disk?  its my second drive for data.

```

sudo chgrp -R familygroup /some/mountpoint
sudo find /some/mountpoint -type d -exec chmod g+s {} \;

```

Replace "/some/mountpoint" in two places above with the path where your drive is mounted, and "familygroup" with the group name of the group you're using to share files.

---

### Post by frediE on 2008-07-03
Awesome!  looks like the family group is sticking and i like it.

one.... hopefully last thing... :-)

the security is changing from drwxrws--- to drwxr-xr-x so the family group is loosing the write permissions on new files/folders.  any way to get more sticky?  (ok that was a bad joke)


if a user1:group1 creates a file in a folder i would like user2:group1 to have full (or same) access.  so... 770 on the folder.  possible?

---

### Post by HalPomeranz on 2008-07-03
I'm assuming here that you're sharing your folder(s) using Samba (this is what you get if you right-click a folder and select "Sharing Options" in the Nautilus file browser).

You need to edit your /etc/samba/smb.conf file and set the following options:

```

directory mask = 0770
force directory mode = 2770

```

The "directory mask" option is used first to sanitize the permissions bits on newly created folders-- this allows us to strip off the permissions bits for the "other" category (the trailing zero on "0770").  Then "force directory mode" is applied to the resulting mode bits-- this allows us to add the set-GID bit (set-GID is the leading "2" in "2770") and make sure that all bits are set for owner and group (the "77" in "2770").  This should result in all new directories having mode 2770, or "rwxrws---".

You'll then need to restart Samba after changing the smb.conf file-- "sudo /etc/init.d/samba restart".

---

### Post by frediE on 2008-07-15
everything is ssh.  i either ssh to the box via terminal or connect to server via nautilus.  i looked in the sshd_config but didn't seen anything related.  

i can feel we are getting close... kind of fun.  :-)

---

### Post by HalPomeranz on 2008-07-15
> **frediE said:**
> everything is ssh.  i either ssh to the box via terminal or connect to server via nautilus.  i looked in the sshd_config but didn't seen anything related.

Oh, in that case it's simply a matter of making sure the default umask setting doesn't strip out the group write permissions.  That probably sounds like greek, but the solution is straightforward:

1) Edit the /etc/profile file

2) The last line probably looks like "umask 022".  Change this to "umask 002"

3) Save the file

4) The changes will only take affect upon the next login, so force everybody to log out and/or close their nautilus sessions.

From that point on, any new files that get created should be writable by everybody in the group.

What's going on here is that umask controls what permissions bits get set on new files.  The default is 666 for regular files or 777 for executables.  But you subtract the umask value from the default value to figure out the actual permissions are set.  So with a "umask 022" setting files will be created with permissions 644 (rw-r--r--, "r" is 4, "w" is 2, "x" is 1).  However, with "umask 002" you end up with files set to 664 (rw-rw-r--), which is what you want.

---

### Post by hyper_ch on 2008-07-16
another approach would be using SSHFS and setting uid and gid upon the connection.

---

### Post by kvmreddy on 2010-03-29
Check bellow link, I explained how to create shared group with an example.

[http://bashscript.blogspot.com/2010/03/creating-user-group-and-shared.html](http://bashscript.blogspot.com/2010/03/creating-user-group-and-shared.html)

---

