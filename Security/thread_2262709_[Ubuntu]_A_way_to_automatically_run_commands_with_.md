---
title: "[Ubuntu] A way to automatically run commands with &quot;sudo&quot; w/o &quot;sudo su&quot;"
date: 2015-01-26
forum: Security
---

### Post by colin012 on 2015-01-26
I want to completely disable anyone from using sudo su to connect log into the root account so that I can have complete control over who gets to use what super user commands. The trick is that sudo su is very convenient for not having to type "sudo" before everything you do!

Is there another way to do this?

---

### Post by ian-weisser on 2015-01-26
Normal (non-admin) users do not have access to sudo nor root already.

---

### Post by HermanAB on 2015-01-27
Well, that is what the sudoers file is for...

---

### Post by colin012 on 2015-01-27
I have been using the sudoers file.

I have another question. I want a separate password to be used for using sudo commands but I don't want it to be the root password (as I don't want root to have a password). This account would have no permissions but their password would be needed by other accounts to use sudo commands. How would I set this up?

---

### Post by ian-weisser on 2015-01-27
I don't understand the use case.
If you are already using the sudoers file to permit access by each user, then what more do you need?
What is the purpose of a separate common-password? (which, since two or more people know it, is insecure)

---

### Post by Lars Noodén on 2015-01-27
Do you want to restrict access to that of specific programs?  That is done by [configuring /etc/sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html).  Or do you want to set up a replayable audit trail to see what is done after *sudo* is run?  That too is in /etc/sudoers

---

### Post by HermanAB on 2015-01-28
Anyhoo, whatever you do, don't share usernames and passwords between different users, because that breaks the audit trail.  the whole idea behind sudo, is that you can configure fine grained access and have a meaningful audit trail.

---

