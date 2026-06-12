---
title: "Is Apache/2.0.55 secure??"
date: 2007-08-13
forum: Server Platforms
---

### Post by cookfromfrozen on 2007-08-13
hi
I am using Apache/2.0.55 and OpenSSL/0.9.8a on Ubuntu 6.06 (both apache and openssl are the versions from the repos).

I notice both these version are quite old.  Does Ubuntu keep apache up to date with security udpates in the repository?  Am I okay to be using Apache/2.0.55 on the net or is there any serious security issues been fixed since 2.0.55??
thank you

---

### Post by p_quarles on 2007-08-13
The 6.06 server edition gets security patches through 2011, so anything you've installed from the repos is going to be secure. Apache itself also maintains the 2.0.5x branch, so it's not obsolete. You can look at the changelog for this branch here:
[http://www.apache.org/dist/httpd/CHANGES_2.0](http://www.apache.org/dist/httpd/CHANGES_2.0)

Of course, make sure that you do regular software updates on the server (you can even make this a cronjob):
```
sudo apt-get update
sudo apt-get upgrade
```

---

