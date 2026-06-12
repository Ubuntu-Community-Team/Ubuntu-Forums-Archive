---
title: "lokkit keeps starting up."
date: 2009-04-13
forum: Security
---

### Post by neba on 2009-04-13
I tried lokkit to see how it works. After a week I was unable to access the internet. Decided to remove Lokkit. After I removed it, every time I start up my computer I have to type this command in the terminal 'sudo /etc/init.d/lokkit stop' and 'sudo apt-get purge lokkit'.

Is there a way to fix this problem I have. I just want to off my computer.

---

### Post by cariboo on 2009-04-14
It looks like you tried to uninstall lokkit while it was still running. You probably have to remove lokkit start up from the rc.d's to do this, open a terminal and type:

```
sudo update-rc.d -f lokkit remove
```

This should stop lokkit from trying to start.

Jim

---

### Post by bodhi.zazen on 2009-04-14
Re-install lokkit , then remove it with the -purge option

```
sudo apt-get remove --purge lokkit
```or use synaptic to remove it and select completely remove. 

If that fails, remove the files manually.

```
locate lokkit
```

---

### Post by neba on 2009-04-17
sweet. Its working fine now. Thank you guys both. :)
That was the easiest problem I was able to solve. lol 
Much obliged,
Neba

---

### Post by mwildam on 2009-06-30
Before removing it manually you should try
```
aptitude purge gnome-lokkit
aptitude purge lokkit
```
That helped in my case.

---

