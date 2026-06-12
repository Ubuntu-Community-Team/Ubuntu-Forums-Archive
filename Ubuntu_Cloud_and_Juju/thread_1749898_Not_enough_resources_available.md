---
title: "Not enough resources available"
date: 2011-05-05
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-05
cloud@node:~$ cd /home/cloud/.euca
[email]cloud@node:~/.euca[/email]$ . eucarc
[email]cloud@node:~/.euca[/email]$ euca-describe-a
euca-describe-addresses           euca-describe-availability-zones
[email]cloud@node:~/.euca[/email]$ euca-describe-availability-zones verbose
AVAILABILITYZONE    cluster1    10.1.1.222
AVAILABILITYZONE    |- vm types    free / max   cpu   ram  disk
AVAILABILITYZONE    |- m1.small    0002 / 0002   1    192     2
AVAILABILITYZONE    |- c1.medium    0002 / 0002   1    256     5
AVAILABILITYZONE    |- m1.large    0001 / 0001   2    512    10
AVAILABILITYZONE    |- m1.xlarge    0001 / 0001   2   1024    20
AVAILABILITYZONE    |- c1.xlarge    0000 / 0000   4   2048    20
[email]cloud@node:~/.euca[/email]$ euca-describe-images
IMAGE    eki-6E341ABC    lucid-20110421182259/lucid-server-uec-i386-vmlinuz-virtual.manifest.xml    admin    available    public        i386    kernel        
IMAGE    emi-210F15BA    lucid-20110421182259/lucid-server-uec-i386.img.manifest.xml    admin    available    public        i386    machine    eki-6E341ABC    
[email]cloud@node:~/.euca[/email]$ euca-run-instances emi-210F15BA -k mykey -t m1.large 
FinishedVerify: Not enough resources available: addresses (try --addressing private)

---

### Post by kim0 on 2011-05-06
Hi,
I think it's unable to allocate an IP for your instance. Try running with the option ( --addressing private) and it should work. Then please check your network configuration. Here's the manual

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

