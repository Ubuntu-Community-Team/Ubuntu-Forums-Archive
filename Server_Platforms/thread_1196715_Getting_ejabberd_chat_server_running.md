---
title: "Getting ejabberd chat server running"
date: 2009-06-25
forum: Server Platforms
---

### Post by martin.knapp on 2009-06-25
I'm running Ubuntu 8.10 server configuration, and I want to install an ejabberd chat server. Trouble is I can't get past the elementary first steps.
I've installed ejabberd 2.0.1-2 by the simple expedient of activating it through the Synaptic package controller - that all seems to have gone fine.

Now here is what I have done:
1) /etc/hostname is ubuntu810
2) /etc/hosts contains 127.0.1.1 ubuntu810
3) On the server I can start Firefox and navigate successfully to http://ubuntu810
4) I change the /usr/share/ejabberd.cfg with the following:
{acl, admin, {user, "copadmin", "ubuntu810"}}.

{hosts, ["ubuntu810"]}

5) sudo /etc/init.d/ejabberd start
6) ejabberd appears to be working because I can navigate to mysystem:5280/admin and get a password challenge
7) HOWEVER, when I try to register my admin user:
sudo ejabberdctl register copadmin ubuntu810 mypassword
I get this error
Can't register "copadmin@ubuntu810" at node ejabberd@ubuntu810: not_allowed

I've checked that the default internal authorisation is allowed...

Any ideas would be gratefully received

---

### Post by bgabga on 2010-08-30
Must be: {hosts, ["ubuntu810"]}.

I have a similar config and I can log in.
I used:

ejabberdctl change_password copadmin ubuntu810 mypassword
/etc/init.d/ejabberd restart

---

