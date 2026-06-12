---
title: "postfix installed during upgrade"
date: 2024-02-25
forum: Ubuntu Development Version
---

### Post by jbicha on 2024-02-25
Upgrading Ubuntu 24.04 LTS will install postfix (an email server) which asks a debconf question interrupting the upgrade. You can answer the question however then afterwards run

```

sudo apt purge postfix

```

I filed [a bug]("https://launchpad.net/bugs/2054908") about the issue. My wild guess was wrong, but still it will be important for it to be fixed.

---

### Post by Claus7 on 2024-02-25
Hello,

I was asked a question during one of the latest updates (not upgrade). It was a puzzle to me, yet I responded and update went fine. I haven't noticed any issues since then. Also it was the first time that I was asked about how I want the updates to take place, when restarting of my system is required.

Regards!

---

### Post by grahammechanical on 2024-02-25
> Upgrading Ubuntu 24.04 LTS will install postfix (an email server) which asks a debconf question interrupting the upgrade

That happened to me a hour ago. I did not know what it was about. I choose the default options. I am just glad that it did not break the Thunderbird settings to the ISP.

I have yet to test today's daily ISO image in an install. If these questions are a permanent addition to the Ubuntu install process then a lot of people will find installing Ubuntu not so friendly.

Regards

---

### Post by corradoventu on 2024-02-25
postfix question

---

### Post by jbicha on 2024-02-25
> **grahammechanical said:**
> If these questions are a permanent addition to the Ubuntu install process then a lot of people will find installing Ubuntu not so friendly

It is a bug and will be fixed. Also, it only affects upgrades (including upgrades from an older Ubuntu release or for those already using Noble). New installs of 24.04 LTS are not affected.

---

### Post by ajgreeny on 2024-02-25
When I saw this a few days ago updating one of my installs of 24.04 I chose the "Internet site" option in the first box and left the second as it showed when it opened, though I can't now remember what that was.
The system worked fine following that and I'm fairly sure that thunderbird still worked even though it is possible that I didn't try using thunderbird on that particular system as I install in KVM and then remove the VMs again a few days later and reinstall with a newly downloaded daily iso..

---

### Post by Irihapeti on 2024-02-26
I just upgraded my Surface Go 3 and wondered what on earth was going on, as I couldn't remember installing Postfix previously. Thanks for the heads-up.

---

