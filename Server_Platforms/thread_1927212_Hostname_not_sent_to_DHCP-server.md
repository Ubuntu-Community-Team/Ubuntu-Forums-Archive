---
title: "Hostname not sent to DHCP-server"
date: 2012-02-17
forum: Server Platforms
---

### Post by lando99 on 2012-02-17
Hi!

I'm running an Ubuntu 11.10-server in my local network. It's connected to a FritzBox7290-router.
Unfortunately the server's hostname is not sent to the DHCP. It shows up as "PC_192-168-178-25" in the FritzBox control panel.
Here's my configuration:

**/etc/hostname** contains the string "lando"

**/etc/dhcp/dhclient.conf**
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "lando";

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers,
        dhcp6.domain-search, dhcp6.fqdn,
        dhcp6.name-servers, dhcp6.sntp-servers;

```

Then I tried to restart the hostname service:
```
root@lando:~# service hostname start
hostname stop/waiting
root@lando:~# dhclient3 eth0
RTNETLINK answers: File exists
root@lando:~#

```
I even rebooted the server, but the hostname is not sent.
Any hints?
Thanks

---

### Post by papibe on 2012-02-17
A few questions:

What is the version of your dhcp client? Could you post the result of these?
```
apt-cache policy dhcp3-client
```
The default directory for the configuration files is /etc/dhcp3  Did you change it?

The default configuration file works fine, and it comes with a line like this:
```
...
send host-name "<hostname>";
...
```
Did you edit the file?

Regards.

---

### Post by Leppie on 2012-02-18
what is the host alias defined in /etc/hosts?

---

### Post by lando99 on 2012-02-18
After fiddling abound with the settings and rebooting the server several times, the problem seems to have disappeared. I don't know why, I don't know how. But thank you anyway.
For the sake of completeness:

> dhcp3-client:
  Installed: (none)
  Candidate: 4.1.1-P1-17ubuntu10.1
  Version table:
     4.1.1-P1-17ubuntu10.1 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) oneiric-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/universe amd64 Packages
     4.1.1-P1-17ubuntu10 0
        500 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) oneiric/universe amd64 Packages


> root@lando:~# cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       lando

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


---

### Post by Leppie on 2012-02-18
I suspect it's just your Fritzbox updating the hosts list much later.
A similar thing happens to me on a Thomson router. It sometimes takes over an hour to correctly display new hostnames.

---

