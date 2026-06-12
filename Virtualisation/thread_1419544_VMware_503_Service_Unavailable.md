---
title: "VMware 503 Service Unavailable"
date: 2010-03-02
forum: Virtualisation
---

### Post by mishfit on 2010-03-02
Ok, I have found this issue scattered all over the web, however most threads containing some sort of solution have seemed much simpler than my problem:

I switched from vmware workstation 6 to vmware server 2.0.1 running on an Ubuntu 9.04 host (with Kernel 2.6.28-18-server). vmware worked fine on workstation. I simply want to have vmware running whether I was logged in (GUI) or not.

2 days ago (when I switched) [http://localhost:8222/ui](http://localhost:8222/ui) or [https://localhost:8333/ui](https://localhost:8333/ui) worked in firefox (currently my only browser besides w3m).

Today neither urls work from firefox (instead the output is '503 Service Unavailable').

Interestingly, I can start/stop connect to my hosts via command line:
```

$ vmrun -u [myusername] -p [mypassword] -h 'http://localhost:8222/sdk' list
Total running VMs: 0

```

and starting my vms is simple and works just fine...
```

vmrun -u [myusername] -p [mypassword] -h 'http://localhost:8222/sdk' start "[standard] azcdskpc-acct/azcdskpc-acct.vmx

```

obviously **vmware-hostd** is listening on the ports to which it should (excuse my clumsy, inefficient regex):
```

$ sudo netstat -nlp | grep 'vm' | grep '8[0-9][0-9][0-9]'
tcp        0      0 0.0.0.0:8333            0.0.0.0:*               LISTEN      4232/vmware-hostd
tcp        0      0 127.0.0.1:8307          0.0.0.0:*               LISTEN      4232/vmware-hostd
tcp        0      0 0.0.0.0:8222            0.0.0.0:*               LISTEN      4232/vmware-hostd
unix  2      [ ACC ]     STREAM     LISTENING     8840     3596/vmnet-natd     /var/run/vmnat.3596


```

since it seems that everything is working fine (my vms start/stop/"are listed" properly from the command line)...only the web portion of vmware server seems to malfunction.

I checked the logs to see what, if anything was being written (today):
```

$ ls /var/log/vmware -alR --sort=time | grep '2010-03-01'
-rw-r--r--  1 root root  55814 2010-03-01 23:08 hostd-7.log
drwxr-xr-x 18 root root   4096 2010-03-01 22:29 ..
-rw-r--r--  1 root root      0 2010-03-01 21:55 hostd-trace.log
drwxr-xr-x  3 root root   4096 2010-03-01 21:55 .
-rw-r--r--  1 root root      1 2010-03-01 21:55 hostd-index
lrwxrwxrwx  1 root root     27 2010-03-01 21:55 hostd.log -> /var/log/vmware/hostd-7.log
-rw-r--r--  1 root root  64192 2010-03-01 21:53 hostd-5.log
-rw-r--r--  1 root root   2690 2010-03-01 19:52 hostd-6.log
-rw-r--r--  1 root root 212809 2010-03-01 19:18 hostd-4.log


```

of most peculiar interest was hostd-7.log (the most recently written-to file):
```

$ tail -20 /var/log/vmware/hostd-7.log
#output repeated about 10 times
[2010-03-01 23:23:27.596 'Proxysvc Req00016' 3063569296 warning] Connection to server localhost:8308 failed with error Connection refused.  Retrying...
#and ended with
[2010-03-01 23:23:27.618 'Proxysvc Req00016' 3063569296 warning] Exception while processing request: Connection refused

```

I hope I've skirted that happy medium between too little information and too much. Where should I check? what do I need to start? in order to get the web mgmt working again?

Other Info:
(I have 8 vms; 4 win xp, 3 ubuntu 9.10, and 1 windows 3.1...I love gorillas)
I've bounced the host twice today...not that that should change a thing...hangover from xp days...eh.

---

### Post by dcstar on 2010-03-02
> **mishfit said:**
> 
I switched from vmware workstation 6 to vmware server 2.0.1 running on an Ubuntu 9.04 host (with Kernel 2.6.28-18-server).
.......
I hope I've skirted that happy medium between too little information and too much. Where should I check? what do I need to start? in order to get the web mgmt working again?
.......

Most likely you did not totally remove VMware Workstation, so the new VMware Server system cannot use the required resources.

---

### Post by mishfit on 2010-03-02
David, thanks for the reply. I would've agreed with that statement if my issues were vmnet, vmmon (or even any congruent modules between server and workstation). However, my only problem resides in a module that workstation doesn't install: **webAccess**.

---

### Post by mishfit on 2010-03-02
It appears that the offending module was the jre under **webAccess**. I must have done something to modify the files under the jre's bin (/usr/lib/vmware/webAccess/java/jre1.5.0_15/bin). After restoring those to the original my problem disappeared.

---

