---
title: "Apparmor &amp; New User"
date: 2008-04-04
forum: Server Platforms
---

### Post by mat3 on 2008-04-04
Hello,

I've recently installed Server version of Ubuntu 8.04 and I have problem with Apparmor. When I try to create new profile for app, the following error appears:

```

Create New User?

(Y)es / [(N)o]
Username: 
Password:

Save Configuration?

[(Y)es] / (N)o

Login failure. Please check username and password and try again
RPC::XML::Client::send_request: HTTP server error: Not Found

```

I've fully patched system. It appears whatever username/password I provide.
Dosesn't matter if the app is installed from the repository or compiled. Do someone know what should I do?

Thanks in advance.

---

### Post by dendrobates on 2008-04-04
What makes you think that this is an Apparmor problem?  You should have an audit log in /var/log/syslog, saying what is happening if it is apparmor.

Does it work if you turn off apparmor?
sudo /etc/init.d/apparmor stop

Rick

---

### Post by mat3 on 2008-04-05
If I turn off the Apparmor the result is the same.

I realised that my syslog weight is 510MB+ :???:

The file is full of:

```
Apr  5 12:51:36 imagic kernel: [39215.969092] audit(1207392696.625:1974981): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969100] audit(1207392696.625:1974982): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969111] audit(1207392696.625:1974983): type=1502 operation="file_lock" request_mask="wk::" denied_mask="wk::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969120] audit(1207392696.625:1974984): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969128] audit(1207392696.625:1974985): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969137] audit(1207392696.625:1974986): type=1502 operation="file_lock" request_mask="wk::" denied_mask="wk::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969146] audit(1207392696.625:1974987): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
Apr  5 12:51:36 imagic kernel: [39215.969154] audit(1207392696.625:1974988): type=1502 operation="file_lock" request_mask="k::" denied_mask="k::" name="/var/run/samba/wins.tdb" pid=6904 profile="null-complain-profile" namespace="default"
```

---

