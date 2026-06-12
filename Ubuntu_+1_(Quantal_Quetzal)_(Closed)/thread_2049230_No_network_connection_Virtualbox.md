---
title: "No network connection Virtualbox"
date: 2012-08-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Jaydrury1992 on 2012-08-28
Hi,

I'm running 12.10 but run a Windows XP VM through Virtualbox and it all worked perfectly until last week, the VM opens correctly and functions properly but the only issue is the network connection as it says its connected but can't see any network drives or load any web pages. I haven't made any changes to the VM but I have installed updates on Ubuntu and i'm wondering if this has caused the issue?
I am willing to supply more information if needed

Thanks

---

### Post by Jaydrury1992 on 2012-08-28
It only seems to have broken the NAT through Virtualbox, I have got it working through the Bridged Adapter option

---

### Post by jfernyhough on 2012-08-28
This will be down to a change in network manager's copy of dnsmasq changing the local DNS server from 127.0.0.1 to 127.0.1.1

I've been running another dnsmasq to listen on 127.0.0.1 and cache responses. I had to edit /etc/dnsmasq.d/network-manager and comment out except-interface=lo. If you don't have dnsmasq installed then the steps would be:

$ sudo apt-get install dnsmasq
$ sudo nano /etc/dnsmasq.d/network-manager <- comment out except-interface=lo
$ sudo nano /etc/dnsmasq.conf <- edit to your liking, e.g. change cache size from 150 to 1000.
$ sudo service dnsmasq restart

---

### Post by evilalive on 2012-10-09
Just came across this problem myself.

jfernyhough, thanks for you instructions. I installed dnsmasq but then I couldn't find anything recognisable in the configuration files you mention. However, upon trying my virtual machine again, it works!

So in summary, for me at least, installing dnsmasq was enough to fix the problem.

---

### Post by fjgaude on 2012-10-09
Installing dnsmasq didn't fix the issue with me, sorry to say!

---

### Post by wgarcia on 2012-10-09
I noticed this problem myself in all my virtualbox machines. Changing from NAT to Bridge Adapter in the virtual machine network configuration seems to solve it, at least for me.

---

### Post by fjgaude on 2012-10-09
> **wgarcia said:**
> I noticed this problem myself in all my virtualbox machines. Changing from NAT to Bridge Adapter in the virtual machine network configuration seems to solve it, at least for me.

Okay, will give it a try! Thanks!

LATER: Didn't work, ah, well!

---

### Post by NZjelle on 2012-10-09
> **Jaydrury1992 said:**
> Hi,

I'm running 12.10 but run a Windows XP VM through Virtualbox and it all worked perfectly until last week, the VM opens correctly and functions properly but the only issue is the network connection as it says its connected but can't see any network drives or load any web pages. I haven't made any changes to the VM but I have installed updates on Ubuntu and i'm wondering if this has caused the issue?
I am willing to supply more information if needed

Thanks

Perhaps it's the same problem with the same solution as below:
Re: Ubuntu 12.10 Beta 1: VBox RC4 NAT not working  Postby pwzhangz » 15. Sep 2012, 23:45
trekfan1 wrote:Navigation from the GUEST is not working, browser responding: impossible to connect etc., 
Open a terminal and try this:
VBoxManage modifyvm "VMNamexxx" --natdnshostresolver1 on 
VMNamexxx is the name of your VM machine.    pwzhangz

---

### Post by Cecil on 2012-10-10
> **jfernyhough said:**
> This will be down to a change in network manager's copy of dnsmasq changing the local DNS server from 127.0.0.1 to 127.0.1.1

I've been running another dnsmasq to listen on 127.0.0.1 and cache responses. I had to edit /etc/dnsmasq.d/network-manager and comment out except-interface=lo. If you don't have dnsmasq installed then the steps would be:

$ sudo apt-get install dnsmasq
$ sudo nano /etc/dnsmasq.d/network-manager <- comment out except-interface=lo
$ sudo nano /etc/dnsmasq.conf <- edit to your liking, e.g. change cache size from 150 to 1000.
$ sudo service dnsmasq restart
Thanks for this, I've been pulling my hair out trying to figure out why my WinXP VM wasn't able to access webpages, despite apparently having a connection. I only had to install dnsmasq, none of the other steps were necessary. For those still trying to get it to work, I wish you luck, I know how annoying it is when things don't work correctly.

---

