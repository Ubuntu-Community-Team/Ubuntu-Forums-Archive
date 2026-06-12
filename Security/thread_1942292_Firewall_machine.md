---
title: "Firewall machine?"
date: 2012-03-17
forum: Security
---

### Post by darkod on 2012-03-17
Hi all.

I might get involved in a firewall project, and wanted some advice before hand.

The idea would be to make a stand alone firewall device (machine) based on Ubuntu Server. The only role would be the firewall and any needed NAT/routing functions, nothing more. No DHCP, no web, no data servers.

Does this seems feasible with ubuntu, and secure enough to protect a production web server (running win server 2008 )? I was reading around and it sounds ufw would be a good choice. I have no problem controlling it in terminal without gui.

Or I should be looking at something like IPCop or Smoothwall?

I would rather do it with ubuntu server with ufw because I am fairly familiar with it.

Also, so far I was unable to find any precise configuration information because in most cases it talks about turning on a firewall on your machine, not about configuring a stand alone firewall device.

1. Would I need to take care of routing between ext and int interfaces? You do that in /etc/network/interfaces? Otherwise how would it now where to pass the data, right...

2. I still don't know if I will need to be routing and redirecting specific ports, but I guess this should not be a problem (NAT option).

3. How attack resilient would all of that be?

Thanks a lot for any advice and resources. If you have more questions I can explain more, what I know up to now.

---

### Post by 2F4U on 2012-03-17
These article may help:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[https://help.ubuntu.com/community/Router/Firewall](https://help.ubuntu.com/community/Router/Firewall)
[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

---

### Post by agillator on 2012-03-17
First, why try to reinvent the wheel? There may be a valid reason, but make sure there is. If there really isn't and existing projects will do the job, spend your effort more profitably on something else you need.  Second, I personally use IPCop. There are some things I don't like, but I can put up with them. I have thought of programming my own firewall, but considering the first paragraph and after investigating IPCop, ufw and others, I turned my attention to other things.   Third, starting with ufw will work, yes. However, I suspect you will quickly go beyond what it will comfortably do and you will find it easier and more efficient to use iptables directly instead of through a go-between.  In short, if existing programs do not do what you need, more power to you. But do expect to be starting from scratch with iptables fairly quickly as you run into other programs' limitations. And do plan to do a lot of reading and technical research on firewalls if you really plan to build something fairly secure. Keep in mind that false security is worse than no security.

---

### Post by darkod on 2012-03-17
Thanks so far. Any comments on Smoothwall?

---

### Post by HermanAB on 2012-03-17
Well, using Linux as a firewall/router is quite trivial actually and can be done in less than ten lines of Bash.

The old firewall programs like Shorewall and all its *wall children are generally overkill, since they tend to set a bazillion rules for things that are simply not a problem anymore.

---

### Post by darkod on 2012-03-17
> **HermanAB said:**
> Well, using Linux as a firewall/router is quite trivial actually and can be done in less than ten lines of Bash.

The old firewall programs like Shorewall and all its *wall children are generally overkill, since they tend to set a bazillion rules for things that are simply not a problem anymore.

That is what got me started with the idea. I need fairly simple rules, and was reading the stickies in the Security forum, that you can only run few commands to open traffic on ports you need and that's it. You leave everything else closed.

That's what I would need, all else to be closed and (hopefully) secure! No fancy rules, not even a fancy GUI since it should be simple. However it would be a first project of mine like this and I do have few gaps. :)

Also, being an "ordinary" ubuntu would make any future recovery very easy I think.

---

### Post by HermanAB on 2012-03-18
A firewall in 9 lines of Bash:
[http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html](http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html)

---

### Post by CharlesA on 2012-03-18
> **HermanAB said:**
> A firewall in 9 lines of Bash:
[http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html](http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html)
Nice script. It sure sticks to the KISS ideal. :)

---

### Post by JKyleOKC on 2012-03-19
Am I doing something wrong here? When I click that link to examine the script, I see only an example of NAT processing, no firewall action at all. With the policy for all three chains set to ACCEPT, and no rule to DROP or REJECT anything, nothing is going to be blocked. Doesn't look very KISS-able to me, just the trailing S...

But it's possible I'm not seeing the same script you are!

EDIT: I did a bit of surfing at Herman's site and found the firewall script on a different page -- the firewall how-to. However it seems to have the same problem, in that the 9-line action doesn't block anything. The how-to goes on to tell how to add blocking, though.

If the policies for INPUT and FORWARD were set to REJECT or DROP, it would be a much better example. However I'm not at all sure it's a good idea to rate-limit the loopback interface...

---

### Post by darkod on 2012-03-19
Update: I went with Smoothwall as a first shot, and so far I like the test done.

Personally I would have liked to go with bare ubuntu server and ufw but it's not only mine decision. Anyway, Smoothwall was very easy to set up, very easy to add rules, and so far it seems it gets the job done.

Not sure if its GUI might be a security risk compared to a command line only system.

---

### Post by HermanAB on 2012-03-19
I run my servers with a single firewall rule, the rate limiter in those examples.

Pretty much all the other rules that smoothwall and the like add are superfluous nowadays, since the problems that they are testing for have been fixed in the Linux network stack many years ago already.

---

### Post by kalkems on 2012-03-19
Hi! I am planing to replace a firewall that's causing grief in our school network. I need a firewall that can handle 4 VLANS and traffic balancing. These VLANS must be sealed from each other. I was even considering having a proxy server. Any suggestions on how to do this? Any suggested howtos to study? 
/ernie

---

### Post by Cheesemill on 2012-03-20
I tend to use [SmoothWall]("http://www.smoothwall.org/"), and have had very good results with it.
Others to look at are [Untangle]("http://www.untangle.com/") which has paid for options such as AV and [Zentyal]("http://www.zentyal.org/") which is based on Ubuntu 10.04 (new beta is based on 12.04).

Like SmoothWall these both provide far more than basic NAT but you only have to install the modules you want to.

---

### Post by kalkems on 2012-03-21
Tanks. We are going to install 12.04 server in july on all our servers and att the same time upgrade the clients to 12.04. I have been running a 11.10 client and have noticed some issues with communication between our domain server (10.04) and this client - a nis connection. Could there be any problem between a firewall and the system if it is another version compared with the rest of the computers? A firewall must be really stable which makes me lean towards looking at 10.04 rather than 12.04 but maybe I'm ovet careful!
/ernie

---

### Post by darkod on 2012-03-22
I am happy how the firewall/server is acting so far. But I was thinking about something and would like an opinion.

How good can I expect it to be with high traffic? Because this is a server with Intel Xeon (not sure if it's 2c or 4c), 2GB RAM and 135GB RAID1 mirror, I would expect it to be able to handle much more traffic than a standalone firewall device which usually have much slower CPUs and less RAM.

This device will need to protect a single (at the moment) web server with about 5-6 sites and approx 50,000 daily visits (probably less).

---

### Post by Cheesemill on 2012-03-22
> **darkod said:**
> How good can I expect it to be with high traffic? Because this is a server with Intel Xeon (not sure if it's 2c or 4c), 2GB RAM and 135GB RAID1 mirror, I would expect it to be able to handle much more traffic than a standalone firewall device which usually have much slower CPUs and less RAM.

I should think you'll be OK, just keep an eye on the CPU, RAM, and disk stats when it's under a known load and you should be able to extrapolate it's maximum performance from that.

About your server having better stats than a standalone device, It's OK but I've been researching things like this for a client of mine :)

Untangle u500 - Xeon Quad Core, 4GB, 120GB SSD, 8x1000Gb LAN

Smoothwall SWG-3600 - 2x6 Core Xeon, 12GB RAM, 1TB RAID1, 4xGb LAN

---

### Post by darkod on 2012-03-22
> **Cheesemill said:**
> I should think you'll be OK, just keep an eye on the CPU, RAM, and disk stats when it's under a known load and you should be able to extrapolate it's maximum performance from that.

About your server having better stats than a standalone device, It's OK but I've been researching things like this for a client of mine :)

Untangle u500 - Xeon Quad Core, 4GB, 120GB SSD, 8x1000Gb LAN

Smoothwall SWG-3600 - 2x6 Core Xeon, 12GB RAM, 1TB RAID1, 4xGb LAN

When I said better stats I meant compared to smaller, basic devices like Cisco ASA5505 or the NETASQ F200 (it's discontinued on top of that) that was the contender to be used.

Not a 2x6c Xeon monsters. :)

It's still not in production so I can't really investigate the resources used up. What I do know so far, the RAM is never above 10% used, swap is always 0%, root and /var are at 1% only (at the moment).

Of course I expect things to change once in production, but hopefully it can take it. :)

