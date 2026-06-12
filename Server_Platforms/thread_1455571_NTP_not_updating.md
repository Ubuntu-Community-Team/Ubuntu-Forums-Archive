---
title: "NTP not updating"
date: 2010-04-16
forum: Server Platforms
---

### Post by iclebyte on 2010-04-16
Hello,

I have installed ntp using 
```
apt-get -y install ntp
```

Logging to /var/log/ntpstats has been enabled in /etc/ntp.conf however this directory is not getting populated with anything.

The following is showing in syslog

```
Apr 16 10:12:38 web1 ntpd[3613]: Listening on interface #6 eth0, 192.168.1.60#123 Enabled
Apr 16 10:12:38 web1 ntpd[3613]: Listening on interface #7 eth1, 192.168.50.10#123 Enabled
Apr 16 10:12:38 web1 ntpd[3613]: kernel time sync status 2040
Apr 16 10:12:38 web1 ntpd[3613]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift

```

However the time is still not updating.

What I have noticed is that I keep getting the following message when starting the ntp service

```
root@web1:/var/log/ntpstats# /etc/init.d/ntp start
**sh: getcwd() failed: No such file or directory**
 * Starting NTP server ntpd  
```

Even running the following doesn't seem to work

```

root@web1:/var/log/ntpstats# ntpdate ntp.ubuntu.com
16 Apr 11:40:52 ntpdate[3815]: no server suitable for synchronization found

```

Any ideas much apprechiated. I have this working on web2 with no problems. Very odd. 

Note: I have also tried removing it with apt-get --purge remove ntp and reinstalling but to no avail.

---

### Post by iclebyte on 2010-04-20
BUMP.

This is still not resolved - any ideas most apprechiated!

---

### Post by richardjh on 2010-04-20
I'm not sure I will be able to help, this looks like you are configured correctly.

The most likely reason for a fail is that a firewall is blocking the connection on port 123. 
The easiest and quickest way to test this assertion, is to shut down the firewall if you have one and try the command again:

```
sudo ntpdate ntp.ubuntu.com
```If this doesn't work try 

```
sudo ntpdate -u ntp.ubuntu.com
```to use an unprivileged port for outgoing packets. 

If this doesn't work then can you post the results of

```
grep -v "^#" /etc/ntp.conf  | grep -v ^$
``````
ntpq -p
```And finally to check ntp.ubuntu.com resolves in your DNS do this

```
dig ntp.ubuntu.com
```

---

### Post by Vegan on 2010-04-20
I use time.nist.gov to update my Linux box, works fine. I have it set to update daily. I also have my box setup to act as a time standard.

I have opened the port, but I have not setup an alias for it yet.

---

### Post by iclebyte on 2010-04-21
richardjh, thanks for your response.

The following command resulted in the same error.
```
ntpdate -u ntp.ubuntu.com 
```

Output from the requested GREP is as follows

```
root@web1:~# grep -v "^#" /etc/ntp.conf  | grep -v ^$
driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/
statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable
server ntp.ubuntu.com
restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery
restrict 127.0.0.1
restrict ::1
```

Interestingly this is exactly the same as the config file on the working server on the same subnet.

The output from 'ntpq -p' is as follows

```
root@web1:~# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 europium.canoni .INIT.          16 u    -   64    0    0.000    0.000   0.000
```

We also have no firewall configured yet - as these server's are currently sat under my desk before we deploy them to the datacenter.

```
root@web1:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@web1:~#

```

I really am at a loss with this one. I've re-installed the ntpd daemon countless times (using --purge) to no avail.

---

### Post by ICEB3AR on 2010-04-21
if > .INIT. stays in the result of the command: ```
ntpq -p 
``` it could be that the server can not resolve the names or has no connection to the internet.

As richardjh already asked: What's the output of
```
dig ntp.ubuntu.com
```

---

### Post by iclebyte on 2010-09-20
Unfortunatley this issue still has not been resolved.

The output of 'ntpq -p' is as follows 
```
root@web01:/var/log# ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 europium.canoni .INIT.          16 u    -   64    0    0.000    0.000   0.000

```
The output of 'dig ntp.ubuntu.com' is as follows
```

root@fuweb01:/var/log# dig ntp.ubuntu.com

; <<>> DiG 9.6.1-P1 <<>> ntp.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58566
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ntp.ubuntu.com.                        IN      A

;; ANSWER SECTION:
ntp.ubuntu.com.         600     IN      A       91.189.94.4

;; Query time: 18 msec
;; SERVER: 213.167.64.80#53(213.167.64.80)
;; WHEN: Mon Sep 20 12:22:35 2010
;; MSG SIZE  rcvd: 48

```

This issue still has me mystified! Any further ideas from the ubuntu-collective?

---

### Post by memilanuk on 2010-09-20
Man, I don't know what to tell you.  Sounds like you are doing almost everything right - it works on another box (web2) installed under similar circumstances, right?  You checked the firewall empty, etc. etc.  I installed two boxes in the last two days, one with 10.04.1 & one with Debian 5.06, both have ntpd working just fine.

Its almost like one (or more) files either aren't getting installed or got accidentally deleted during one of your early attempts to set things up, and now thats causing grief later because the ntpd depends on them being there.  How to figure that out... wish I could help, but I can't, short of suggesting a clean re-install.  Far from ideal, and it shouldn't be necessary, but sometimes it ends up being simpler than beating your head bloody on the keyboard...

Good luck,

Monte

---

### Post by iclebyte on 2010-09-22
Unfortunatley this box has now made it's way into the DC as our primary front end webserver so a rebuild is not really an option at this point in time.

Nightmare!

---

### Post by SlugSlug on 2010-09-22
can you post 

cat /etc/ntp.conf

&
cat /etc/default/ntp*

---

### Post by iclebyte on 2010-09-22
/etc/ntp.conf

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
server 192.168.161.254


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


/etc/defaults/ntp

```

NTPD_OPTS='-g'

```

---

### Post by SlugSlug on 2010-09-22
server 192.168.161.254

does that server serve as a ntp server??

try replace it with 

server ntp.ubuntu.com

---

### Post by memilanuk on 2010-09-22
If you look back at one of his first couple posts... he originally had it set to connect to ntp.ubuntu.com and got nothing.

---

### Post by SlugSlug on 2010-09-22
> **memilanuk said:**
> If you look back at one of his first couple posts... he originally had it set to connect to ntp.ubuntu.com and got nothing.


I believe issuing the command ntpdate 'server'  is different from the ntp running as a services that references /etc/ntp.conf..

not sure tho..

you could try the IP address instead


server 91.189.94.4

---

### Post by memilanuk on 2010-09-22
Yes, it is... but look @ post #5 in the thread... response to a request for a grep of ntp.conf... 'server ntp.ubuntu.com'

Why this one machine is b0rked as opposed to the other ones, and doesn't seem to run ntpdate *or* ntpd correctly is bizarre, and why I was thinking that somewhere along the line a file critical to the setup/execution of the commands got accidentally purged along with the rest.

iclebyte... have you tried removing (not purging) ntp and getting just ntpdate to work?  Perhaps removing the services aspect will get some clutter out of the way of finding what is wrong...  and try 'ntpdate pool.ntp.org', to remove ntp.ubuntu.com as a possible suspect (wheter due to network filters, etc.)

---

