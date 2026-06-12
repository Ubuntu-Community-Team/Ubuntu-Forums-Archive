---
title: "dnsmasq refuses if run as service, works when run manually"
date: 2012-07-13
forum: Server Platforms
---

### Post by clickwir on 2012-07-13
I'm not sure this makes sense. But if I do 'sudo service dnsmasq start' and then dig something, I get a 'status: REFUSED'. If I stop the service and just run 'sudo dnsmasq', doing the same dig request results in a proper response.

This odd behavior is happening on 2 systems. Both systems are working and serving queries fine right now. However, if they reboot, I'll be catching hell.

I don't get any errors in /var/log/syslog even with turning on log-queries in the dnsmasq.conf file. 

Any idea why running dnsmasq as a service would make it refuse connections but run from a command line and allowed to daemonize it self, it works fine?

---

### Post by Cheesehead on 2012-07-13
That is not the normal behavior. It should respond no matter how it is started.

If you start it as a service, does the daemon really start? Is it listed in a ps? Does it start at startup or do you always start it manually? If manually, then how did you install it?

---

### Post by clickwir on 2012-08-11
Sorry, forgot about it after I got it working. Remembered after I rebooted and the wife came yelling that she couldn't get Netflix. Opps. Necessity is the mother of fixing!

```
clickwir@ubuntu:~$ sudo service dnsmasq start
 * Starting DNS forwarder and DHCP server dnsmasq                                                                                                                           [ OK ] 
status: Unknown job: squid

clickwir@ubuntu:~$ dig kingston.com

; <<>> DiG 9.8.1-P1 <<>> kingston.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 25391
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kingston.com.                  IN      A

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Aug 11 00:13:56 2012
;; MSG SIZE  rcvd: 30

clickwir@ubuntu:~$ ps aux | grep dns
dnsmasq   2205  0.4  0.0  30404  2572 ?        S    00:13   0:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -r /var/run/dnsmasq/resolv.conf -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new
clickwir  2298  0.0  0.0   9388   928 pts/2    R+   00:14   0:00 grep --color=auto dns

clickwir@ubuntu:~$ sudo service dnsmasq stop
status: Unknown job: squid
 * Stopping DNS forwarder and DHCP server dnsmasq                                                                                                                           [ OK ] 

clickwir@ubuntu:~$ ps aux | grep dns

clickwir  2392  0.0  0.0   9388   924 pts/2    S+   00:15   0:00 grep --color=auto dns

clickwir@ubuntu:~$ sudo dnsmasq 

clickwir@ubuntu:~$ ps aux | grep dns
nobody    2397  4.0  0.0  30404  2580 ?        S    00:16   0:00 dnsmasq
clickwir  2399  0.0  0.0   9388   928 pts/2    S+   00:16   0:00 grep --color=auto dns

clickwir@ubuntu:~$ dig kingston.com

; <<>> DiG 9.8.1-P1 <<>> kingston.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8726
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kingston.com.                  IN      A

;; ANSWER SECTION:
kingston.com.           3600    IN      A       63.251.221.6

;; Query time: 690 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Aug 11 00:16:08 2012
;; MSG SIZE  rcvd: 46

```

So I started the service, tried a dig. Got a REFUSED. Stopped the service and just ran 'sudo dnsmasq' by itself and no get NOERROR and responses are fast and accurate.

It must be a config thing because I've mirrored the config on 2 servers, they are both doing the same thing. The second server was just wiped and reloaded with Ubuntu Server 12.04 64bit last week. Though I didn't test dnsmasq as a service before copying over my config, so I'm assuming a bit there.

The service does start at startup, that's how I refound out about the problem. I was rebooting because of a kernel update and forgot I had the dnsmasq issue. I installed it via 'sudo apt-get install dnsmasq', just like I always have.

---

### Post by clickwir on 2012-08-11
Ok, I poked around a bit and.... best I can tell it's trying to default to using /var/run/dnsmasq/resolv.conf as per /etc/default/dnsmasq

Simply uncommenting IGNORE_RESOLVECONF=yes, seems to have fixed it.

While in there, I also changed: #CONFIG_DIR=/etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new 

To this: CONFIG_DIR=/etc/dnsmasq.d

I don't know why it would want to be looking at all those configs.

```
clickwir@ubuntu:/etc/init.d$ ps aux | grep dns
dnsmasq   3029  0.0  0.0  30404  2576 ?        S    00:34   0:00 /usr/sbin/dnsmasq -x /var/run/dnsmasq/dnsmasq.pid -u dnsmasq -7 /etc/dnsmasq.d
clickwir  3138  0.0  0.0   9388   924 pts/2    R+   00:37   0:00 grep --color=auto dns

clickwir@ubuntu:/etc/init.d$ dig mushkin.com

; <<>> DiG 9.8.1-P1 <<>> mushkin.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12897
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mushkin.com.                   IN      A

;; ANSWER SECTION:
mushkin.com.            300     IN      A       140.239.141.11

;; Query time: 79 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Aug 11 00:37:47 2012
;; MSG SIZE  rcvd: 45

```

---

