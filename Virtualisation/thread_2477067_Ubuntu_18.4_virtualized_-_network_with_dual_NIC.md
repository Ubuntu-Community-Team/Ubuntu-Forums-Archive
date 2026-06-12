---
title: "Ubuntu 18.4 virtualized - network with dual NIC"
date: 2022-07-13
forum: Virtualisation
---

### Post by sprintership on 2022-07-13
By default with either DHCOP or Static dual NIC does not work. I am pretty sure its static route issue on Ubuntu. When I set up Centos or Windows and both NIC enabled all is fine.

I am sure I am missing something here.

NIC1 10.2.1.220/24 GW 10.2.1.1 DNS 8.8.8.8 

NIC2 192.168.1.220 GW 192.168.1.1 DNS 8.8.8.8 

Only one NIC works at the time.

---

### Post by TheFu on 2022-07-13
Which hypervisor is being used?
How are the NICs presented to the guest OS?  
Please post the netplan.yaml files which are controlling the networks.

BTW, support for 18.04 will end in April, so it would be smart to do any new install with at least 20.04 at this point.  Any project has had 2 yrs to move to 20.04 and if they haven't yet, it is a dead project which should be avoided.
If you like the bleeding edge, the next LTS after 20.04 is 22.04. There are some issues with it which some people would consider show-stoppers, but only you can decide.  Regardless, please read the release notes both for the specific release chosen AND for any DE/Desktop release if you are using a desktop version.

---

