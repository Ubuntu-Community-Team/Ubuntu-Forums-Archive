---
title: "File permissions, the linux way?"
date: 2012-08-10
forum: Security
---

### Post by fixerdave on 2012-08-10
I do Windows admin for money... working towards Linux because I want to.  I know NTFS, global and local groups, and how to make a Windows server dish out file exactly the way I want.  I want to be that way in the Linux world.

I have a reasonable handle on the Linux user:group stuff, the tools, etc. I've been running home shares from a Linux server for several years and managed to get both NFS and Samba working.  I know I could implement ACLs and work the way I do in Windows.  However, I've learned over the last while that while I can beat Linux into sort of working like Windows... that's generally not the right way to go.

Are there any decent guides for how to set up share/group structures in Linux the Linux way?  I mean, if I've got 2 or more groups of people... how do I grant them different permissions to the files in the same folder?  Yeah, ACLs will do it... but I expect people have been doing that in Linux long before ACLs were implemented.  

What's the Linux way?  Multiple shares to the same files?  Symlinks?  What?  How would old-school Linux gurus manage a bunch of group data on a server?

David...

---

### Post by 2F4U on 2012-08-10
ACL's are not invented by Windows. As far as I understand it, it is an overarching concept supported by unix and unix-like operating systems as well as Windows.

[http://en.wikipedia.org/wiki/Access_control_list](http://en.wikipedia.org/wiki/Access_control_list)

---

### Post by claracc on 2012-08-10
Take a look: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by fixerdave on 2012-08-10
> **claracc said:**
> Take a look: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

From that page:
> 
ToDo
...
In other words, this page does the nuts and bolts ok, but we need to describe what the permissions should be. 
...


Which is kind of where I'm at.

I mean, yes, I don't mind using ACLs.  But, if ACLs were just the way to go then why all the fuss about user/group/other?  The entire OS manages to get by just fine without ACLs, so I feel like I must be missing something.

Put another way, something like: "accounting people get rw, payrole gets ro, and everyone else gets denied" can't be that hard.  I expect there's a perfectly reasonable way to do it with user/group/other permissions, but I can't see it.  Am I missing something or do people running up Linux servers just run ACLs whenever stuff like this comes up?

David...

---

### Post by bab1 on 2012-08-10
> **fixerdave said:**
> From that page:


Which is kind of where I'm at.

I mean, yes, I don't mind using ACLs.  But, if ACLs were just the way to go then why all the fuss about user/group/other?  The entire OS manages to get by just fine without ACLs, so I feel like I must be missing something.

Put another way, something like: "accounting people get rw, payrole gets ro, and everyone else gets denied" can't be that hard.  I expect there's a perfectly reasonable way to do it with user/group/other permissions, but I can't see it.  Am I missing something or do people running up Linux servers just run ACLs whenever stuff like this comes up?

David...

The default Linux permissions for EXT2/3/4 are user centric. These need to be configured to allow inherited group permissions. This is accomplished by setting the GID bit (SGID).  It allows you to control access via the group permissions rather than the user permissions.

Here is a [**_[COLOR="DarkSlateGray"]google search[/COLOR]_**]("https://www.google.com/search?q=bsd+style+group+permissions&btnG=Go!#hl=en&gs_nf=1&gs_mss=sgid%20bs%20group%20permissions%20for%20linux&tok=5A5U-fERd5UJr5zX0WuMzQ&pq=bsd%20style%20group%20permissions%20for%20linux&cp=8&gs_id=34p&xhr=t&q=sgid+bsd+group+permissions+for+linux&pf=p&sclient=psy-ab&oq=sgid+bsd+group+permissions+for+linux&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ce106b493fe37127&biw=1230&bih=679") on the topic.

---

### Post by lukeiamyourfather on 2012-08-10
If the server and client are both *NIX and the user ID is the same then the *NIX permissions will work as expected (read, write, execute). If using network authentication the user ID can be mapped to match the domain so they are consistent across all systems. So user 1293 on the server is the same as user 1293 on the client, and another user with a different ID will have different permissions and vice versa. Same goes for group ID (uid and gid are the short form).

---

### Post by fixerdave on 2012-08-10
> **bab1 said:**
> The default Linux permissions for EXT2/3/4 are user centric. These need to be configured to allow inherited group permissions. This is accomplished by setting the GID bit (SGID).  It allows you to control access via the group permissions rather than the user permissions.

...

Yes, I've been through that and can have new files in a directory get the directory group rather than the user default group.  No problem there.

> **lukeiamyourfather said:**
> If the server and client are both *NIX and the user ID is the same then the *NIX permissions will work as expected (read, write, execute). If using network authentication the user ID can be mapped to match the domain so they are consistent across all systems. So user 1293 on the server is the same as user 1293 on the client, and another user with a different ID will have different permissions and vice versa. Same goes for group ID (uid and gid are the short form).

Yes, I've been through this too, though being a small home network I've just been manually creating local accounts with the uid/gid to match the ones on the server.  I'm currently experimenting with NFS shares that root_squash to anonuid/anongid... all makes sense, though the details can get finicky.

I do (I think) have a reasonable understanding of the mechanics.  What I'm missing (again, I think) are the " best practices" for what to do with them.

If you were going to run up an enterprise file server, how would you manage group share permissions?  Back to the example: A directory full of files, Accounting users get read-write, Payroll users gets read-only, and everyone else gets access-denied.  How would a SysAdmin do that on a Linux server?

Multiple shares/mounts?  ACLs, something else?

David...

---

### Post by unevenflow on 2012-08-10
Hey,
ACLs do the work for me just fine.

---

### Post by bodhi.zazen on 2012-08-12
> **fixerdave said:**
> From that page:


Which is kind of where I'm at.

I mean, yes, I don't mind using ACLs.  But, if ACLs were just the way to go then why all the fuss about user/group/other?  The entire OS manages to get by just fine without ACLs, so I feel like I must be missing something.

Put another way, something like: "accounting people get rw, payrole gets ro, and everyone else gets denied" can't be that hard.  I expect there's a perfectly reasonable way to do it with user/group/other permissions, but I can't see it.  Am I missing something or do people running up Linux servers just run ACLs whenever stuff like this comes up?

David...

Most people do not feel they need more then the standard ownership / permissions.

If you need finer control, then yes, acl is the tool you want.

If you need finer control then even acl, I would advise selinux 

See: [http://blog.bodhizazen.net/linux/selinux-mcs/](http://blog.bodhizazen.net/linux/selinux-mcs/)

You of course match your security needs vs ease of use. Again, in your user case, acl are the way to go. 

If you want a graphical tool to manage acl, use Eiciel

---

### Post by fixerdave on 2012-08-13
> **unevenflow said:**
> Hey,
ACLs do the work for me just fine.

> **bodhi.zazen said:**
> Most people do not feel they need more then the standard ownership / permissions.

If you need finer control, then yes, acl is the tool you want.

If you need finer control then even acl, I would advise selinux 

See: [http://blog.bodhizazen.net/linux/selinux-mcs/](http://blog.bodhizazen.net/linux/selinux-mcs/)

You of course match your security needs vs ease of use. Again, in your user case, acl are the way to go. 

If you want a graphical tool to manage acl, use Eiciel

Thank you... I guess that settles it.  I'm not missing something and if I need permissions on one directory that involve more than one group (or similar) then ACLs are the way to go.  

It's kind of refreshing actually... normally when I ask a question the answers I get back are so simple I wind up kicking myself for missing the obvious.  Some days I actually feel like I'm getting there... kind of makes up for the other days.

Thanks again for all the responses,

David...

---