---

### Post by JKyleOKC on 2012-03-22
I suspect that your biggest resource usage is going to be the space occupied by the /var/log files. These can grow exponentially with increasing activity, but keeping an eye on them and if necessary archiving older ones to a separate disk should be adequate. For years, I used an ancient (1995-era) Pentium 2 machine with only 80 MB of RAM and a 20-GB disk as my firewall. I would still be using it except for a switch failure that burned out its motherboard!

It doesn't take a lot of resources to check each packet as it moves through.

---

### Post by darkod on 2012-03-23
Ok guys, new question. :)

I have configured two machines, for comparison. One with Smoothwall Express 3.0 and the other with Ubuntu Server 10.04.4 LTS with ufw enabled.

So far they both seem to do the work. But doing a scan with nmap, I noticed something curious.

Scanning the Smoothwall shows all 1000 ports that nmap scans as filtered, which is what I should be expecting if I understood it correctly.

However, the same scan on Ubuntu Server shows me 5 ports as open or closed, and 995 as filtered. The 5 ports are the ones I have set ufw to allow and set port forwarding to the correct server on the private LAN.

So it seems Smoothwall has some setting that replies to a scan as filtered instead of open, even though it does accept traffic on that port and forwards it on to the server.

Is this something I can do with ufw too? Because from reading around it seems filtered is a much better response to a scan than open.

---

### Post by darkod on 2012-03-23
I managed to sort it out after playing with the ufw commands.

If you allow a rule in ufw with:
sudo ufw allow <port/protocol>

it will show as open during nmap scan (at least it did for me).

But, if you allow the same rule with more parameters, using the name of the external interface, like:
sudo ufw allow in on eth0 to any port <port> proto <protocol>

then the port appears as filtered during nmap scan.

That command would allow incoming (in) traffic on interface eth0, in my example the interface connected to the internet. For example, for allowing http traffic incoming from the internet:
sudo ufw allow in on eth0 to any port 80 proto tcp

---

