---
title: "Overriding resolvconf on gateway servers 12.04"
date: 2012-05-29
forum: Server Platforms
---

### Post by jlittle on 2012-05-29
Prior to 12.04 when using Ubuntu as a gateway server for LANs I would setup systems
  as router, firewall, DHCP server and private DNS server for LAN and caching. The WAN (red) eth0 interface DHCP from the ISP and LAN (green) eth1 is static 192.168.1.1. To setup my forwarders for DNS server I created a hook script in dhclient-enter-hooks.d that when eth0 goes up: 
   
  1. grabbed the ISP nameservers from $new_domain_name_servers 
  2. format and write nameservers to /var/cache/bind/ fowarders which is an include in named.conf.options
  3. reload bind to get forwarders config
  4. override make_resolv_conf() to set the resolv.conf with LANs domain and nameserver and not the ISP's since anything outside the LAN will be forwarded by local DNS server if not cached.
   
  This served me well until 12.04 with resolvconf. I can still get it to work because the hook writes directly to resolv.conf removing the symbolic link which effectively disables resolvconf. So my questions are is there any consequences to this approach? Should I just uninstall resolvconf? Is there a better way to do what I wish utilizing resolvconf? So far I have not figured out how to make it work with resolvconf. 

-- 

Jonathan

---

### Post by safa on 2012-09-05
Hi,

Am interested in detail about your configuration..
Would you be kindly to mention in detail.

Thanks,

Safa Al-Saki
[www.freewebs.com/tododigitalvzla](www.freewebs.com/tododigitalvzla)

---

### Post by jdthood on 2012-10-29
> **jlittle said:**
> Prior to 12.04 when using Ubuntu as a gateway server for LANs I would setup systems as router, firewall, DHCP server and private DNS server for LAN and caching. The WAN (red) eth0 interface DHCP from the ISP and LAN (green) eth1 is static 192.168.1.1. To setup my forwarders for DNS server I created a hook script in dhclient-enter-hooks.d that when eth0 goes up: 
   
  1. grabbed the ISP nameservers from $new_domain_name_servers 
  2. format and write nameservers to /var/cache/bind/ fowarders which is an include in named.conf.options
  3. reload bind to get forwarders config
  4. override make_resolv_conf() to set the resolv.conf with LANs domain and nameserver and not the ISP's since anything outside the LAN will be forwarded by local DNS server if not cached.
   
  This served me well until 12.04 with resolvconf. I can still get it to work because the hook writes directly to resolv.conf removing the symbolic link which effectively disables resolvconf.

This is probably the best solution for now. BIND9 is not yet properly integrated with resolvconf. See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483098](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483098) for background.

> So my questions are is there any consequences to this approach? Should I just uninstall resolvconf? Is there a better way to do what I wish utilizing resolvconf? So far I have not figured out how to make it work with resolvconf.

Because BIND9 is not properly integrated with resolvconf you have to do it yourself, as you have done.

Leave resolvconf installed. Its mere presence inhibits other programs from futzing with /etc/resolv.conf.

---

### Post by jdthood on 2013-01-05
@jlittle: If you are interested in being able to use bind9 with an automatically generated list of forwarders, please add your voice to this Ubuntu "wish" report:

    [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)

---

