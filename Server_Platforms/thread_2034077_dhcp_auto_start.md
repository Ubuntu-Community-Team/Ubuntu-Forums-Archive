---
title: "dhcp auto start?"
date: 2012-07-27
forum: Server Platforms
---

### Post by Roasted on 2012-07-27
I'm using a 12.04 server with the regular desktop version on it. It's running its own dhcp server as well. I just upgraded it fron 10.04 and everything went great. However I noticed dhcp doesn't seem to auto start. The systems (ltsp thin clients) don't get an IP unless I manually start the service. Does anybody know a way to get it to kick on automatically when the system fires up?

Thank you!

---

### Post by darkod on 2012-07-27
I am not sure if you need to investigate why it doesn't auto start as it should, or simply make it start on boot.

Usually you put commands you want to be executed on boot in /etc/rc.local

To start the dhcp daemon (service), it would be something like (I am not sure if the exact name is dhcp or dhcpd):
/etc/init.d/dhcp[COLOR=Red]d[/COLOR] start

Add that in /etc/rc.local before a line saying 'exit 0' if there is one. If not, simply add it to the end.

---

### Post by papibe on 2012-07-27
Hi Roasted.

What are you running as dhcp server? Is it dnsmasq, dhcp3-server or 	isc-dhcp-server?

Could you post the results of these commands?
```
more /etc/default/*dhcp*

grep -i dhcp /var/log/syslog

```
Regards.

---

### Post by Roasted on 2012-07-27
> **darkod said:**
> I am not sure if you need to investigate why it doesn't auto start as it should, or simply make it start on boot.

Usually you put commands you want to be executed on boot in /etc/rc.local

To start the dhcp daemon (service), it would be something like (I am not sure if the exact name is dhcp or dhcpd):
/etc/init.d/dhcp[COLOR=Red]d[/COLOR] start

Add that in /etc/rc.local before a line saying 'exit 0' if there is one. If not, simply add it to the end.

Good thought but those commands look old. Would they still be in use? sudo service isc-dhcp-server sounds more like it to me - no? It just struck me as odd that it didn't register it as an autostart job, but maybe that's a small side effect of the upgrade process?? Otherwise it worked great, no complaints.


> **papibe said:**
> Hi Roasted.

What are you running as dhcp server? Is it dnsmasq, dhcp3-server or 	isc-dhcp-server?

Could you post the results of these commands?
```
more /etc/default/*dhcp*

grep -i dhcp /var/log/syslog

```
Regards.

I won't have access to the server until next week so I won't be able to post any logs just yet. It's isc-dhcp-server. The server has two nics in use... one on a 10.52.17.0 network and the other on a 10.52.18.0 network. Each nic is plugged into its own 48 port switch where it serves ~40 clients per nic, potential of 80 under maximum load. Like I said its serving its own dhcp... just noticed it wasn't autostarting. Other than that if I manually run sudo service isc-dhcp-server start then the clients on ltsp work fine and pxe boot into their environment as expected.

---

### Post by Roasted on 2012-08-15
I'm also beginning to see a tftp error where it hangs the clients during boot, but if I restart the service (sudo service tftpd-hpa restart) it begins working fine. This only happens following a server reboot/power outage/etc. I talked to a few guys who were devs for various projects and said it sounds more like a bug if anything, because the difference between the system auto starting tftp and me restarting tftp is none, so if it fails during system start, yet works under manual restart, then it should be a bug. No idea otherwise.

Ironically, DHCP doesn't seem to be an issue anymore... clients seem to pull an IP and hang at the tftp screen. 

Just for fun... let's say DHCP is not auto starting and it SHOULD be. What would the remedy be? Likewise, can I set up a temporary work around, where I have the tftp service restart itself via script say 20 seconds after reboot?

---

### Post by Roasted on 2012-11-11
Been a few months now, but I heard today that while the server isn't rebooted frequently, once it is rebooted for whatever reason (most commonly power failure after the UPS's deplete... been a lot of storms and hurricanes lately) then they're finding they have to SSH in and manually get dhcp and tftp running.

As a quick band aid, I figured they could set some sort of a cron autostart job, but that's not really fixing the problem. I have *zero* idea why it's fouling up. It works perfectly when you manually initiate it, but it's a real pain to have to even do that. Any further ideas?

---

### Post by papibe on 2012-11-12
Check the syslog. It may be give you some clues:
```
grep dhcpd /var/log/syslog | less
```

Regards.

---

### Post by nomes on 2012-12-06
Hi, I was recently experiencing the same problem with tftpd-hpa service not restarting in ubuntu 12.04 and found a solution which involved the following instructions:

edit file : /etc/init/tftpd-hpa   and edit following lines:

start on runlevel [2345]

        TO:

start on (local-filesystems and net-device-up IFACE!=lo)

I really don't know the exact reason why this works, but it has something to do with tftpd-hpa coming up before the system has an ip address from its own dhcp server or router. Once you edit the file and reboot the server, tftpd-hpa should start with a process id....right now it probably start but without a process id.  I am sure others can explain why this works or is a good solution, im too much of a newbie to understand the inner working of "why" and "how".  hope it works for you?

---

