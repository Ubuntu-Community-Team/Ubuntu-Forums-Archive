---
title: "Static Network Addresses Changed This Morning?"
date: 2016-10-18
forum: Server Platforms
---

### Post by howard14 on 2016-10-18
Hi,

I am running 3 Ubuntu 14.04 LTS servers, and something weird happened this moring to all 3 servers within about 30 minutes. I lost connection to them all. After a little investigation, it appears that they changed all their static IP addresses?

I managed to get them to reset by running ifdown followed by ifup. But am curious as to why this happened, especially to all three servers.

Anyone have any ideas?

Thanks.

---

### Post by howard14 on 2016-10-18
OK - found some other articles which suggest that the DHCP client is overwriting the static ip address. How do I disable the dhcp client?

---

### Post by howard14 on 2016-10-18
Hello again. So the problem appears to have been the DHCP client retrieving a new address from the DHCP server - overwriting the static address. I do not appear to be able to remove the DHCP client, since this is a virtual service. So I have searched for any running DHCP client services using:

$ ps ax | grep dhcp

And then killed any resultant dhcp client services using

$ sudo kill *p*[I]id

[/I]Hopefully the DHCP client process will not restart when I reboot the server, if it does I will need a more permanent way to kill the dhcp client.

Hope this helps someone.

---

### Post by smurphy2 on 2016-10-18
can't you configure the /etc/network/interfaces file? If yes, put a static entry into these. Easier.
If you have root-access to the vm, remove the dhcp-client.

---

### Post by howard14 on 2016-10-18
Thanks smurphy2. I do have access to the interfaces file, that is where the static IP is set up. Unfortunately it appears that the DHCP client is, periodically, overriding the static IP address with a DHCP address. When I run ifdown/ifup, it restores the static ip as defined in the interfaces file. I cannot remove the dhcp-client (using apt-get remove dhcp-client tells me that this is a virtual service and cannot be removed). I have killed the DHCP client process as mentioned in my previous posts. Hopefully this process will not restart.

---

### Post by darkod on 2016-10-18
Hmmm, if that is correct that would be very serious bug or problem. I run quite a few servers for a friend and have never seen one server losing static IP... If you had a configuration of "dhcp with reservation" it could somehow maybe get another IP. But with a static setting, I have never seen it.

You don't have any type of GUI installed on the servers right? Because that usually installs NetworkManager and that makes server networking act unexpectedly.

---

