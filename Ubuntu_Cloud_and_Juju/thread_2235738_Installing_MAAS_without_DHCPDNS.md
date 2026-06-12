---
title: "Installing MAAS without DHCP/DNS"
date: 2014-07-22
forum: Ubuntu Cloud and Juju
---

### Post by David_Grigglestone on 2014-07-22
I'm trying to install MAAS without DHCP/DNS .. seems like instructions at [http://maas.ubuntu.com/docs1.5/install.html#installing-maas-from-ubuntu-server-boot-media](http://maas.ubuntu.com/docs1.5/install.html#installing-maas-from-ubuntu-server-boot-media) are for 12.04 only.

Is my only option to use the MAAS install and then remove DHCP/DNS after?

Many thanks for your input

---

### Post by atifzia.81 on 2014-08-25
Everyone suggest to install and configure DHCP/DNS on MAAS controler because if you don’t let MAAS manage DHCP, then MAAS will not be able to allocate its static IP addresses to Nodes and that may cause the problem. If you don't want to use MAAS DHCP/DNS then you need follow the following

At the very least the “filename” option should be set to “pxelinux.0”.

 How to configure this depends on what software you use as a DHCP server.  If you are using the ISC DHCP server, for example, the configuration entry might look something like this:

 subnet 192.168.10.0 netmask 255.255.255.0 {
    filename "pxelinux.0";
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.10.255;
    option domain-name-servers 192.168.10.136;
    range dynamic-bootp 192.168.10.5 192.168.10.135;
}

---

