---
title: "instance terminating soon."
date: 2011-03-23
forum: Ubuntu Cloud and Juju
---

### Post by cloud25 on 2011-03-23
while i running an instance.i amgetting the following error ,where instance getting terminated state as soon as running mode arrived. 

server@Node:~$ euca-run-instances -g wiki -k mykey -t c1.medium emi-E2491084
RESERVATION    r-375E06AB    admin    admin-wiki
INSTANCE    i-2B520640    emi-E2491084    0.0.0.0    0.0.0.0    pending    mykey    0        c1.medium    2011-03-23T17:51:57.383Z    cluster1    eki-F8E1110D    eri-0D71117D
server@Node:~$ watch -n1 euca-describe-instances

RESERVATION     r-4DA80908      admin   wiki
INSTANCE        i-3D330822      emi-E2491084    192.168.0.50    172.19.1.2      terminated      m
ykey    0               c1.medium       2011-03-23T17:46:57.037Z        cluster1        eki-F8E11
10D     eri-0D71117D

[7]+  Stopped                 watch -n1 euca-describe-instances
server@Node:~$ euca-get-console-output i-2B520640
DefaultJavaComponent: Instance i-2B520640 is not in a running state.


how to solve this problem ...and get the output console

---

### Post by kim0 on 2011-03-24
On your NC machine, inside /var/log/eucalyptus .. check for nc.log and maybe other log files for potential erros

---

### Post by cloud25 on 2011-03-31
what changes are to done in the /var/log/eucalyptus/nc.log
it showing the following lines

[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] NC is looking for configuration $
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] SC is looking for configuration $
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] euca_init_cert(): using file //v$
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] euca_init_cert(): using file //v$
[Thu Mar 10 12:52:24 2011][001179][EUCADEBUG ] doInitialized() invoked
[Thu Mar 10 12:52:24 2011][001179][EUCADEBUG ] system_output(): [//usr/lib/euca$
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] Using 1 cores
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] Using 770 memory
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] looking for existing domains
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] no currently running domains to $
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] vnetInit(): VNET Configuration: $
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] checking the integrity of instan$
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] checking the integrity of the ca$
[Thu Mar 10 12:52:24 2011][001179][EUCAINFO  ] Maximum disk available = 835 (un$
[Thu Mar 10 12:52:24 2011][001179][EUCADEBUG ] doDescribeResource() invoked
[Thu Mar 10 12:52:24 2011][001179][EUCADEBUG ] Starting monitoring thread
!
[Thu Mar 10 12:52:24 2011][001179][EUCADEBUG ] doDescribeInstances() invoked
[Thu Mar 10 12:52:30 2011][001179][EUCADEBUG ] doDescribeResource() invoked

---

### Post by kim0 on 2011-04-02
hmm, that log file is not too useful .. what's the output of "kvm-ok" command
Can you check out other log files as well for hints

---

### Post by cloud25 on 2011-04-04
i had used the KVM-ok command..i am using Vmplayer ..i am getting the message as


server@Node:~$ kvm-ok
INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used


now what can i do to solve this problem

---

### Post by kim0 on 2011-04-05
You need to use a real machine to run VMs, running VMs inside a VM (vmplayer) doesn't really work (in general). The min requirements for UEC is 2 machines, with at least the NC machine being physical and supporting VT (kvm-ok) should return successfu

---

