---
title: "vb guest cannot ping another guest, but can ping host"
date: 2009-09-06
forum: Virtualisation
---

### Post by pctlinux on 2009-09-06
vbox 3.0 running on host jaunty (ubuntu 9.04)
guests  vmXP is  windows-xp, vmW3 is windows 2003.
bridged network setting on both guests.

vmxp and vmw3 can ping host jaunty
host jaunty can ping vmXP and vmW3

BUT **vmXP cannot ping vmW3 and vice versa**. (although both vms can ping to gateway and see ip address, but time out)
C:\>ping vmW3
  Pinging vmW3.gateway.2wire.net [192.168.1.78] with 32 bytes of data:

  Request timed out.
  Request timed out.
  Request timed out.
  Request timed out.

any help much appreciated!  (i need a web app in vmXP to connect to mysql in vmW3).

---

### Post by Perryg on 2009-09-06
Firewall?

---

### Post by pctlinux on 2009-09-06
Perryg, firewall it is, thanks!  i turned off firewalls on the guests, and now they can now ping each other.

dumb question: are these vms now vulnerable to internet attacks?  (this is a home network, host jaunty and all devices including swtiches are connected to an att-uverse router)

---

### Post by Perryg on 2009-09-06
Well I would think that these PC's are using private addresses and since that is not routable it really doesn't matter that much unless you set the router to port forward to the non-routable IP addresses.  Either way having multiple firewalls is not necessary IMHO and causes more problems than they are worth.  Just make sure that your router firewall is active and configured properly and you should not have a problem.

---

### Post by jocampo on 2009-09-06
> **pctlinux said:**
> Perryg, firewall it is, thanks!  i turned off firewalls on the guests, and now they can now ping each other.

dumb question: are these vms now vulnerable to internet attacks?  (this is a home network, host jaunty and all devices including swtiches are connected to an att-uverse router)

Of course they are :-) ... if you got a public IP anything can happen. In fact, you are using a similar configuration that I got at home with my ATT Uverse Router. I got VirtualBox on a Headless server. Crated a small Ubuntu Server virtual machine on top of my physical Ubuntu Server and I put that one on a DMZ zone. Hours later, bunch of jerks were trying to hack my vbox 'cause was using default ssh port.

What you can do, for your home lab, make sure everything is behind the ATT router; that way, you'll be safe. But if you exposed something via DMZ you are taking the risk that someone can jump from there to something inside your home lab so, use ufw. I put ufw on my WWW server and block everything but 80 and the port I am using for ssh (so I can manage remotely)

---

### Post by pctlinux on 2009-09-06
im learning quite a bit Today...gleaning from Perryg and Jocampo's reply, i think my vm guests are still ...'safe' as they're behind and protected by the att uverse firewall.  thanks to both of you.

please understand my firewall talk is an art not a science :-?.

eventually i want to be able to run my web app from anywhere in the world. i dont know the mechanics to get there yet. some of the basics i need to get past are:

