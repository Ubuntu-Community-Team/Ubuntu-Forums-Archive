---
title: "Dovecot auth-worker error"
date: 2014-10-04
forum: Server Platforms
---

### Post by Dale_Walsh on 2014-10-04
A user fears public posting as he's a newbie, he has asked me about an issue he is experiencing in his mail server, I've ssh'd in to check it out as I don't have the issue he is experiencing.

The config files seem to be good, no permission issues, all files are where they are expected.
 
I've even tried using my own working config files, the error remains.

The only issue I see that results from this error is that mail from his server is never removed so each time the server (or postfix) is restarted, local mail going back several months is resent.

No, it's not a client configuration issue, I've configured my client to immediately remove mail that it retrieves, works on my server and other servers (I verified it) but not on his, he's using the same 14.04.1 LTS so why he has this error and I do not, it makes no sense to me.

Since I've not encountered this problem, don't have days to spend debugging his system I thought the best solution was to solicit assistance, if anyone knows the solution, please provide simple instruction for the user to follow to correct this error.

If he has to rebuild dovecot from the same or newer source, please include the instructions to install the tools to build it, linux-headers and build-essentials should be sufficient I believe.

Here's a copy of the log showing the error
```
Oct  4 12:55:53 humphrey dovecot: auth-worker: Error: no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Oct  4 12:55:54 humphrey dovecot: pop3-login: Login: user=<mike>, method=PLAIN, rip=192.168.1.229, lip=192.168.1.102, mpid=5887, session=<Tx//uJsEDwBDTgvl>
Oct  4 12:55:54 humphrey dovecot: pop3(mike): Disconnected: Logged out top=0/0, retr=0/0, del=0/0, size=0
```

---

### Post by DigiAngel on 2014-10-05
From this post:

[http://ubuntuforums.org/showthread.php?t=2214042]("http://ubuntuforums.org/showthread.php?t=2214042")

sudo apt-get remove libpam-smbpass OR "You can also fix this issue while keeping libpam-smbpass installed by running " sudo pam-auth-update" and remove "SMB password synchronization"."

I had the same issue.  Ended up going back to 12...14 isn't ready for prime time.

---

### Post by Dale_Walsh on 2014-10-06
The user followed your instructions and reported to me the error is now gone.

Does this mean that samba authentication may have issues because synchronization is disabled?

---

### Post by DigiAngel on 2014-10-06
I did not see any other impact besides the log entry going away...a good thing.

---

