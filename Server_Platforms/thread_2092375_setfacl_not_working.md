---
title: "setfacl not working"
date: 2012-12-07
forum: Server Platforms
---

### Post by flycast on 2012-12-07
I created the user "test" and setfacl:
> setfacl -m u:test:rwx /srv/samba/shares/share

It seems to run with no failure - no feedback.

Running getfacl:
> getfacl /srv/samba/shares/share
Gives these results:
> getfacl: Removing leading '/' from absolute path names
# file: srv/samba/shares/share
# owner: samba
# group: sambashare
user::rwx
user:anotheruser:rwx
group::r-x
mask::rwx
other::---
Running:
> setfacl --test -m u:test:rwx /srv/samba/shares/share
gets:
> /srv/samba/shares/share: *,*

What's going on?

---

### Post by Wim Sturkenboom on 2012-12-08
Looks like it worked for another user. So maybe 'test' is a bad name.

---

### Post by flycast on 2012-12-13
Hmmm...I added a new users and setfacl worked on them. I deleted the user I was having an issue and recreated. It works now.

Not sure what to think but is now resolved.

---

