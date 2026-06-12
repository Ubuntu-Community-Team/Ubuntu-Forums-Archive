---
title: "Configuring iptables to allow VNC and OpenVPN"
date: 2010-06-20
forum: Security
---

### Post by hierophant on 2010-06-20
I'm new to Linux, and would appreciate some help configuring iptables using Shorewall.  I'm running Ubuntu 10.04 LTS as a VM in Hyper-V, and accessing it via VNC with a machine in the same broadcast domain.  I'm using OpenVPN to connect to XeroBank.  I have instructions for configuring iptables to permit establishing and using the XeroBank connection, while blocking all other traffic on eth0. I've followed them successfully.  I need to also permit the VNC connection, and haven't managed that.  FWIW, the VM is at 192.168.111.12::5900 and the workstation is 192.168.111.2.

The attachment to this post lists the recommended contents for each Shorewall file.  Which files need changed, and what do I add to each?  Alternatively, please recommend a good Shorewall manual, or a relevant howto.  Thanks.

---

### Post by HermanAB on 2010-06-20
Hmm, please note that VNC is a very popular way to get your machine hacked.  These forums are full of tales of woe of tearful ex VNC users.

All the grey beards will concur that the best way to remote control a machine is via the Secure Shell. For example:
$ ssh -X -C -c blowfish user@serveripaddress gnome-panel

That even works from Windows, if you install Cygwin, or Xming and Putty.

---

### Post by hierophant on 2010-06-21
Thanks for your reply, HermanAB.

I did see the warnings re VNC in the Ubuntu Security sticky.  However, I assumed that they don't apply in my situation.  I do get that this may be a classic fail -- and I'd appreciate confirmation.

The Ubuntu VM and VNC client PC are both on 192.168.111.*, behind a Watchguard Firebox x5 (which is the DHCP server).  I'm the only admin/user (AFAIK) of all other machines on that domain.  No ports are forwarded through the Firebox (confirmed by external nmap scan) and there is no wireless access.  All IPs are hard coded, and reserved by MAC, and no non-reserved IPs are available.

Given that, do I still need SSH?

---

### Post by HermanAB on 2010-06-22
If the firewall has Plug and Pray disabled, then you should be fine.

---

