---
title: "Iptables and UFW - some questions regarding ports."
date: 2010-11-22
forum: Security
---

### Post by zozza on 2010-11-22
I would like to clarify some information and also ask for advice regarding iptables and ufw.

The only things I have done with ufw are:

sudo ufw enable.

and

sudo ufw logging on.

The following is my understanding - please correct me if I am wrong:

1.   I have no permanently open ports on my machine because I have not installed any servers e.g. Apache.  There are times when I use Firefox or Deluge or Thunderbird when ports will be open - for the duration of those connections.  I have used Steve Gibson's "Shields Up" on the most common ports and all are "stealth".

2.   All incoming traffic will be automatically blocked by iptables / ufw unless the traffic is in response to a connection I have initiated e.g. a Firefox session. 

3.  No outgoing traffic is blocked and, in fact, there is no reason to do this especially considering that Firefox and Deluge use a wide range of ports (as shown by netstat). 

Would anyone suggest that I require a more advanced firewall implementation for example, more ports locked down?  I am directly connected to my University network (no NAT).

I have read the "Iptables Primer" (as much as I can understand) by Bodhi Zazen (thanks!) and the "UFW Community Documentation" and there are a lot of options and I wonder how necessary they are for me.

Finally, the UFW Documentation recommends to go to /etc/ufw/before.rules and in the following section change ACCEPT to DENY.  Is this necessary for me?

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
  
Many thanks!

---

### Post by zozza on 2010-11-24
bump....please!

---

### Post by endotherm on 2010-11-24
I'm no expert with IPTabs, so I can only speak to the last point about the ICMP config.
ICMP messages can give hackers information about your system, if they probe you correctly, so that is why they recommend rejecting them. you don't NEED to reject them, but it will improve your overall security from automated scans and info gathering techniques, since you don't leak any information. 

many firewall experts recomend instead of rejecting the packet (which sends a message back to the attacker) that you simply ignore the connection and let it fall into digital nothingness. not sure how that disctinction applies to IPTabs though.

I'll take a stab at your other questions
1) you are quite correct, if you don;'t have services, open ports can't hurt you. additionally, a port can only be used in one connection at a time, so your FF ports (opened for specific connections) can't easily be subverted; don't worry about them. Deluge however may be a bigger issue. how do you handle incoming connections in your config?

2/3) what you are describing is called "Stateful packet inspection" and yes, all outbound packets are allowed, whereas all incomming packets are blocked, unless they are part of an established connection (which would have had to be initialted by an internal connection outgoing ).
That is not however how IPTables is set by default. IPTables starts off with a blank ruleset, so it allows everything. 
when you install and configure UFW/GUFW turning on stateful filtering is one of the most basic settings. I'm not sure what is needed for UFW, but it;s like one checkbox to enable stateful via gufw. 

lastlly, be careful about assuming that your apps use wide ranges of ports. server apps listen on one or a small number of ports. when a request for connection comes in to the listening port, it forks it;s process establishing a new port in the dynamic range, and the connection is mapped to the new port using the RPC portmapper service. the only port that can initiate a connection is the one that is listening. the others don;t matter much. 
so if you connect to someones webserver, your packets go intitally to TCP/80 but the servers RPC service will remap your session to a higher range number like 49875. in netstat (on the server ) you will see both the listening port (80) and the connected ports (49875), but 80 is the only one that is really "open". if someone tried to send somthing to 49785 and they were not the person/app that established that connection, then the transmission would be rejected because the TCP syn and ack values are not what the 49785 expects to be in the next packet.

---

### Post by zozza on 2010-11-25
Many thanks for your detailed reply.  Much appreciated. 

> 1) you are quite correct, if you don;'t have services, open ports can't  hurt you. additionally, a port can only be used in one connection at a  time, so your FF ports (opened for specific connections) can't easily be  subverted; don't worry about them. Deluge however may be a bigger  issue. how do you handle incoming connections in your config?

My Deluge configuration has incoming ports using random ports.  I presume you would suggest I set these ports to a specific small range (6882 to 6891 is grayed out). 

> 2/3) what you are describing is called "Stateful packet inspection" and  yes, all outbound packets are allowed, whereas all incomming packets are  blocked, unless they are part of an established connection (which would  have had to be initialted by an internal connection outgoing ).
That is not however how IPTables is set by default. IPTables starts off with a blank ruleset, so it allows everything.  when you install and configure UFW/GUFW turning on stateful filtering is  one of the most basic settings. I'm not sure what is needed for UFW,  but it;s like one checkbox to enable stateful via gufw.

