---
title: "LibreOffice bug needs confirmation"
date: 2014-03-04
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2014-03-04
After upgrading from LibreOffice version 4.2.0 to version 4.2.1 I'm getting on every start of writer or calc the following error:

```
The application cannot be started.
Extension Manager: exception in synchronize
```


The upstream version 4.2.1 is working fine. I have already opened a bug report for this issue ([https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1286102](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1286102)) but currently this bug would be another major breakage for me on Ubuntu 14.04. Has somebody else this issue too?

---

### Post by grahammechanical on 2014-03-04
I do not. I have LibreOffice 4.2.1.1 Build ID: 42mO (Build: 1). I run LibreOffice Writer and Calc every day and I never have this error. I have never installed an extension either, for that matter.

I just opened Extension Manager and the panel is blank. Is that normal? But the link to the LibreOffice Extensions web page works. This is the best that I can add.

Regards.

---

### Post by ventrical on 2014-03-04
Just upgraded . Works great here.

---

### Post by Cavsfan on 2014-03-04
I have 1:4.2.1 installed and both writer and calc work fine. I have been using them off and on and not had any problems.
I also opened extension manager and it was blank. I clicked add and it asked what I wanted to add. Looked normal to me.

---

### Post by mc4man on 2014-03-04
The error is generally attributed to wrong permissions on some file/directory in your LO install.
Do a web search on error for some possible locations

---

### Post by Sworddragon on 2014-03-05
Thanks for all your help. I have just downgraded LibreOffice to make a test and upgraded it then again and all was working fine. I haven't installed any extensions too but maybe something has really borked the permissions which got fixed on the upgrade.

---

### Post by juan-2 on 2014-07-26
I'm also experiencing this issue. I don't understand why the thread was marked as "Solved". What do I have to do to sort it out?

---

### Post by bapoumba on 2014-07-26
@juan-2 : are you running the Ubuntu development release ?

---

### Post by juan-2 on 2014-07-26
Thanks @bapoumba for picking this up. No, just the stable version 14.04.1 LTS 64 bit

---

### Post by bapoumba on 2014-07-26
> **juan-2 said:**
> Thanks @bapoumba for picking this up. No, just the stable version 14.04.1 LTS 64 bit

Please start a new thread in the General area. Here is the sub-forum for the 14.10 development release, thanks (and not seeing this bug in 14.10 BTW).

---

### Post by cariboo on 2014-07-27
Thread closed, as it isn't concerning Utopic.

---

