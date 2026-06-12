---
title: "Deploy Cluster/Node Controller on ubuntu 9.10 server on single physical system"
date: 2010-03-17
forum: Server Platforms
---

### Post by Richaa on 2010-03-17
Hi,

I have installed Ubuntu 9.10 server (Karmic Kola) on HP server successfully using the following link [https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html). I have installed eucalyptus packages but when I am trying to register the Node, following error is coming "**you need to be on CC and CC needs to be running**". **[COLOR=Blue]I need a help in deploying eucalyptus-cc/eucalyptus-NC on single physical system, is it possible or not? If yes, how can it be done?[/COLOR]**:confused:

Will appreciate your help.:)

Thanks in advance.
Richa

---

### Post by kiranmurari on 2010-03-17
Hi,

It is possible to run both CC and NC on one physical machine.
Please check if the Eucalyptus CC services are running or not.

For CC, following services should be running:
```
$ sudo service eucalyptus status
$ sudo service eucalyptus-cc status
$ sudo service eucalyptus-cloud status
```If CC is not running, issue the following command:
```
$ sudo service eucalyptus start
$ sudo service eucalyptus-cc start
$ sudo service eucalyptus-cloud start
```For NC, following service should be running:
```
$ sudo service eucalyptus-nc status
```If NC is not running, issue the following command:
```
$ sudo service eucalyptus-nc start
```Now in order to register the NC, you need to issue the following command:
```
$ sudo euca_conf --no-rsync --discover-nodes
```If the NC is discovered, it should prompt if the node has to be added:
> New node found on A.B.C.D; add it? [Yn]If it still gives error, please check log files for any possible errors. The files are /var/log/eucalyptus/cc.log,
 /var/log/eucalyptus/cloud-*.log for CC specific logs and /var/log/eucalyptus/nc.log
 for NC specific logs.

Hope this helps.

Regards,
Kiran

---

### Post by Richaa on 2010-03-18
Thank you for replying.

I tried this with no luck :(

[COLOR=Red]**Also I am getting the error in /var/log/eucalyptus/euca_test_nc.log "libvirt error unable to connect to '/var/run/libvirt/libvirt-sock': No such file or directory (code=38)**[/COLOR] 

Please advice

---

### Post by kiranmurari on 2010-03-23
Hi,

I was able to get both CC and NC working on a single machine. Please see the below link for details.
[http://kiranmurari.wordpress.com/2010/03/19/22/](http://kiranmurari.wordpress.com/2010/03/19/22/)

---

