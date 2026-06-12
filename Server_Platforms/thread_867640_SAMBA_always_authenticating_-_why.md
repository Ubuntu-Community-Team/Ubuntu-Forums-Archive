---
title: "SAMBA always authenticating - why?"
date: 2008-07-23
forum: Server Platforms
---

### Post by devonps on 2008-07-23
Hi,

I've managed to get SAMBA working and communicating with my windows desktops/users.

I've also created a public share that all users will be able to read/write from/to.

My situation is this: when (windows users) steven maps a network drive to //server/music (which is on the Ubuntu server box) he is asked to provide a user name & password.

Why is this? I thought that because the users are aligned on both the (Ubuntu) server and the (windows) client that authentication is taken care of.

I've attached my current SAMBA config file for additional information.

---

### Post by windependence on 2008-07-23
Change this line:

```
security = user
```

to this:

```
security = share
```

and restart samba. If that doesn't work, add this line in your conf file somewhere:

```
guest account = nobody
```

and remember to restart samba (NOT reboot).

-Tim

---

### Post by devonps on 2008-07-23
Hi,

Just wanted to say thanks for the help - worked a treat :)

---

