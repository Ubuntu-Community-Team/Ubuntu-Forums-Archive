---
title: "NTP server problem"
date: 2008-11-08
forum: Server Platforms
---

### Post by vmaxx on 2008-11-08
In installed ntp on ubuntu 8.10 server. I followed instructions from several sites which are basically the same as [this]("http://www.ubuntugeek.com/network-time-protocol-ntp-server-and-clients-setup-in-ubuntu.html").
Everything looks right on the server itself. I check with ntpq -np and all the servers I configured in /etc/ntp.conf are displayed. jitter is not bad, but when I check from another ubuntu machine using ntpdate IP or Windoz box with an ntptool, it says "no server suitable for synchronization found".

I have tried different restrictions and have even gone through the documentation from ntp.org and nothing changes the result from other machines. 
My ntp.conf list is:
# Enable this if you want statistics to be logged.

#statsdir /var/log/ntpstats/



statistics loopstats peerstats clockstats

filegen loopstats file loopstats type day enable

filegen peerstats file peerstats type day enable

filegen clockstats file clockstats type day enable





# You do need to talk to an NTP server or two (or three).

server ntp.ubuntu.com

server ntp0.pipex.net





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

restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap



# If you want to provide time to your local subnet, change the next line.

# (Again, the address is an example only.)

broadcast 192.168.1.255



# If you want to listen to time broadcasts on your local subnet, de-comment the

# next lines.  Please do this only if you trust everybody on the network!

#disable auth

#broadcastclient


Any ideas what I am doing wrong. I want all machines in the 192.168.1.0/24 subnet to get its time from the ubuntu server.

---

### Post by Krupski on 2008-11-08
> **vmaxx said:**
> .....I check with ntpq -np and all the servers I configured in /etc/ntp.conf are displayed. jitter is not bad, but when I check from another ubuntu machine using ntpdate IP or Windoz box with an ntptool, it says "no server suitable for synchronization found".

I have a local intranet on 192.168.1.nn and I finally got NTPD to run fine as a time server. Here's my "/etc/ntp.conf" file:

```

# /etc/ntp.conf, configuration for ntpd; see ntp.conf(5) for help

driftfile /var/lib/ntp/ntp.drift

# Enable this if you want statistics to be logged.
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
server time.nist.gov
server time-a.nist.gov
server time-b.nist.gov
server time-a.timefreq.bldrdoc.gov
server time-b.timefreq.bldrdoc.gov
server time-c.timefreq.bldrdoc.gov

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
[COLOR="Red"]**restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap**[/COLOR]
restrict 127.0.0.1
restrict ::1

# Clients from this (example!) subnet have unlimited access, but only if
# cryptographically authenticated.
# restrict 192.168.123.0 mask 255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
# broadcast 192.168.1.255

# If you want to listen to time broadcasts on your local subnet, de-comment the
# next lines.  Please do this only if you trust everybody on the network!
# disable auth
# broadcastclient

```

Note the line in red... that's what made it work.

Note that after you edit ntp.conf, you have to do two things:

(1) Restart the NTP daemon:

```

sudo /etc/init.d/ntp restart

```

(2) Wait at least 10 to 15 minutes before trying to sync to your server.

Don't know WHY it takes 10 to 15 minutes, but it does.

Good luck!

-- Roger

---

### Post by hictio on 2008-11-08
Is your Ubuntu NTPD box allowing connections on the ntpd ports (123 TCP & UDP)?
Does it have any firewall (built in or external) blocking access to those ports?

---

### Post by hictio on 2008-11-09
Another test, from one of the Linux boxes on your LAN, type at the prompt:

```

/usr/sbin/ntpdate -q -d ip.address.of.your.Ubuntu.ntpd

```

No need to issue this via sudo, since you are only querying the NTPD server.
You should see something like this:
```

web10 ~ $ /usr/sbin/ntpdate -q -d clock.via.net
 9 Nov 00:19:10 ntpdate[18797]: ntpdate 4.2.2p1@1.1570-o Tue Jun 10 00:07:19 UTC 2008 (1)
Looking for host clock.via.net and service ntp
host found : clock.via.net
transmit(209.81.9.7)
receive(209.81.9.7)
transmit(209.81.9.7)
receive(209.81.9.7)
transmit(209.81.9.7)
receive(209.81.9.7)
transmit(209.81.9.7)
receive(209.81.9.7)
transmit(209.81.9.7)
server 209.81.9.7, port 123
stratum 1, precision -18, leap 00, trust 000
refid [GPS], delay 0.10081, dispersion 0.00003
transmitted 4, in filter 4
reference time:    ccc0f146.5430070d  Sun, Nov  9 2008  0:19:02.328
originate timestamp: ccc0f14f.55a0873e  Sun, Nov  9 2008  0:19:11.334
transmit timestamp:  ccc0f14f.4bcb923a  Sun, Nov  9 2008  0:19:11.296
filter delay:  0.10089  0.10095  0.10095  0.10081 
         0.00000  0.00000  0.00000  0.00000 
filter offset: 0.000451 0.000386 0.000493 0.000422
         0.000000 0.000000 0.000000 0.000000
delay 0.10081, dispersion 0.00003
offset 0.000422

 9 Nov 00:19:11 ntpdate[18797]: adjust time server 209.81.9.7 offset 0.000422 sec

```

