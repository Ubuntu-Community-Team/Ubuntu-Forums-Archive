---
title: "I have to chown files copied over my network"
date: 2011-07-13
forum: Security
---

### Post by atomicben on 2011-07-13
I'm sure this has probably been asked and answered a million times but I can't find the right wording to search on because I don't understand the problem.

Here's the setup:
2 computers (A and B)
Computer A has a Samba share (called 'shared') that anyone (everyone) can upload a file to.
From computer B I connect to the share on computer A and copy a file from B to A.
When I go to do something to the file on computer A it has the lock symbol and permissions say owner 'nobody' group 'nogroup'.

Here's my confusion.  On both computer A and computer B I am using the same credentials so if my user name and password are the same on both computers, why to I have to chown it?  Why does it change to 'nobody:nogroup'.  If jdoe owns the file on computer b doesn't jdoe own the file on computer A?


NOTE:  This is NOT a domain.  This is my own simple home network with 2 Ubuntu machines with the same login/password credentials.

My guess?? I suppose that a login name has more to it that I can't see (don't understand) and that ownership of a file is not solely based on the login name.  Perhaps there's hash or metadata or something that is unique - even with the same user names.  Or maybe Samba strips unix credentials.

I guess the easiest place to start is: Is this a Samba thing or a linux security thing (if that even makes sense).

Feed the n00b!

Thanks.

---

### Post by karlson on 2011-07-13
> **atomicben said:**
> 
Here's the setup:
2 computers (A and B)
Computer A has a Samba share (called 'shared') that anyone (everyone) can upload a file to.
From computer B I connect to the share on computer A and copy a file from B to A.
When I go to do something to the file on computer A it has the lock symbol and permissions say owner 'nobody' group 'nogroup'.

Here's my confusion.  On both computer A and computer B I am using the same credentials so if my user name and password are the same on both computers, why to I have to chown it?  Why does it change to 'nobody:nogroup'.  If jdoe owns the file on computer b doesn't jdoe own the file on computer A?


is user jdoe for samba mapped to the user jdoe on Linux?  Also are you sure you are not accessing the share as guest which is being squashed to user nobody.

---

### Post by atomicben on 2011-07-13
> **karlson said:**
> is user jdoe for samba mapped to the user jdoe on Linux?  Also are you sure you are not accessing the share as guest which is being squashed to user nobody.


The samba share 'shared' is setup for access to 'everyone'.  So at least from Sambas point of view, everyone should be able to read and write.  

