---
title: "samba sharing write permissions"
date: 2012-09-11
forum: Server Platforms
---

### Post by geminiscorpio on 2012-09-11
Hello!

I have a computer running ubuntu 10.04,and want share some folders on it.The operating system is on one hdd and i have other 2 hdd in RAID1.Everything looks and acts ok until I try to share a folder.
I can see all sharings, but I get access denied everytime I try to write logged in as user and not as root no matter the location of the folder (Raid or users home). I forgot to mention that I want an xp user to write in a specific folder on the ubuntu computer.The only situation I can write is when I share [homes] using samba, and the folder is located on /home/user/desktop/sharedfolder
This is strage because from xp I can see both folders.When I try to write directly to sharedfolder I get "Acces Denied".When I browse for it in /homes/Desktop/sharedfolders I can write loged in as user.

What am I doing wrong?

In smb.conf the sharing looks like this:

[sharedfolder]
path = /home/user/desktop/sharedfolder
writeable = yes
create mask = 0775
directory mask = 0775
valid users = user

Thank you!

---

### Post by SeijiSensei on 2012-09-11
Samba will execute file operations with the username that matches the Samba username (unless you use some of Samba's more arcane name-mapping features).  So either all the Samba users need to have Unix write privileges on the exported shares, or you have to take another approach.

One is to put all the Samba users into a Unix group and grant the group write privileges on the share.  I find, though, that the Samba directives "force user" and "force group" offers a simpler solution in cases like these.

Set up the share so it is owned by a user with full privileges.  Let's call this user "sharemgr".  Create a Unix account for sharemgr and use "chown" and "chgrp" to grant sharemgr full access to the exported share.  Now in Samba, add these lines to the definition for [sharedfolder]:

```

force user  = sharemgr
force group = sharemgr

```

Now restart Samba.  You should now be able to read and write to this share with any valid Samba username.  

The drawback to this approach is that all the files will be owned by sharemgr and not the individual users themselves.  If it is important for auditing purposes that you know which files were written by bob and which by shirley, then this method will not work for you.  If you don't care about tracking ownerships, then this is a simple and convenient solution.

---

### Post by geminiscorpio on 2012-09-12
Thank you for the prompt answer.I'll try that and reply.

---

### Post by geminiscorpio on 2012-09-13
Worked like a charm.Thanks again.

---

