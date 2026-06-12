---
title: "Ubuntu One experienced an error"
date: 2013-07-31
forum: Ubuntu One (CLOSED)
---

### Post by sgshah on 2013-07-31
"Sorry, an error has occurred and Ubuntu One needs to close."

"UnauthorizedErroru'Host requires authentication'
u'Invalid access token: '"

this message is displayed upon starting Ubuntu One & syncing.

Please help how to overcome above Ubuntu One Syncing error.
Thanks in advance.

--
regards,
SGS

---

### Post by Irihapeti on 2013-07-31
Which version of Ubuntu are you running?

---

### Post by sgshah on 2013-08-02
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise

Sorry I missed out in post :( :)

---

### Post by Irihapeti on 2013-08-02
That's good. I wondered if you were using an old, unsupported version because that's what's in your profile. Running an old version can cause this error.

In this case, it is probably because there's a mismatch between the token on your machine and the one on the server.

First, open a terminal and run 
```
killall ubuntuone-login ubuntuone-preferences ubuntuone-syncdaemon
```

This makes sure there are no Ubuntu One processes running on your machine. If you get some "no process found" messages, it doesn't matter.

Open Passwords and Keys and remove the password/token for Ubuntu One.

Browse to the Ubuntu One web interface and login. Under "My Account", there's a section showing Authorized Machines (or similar). Find the entry that relates to your machine and remove it.

Then try restarting the Ubuntu One client and connecting to the server. It should go through an authentication routine again and create a new token.

---

