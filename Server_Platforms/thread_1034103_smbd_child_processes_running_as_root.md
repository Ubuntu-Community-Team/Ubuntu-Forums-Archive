---
title: "smbd child processes running as root"
date: 2009-01-08
forum: Server Platforms
---

### Post by cryogen on 2009-01-08
Not sure if this should go in here or in the Security category.

I have an ubuntu server running hardy and samba running as a standalone.  I've noticed that when a client connects smbd spawns a child process running as the user who connected.  That is, if user bob1 logs in, smbd spawns a child process running with the privileges of bob1.  At least for a while.

If the user is connecting from a *nix system (linux or OSX), the child smbd process will run as the logged in user forever, and the child process quits when the user logs out.

That is, the processes look like this for *nix clients:

```

21584 root    `/usr/sbin/smbd -D
21609 bob1       `- /usr/sbin/smbd -D
21586 root       `- /usr/sbin/smbd -D

```

and they stay that way until bob1 disconnects and then reverts to this:

```

21584 root    `/usr/sbin/smbd -D
21586 root       `- /usr/sbin/smbd -D

```

However, if the client is connecting from windows (XP SP2/3), the child process will run as the user for a while, and then mysteriously start running as root.  In addition, the child process doesn't die when the user logs out, and requires restarting samba to kill the process.

That is, the process starts like this:
```

21584 root    `/usr/sbin/smbd -D
21609 bob1       `- /usr/sbin/smbd -D
21586 root       `- /usr/sbin/smbd -D

```

and after a while becomes this:

```

21584 root    `/usr/sbin/smbd -D
21609 root       `- /usr/sbin/smbd -D
21586 root       `- /usr/sbin/smbd -D

```

even when bob1 has disconnected.

What I'm looking for is a way to correct this behavior.  Does anyone have any advice, links or magic smb.conf parameters?

The 'reverting to root' part really bothers me since it strikes me as a very bad idea to have a windows(!) box with direct access to a process running as root.

---

### Post by windependence on 2009-01-08
According to samba this is normal behavior and does not pose a security risk. I am looking for an explanation because the engineer in the post I read was rather indignant about the fact that it was perfectly OK.

-Tim

---

### Post by cryogen on 2009-01-08
> **windependence said:**
> According to samba this is normal behavior and does not pose a security risk. I am looking for an explanation because the engineer in the post I read was rather indignant about the fact that it was perfectly OK.

-Tim

Thank you for the response!  Could you post the link to what you were reading?

I'd have to agree with the engineer you're referring to.  It might not bother me so much if the *nix clients did the same thing, but they don't.

---

### Post by cryogen on 2009-06-26
Well, I finally stumbled on the answer to this and I figured I should probably close this thread and post the solution in case someone needs it.  It seems that I was missing some parameters in my smb.conf file.  Specifically, when I added:
```
lanman auth = no
lm announce = no
min protocol = NT1
```
the smbd processes suddenly started keeping their users instead of reverting to root.  I'm still watching this, but it looks like the behavior I wanted.

---

