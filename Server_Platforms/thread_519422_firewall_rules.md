---
title: "firewall rules"
date: 2007-08-07
forum: Server Platforms
---

### Post by gishaust on 2007-08-07
hi,

I am in need of some direction.

I have set up shorewall with webmin and it is great I have got a couple of tutorials and worked out zones and polices. But I have one issue I don't know where to look. In the shorewall website I followed the single nic card tutorial. 

I can get it to work a treat. but I also have webmin running so I decided to add the following using webmin and all the server says is the port that 
I have assign won't work.(fw  is assigned to firewal)l 

action             source        destination

Webmin/ACCEPT	all	fw		30000(not real port)
Web/ACCEPT	all	fw

so I tried it without the port number and shorewall will start but won't  allow me into webmin when I try to access it the page just times out

Webmin/ACCEPT	all	fw
Web/ACCEPT	all	fw

can anyone give me some pointers please

---

### Post by gishaust on 2007-08-07
this subject is obviously not too clear. So as I am trying to solve my issue I will keep add to the forum I have found this site that is provided by shorewall  
 [http://www.shorewall.net/troubleshoot.htm](http://www.shorewall.net/troubleshoot.htm).

It is very explanatory  I will see how it goes 

Gishaust

---

### Post by gishaust on 2007-08-08
Anyone that wants to answer this forum is most welcome.

But if you see the answer to problem please don't tell me. Just point me in the right direction I want to try and work this out? it is now me and the computer

I have gone over the complete setup to make sure that it is correct.

I have two zones a fw for the firewall, and net is Ipv4. 
The network interface is eth0, broadcast address is auto, and options is dhcp(with out the firewall I can ping around the network and there is no issue. When the firewall is up i cannot ping as there is no rule to allow it).

default policies are
source, destination, policy, syslog, trafficlimit,
fw  	net          accept  no logs    none
net     any          drop      info     none
any     any          reject   info      none

I think believe policies apply if no firewalls rules apply to the request that are sent to shorewall.

firewall policies
action	      source   destination
Webmin/ACCEPT  all       fw
Web/ACCEPT     all       fw

Now according to the shorewall howtos the above tells me that if I request to access the server inside the network or from the net it will let me in through. But that is not happening.

So i am going to check to see if there are any errors.

I have tried the Verbosity call "shorewall -vv restart" ( this rule is creates a situation that will tells you of any small errors in your setup. It moves very quickly but I from what I can see there are no errors. I will see if there is a switch to slow it down.

---

### Post by gishaust on 2007-08-08
ok todays installment


I did a google seach for a switch that will slow down -vv restart didn't find anything.

In webmin under shorewall three is a button check the script . I did that and it says that the script is fine.

i thought today i would check the logs to ensure that the machine is ok! before i go on. So I am checking the logs of not only shorewall but others to see if there is an issue.From what I can gather about linux boxes that they are kept in /var/logs and in these I am looking for errors of some sort. To enter the log you need a text editor vi vim or nano are the ones I know. I am using nano right now for simplcity but vim is on the to do list. all logs were fine. I checked all of them. But there is no log for shorewall. So I typed in
"whereis shorewall" (i love this command it finds files and directories) I found three folders. On searching I found one of the folder has had the macros that i are asked for in the firewall. So I "sudo nano macro.Webmin" (watch it is case sensitive). but the macro port is set to 1000. But when you install webmin it asks 
you to change the port number for security.So I did to ******* sorry.Could his be the issue???.

Does shorewall have logs.

---

### Post by gishaust on 2007-08-08
quick note   I just started the server and the firewall is down but I will not let me access webmin from another computer on the network. May be a second problem. I can ping the box. It has not done this before.

---

### Post by gishaust on 2007-08-09
next installment

Well i got webmin to work and changed the port number for shorewalls macro.Webmin. Then  restarted shorewall, it still will not let me run webmin throught shorewall. So I am going to go back to trouble shooting with [http://www.shorewall.net/troubleshoot.htm](http://www.shorewall.net/troubleshoot.htm).

"shorewall debug start 2>  /tmp/trace" that is next 

Gishaust

---

### Post by gishaust on 2007-08-19
hi everyone,

I have just tried this tool and it is great it shows you the startup log traces the information of the start up . but no luck I have no errors

"shorewall debug start 2>  /tmp/trace" is the call

next is the support guide I thats the next installment.

---

### Post by gishaust on 2007-08-19
I have just found out about "shorewall dump |more" "wow wow wow"  It show past and present request of the wall how it processes it. I have found that the firewall has received requests from the internal network that I am running. I have found out
that the port that I am requesting from another computer to run webmin shorewall  is rejecting.

The out =src is 192.168.1.2   dsp 192.168.1.4  

I am not ensure what that means.  

can anyone point me in the right direction.

---

### Post by gishaust on 2007-08-20
well I have not solve the issue so I unstalled shorewall and using webmin I tried linux firewall (iptables) with in five minutes I got it to work. 

I don't know

---

### Post by enuf on 2008-01-17
Had a quick look and you state you have two zones - fw & ext
I think you need another zone for int(ernal network) as well...if you ever decide to tackle shorewall again...

---

