---
title: "Issue with GIT on 11.10 (Server and Desktop) with https"
date: 2011-11-12
forum: Server Platforms
---

### Post by rmarc71 on 2011-11-12
I upgraded both my ubuntu server and ubuntu desktop with 11.10.  On both versions, I was unable to connect to GIT over https to a local repo (am running a GIT repo via Apache on my server with a self signed cert).

After fighting it for about a day, I decided to try a different version (the latest from git's site).  That client version worked without a hitch.


Note: I added the cert to my ca chain in my gitconfig.

Smells like a bug to me, but not sure where to report it.

Here's the git-core version and error:
```

laptop:~$ /usr/bin/git --version
git version 1.7.5.4

laptop:~$ /usr/bin/git clone https://git.mydomain.com/git/testproject.git
Cloning into testproject...
error: gnutls_handshake() failed: A TLS warning alert has been received. while accessing https://git.mydomain.com/git/testproject.git/info/refs

fatal: HTTP request failed

```


Here's the same information with my newer client version of git (TLS error gone)

```

laptop:~$ /usr/local/bin/git --version
git version 1.7.8.rc1.14.g248db

laptop:~$ /usr/local/bin/git clone https://git.mydomain.com/git/testproject.git
Cloning into 'testproject'...
Username for 'git.mydomain.com':
Password for 'git.mydomain.com':
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.

```

---

### Post by Jliax on 2012-04-18
Any workaround on this for older versions?

---

