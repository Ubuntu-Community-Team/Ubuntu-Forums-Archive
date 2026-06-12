---
title: "Server won't completely restart - LDAP issue?"
date: 2007-11-22
forum: Server Platforms
---

### Post by steenbras on 2007-11-22
I've just encountered a problem which seems pretty weird. I've got Gutsy Server running in VMWARE on a Win2k3 host, and something on the host required a reboot. I gave it time to restart, and when I could successfully ping the VM by IP I tried to SSH on and got a connection refused.

Looking at the Host directly, and attaching to the VM, I noticed that it was prompting for a login. It was hanging here, and not starting SSH, apache, etc, but most importantly hadn't yet started slapd.

Now I thought that's what the idea of the nsswitch.conf and the pam.d/common-* config files was - to first attempt local login and only after attempt LDAP lookup. Changing my nsswitch.conf back to files rather than files ldap makes the problem go away, but obviously then causes problems with non-local accounts logging in.

What's wrong?

This is my current config:

nsswitch.conf
----------------
passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

common-account
---------------------
account sufficient      pam_ldap.so
account required        pam_unix.so

common-auth
-----------------
auth    sufficient      pam_ldap.so
auth    required        pam_unix.so

common-password
-----------------------
password   sufficient pam_ldap.so
password   required   pam_unix.so nullok obscure md5

common-session
--------------------
session required        pam_unix.so
session required        pam_mkhomedir.so skel=/etc/skel/
session optional        pam_ldap.so
session optional        pam_foreground.so

---

### Post by steenbras on 2007-11-22
Another point I should add, btw is that I could not log in with the administrator account defined during setup - I get the login timeout after 60 seconds message.

---

### Post by steenbras on 2007-11-23
I take it no-one's got any ideas here :( - should I try a different forum?

---

### Post by tavasti on 2008-02-01
I met same problem. I have slapd running on same server.

Adding 'ldap' to nsswitch.conf makes system 'unbootable'. Boots ok to single, but after it, init won't start any servers. Cannot login, same symptom, 60 s timeout even before asking passwd.

Putting std nsswitch.conf makes everything work ok.

I'm goin to resolve problem by creating 2 init scripts:

- one script putting std nsswitch.conf on early boot stage
- second script putting ldap-anabled nsswitch.conf after everything is up

Any better ideas?

---

### Post by tavasti on 2008-02-01
Solution is 'bind_policy soft' in /etc/ldap.conf

[http://ubuntuforums.org/showthread.php?p=3598637](http://ubuntuforums.org/showthread.php?p=3598637)

---

