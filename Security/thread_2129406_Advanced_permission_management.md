---
title: "Advanced permission management"
date: 2013-03-26
forum: Security
---

### Post by eskimo on 2013-03-26
Hello,
i need some help to make a directory's special permission to apply. I have a directory (a home with a user that nobody uses) to be accessed by three users, it has 770. Two of them have to rwx and only one has to x only, they are not owners. Firsts users can do newgrp and put theirselves in the group of the home user and rwx, but how can the third one execute only without change whole permissions from 770 to 771? i don't want that all others can execute!
thanks
Paolo

---

### Post by schragge on 2013-03-26
If the directory is on an ext4 filesystem, you can use [ACL]("http://manpages.ubuntu.com/manpages/precise/en/man5/acl.5.html") for that. See an example in [post=12507056]this post[/post].

---

### Post by eskimo on 2013-03-26
yes, it has ext4. I ignored acl on linux filesystem.
Thank you!
P.

---

### Post by SeijiSensei on 2013-03-26
Also the "execute" permission on directories means something very different from the same permission applied to files.  Since it makes no sense to execute a directory, the "x" permission means that the user or group can list the contents of the directory.  A directory with "x" but not "r" allows listing the directory's contents but forbids reading the files themselves.

---

