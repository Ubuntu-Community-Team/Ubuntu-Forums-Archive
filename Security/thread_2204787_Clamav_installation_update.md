---
title: "Clamav installation update"
date: 2014-02-10
forum: Security
---

### Post by geoff.lannon on 2014-02-10
Hi
I am new to Ubuntu. I have clamav installed. I was told to enter 'sudo freshclam' command to update. My query is that the end result is an entry which states 'Your ClamAV installation is OUTDATED' 'Local version 0.97.8 Recommended version 0.98.1' All other entries are shown as up to date.

I have no idea how to update clamAV or whether or not I need to. I have Ubuntu 13.10 installed.

Can someone please point me in the right direction. You will need to keep the explanation simple as I am not that computer literate.

Many thanks 

G

---

### Post by Dave_L on 2014-02-10
Personally I don't think upgrading it is necessary. It's just an informational message that there's a newer version available.

If you do want to upgrade now, there's a PPA with the newer version: [https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)
The instructions there tell you how to use the PPA.
That's not the very latest version either, so you might still get the warning message.

---

### Post by geoff.lannon on 2014-02-10
Thanks. I think I will leave things as they are.

---

### Post by fugu2 on 2014-02-10
clamav is also signature based detection which means its not very effective most of the time. It'd be nice if there was a FOSS solution that used sandboxing at least.

---

