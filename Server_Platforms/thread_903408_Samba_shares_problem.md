---
title: "Samba shares problem"
date: 2008-08-28
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-08-28
Having a wee bit of trouble configuring samba on my ubuntu server
I configured my smb.conf as below but am unable to write to the directory. Am I doing something silly?

ta,

extract from /etc/smb.conf
```
[Company Files]
	path = /media/80gbhdd/Company_Files
	comment = Company Documents 
	read only = No
       create mask = 0770
       directory mask = 02770
       inherit permissions = Yes
        write list = paul
        valid users = paul
```
        
the /media/80gbhdd is set to permissions 770

---

### Post by G1ZmO65 on 2008-08-28
Think I've solved it.

I had set the 80gbhdd dir to 777 but it hadn't set the subdirectories.

Just on this though. I have some unix groups which I want to allow write access to the folder and others who should only get read access.

Am I supposed to do this through the samba config or via the cli CHMOD for the folder?

Thanks

---

### Post by G1ZmO65 on 2008-08-28
Hmm right, possibly answering my own question again:

My user (paul) is part of the unix group companySTAFF

When I have the write list and valid users set to paul I can write to the directory from my windows box but when I have it set to as it is below I cannot even browse the folder.

This says to me that the unix group names are not valid for Samba shares. Correct asssumption?

If so I need to figure out how to create users and groups for samba.

```
[Company Files]
	path = /media/80gbhdd/Company_Files
	comment = Company Documents
	read only = No
       create mask = 0770
       directory mask = 02770
       inherit permissions = Yes
        write list = @companySTAFF
	valid users = @companySTAFF
```

---

### Post by G1ZmO65 on 2008-08-29
Ok I have created 1 or 2 Samba users using smbpasswd -a username

I now understand that to enable some sort of folder read/write permissions by GROUP I need to set up either LDAP, Active Directory or Kerberos.

Can someone advise me on the easiest of these to impliment? and maybe point me in the direction of a good "how to"?

Another wee issue I have is that when I write to a directory on the linux server e.g. create a new folder, it doesnt appear unless I refresh the windows explorer! I'm guessing that this is something that might be resolved with the above configuration but can anyone explain WHY this happens?

Thanks

---

### Post by brad8266 on 2008-08-29
Implementing LDAP just to use group file sharing is going to be a waste, just do your shares by user. Setting LDAP to work with Samba is a pain and you will be introducing a domain controller on the network also.

---

### Post by G1ZmO65 on 2008-08-29
Is it not possible to use the unix groups with the samba server? Wondering what the point of the unix groups are....

I'd really prefer to allow directory access at a group level so that a new user can be just added to a group rather than having to change the permissions for every folder when theres a new user.

---

### Post by brad8266 on 2008-08-29
I have my samba shares set to a group but I also have some users added to the share too. Ill have to try it with just the group to check.

---

### Post by G1ZmO65 on 2008-08-29
How is a samba group created from the CLI?

I know there was an option in webmin but I have dispensed with that in order to learn the CLI properly.

---

### Post by G1ZmO65 on 2008-09-01
I'm really stuck here.

Can anyone tell me how to create a Samba group from the CLI?

I have looked through the Samba configuration docs and can't see how to do it.

I see there's a program called SWAT for configuring Samba but I really wanted to be able to do it via the CLI to gain the knowledge.

Thanks,

---

### Post by mbeach on 2008-09-01
G1Z, I had the same problem awhile back after and never really solved it.  I don't think (not 100%) that there is a smbgroup.  I ended up using a long list of users which got me through the requirement, but indeed not a fantastic solution.

I also had some issues with a "force group" setting after upgrade to Hardy [still unresolved but not causing me much grief].  I was getting an error when attempting to connect from a windows machine "The group name could not be found".  I never even thought about smb groups (assumed linux group was what was being referred to).

I'll see if a month makes a difference in my ability to solve this one.

---

### Post by G1ZmO65 on 2008-09-01
Thanks mbeach,

This is really doing my head in lol

I've even reinstalled webmin to try to understand it but still failing.

I cant find a place in webmin to add the samba users to the samba groups.

All I want is to be able to have folders shared on the linux server that have group permissions to save me using the "long list of users" method.

I'd have thought this was a simple requirement but it seems not and it looks like there arent many folk with answers. :(

pretty stumped and fed up now! :confused:

---

### Post by mbeach on 2008-09-01
G,
There is no samba group that I can find (in the context you are talking about, one that is similar to using smbpasswd to create samba users).  Samba does use the *nix groups.

I do believe, however, you are wanting to use the "force group" setting in the section of the share in smb.conf.  Something like:
force group = companystaff

In trying something similar on my Hardy machine, I'm running into a problem which is presented on the Windows side as the "Group name could not be found".  Looking in my logs in /var/logs/samba I see that I'm getting errors like:
```
[2008/09/01 13:10:14, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/09/01 13:10:14, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

This eventually brought me around to looking at the Samba howto:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html)

I'm sure the answer to my issue is in there, but I've run out of time for this morning.

I'm also digging through:
[Google search: site:www.samba.org "force group"]("http://www.google.com/search?q=site%3Awww.samba.org+%22force+group%22")

Version of samba I'm dealing with:
smbd -V
Version 3.0.28a

Perhaps someone else has some info in the meantime.

---

### Post by mbeach on 2008-09-01
by the way, you may also want to try:
create mask = 0755
directory mask = 0755

then restart
sudo /etc/init.d/samba restart

---

### Post by bab1 on 2008-09-01
I see you have 2 posts on the same subject.  See: [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=907168").

Which thread do you wish to use?

---

### Post by G1ZmO65 on 2008-09-02
I've marked the other thread as solved bab as it only really concerned the gui and will persist with this thread.

Thanks

---

### Post by G1ZmO65 on 2008-11-04
With regards to SAMBA and ACLs, someone pointed me to this webpage:
[http://www.bluelightning.org/linux/samba_acl_howto/](http://www.bluelightning.org/linux/samba_acl_howto/)

Now, this was written in 2003 and I'm assuming is a little out of date. Can anyone tell me:

1: Is the ability to deal with ACLs inbuilt into the more recent Samba versions and/or do I need to update my Samba to a different version?

2: It says "I have assumed you are joining to a Windows 2000 domain which is using Active Directory, you aren't trying to use Samba as a domain controller, and that you're using ext2 or ext3 on Linux." - Do I HAVE to use a PDC on our network to use ACLs or can I do it with the server just acting as a bog standard fileserver?

Thanks

Paul

---

### Post by bab1 on 2008-11-04
> 1: Is the ability to deal with ACLs inbuilt into the more recent Samba versions and/or do I need to update my Samba to a different version?

ACL's are O/S file system settings.  They are not Samba specific.

You can install ACLs with: ```
sudo apt-get install acl
```

> Do I HAVE to use a PDC on our network to use ACLs...?  Not that I know of.

A good ACL howto can be found [[COLOR="Blue"]**here**[/COLOR]]("http://beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists?tmpl=component&print=1&page=")

---

### Post by G1ZmO65 on 2008-11-05
Thank You Bab :)

I'll have a good read at that and let you know how I get on

Cheers

Paul

---

