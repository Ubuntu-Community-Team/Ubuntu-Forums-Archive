---
title: "vmware fails to configure"
date: 2007-12-25
forum: Virtualisation
---

### Post by rickycodie on 2007-12-25
i've configured it from source code and everything says it installs fine-no errors, so when i  enter /usr/bin/vmplayer and this is what happens

ricky@ricky-laptop:~$ /usr/bin/vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

ricky@ricky-laptop:~$

i've configured it three times and it hasn't taken at all. i've ran the suggested script and still no dice. reboot system and still no fun. so any help?

ricky

---

### Post by popch on 2007-12-26
What happened when you 'configured it three times', as you say?

Did you remember to run  /usr/bin/vmware-config.pl using sudo?

By the way, did you 'configure from source code' for a particular reason? Last time I looked, you could install the VMWare Player through ***Add/Remove application*** in the Applications menu.

---

### Post by rickycodie on 2007-12-26
the add remove vmware package is broken, and each time i configured it i used the command as you said. 

every time i configured it it said that it configured fine.

---

