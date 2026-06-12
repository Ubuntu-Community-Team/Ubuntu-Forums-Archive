---
title: "Installing SNORT"
date: 2013-06-11
forum: Security
---

### Post by Linux_n00b on 2013-06-11
Hello,  what is the proper/successful way to installing Snort on Ubuntu 12.04.2 Server LTS?  I tried searching on the internet, but each tutorial does not work successfully...

---

### Post by linuxtechguy on 2013-06-11
apt-get install snort

---

### Post by Linux_n00b on 2013-06-11
How do I configure it properly?

---

### Post by claracc on 2013-06-12
I think the staightforward method to know about this software is to read the manual provided here: [http://www.snort.org/start/documentation](http://www.snort.org/start/documentation)

---

### Post by termvrl on 2013-06-16
Hi,

A few things you need to look at during troubleshooting snort:- 
1) Make sure your interface in promiscuous mode. If you want to sniff on you LAN, you need to port mirror the switch port.
2) Make sure your snort.conf have set the HOME_NET variable, in the latest version of snort, you need to set it.
3) The user account you use need to have enough permission to access all needed files for snort to run.
4) You can test your snort with a test rule,alert tcp any any -> any any (msg:"Testing rule"; classtype:not-suspicious; sid:999999; rev:1; priority:0;)

Thanks

---

