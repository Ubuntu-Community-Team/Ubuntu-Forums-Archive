---
title: "ssh, sftp usage howto"
date: 2009-10-06
forum: Security
---

### Post by christian18 on 2009-10-06
hay i'm newbie..
i juzt confused how tu use ssh or sftp..could you help me guys...

---

### Post by cariboo on 2009-10-06
Have alook at this [page]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html") for help setting up openssh-server.

To use sftp once you have ssh setup, open nautilus and in the location bar type:

```
sftp://user@server
```

Your home directory on the remote computer will open in nautilus.

Personally I use filezilla for transferring files between systems if there are no shares mounted.

---

### Post by The Cog on 2009-10-07
> **cariboo907 said:**
> To use sftp once you have ssh setup, open nautilus and in the location bar type:
```
sftp://user@server
```

Or from the nautilus menu, File->Connect to Server and choose service type SSH.

---

