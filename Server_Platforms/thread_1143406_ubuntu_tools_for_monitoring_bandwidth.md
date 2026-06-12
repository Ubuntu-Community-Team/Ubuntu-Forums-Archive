---
title: "ubuntu tools for monitoring bandwidth?"
date: 2009-04-29
forum: Server Platforms
---

### Post by submute on 2009-04-29
I'd like some command-line tools to monitor bandwidth (to the outside world, not my LAN). Ideally something with simple output (kbps up/down) so I can graph it in Cacti.

Any suggestions? Thanks!

---

### Post by upbeat.linux on 2009-06-01
What exactly are you trying to monitor the bandwidth of? From where to where?

---

### Post by Axanon on 2009-06-02
I would like to monitor all in/out WAN traffic and exclude LAN traffic between computers on the LAN. I do want to monitor the other computer's WAN traffic too though. I have tried Darkstat, but am looking for something else. HTTP/Graphs would be nice, but anything that keeps a human-viewable database for a configurable amount of time will do.

---

### Post by Alekz_ on 2009-06-02
It may supply your needs:

[http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)

IF I understood what you want! :)

---

### Post by upbeat.linux on 2009-06-02
You can try using ipflow. It's simple and live.

Also, you can autograph stuff like this in Cacti by enabling SMTP on the appropriate device or box and then using the appropriate template.

---

### Post by nix4me on 2009-06-02
vnstat is an excellent command line bw monitor.  I use it to monitor my dedicated servers.

---

### Post by SlugSlug on 2009-06-04
i like iftop..

---

### Post by iponeverything on 2009-06-04
depending on the setup the below might work. 

```
iptables -N outside
iptables -A INPUT -s 0/0 -j outside
iptables -A INPUT -d 0/0 -j outside
netstat -tn |awk '$5 {print $5}' |awk -F\: '{print $1}' | sort | uniq |grep -v Add |grep -v serv|awk '{print "iptables -A outside -s "$1" ; iptables -A outside -d "$1 }'  |sh

```

To see the traffic stats use 

```
iptables -nvx -L outside
```

Here is good howto:

[http://wiki.openvz.org/Traffic_accounting_with_iptables](http://wiki.openvz.org/Traffic_accounting_with_iptables)

ntop works very well also

---

### Post by fmsismo on 2009-06-04
You can use munin.

[http://munin.projects.linpro.no/](http://munin.projects.linpro.no/)

---

### Post by hictio on 2009-06-04
++ iftop
For a quick "see who's stealing all the bandwidth" I like iftop.
If you want a more thorough look at what's going then [ntop](http://www.ntop.org/).

---