A possibility is that your clients clock's are so offset that they can't sync to your NTPD server.
If that is the case, you;ll have to issue, as root or via sudo, an ntpdate to force the sync to reduce the time difference between the client and the server.

---

### Post by Krupski on 2008-11-09
> **hictio said:**
> Another test, from one of the Linux boxes on your LAN, type at the prompt:

```

/usr/sbin/ntpdate -q -d ip.address.of.your.Ubuntu.ntpd

```



I tried that command against my file server box (Ubuntu 8.10 server 64 bit) and got this:

```

root@michael:/# /usr/sbin/ntpdate -q -d storage
 9 Nov 09:38:01 ntpdate[6856]: ntpdate 4.2.4p4@1.1520-o Wed Aug 20 17:03:53 UTC 2008 (1)
transmit(192.168.1.11)
receive(192.168.1.11)
transmit(192.168.1.11)
receive(192.168.1.11)
transmit(192.168.1.11)
receive(192.168.1.11)
transmit(192.168.1.11)
receive(192.168.1.11)
transmit(192.168.1.11)
server 192.168.1.11, port 123
stratum 2, precision -20, leap 00, trust 000
refid [192.168.1.11], delay 0.02573, dispersion 0.00000
transmitted 4, in filter 4
reference time:    ccc16cc7.884eb10a  Sun, Nov  9 2008  9:05:59.532
originate timestamp: ccc1744a.153931bc  Sun, Nov  9 2008  9:38:02.082
transmit timestamp:  ccc1744a.1540dd3f  Sun, Nov  9 2008  9:38:02.083
filter delay:  0.02576  0.02573  0.02573  0.02573 
         0.00000  0.00000  0.00000  0.00000 
filter offset: -0.00019 -0.00019 -0.00019 -0.00019
         0.000000 0.000000 0.000000 0.000000
delay 0.02573, dispersion 0.00000
offset -0.000197

 9 Nov 09:38:02 ntpdate[6856]: adjust time server 192.168.1.11 offset -0.000197 sec

```

Does this look right?

-- Roger

---

### Post by vmaxx on 2008-11-09
Krupski, thanks for the conf file and the patience tip. I never would have thought to wait 15 minutes after restarting and have never read that on any other post. Both tips worked like a charm. It is surprising that leaving the broadcast commented out works {# broadcast 192.168.1.255}, but it does. 

Thanks again

vm

---

### Post by vmaxx on 2008-11-09
hictio, thanks for the other test. I have not seen that one before, and it works.

vm

---

### Post by hictio on 2008-11-09
> **vmaxx said:**
> hictio, thanks for the other test. I have not seen that one before, and it works.

vm

Cool, remember that you can use ntpdate any time, even if the ntpd service is up and running; the only thing is that if that is the case, you have to the flag '-u' so it uses another port and it doesn't conflict with the running ntpd.

> **Krupski said:**
> I tried that command against my file server box (Ubuntu 8.10 server 64 bit) and got this:

Does this look right?

-- Roger

Yes, it does.

---

### Post by Krupski on 2008-11-09
> **vmaxx said:**
> Krupski, thanks for the conf file and the patience tip. I never would have thought to wait 15 minutes after restarting and have never read that on any other post. Both tips worked like a charm. It is surprising that leaving the broadcast commented out works {# broadcast 192.168.1.255}, but it does. 

Thanks again

vm

Well, I was trying different things (editing ntp.conf) then immediately testing them.

Tried broadcast, then test - no go.

Tried restrict, then test - no go.

Then I did another Google search and saw a different "restrict" line, so I put it in and tested it - no go.

Then I had to go to the bathroom :) and when I came back, I forgot if I had made a change, so I tested it again and it WORKED!

I said "Whoa there what did I do to make it work?"

I also got the idea that the "bathroom delay" had something to do with it, so I ran through the different options, WAITED 10 minutes each time, then tested.

That's how I found out that:

(1) Only a simple edit is needed and
(2) You have to wait 10 minutes!

Lucky I stumbled across it!  :)

-- Roger

---

### Post by hictio on 2008-11-09
> 
(1) Only a simple edit is needed and
(2) You have to wait 10 minutes!


You can also use 'ntpdate' as root or via sudo, to reduce those 10 minutes; another good, I don't know, practice, I guess is the word; is adding an entry, to say, the '/etc/rc.local' file to issue an ntpdate sync upon booting (again, using the '-u' flag if the box has ntpd running), just in case the server drifted a bit due to BIOS date or similar.

---

