---
title: "Dyndns.org domain nees to go to localhost"
date: 2009-01-01
forum: Server Platforms
---

### Post by Stoneface on 2009-01-01
I have been at it the entire day. trying to get my new free dyndns.com domain to go to my Ubuntu server. I have googled until I was blue in the face and tried many different setups in my d-link DIR-300 Wireless router and /etc/hosts file. But to no avail. 
Does anybody know a good tutorial to get my domain name to go to my localhost? Now it goes to the router. I have added the dyndns domain name to the router configuration so it keeps on updating dyndns on my current external dynamic ip address. That works. But now everyone is being redirected to my router. What do I need to add in /etc/chosts and what do I need to change in the router preferences to get my domain name to go to my local host?:(

---

### Post by volkswagner on 2009-01-01
In your router disable remote access.  Not sure on that particular model.  You also need to forward ports to the servers internal ip.

---

### Post by Stoneface on 2009-01-01
Remote management was turned off from the begining so I guess that is not the issue here.
I understood that my internal ip needs to be static while d-link is running DHCP. How do I do that?
When I forward http 80 to my internal ip I get a time-out going to the domain name...
When I type dmesg I see my router is trying to connect to my sever's internal ip address...but no success though.

---

### Post by Hobgoblin on 2009-01-01
What's your server's IP address (on your internal network)?

---

### Post by Stoneface on 2009-01-01
@Hobgoblin 192.168.0.25 . I made it a fixed internal ip in my d-link wireless router now.

---

### Post by volkswagner on 2009-01-01
To set a static ip:

Edit /etc/network/interfaces

here is a sample from my server

```
sudo nano /etc/network/interfaces
```


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.128
        network 192.168.1.1
        broadcast 192.168.1.127
        gateway 192.168.1.1
```

Notice "static" above , replace DHCP on previous version for this file.

Save the file and restart networking, for change to take effect.

```
sudo /etc/init.d/networking restart
```

When assigning an address use an IP outside the range of your DHCP server (but still in the range of your subnet) to avoid IP conflicts in the future.



Have you verified a working internet connection on the server?  An easy confirmation is to run host.

```

host google.com

```

You should get a list of Google's name servers IP addresses.  This is a good practice after editing your /interfaces file.

---

### Post by Stoneface on 2009-01-01
This is my interfaces file:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

Do I need to replace the text starting auto dsl-provider by your text plus my ips?

---

### Post by Stoneface on 2009-01-01
new interfaces:

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.25 (fixed internal ip)
        netmask 255.255.255.0
        network 192.168.0.1
        broadcast 192.168.0.255
        gateway 192.168.0.1

host google.com did show Google's name servers. Still I don't seem to be able to connect..:(

---

### Post by volkswagner on 2009-01-01
If you can access your sites on your local LAN, the issue is most likely the router.

You may need to check the security setting on the router.  I am not familiar with that model.

For my setup I have the following _disabled_
[LIST]
[*]Block Anonymous Internet Requests
[*]Filter Multicast
[*]Filter Internet NAT Redirection
[/LIST]

Please realize I am no security Guru.  I have no Idea the impact.  I just know the above lets my host at home.

---

### Post by bluefrog on 2009-01-02
If you are trying all this from your machine from inside your network, there is a good chance for everything to be ok since a long time.

The thing is you cannot loopback: home your-router --> outside --> your-router home.
Find someone to test it from outside.

If other people says the opposite, they are much welcome to give PRECISE details on how they do.

---

### Post by volkswagner on 2009-01-02
> **bluefrog said:**
> If you are trying all this from your machine from inside your network, there is a good chance for everything to be ok since a long time.

The thing is you cannot loopback: home your-router --> outside --> your-router home.
Find someone to test it from outside.

If other people says the opposite, they are much welcome to give PRECISE details on how they do.

Disable NAT is the short answer.  With my Linksys WRT54G, I can do exactly as you say.

If I enter my ISP provided ip address or domain, in FireFox, I get my default website (server is on my LAN behind the same router).   If I am wrong, than the router must be providing a direct port forward to the server.  I would say not because if I manually change my ip at dyndns and use domain names I can't access my sites locally.

May not be the detail you were after, but not sure what else to say.  I am still a NOOB.

---

### Post by johndoe75 on 2009-01-02
I've created a dynDNS domain yesterday,

What I did was give my home server a static IP like mentioned before, defined my external IP with my new dynDNS domain,
installed the dynDNS updater,

then in my router, I've defined my home server's static IP as DMZ host to get passed the router from a remote location.

Be warned, I'm a noob :D I just set up my first server ever yesterday. 
So do verify with other's if my solution is correct ;)

---

### Post by hrod beraht on 2009-01-02
> **johndoe75 said:**
> then in my router, I've defined my home server's static IP as DMZ host to get passed the router from a remote location.

:shock:
Putting your server in the DMZ only serves to expose it totally to the internet as if it's on the other side of the router. With DMZ enabled, the Router firewall protection of your server will be disabled.
It's unnecessary to do that. The correct solution is to forward the ports you need in your router setup.

After giving your server a static ip, you can then forward the ports for whatever services you need (e.g. port 80 for http) in your router setup and forward them to the static IP of your server (e.g. 192.168.1.150). So that way, when an http request comes in from the internet, your router will send the request to the specified ip of your server.

Bob

---

### Post by randyks on 2009-01-02
You won't be able to reach a dyndns (or any domain name) address pointed to a computer inside of your lan from another computer on the lan. There are, I am sure, big technical reasons for this, but I do not know what they are. You will need someone outside of your lan to test it for you, or find an unsecured wireless network to use (my neighbors suddenly became unsecured for some reason). You can edit the hosts file to point the name at the internal ip, if you want it to work locally.

---

### Post by hrod beraht on 2009-01-02
> **randyks said:**
> You won't be able to reach a dyndns (or any domain name) address pointed to a computer inside of your lan from another computer on the lan.

Sure you can; I'm doing it right now. Dyndns doesn't point to computers within your LAN. They point to the external IP address of your *router* and the router then forwards the port to the appropriate local address (e.g. 192.168.1.100).

The purpose of a Dyndns account is because your ISP may change your address periodically; the internet IP address of your router, i.e. the 'outside' IP address. But the internal LAN address of your computer will always be 192.168.1.XXX (or similar, and may be either static or changing if you use DHCP). Once Dyndns is set up and your router configured properly to forward the appropriate ports, you can access your server all day and night from either outside or inside your LAN because it's resolving the address via basic DNS.

Bob

---

### Post by randyks on 2009-01-02
I am sorry. I was under the impression that the only way I could make it work was to edit the hosts file and add a pointer, like so.

192.168.0.135	patterson.webhop.net

With that added I can access my server from inside the lan from my windows box using the domain name. Without it I cannot. Please explain to me what I am missing.

---

### Post by johndoe75 on 2009-01-02
> **hrod beraht said:**
> :shock:
Putting your server in the DMZ only serves to expose it totally to the internet as if it's on the other side of the router. With DMZ enabled, the Router firewall protection of your server will be disabled.
It's unnecessary to do that. The correct solution is to forward the ports you need in your router setup.

After giving your server a static ip, you can then forward the ports for whatever services you need (e.g. port 80 for http) in your router setup and forward them to the static IP of your server (e.g. 192.168.1.150). So that way, when an http request comes in from the internet, your router will send the request to the specified ip of your server.

Bob

Thank you for that golden pointer!:KS
Changed it right away.

---

### Post by xmagixx on 2009-01-02
erhm as someone wrote "disable NAT" 
dont have to that. just forward port 80 from router to the computer ip that runs the service. 
and if your useing ddclient to autoupdate the ip at dyndns.org
to get your ip from router instead of local 
use this

in your /etc/ddclient.conf
comment out the line
#use=if, if=eth0
and below write
use=web, web=checkip.dyndns.org/
and viola
if forward is setup ok then you should be op and runing

---

### Post by hrod beraht on 2009-01-02
> **randyks said:**
> I am sorry. I was under the impression that the only way I could make it work was to edit the hosts file and add a pointer, like so.

192.168.0.135	patterson.webhop.net

With that added I can access my server from inside the lan from my windows box using the domain name. Without it I cannot. Please explain to me what I am missing.

If your Dyndns is set up correctly and your router has the appropriate port forwarded, you should be able to reach your server via the domain name system (DNS) just like any other web site.

Basically, here's how it should work; when you put [http://patterson.webhop.net](http://patterson.webhop.net) into your browser address bar, that domain name is translated into an IP address. Let's assume it's 1.2.3.4
Now this IP address should be, through Dyndns, the IP address of your router, i.e. your external IP address, not to be confused with your internal LAN addresses which are all  192.168.X.X

Now Dyndns should know the IP address of your location and when there is a request for [http://patterson.webhop.net](http://patterson.webhop.net), it will be translated into 1.2.3.4 and go to your location. There it will hit your router. In fact, the 1.2.3.4 address is the IP address of your router. So, that http request hits the router and - assuming you have port 80 properly forwarded - your router then forwards the http request to your LAN IP address of 192.168.0.135 which is your server. Your server gets the http request and processes it with whatever web server you have running, such as Apache.

Essentially, I think your question has to do with accessing your server from inside and outside your LAN. What I was trying to point out was that inside or outside your LAN is irrelevant if Dyndns is properly translating the IP address for [http://patterson.webhop.net](http://patterson.webhop.net) and your router is properly forwarding the port, because then your web server is just accessed through DNS like any other web site.

Since you say that you can't access your server without the hosts file edit, then that simply means that either your Dyndns address isn't resolving correctly (it should NOT point to 192.168.0.135. it should point to internet IP address of your router), or your router isn't forwarding the port.

Bob

P.S. I just tried [http://patterson.webhop.net](http://patterson.webhop.net) and it is up. :)

P.P.S. I'm always security conscious with my server and don't like giving any bad-guys more information than they need. So with that in mind, you may want to consider paring down your [[COLOR="Blue"]ServerTokens[/COLOR]]("http://httpd.apache.org/docs/2.2/mod/core.html#servertokens") setting to Prod as yours is currently kind of wordy :)
> Server: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ruby/1.2.6 Ruby/1.8.7(2008-08-11) mod_ssl/2.2.9 OpenSSL/0.9.8g

---

### Post by randyks on 2009-01-02
I'll do that. My wife says I am kinda wordy myself, so no doubt my server would be.

---

### Post by Stoneface on 2009-01-07
Well I still don't have outside acces to [http://localhost:81/](http://localhost:81/) or [http://192.168.0.101:81/](http://192.168.0.101:81/) (WAMP Server) I have forwarden port 80 to port 81 and ip address 192.168.0.101:81. But when I access mattias-lab.dyndns.org or 193.138.70.59 I get a 110 time-out...

---

### Post by volkswagner on 2009-01-07
> **Stoneface said:**
> Well I still don't have outside acces to [http://localhost:81/](http://localhost:81/) or [http://192.168.0.101:81/](http://192.168.0.101:81/) (WAMP Server) I have forwarden port 80 to port 81 and ip address 192.168.0.101:81. But when I access mattias-lab.dyndns.org or 193.138.70.59 I get a 110 time-out...
 
When I try the your domain name I get a blank page, no time out, it says done.

When I try the your ip I get a time out.

You say you are forwarding port 80 to port 81, then apache would need to be listening on 81 in ports.conf.

Are you sure your ISP is not blocking traffic?  Firewall?

EDIT:  If your router is forwarding port 80 to port 81, you then need to forward port 81 to 192.168.0.101 not 192.168.101:81

I guess you have apache2 listening on port 81 if it works internally...

---

### Post by Stoneface on 2009-01-07
In httpd.conf I found :
 Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses.
#
#Listen 12.34.56.78:81
Listen 81

I have emailed my ISP on port blocking yesterday and today. No reply yet.

---

### Post by volkswagner on 2009-01-07
You can try an online port checker from inside your lan, like [canuseeme]("http://www.canyouseeme.org/").

---

### Post by Stoneface on 2009-01-07
[www.canyouseeme.org:](www.canyouseeme.org:)
Error: I could not see your service on 193.138.70.59 on port (80)
Reason: Connection refused
So I guess it is my ISP?

---

### Post by ProfDecoy on 2009-01-07
In reading the issue, the inbound connection could be blocked by your ISP.  Some ISPs don't like people "hosting" web pages on "personal" internet connections and want you to pay extra for a business or commercial connection.

I'd try changing the listening IP on your router to something like 8080, or 8888 (more or less "standard" non-standard HTTP ports) and see if the same thing happens.  If the inbound still appears to be blocked, try changing it to a random high-number port.  Take a look at the firewall logs on your router to see if the traffic is even making it to it.

I assume that you're able to pull up the page just fine on another system on your local network using the internal IP?

---

### Post by volkswagner on 2009-01-07
> **Stoneface said:**
> [www.canyouseeme.org:](www.canyouseeme.org:)
Error: I could not see your service on 193.138.70.59 on port (80)
Reason: Connection refused
So I guess it is my ISP?

As ProfDecoy said you will need to host on a non standard port.  Verify with canyouseeme ports like 8080.

With your ISP forwarding port 80 to 8080 wont work.  Your outside browsers will need the port specified as part of the url.

mattias-lab.dyndns.org:8080

---

### Post by Stoneface on 2009-01-07
I can access the sever internally (LAN) I am trying to contact my Russian ISP to ask questions about their port policy. I hope to get some answers soon. They are not replying quickly to my em-mail including a translation into Russian ( Google translate)...

P.S. canyouseeme.org: Error: I could not see your service on 193.138.70.59 on port (8080)
Reason: Connection timed out

---

### Post by ProfDecoy on 2009-01-09
The latest result looks like something isn't listening properly, since the attempt timed out.  The first one was being blocked/denied.

---

### Post by Stoneface on 2009-06-09
> **ProfDecoy said:**
> The latest result looks like something isn't listening properly, since the attempt timed out.  The first one was being blocked/denied.
Hi there again. I let this rest for a while. Still struggling with my router and port forwarding.

What do you mean by not listening properly? On my router I get
```
Error: I could not see your service on 193.138.70.59 on port (49156)Reason: Connection timed out
```
while I have opened port 49156 for any traffic type under advanced > application rules in my D-Link DIR-300....

---

