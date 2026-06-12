---
title: "Netatalk - can't browse shares"
date: 2011-12-30
forum: Server Platforms
---

### Post by harveyd on 2011-12-30
I am using Ubuntu server 11.10, running a compiled version of netatalk 2.2.1.

The AFP server is working ok and I can connect to shares successfully from my mac by going Go -> Connect to Server then type:-

afp://ipaddress/sharename

I am prompted for username and password and am let in and can see the share just fine!

If however I leave off the share name in the connect to server box I am asked for username and password and then told that no share's are available.

I have two shares that I have access to, which I can manually connect to.

How can I get a list of available shares to show?

The only thing I can think is that I am using ACL's? I compiled netatalk with ACL support and once connected the ACL's are working.

Any ideas are gratefully received.

---

### Post by jchung on 2011-12-30
Did you install and configure Avahi?

[http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/](http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/)

---

### Post by harveyd on 2012-01-15
Sorry for the delay in reply. Yes Avahi is all installed and configured.

It appears there is a but with Ubuntu 11.10 + netatalk 2.2.1 and Lion 10.7.2

Will have to keep an eye on it.

---

