---
title: "Ubuntu One does not work on U10.10-64bit"
date: 2011-03-23
forum: Ubuntu One (CLOSED)
---

### Post by sbrbot on 2011-03-23
I have two computers connected to Ubuntu One (Ubuntu 10.04 and Ubuntu 10.10 32bit both) and want to connect the third one with Ubunut 10.10 64bit and it wont connect!

ubuntu-syncdaemon and ubuntu-sso-login service work in background. When I click on Connect it writes Synchronizing... for three seconds and disconnects immediately.

---

### Post by Stebbins on 2011-03-23
Unfortunately I can't solve your problem, but I can assure you that it is not related to the 64-bit architecture.  I am also running 10.10 on a 64-bit, and Ubuntu One... well it doesn't work, but it is broken in exactly the same way as on my 32-bit system :P

---

### Post by sbrbot on 2011-03-23
Probably the problem is general and not strictly related to 32bit or 64bit architecture as you suggest. Yesterday I even succeeded to connect to Ubuntu One repository with that 10.10@64bit machine but I removed this machine from Ubuntu One repository (for some reason) from another machine. Since then I haven't been able to connect any more.

---

### Post by Scott Deagan on 2011-03-28
I had the same problem. "Re-kick-starting" the U1 sync daemon solved the problem for me:

1. Install CLI tools: sudo apt-get install ubuntuone-client-tools
2. Stop the U1 daemon: u1sdtool --quit
3. Delete sync daemon data: rm -rdf ~/.local/share/ubuntuone/syncdaemon/*
4. Start the U1 daemon: u1sdtool --start
5. Connect to your account: u1sdtool --connect
6. Refresh volumes: u1sdtool --refresh-volumes

I've been using U1 for 3 days now, and it's surprisingly fast. Within seconds of changing or copying something over to a synchronized directory, it appears in the U1 cloud (I refresh [https://one.ubuntu.com/files/](https://one.ubuntu.com/files/) in the browser to see newly added files appear).

I hope that this helps...

---

### Post by sbrbot on 2011-03-30
I don't know what is going on with this Ubuntu One (U1) service. I changed exactly nothing about U1 settings on my machine and today it connects fine! It seems that something wrong was on their side. I remember that before U1 reported my repository of 2GB total size, now it reports 1.5GB for the same repository (U1 space). Also I have the same computer registered in repository twice; once it is assigned with name "CyberMini" and second time it is "Ubuntu One @ CyberMini".

---

### Post by sbrbot on 2011-08-26
I found the solution: I had to delete Ubuntu one account manually;

System->Preferences->Passwords and Encryption Keys

Ubuntu One password has to be deleted in it.

After deleting it one will be asked again about to create new Ubuntu One acc while connecting to Ubuntu One repository.

---

### Post by Vinas on 2011-10-05
Unfortunately U1 does have many problems. Hopefully they will get this sorted out... As it stands now I'm still paying for it but with the frequency of missed syncs I'm about to just stop and pay [much] more for dropbox. If U1 can reach the level of drop box then they'll keep a lot of customers... As it stands now, expect this project to die a slow and painful death. :(

---

