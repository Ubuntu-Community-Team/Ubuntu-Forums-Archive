---
title: "apt-get retry/resume failed downloads"
date: 2004-12-24
forum: Repositories &amp; Backports
---

### Post by acidmax on 2004-12-24
Hello everyone

Just moved from Fedora core 3 to Ubuntu and I am very happy with it.

I have only one problem: my connection is permanent, but very unstable. Right now I am doing an apt-get upgrade (104 MB) which contains some big packages. My connection is not stable enough to complete their downloads, apt-get timeouts, continues to download the next package and leaves only unusable packages, which has to be downloaded again.

My question is: is there any APT settings that might help me in this situation?
I have:

**Acquire::Retries "999";** 

in /etc/apt/apt.conf.d/70debconf, but this doesn't seem to be the correct option...

Thanks in advance
Todor

---

