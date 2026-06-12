---
title: "ddclient unable to determine IP address"
date: 2012-11-20
forum: Server Platforms
---

### Post by automaticgiant on 2012-11-20
i've tried every combination of the lines here(aside from account options) to get detect ip with all giving the same unable to determine error. the only one that works is specifying an ip which defeats the purpose.
ssl doesnt change anything but i'll use it when i get it working. i tried http... with the web site addresses, no change. tried like 5 different detection services, two firewall methods, just default w/o a web specifier. nothing. every post and thread i've come across does not help my situation. the problem is that for some reason, the get_url sub doesn't give a valid reply. cant understand why.

config:
```
#syslog=yes
#ssl=yes
#use=web, web=myip.opendns.com/
#ip=10.10.10.10
#use=web, web=myip.dnsomatic.com
#use=fw, fw=192.168.1.1/RST_status.htm, fw-login=admin, fw-password=password, fw-skip='IP Address       '
#use=web, web=checkip.dyndns.org/, web-skip='IP Address'
#use=netgear-wpn824, fw=192.168.1.1, fw-login=admin, fw-password=password
use=web
server=updates.dnsomatic.com
protocol=dyndns2
login=automaticgiant@gmail.com
password=*************
all.dnsomatic.com
```


server says these outputs. first is with use=web. second is with IP to show ddclient partially works with bum ip. third is to show that failure is strictly due to -noexec.
> $ ddclient -verbose -noexec
CONNECT:  checkip.dyndns.org
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.org
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:
WARNING:  unable to determine IP address
$ ddclient -verbose -noexec
INFO:     setting IP address to 10.10.10.10 for all.dnsomatic.com
UPDATE:   updating all.dnsomatic.com
CONNECT:  updates.dnsomatic.com
SENDING:  GET /nic/update?system=dyndns&hostname=all.dnsomatic.com&myip=10.10.10.10 HTTP/1.0
SENDING:   Host: updates.dnsomatic.com
SENDING:   Authorization: Basic YXV0b21hdGljZ2lhbnRAZ21haWwuY29tOjVDaHU2cmNoNw==
SENDING:   User-Agent: ddclient/3.8.0
SENDING:   Connection: close
SENDING:
FAILED:   updating all.dnsomatic.com: Could not connect to updates.dnsomatic.com.
$ ddclient -verbose
SUCCESS:  all.dnsomatic.com: skipped: IP address was already set to 10.10.10.10.

---

### Post by kevinthecomputerguy on 2012-11-21
Do you have multiple nics? have you tried the use this interface option, for multiple nics
use=if, if=eth1

replacing eth1 with eth0, or eth2, whatever your using.

this command will show you all of your interfaces.
ifconfig -a 

my ddclient.conf also has this line
pid=/var/run/ddclient.pid

---

### Post by automaticgiant on 2012-11-21
> **kevinthecomputerguy said:**
> Do you have multiple nics? have you tried the use this interface option, for multiple nics
use=if, if=eth1

replacing eth1 with eth0, or eth2, whatever your using.

this command will show you all of your interfaces.
ifconfig -a 

my ddclient.conf also has this line
pid=/var/run/ddclient.pid

reverse order:
i have no need to generate a pid file

one nic, but i've got the box behind a wireless router as i haven't set up iptables on it yet. so eth0 wouldn't be a useful source of ip.

---

