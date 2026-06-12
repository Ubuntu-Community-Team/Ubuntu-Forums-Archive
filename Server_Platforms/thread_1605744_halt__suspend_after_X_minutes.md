---
title: "halt / suspend after X minutes"
date: 2010-10-25
forum: Server Platforms
---

### Post by l0xin on 2010-10-25
How do I configure acpi(d?) to suspend/halt the system after a specified period of inactivity? I can find plenty of information about setting up events to respond to button presses, but none on setting inactivity.

---

### Post by egpetrich on 2010-12-01
I'm seeing several threads with topics similar to this one. For example:

[http://ubuntuforums.org/showthread.php?t=1335400](http://ubuntuforums.org/showthread.php?t=1335400)

Either this thread or another thread pointed toward an application called "PowerNap":

[https://launchpad.net/powernap](https://launchpad.net/powernap)

From what I can see, the hard part appears to be identifying the processes to use as flags for suspending the system.

---

### Post by l0xin on 2010-12-01
Thanks. Yes, I eventually found Powernap which I set to watch the SSH process, so that it would halt after logging out.

---

