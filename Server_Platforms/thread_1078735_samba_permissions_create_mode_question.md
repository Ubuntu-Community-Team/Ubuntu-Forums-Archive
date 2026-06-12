---
title: "samba permissions: create mode question"
date: 2009-02-23
forum: Server Platforms
---

### Post by kingaaronj on 2009-02-23
I have a question about my smb.conf file.  I understand the last three digits of the "create mode" option as being permission specifiers.  But what is the first digit?  I have looked in several forums and tutorial sites and often the first digit is a "0" or a "2" but I never see an explanation.  Any ideas? :)

---

### Post by capscrew on 2009-02-23
The create modes are actually OS based.  Samba is only one way of using them.  You an also use chmod from the CLI.

This allows you to set user (suid), set group (sgid), and sticky bit.

See the following:

4000 set-user-ID-on-execution
2000 set-group-ID-on-execution
1000 sticky bit

Set user changes the effective UID to the owner of the file.

Set group changes the effective GID to the owner of the file.

Sticky bit used on a directory allows users to write files in that directory.

They can be added together too.  So you can have sgid and sticky bit with:

3000 sgid + sticky bit set.

The sticky-bit on directories forces the behavior that (within that directory with the sticky-bit set) only the **owner** (and root) of the file can remove the file. This is how /tmp is set up.  The same applies to directories within a directory that has the sticky-bit set. As an example, Bob could also create a directory in /tmp that George can't remove it.

---

### Post by kingaaronj on 2009-02-23
Awesome!  That's exactly what I was trying to find out.  Thankyou :)

---

