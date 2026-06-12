---
title: "[SOLVED] VMWare won't start"
date: 2008-08-20
forum: Virtualisation
---

### Post by antknee869 on 2008-08-20
I am running Ubuntu 804. I installed VMWare Workstation 6.02 successfully however when I click on the icon, nothing happens. The program doesn't launch.
If I type vmware in the terminal it says:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

I followed it's instructions, rebooted, typed vmware in the terminal again and guess what? Same message.
I followed numerous tutorials on this site and vmware's site

I am lost, any ideas?
Thanks

---

### Post by dexter.deepak on 2008-08-20
have a look here :
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by bodhi.zazen on 2008-08-20
Follow the tutorial above, particularly the post-install configuration.

Should work, if not, what additional steps have you taken (post install) and what error message are you getting ?

note: The any-any update is somewhat outdated and not needed.

---

### Post by antknee869 on 2008-08-20
I followed those direction but I get the same results. The installation itself completes succesfully. However when I click on the vmware workstation icon, an icon in the taskbar says "starting" but then it goes away and vmware never opens.
If I type "vmware" in the terminal I get this:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


But like I said originally, no matter how many times I run vmware-config.pl I get the same message.

---

### Post by bodhi.zazen on 2008-08-20
Go here : [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

Start at step 5 "[FONT=Times New Roman]Post-install configuration. Last, before running vmware :"[/FONT]

---

### Post by antknee869 on 2008-08-20
Thanks, but this didn't help. Same exact message....

---

### Post by antknee869 on 2008-08-25
I installed the VMWare Workstation 6.5 beta and it works flawlessly.

---

