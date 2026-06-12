---
title: "ACL installation on the root partition"
date: 2009-12-08
forum: Server Platforms
---

### Post by rmccarri on 2009-12-08
Hi everyone,
I have a dedicated web server that I've set up at work.  There are several users that can connect and make changes to the apache working directory (currently,everything is www-data:www-data and I've added the users that need access to the www-data group).  I would like to have a little more nuanced control over who can have access to which directories and files that ACL provides.

I've installed the ACL package, but have yet to activate it.  I didn't have the foresight to set up the home and www directories as separate partitions (everything is in just one / partition).  My questions are as follows:

1:  Can I activate ACL for just the home and www directories?
2:  If so, how would I go about doing that?
2:  If not, are there reasons that I would not want to activate ACL for the entire root partition (I've heard that it can slow things down and such)?

Thanks in advance for any comments or suggestions.
Rob

---

### Post by munky99999 on 2009-12-08
[http://www.youtube.com/watch?v=6piQXXHTmqk](http://www.youtube.com/watch?v=6piQXXHTmqk)

Pretty good vid.

[https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport](https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)

Where I stole it from.

Basically you're messing with the /etc/fstab in order for it to be run.

Nothing too hard.

---

