---
title: "tunneling"
date: 2009-12-22
forum: Security
---

### Post by cucuru on 2009-12-22
hello, I would like to have a SSL tunnel, in the same way that the kind of tunnel we get with:

ssl -L local_port:host:host_port server

How can I do it? is stunnel a good option?

Thank you. Regards

---

### Post by BkkBonanza on 2009-12-22
You can use stunnel to do the same thing as ssh tunnels except that it needs to be set up in advance on the server or by using ssh to login and set it up.

ssh offers an easier way since you can do it completely at one end with one command. ssh is also more flexible since you can use it as a proxy as well.

As far as security I believe they are both comparable and use similar levels of encryption. I haven't seen any info that indicates ssl is better but there may be some applications that natively support ssl and hence may work more directly with stunnel.

Do you have a particular application in mind you want to make work?

As far as how to do - well, there are lots of examples on the stunnel.org web site. Check that out.

---

### Post by cucuru on 2009-12-22
thank you for reply. I have to use a SSL tunnel, I've found this example:

[http://www.stunnel.org/examples/generic_tunnel.html](http://www.stunnel.org/examples/generic_tunnel.html)

I want to do :

ssl -L local_port:host:host_port server

so, do I need 3 connexions?  I suppose one from user to server, one between 2 differents ports in the server and the last one from the server to the host.

Regards

---

### Post by BkkBonanza on 2009-12-22
The syntax you show above is for ssh not ssl.

stunnel uses a syntax like, (using the same parms as above)

stunnel -d local_port -r host:host_port

I don't know why you would need 3 connections. You run stunnel on ther server, and you run it on the client. That creates your tunnel. Now you connect to your local port which tunnels to the server where it's already connected to the destination port there.

---

### Post by cucuru on 2009-12-22
Hello, I know that's ssh, it was just an example, what I want to do.

Maybe, I didn't explain my problem very well.

I have 3 computers, the origin, the destiny and a intermediate one, wich connects origin and destiny. 

With the ssh example, I execute it in the origin, host is the destiny and the connection is the server.

Sorry about the misunderstanding 

Thank you. REgards

---

### Post by HermanAB on 2009-12-23
Howdy,

SSH also has a Socks Proxy feature which works with tsocks on Linux and Windows (this is a kind of VPN).  Read the ssh man page and look for the -D option.  It may be handy one day.  I sometimes use it to tunnel Firefox, email and Skype.

---

### Post by cucuru on 2009-12-23
Thank you for your reply, the problem is that I need a SSL tunnel it is for the number of connections, so, it is not useful for me.

Do anybody knows how to make a SSL tunnel?

Regards!

---

### Post by BkkBonanza on 2009-12-23
Your description of what you want is still quite unclear. 
Provide details of what you want to connect and how and I can provide a more detailed reply. It really sounds like you need a proxy not just a tunnel.

---

### Post by cucuru on 2009-12-23
I'm sorry, I'll try again.

I have 3 different computers, in 2 different networks.

Computer1 in Network1
Computer2 in both of them
Computer3 in Network2

I want a tunnel between Computer1 and Computer3, but it is necessary use Computer2 as "linker"

Did I explain it well?

Thank you. 

Regards

---

### Post by BkkBonanza on 2009-12-23
stunnel can be used but you'll have to run it on all three computers for each port you want to forward. 

What is the reason for not using ssh? Because ssh can do this with one command on one computer for any number of ports and is just as good as ssl. It can forward ssl connections too, so if you are just thinking you need to connect a https web page then it can do that. 

If there is some arcane "legal" reason you are forced to use stunnel then I'll work out some example commands for you.

---

### Post by cucuru on 2009-12-23
I want a SSL tunnel because it's faster in my case. Is stunnel the best way to make a SSL tunnel?

I'm trying now with the basic example in the web site, but it doesn't work.


Thanks 

Regards

---

### Post by BkkBonanza on 2009-12-23
I don't know if it's the best but it's one way.
I have no idea why you think ssl is faster than ssh but you seem convinced it's what you want. Can't tell you otherwise so try like this,

CompA
stunnel -c -d 8080 -r CompB:8080

CompB
stunnel -p /path/to/cert.pem -d 8080 -r CompC:8081

CompC
stunnel -c -d 8080 -r CompB:8081

Actually I'm not sure if you will need 2 instances of stunnel on CompB or one can handle both ends.

To do the same thing with ssh,

CompA
ssh -r -D 8080 user@CompB -N

Tell your local program to use SOCKS5 proxy localhost:8080 and connect to CompC:8080.
All traffic between CompA and CompC will be encrypted and tunneled via CompB.

---

### Post by cucuru on 2009-12-23
Thank you!! very useful your information.

I don't know how to change the topic to solved, but it is. 

Regards

---

### Post by BkkBonanza on 2009-12-23
Good. If you want the tunnels to start at boot you can add the line to /etc/rc.local for each machine.

---

### Post by cucuru on 2009-12-23
Perfect! I've just had another question, could I have more than one computer C in the same port? they are CompC1 and CompC2 Would I make this with this sentences?: 

CompB
stunnel -p /path/to/cert.pem -d 8080 -r CompC1:8081
stunnel -p /path/to/cert.pem -d 8080 -r CompC2:8081

CompC1
stunnel -c -d 8080 -r CompB:8081

CompC2
 stunnel -c -d 8080 -r CompB:8081

Regards

---

### Post by BkkBonanza on 2009-12-23
No, I don't think so. stunnel can't split or duplicate the tunnel traffic. You would need seperate tunnels using different ports. You may be able to extend the tunnel from C1 to C2 though. If you can monitor the traffic on C1 and pass it on to C2 that may work. I've never tried anything like that but it sounds feasible.

Having multiple ports open is something that SOCKS is designed for - it is a dynamic proxy protocol where the program communicating can send down the [dest : port] it needs dynamically as it runs but still only use one tunnel.

---

