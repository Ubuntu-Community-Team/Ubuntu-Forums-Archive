---
title: "User groups"
date: 2008-09-11
forum: Security
---

### Post by Drezard on 2008-09-11
Ok setting up a server for my parents business. What I want to know, is how do I edit group permissions on a file. Like I know how to edit the permissions of the group that owns the file... but say i have 3 groups, accounting, management and employees. I want management to have wrx permissions to file.txt, i want accounting to have just r access to file.txt and I want employees to have NO access to file.txt.

How do I set something like this up?

Daniel

---

### Post by Paul41 on 2008-09-11
I have never done this but was curious as to how and it looks like you can do it with ACL.

[https://help.ubuntu.com/community/FilePermissions#ACLs](https://help.ubuntu.com/community/FilePermissions#ACLs)
[https://help.ubuntu.com/community/HelpOnAccessControlLists?action=show&redirect=HelpOnAcl](https://help.ubuntu.com/community/HelpOnAccessControlLists?action=show&redirect=HelpOnAcl)

---

### Post by ilrudie on 2008-09-11
+1 for ACL

---

### Post by paulg on 2008-09-11
I hadn't heard of ACL previously so thought I'd post explaining my thought process on why file access with uid:gid probably isn't enough and the tutorial that helped me make sense of ACL.

My original thought was that if you only have 3 groups then you could think of them as 'owner: group: other' and set your permissions such that they are equivalent to 'management: accounting: employee' (e.g. chmod 0740 = -rwxr-----). However there would be limitations to that if it's applied universally where management might actually be able to change permissions to gain access to anything unless you replace the owner with someone other than management but then you're getting into file-by-file or directory by directory permissions changes (e.g. setting ownership in terms of accounting: management: employee). If there's a lot of files/directories with different requirements it's going to quickly become complicated and as a result, probably not as secure as you'd probably like. If your needs are simple and unlikely to vary much, then it might work. [Setuid and setgid]("http://www.gnu.org/software/coreutils/manual/html_node/Directory-Setuid-and-Setgid.html") might help make this more usable so you can set it up per directory but it will always have poor flexibility even if you can figure out a way to make it work for you. The advantage of this is that you can set it so that all new files in a directory have the same permissions. For my home system this works well because I only have a few users so shared files are owned by root with my users given appropriate level of access through the GID and only users I approve are added to this group.

So I looked at the ACL examples. The links provided didn't make a lot of sense to me or tell me how it worked and the second link seemed to cover webpage creation (sorry Paul41, away from my system so 'man acl' is of no use to me ;)). The key description of 'fine grain permissions' kept me going, so with the assistance of google I found a little tutorial that describes *exactly* what I think Drezard is trying to do in terms that even I understand. Actually, seems like something potentially useful to implement on any shared storage or system. 

[http://linuxcommando.blogspot.com/2007/12/basic-linux-permission-model-lets-you.html](http://linuxcommando.blogspot.com/2007/12/basic-linux-permission-model-lets-you.html)
[http://linuxcommando.blogspot.com/2008/01/part-2-how-to-work-with-access-control.html](http://linuxcommando.blogspot.com/2008/01/part-2-how-to-work-with-access-control.html)

Where I see potential for this on my system, and I'm not sure this is 100% possible, but I'm thinking I can mount my backup partition in ACL mode allowing only the system to copy files to it (rsync script) and then assigning only read permissions per owner:group permissions assigned and no access to others - this I know I can do. What I am unsure of, but my current understand is that the regular, non-ACL permissions will be maintained when restored from the backup drive to the regular drives I have that aren't mounted to support ACL such that normal execution/read/write permissions should be returned per owner group and other settings(?). I see more reading in my future...

---

### Post by Drezard on 2008-09-12
Ok. So I kind of get it. But say if I wanted to Jail to their group directory only (like /groups/groupname/ yes, its not a default directory) using SSH. Do I use ACL's?

Daniel

---

