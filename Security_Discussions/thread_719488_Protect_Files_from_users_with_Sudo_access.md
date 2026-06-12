---
title: "Protect Files from users with Sudo access"
date: 2008-03-09
forum: Security Discussions
---

### Post by manicman on 2008-03-09
Hello
I have two users that use my machine (Gutsy 7.10). both need to have sudo access so they can install applications mount hard drives and so on.

I'm looking for a way to protect files against the other users. obviously I can't just change the permissions as both users have access to sudo. so is there a way to limit sudo access ?

I already have some files that i have encrypted with gpg but there remaining files are very large and would take hours to decrypt.

Thanks is advance for any help 
Regards
Chris

---

### Post by p_quarles on 2008-03-09
The nice thing about sudo is that it allows you to give users some access to root privileges without giving them everything. I would suggest removing these users from the admin group and listing specific commands (such as apt-get) that they are allowed to run as root. 

A bit more information here:
[http://ubuntuforums.org/showpost.php?p=4464175&postcount=2](http://ubuntuforums.org/showpost.php?p=4464175&postcount=2)

---

