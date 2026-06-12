---
title: "Gnupg. . ."
date: 2010-08-15
forum: Security
---

### Post by krpnm on 2010-08-15
Hi Folks,

Am using V10.04(lts), amd-64/32 edition.  The problem is when I attempt to download and install Gnupg-agent.  I receive the following (dependency[s]) error[s]:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnupg2/gpgsm_2.0.14-1ubuntu1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnupg2/gpgsm_2.0.14-1ubuntu1.1_amd64.deb)
  404  Not Found [IP: 91.189.88.40 80]

There are other dependency issues as well *all* providing the same error message (just change the file name).

I suspect that security vulnerability, USN-970-1: GnuPG2, maybe the culprit.  However, I can find no, as in zero, information about it which leaves me in the blasted dark.  And that is unsatisfactory.

Can someone shed some light on this or get the files put back where the system can find 'em?

---

### Post by rookcifer on 2010-08-15
It just means the repository is not responding (as in it's down right now for some reason).  Or the connection problem could be on your end, of course.  It's hard to tell without more info.  But nothing you posted even hints at any kind of malicious activity.

Try a different repository mirror.

---

### Post by FuturePilot on 2010-08-16
Not a connection problem, it's 404. apt-get update because it looks like it's been replaced with -1ubuntu1.2

---

### Post by krpnm on 2010-08-16
> **FuturePilot said:**
> Not a connection problem, it's 404. apt-get update because it looks like it's been replaced with -1ubuntu1.2


Did that -- no joy.

---

### Post by cdenley on 2010-08-16
> **krpnm said:**
> Did that -- no joy.

No joy because because it is still trying to download a package which does not exist, or because it is trying to download a current package but still getting a 404 error? Post some output.
```

apt-cache policy gpgsm
sudo apt-get update
apt-cache policy gpgsm
sudo apt-get install gnupg-agent

```

---

### Post by krpnm on 2010-08-17
> **cdenley said:**
> No joy because because it is still trying to download a package which does not exist, or because it is trying to download a current package but still getting a 404 error? Post some output.
```

apt-cache policy gpgsm
sudo apt-get update
apt-cache policy gpgsm
sudo apt-get install gnupg-agent

```

Sorry for the delay in responding -- due to some real entertaining electrical storms over the past 24 hours or so we haven't had our 'puters on till about 30 minutes ago.

Went back to the repositories and everything *worked* just fine.

Thank you all.

---

