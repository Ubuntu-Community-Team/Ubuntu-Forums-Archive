---
title: "Seeking advice on multiple user accounts, permissions, etc."
date: 2009-07-12
forum: Server Platforms
---

### Post by nerr on 2009-07-12
Hey everybody, this might turn into one heck of a post, but I'll do all I can to avoid repeating myself.  Please bear with me, hehe. :)

Basically, I'll be setting up a home server box in a few days here.  I want to be able to create a varied array of user accounts for use with different tasks, and I want to be able to prohibit certain accounts from doing anything other than what I would specifically like them to be able to access.

I'm going to need accounts such as the following:

**"admin" group:**
Master administrative accounts, with permissions to all other users' folders and property, as well as sudo and other administrative rights.

**"family" group:**
Users on Windows machines on my local network (family) who will need Samba share access to my dedicated read-only media shares, as well as their own data shares, but no access to other users' shares, or the actual root filesystem itself.  Only their data and media I define to be shared with them.

**"friends" group:**
Friends on remote networks whom I would like to allow to access my defined media shares, and their own small data shares on my server.  SFTP only, no SSH shell, absolutely no sudo.  This will allow them to grab some of my media and perhaps add some data on their own share (with a disk quota), all via SFTP in FileZilla.  I would like advice on how to chroot these users to their own data shares, and then create a soft link to my own read-only media shares, but disallow them from accessing any other resources.  I would very much prefer to be able to log user logins and such, perhaps file transfers if possible, and perhaps impose a bandwidth limit per month, due to limitations with Comcast.[B]

"services" group:[/B]
Dummy users for use with services like rsync to authenticate automatically over SSH and backup other machines, but absolutely restricted from doing anything other than this purpose.  No SFTP login, no SSH (besides tunneling in to perform backups), no sudo, and only privileges to access shares which it will be backing up files to.
EDIT: I should add that I would like to use RSA/DSA key authentication via SSH ONLY for logging in to certain accounts, like the admin or service ones.   All other accounts will just use plain passwords, as they won't have any sort of destructive power, being that they don't have access to sudo or resources outside of their own.  If this is possible, please let me know!  Thanks.


I'm still fairly new to Linux and don't really know where to even start with this, haha.  Any advice on how to set up my user system would be greatly appreciated.  I want this to be very usable, but also locked down tightly enough that nobody can just log into a shell, access sudo, or muck around with anything in my filesystem other than their own shares.  If anybody has a better system in mind for me, please do share your ideas, as it would be greatly appreciated.

Thanks for any advice! :p

---

### Post by nerr on 2009-07-13
Bump?  I'd really appreciate a few links, configuration file examples, or just good ol' veteran advice if anybody has any to offer.  Thank you very much.

---

