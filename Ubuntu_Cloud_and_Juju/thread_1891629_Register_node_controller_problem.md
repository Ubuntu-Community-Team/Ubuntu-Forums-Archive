---
title: "Register node controller problem"
date: 2011-12-06
forum: Ubuntu Cloud and Juju
---

### Post by logskish on 2011-12-06
Hi ,

      I was installing ubuntu enteprise cloud 11.04 and configuring Eucalyptus. I was trying to register node controller manually to the CC. My set up is with one router that is connected to 3 systems, where i have installed CLC,CC,SC,WS3 in one system & installed NC in another system (i have installed 11.04 UEC in Vmware VMplayer and bridged to my NIC).
 
I configured de router as static .. so that IP's of individual systems as follows
gateway : 192.168.0.1
CLC,WS3,SC,CC : 192.168.0.5
NC : 192.168.0.6

when i tried euca_conf --discover-nodes ====> it is able find the new node .. but it throws an error,

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization
trying rsync to sync keys with "fe80::20c:29ff:fe4f:ed44" .. ssh: could not resolve hostname fe80: Name or service not known
rsync: connection unexpectedlyy closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender 3.0.7] failed
trying scp to sync keys to eucalyptus@fe80::20c:29ff:fe4f:ed44://var/lib/eucalyptus/keys/...
lost connection failed

ERROR: could not synchronize keys with fe80::20c:29ff:fe4f:ed44
the configuration will not have this node
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::20c:29ff:fe4f:ed44
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAA.......... eucalytptus@192.168.0.5
......
...........

I actually synchronized the keys using the command from CLC to NC ..!
sudo -u eucalyptus ssh-copy-id -i ~eucalyptus/.ssh/id_rsa.pub eucalyptus@192.168.0.6

 I could not register my NC and at euca-describe-availability-zones verbose, i can only see 
AVAILABILITYZONE    serverCLC    192.168.0.5
AVAILABILITYZONE    |- vm types    free / max   cpu   ram  disk
AVAILABILITYZONE    |- m1.small    0000 / 0000   1    192     2
AVAILABILITYZONE    |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE    |- m1.large    0000 / 0000   2    512    10
AVAILABILITYZONE    |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE    |- c1.xlarge    0000 / 0000   4   2048    20

to access the internet i am using proxy, even wen i included NC's ip in no_proxy .. i could see the same error ! 

Please help me thro' this 

Thanks

---