1. how to put my web app on the DMZ? what does it exactly mean? for example, (1) i want to run [http://www.vmXP.com/myWebApp](http://www.vmXP.com/myWebApp) from oversea,  what do i need to do?  (2) i want to run connect to mysql on \\myHomeNetwork\vmW3  and execute a sql query ,  what do i need to do?

2. what is this dynDNS? does it work with linux/Ubuntu?

---

### Post by jocampo on 2009-09-07
> **pctlinux said:**
> im learning quite a bit Today...gleaning from Perryg and Jocampo's reply, i think my vm guests are still ...'safe' as they're behind and protected by the att uverse firewall.  thanks to both of you.

please understand my firewall talk is an art not a science :-?.

eventually i want to be able to run my web app from anywhere in the world. i dont know the mechanics to get there yet. some of the basics i need to get past are:

1. how to put my web app on the DMZ? what does it exactly mean? for example, (1) i want to run [http://www.vmXP.com/myWebApp](http://www.vmXP.com/myWebApp) from oversea,  what do i need to do?  (2) i want to run connect to mysql on \\myHomeNetwork\vmW3  and execute a sql query ,  what do i need to do?

2. what is this dynDNS? does it work with linux/Ubuntu?

OK... for the DMZ zone, you need to use the ATT&T Firewall conf app, which you can reach internally putting this on your PC: [http://gateway.2wire.net/](http://gateway.2wire.net/). The password is on your Router.

A DMZ is a zone where you put your PC exposed to internet but still has some connectivity to your LAN. You can do that easily using the ATT&T Firewall app via web. But please, DO NOT DO THAT NOW if you don't really need it. Like Perry explained to you, right now, your PCs behind the LAN are using private IPs and protected by the AT&T router/firewall; whatever you put on the DMZ is going to be exposed and using a Public IP. BTW, I believe you can put just one machine on the DMZ zone with AT&T.

For a WebServer you need to install Apache but 1st and then you must pay and register your domain name. Depending of the company prices varies from 10 to 30 bucks per year. Once you got your DNS name, you point it to your Apache webserver, using the public IP and voila ... it will display your website on internet.

---

### Post by pctlinux on 2009-09-07
thanks Jocampo...fwiw, i'm an old school MS windows, iis, asp, sql server...it career ](*,)...i wanna retool myself in opensource wares linux/ubuntu, apache, php, mysql...

let me dumb down what i need to do:

1st/ develop and test my webb  app internally (3-6 months). 
       - hold off putting my vms out on DMZ
       - install apache on vmW3
       - install mysql on vmW3
       - install php-equivalent of MS vstudio on vmXP (or just use notepad)
       - dive into php and mysql ...

2nd/ fully understand implication of putting a pc d to the DMZ
       - if i expose the att router to the internet
            - can i just expose the vmW3 vm machine
            - or will my entire home network be exposed?

3nd/ put my web site out to DMZ
       - research and install a virus protection sw for the apache server(vmW3).i assume i need this
       - research and install a 'network intruder/hacker'   monitor sw
       - register my domain name
       - expose the apache server
       - have someone out there on the internet fire up my site url 

 any holes in this dumb down plan? 
i realize i'm scope creeping (from a vbox post to this dumb down to-dos)!

---

### Post by jocampo on 2009-09-07
No problem, MCSA, MCTS SQL2005 and SQL DBA for a major IT company :-)

But I love Ubuntu and if you learn, will expand you knowledge and you'll be able to see the two side of the coin 'cause I know for experience that not all Microsoft software sucks. Anyway, I do not want to start the flame, lol ...so, let me give some hints...

1. Do not pay for the Domain Registration yet!
2. You can setup a LAMP (Linux Apache MySQL Python) and play internally on your LAN, before put anything online.
3.Securing you APACHE is a good idea, got couple of links that I'll send you.

Regarding the DMZ zone, it will NOT expose all your machines to the outside world, just the one you put there. For instance: I have like 10 VMs (not all of them are on all the time, of course) but one of them resides on the DMZ zone. It hosts my webpage and runs Apache so needs to be on the DMZ and has a public IP. The remaining machines including my physical laptops, are behind the AT&T router and they run on private IP address. They are safe 'cause I am not doing port forwarding but it is always useful to run "ufw" on them and not installing ssh for remote connections if you don't need it.

---

### Post by pctlinux on 2009-09-07
good to know i can select which machine(s) to expose. learned what LAMP stands for! python, ssh, ufw ... sound like greek to me, i'll save learning those for another day! 

so far i like ubuntu, although still in all-things-ubuntu/linux.101 stage. i like the fact that after 4 months my ubuntu machine still runs fast, unlike windows where eventually a format and reinstall is required to get rid of the bugs in the registry!  confident i'll make it to 102 series. thanks again Jocampo for your pointers, have a great short workweek. till the next weekend.:popcorn:

---

