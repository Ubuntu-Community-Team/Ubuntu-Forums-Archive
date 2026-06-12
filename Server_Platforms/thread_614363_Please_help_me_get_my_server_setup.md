---
title: "Please help me get my server setup"
date: 2007-11-15
forum: Server Platforms
---

### Post by Someone-Void on 2007-11-15
Ok, I am having the same problem as the other people... I can view my server but people outside my network can't. I am on 7.10 and I'm pretty sure I enter the wrong IP... I am unsure of how to correct this problem and I'm pretty new to all this so any help would be greatful

---

### Post by Someone-Void on 2007-11-15
Oiy! My head.... How to fix this....

---

### Post by Someone-Void on 2007-11-15
Ok I guess I should say alittle about my problem... My computer is connected to a router and I mistakenly enter the router ip instead of the computer ip... which is kinda a problem I'm betting...

---

### Post by twistedtwig on 2007-11-16
ok so we need a little more info please.

the router.. is this a modem router?  Does it get the external IP address and use DHCP to give all your machines internal IP address (like 192.168.1.1)?

What IP address do you use to view the server locally?

Do you have a domain name?  I.e. how do you want other people in the world to view your server?

as a basic guide..

what you want to have is either:

1) a modem  / modem router that forwards the External IP address to the server which needs to be firewalled (all ports are closed by default).  This means that (when you open a port, i.e. 80 for web server) people outside your lan can access it if they use your IP address.

2) if your modemrouter takes your external IP you will need to port forward each port you want anyone else to be able to see.

GL

---

### Post by Someone-Void on 2007-11-16
The router is the linksys WR54G (I think, not at home... I know it is the linksys though) It does get the external IP address and assign each computer an internal IP address.. The ip locally is 192.168.0.100
the router.. is this a modem router? I am planning on purchasing a domain name but am going to use no-ip for now.
I'm sorry for the lack of information, if there is anything else needed please ask...

Thank you in advance.

---

### Post by idiotsruleintheshowerjane on 2007-11-16
ola.

you will want to port forward  from your routers wan ip  to your server ip. if you are going to do that  as a test and this is your first try at all of this then you might want to consider to modify the web server (apache2 assumedly) conf file to listen on a non standard port, and port forward that one port back to  your internal private ip, also  known  as the nat'd ip. also, consider reading up on iptables/ipchains. some use firestarter for their firewall  front end gui. that's all good but only if you run iptables/chains and learn what firestarter is doing ----> how it actually modifies the inbound/outbound rules. anyway i am off topic.

linksys home routers  can all port forward. linksys web will have exact directions for your model. if you get a cisco the command is similar
to this:

ip nat 192.168.x.x 80 223.223.x.x 80 extendable

that sends port 80 traffic from the outside via port 80 back to
the 192.168 ip, in  this case your server. good luck. peace.

j_k

---

### Post by Someone-Void on 2007-11-17
Still only a local webserver... I think I messed up somewhere along the line... Anyone got a good guide?

Thanks in adance...

---

### Post by ruibernardo on 2007-11-17
Did you try what twistedtwig said? Maybe this helps: [http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/)

---

### Post by Someone-Void on 2007-11-17
Yes, I port forwarded... O this is no fun...

---

### Post by kesomir on 2007-11-18
to test, enter your external ip in your browser.

Make sure port 80 forwards from the router to the internal ip of your web server.

Secure the webserver properly.

---

### Post by sciurus on 2007-11-22
Normally you can't test port forwarding from within your internal network. IE, pretending your network looks like this

Gateway: WAN 1.2.3.4, LAN 192.168.1.1
Server: LAN 192.168.1.2

even if you have port forwarding from 1.2.3.4 to 192.168.1.2 set up correctly, you won't be able to access your website from 192.168.1.2 by visiting 1.2.3.4

---

### Post by WIGGMPk on 2007-11-22
I believe you might have an ISP problem and not a port forwarding issue. Some Cable/DSL providers try an force customer's into 'upgrading' their subscription to a 'commercial' account by effectivly blocking INCOMING requests to certain ports, which by default are ports that are used for specific services.

I had this issue with Service Electric (Cable Prov) and NOT Comcast (Cable Prov), so it really depends on your ISP.

For arguments sake, lets say your using 'apache2' to host your webserver. By default it is bound to port 80 of your machines IP address. For instance, if your machines IP is 192.168.1.100 and you have port 80 forwarded to that machine, but you still have no webpage displayed by typing in your EXTERNAL IP address, try typing in the INTERNAL IP of the machine.


NOTE: PORT FORWARD       NOT      PORT TRIGGERING


For instance "http://192.168.1.100/" further more, try with the port associated with the webserver "http://192.168.1.100:80". If these options dont work (usually if your on the LAN your testing from you'll be able to see it regardless of weither you have the port forwarded or not) then its most likely your ISP blocking ALL INCOMING requests on port 80.

If this is the case, its prolly safe to say that your ISP is blocking INCOMING requests on port 8080 as well. (which is usually the alternative port used in this case) If this is the case, simply change to port that you KNOW is open. Otherwise, call up your ISP and see what they allow/deny as far as hosting services.

Once you gathered more info from you ISP, troubleshooting will be a bit easier. Hope this information helped.

---

