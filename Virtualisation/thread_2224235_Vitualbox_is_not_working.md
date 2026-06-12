---
title: "Vitualbox is not working"
date: 2014-05-15
forum: Virtualisation
---

### Post by Cody_Tellor on 2014-05-15
Hello,

i download VB in the Ubuntu Software Center and install it. i open it and made a vm on then open it up and it shows:

Failed to open a session for the virtual machine Windows Vista.

AMD-V is disabled in the BIOS (or by the host OS). (VERR_SVM_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {8ab7c520-2442-4b66-8d74-4ff1e195d2b6}

please help this is my first post on ubuntu forums.

---

### Post by brantcgardner on 2014-05-15
It tells you right in the message what to do - enable AMD-V in the BIOS.  Do that and your VM should run.

Refer to the hardware manufacturer's documentation for your machine for the specific method of how to do that.

Good luck

---

### Post by deadflowr on 2014-05-15
Thread moved to Virtualisation

---

### Post by HiImTye on 2014-05-15
go to virtualbox, select the os thats giving you trouble, click on 'settings' then navigate to system > acceleration. turn on 'enable vt-x/amd-v' and hit OK

---

### Post by maxweis1 on 2014-07-31
It finally worked for me.  I had to use Windows 7 32-Bit.  64-Bit will not work

You have to use the 32-Bit version for it to work.

---

### Post by firegrim on 2015-05-02
Yeah, but it`s how does it work for 64-Bit?? Enabling the VT-x in the BIOS or from the settings doesn`t do the job....

---

### Post by QIII on 2015-05-02
... and back to sleep.

firegrim:  Please start a new thread with your issue.  You may refer to this thread if you think it will be helpful.

In your new thread, please let everyone know the hardware specifications of your host machine.

---

