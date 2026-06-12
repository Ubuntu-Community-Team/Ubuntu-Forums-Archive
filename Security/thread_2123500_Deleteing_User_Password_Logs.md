---
title: "Deleteing User Password Logs"
date: 2013-03-08
forum: Security
---

### Post by bronstein on 2013-03-08
I am a user in a computer network (not root). I didn't know that root can see other users' passwords, after learning I changed my password (previous password was an important password for me). I learned linux stores old passwords, so I want to if there is a way to delete my account's password log. Thanks for your consideration. Sorry if topic is in wrong section.

---

### Post by drmrgd on 2013-03-08
I'm not positive this is 100% correct.  Root can view the /etc/shadow file, which contains the user's password, but it's encrypted and requires quite a bit of effort to decrypt.  PAM only stores old passwords if the feature is turned on to remember old passwords in order to prevent users from re-using them (for example remember the last 10 passwords to force a user to never repeat the same password over 10 iterations).  But, that's encrypted as well (I think...I've not played with this myself).  So, there's no way for root to know your password without considerable effort.

That being said, the file that does contain the older passwords, again assuming it's turned on, would only be accessible by root anyway.  So, you couldn't delete it if you wanted to.

---

### Post by slickymaster on 2013-03-08
System account passwords can be found in **/etc/shadow**. You need root privileges to read the file. The passwords are SHA encrypted. Additional information can be found on the corresponding [manpages]("http://manpages.ubuntu.com/manpages/precise/en/man5/shadow.5.html").

---

