---
title: "Removed Firestarter and  killed my network connection."
date: 2009-06-17
forum: Security
---

### Post by greenmanu on 2009-06-17
Hi All 
I have been enjoying Ubuntu for a while now and its about time broak it, and I have by removing Firestarter Firewall. Now I am unable to connect to the Net with my Wireless Card. What should I do folks! apart form kick myself??

---

### Post by lovinglinux on 2009-06-17
Post the output of this command:

```
sudo iptables -L
```

Also try this:

```
sudo apt-get purge firestarter
```

---

### Post by greenmanu on 2009-06-17
Thanks lovinglinux!!

---

### Post by lovinglinux on 2009-06-17
> **greenmanu said:**
> Thanks lovinglinux!!

You are welcome. Is it working now?

What is th output of this command:

```
sudo iptables -L
```

---

