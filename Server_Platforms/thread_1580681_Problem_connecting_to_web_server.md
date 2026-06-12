---
title: "Problem connecting to web server"
date: 2010-09-23
forum: Server Platforms
---

### Post by cruizer8 on 2010-09-23
I am having a problem with my web server that I just can't seem to figure out.  When I try to connect to my website remotely, the connection always times out.  I recently moved my server to a new location with a new router, and I could access the web server before this move without any issues.

I know apache is working properly because I can access it locally from within the network.  I have also set up port forwarding on the router and have confirmed that it works with ssh to the server.  Also, using the open port tool from dyndns.com, it shows the port as being open and not blocked.

I am running out of ideas on how to fix it.  Can someone help me?

---

### Post by scrooge_74 on 2010-09-23
Did you forwarded the web port (I know it sounds like a dumb question), the port may look open because is open to allow your traffic in and out when is generated inside your network. 

Also the port could be open so ISP router can be access from their site

---

### Post by cruizer8 on 2010-09-24
The router is setup to forward ports 80 and 22 for web and ssh, respectively.  The ssh works without issue, its only when I try to connect to the web server that the connection times out.

---

### Post by arrrghhh on 2010-09-24
Did you change providers at all?  It's possible your provider is blocking it...

Also, did you check the firewall on the Ubuntu box?  Although if open port tool shows its open... Hrm.

---

### Post by cruizer8 on 2010-09-24
I have changed service providers.  The router has a remote access feature that allows me to set the port, so I set it to port 80 to test if the provider was blocking it.  I am able to access the router remotely, so the provider must not be blocking it.

As far as a firewall, I haven't touched it in the move and it was working before the move.  I will have to go back in and see if there is a problem there, but I don't believe there is.

---

### Post by arrrghhh on 2010-09-24
Well it seems you've confirmed everything... Perhaps a DNS issue?  Can you hit it using the WAN IP instead of the DNS friendly name?

Be sure to change your router config back as well ;)

---

### Post by cruizer8 on 2010-09-24
I attempted to connect using the WAN IP but still a no go.  I also threw the server into a DMZ to see if that made a difference, but again no luck.  The only other thing I can think of to try is to set up a temporary apache server on another computer and see if that works.
 
Thanks for your help so far.

---

### Post by BobVila on 2010-09-24
Can you hit the web server from INSIDE the remote network? Before you go through the trouble of setting up another one, see if you can exclude a misconfiguration. Signs seem to point to filtering, though.

---

### Post by arrrghhh on 2010-09-24
I can't think of anything off hand that would prevent machines connecting to apache from the WAN but allow connections from the LAN... but stranger things have happened.

---

### Post by BobVila on 2010-09-24
> **arrrghhh said:**
> I can't think of anything off hand that would prevent machines connecting to apache from the WAN but allow connections from the LAN... but stranger things have happened.

If the ISP is blocking port 80 traffic, it seems reasonable to me that he'd still be able to hit the server internally. If OP can't connect from inside the same network as the apache server, though, then there may be misconfiguration afoot.

---

### Post by cruizer8 on 2010-09-24
I am able to access the website locally from the server as well as from another computer on the same network as the server.

---

### Post by SeijiSensei on 2010-09-24
What do you see in apache's logs? /var/log/apache2/access_log and error_log might have some useful information.  Does it register attempted connections from external IP hosts?  Or do you only see connections from your internal network?

You're sure external machines can resolve the name your.host.name correctly?  You can ping and ssh from remote machines but not use HTTP, yes?  Try using telnet on a remote host and run "telnet your.host.name 80"?  Does the server reply?

Did the server's IP address change in the move?  Do the router and server now use the same pair of addresses to communicate on the inside network as they did before?

I'd look carefully at your apache configuration files in /etc/apache2 and the apache logs to see if you're accidentally blocking connections from the router.  Take a look at all the allow/deny statements.  Do any of them limit access only to hosts on your internal network?  Is the server listening for HTTP requests on all interfaces by using *:80 in all <VirtualHost> declarations?  Does the Listen directive in ports.conf specify an IP address as well as a port number?  Does that address correspond to the server's address in its new environment?

Does this server run its own firewall?  Does the firewall permit incoming connections from the router's IP address?

How about opening another port on the router for testing like 8888 and forwarding that to the server's port 80?  Now see whether you can hit http://your.host.name:8888/.  If that works, and 80 doesn't, something fishy is going on with this router and/or your ISP.

---

