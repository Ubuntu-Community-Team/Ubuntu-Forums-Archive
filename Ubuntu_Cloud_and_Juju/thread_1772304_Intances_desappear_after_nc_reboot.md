---
title: "Intances desappear after nc reboot"
date: 2011-05-31
forum: Ubuntu Cloud and Juju
---

### Post by almacenero on 2011-05-31
Hello 

I'm using  UEC in 3 dell servers, two nodes and one for controller cloud, cluster and storage. I have a serious problem because when I restarted the nodes instances disappear  that are running. I've read that is a possible bug but I have not seen solution to the issue. I'm using the default configuration that brings. My system is ubuntu 10.04.
 I would appreciate any help you can give me since I need to turn on the cloud in my company.:(

Sorry it's my english is not good.

 Greetings

---

### Post by kim0 on 2011-06-04
Hi
I don't really understand. Are you saying when NC restarts, the instances die ? that's really expected! Please explain more what your question is

---

### Post by almacenero on 2011-06-06
> **kim0 said:**
> Hi
I don't really understand. Are you saying when NC restarts, the instances die ? that's really expected! Please explain more what your question is

That's the problem exactly and I have no idea because it may be happening. Then put the log.

NC.log

 [Tue May 31 11:53:32 2011][001207][EUCADEBUG ] doDescribeResource() invoked
[Tue May 31 11:53:32 2011][001207][EUCADEBUG ] doDescribeInstances() invoked
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] NC is looking for configuration in //etc/eucalyptus/eucalyptus.conf///etc/eucalyptus/eucalyptus.local.conf
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] SC is looking for configuration in files (//etc/eucalyptus/eucalyptus.conf,//etc/eucalyptus/eucalyptus.local.conf)
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] euca_init_cert(): using file //var/lib/eucalyptus/keys/node-cert.pem
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] euca_init_cert(): using file //var/lib/eucalyptus/keys/node-pk.pem
[Tue May 31 12:27:38 2011][001235][EUCADEBUG ] doInitialized() invoked
[Tue May 31 12:27:38 2011][001235][EUCADEBUG ] system_output(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/get_sys_info]
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] Using 8 cores
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] Using 1796 memory
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] looking for existing domains
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] no currently running domains to adopt
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] vnetInit(): VNET Configuration: eucahome=/, path=//var/run/eucalyptus/net, dhcpdaemon=, dhcpuser=, pubInterface=eth0, privInterface=eth0, bridgedev=br0, networkMode=MANAGED-NOVLAN
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] checking the integrity of instances directory (/var/lib/eucalyptus/instances/)
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] vrun(): [rm -rf /var/lib/eucalyptus/instances//admin/i-39FD0740]
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] checking the integrity of the cache directory (/var/lib/eucalyptus/instances//eucalyptus/cache)
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eki-F65410E8 directory, size=4166583
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image emi-39711604 directory, size=1075848495
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image emi-E05C107F directory, size=1512056575
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eri-08191147 directory, size=4248915
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eki-AE5917D8 directory, size=3529891
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eki-F3A810D9 directory, size=4100791
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eri-0AEF1161 directory, size=3906613
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image emi-DD451053 directory, size=1512056575
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] - cached image eri-16CD1924 directory, size=8686967
[Tue May 31 12:27:38 2011][001235][EUCAINFO  ] Maximum disk available = 124880 (under /var/lib/eucalyptus/instances/)
[Tue May 31 12:27:38 2011][001235][EUCADEBUG ] doDescribeResource() invoked
[Tue May 31 12:27:38 2011][001235][EUCADEBUG ] Starting monitoring thread
!
[Tue May 31 12:27:38 2011][001235][EUCADEBUG ] doDescribeInstances() invoked
[Tue May 31 12:27:38 2011][001235][EUCAWARN  ] Cannot create ///var/run/eucalyptus/nc-stats!
[Tue May 31 12:27:44 2011][001235][EUCADEBUG ] doDescribeResource() invoked

---

### Post by almacenero on 2011-06-10
hello
 
 Someone with an answer to my problem?

 Greetings

---

### Post by tkarint on 2011-06-15
The problem looks very complicated, I gave up from half-way :) I'm sure someone well versed will soon chime in.

---

