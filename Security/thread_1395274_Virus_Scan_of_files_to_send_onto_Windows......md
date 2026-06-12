---
title: "Virus Scan of files to send onto Windows....."
date: 2010-01-31
forum: Security
---

### Post by listerdl on 2010-01-31
Hi I know that there is little need for me to install an anti-virus etc - but - I was thinking, it is a good idea to scan folders and files that I send to colleagues that run windows.

Whats the best way and programme to do this? I guess I simply install an AV programme and thats it!

Any ideas for the best one to use?

Thansk!

---

### Post by Barriehie on 2010-01-31
ClamAV is popular.  It's in the repos.

Barrie

---

### Post by listerdl on 2010-01-31
When I look in the Synaptic, there are many programs relating to ClamAV - should I install them all?

Or my question asked antother way is, how do i install ClamAV?

thanks for all replies!

---

### Post by Barriehie on 2010-01-31
> **listerdl said:**
> When I look in the Synaptic, there are many programs relating to ClamAV - should I install them all?

Or my question asked antother way is, how do i install ClamAV?

thanks for all replies!

If you:
```

sudo apt-get install clamav
```
it will install the required other files.

Barrie

---

### Post by Dalek Draco ON LINUX on 2010-02-01
I run Bitdefender Anti-Virus. Basically have it completely turned off, and then alt +f2 'gksudo bdgui' to open it and scan files as desired, before sending them to a poor Windows user.

ClamAV is also good, but you have to type in the location you want to scan rather than browsing your folders/files.

---

### Post by Leppie on 2010-02-01
clamav also has a tk gui:
```
sudo apt-get install clamtk
```

---

