---
title: "Protecting windows files when i'm using ubuntu"
date: 2016-02-22
forum: Security
---

### Post by tharushi_pabodya on 2016-02-22
I'm new to ubuntu. The problem i have is if i acciedently delete or some virus delete my windows files( they are in a seperate partion) it could be a huge problem. How can i protect them by ejecting the relavent partition?

---

### Post by HermanAB on 2016-02-22
Simple.  Don't mount that file system.  

If it is automatically mounted, delete the relevant line in /etc/fstab, or change the relevant line so it mounts read only, instead of read write.

---

### Post by bashiergui on 2016-02-22
> **tharushi_pabodya said:**
> I'm new to ubuntu. The problem i have is if i acciedently delete or some virus delete my windows files( they are in a seperate partion) it could be a huge problem. How can i protect them by ejecting the relavent partition?
A backup of the data would solve the problem. Get a removable drive or add a second hard drive. 

A virus compromising your windows data is far more likely when you're running the windows operating system. You can't eject windows data when running windows. A good automated backup would solve that. 

For a virus to compromise another partition while running the linux operating system, the odds are so low it might as well be impossible. Accidental deletion is possible, protect against that with backups.

TL;DR back your important data up. If it's not backed up it's not important.

---

