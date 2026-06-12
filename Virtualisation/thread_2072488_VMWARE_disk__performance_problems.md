---
title: "VMWARE disk  performance problems"
date: 2012-10-17
forum: Virtualisation
---

### Post by dazman19 on 2012-10-17
Hi there,

I have a bunch of debian VMs on a pretty grunty ESX host,

These servers are just webservers running mysql and apache/php.

The problem I have is one server always seems to get all the resources in regards to disk i/o. 

To be fair it is quite a heavy web application. (4 years of development and still going), For example host01 is the machine that is having long page loads etc. 
mailinator is essentially the same as host01, but its disk I/O is fine.

Both machines have the latest version of VMware tools on them. And they use the same physical datastore. 

Here are the test results.

daryl@mailinator:~$ sudo hdparm -t /dev/sda1
[sudo] password for daryl:
/dev/sda1:
 Timing buffered disk reads: 390 MB in  3.01 seconds = 129.60 MB/sec

daryl@host01:~$ sudo hdparm -t /dev/sda1
[sudo] password for daryl:

/dev/sda1:
 Timing buffered disk reads:  34 MB in  4.13 seconds =  8.23 MB/sec

For a web server this is pretty bad, it only really needs about 40MB/sec to be sufficent

Both of these machines spec is:
2vCPU
4096MB Ram

The only thing in VMware that i can find different is the guest os on the slow machine (host01) says Other 2.6.x Linux (64-bit)

The faster machine (mailinator) says Other (32bit) which is wrong as well, since both of these machines are debian squeeze 64bit. So any suggestions on what I can do?? 

They both got the same amount of shares for disk IO and the same priority as far as VSPHERE is concerned.

---

### Post by dcstar on 2012-10-18
> **dazman19 said:**
> 
The faster machine (mailinator) says Other (32bit) which is wrong as well, since both of these machines are debian squeeze 64bit. So any suggestions on what I can do?? 


[LIST=1]
[*]Are they using Independent Disks?
[*]Are they using the same Virtual Drivers?
[*]Are the VMs using the same filesystems?
[/LIST]

---

### Post by dazman19 on 2012-10-18
We have 8x146gb 15K SAS disks in an IBM x3650 server.

Same virtual drivers? I assume so, I dont understand this they are both using the latest version of vmware tools.  I would say they are using exactly the same drivers, as Host01 was a "Copy" of Mailinator's VMDK with its IP and a few other minor settings changed after we performed the copy.

Yep they must both be using ext journaling filesystems, because of the fact that the server that is performing badly is an exact copy of mailinator, i think all we changed were its hostname, IP address and i think we made a new VMX file when we deployed it.

This saved us loads of time because we have lots of apache extensions etc installed for our web app, and they have lots of settings.

---

