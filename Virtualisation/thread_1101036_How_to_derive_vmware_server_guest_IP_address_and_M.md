---
title: "How to derive vmware server guest IP address and MAC"
date: 2009-03-19
forum: Virtualisation
---

### Post by mperry on 2009-03-19
Hi all-

I'm building a demo environment using VMWare Server 1.0.8 on Ubuntu 8.10 server. I have built a basic web environment to launch, manage, and stop vmware guests. What I'd like to do is present a launched VMWare guest's IP address as part of a shell script output. This will help us launch the guest in a web session since the guests all run various and sundry web UIs.

Anyone know a way to use vmrun or other command line tools to extract the IP address from a running guest session without visiting that session and running the command line tools (ipconfig for windows, etc)? I'd like to write a PHP wrapper that would present this information on my webpage after I start a VM guest.

Thanks!

---

### Post by HermanAB on 2009-03-20
[http://www.vmware.com/pdf/vix160_vmrun_command.pdf](http://www.vmware.com/pdf/vix160_vmrun_command.pdf)

```
Run a program in a Linux virtual machine on VMware Server:
vmrun -T server -h https://10.0.1.8/sdk -u root -p <pass> -gu <user> -gp <userpass>
runProgramInGuest "[storage1] RHEL4/RHEL4.vmx" "/sbin/ifconfig eth0"
```

Hope that helps!

Herman

---

### Post by dcstar on 2009-03-22
> **mperry said:**
> Hi all-

I'm building a demo environment using VMWare Server 1.0.8 on Ubuntu 8.10 server. I have built a basic web environment to launch, manage, and stop vmware guests. What I'd like to do is present a launched VMWare guest's IP address as part of a shell script output. This will help us launch the guest in a web session since the guests all run various and sundry web UIs.

Anyone know a way to use vmrun or other command line tools to extract the IP address from a running guest session without visiting that session and running the command line tools (ipconfig for windows, etc)? I'd like to write a PHP wrapper that would present this information on my webpage after I start a VM guest.

Thanks!

The Guest IPs are not known to the host (AFAIK) if you are using bridge mode networking, you may have to get each guest to write a file with this info to a shared resource (like a Samba share) on startup.

It may be easier just assign static IPs to the guests and use those.

---

### Post by Dedoimedo on 2009-03-22
Run nmap against the vmnet subnet (192.168.x.x) and query os version and such ... then run arpwatch and check for mac/ip pairings?
Dedoimedo

---

