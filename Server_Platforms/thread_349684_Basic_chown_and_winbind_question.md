---
title: "Basic chown and winbind question"
date: 2007-01-30
forum: Server Platforms
---

### Post by mahalie on 2007-01-30
I have just added my Ubuntu server (dapper drake LAMP) as an Active Directory member server (using these [excellent instructions]("http://ubuntuforums.org/showthread.php?t=280702")). The install and configuration of Samba & Winbind went great but I am stuck now on the very last step, as I'm a total newbie. Can someone explain to me what this means?

```
chown -R 'localdomain\administrator:localdomain\Domain Users' /home/data
```
Following that example, I did the following: 
```
sudo chown -R 'MYDOMAIN\adminuser:MYDOMAIN\all mydomain users' /home/data
```

I don't understand the colon used above, what exactly does this mean? The group 'all mydomain users' can now read (only) the share...right? I would like to make the shared directory /home/data readable by also writable only by the Domain Group 'webmasters'. 

I am able to list users and groups from the AD Domain Controller using [FONT="Courier New"]sudo wbinfo -u[/FONT] but have not figured out how to chmod the /home/data directory properly and the Linux permissions tutorials I've found haven't covered the AD (winbind) specifics to help me figure this out.

I'm not sure if I should be reading chmod tutorials, winbind documentation or ? Any help greatly appreciated! I need to move on to configuring my Apache install soon :D

---

### Post by Brunellus on 2007-01-30
moving this to server talk in the hopes of attracting knoweldgeable eyeballs.

---

### Post by Brazen on 2007-01-30
the colon seperates user owner from group owner.  The syntax is basically "chown user:group /folder/location"

The -R means to be recursive, ie. applying to all files and subfolders under the specified subfolder.

In the example given: 'localdomain\administrator:localdomain\Domain Users', the "administrator" and "Domain Users" should have stayed.  The only part you should have changed is the "localdomain" to the actual name of your domain.  Of course this will make all those files and folders owned by the domain user 'administrator' and the domain group 'Domain Users'.  If you want a different user account or group account to own the files, then you should adjust accordingly.

---

### Post by louieb on 2007-01-30
I don't know much but I do know that the colon is separator between a files owner and group. The chown command  sets the owner and/or group a file belongs to. 
The -R means change ownership recursively.
The colon is the separator between owner and group.

chown has  short set of options just run 
```
info chown
```You may want to look at how to change / set owner group and other permissions. 
```
info chmod
```to view ownership and permissions 
```
ls -l
```

---

### Post by mahalie on 2007-01-30
Thank you for the info! I have been forcing myself to get in the habit of reading the man pages and did get to [FONT="Courier New"]info chown[/FONT]. I guess my confusion is a little more fundamental than the specifics of chown, and is now more of a chown vs. chmod (vs. htaccess?). 

I'm still not sure how to give the webmasters group read/write while all others have read only permission...

---

### Post by Brazen on 2007-01-30
> **mahalie said:**
> Thank you for the info! I have been forcing myself to get in the habit of reading the man pages and did get to [FONT="Courier New"]info chown[/FONT]. I guess my confusion is a little more fundamental than the specifics of chown, and is now more of a chown vs. chmod (vs. htaccess?). 

I'm still not sure how to give the webmasters group read/write while all others have read only permission...

Is the webmasters group a domain group?  If so make that the group owner of the directory ```
sudo chgrp -R 'DOMAIN\webmasters' /path/to/folder
```

chrgrp is just like chown but for only the group, not user, or user:group.  This would be the EXACT same as the above command, but also making sure the owner user is root: ```
sudo chown -R root:'DOMAIN\webmasters' /path/to/folder
```

Now, chmod is for what permissions each of those have.  Each folder or file on a linux computer has three sets of permissions (unless using ACLs which is a whole 'nother can of worms): user/group/everyone.  Each of those sets can have certain permissions, applied with the chmod command, such as 750, would give user read, write and execute, give group read and execute, and give everyone no permissions whatsoever.

.htaccess has nothing to do with file permissions.  .htaccess is for web page options.

---

