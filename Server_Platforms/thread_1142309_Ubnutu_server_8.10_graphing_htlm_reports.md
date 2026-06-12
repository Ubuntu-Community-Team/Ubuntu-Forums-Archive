---
title: "Ubnutu server 8.10 graphing htlm reports"
date: 2009-04-29
forum: Server Platforms
---

### Post by thefatmoop on 2009-04-29
Hi everyone

I run a bunch of virtual machines on server 8.10 and i'd like to keep track of the master server's bandwidth usage. 

Are there any easy/popular programs that will keep track of what's going on and (i hope) generate an html output with visuals? (including users who logged in, bandwidth graphs, some log tails...etc) 

thanks alot

---

### Post by smeerbartje on 2009-04-29
> **thefatmoop said:**
> Hi everyone

I run a bunch of virtual machines on server 8.10 and i'd like to keep track of the master server's bandwidth usage. 

Are there any easy/popular programs that will keep track of what's going on and (i hope) generate an html output with visuals? (including users who logged in, bandwidth graphs, some log tails...etc) 

thanks alot

Just Google a bit and you will find out that there are a lot of bandwith monitoring tools. My favorite: vnstat. It generated output to console and/or webpage/mail/etc.

---

### Post by samosamo on 2009-04-29
You're looking for what is called an NMS.  No datacenter should be without one.  I personally use Cacti.  Since you are running a VM server, go ahead and download CactiEZ, which is a CentOS based Cacti server CD.  Comes with Nagios, Webmin, all the goodies.  I have it tracking ~10 servers with SNMP.  Things like interface bandwidth, disk space, CPU utilization, load times.  If configured it can email you when it sees problems.

---

### Post by thefatmoop on 2009-04-29
i just did sudo apt-get install cacti....
how do i access it, where did it end up being installed..?

---

### Post by wsonar on 2009-04-29
does this do tempature also?

---

### Post by thefatmoop on 2009-04-30
good program, but installing new plugins seems to be a pain

---

### Post by samosamo on 2009-04-30
> **wsonar said:**
> does this do tempature also?

It does anything SNMP is capable of doing.  So yes.  Mine gets info from lm_sensors and hddtemp.


> **thefatmoop said:**
> good program, but installing new plugins seems to be a pain

I agree.  They do not have a very good plugin system.  That is why I recommended installing the full CactiEZ OS with all the plugins done already.  It's the easiest solution unless you want to wrestle with adding plugins yourself.

---