Locally the folder 'shared' is owned by me (let's say jdoe) but allows 'others' to read/write. However, when other's write the file gets the nobody/nogroup permissions when it's me on the other side sending.  

Also note: if i just copy a file (locally) to that folder it's owned by me.  There are no issues.  So does samba make it 'nobody' or does linux?

I hope that helps you help me.

---

### Post by karlson on 2011-07-13
> **atomicben said:**
> The samba share 'shared' is setup for access to 'everyone'.  So at least from Sambas point of view, everyone should be able to read and write.  
[snip]
Also note: if i just copy a file (locally) to that folder it's owned by me.  There are no issues.  So does samba make it 'nobody' or does linux?

I hope that helps you help me.

I think by 'everyone' you mean guest access.  If you enable guest access and not redefine guest account to something it will be "squashed" to user nobody.   So to answer your question it's samba that squashes the user.

---

### Post by atomicben on 2011-07-13
This demonstrates even more of my ignorance.

In Users and Groups GUEST (and SMBGUEST) accounts are disabled.

In SAMBA, I can select specific users or I can choose to allow 'everyone' for a share (see screenshots).  I allow everyone access (visable/writeable) to my 'shared' folder.

Does enabling access to 'everyone' turn on a guest account that I'm not aware of?

BTW, I'm starting to realize that one of my linux pain-points has always been with Samba.  I just think that sharing should be included in an OS (as opposed to an add on).  I don't think it's very secure (or end-user friendly) to have more than 1 level of security to think about.  Especially when that thinking has to be transferred between M$ and Linux.

---

### Post by karlson on 2011-07-13
> **atomicben said:**
> 
Does enabling access to 'everyone' turn on a guest account that I'm not aware of?

BTW, I'm starting to realize that one of my linux pain-points has always been with Samba.  I just think that sharing should be included in an OS (as opposed to an add on).  I don't think it's very secure (or end-user friendly) to have more than 1 level of security to think about.  Especially when that thinking has to be transferred between M$ and Linux.

you should look at /etc/samba/smb.conf.  That file actually contains the information that the GUI updates, so giving access to "everyone" most likely enables "guest user" access.

As far as security is concerned you have the same level of security in the newer M$ system as you do with Linux/UNIX.  The difference is that because of backward compatibility requirements it allows for easy circumvention of security.

In addition the GUIs on Linux for administration need work([Not just my opinion](http://www.catb.org/~esr/writings/cups-horror.html)).  Reason being is that most administrators configure SAMBA or NFS by editing the configuration files directly rather then using the GUI.

---

### Post by capscrew on 2011-07-14
> **atomicben]
atomicben 	
Re: I have to chown files copied over my network
This demonstrates even more of my ignorance.

In Users and Groups GUEST (and SMBGUEST) accounts are disabled.
[/QUOTE]
Samba users must be Ubuntu users or.... They are "Mapped to 'Bad User' which is by default the system user "nobody" and the group "nogroup".  The bad user can be configured to any user you wish in the smb.conf file.  All the options (and the defaults) are discussed [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

The groups GUEST and (and SMBGUEST) by default have nothing to do with the default Samba configuration.  There is no concept of "guest account" in Samba.  As you have found out said:**
> 

In SAMBA, I can select specific users or I can choose to allow 'everyone' for a share (see screenshots). I allow everyone access (visable/writeable) to my 'shared' folder.

Does enabling access to 'everyone' turn on a guest account that I'm not aware of?
Nope.  When you allow everyone the Samba daemon checks the user login; If the user is not in the database then Samba considers that user to be unknown and it is mapped to the "bad user".  See above for the rest of the scenario.> 

BTW, I'm starting to realize that one of my linux pain-points has always been with Samba. I just think that sharing should be included in an OS (as opposed to an add on). I don't think it's very secure (or end-user friendly) to have more than 1 level of security to think about. Especially when that thinking has to be transferred between M$ and Linux. 

That is not really an option.  Linux is the kernel and SMB is not part of the kernel.  Debin/Ubuntu provide all of the rest of the individual apps that make up the OS.  Samba is just one of the apps (i.e like Gnome, NFS, DHCP, Apache, BIND, etc.)  Samba  is popular, but not used by everyone who installs Ubuntu (Linux).



[QUOTE=karlson]you should look at /etc/samba/smb.conf.  That file actually contains the information that the GUI updates, so giving access to "everyone" most likely enables "guest user" access.
[/QUOTE]See above.  There is no "guest" access.  It more like this: we will call the unknown user "nobody".  If you did not define *guest=ok* in the smb.conf file or "*everyone*" in usershares (at /var/lib/samba) then the unknown user is denied access to the Samba share.

---

### Post by capscrew on 2011-07-14
> **atomicben said:**
> I'm sure this has probably been asked and answered a million times but I can't find the right wording to search on because I don't understand the problem.

Here's the setup:
2 computers (A and B)
Computer A has a Samba share (called 'shared') that anyone (everyone) can upload a file to.
From computer B I connect to the share on computer A and copy a file from B to A.
When I go to do something to the file on computer A it has the lock symbol and permissions say owner 'nobody' group 'nogroup'.

Here's my confusion.  On both computer A and computer B I am using the same credentials so if my user name and password are the same on both computers, why to I have to chown it?  Why does it change to 'nobody:nogroup'.  If jdoe owns the file on computer b doesn't jdoe own the file on computer A?
Technically speaking the answer is no in your case.  The user (UID) on one host is not necessarily the user (UID) on the second host.  The file is actually owned by the UID/GID.  If those numbers don't match you can have problems.  I always setup shares with the group the same (GID) to eliminate that problem.  I don't care who the owners is as long as all files and folders have the group the same and all user are in that group.

It is important to remember that file system rights (Linux) always determine the ultimate rights to a file or folder.> 


NOTE:  This is NOT a domain.  This is my own simple home network with 2 Ubuntu machines with the same login/password credentials.

My guess?? I suppose that a login name has more to it that I can't see (don't understand) and that ownership of a file is not solely based on the login name.  Perhaps there's hash or metadata or something that is unique - even with the same user names.  Or maybe Samba strips unix credentials.

[QUOTE]No hash or metadata.  The user is the owner if he created the file.  The user is a you want to define it (by prior default or configuration) such as in the Samba configuration file.

I guess the easiest place to start is: Is this a Samba thing or a linux security thing (if that even makes sense).[/QUOTE]Both!!!!> 

Feed the n00b!

Thanks.

Edit:> Also note: if i just copy a file (locally) to that folder it's owned by me. There are no issues. So does samba make it 'nobody' or does linux?
Transferring a file locally does not need the services of Samba.  The file ownership is defined only by the file system.  Samba does make the owner "nobody" if it can't ID the user (not in the smbpasswd database).

---

