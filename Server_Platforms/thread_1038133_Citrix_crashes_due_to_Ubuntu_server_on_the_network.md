---
title: "Citrix crashes due to Ubuntu server on the network"
date: 2009-01-12
forum: Server Platforms
---

### Post by stefangr1 on 2009-01-12
I recently installed a simple home server, running Ubuntu (installed with the Ubuntu 8.04 x64 alternate cd). The other computers at home are now no longer connected trough the internet modem, but trough the server, with dhcp (dhcp3-server) + dns (bind9) + pxe server. A virtual server with some other applications runs on the same machine as a diskless client. The setup worked very smoothly, and (at first) I was very happy with it. 

Untill...  I discovered that the server crashes citrix running on a windows-xp pc, that exits with a "driver protocol error", with a "mean time to failure" of about one hour. As the new server is the only thing I changed recently, it seems it is the cause.

My dhcpd.conf script is very simple:

# /etc/dhcpd.conf

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
authorative;


# eth0 connects the server to the internet
subnet 192.168.1.0 netmask 255.255.255.0 {
}


# eth1
subnet 192.168.2.0 netmask 255.255.255.0 {
  option routers 192.168.2.1;
  option domain-name-servers 192.168.2.1;
  filename "ubuntu-alternate/pxelinux.0";
  next-server 192.168.2.1;

  host winxp {
    hardware ethernet ##:##:##:##:##:##:##;
    fixed-address 192.168.2.10;
    option host-name "winxp";
    }

  <other computers running different versions of Ubuntu>

  # Unknown clients get this pool.
  pool {
    range 192.168.2.20 192.168.2.30;
    allow unknown clients;
    }

# vmnet1
subnet 192.168.3.0 netmask 255.255.255.0 {
  option routers 192.168.3.1;
  option domain-name-servers 192.168.3.1;

  host ubuntu-x64-vm {
    hardware ethernet ##:##:##:##:##:##;
    fixed-address 192.168.3.10;
    option host-name "ubuntu-x64-vm";
    filename "ubuntu-nfs-vm/pxelinux.0";
    next-server 192.168.3.1;
    }

}


Then I have added some simple routing options:

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

And thats basically everything I did.

I would really appreciate a solution to this, since using citrix is quite important to me. Any suggestions?

---

