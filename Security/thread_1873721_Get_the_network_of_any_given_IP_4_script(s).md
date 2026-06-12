---
title: "Get the network of any given IP 4 script(s)"
date: 2011-11-01
forum: Security
---

### Post by AskTell on 2011-11-01
how do i easily detect the network of an ip address for use in a script (easy to extract info like in log files)

IP Address  58.218.199.147 
Network      58.218.199.0/24

with that said I'm gonna go read the stickys I should of read a long time ago

---

### Post by Lars Noodén on 2011-11-02
Which language are the scripts going to be in?  There probably are libraries or modules that do what you need.  For perl you can try looking around [CPAN](http://www.cpan.org/) in Net:: and Net:: modules.  For example there is [NetAddr::IP](http://search.cpan.org/~miker/NetAddr-IP-4.055/IP.pm).

---

### Post by AskTell on 2011-11-02
bash and/or perl

I'll make it in bash first but i know i should make it in perl for future compatibility

---

### Post by lensman3 on 2011-11-02
I only have access to a Fedora Core 15 right now, but my machine has a program call "ipcalc" in /bin . When it is executed from a command line like:

/bin/ipcalc --network 192.168.200.10 255.255.255.0

it returns NETWORK=192.168.200.0

There are lots of other options.  Then is used in FC15 network scripts and uses of it can be found in "/etc/sysconfig/network-scripts/network-functions."

Hope this helps.

---

### Post by emiller12345 on 2011-11-02
I wrote a couple of bash scripts a while ago that when you give it an ipaddr and netmask, if will give you the lowerest ip in the range, and another script that will give the highest ip in the range.
> 
[http://digitalmagican.wordpress.com/2011/07/07/maximum-and-minimum-ip-for-a-given-ipnetmask-combo/](http://digitalmagican.wordpress.com/2011/07/07/maximum-and-minimum-ip-for-a-given-ipnetmask-combo/)


---

### Post by AskTell on 2011-11-03
This thread has some good answers, i'll mark it solved.

TY!

---

