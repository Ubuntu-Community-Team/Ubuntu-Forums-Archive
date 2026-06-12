---
title: "Ubuntu Server to Windows Box  SSH?"
date: 2007-09-16
forum: Server Platforms
---

### Post by jwes on 2007-09-16
Can I use this tool or is there a compatibility issue?  What tool should I be using?...I've tried but I get  'connection refused' response....
Have I missed something in the configuration?


Thanks.

---

### Post by HermanAB on 2007-09-16
Windows doesn't natively present SSH, but you can install Cygwin and OpenSSH on Windows.  This works very well and is very reliable.  I have found that Windows can be crashed with a non-functional console and then OpenSSH is still working allowing me to log in and restart the machine remotely!

For remote control, Windows has a Citrix (remote desktop) terminal server running on port 3389.  You can connect to that using 'rdesktop' from Ubuntu.

Cheers,

Herman

---

### Post by netlogic on 2007-09-18
[http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=12&MMN_position=149:149]("http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=12&MMN_position=149:149")

You need to install something like copsshd  if you want to sshd to your windows box. There are many compact versions of sshd that were stripped down from cygwin.

---

