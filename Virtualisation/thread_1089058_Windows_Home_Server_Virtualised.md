---
title: "Windows Home Server Virtualised"
date: 2009-03-06
forum: Virtualisation
---

### Post by silentbob1978 on 2009-03-06
Hello All

I am very new to all this stuff but I am determined to learn.

Anyways to the issue I have.....

I have Ubuntu Server 64bit installed (latest version) and I have vmware server 2 installed on top.

I have created 2 virtual machines and I am having some network speed issues.  If I transfer files to the VM's one of which is WHS my network speed is approx 7/8 MB/second.  I have a gigabit network and never had any issue before with speed.  

Is there anything you may think I have missed when installing ubuntu/vmware server as the speeds I am getting are awful.

---

### Post by HermanAB on 2009-03-07
There is a difference in efficiency with VMware's different network interface topologies.  I believe that Host networking is fastest and NAT is slowest.  I usually use Bridged mode.  So I guess that you are using NAT mode.

Cheers,

Herman

---

### Post by veloce on 2009-03-08
> **HermanAB said:**
> There is a difference in efficiency with VMware's different network interface topologies.  I believe that Host networking is fastest and NAT is slowest.  I usually use Bridged mode.  So I guess that you are using NAT mode.

Cheers,

Herman

There was an issue with speed when transferring between the host and vm using bridged networking but I thought it had been fixed with vmware server 2.

I now put in two virtual network cards one bridged and one host only.  Communication btw host and vm is done on the host network.

---

