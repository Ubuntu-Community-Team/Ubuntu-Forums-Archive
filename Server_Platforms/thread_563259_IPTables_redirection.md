---
title: "IPTables redirection"
date: 2007-09-29
forum: Server Platforms
---

### Post by jleiss on 2007-09-29
I just got iptables up and working. Now I have something a little trickier that I need help with. I have zimbra on a vm machine and want to make the web interface available to the outside, other than that it will not house any other web traffic so redirecting port 80 won't work. What I want it to do is take any outside connections going to port 81 and redirect them to the vm on port 80. Any ideas?

---

### Post by HermanAB on 2007-09-29
Hmm, if the VM uses bridging, it can have its own IP address, then you don't need to jump through any hoops.

Cheers,

H.

---

### Post by jleiss on 2007-09-29
the vm does have its own ip address, but it is a local address on a non-routable subnet.

---

### Post by HermanAB on 2007-09-29
You could try something like this:
iptables -t nat -I PREROUTING -i eth0 -p tcp --dport 81 -j REDIRECT --to-port 80

I'm using a trick like that to make my mail server listen on port 2525 in addition to port 25, which is blocked by some schtoopidt ISPs.  So then I can go wherever I need to and use my own mail server with my laptop without having to reconfigure it all the time.

Cheers,

H.

---

### Post by jleiss on 2007-09-29
I would need to set the firewall to accept that port too I assume, what about a forwarding statement? Also since I would be redirect to a different machine would i put the IP before the destination port?

---

### Post by HermanAB on 2007-09-29
Hmm, come to think of it, the easiest way by far, to forward packets from one machine to another is with 'rinetd'.  I always use that one to forward an old server to a new server while the DNS is still updating around the world: [http://www.boutell.com/rinetd/](http://www.boutell.com/rinetd/)

It is exceptionally easy to configure in /etc/rinetd.conf:
oldipaddress oldport newipaddress newport
...

then it just happily shovels packets back and forth.

Cheers,

H.

---

### Post by jleiss on 2007-09-30
So i installed rinetd from the universe repository. I also configured based upon what you and the rules showed. Here is my config file.

  GNU nano 1.3.10               File: /etc/rinetd.conf                                     

#
# this is the configuration file for rinetd, the internet redirection server
#
# you may specify global allow and deny rules here
# only ip addresses are matched, hostnames cannot be specified here
# the wildcards you may use are * and ?
#
# allow 192.168.2.*
# deny 192.168.2.1?
allow 67.170.168.75

#
# forwarding rules come here
#
# you may specify allow and deny rules after a specific forwarding rule
# to apply to only that forwarding rule
#
# bindadress    bindport  connectaddress  connectport
67.170.168.75 81 192.168.0.2 80

# logging information
logfile /var/log/rinetd.log

# uncomment the following line if you want web-server style logfile format
# logcommon

I put a tail against the log file and tried to hit it from the outside and got nothing in the logs and a time out from the other machine. I also have the port opened at the firewall. I killed and restarted the process too.

---

### Post by HermanAB on 2007-09-30
Hmm, I think your allow/deny rule is wrong.  You have to allow everything, since you have no idea who is going to contact your machine.  I think that by default rinetd accepts everything, so just remove the 'allow' rule altogether and only leave the ip and ports rule.

For starters open up the firewalls completely and once you are sure that it works, you can tighten things down a bit.

This will remove all firewall rules:
$ sudo iptables -F

(Don't worry, it is Linux, you are quite safe even with NO firewall rules)

Then test things with telnet:
$ telnet ipaddress port

Cheers,

H.

---

