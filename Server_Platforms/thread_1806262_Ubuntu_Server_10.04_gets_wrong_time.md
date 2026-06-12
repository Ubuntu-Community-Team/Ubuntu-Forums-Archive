---
title: "Ubuntu Server 10.04 gets wrong time"
date: 2011-07-17
forum: Server Platforms
---

### Post by hunters1094 on 2011-07-17
hi

Yesterday, i installed Ubuntu on my 3 servers. I used the Ubuntu Server 10.04 64 bit. But the time of all server got wrong, although i chose right time zone. 

I tried like in this article:

[https://help.ubuntu.com/10.04/serverguide/C/NTP.html](https://help.ubuntu.com/10.04/serverguide/C/NTP.html)

But when i ran the command:

ntpdate ntp.ubuntu.com

The result said that no server to synchronize.

My network  connection was good. 

Thanks for any ideas.

---

### Post by Cheesehead on 2011-07-17
Please post the contents of your file: /etc/ntp.conf

---

### Post by hunters1094 on 2011-07-17
> **Cheesehead said:**
> Please post the contents of your file: /etc/ntp.conf

thanks for your quick reply. The file /etc/ntp.conf appears when the ntpd is installed. right? Because my Desktop (use the Ubuntu 10.04 Desktop) has got right time since i installed it. And the command 
ntpdate ntp.ubuntu.com

run well without /etc/ntp.conf. About 9 hours, i'm showing the /etc/ntp.conf of my servers to u.

Thanks if you have more ideas.

---

### Post by hunters1094 on 2011-07-17
after install ntp, the /etc/ntp.conf file does not exist. So i create another one, that has content :

I reboot 2 times, but nothing changes.


```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift


# Enable this if you want statistics to be logged.
#statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server 1.pool.ntp.org
server 2.pool.ntp.org
server 0.pool.ntp.org
server ntp.ubuntu.com
# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

---

### Post by tgalati4 on 2011-07-18
Did you actually start the ntp server?

sudo /etc/init.d/ntp start

Also check in /etc/default to make sure that the ntp daemon is configured to start automatically.

Set Is_Configured to yes

---

### Post by hunters1094 on 2011-07-18
> **tgalati4 said:**
> Did you actually start the ntp server?

sudo /etc/init.d/ntp start

Also check in /etc/default to make sure that the ntp daemon is configured to start automatically.

Set Is_Configured to yes



hi. thank you

i rebooted 2 times. When i use 

ntpdate ntp.ubuntu.com

it said that ntp socket is in use.

in the directory /ect/default, i see ntp file.

---

### Post by SeijiSensei on 2011-07-18
ntpdate doesn't use the ntp.conf file; only the NTP server ntpd does.

If you're running ntpd, you can't run ntpdate.  You'll get the "socket in use" error that you reported above.

Try stopping ntp (sudo service ntp stop), then running

ntpdate 0.pool.ntp.org

If it doesn't connect, try first running "ping 0.pool.ntp.org" and see if (a) your server can resolve the name and, (b) it can ping the server.

If the server is directly on the Internet with an iptables firewall in place, you probably need to open UDP port 123 to allow replies from the remote time server.  If you're behind a masquerading firewall, this shouldn't be needed.

---

### Post by hunters1094 on 2011-07-19
> **SeijiSensei said:**
> ntpdate doesn't use the ntp.conf file; only the NTP server ntpd does.

If you're running ntpd, you can't run ntpdate.  You'll get the "socket in use" error that you reported above.

Try stopping ntp (sudo service ntp stop), then running

ntpdate 0.pool.ntp.org

If it doesn't connect, try first running "ping 0.pool.ntp.org" and see if (a) your server can resolve the name and, (b) it can ping the server.

If the server is directly on the Internet with an iptables firewall in place, you probably need to open UDP port 123 to allow replies from the remote time server.  If you're behind a masquerading firewall, this shouldn't be needed.

hi

Thanks for your reply

I know it because i use ntpdate to check if ntp service is running.
I stop ntp service, and can ping 0.pool.ntp.org. But to run the "ntpdate 0.pool.ntp.org", it says "no server suitable for synchronization found"

---