Yes, you are right.  I needed to do sudo ufw default deny according to the UFW Community Ubuntu Documentation.

Although it does not say this specifically I think I am correct to assume that this refers to the incoming policy - while allowing all outgoing still. 

See the first page: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

 
> lastlly, be careful about assuming that your apps use wide ranges of  ports. server apps listen on one or a small number of ports. when a  request for connection comes in to the listening port, it forks it;s  process establishing a new port in the dynamic range, and the connection  is mapped to the new port using the RPC portmapper service. the only  port that can initiate a connection is the one that is listening. the  others don;t matter much. 
so if you connect to someones webserver, your packets go intitally to  TCP/80 but the servers RPC service will remap your session to a higher  range number like 49875. in netstat (on the server ) you will see both  the listening port (80) and the connected ports (49875), but 80 is the  only one that is really "open". if someone tried to send somthing to  49785 and they were not the person/app that established that connection,  then the transmission would be rejected because the TCP syn and ack  values are not what the 49785 expects to be in the next packet. 	

I see.  And what about from the client side.  Does the following really mean I am using ports 50069, 33785, 33783, and 32769 or is the portmapper service being used also on the client side?

4833/firefox-bin
tcp        0      0 128.86.153.171:50069    87.248.112.181:80       ESTABLISHED 4833/firefox-bin
tcp        0      0 128.86.153.171:33785    77.238.187.43:80        ESTABLISHED 4833/firefox-bin
tcp        0      0 128.86.153.171:33783    77.238.187.43:80        ESTABLISHED 4833/firefox-bin
tcp        0      0 128.86.153.171:32769    173.194.36.142:80       ESTABLISHED 


Thanks!

---

### Post by zozza on 2010-11-28
bump....anyone?

---

### Post by endotherm on 2010-11-28
sorry, I thought I replied to this a couple days ago. must have gotten lost in the mail.

one thing to consider, is that it is very very hard to connect to a port that is part of someone else's connection. its called hijacking, and it is an attack on the tcp/ip stack itself. over the last 10 years however, most OS vendors have made seriously significant improvements in their IP stacks, so this kind of attack is very rare. 

so that means that if someone wants to connect to a port on your system, they are probably going to have to make their own connection, rather than attempt to connect to a port that is already part of an established connection.  

there are 4 kinds of connections/ports that you will see in netstat: 

[LIST]
[*]Service Listerner ports
[*]Service Connections
[*]Application Connections
[*]Local connections (filtered connections)
[/LIST]

Service Listener ports are your primary concern when it comes to gateway security matters. a listener port will accept incoming requests to connect to an process, so it's like the front door to your service. only a listener port will accept a request to create a connection. all the other types are Established connections. to make a listener port accessible through a statefull packet filter, you have to allow incoming connections to the port, or it will be rejected, because it is not part of an established connection. most modern routers also require you to forward the port. 

Service connections are connections initiated from the OUTSIDE, by creating a connection using the services listener port. they are established connections, so they pass through a statefull filter without trouble. that means that if you want to block them, you focus on blocking their listener, rather than the individual service connections. if you block the listener, no one can create a service connection anyway. your services may use many ports (1+ per client), or it may run all its clients within the same port/process.  

Application connections are connections initiated from the INSIDE, by contacting a remote servers service listener port. after your application requests a connection to their service, their server will either start a process to handle your request (which uses a different port than the listener as I described above), or it will start a thread within the service process for your job (which uses the same port as the listener).

Local connections are connections that exist only on your computer. they allow processes to pass information back and forth, and can only be accessed by apps on your system. on this level, they don't represent a great security risk. 

in the netstat you are showing, you have procID 4833 (FF), creating 3 outbound application connections to 2 different servers. this is likely because a modern webpage uses content off several differant servers (ad networks, analytics, embedded content, etc), and each peice requires an call to the host webservers http service. these servers appear to use a threaded approach to handling clients (MS IIS does this), so the established connection is to port 80 (not a higher range port).
I'm not sure about the  bottom most connection, since it does not appear to have an process attached to it. it may be a connection in the process of disconnecting, or it may be a process that you don't have privileges to monitor, so netstat can't provide the name (run netstat with sudo to see if that is the case). several other threads on the matter indicate that the process may have crashed (check dmesg) leaving the port open. that could theoretically be a sign of a failed remote execution attack, but is much more likely an internal error.

---

### Post by zozza on 2010-11-29
Thanks for the information - much appreciated!

---

