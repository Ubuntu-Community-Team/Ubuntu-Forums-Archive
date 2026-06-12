---
title: "Could not find data source"
date: 2011-02-22
forum: Ubuntu Cloud and Juju
---

### Post by nbartolome on 2011-02-22
Hi,

I've been googling for the past few days trying to get instances on my UEC cluster to run but haven't had much success.

I have the CLC/CC/WC/SC running on one machine.

I have the NC running on a separate machine.

Both machines are HP DL160 with dual nics.   eth0 is reserved for the iLO (management interface) and eth1 is being used as the primary network interface.

I've installed both hosts using the UECCDinstall (except that I'm installing with a USB drive) with this document: [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

The cloud comes up.   The issue is that I cannot get any instance to successfully boot.   The only image that I can get to run is Lucid AMD64 from the store.  Any of the other images from store the or [http://uec-images.ubuntu.com](http://uec-images.ubuntu.com) will remain in pending mode until they eventually terminate themselves.

The Lucid amd64 image will go into a running state, however it won't boot up successfully.   The error from the console is:

<snip>
Begin: Running /scripts/init-bottom ...
Done.
[    3.803895] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.917240] EXT3-fs warning: checktime reached, running e2fsck is recommended

[    3.950516] EXT3 FS on sda1, internal journal
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
Could not find data source
Failed to get instance datainit: cloud-init main process (541) terminated with s
tatus 1
mountall: Event failed[FONT=monospace]
</snip>

[FONT=Verdana]I apologize if this is a repost but there has to be someone else that has encountered this same situation.   Please let me know what logs/info I could provide as I've been at it for the past week and just don't know where else to look.   

Thanks.
[/FONT][/FONT]

---

### Post by nbartolome on 2011-02-23
A few updates:

I've primarily been using the command line from the CC/CLC/SC/WC to try and run instances.

I've read suggestions on running instances as a different user other than 'admin'.   So on the frontend I created a new user.   Then using Hybridfox I've been trying to launch instances as that new user.   The good news is that most of my instances actually go into a running state instead of pending/terminated.

The bad news is that they still don't successfully boot into the OS.

When I try to launch Ubuntu 10.04 the error is still "Could not find data source".

When I try to launch Ubuntu 9.04 the error waits at "[80G  * Waiting for EC2 meta-data service"

---

### Post by kim0 on 2011-02-23
It seems metadata service is not running correctly. Assuming that is not a bug, you might have configured a networking mode that doesn't have a metadata service

Can you please revert to the standard setting of managed_novlan

---

### Post by raymdt on 2011-02-23
Post edited

---

### Post by nbartolome on 2011-02-23
> **kim0 said:**
> 
Can you please revert to the standard setting of managed_novlan

Thanks for replying.

I am using managed-novlan.

---

### Post by raymdt on 2011-02-23
Hi,
hmmm this  problem is a bit little bit curious.
So we need more informations about your problem.

Can you post the result of the following commands(as root).
```

euca_conf --list-clusters
euca_conf --list-walruses
euca_conf --list-scs
euca_conf --list-nodes

```

And the cotent of the following files
```

/var/log/eucalyptus/cc.log
/var/log/eucalyptus/registration.log

```

---

### Post by nbartolome on 2011-02-23
Thanks for the reply.  Here's the info requested.

> **raymdt said:**
> Hi,
hmmm this  problem is a bit little bit curious.
So we need more informations about your problem.

Can you post the result of the following commands(as root).
```

euca_conf --list-clusters
euca_conf --list-walruses
euca_conf --list-scs
euca_conf --list-nodes

```
cloud@uec01:/etc/eucalyptus$ sudo euca_conf --list-clusters
registered clusters:
   cluster1  10.12.10.100 
cloud@uec01:/etc/eucalyptus$ sudo euca_conf --list-walruses
registered walruses:
   walrus  10.12.10.100 
cloud@uec01:/etc/eucalyptus$ sudo euca_conf --list-scs
registered storage controllers:
   cluster1  10.12.10.100 
cloud@uec01:/etc/eucalyptus$ sudo euca_conf --list-nodes
registered nodes:
   10.12.10.102  cluster1   i-4493083A  i-595C0A8A  
cloud@uec01:/etc/eucalyptus$ 

> 
And the cotent of the following files
```

/var/log/eucalyptus/cc.log
/var/log/eucalyptus/registration.log

```cc.log is quite noisy so I've only attached the last 100 lines:
**cloud@uec01:/var/log/eucalyptus$ tail -100 cc.log**
[Wed Feb 23 11:57:44 2011][025285][EUCADEBUG ] vnetSetCCS(): setting localIpId: 0
[Wed Feb 23 11:57:44 2011][025250][EUCAINFO  ] DescribeResources(): called
[Wed Feb 23 11:57:44 2011][025250][EUCADEBUG ] DescribeResources(): params: userId=eucalyptus, vmLen=5
[Wed Feb 23 11:57:44 2011][025250][EUCADEBUG ] init_thread(): init=1 607CF000 F752B000 FD5A9000 6074F000
[Wed Feb 23 11:57:44 2011][025250][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a bridge, tunneling disabled
[Wed Feb 23 11:57:44 2011][025250][EUCAINFO  ] DescribeResources(): resource response summary (name{avail/max}): m1.small{2/4} c1.medium{2/4} m1.large{1/2} m1.xlarge{1/2} c1.xlarge{0/1}
[Wed Feb 23 11:57:44 2011][025250][EUCADEBUG ] DescribeResources(): done
[Wed Feb 23 11:57:44 2011][025225][EUCAINFO  ] DescribeInstances(): called
[Wed Feb 23 11:57:44 2011][025225][EUCADEBUG ] DescribeInstances(): params: userId=eucalyptus, instIdsLen=0
[Wed Feb 23 11:57:44 2011][025225][EUCADEBUG ] init_thread(): init=1 607CF000 FE01E000 0409C000 6074F000
[Wed Feb 23 11:57:44 2011][025225][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a bridge, tunneling disabled
[Wed Feb 23 11:57:44 2011][025221][EUCADEBUG ] init_thread(): init=1 607CF000 F7FA0000 FE01E000 6074F000
[Wed Feb 23 11:57:44 2011][025221][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a bridge, tunneling disabled
[Wed Feb 23 11:57:44 2011][025221][EUCAINFO  ] DescribePublicAddresses(): called
[Wed Feb 23 11:57:44 2011][025221][EUCADEBUG ] DescribePublicAddresses(): params: userId=eucalyptus
[Wed Feb 23 11:57:44 2011][025221][EUCADEBUG ] DescribePublicAddresses(): done
[Wed Feb 23 11:57:44 2011][025225][EUCAINFO  ] DescribeInstances(): instance response summary: instanceId=i-4493083A, state=Extant, publicIp=10.12.10.230, privateIp=172.19.1.2
[Wed Feb 23 11:57:44 2011][025225][EUCAINFO  ] DescribeInstances(): instance response summary: instanceId=i-595C0A8A, state=Extant, publicIp=10.12.10.231, privateIp=172.19.1.3
[Wed Feb 23 11:57:44 2011][025225][EUCADEBUG ] DescribeInstances(): done
[Wed Feb 23 11:57:44 2011][025285][EUCADEBUG ] DescribeNetworks(): done
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] monitor_thread(): running
[Wed Feb 23 11:57:48 2011][025844][EUCAINFO  ] refresh_resources(): called
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:57:48 2011][013885][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:57:48 2011][013885][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 client calling 'ncDescribeResource'
[Wed Feb 23 11:57:48 2011][013885][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 done calling 'ncDescribeResource' with exit code '0'
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_resources(): received data from node=10.12.10.102 mem=5860/5348 disk=429110/428076 cores=4/2
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_resources(): done
[Wed Feb 23 11:57:48 2011][025844][EUCAINFO  ] refresh_instances(): called
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:57:48 2011][013886][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:57:48 2011][013886][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 client calling 'ncDescribeInstances'
[Wed Feb 23 11:57:48 2011][013886][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 done calling 'ncDescribeInstances' with exit code '0'
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-4493083A, Extant, 0
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-4493083A/10.12.10.230/172.19.1.2'
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-4493083A/Extant/10.12.10.230/172.19.1.2
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-4493083A reservationId=r-37F8077F emiId=emi-DF4E1078 kernelId=eki-F56310EF ramdiskId=eri-09E41160 emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/ramdisk.manifest.xml state=Extant ts=1298487983 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.2 publicIp=10.12.10.230 privateMac=D0:0D:44:93:08:3A vlan=10 networkIndex=2} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-595C0A8A, Extant, 1
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-595C0A8A/10.12.10.231/172.19.1.3'
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-595C0A8A/Extant/10.12.10.231/172.19.1.3
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-595C0A8A reservationId=r-5AC50972 emiId=emi-E08A107A kernelId=eki-F6F51103 ramdiskId=eri-0B66116A emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/ramdisk.manifest.xml state=Extant ts=1298488106 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.3 publicIp=10.12.10.231 privateMac=D0:0D:59:5C:0A:8A vlan=10 networkIndex=3} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] refresh_instances(): done
[Wed Feb 23 11:57:48 2011][025844][EUCADEBUG ] monitor_thread(): done
[Wed Feb 23 11:57:54 2011][025224][EUCADEBUG ] init_thread(): init=1 607CF000 F7FA0000 FE01E000 6074F000
[Wed Feb 23 11:57:54 2011][025224][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a bridge, tunneling disabled
[Wed Feb 23 11:57:54 2011][025224][EUCAINFO  ] DescribePublicAddresses(): called
[Wed Feb 23 11:57:54 2011][025224][EUCADEBUG ] DescribePublicAddresses(): params: userId=eucalyptus
[Wed Feb 23 11:57:54 2011][025224][EUCADEBUG ] DescribePublicAddresses(): done
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] monitor_thread(): running
[Wed Feb 23 11:57:54 2011][025844][EUCAINFO  ] refresh_resources(): called
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:57:54 2011][013905][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:57:54 2011][013905][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 client calling 'ncDescribeResource'
[Wed Feb 23 11:57:54 2011][013905][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 done calling 'ncDescribeResource' with exit code '0'
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_resources(): received data from node=10.12.10.102 mem=5860/5348 disk=429110/428076 cores=4/2
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_resources(): done
[Wed Feb 23 11:57:54 2011][025844][EUCAINFO  ] refresh_instances(): called
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:57:54 2011][013906][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:57:54 2011][013906][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 client calling 'ncDescribeInstances'
[Wed Feb 23 11:57:54 2011][013906][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 done calling 'ncDescribeInstances' with exit code '0'
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-4493083A, Extant, 0
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-4493083A/10.12.10.230/172.19.1.2'
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-4493083A/Extant/10.12.10.230/172.19.1.2
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-4493083A reservationId=r-37F8077F emiId=emi-DF4E1078 kernelId=eki-F56310EF ramdiskId=eri-09E41160 emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/ramdisk.manifest.xml state=Extant ts=1298487983 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.2 publicIp=10.12.10.230 privateMac=D0:0D:44:93:08:3A vlan=10 networkIndex=2} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-595C0A8A, Extant, 1
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-595C0A8A/10.12.10.231/172.19.1.3'
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-595C0A8A/Extant/10.12.10.231/172.19.1.3
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-595C0A8A reservationId=r-5AC50972 emiId=emi-E08A107A kernelId=eki-F6F51103 ramdiskId=eri-0B66116A emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/ramdisk.manifest.xml state=Extant ts=1298488106 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.3 publicIp=10.12.10.231 privateMac=D0:0D:59:5C:0A:8A vlan=10 networkIndex=3} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] refresh_instances(): done
[Wed Feb 23 11:57:54 2011][025844][EUCADEBUG ] monitor_thread(): done
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] monitor_thread(): running
[Wed Feb 23 11:58:00 2011][025844][EUCAINFO  ] refresh_resources(): called
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:58:00 2011][013972][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:58:00 2011][013972][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 client calling 'ncDescribeResource'
[Wed Feb 23 11:58:00 2011][013972][EUCADEBUG ]     ncClientCall(ncDescribeResource): ppid=25844 done calling 'ncDescribeResource' with exit code '0'
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_resources(): received data from node=10.12.10.102 mem=5860/5348 disk=429110/428076 cores=4/2
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_resources(): done
[Wed Feb 23 11:58:00 2011][025844][EUCAINFO  ] refresh_instances(): called
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://10.12.10.102:8775/axis2/services/EucalyptusNC timeout=20
[Wed Feb 23 11:58:00 2011][013975][EUCADEBUG ] DEBUG: requested URI [http://10.12.10.102:8775/axis2/services/EucalyptusNC](http://10.12.10.102:8775/axis2/services/EucalyptusNC)
[Wed Feb 23 11:58:00 2011][013975][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 client calling 'ncDescribeInstances'
[Wed Feb 23 11:58:00 2011][013975][EUCADEBUG ]     ncClientCall(ncDescribeInstances): ppid=25844 done calling 'ncDescribeInstances' with exit code '0'
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-4493083A, Extant, 0
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-4493083A/10.12.10.230/172.19.1.2'
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-4493083A/Extant/10.12.10.230/172.19.1.2
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-4493083A reservationId=r-37F8077F emiId=emi-DF4E1078 kernelId=eki-F56310EF ramdiskId=eri-09E41160 emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298416313/ramdisk.manifest.xml state=Extant ts=1298487983 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.2 publicIp=10.12.10.230 privateMac=D0:0D:44:93:08:3A vlan=10 networkIndex=2} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_instances(): describing instance i-595C0A8A, Extant, 1
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-595C0A8A/10.12.10.231/172.19.1.3'
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_instances(): storing instance state: i-595C0A8A/Extant/10.12.10.231/172.19.1.3
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-595C0A8A reservationId=r-5AC50972 emiId=emi-E08A107A kernelId=eki-F6F51103 ramdiskId=eri-0B66116A emiURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/image.manifest.xml kernelURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/kernel.manifest.xml ramdiskURL=http://10.12.10.100:8773/services/Walrus/image-store-1298414784/ramdisk.manifest.xml state=Extant ts=1298488106 ownerId=cloud keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCbXDronRkN3F5ZK4rupfYLyD2ZJZFqQ1IAxdOEMbAJSaZL7Wju5ffrYmheOBf8SWen7K7KMpqJxFip++k7QR0x2Z9herpeDAYY078jdY8EVer0V0cjf2jRD4Ewf4XgOKv0uh8Ro+rQUoTxUI/8ETnPN4KNlSuEcVg1ujTxsNmG09Us2nZh35Zy+JEz+PGx3dVYricIEPBacpv+Jq7WwQ7IL+Far+5u4pAPhozgfdesqxpoUtgRocVaaS1NWx4JqGd+0jR+t8vDCDpB9BZTAOyp0p/aHxHdgiXwHBuEijzvnCe6PRwmd6ouh7kx5tSYIkxInYZVF1PWDOC43+1GbehH cloud@eucalyptus ccnet={privateIp=172.19.1.3 publicIp=10.12.10.231 privateMac=D0:0D:59:5C:0A:8A vlan=10 networkIndex=3} ccvm={cores=1 mem=256 disk=5} ncHostIdx=0 serviceTag=http://10.12.10.102:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] refresh_instances(): done
[Wed Feb 23 11:58:00 2011][025844][EUCADEBUG ] monitor_thread(): done
cloud@uec01:/var/log/eucalyptus$

**/var/log/eucalyptus/registration.log:**

2011-02-23 10:54:23-08:00 | 21572 -> Calling storage cluster1 storage 10.12.10.100
2011-02-23 10:54:23-08:00 | 21573 -> Calling walrus Walrus 10.12.10.100
2011-02-23 10:54:23-08:00 | 21571 -> Calling cluster cluster1 10.12.10.100
2011-02-23 10:54:23-08:00 | 21571 -> Cluster cluster1 is already registered.
2011-02-23 10:54:23-08:00 | 21572 -> SC for cluster1 is already registered.
2011-02-23 10:54:23-08:00 | 21573 -> Walrus 10.12.10.100 is already registered.
2011-02-23 11:02:11-08:00 | 25854 -> Calling storage cluster1 storage 10.12.10.100
2011-02-23 11:02:11-08:00 | 25857 -> Calling node cluster1 node 10.12.10.102
2011-02-23 11:02:11-08:00 | 25856 -> Calling walrus Walrus 10.12.10.100
2011-02-23 11:02:11-08:00 | 25858 -> Calling node cluster1 node #2 10.12.10.104
2011-02-23 11:02:11-08:00 | 25855 -> Calling cluster cluster1 10.12.10.100
2011-02-23 11:02:11-08:00 | 25857 -> Node 10.12.10.102 is already registered.
2011-02-23 11:02:11-08:00 | 25855 -> Cluster cluster1 is already registered.
2011-02-23 11:02:11-08:00 | 25854 -> SC for cluster1 is already registered.
2011-02-23 11:02:11-08:00 | 25856 -> Walrus 10.12.10.100 is already registered.
2011-02-23 11:02:11-08:00 | 25858 -> euca_conf --register-nodes returned FAILURE (error 1): Command attempted was /usr/sbin/euca_conf --no-rsync --skip-scp-hostcheck --register-nodes 10.12.10.104, and had the following output: 
INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.


Trying scp to sync keys to: eucalyptus@10.12.10.104://var/lib/eucalyptus/keys/...
failed.

ERROR: could not synchronize keys with 10.12.10.104!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node 10.12.10.104:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCS5h6VJMUL3Q/aLEstit9nDumPP+XLFlSaShKUXjHcZ+IH2zJ9sSSaxjA+pH4tQEWLD76VId8QLvKTc4yn2u1+IQhoPQcUeMCKqQq4FDSkDVtjfDir1DPKqt1uCMFFZYgQ3R9rnlIGElYnCz45jIprKV2QV3W53bxCeH+Q4jL8a1j4fGSC2tHAgsQFPIXtmcMppJry2NICtMamFUV1Zh+hzpfZNdEyYkB0xwHccsd/y9yagOwl98jxlwh4pQscXuDVbnk9UGK5VYENrd8G0sByO64c+T04XFouuRwaUQL4CO8nkPP8S0y25lzMq36yytN5HfKfdaztUnuniL3deHgb eucalyptus@uec01
EOT

Be sure that authorized_keys is not group/world readable or writable


I intentionally stopped eucalyptus-nc on 10.12.10.104 to help simplify my troubleshooting.  So that error should be okay.


Thanks again.

---

### Post by nbartolome on 2011-02-23
and a snippet from nc.log on my NC (10.12.10.102)

[Wed Feb 23 16:20:15 2011][005684][EUCADEBUG ] doDescribeResource() invoked
[Wed Feb 23 16:20:15 2011][005684][EUCADEBUG ] doDescribeInstances() invoked
[Wed Feb 23 16:20:15 2011][005684][EUCADEBUG ] doDescribeInstances(): instanceId=i-354705E8 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:35:47:05:E8 vlan=10 networkIndex=2 
[Wed Feb 23 16:20:21 2011][005684][EUCADEBUG ] doDescribeResource() invoked
[Wed Feb 23 16:20:21 2011][005684][EUCADEBUG ] doDescribeInstances() invoked
[Wed Feb 23 16:20:21 2011][005684][EUCADEBUG ] doDescribeInstances(): instanceId=i-354705E8 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:35:47:05:E8 vlan=10 networkIndex=2 
[Wed Feb 23 16:20:27 2011][005684][EUCADEBUG ] doDescribeResource() invoked
[Wed Feb 23 16:20:27 2011][005684][EUCADEBUG ] doDescribeInstances() invoked
[Wed Feb 23 16:20:27 2011][005684][EUCADEBUG ] doDescribeInstances(): instanceId=i-354705E8 publicIp=0.0.0.0 privateIp=172.19.1.2 mac=D0:0D:35:47:05:E8 vlan=10 networkIndex=2 

I suspect it has something to do with my networking, but just not sure what.

---

### Post by raymdt on 2011-02-24
hi nbartolome,
i suppose that you
- have activate the "VT-Extension" in Bios
- that you use kvm as hypervisor
- that you use an "unused ip-range" for your public addresses and an "unused** network**" for private addresses
- You are not running a firewall on the CLC

> 
[Wed Feb 23 16:20:15 2011][005684][EUCADEBUG ] doDescribeInstances():  instanceId=i-354705E8** publicIp=0.0.0.0** privateIp=172.19.1.2  mac=D0:0D:35:47:05:E8 vlan=10 networkIndex=2 
There is some problem with your public addresses

can you please post  the content of /etc/eucalyptus/eucalyptus.local.con   /etc/eucalyptus/eucalyptus.conf

---

### Post by nbartolome on 2011-02-24
Hi raymdt.   Thanks for the response.  I really appreciate it.

> **raymdt said:**
> hi nbartolome,
i suppose that you
- have activate the "VT-Extension" in Bios
- that you use kvm as hypervisor
- that you use an "unused ip-range" for your public addresses and an "unused** network**" for private addresses
- You are not running a firewall on the CLC


I'll have to double-check the VT-Extension thing, but I am able to successfully run the Maverick image on my NC outside of the cloud.  I followed the instructions here: [https://help.ubuntu.com/community/UEC/Images](https://help.ubuntu.com/community/UEC/Images)

KVM is indeed the hypervisor.  I tried to use XEN and eucalyptus-nc failed to start.

The IP range is unused.   I'm using 10.12.10.230 - 10.12.10.250 for the cloud.   My CLC uses 10.12.10.100 and the NC uses 10.12.10.102.

No firewall on the CLC that I know of.   I simply did an Ubuntu Enterprise Cloud installation from the 10.10 CD and followed the document here: [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

> 
can you please post  the content of /etc/eucalyptus/eucalyptus.local.con   /etc/eucalyptus/eucalyptus.confThe reason I suspect networking is because of the error that you pointed out and that my instances aren't able to receive any metadata.   From what I've been reading it should gather the metadata from [http://169.254.169.254/](http://169.254.169.254/)....    I do see that address on my CLC, but my NC isn't able to contact that address.

Here are the eucalyptus.conf and eucalyptus.local.conf files from my CLC and NC:

**From the CLC:**

cloud@uec01:/etc/eucalyptus$ **cat eucalyptus.conf **
# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth1"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################

cloud@uec01:/etc/eucalyptus$ **cat eucalyptus.local.conf**
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="209.242.128.100"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="10.12.10.230-10.12.10.250"


[B]From the NC:
[/B]
cloud@uec02:/etc/eucalyptus$ **cat eucalyptus.conf **
# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
#VNET_PUBINTERFACE="eth0"
#VNET_PRIVINTERFACE="eth0"
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
DISABLE_TUNNELLING="N"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################



cloud@uec02:/etc/eucalyptus$ **cat eucalyptus.local.conf **
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).

---

### Post by raymdt on 2011-02-24
Hi and thanks your efforts.

> 
but I am able to successfully run the Maverick image on my NC outside of the cloud


kvm without VT just runs QEMU. Please check the VT in Bios and run **kvm-ok** on NC.

Sometime it is easier to reinstall eucalyptus(it takes just 2 hours).

---

### Post by nbartolome on 2011-02-24
> **raymdt said:**
> Hi and thanks your efforts.



kvm without VT just runs QEMU. Please check the VT in Bios and run **kvm-ok** on NC.

Sometime it is easier to reinstall eucalyptus(it takes just 2 hours).


I double checked the bios and verified that Virtualization is enabled.   

kvm-ok looks okay.

cloud@uec02:/etc/eucalyptus$ sudo kvm-ok
INFO: Your CPU supports KVM extensions
INFO: /dev/kvm exists
KVM acceleration can be used

I have re-installed multiple times.   I'm actually in the process of re-installing again.

---

### Post by nbartolome on 2011-02-28
Okay, so I got my UEC on Ubuntu 10.10 to work.   In my  previous setup my CLC and NC were physically connected to a Cisco 3548  with multiple VLANs and a somewhat "secure" setup in that it requires us  to set up static routes in order for all the other VLANs to pass  traffic to one another.   Even though I setup static routes for  172.19.0.0 and 169.254.169.254 to be able to communicate to the CLC and  NC i was still receiving this error.

 So I moved the CLC and NC to a "dumb" switch without any VLANs  (similar to a cheesy Netgear 5 port switch) and re-installed.   The  result is that I have a working cloud and can successfully log in to  instances, run apache webserver on them and access web pages from my  desktop.

 Here are a few interesting things that I've discovered:
 
[LIST]
[*]Even though UEC assigns a 172.19.1.2, 172.19.1.3, etc..   address  you  will not ever see it on the CLC or the NC.   The only place that I  have  found it is on the actual instance.    It looks like the NC i  brings  up a 'vnetX" interface and you can confirm the mac address with  the one  being used in your instance.
[*]I am not administering my cloud via the command line on the CLC.   I am using the hybridfox plugin for firefox.
[*]I am not launching my instances as the default 'admin' user.    Instead I  created a different user through the web interface and gave it   Administrator privileges.
[*]Although this new user has Admin privileges I cannot download  images from the store because I get a "**bad request signature**" error.    So in order to download an image from the store I have to login as the  "admin" user.
[*]The only image I can get successfully to run is Lucid (amd64).    Both Karmic (AMD 64) from the store nor Maverick downloaded from  uec-images.ubuntu.com will run.   They just stay in "pending" state  until they terminate themselves.
[*]I sometimes receive this error on the instance console: "**consuming  user data failed!**"   Apparently this is a bug with the image that has  been fixed but hasn't been pushed out to the store yet ?  [http://open.eucalyptus.com/forum/possible-bug-walrus-20](http://open.eucalyptus.com/forum/possible-bug-walrus-20)  .   Suggestions say to just keep trying to launch and it'll eventually  run successfully.   I have confirmed this and after the 4th or 5th time  will finally get the instance to boot up successfully.
[/LIST]
  I bet I could have gotten it to work on my Cisco switch.   The switch  ports probably just need to be set to Operational mode multi or  something like that.

 I hope this can help any other people that have been working through the bugs.

---

### Post by kim0 on 2011-03-01
I believe UEC requires a vlan clean switch. I'm copying this from a whitepaper

"you will also need to verify that yournetwork is “VLAN-clean”, that is, it passes Ethernet frame with VLAN tag intact. Managed switches will often be configured to strip the VLAN tag on frame it pass through, or to drop these frames entirely. As security groups is implemented in Eucalyptus using special VLAN interface,you will need to configure your switches to pass Ethernet frames between the Node Controllerand the front-end as-is."

---

### Post by nbartolome on 2011-03-01
Yeah that's what made me suspect the network setup because when I went to test VLAN clean my machines would hang and become unresponsive.

[http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0](http://open.eucalyptus.com/wiki/EucalyptusNetworkConfiguration_v2.0)

However I thought it was only for MANAGED mode and by default it installs as MANAGED-NOVLAN. I also tried to use  STATIC and SYSTEM but those were also unsuccessful.

[B][FONT=Arial Black]Note that in MANAGED mode the underlying physical network must be   VLAN clean, as Eucalyptus provides and manages its own VLAN   tagging. If your network is not VLAN clean, you can use   MANAGED-NOVLAN mode, which provides the full set of networking   features, with the exception of VM isolation between   instances.
In the remaining networking modes, SYSTEM and STATIC, there   are no virtual subnets—VM instances appear on the physical   network as if they were physical machines; and VM instances are   directly bridged with the NC machine's physical ethernet device.   [/FONT][/B]

---

### Post by rabinnh on 2011-03-16
I am having the identical problem, but I am running in SYSTEM mode. One image instance hangs on "Waiting for EC2 meta-data" and the other gives me this:

Begin: Running /scripts/init-bottom ...
Done.
[    3.984801] EXT3 FS on sda1, internal journal
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
sleeping 1
Could not find data source
Failed to get instance datainit: cloud-init main process (620) terminated with status 1
mountall: Event failed
 * Starting AppArmor profiles                                                   Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
                                                                         [ OK ]
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'
Traceback (most recent call last):
  File "/usr/bin/cloud-init-cfg", line 56, in <module>
    main()
  File "/usr/bin/cloud-init-cfg", line 43, in main
    cc = cloudinit.CloudConfig.CloudConfig(cfg_path)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 42, in __init__
    self.cfg = self.get_config_obj(cfgfile)
  File "/usr/lib/python2.6/dist-packages/cloudinit/CloudConfig.py", line 53, in get_config_obj
    f=file(cfgfile)
IOError: [Errno 2] No such file or directory: '/var/lib/cloud/data/cloud-config.txt'


Since the errors are different, is it really probable that it is a switch stripping vlan tags?  Especially since I am running in SYSTEM mode.

---

### Post by kim0 on 2011-03-17
My advice would be not to run in SYSTEM mode, since that does not get enough testing. Keep the default networking mode

---

### Post by rabinnh on 2011-03-17
I started in MANAGED-NOVLAN mode and all the instances stayed in PENDING.  I can't really understand why there is documentation for things that (at least you are saying) don't work.

I have seen this reply on these forums quite a bit, so I'd like some clarification.  Do you work for Canonical?  I'm just curious how you know about the test plan and test matrix.

Thanks

---

### Post by kim0 on 2011-03-18
Hi, I'm not saying it doesn't work, I'm just saying other networking modes are not getting enough testing, thus are most likely to be buggy. The advice is to stick to the default networking mode. Yes I work for canonical, although that's irrelevant. I got this information from the Ubuntu server team on irc on #ubuntu-cloud you could join there and will probably get the same info

---

### Post by rabinnh on 2011-03-18
I went back to 10.04 and Eucalyptus 1.6.2 and had everything up and working in about an hour.  I spent 4 days trying to get 10.10 to work on the same hardware.

I think some (but not all) of the problems are caused by the images in the Store.  If they are to remain in the Store for 10.10 then someone should ensure that they work properly.  I don't think that people are going to attempt to bundle their own images when they can't get images that are blessed by Ubuntu to work based on the posts that I have been reviewing.

I see that Ubuntu is going to support OpenStack in 11.04.  I say, "good move".  Eucalyptus is not up to your standards in terms of documentation, robustness, and testing.  I don't think that UEC can be fixed by Canonical because the quality of Eucalyptus is questionable.  It's a great idea, but it doesn't seem to have gone through a professional level of review, testing, and debugging before release.

Regards

---

### Post by kim0 on 2011-03-21
Both openstack and eucalyptus will-be/are packaged for natty .. Joy :)

---

### Post by JasonN on 2011-05-05
Hello All,

I hope you guys don't mind that I'm bumping an old thread, but I am having practically the same issue and I made a small 'discovery' that perhaps may shed some light on the issue.  Perhaps it can go to benefit future users (and future me?).

**Setup**

I'm running a multi-cluster, Eucalyptus 2.0.2 setup (on Natty) with 2 CCs and 1 NC to each cluster. The CLC runs on the same network as one of the clusters while the other cluster is in a different domain.  The cloud runs with the default 'managed no-vlan' settings.

**Issue**

Each time I run an instance, it gets to a 'running' state which is neither pingable (outside the CC) or ssh-able (from anywhere).  The console output shows the 'sleeping 1' or 'url error [timed out]' items followed by a traceback of the most recent calls.  Checking the NC logs, I see that the instance fails to acquire the proper public IP address when 'doDescribeInstances()' is invoked even though Hybridfox, CLC, CC all show the public IP being attached to the instance in question.

**Discovery?**

I opted to run TCPDump to try and determine where the communication may have been breaking down.  After running it on both NC and CC, I started an instance and tried to ssh into the VM.  Then, surprisingly, it went through and I was able to log into the VM. I then turned off the TCPDump and the connection to the VM was dropped.  I started/stopped TCPDump again and found that the connection to the VM is possible when it's running on the CC.
[B]
One last note.[/B]

My colleague mentioned that this most likely occurs because the interface is put into 'promiscuous' mode when TCPDump is run (hence having to sudo tcpdump). 

[B]Any ideas?
[/B]
Anyone have any idea what might be going on?


Thanks always,
Jason :)

---

### Post by rabinnh on 2011-05-05
I'm pretty sure that I had a different problem.  My instances were definitely hing.

In your case, instead of tcpdump, go to the CC and just enter:

"sudo iptables -P FORWARD ACCEPT"

I'll bet that you iptables on the CC is not port forwarding, and that when you run tcpdump you are picking up the frames in promiscuous mode.

---

