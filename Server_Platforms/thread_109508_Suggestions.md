---
title: "Suggestions"
date: 2005-12-28
forum: Server Platforms
---

### Post by nkingcade on 2005-12-28
what is the suggested firewall, ids, spamware configuration for ubuntu? Or is it roll your own? suggestions?

Neal

---

### Post by lutrafobic on 2005-12-28
'FireStarter' = Firewall that uses iptables. Nice GUI, simple to use/install

No real need for anything else :)


To install 'firestarter':

(in a 'terminal')```
sudo aptitude install firestarter
```

To start the configuration (after installing):

(in a 'terminal')```
sudo firestarter
```


Follow the step-by-step -guide and then your all done.

P.S. Even though the program (firestarter) might seem not to be started, after installation it ALWAYS started.

---

### Post by towsonu2003 on 2005-12-28
[QUOTE=lutrafobic]
P.S. Even though the program (firestarter) might seem not to be started, after installation it ALWAYS starts.[/QUOTE]
```
sudo /etc/firestarter/firestarter.sh *status*
``` to check if it's running... put *start* instead of status to start and *stop* to stop it...

---

