---
title: "File / Directory permissions"
date: 2010-01-28
forum: Security
---

### Post by BigSteve_G on 2010-01-28
I'm new to ubuntu / Linux after using Windows NT / 2000 & XP for about 11yrs - Now I'm getting my head around ubuntu slowly but surely (especially with help from on here) - Anyways I've worked out how to setup & control file & directory permissions (although some adviced would be appreciated) but what I'm woundering is in Windows with NTFS I can set files & directorys to inherit access permissions from the parent folder - how do I do this in ubuntu with ext3 or ext4?

Another thing is how do I set a directory so that the owner (root) has full access, one group (photoviewers) has readonly access, another group (photoeditters) has full access & everyone else has no access?

---

### Post by adam814 on 2010-01-28
> **BigSteve_G said:**
> 
Another thing is how do I set a directory so that the owner (root) has full access, one group (photoviewers) has readonly access, another group (photoeditters) has full access & everyone else has no access?

This can be done using ACLs.  I'd recommend installing eiciel, which allows configuring ACLs graphically in Nautilus.

The first part of this guide (before it branches off onto KDE stuff) explains adding the "acl" option for your partitions in /etc/fstab.

I think you can also do the "inherited permissions" thing too with ACLs, just haven't had the need to set it up that way.  I may give it a try now just because it sounds like a good idea.

---

### Post by BigSteve_G on 2010-01-30
- Thanks

The only thing is I'm new to Ubuntu so not sure how to do this - I know a bit about the 'get apt' command to install stuff but not sure what fstab file is that you mentioned.

---

### Post by adam814 on 2010-01-31
This a pretty decent guide to setting up ACLs:
[https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)

But it doesn't mention that you have to add "acl" to the mount options in /etc/fstab.  I'll show you an example from mine.

Press ALT+F2 and type "gksudo gedit /etc/fstab" to open the file in a text editor.  You'll see a line for your "/" partition.  It will look something like this:
```
UUID=f3ad4c7d-7b13-40a4-a24c-1c6ee5b8305a /               ext4    errors=remount-ro 0       1
```

The UUID section will be different.  You'll only make this change:
```
UUID=f3ad4c7d-7b13-40a4-a24c-1c6ee5b8305a /               ext4    acl,errors=remount-ro 0       1
```

If you have a separate "/home" partition or any others you might need to add it for those.  Don't add it for proc or swap or any other OS partitions.

---

### Post by BigSteve_G on 2010-01-31
Thanks for the replies, I think with a bit of experimenting (& a little bit trail & error) I will get there, the only thing is I really need to know if theres a way of setting a files permission to be inherited rather the set it by hand - for example if I have a folder called 'Photos' with 200 files in it rather then set the permissions on all 200 files sepratly I'd rather run one command to set all 200 files to get the permissions from the parent directory (just a thought does chmod work with wild cards?) same as any new files I add.

---

### Post by adam814 on 2010-01-31
"chmod -R /path/to/dir" will change permissions recursively for all files in a directory.

You could also change your umask in /etc/profile if you want to specify different *default* permissions.

---

### Post by BigSteve_G on 2010-01-31
Thanks a lot with a bit of experimenting I've worked out how to set things up, the "chmod -R /path/to/dir" has kind of made things a little simpler for me too - I feel the biggest learning curve for me coming from Windows to Linux is the different terminology (ie, its not "set files to inherit the parent directories permissions" but "set permissions recursively for all files in a directory" - may sound odd but when you dont know the correct terms it can be a struggle finding things out).

Although I was kind supprised that although I'am used to doing this sort of thing the GUI way with windows I found the Linux command terminal easier using chown & chmod & much more my cup of tea

---

### Post by BkkBonanza on 2010-02-01
For basic permissions to inherit from the parent directory you want to check out the setgid bit in chmod. Here is the wikipedia reference,

[http://en.wikipedia.org/wiki/Setuid#setgid_on_directories](http://en.wikipedia.org/wiki/Setuid#setgid_on_directories)

That tells you about how it works. It won't do what you want for multiple groups rights - you need acl, but it is good to know about setuid/setgid for controlling inherited permissions.

---

### Post by BigSteve_G on 2010-12-29
Sorry everyone - I switched to Linux Mint & stopped using this forum - although I'm still using Mint I'm back on this forum as Mint is based on Ubuntu.

Anyways I've got the hang of the permissions thing now thanks to chown & chmod

---

