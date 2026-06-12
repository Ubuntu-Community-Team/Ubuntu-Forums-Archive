---
title: "Groups and permissions cancel out settings."
date: 2016-04-07
forum: Server Platforms
---

### Post by will105 on 2016-04-07
Hi All!

I have a problem that i, for the life of me, can´t seem figure out.

I have Ubuntu Server 14.04.4 with webmin and samba.
I have both user and guest access setup.

However, to get the users permissions to function properly, every user has to have their
own group with the same name as the user, as their primary group.

This creates a problem for me, as all the files/directorys they create, are owned by their own private group.
So for the other user accounts to have the right permissions to a file, they have to have the creators group as their primary group.

But then every file they create are created with the wrong permissions, and so on.

Samba config output: 
```
[global]    security = user
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    map to guest = bad user
    max log size = 1000
    unix password sync = yes
    write raw = no
    create mode = 0777
    usershare allow guests = yes
    passwd program = /usr/bin/passwd %u
    create mask = 0777
    obey pam restrictions = yes
    passdb backend = tdbsam
    directory mask = 0777
    os level = 255
    public = yes
    dns proxy = no
    write list = @personal
    server role = standalone server
    preferred master = yes
    read raw = no
    pam password change = yes
    netbios name = Atlas
    workgroup = media.huset
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    log file = /var/log/samba/log.%m
    panic action = /usr/share/samba/panic-action %d
    writeable = yes
```

In my test server i have also tried:
```
    directory mask = 0775    force directory mode = 0775
    directory security mask = 0775
    force directory security mode = 0775
    create mask = 0775
    force create mode = 0775
    create security mask = 0775
    force create security mode = 0775
```

Is there a simple solutions to this problem that i´m not seeing?

---

### Post by darkod on 2016-04-07
I'm no samba expert but in your place I wouldn't put create mask and directory mask in the [global] section. It should be used in the share definition, that way you can have different masks for different shares. That's first.

Then, for the problem of created files being owned only by particular group/user, you can create one (or more) common group(s) and set users as members of those groups. Then in the share definition use something like:
```
create mask = 0664
directory mask = 0775
force group = <groupname>
```

The create mask is used for files and never use 775 or 777 for it. That will make all newly created files executable, when in reality you rarely need executable files. The bit 1 is for execute or search when applied on folders. That's why folders should have it (so that they can be opened) but files no. Use 775 for folders and 664 for files.

The force group will make all files being created as created by that group. Then each member of the group will have Write permissions because you used mask 664 which gives RW to user and group and R to everyone else.

Would something like that work for you?

Don't forget that linux permissions are separate for samba permissions so it will be important that the path where the share is to be also RW for all users and groups that will need to use it.

For the group membership you can also use the sticky bit on a folder and if I'm not mistaken that makes all files created in it to have same group membership as the parent folder.

PS. I just checked smb.conf man page, create mode is synonym for create mask, so don't use both. Makes confusion. Use just create mask and directory mask, and drop any unnecessary settings from smb.conf. It looks like it can be cleaned up little. Start small and then add complexity...

PPS. Also, one important thing: The force directory mask and force create mask are used in a different way. You should not set them to 775. By default they are 000 and leave them alone. Control the permissions without the 'force' only with the standard 'directory mask' and 'create mask'.

---

### Post by bab1 on 2016-04-07
Adding a little bit to @darkod's excellent advice;  the user group for the share directory does not need to be the primary group for any user as long as the user is a member of the group-owner of the share.  The problem is that you need a mechanism to override the users primary group when that user **creates ** or modifies the file or adds a new directory.  You can use "force group".  However if you or your users use NFS or ssh to the server they will not have the services of Samba so "force group" won't be used.

I recommend you set the user group ownership on the shared directory and set SGID that directory.  This will cause Linux to always set the group ownership on files and directories to the user group you have set at the root of the share.  This way is Samba does not work or is not being used you still have the correct user group on shared files and directories.  I manage the share content by ssh login, my users have both Samba and NFS access.

---

### Post by will105 on 2016-04-08
Thank you so much! 

I had'nt even thought of looking at "force group" or researching what the sticky bit really does.

There will only be 1 account for ssh to the server so i don't THINK that will be a problem. &#128519;

I will implement the changes come monday.

Have a nice weekend, both of you!

---

### Post by SeijiSensei on 2016-04-08
Just a reminder that making directories and files group-writable means that any group member can delete files created by another group member.  That's fine if you trust your users, but not so fine if one of them wants to be malicious.

---

