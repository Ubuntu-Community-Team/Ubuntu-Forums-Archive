---
title: "How to run vb script on a Windows 7 box from Ubuntu?"
date: 2012-02-20
forum: Server Platforms
---

### Post by deepakdeshp on 2012-02-20
I need to run a vb script on a Windows 7 box remotely from a Ubuntu 10.04 server automatically. I have tried to search but not found an answer. Any help will be appreciated.

---

### Post by nsnidanko on 2012-02-27
I would take the following approach: establish telnet connection to your Windows 7 box and execute vb script from there. You can use ssh instead, since telnet transmits password in plain text.

---

### Post by deepakdeshp on 2012-03-01
I want to run the vb script on the WIndows 7 box from command line. I will be putting this in cron once successful. Telnetting may not serve what I want to do

---

### Post by VanJr on 2012-03-01
> **deepakdeshp said:**
> I want to run the vb script on the WIndows 7 box from command line. I will be putting this in cron once successful. Telnetting may not serve what I want to do

Then use SSH. You will need to install and SSH server on the Windows 7 box.

---

