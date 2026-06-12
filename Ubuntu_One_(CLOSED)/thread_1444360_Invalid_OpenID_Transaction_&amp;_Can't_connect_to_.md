---
title: "Invalid OpenID Transaction &amp; Can't connect to localhost:37111"
date: 2010-04-01
forum: Ubuntu One (CLOSED)
---

### Post by nathand28 on 2010-04-01
Fixed. Follow the instructions below if you can't add computers through the FAQ method.

Login to Ubuntu One on the website, open a terminal and type ```
u1sync --authorize
``` Press enter and a window should open redirecting you to one.ubuntu.com, if you are already logged in.

----------

Every time I try to login to U1, or add any computers to it, it gives me this error. I've tried removing cookies,history, etc. but it still doesn't work. Not even on a Windows machine using IE or Firefox.

Also, I can't add any computers to U1, as Firefox won't connect to [http://localhost:37111/?nonce=4276062&oauth_token=978z6PknsshRTGqJCj5s&oauth_verifier=6d5d3e88-bfeb-46ef-983a-6edbf431573b&return=https://one.ubuntu.com](http://localhost:37111/?nonce=4276062&oauth_token=978z6PknsshRTGqJCj5s&oauth_verifier=6d5d3e88-bfeb-46ef-983a-6edbf431573b&return=https://one.ubuntu.com). Tried resetting my hosts file, doing the things listed [here]("https://answers.edge.launchpad.net/ubuntuone-client/+faq/633"), even in the Gnome proxy settings. Still no luck.


Any ideas?
Thanks

---

### Post by joshuahoover on 2010-04-01
> **nathand28 said:**
> Every time I try to login to U1, or add any computers to it, it gives me this error. I've tried removing cookies,history, etc. but it still doesn't work. Not even on a Windows machine using IE or Firefox.

Also, I can't add any computers to U1, as Firefox won't connect to [http://localhost:37111/?nonce=4276062&oauth_token=978z6PknsshRTGqJCj5s&oauth_verifier=6d5d3e88-bfeb-46ef-983a-6edbf431573b&return=https://one.ubuntu.com](http://localhost:37111/?nonce=4276062&oauth_token=978z6PknsshRTGqJCj5s&oauth_verifier=6d5d3e88-bfeb-46ef-983a-6edbf431573b&return=https://one.ubuntu.com). Tried resetting my hosts file, doing the things listed [here]("https://answers.edge.launchpad.net/ubuntuone-client/+faq/633"), even in the Gnome proxy settings. Still no luck.


Any ideas?
Thanks

Do you have any sort of script blocking software enabled in Firefox like NoScript? If so, please see: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/957](https://answers.edge.launchpad.net/ubuntuone-client/+faq/957) Also, are you behind a proxy server? Ubuntu One will not work properly behind a proxy server right now.

It would be helpful to see log files if the above does not help. If you can file a bug report and attach the following log files to that report, it would be greatly appreciated: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

Thank you,

Joshua

---

### Post by nathand28 on 2010-04-05
Joshua, I think you misunderstood my problem.  It isn't with the client ( mainly), but the website. It won't let me connect to authorize my computer. I have everything disabled, including add-ons and proxies. I'm not the lucid beta with Firefox by the way.

Maybe U1 is sending me to the wrong address?

I've attached *syncdaemon-exceptions*, but it doesn't relate to this problem as much. The other file has only a log of logging on.

```

2010-04-01 11:51:00,335 - ubuntuone-preferences - ERROR - org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/bin/ubuntuone-preferences", line 1055, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 733, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 163, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.

2010-04-01 14:12:41,037 - ubuntuone-preferences - ERROR - org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/bin/ubuntuone-preferences", line 1055, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 733, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 163, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.


```

---

### Post by nathand28 on 2010-04-05
Thanks for helping, but I fixed it with *u1sync --authorize*. Don't know why I had to do it that way.

For anyone else reading, login to Ubuntu One on the website, open a terminal and type ```
u1sync --authorize
``` Press enter and a window should open redirecting you to one.ubuntu.com, if you are already logged in. That should fix the problem.

Would it be a good idea to include the *u1sync --authorize* bit into the FAQ?

EDIT : Client works fine after updating and restarting.

---

