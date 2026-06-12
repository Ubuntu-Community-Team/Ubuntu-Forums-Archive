---
title: "Proper Configuration for virtual on win 10."
date: 2017-01-26
forum: Virtualisation
---

### Post by wlraider702 on 2017-01-26
Hi, 

I'm trying to setup ubunut 16.04 as guest OS on Win10 ent. I just want internet access and internal traffic. 
Everywhere I look there is different guide with different approaches I'm willing to start fresh, is there an authoritative guide on how to do this?

thanks

---

### Post by SeijiSensei on 2017-01-27
What are you using? VirtualBox?  Then the default installation should be fine.  It uses "network address translation" to enable the VM to see the network beyond the host machine, but does not allow connections from the outside back to the VM.  In essence the VM can only be a "client" and not a "server."

If by "internal traffic" you mean being able to connect to the VM from other machines on the network, you can configure VB in "bridged" mode.  Then it will get an address on the same network as the host.  That exposes the VM to potential mischief from other machines on your network.  You can make it more secure with two simple iptables rules.  Suppose your computer is on the 192.168.1.0/24 network with 192.168.1.1 as the address of your router.  Then you can enable all the other machines on your local network to see it while blocking outside connections through the router like this:

```

/sbin/iptables -A INPUT -s 192.168.1.1 -j REJECT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT

```

The first rule blocks inbound connections from the router, while the other permits connections from other machines on your local network.  If you add these lines to the file /etc/rc.local on the Ubuntu VM, they will be run automatically whenever the VM is booted.  You can edit that file with "sudo nano /etc/rc.local".  Use Ctrl+X and "Y" to save it when you're done.

---

### Post by wlraider702 on 2017-01-27
yes it is virtuabox. Enabling a bridged adapter fixed it. Thanks for the help.

---

