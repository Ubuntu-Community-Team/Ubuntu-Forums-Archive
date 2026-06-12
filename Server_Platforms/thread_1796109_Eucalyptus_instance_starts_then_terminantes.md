---
title: "Eucalyptus instance starts then terminantes"
date: 2011-07-03
forum: Server Platforms
---

### Post by mikec007 on 2011-07-03
I spend 6hrs yesterday fighting with Ubuntu Server 11.04 trying to get a private cloud setup.  Worthless.  I reinstalled 10.04 and everything registered and works now.  

However, now when I try to launch an instance, it goes from pending, to running then terminates.  

This is what it looks like after I launch the instance. 
```
control@cloud-controller:~$ euca-run-instances emi-DE261062 -k mainkey -t c1.medium
RESERVATION	r-52930976	admin	admin-default
INSTANCE	i-31F10614	emi-DE261062	0.0.0.0	0.0.0.0	pending	mainkey	0		c1.medium	2011-07-03T17:20:11.909Z	cluster1	eki-F45B10E3	eri-08D81150
```

Then

```
RESERVATION     r-52930976      admin   default
INSTANCE        i-31F10614      emi-DE261062    192.168.0.170   172.19.1.2
terminated      mainkey 0               c1.medium       2011-07-03T17:20:11.909Z
        cluster1        eki-F45B10E3    eri-08D81150
```


This is the cc.log file on the CC

```
[Sun Jul  3 08:24:03 2011][001466][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Sun Jul  3 08:24:03 2011][001466][EUCADEBUG ] DescribeInstances(): returning: instanceId=i-31F10614, state=Teardown, publicIp=0.0.0.0, privateIp=172.19.1.2, volumesSize=0
[Sun Jul  3 08:24:03 2011][001466][EUCADEBUG ] DescribeInstances(): done
[Sun Jul  3 08:24:03 2011][000827][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
```

Here is the nc.log from the node. 

```
[Sun Jul  3 08:13:11 2011][001191][EUCAINFO  ] doTerminateInstance() invoked (id=i-3ED80707)
[Sun Jul  3 08:13:11 2011][001191][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-3ED80707' (code=42)
[Sun Jul  3 08:13:11 2011][001191][EUCAWARN  ] warning: domain i-3ED80707 to be terminated not running on hypervisor
```

---

