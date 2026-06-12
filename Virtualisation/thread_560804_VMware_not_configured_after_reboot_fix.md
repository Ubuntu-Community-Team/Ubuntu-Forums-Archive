---
title: "VMware not configured after reboot fix"
date: 2007-09-26
forum: Virtualisation
---

### Post by Cornerville on 2007-09-26
I have found the solution, at least for my system, for vmware-server needing a reconfiguration after every reboot.  The problem, in my case, was incomplete removal of vmware-player that I had installed before.  The uninstaller leaves files that cause a conflict when the program starts up from boot and generates a /etc/vmware/not_configured file.  You can remove this file and the program will work until you boot it again, then it the problem reoccurs.

If you have this problem, look in your etc/init.d file and the etc/rc*.d files and you will probably find more vmware and vmware-server files plus some k*vmware files.

I fixed the problem by uninstalling vmware-server.  This will not remove your virtual machines.  Then I ran whereis and deleted all the vmfiles it found.  In this case /usr/lib/vmware.  Actually I moved it to a backup directory, just in case.  Then, I opened /etc/init.d and all the /etc/rc*.d files and removed any files that had vmware in the name.  Then, I reinstalled vmware-server and voila, problem solved!

Hope this helps

For the record, I am running fiesty and installed the server from the repositories.

---

### Post by tristangrimaux on 2008-02-07
Great!! It worked for me too!!!!! Great tip.

---

### Post by karlkropf on 2008-02-08
This fix also worked after a recent linux header update (2.6.22-14.51 on 7.10) broke vmware server.

---

### Post by quaternio on 2008-09-10
hi there, 

thanks. this was just the fix i needed. i used the [install_vmware.sh]("http://ubuntuforums.org/showthread.php?t=788169") script which completed successfully, but when i went to start vmware i kept getting the error: 

```
"vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl."
```

deleting the file in /etc/vmware/not_configured fixed this.

---

