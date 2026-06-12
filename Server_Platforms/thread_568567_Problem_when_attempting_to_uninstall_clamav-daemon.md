---
title: "Problem when attempting to uninstall clamav-daemon"
date: 2007-10-06
forum: Server Platforms
---

### Post by JonnJack on 2007-10-06
I get this when I try to remove clamav-daemon using Synaptic Package Manager.

**E: /var/cache/apt/archives/clamav-daemon_0.91.1-1ubuntu3~feisty1_i386.deb: subprocess new pre-removal script returned error exit status 2**

I've already done:

**sudo apt-get install -f**

These are the last three lines when I try that:

Errors were encountered while processing:
 /var/cache/apt/archives/clamav-daemon_0.90.2-0ubuntu1.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Using Feisty Fawn 7.04

Any thoughts or help appreciate. Please do not assume I know ANYTHING about Ubuntu, most of my experience is either Apple or DOS....:-|

---

### Post by netlogic on 2007-10-06
did you tried with dpkg -r packagename?
if not, you might have to manually remove it.

---

### Post by JonnJack on 2007-10-06
> **netlogic said:**
> did you tried with dpkg -r packagename?
if not, you might have to manually remove it.

Did try the 'dpkg -r', still getting error message.

If there a walk-through, or some advice for removing manually?

---

### Post by netlogic on 2007-10-06
Yes, if you visit their website I have seen the instruction and documentation.

---