### Post by cruizer8 on 2010-09-24
I took a look at the apache logs and it shows that it isn't getting any requests from the outside, only from the inside. I then decided to change the outside port that points to the server. After I changed it, I was able to access the web server from that port without a problem. The only thing I am concerned with is that I had already tried changing the ports yesterday and it did not work. 

I used telnet to try to access the server on port 80 and the server did not respond. 

Also the server has a different internal IP then it did at the old location but I am also using a different router. Does it matter to apache what the servers IP is?

---

### Post by arrrghhh on 2010-09-24
Shouldn't, but it does matter to your router for port forwarding.  I assume you got that in order already.

So maybe there's something else butting heads... is there ANYTHING else on your LAN that could be using port 80?

---

### Post by SeijiSensei on 2010-09-24
> **cruizer8 said:**
> Also the server has a different internal IP then it did at the old location but I am also using a different router. Does it matter to apache what the servers IP is?

It would if there are any access restrictions being enforced by Apache, but you'd see those errors in the logs.

So let's go back to the router.  If you remove the port-forwarding rule, and turn off external access to the management console on port 80, what do you see when you try connecting to the site from a remote location?  It should simply time out; is that what happens?

It really sounds like your ISP is getting in the way here.  Might I ask if servers are allowed under the Acceptable Usage Policy for the type of ISP account that you have?  If the AUP forbids servers, the ISP might enforce this rule by hijacking or blocking port 80 using a method outside your control.

---

### Post by cruizer8 on 2010-09-24
Okay, so I kind of solved the problem thanks to SeijiSensei.  The conflict occurs when remote access for the server is enabled, regardless of which port it is set to.  As soon as I disabled it, the website came right up.

Now the only issue is that I no longer have remote access to the router.  Is there some way to bypass this?  The router is a Belkin F5D9230-4 v2.

EDIT: I decided to restore factory settings on my router and start over to see if it would change anything and lo and behold everything somehow works now without issue.  Must have just been a bad configuration file or something on the router.

---

### Post by scrooge_74 on 2010-09-24
yup most likely, usually when you tell a router to forward port 80 then te router takes port 8080 or some other port as its remote access port

---

### Post by SeijiSensei on 2010-09-24
Here's a simple solution that might work.  Can you forward a port on the router's external IP to a port on its internal address?  Say the router's inside IP is 192.168.1.1; can you proxy external traffic on an arbitrary port like 8888 to 192.168.1.1:80?

If not, here's a more complex, roundabout solution that should work.  You can implement this idea with iptables, but I'm going to suggest using a small, free application called "tcpproxy" instead.  As you might deduce from its name, it accepts inbound traffic on a local port and sends it to a port on another IP address.  

I've used version 1.1.9 for quite some time now.  It works as advertised and is quite reliable.  There's a 2.0.0 "beta" version out there that won't compile for me in Ubuntu.  Here's a link to the 1.1.9 source code: [http://www.sourcefiles.org/System/Daemons/Proxy/tcpproxy-1.1.9.tar.gz](http://www.sourcefiles.org/System/Daemons/Proxy/tcpproxy-1.1.9.tar.gz).

Download this to your web server, unpack it and compile by typing "make" in the source-code directory.  You'll need to have installed the build-essential and ctags packages: 'sudo apt-get install build-essential ctags'.  You'll probably see some warnings, but they can be safely ignored.

When it's finished type "sudo make install" which will place the binary into /usr/local/sbin/ with appropriate privileges.  

Now, on the router, forward an arbitrary high port to an arbitrary high port on the web server (can be the same or different).  Finally, on the web server, use tcpproxy to forward traffic arriving on the local arbitrary port to port 80 on the router's internal IP.  If we let 8888 be the arbitrary port, you'd set up the proxy like this:

sudo /usr/local/sbin/tcpproxy -b 8888 router.internal.ip.address:80

This "binds" the proxy to the local machine's port 8888 and sends all traffic it receives there to your router's internal web port.  Thus external connections to port 8888 on the router will be forwarded first to the web server's port 8888 whereupon they will be rerouted to the router's management console on its internal port 80.

Now I do have to ask, though, why you need external access to your router?  Most of the time, once they're configured, routers don't need much further attention.  Giving outsiders the opportunity to talk to your router's configuration page is a [bad]("http://www.theregister.co.uk/2009/06/01/linksys_router_remote_takeover/") [idea]("http://securitytracker.com/id?1014493") unless you have really strong passwords.  Putting it on an arbitrary port helps a little ("security through obscurity"), but a diligent remote port scanner will find 8888 with little trouble and probably deduce from the server's response what kind of device it is and go from there.

Documentation for tcpproxy is via its "man" page; type "man tcpproxy" to see it.

---

