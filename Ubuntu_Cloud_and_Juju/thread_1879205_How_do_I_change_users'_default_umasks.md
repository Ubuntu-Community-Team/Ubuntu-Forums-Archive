---
title: "How do I change users' default umasks"
date: 2011-11-11
forum: Ubuntu Cloud and Juju
---

### Post by sudonym on 2011-11-11
I've installed an 11.10 EC2 AMI and created a new user created through webmin to own a website.


When I log on (ssh) as this user, new directories are created with perms 775 and files with 664. I want to make these permissions more restrictive - without having to remember to change the umask manually every time I login.

I've tried putting the umask command in the users .bashrc, and creating a ~/.ssh/rc. Neither have worked and searches (that I've run at least) are not returning relevant answers.

How can I change the default umask? (Ideally in a way that allows me to use it in /etc/skel/, so that it affects all future users, without affecting the "ubuntu" user)

---

### Post by sudonym on 2011-11-11
Ah, apologies for the trick question - I didn't actually add the user through webmin and ended up with a shell of /bin/sh which, understandably, wasn't running my .bashrc file.

---

