---
title: "Permissions on home directories"
date: 2013-01-30
forum: Security
---

### Post by SeijiSensei on 2013-01-30
I just installed a clean version of Kubuntu 12.04 in a VM and noticed that the permissions on my home directory are 755 which grants read and list rights to everyone.  I thought earlier versions of Ubuntu defaulted to 700 permissions on home directories to protect them from the prying eyes of other users.  RedHat-flavored distributions have done this for a very long time.  I remember discussing that change with one of my employees back in the mid-to-late 1990s.  We both agreed that this seemed a much more secure method of handling home directories.

Has Ubuntu always used such an open permissions scheme for home directories, and thus my memory of earlier versions is wrong, or is this a recent change?  Is this a concession to ease-of-use, especially when most people are the only users on their machines?  I just checked a Debian server I built a year or two back, and it also has the 700 permissions model.  What about Ubuntu server?  I would think that should have restricted permissions by default.

Personally, I prefer the restricted model.  If I want to let others view my files, I can make that choice for myself.  I see the opposing arguments for a consumer-oriented distribution, but it seems to run contrary to the emphasis on security in other parts of Ubuntu.

---

### Post by bodhi.zazen on 2013-01-30
It is a long standing Ubuntu policy:

[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive_Home_Directory_Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive_Home_Directory_Access)

It has always been controversial

[https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734](https://bugs.launchpad.net/ubuntu/+source/adduser/+bug/48734)

Personally I do not agree with the policy either.

---

### Post by movieman on 2013-01-30
> **bodhi.zazen said:**
> Personally I do not agree with the policy either.

For a home desktop system, not being able to share files is a pain. So it makes sense as an Ubuntu policy.

It's not hard to change if you care, and if you do care you should be encrypting your files anyway. Then no-one else can read them when you're logged out, regardless of permissions.

---

### Post by bodhi.zazen on 2013-01-30
> **movieman said:**
> For a home desktop system, not being able to share files is a pain. So it makes sense as an Ubuntu policy.

It's not hard to change if you care, and if you do care you should be encrypting your files anyway. Then no-one else can read them when you're logged out, regardless of permissions.

As I said I disagree with the policy. Yea, encrypt this encrypt that, blah blah, it is an old argument, probably belongs in recurring discussions.

Encryption ($HOME or full disk) falls flat if your user is still logged in, which is easy to happen in a house full of children. Children are very fast and encryption is far from fool proof.

Yes you *should* log off, but the reality is, with a house full of in-laws, friends, family, young children, it is sometimes easier said then done, especially with the fast switch user feature.

Yes I change it when I use Ubuntu. Yes I appreciate the Policies of Fedora =)

IMO anything shared belongs in a shared directory, but then there are issues best solved, IMO, with acl ;)

---

### Post by SeijiSensei on 2013-01-30
> **movieman said:**
> For a home desktop system, not being able to share files is a pain. So it makes sense as an Ubuntu policy.

Fixing this problem would be as easy as creating a public shared directory, say /usr/share/public, with 777 permissions and putting a symlink to it in /etc/skel so it would be added to each home directory when a new user is created.  Having read through the arguments in the bug report I remain unpersuaded by the Ubuntu developers.  Even having Mark Shuttlesworth himself chime in didn't change my opinion.

---

