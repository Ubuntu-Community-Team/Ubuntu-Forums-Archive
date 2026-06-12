---
title: "vm instance cannot not be connected to internet"
date: 2011-05-06
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-05-06
I have setup a private cloud using two machines using uec 10.04. I can access the vm instances from the NC. The problem is i cannot connect the vm instance with internet because i have to install netbeans ide or java compiler on the vm install and get service from it. 

ubuntu@ip-172-19-1-2:~$ sudo apt-get install java-sdk
sudo: unable to resolve host ip-172-19-1-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package java-sdk is a virtual package provided by:
  openjdk-6-jdk 6b20-1.9.7-0ubuntu1~10.04.1
  gcj-4.4-jdk 4.4.3-1ubuntu4.1
  gcj-jdk 4:4.4.3-1ubuntu1
  default-jdk 1.6-34
You should explicitly select one to install.
E: Package java-sdk has no installation candidate


on  node controller (10.1.1.221)

[email]cloud@node:~/.euca[/email]$ euca-describe-instances 
RESERVATION    r-4A960A06    admin    default
INSTANCE    i-2E650646    emi-210F15BA    10.1.1.106    172.19.1.2    running    mykey    0        m1.xlarge    2011-05-06T04:41:56.514Z    cluster1    eki-6E341ABC    
[email]cloud@node:~/.euca[/email]$ 


Is there any solution to this problem?


The ultimate aim is to install netbeans or jdk on vm instances for which internet is needed to update the vm instances. I suddenly got an idea to copy the netbeans ide or jdk which is downloaded from internet in the node controller (nc) machine  to vm instance. Is it possible to copy the files from nc to vm instances? I do know because i am new to this environment. I first all tried to copy a small file from nc to vm instances using scp but couldn't.

---

### Post by kim0 on 2011-05-06
Hi,
Can you please try executing the 2 following commands on the CLC/CC node

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

I am assuming eth0, is the "outer" interface connecting to the internet. if it's not, change the name to the appropriate one.

---

### Post by viswacse02 on 2011-05-07
> **kim0 said:**
> Hi,
Can you please try executing the 2 following commands on the CLC/CC node

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

I am assuming eth0, is the "outer" interface connecting to the internet. if it's not, change the name to the appropriate one.


cloud@cloud:~$ sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
[sudo] password for cloud: 
cloud@cloud:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
cloud@cloud:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

---

