---
title: "Worried about rootkit hunter results"
date: 2015-02-10
forum: Security
---

### Post by Loyalis on 2015-02-10
Hi, my VPS was recently compromised and infected. The hosting company told me that they've cleaned the server of the infection, however I've ran a rootkit hunter scan and seen a few worrying things. Here is the full scan, the things I'm not sure about are highlighted in bold..

```
root@badbox:~# sudo rkhunter -c --enable all --disable none --rwo
Warning: The following processes are using deleted files:
**         Process: /usr/bin/tgfvvtxvse    PID: 1608    File: /usr/bin/tgfvvtxvse**
**         Process: /usr/bin/tgfvvtxvse    PID: 1611    File: /usr/bin/tgfvvtxvse**
**         Process: /usr/bin/tgfvvtxvse    PID: 1612    File: /usr/bin/tgfvvtxvse**
**         Process: /usr/bin/tgfvvtxvse    PID: 1615    File: /usr/bin/tgfvvtxvse**
**         Process: /usr/bin/tgfvvtxvse    PID: 1621    File: /usr/bin/tgfvvtxvse**
         Process: /usr/bin/sudo    PID: 3809    File: /dev/pts/0
         Process: /bin/dash    PID: 3810    File: /dev/pts/0
         Process: /usr/bin/xinit    PID: 4044    File: /dev/pts/0
         Process: /usr/bin/xfce4-session    PID: 4061    File: /dev/pts/0
         Process: /usr/bin/dbus-launch    PID: 4092    File: /dev/pts/0
**Warning: File '/tmp/gvxddrshkl' (score: 206) contains some suspicious content and should be checked.**
Warning: File '/tmp/vmware-root/vmware-apploader-1068.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-26937.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-4536.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-1073.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-27797.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-4291.log' (score: 221) contains some suspicious content and should be checked.
Warning: File '/tmp/vmware-root/vmware-apploader-28589.log' (score: 221) contains some suspicious content and should be checked.
Warning: Checking for files with suspicious contents [ Warning ]
```


Does anybody have any idea about what these randomly named files/processes I highlighted could be? Right click -> properties says it's an executable. I can try to upload the contents of the file onto pastebin however I'm not sure if that is against the forum rules or not - so if it's allowed and needed then ask.

I really don't know much about this kind of thing so if there is any information I was meant to provide please ask for it and I'll do my best to provide it.

Best regards

..Also, how can I whitelist .log files?

---

### Post by TheFu on 2015-02-10
Security isn't a checkbox. It is a process.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
There are security links in my sig too.

BTW, you can look at those files and look for dangerous stuff too.  What are the complete permissions for them? Are they suid root? The random names are concerning to me.

---

### Post by fugu2 on 2015-02-11
> **Loyalis said:**
> root@badbox:~#  is this the user that you log in with? You should usually not be running as root as a normal user.

---

### Post by unspawn on 2015-02-11
> **Loyalis said:**
> Hi, my VPS was recently compromised and infected. The hosting company told me that they've cleaned They may be cheap to rent services from but I'm sorry to say by their actions they're security-wise not the hosting company you're looking for. Nobody in their right mind "cleans" root compromises, period.   > **Loyalis said:**
> Does anybody have any idea about what these randomly named files/processes I highlighted could be? Right click -> properties says it's an executable.  Running 'stat' on the binary and 'lsof -Pwln' may reveal more details.   > **Loyalis said:**
> I can try to upload the contents of the file onto pastebin however I'm not sure if that is against the forum rules or not - so if it's allowed and needed then ask. You are right to consider exposing malware inadvertedly however sharing data is an overarching necessity. I'd like a copy (upload in any of the categories at [http://sourceforge.net/p/rkhunter/_list/tickets](http://sourceforge.net/p/rkhunter/_list/tickets)) or feel free to email me.   > **Loyalis said:**
> ..Also, how can I whitelist .log files? That question is of no importance right now: please focus on priority #1 meaning ensuring the situation is mitigated properly and integrity is maintained / restored in full.

---

