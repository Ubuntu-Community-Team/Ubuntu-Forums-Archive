---
title: "Avoiding a Wine Floodgate....."
date: 2010-02-17
forum: Security
---

### Post by Malithorne on 2010-02-17
Forum,
We are considering an enterprise deployment of Ubuntu as our desktop replacement. We have a small number of custom Windows applications that would still need to run and we have verified that they run under Wine in Ubuntu.
However, from a client management perspective, it seems that Wine is an all or nothing avenue to install Windows applications. In other words, once we have Wine loaded, there is no way to restrict additional Windows software from being installed by the end user. Am I missing something or is this an Achilles heel for enterprise deployments of Ubuntu?

---

### Post by bodhi.zazen on 2010-02-17
Lock down the .wine directory, either by making it owned by root and not allowing users to write to it or by giving your users a restricted shell, ie confining either your users or wine with apparmor.

In general, users can compile , install, or write executable files but Linux permissions restrict them (normally) from changing system files.

One "problem" is a users $HOME is usually unrestricted, and one of the "major" uses of apparmor/selinux is to restrict access to files and data in $HOME (Why would firefox need access to ~/.ssh for example ?)

---

