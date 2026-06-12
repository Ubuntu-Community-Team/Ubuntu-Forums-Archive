---
title: "Virtualbox Security"
date: 2008-09-12
forum: Virtualisation
---

### Post by donniezazen on 2008-09-12
Hi Guys.

Virtualbox has made my life easy. Please help me with following questions.

I am concerned about security of my system. I am always scared of all those viruses and bots. Is my system secure and stable even after installing Vista as guest? Any tips.

Is it safe to make whole your home folder as shared folder?

Thanks.

---

### Post by Thelasko on 2008-09-12
That all depends on what you want secure.  

[LIST]
[*]If by secure you are referring to your Ubuntu host:

Ubuntu is immune to Windows viruses, but it can be a carrier for them.  By sharing your /home folder with Vista, you have two worries.

[LIST=1]
[*]A virus can plant itself in your /home folder and infect other Windows guests in virtual machines.

[*]A virus can delete/corrupt your data in your /home folder from within Windows.
[/LIST]

Therefore, I wouldn't share my entire /home folder with Windows.  I have a folder named VMshare or something similar that I move files in and out of as I wish to share them with the VM.  Any malware will be contained to that folder, and any data loss/corruption will be limited to that folder, because these things can only happen to folders Windows has access to.


[*]If by secure you mean the Windows guest, the answer is no.  You may benefit from running a firewall in Ubuntu.  But you still won't have any virus protection.  The good news is, you can back up your VMs and simply delete any infected ones and go back to known good ones very easily.
[/LIST]

---

### Post by donniezazen on 2008-09-13
> **Thelasko said:**
> That all depends on what you want secure.  

[LIST]
[*]If by secure you are referring to your Ubuntu host:

Ubuntu is immune to Windows viruses, but it can be a carrier for them.  By sharing your /home folder with Vista, you have two worries.

[LIST=1]
[*]A virus can plant itself in your /home folder and infect other Windows guests in virtual machines.

[*]A virus can delete/corrupt your data in your /home folder from within Windows.
[/LIST]

Therefore, I wouldn't share my entire /home folder with Windows.  I have a folder named VMshare or something similar that I move files in and out of as I wish to share them with the VM.  Any malware will be contained to that folder, and any data loss/corruption will be limited to that folder, because these things can only happen to folders Windows has access to.


[*]If by secure you mean the Windows guest, the answer is no.  You may benefit from running a firewall in Ubuntu.  But you still won't have any virus protection.  The good news is, you can back up your VMs and simply delete any infected ones and go back to known good ones very easily.
[/LIST]

Thank You for your intelligent reply.

---

### Post by Thelasko on 2008-09-15
Glad I could help.  I was concerned my reply was too long and complex.

P.S. You can simply click the gold star in the lower right of any comments you find helpful to thank that person.

---

### Post by tuxxy on 2008-09-15
Install your security suite as normal in windows, firewall, anti virus etc as you will still want protect the guest OS

---

