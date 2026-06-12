---
title: "unexpected download - how to investigate"
date: 2010-08-27
forum: Security
---

### Post by jarviser on 2010-08-27
One reason I left Windows behind, particularly with a 3GB a month download limit, was that Linux generally only downloads files when you expect it to.  

Having the cap on downloads I run Netmeter in Wine. Now if like today I see a large unexpected download (pic) which is even in red to increase the paranoia, **how can I find out what it is preferably while it is happening? **

[IMG]http://jarviser.co.uk/jarviser/images4/netmeter.png[/IMG]

It does not seem to be an email with attachment (I run Thunderbird); Nothing in Downloads, and as far as I knew application updates only happen after confirming permission in update manager?

---

### Post by Ryan Dwyer on 2010-08-27
Ubuntu might be checking for updates. It has to download a list of software versions so it can compare it with your own and prompt you to update.

---

### Post by Lars Noodén on 2010-08-27
You can run [wireshark](http://packages.ubuntu.com/lucid/wireshark) without WINE, that will be a native source of information.

---

### Post by cdenley on 2010-08-27
+1 for wireshark, but this command would show you all network connections (what process is connecting where on what port).
```

sudo netstat -tnp

```

---

### Post by jarviser on 2010-08-27
wireshark looks cool. Thanks.

---

### Post by Lars Noodén on 2010-08-28
As @cdenley mentions, there is also netstat.  It is much faster and in many ways easier.  It can even be run from the applications menu.  With it you can be running in a second or so, if you are quick.  

Being in [/bin](http://manpages.ubuntu.com/manpages/lucid/en/man7/hier.7.html), it is **always** there in the default.  

A formula for sudo would be to make a group (e.g. networkers in the example below) to work with and add yourself to that group.  Then put something like the following (test carefully) in /etc/[sudoers](https://help.ubuntu.com/community/Sudoers):

```

%admin ALL=(ALL) NOPASSWD: NOEXEC: /bin/netstat, /usr/bin/wireshark

```

YMMV

---

### Post by jarviser on 2010-08-28
thanks again folks.

---

