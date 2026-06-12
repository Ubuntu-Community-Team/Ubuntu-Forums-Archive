---
title: "NTP time server"
date: 2011-05-13
forum: Server Platforms
---

### Post by chrisbay90 on 2011-05-13
Having trouble getting my server set up as a time server. I have install ntp, and configured /etc/ntp.conf as follows. My laptop give the following error

```
$ sudo ntpdate <serverIP>
13 May 16:30:14 ntpdate[4085]: no server suitable for synchronization found

```

Win clients also say "There was an error sychronising"

Any idea what im doing wrong?

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

server 0.au.pool.ntp.org
server 1.au.pool.ntp.org
server 2.au.pool.ntp.org
server 3.au.pool.ntp.org

server ntp.ubuntu.com


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
#restrict -4 default kod notrap nomodify nopeer noquery 
#restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1
restrict 10.1.69.53

restrict 10.1.69.0 mask 255.255.255.0 nomodify notrap

#IPv4: restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap nopeer
#restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap nopeer
#restrict 10.1.69.0 mask 255.255.255.0

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255
broadcast 10.1.69.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient


```

---

### Post by chrisbay90 on 2011-05-13
P.S.

Some output that may help

```
$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 2x2sbs.2x2.loca 86.77.84.80      2 u    5   64    1    2.941  -16445.   0.001
 ntp.tourism.wa. 130.95.179.80    2 u   26   64    1   65.973  -20.996   0.001
 203.188.137.97  121.0.0.42       3 u   40   64    1   69.811  -17.078   0.001
 lists2.luv.asn. 203.161.12.165   3 u   27   64    1   31.936  -29.017   0.001
 cachens2.onqnet 209.81.9.7       2 u   33   64    1   26.344  -20.042   0.001
 europium.canoni 193.79.237.14    2 u   60   64    1  308.619  -11.015   0.001
 10.1.69.255     .BCST.          16 u    -   64    0    0.000    0.000   0.001

$ sudo ntpdate localhost
13 May 17:37:39 ntpdate[1468]: the NTP socket is in use, exiting

```

---

### Post by Lars Noodén on 2011-05-13
The error "no server suitable for synchronization found" means that you are not pointing at a time server or that the server is inaccessible.  Try pointing **ntpdate** at a different host.

---

### Post by chrisbay90 on 2011-05-13
Thanks Lars, appreciate you taking the time to help.

the client can sync ntpdate with another server.
```

sudo ntpdate ntp.ubuntu.com
13 May 17:43:44 ntpdate[5504]: adjust time server 91.189.94.4 offset 0.008510 sec

```

The server is accessible from this client as I am currently configuring it via SSH through this client.

---

### Post by Lars Noodén on 2011-05-13
Are you trying to set up your own time server for you LAN?  Or just trying to sync machines on your LAN with the world's (or Ubuntu's) time servers?

---

### Post by chrisbay90 on 2011-05-13
Trying to set up my own server to be a time server in this network.

---

### Post by Lars Noodén on 2011-05-13
> **chrisbay90 said:**
> Trying to set up my own server to be a time server in this network.

And just to check the obvious, your firewall should allow incoming TCP and UDP traffic on port 123 (ntp) from your LAN.

---

### Post by Lars Noodén on 2011-05-13
> **chrisbay90 said:**
> ```
$ sudo ntpdate localhost
13 May 17:37:39 ntpdate[1468]: the NTP socket is in use, exiting

```

You will get that error if you try to run **ntpdate** on the same machine as your time server.  Try running the test from one of your clients.

---

### Post by chrisbay90 on 2011-05-13
That wouldnt be the first time I needed the obvious pointed out to me.
No firewall on this server. Brand new install today, on development LAN. Am correct in assuming that Ubuntu does not have ANY a firewall by default? 10.04 by the way.

---

### Post by chrisbay90 on 2011-05-13
> **Lars Noodén said:**
> You will get that error if you try to run **ntpdate** on the same machine as your time server.  Try running the test from one of your clients.

Have done, fails with
```
client:~# ntpdate 10.1.69.17
13 May 18:54:25 ntpdate[6955]: no server suitable for synchronization foun
```

---

### Post by Lars Noodén on 2011-05-13
And nmap probably shows that port 123 is closed: I am able to duplicate your error on my machines with ntpd. There is either a bug or we are both missing something obvious.

Edit: sudo nmap -sU -p 123 timeserver

Edit;  It is now working for me, I had to modify the [restricting keywords](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server#The_.2Fetc.2Fntp.conf_File)

```

restrict 10.1.69.0 mask 255.255.255.0 nomodify notrap
broadcast 10.1.69.255

```

---

### Post by chrisbay90 on 2011-05-13
Just got home (about an hours drive). Thank you for going to such an effort for me, that is highly appreciated. Will try this after dinner.

---

### Post by chrisbay90 on 2011-06-13
Is working now (since the morning after). Could have sworn that's what I had while it wasn't working. Possibly a case of typo's/forgetting to restart the service/silliness that comes from trying to make administrative changes late at night. For completeness I thought i would pop back and display my entire /etc/ntpd.conf file for anyone who may find it useful. Thanks so much for you're help.

> **Lars Noodén said:**
> And nmap probably shows that port 123 is closed: I am able to duplicate your error on my machines with ntpd. There is either a bug or we are both missing something obvious.

Edit: sudo nmap -sU -p 123 timeserver

Edit;  It is now working for me, I had to modify the [restricting keywords]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch24_:_The_NTP_Server#The_.2Fetc.2Fntp.conf_File")

```

restrict 10.1.69.0 mask 255.255.255.0 nomodify notrap
broadcast 10.1.69.255

```

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
server 10.1.69.2

server 0.au.pool.ntp.org
server 1.au.pool.ntp.org
server 2.au.pool.ntp.org
server 3.au.pool.ntp.org

server ntp.ubuntu.com


# Access control configuration; see /usr/share/doc/ntp-doc/html/accopt.html for
# details.  The web page <http://support.ntp.org/bin/view/Support/AccessRestrictions>
# might also be helpful.
#
# Note that "restrict" applies to both servers and clients, so a configuration
# that might be intended to block requests from certain clients could also end
# up blocking replies from your own upstream servers.

# By default, exchange time with everybody, but don't allow configuration.
#restrict -4 default kod notrap nomodify nopeer noquery 
#restrict -6 default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1
restrict ::1
restrict 10.1.69.53

restrict 10.1.69.0 mask 255.255.255.0 nomodify notrap

#IPv4: restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap nopeer
#restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap nopeer
#restrict 10.1.69.0 mask 255.255.255.0

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
#restrict 192.168.123.0 mask 255.255.255.0 notrust


# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255
broadcast 10.1.69.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
#disable auth
#broadcastclient

```

---

