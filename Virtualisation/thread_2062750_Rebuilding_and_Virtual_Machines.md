---
title: "Rebuilding and Virtual Machines"
date: 2012-09-25
forum: Virtualisation
---

### Post by duranl on 2012-09-25
Hello open source peoples of the world,

I want to rebuild my computer, but I have a question regarding a virtual machine on it.  It is currently running Ubuntu, and I use VirtualBox to run WinXP.  On that WinXP I have fully licensed versions of SPSS and AMOS (statistical analysis software) which is the only reason I have XP.  If I were to rebuild my Ubuntu machine and import the WinXP virtual machine, would I lose my license?  I ask this because I have tried to import the WinXP on another computer and the license was not valid on it.

Thanks in advance :)
):P:KS;):p

---

### Post by Lars Noodén on 2012-09-25
Isn't AMOS a module for SPSS?  There is now a native version of SPSS for Linux according to the home page at IBM.  Could you use that?

---

### Post by JKyleOKC on 2012-09-25
If you copy all of the VirtualBox files in your home directory over to the new machine after installing vbox there, your WinXP installation and licenses should remain unchanged. They apply to the guest machine, not to the host, and the guest machine is completely contained in those files.

I've done this with an installation of Microsoft Publisher, with no problem, and also moved WinXP systems with no effect at all on their activation status.

---

### Post by duranl on 2012-09-26
> Isn't AMOS a module for SPSS?  There is now a native version of SPSS for Linux according to the home page at IBM.  Could you use that?

Yea, AMOS rides on SPSS, but each one has it's own license.  My university only provides Windows and Mac versions at the discounted price ($25 for both).  I asked about Linux/GNU specifically, which they didn't supply #-o.  Microsoft has a virtual monopoly in that school.  They even run Exchange as the mail server for faculty and use Hotmail for students.

> If you copy all of the VirtualBox files in your home directory over to the new machine after installing vbox there, your WinXP installation and licenses should remain unchanged. They apply to the guest machine, not to the host, and the guest machine is completely contained in those files.

I've done this with an installation of Microsoft Publisher, with no problem, and also moved WinXP systems with no effect at all on their activation status.

I'm going to import it tomorrow.  I'll keep this thread open until then and report back with the results.

Thank you!

---

### Post by Lars Noodén on 2012-09-27
> **duranl said:**
> Yea, AMOS rides on SPSS, but each one has it's own license.  My university only provides Windows and Mac versions at the discounted price ($25 for both).  I asked about Linux/GNU specifically, which they didn't supply #-o.  Microsoft has a virtual monopoly in that school.  They even run Exchange as the mail server for faculty and use Hotmail for students.

Ouch. MS Exchange is not an adequate substitute for e-mail. Hotmail isn't so hot either, from what I recall it even lacks IMAP support. 

But about that license, it would be very unusual for their agreement to limit to specific operating systems.  I bet if you are persistent and get past the first layer or so of bureaucracy you can get an answer to the affirmative.

---

### Post by duranl on 2012-09-28
Sorry for the delay.  I exported the virtual machine, saved it on another computer, rebuilt the original machine, and imported the virtual machine.  The products dais that they didn't have the licenses.  I used the original codes and that worked.  So, whatever that means 8-[

---

### Post by houstonbofh on 2012-09-30
A lot of software keys itself to things it figures will not change.  That is UUID of the Windows install, serial on the CPU, or MAC address on the first (usually on board) nic.  This is good in that KVM can set all of those things.  Bad in that if you didn't record what they were...

Call the vendor and let them know that your motherboard was replaced under warranty and since then nothing works.  They will usually get you going again.  DO NOT MENTION KVM.

---

