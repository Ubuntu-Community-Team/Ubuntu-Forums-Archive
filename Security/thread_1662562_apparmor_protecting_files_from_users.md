---
title: "apparmor protecting files from users"
date: 2011-01-08
forum: Security
---

### Post by freemant on 2011-01-08
Hi,

It seems that AppArmor can't be effectively used to protect read access
to files from users (including roots). It is possible to create a profile
for, eg, 'cat', but then the users can use 'less'.

Is this true? Should use SELinux instead for this?

Thanks!

---

### Post by CharlesA on 2011-01-08
What are you wanting them to not have read access to?

---

### Post by bodhi.zazen on 2011-01-08
> **freemant said:**
> Hi,

It seems that AppArmor can't be effectively used to protect read access
to files from users (including roots). It is possible to create a profile
for, eg, 'cat', but then the users can use 'less'.

Is this true? Should use SELinux instead for this?

Thanks!

Depends on what you are wanting to do and how familiar you are with selinux.

I restrict users with "jailbash"

[http://ubuntuforums.org/showpost.php?p=9799756&postcount=5](http://ubuntuforums.org/showpost.php?p=9799756&postcount=5)

Jailbash would restrict root as well (assuming you set jailbash as roots default shell).

IMO the advantage of selinux is that it is more mature, meaning more tested and there are more default policies then apparmor. There are also better tools to manage selinux.

BUT writing a selinux policy form scratch can be a bit of work.

The advantage of apparmor is that the syntax is very easy to learn, but you often have to write your own policies and at times documentation and debugging tools are lacking.

---

### Post by freemant on 2011-01-08
Thanks for the replies. What I'd like to do is to protect the DB access credential (in a file) from the OS admin (root) so that even root can't modify the DB (on the DB server).

I don't understand how jailbash would meet the requirement as root must be able to run 'cat' and 'less' to perform his rightful duties.

---

### Post by bodhi.zazen on 2011-01-08
> **freemant said:**
> Thanks for the replies. What I'd like to do is to protect the DB access credential (in a file) from the OS admin (root) so that even root can't modify the DB (on the DB server).

I don't understand how jailbash would meet the requirement as root must be able to run 'cat' and 'less' to perform his rightful duties.

Well, you will have to write an apparmor profile to do this for you. It is not *that* hard to allow access to cat, less, or any other command yet restrict access to other files and binaries. If you deny access to a file, foo, with apparmor, you can not read foo with cat or less.

I am not sure selinux will do this out of the box, but if so, or if you prefer selinux, stay with selinux.

---

### Post by freemant on 2011-01-09
After studying apparmor more, I think that this can be done by:
1) using a jailbash.
2) using a profile for jailbash to restrict access to that secret file, while allowing access to almost everything (required by root to perform normal duties).
3) configuring the profile so that jailbash executes all child processes with inherited transition (ix) so that they inherit the profile of jailbash to prevent them from accessing that secret file.
4) amending 3) so that for selected child processes, they run with their own probably more restricted profiles.

While this can be done, I think 4) will take a lot of effort. The ideal solution would be for apparmor to support intersecting the profiles for the parent and the child (e.g., combining the explicit deny rules).

---

