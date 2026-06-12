---
title: "Please help me install videocache 1.9.1"
date: 2009-06-17
forum: Server Platforms
---

### Post by marklodge on 2009-06-17
I have installed squid and its running fine
now i am trying to install videocache

First ii did [COLOR=Green]# python setup.py install[/COLOR] [in videocache-1.9.1 folder]
But at that time python-iniparse was not installed

I then installed iniparse, but now when i try to do [COLOR=Green]# python setup.py install[/COLOR] i get the following errors:

vpro:/home/ztel/videocache-1.9.1# python setup.py install
Traceback (most recent call last):
  File "setup.py", line 397, in <module>
    setup(root)
  File "setup.py", line 288, in setup
    if not dir_perms_and_ownership(new_dir, squid_user, squid_group):
  File "setup.py", line 76, in dir_perms_and_ownership
    user = pwd.getpwnam(user)[2]
KeyError: 'getpwnam(): name not found: squid'
vpro:/home/ztel/videocache-1.9.1# 

and here is the videocache setup log

2009-06-17 13:03:15,039 INFO Directory /etc/apache2/conf.d already exists.
2009-06-17 13:03:15,039 INFO Directory /etc already exists.
2009-06-17 13:03:15,039 INFO Directory /usr/share already exists.
2009-06-17 13:03:15,039 INFO Directory /usr/share/man/man8 already exists.
2009-06-17 13:03:15,039 INFO Directory /usr/sbin already exists.
2009-06-17 13:03:15,040 INFO Directory /var/log/videocache already exists.

Please tell me how i can overcome this.
Thank you very much

---

