---
title: "Restrict Filedelete of Samba Profile"
date: 2013-04-24
forum: Server Platforms
---

### Post by Bathroth on 2013-04-24
Hey guys,

at the moment im doing some Samba Shares and profiling with PDC.

Now im at the point where my boss wants that noone can delete any files from their profile. They need to be allowed to create modify but not to delete.
I also searched on google if i find something. I also tried the "sticky bits" but the users still can delete their files!

> [profile]
path = /home/samba/profiles
valid users =%u
create mask = 1700
directory mask = 1700
force create mode = 1700

I checked the files i created from my testaccount.

it got a T so the sticky bit is sucessfully enabled.

But what am i missing here?

I guess that its because of the synchronisation. I got the permissions in Unix. After closing the session Samba checks the files and synchronises. But not contributional - he deletes the files which he cant find on the "right" side right?

Have someone an idea about this? also i read about umask but im not sure how i can use them for my problem.

Please help me!

Greets

---

### Post by SeijiSensei on 2013-04-25
I don't think you can do what you want with normal POSIX permissions.  Usually if I can create or modify a file, I can also delete it. You might take a look at [Access Control Lists]("http://bencane.com/2012/05/acl-using-access-control-lists-on-linux") as another option.  They provide more fine-grained control.  You may need to include some "acl" directives in [smb.conf]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") as well.

---

### Post by Bathroth on 2013-04-25
> **SeijiSensei said:**
> I don't think you can do what you want with normal POSIX permissions.  Usually if I can create or modify a file, I can also delete it. You might take a look at [Access Control Lists]("http://bencane.com/2012/05/acl-using-access-control-lists-on-linux") as another option.  They provide more fine-grained control.  You may need to include some "acl" directives in [smb.conf]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") as well.

Thanks so far for the advice.

Till now didnt had the time for check it out. If someone else have any ideas. Im open for everything.

SeijSensei - ill check ACL when ive got time. Thanks so far!

Greets

---

