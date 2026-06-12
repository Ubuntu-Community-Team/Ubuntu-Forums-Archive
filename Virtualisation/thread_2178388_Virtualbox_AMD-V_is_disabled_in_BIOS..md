---
title: "Virtualbox AMD-V is disabled in BIOS."
date: 2013-10-03
forum: Virtualisation
---

### Post by yogiman.uk on 2013-10-03
Hi

I wonder if anyone can shed any light on this problem.

AMD based PC running Ubuntu 12.04 LTS x64

Virtualbox 4.1.12

Virtual Machine: Windows 7 Pro X64

Was working perfectly well with no problems.

Did recent available updates to Ubuntu 12.04 LTS

Virtual Machine now not working gives this error:-

**Failed to open a session for the virtual machine Windows 7 (64 bit).**

**AMD-V is disabled in the BIOS. (VERR_SVM_DISABLED)**

Now remember this worked perfectly before the Ubuntu Updates.

Tried a re-installation of VirtualBox 4.1.12 = Did not work.

Tried an installation of latest verion 4.12.xx from the Oracle VirtualBox web site. = Did not work.

Re-installed VirtualBox 4.1.12 = Still not working.

Now nothing has been changed in the BIOS, if it was working before then AMD-V must have been enabled.  So I can not change this setting in the BIOS.

This has to be something to do with the Updates from Ubuntu that have caused this problem.  I understand that these can break the VirtualBox installation, however as it has now been re-installed and presumably re-compiled it should now work?

Any help would be appreciated.

Thanks

Yogiman!

---

### Post by slickymaster on 2013-10-03
See if this can somehow help you: [Fixing the VERR_SVM_DISABLED problem in VirtualBox]("http://hobnobsandcheese.blogspot.pt/2011/09/fixing-verrsvmdisabled-problem-in.html")

---

### Post by yogiman.uk on 2013-10-03
Hi thanks for the response, I did find this previously and checked it but that does not resolve the problem. In addition as I stated above everything was working fine previously so the correct setting must be applied in the BIOS.

Thanks again for trying to help.

yogiman!

---

