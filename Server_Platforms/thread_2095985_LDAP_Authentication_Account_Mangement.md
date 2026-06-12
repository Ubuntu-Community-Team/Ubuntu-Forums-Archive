---
title: "LDAP Authentication: Account Mangement"
date: 2012-12-18
forum: Server Platforms
---

### Post by dr1134 on 2012-12-18
I have two questions concerning PAM and authenticating against LDAP. I am trying to make it so that the creation and deletion of user accounts requires little effort on the admins part.

My first question is their a way that I can delete the user's home directory automatically when they are removed from LDAP?

The second question is there a way to run a script when the user first logins? The purpose of the script is to move files to the user's home directory to help them get started.

---

### Post by dr1134 on 2012-12-24
I solved my second question using /etc/skel directory. Now all I need is to find out how auto delete user's home folders

---

### Post by craigp84 on 2012-12-24
A common way to do this in most UNIX environments is the sysadmins create a script for handling all actions required around adding or removing a user specific to that environment or organisation.

With Ubuntu you don't really need to roll your own - it has always come with one of these scripts out of the box (adduser / deluser - configured via the /etc/adduser.conf and /etc/deluser.conf files respectively). You can add extra commands to them (check the man pages, your commands go in a file under /usr/local/bin) so they allow you to cover most use cases.

Whether you reuse these or roll your own is up to you, but in case it helps, here are some common tasks performed in a custom deluser:

[LIST]
[*]Archive the user's home directory (zip it and move it, or just chmod a-rwx it)
[*]Delete any files owner by that user in any /tmp, /var/tmp or /scratch partitions
[*]Disable any cron or at jobs
[*]Lock the account password, remove any ssh keys
[/LIST]

These actions can become more involved in some environments: e.g. your users home dirs are nfs mounted and you can only do the home dir archiving from a specific host which is able to mount the nfs share with no_root_squash, but hopefully the ideas above are enough to get you going.

---

### Post by dr1134 on 2012-12-25
Ok so if I understand you, I can use deluser to also delete the users ldap entry, yes?

---

### Post by ranger12 on 2012-12-26
I would recommend you install the ldapscripts package and use those. This is what I use and they make life a lot easier for working with ldap accounts. Look in Chapter 7 Section 1 "OpenLDAP Server" subsection 1.11  "User and Group Management" of the Ubuntu Server guide. Hopes this helps.

---

### Post by dr1134 on 2012-12-27
I tried using LDAP Scripts but the problem with it is that it is not playing ball with how I have my LDAP setup for users(Posix Group then Posix Account). So what I will do is just delete the LDAP entry and then the user.

---

### Post by ranger12 on 2012-12-27
Really, I have mine setup with PosixGroup and PosixAccount and I have no issues. I also have other objectclasses in the entries but I have posixAccount in there and have no issues.  There is an entry in the deluser.conf that would force deluser to automatically delete the user's home directory. So just try that and see what happens. I use a ldapadduser template and modified it so when I created ldapusers and could customize what fields get put into the ldap records.

---

