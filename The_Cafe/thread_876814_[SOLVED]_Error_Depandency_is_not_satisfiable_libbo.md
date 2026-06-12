---
title: "[SOLVED] Error: Depandency is not satisfiable: libboo2.0-cil"
date: 2008-08-01
forum: The Cafe
---

### Post by jeyaganesh on 2008-08-01
Hi,
I was trying to install Banshee 1.2. But package installer showing this 'Error: Depandency is not satisfiable: libboo2.0-cil' I found libboo2.0-cil installed already in the synaptic package manager.
How to solve this problem?:guitar:

---

### Post by Tom--d on 2008-08-01
use this repo
```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main

```

:)
Then it should work!

---

### Post by jeyaganesh on 2008-08-01
Hi Tom,
it says 'bash deb: command not found'
Moreover I was trying to install Banshee 1.2 from ppa.launch pad website only.

---

### Post by Tom--d on 2008-08-01
> **jeyaganesh said:**
> Hi Tom,
it says 'bash deb: command not found'
Moreover I was trying to install Banshee 1.2 from ppa.launch pad website only.

I just installed it. 

Do it in Software Resources then Third party. Then add it.
Then
```
sudo apt-get update
sudo apt-get install banshee-1
```

done :)

---

### Post by jeyaganesh on 2008-08-01
Yes thanks,
I did exactly what they instructed (adding to software source) in this page [https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)
I installed new Banshee.:popcorn:

---

