---
title: "Which version am I running?"
date: 2010-04-29
forum: The Cafe
---

### Post by 98cwitr on 2010-04-29
*cat /etc/issue*

gives me Ubuntu 10.04 /n /l

How do I tell im I've still on beta or fully upgraded?

---

### Post by Ewingo401 on 2010-04-29
Open up a terminal and type in

```
sudo apt-get update && sudo apt-get upgrade
```

After running those commands you'll be fully updated to the release version.

---

### Post by 98cwitr on 2010-04-29
did the partial...everything's set...did sudo apt-get update && sudo apt-get upgrade and came back with 0 updates. Welcome to our New World ladies and gents :)

---

### Post by 98cwitr on 2010-04-29
Would still like to know what the n and l switches mean though. Anyone?

---

### Post by RedSquirrel on 2010-04-29
> **98cwitr said:**
> Would still like to know what the n and l switches mean though. Anyone?

Read the man page for getty.

```
man getty
```From the section, **ISSUE ESCAPES**:

**n**        Insert the nodename of the machine, also known as the hostname.

**l**        Insert the name of the current tty line.

---

### Post by 98cwitr on 2010-04-29
would it have said beta if I was actually still on beta?

---

### Post by CharlesA on 2010-04-29
Would probably have said "development release" or some such thing.

---

