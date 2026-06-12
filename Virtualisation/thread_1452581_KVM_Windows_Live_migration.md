---
title: "KVM Windows Live migration"
date: 2010-04-12
forum: Virtualisation
---

### Post by TheR on 2010-04-12
Ubuntu Lucid beta2, beta1, Alpha ...

What has been your practice with Windows Live migration on KVM. I have 3 KVM servers attached to iSCSI. Two servers are for production one is for testing. I can say that everything works quite good except the Windows Live migration issue. 

The thing is if the server which is beeing live migrated does nothing special migration (just beeing pinged) works OK. If I have open RDC session live migration seems OK, virsh reports that instance is running,  but virtual machine is practicly dead. Ping and nothing else works. And machine had to be destroyed and started again.

Same thing happens if machine has some load (ex. running hdtach). But not always. So I am asking you what is your practice with KVM live migration. 

I haven't seen same problem with Linux guests. Althow I haven't done lots of tests with load yet.


by
TheR

---

