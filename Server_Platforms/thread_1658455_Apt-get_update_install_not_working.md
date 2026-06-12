---
title: "Apt-get update/ install not working"
date: 2011-01-02
forum: Server Platforms
---

### Post by Shiv Prakash on 2011-01-02
Server has ubuntu 9.10 installed and running sudo apt-get update throws the following error.

```
Err http://archive.ubuntu.com karmic Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com karmic-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com karmic-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

I did check this link out [http://www.davidtan.org/ubuntu-apt-get-update-problem-solution/]("http://www.davidtan.org/ubuntu-apt-get-update-problem-solution/") but how should I do the same from command line.

Thanks!!

---

### Post by Shiv Prakash on 2011-01-02
Solution found at [http://ubuntuforums.org/showthread.php?t=871015]("http://ubuntuforums.org/showthread.php?t=871015")

Basically my /etc/resolv.conf file was empty :oops:, so obviously lookups weren't getting resolved.

Simply added ```
Nameserver 8.8.8.8
``` to it and everything worked fine. FYI 8.8.8.8 is google's DNS.

---

