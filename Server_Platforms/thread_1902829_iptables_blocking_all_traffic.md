---
title: "iptables blocking all traffic"
date: 2011-12-31
forum: Server Platforms
---

### Post by plazma on 2011-12-31
Hi all,
 
I'm using ubuntu 10.4 64bit on vmware
 
I have a bit of a problem with my iptable rules and i'm wondering if someone can point me in the right direction. 
 
Anyway i've written some rules and saved them to file iptable.rules in /etc.
 
I then issue a iptables-save > /etc/iptables.rules and check the file and all the rule are saved nicely and traffic from IP's not on my whitelist just get dropped as they should. I can also run a iptables -L -v and see the rules are there and working.
 
Here are the rules i have setup (minus the actual IP's i've white listed):-
 
iptables -P INPUT ACCEPT
iptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s some.ip.here -j ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
 
I have set amount of IP's i wanted white listed then everything else gets dumped.
 
 
This works nicely for a few days or so then all of a sudden it starts dropping packets from certain IP's in my white list. These IP's are sending a fair amount of traffic to the server but i cant see why that would cause certain IP's to be blocked.
 
I do have Ossec installed but the logs arent showing any rules applied for these IP's and i have all the IP's setup in the global white list for Ossec also.
 
Can anyone point me in the right direction on what i'm doing wrong here?
 
Any advice is greatly appreciated.

---

### Post by rsvancara on 2012-01-01
I recommend using tcpdump to troubleshoot the problem.  You could also create new chains for your white listed servers to log traffic.  Either way, you need more information.

My suspicion is that your white listed servers are falling under the established/related category and then when the connections are reset at some arbitrary interval, you are seeing the connection failures.

-- 
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by plazma on 2012-01-01
Its a real pain in the butt, the server is a production server so i cant run the risk of blocking everything again.
 
For now i'm relying on other security installed to perform the task of monitoring for brute force but i'm never comfortable with log scanning etc, i'm always happier with white lists.
 
I'll have to get a another VM instance up and start trouble shooting that.
 
The odd thing is it doesnt block my IP so i'm still able to ssh into it and clear all the rules when it has happened.

---

### Post by rsvancara on 2012-01-01
Are you trying to monitor for brute force ssh attacks?  Also what services are being blocked?  Is it http, nfs, email?  

Thanks

---

### Post by collisionystm on 2012-01-01
> **plazma said:**
> Hi all,
 
I'm using ubuntu 10.4 64bit on vmware
 
I have a bit of a problem with my iptable rules and i'm wondering if someone can point me in the right direction. 
 
Anyway i've written some rules and saved them to file iptable.rules in /etc.
 
I then issue a iptables-save > /etc/iptables.rules and check the file and all the rule are saved nicely and traffic from IP's not on my whitelist just get dropped as they should. I can also run a iptables -L -v and see the rules are there and working.
 
Here are the rules i have setup (minus the actual IP's i've white listed):-
 
iptables -P INPUT ACCEPT
iptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s some.ip.here -j ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
 
I have set amount of IP's i wanted white listed then everything else gets dumped.
 
 
This works nicely for a few days or so then all of a sudden it starts dropping packets from certain IP's in my white list. These IP's are sending a fair amount of traffic to the server but i cant see why that would cause certain IP's to be blocked.
 
I do have Ossec installed but the logs arent showing any rules applied for these IP's and i have all the IP's setup in the global white list for Ossec also.
 
Can anyone point me in the right direction on what i'm doing wrong here?
 
Any advice is greatly appreciated.


iptables -A INPUT -i lo -j ACCEPT
iptables -P INPUT ACCEPT
iptables -F
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -s some.ip.here -j ACCEPT
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

your iptables file you are restoring from should look similar to this.


*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7
-A INPUT -s some.ip.here -j ACCEPT
-A INPUT -j DROP
-A FORWARD -s some.ip.here -j ACCEPT
-A FORWARD -j DROP
COMMIT

You do not want to drop all forwards.
If you choose to use a drop in your forwarding, do the same as listed above.
Input your forwarding rules and then add the drop at the end.
You should also include the logging so you can actually see what is being blocked.
you can watch the traffic with

sudo tail -f /var/log/kern.log


Look here
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

and have a look at the attachment to help you understand

---

### Post by collisionystm on 2012-01-01
also, why are you including iptables -F

-F implies you want to flush your tables

---

### Post by Doug S on 2012-01-02
With all due respect to Collisionystm, and if I understand your system correctly, you do not need to worry about the FORWARD chain at all, because that packet path is never used. The adding some logging suggestions are good to help with figuring out what is going on.
How many addresses are on the white list? I am wondering if the complete iptables rule set ends up very CPU intensive because the list is very long.
As rsvancara suggested, perhaps some issues with established connections and timeouts and the conntrack table.

---

### Post by plazma on 2012-02-02
I should have clarrified, the rules i posted there are how i actually set them up, the saved rules appear as below in the saved file.
 

I used the -F to flush all rules before setting up new rules.
 


*filter
:INPUT DROP [44:8716]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [315:64819]
-A INPUT -i lo -j ACCEPT 
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A INPUT -s IPs.start.here -j ACCEPT 
 


I have a list of 12 IPs on the whitelist
 

I havent noticed any CPU usage spikes on the system, i do graph the system and its pretty steady. There is a bit of traffic that comes from those IP's though.
 

Not really sure what is going on with this.

---

