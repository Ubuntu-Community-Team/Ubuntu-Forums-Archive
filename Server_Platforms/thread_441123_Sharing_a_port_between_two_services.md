---
title: "Sharing a port between two services"
date: 2007-05-12
forum: Server Platforms
---

### Post by Joe Jarvis on 2007-05-12
Is it possible to share a port between two services, letting software decide which service to send each packet to?  My employer has a restrictive firewall that requires me to open an SSH tunnel on either port 80 or 443 to my home, but I need these ports for HTTP and HTTPS.  I only have one static IP address at home.

---

### Post by craigp84 on 2007-05-12
Yes and No.

Officially the answer is no. But i work around this by having sshd listen on port 7443 and my web server on 443.

I then have a firewall (iptables) rule which looks for traffic to port 443 originating from my work's IP subnet, and internal reroutes the packet to port 7443.

This means when anyone connects from anywhere apart from your work, they see the web server, but when you connect from your work, you get sshd.

If you need to access the webserver, you can do port forwarding over ssh anyway:

```
ssh -p 443 -L443:127.0.0.1:443
```

Then point your browser to [https://localhost](https://localhost) - and you'll see your home server pages.

---

### Post by MrHorus on 2007-05-12
> **craigp84 said:**
> 
I then have a firewall (iptables) rule which looks for traffic to port 443 originating from my work's IP subnet, and internal reroutes the packet to port 7443.


I was going to lambast you and say that doesn't help him as he needs 443 for SSL... then I re-read about checking if it was from your work's subnet with iptables and actually, that's pretty clever :)

*doffs hat*

---

### Post by Joe Jarvis on 2007-05-12
> **craigp84 said:**
> Yes and No.

Officially the answer is no. But i work around this by having sshd listen on port 7443 and my web server on 443.

I then have a firewall (iptables) rule which looks for traffic to port 443 originating from my work's IP subnet, and internal reroutes the packet to port 7443.

This means when anyone connects from anywhere apart from your work, they see the web server, but when you connect from your work, you get sshd.

If you need to access the webserver, you can do port forwarding over ssh anyway:

```
ssh -p 443 -L443:127.0.0.1:443
```

Then point your browser to [https://localhost](https://localhost) - and you'll see your home server pages.

Thanks, your solution is clever.  Will try and report back to forums.

Unfortunately, my less technically inclined coworkers use my secure Web server from work, and their Web traffic is routed through the same proxy server at my office... so I think they would lose that access with your solution.  But that may just be the price I have to pay.  Any other ideas?

In my wildest dreams, a superserver like Inetd would have a plugin or functionality to sniff the service.  Le sigh.

Out of curiosity, why do you run your SSH server on port 7443?

---

### Post by Frosty Cold Drink on 2007-05-12
Yes yes! You can do this. There are a couple of ways. A cheap way is to add an iptables rule that will rewrite packets coming from a specified source port to go to your SSH server. Then you can SSH in while binding to a local port. You have (very roughtly) one two thousandth of a percent chance of that breaking for any given attempt to conenct to your server (the chance of some web browser randomly selecting that local port for an outgoing connection.) You'll have to add an outgoing rule too to make sure the packets look proper.

There are other methods of multiplexing ports (there is actualy a TCP multiplexing protocol!) including using deep packet inspection, but those will likley slow things up too much and choke.

Edit: You will of course want to keep state and flag the connection to make rewriting after the initial packets go a bit smoother.

---

### Post by craigp84 on 2007-05-12
Joe,

Technically, i think it is feasible that you could write code to watch incoming packets for what looks like an  HTTP connection, and hand off to the webserver, you would have to make the code assume that if it cant match an HTTP request, that it's then an SSH connection (SSH client doesn't say anything when it connects to the SSH server, it just makes the connection, and awaits SSHD announcing its version before it commences hand shaking).

Hence the "Yes and no" before. Unfortunately i don't know of anyone who has created code to do this. I can't even create some PoC code as i don't do C, and a scripting language would be too poor performance i think.

MrHorus - thanks, i borrowed the idea from an old colleague who had setup 2 x apache instances (in production) to control what sites the two different sets of clients saw. I was brand new back then and didn't know about vhosts either, so i was just impressed!

I run on 7443 because, well long story, but 7/8/84 is my birthday, and i always use port 7884 for odd jobs. 443 was taken, so i normally just prepend a 7 to whatever port i need. You pick a number special to you :-)

Frosty, you're a wee bit off base with this, but your general concept is kinda along the right lines.

---

### Post by Frosty Cold Drink on 2007-05-12
> **craigp84 said:**
> Frosty, you're a wee bit off base with this, but your general concept is kinda along the right lines.

Why wouldn't that work? (Forgetting about possible source port rewrites from a NAT or something along the way, of course.)

Watching for incoming connetions and handing them off based on what happens would be the best way, but it would involve more work (as you state.) Worse, everything will be "slow". There would have to be two TCP connections (one to the multiplexer then one to the service) unless everything was working through (x)inetd or something, which isn't the greatest thing either since that would mean a new process spawned for each hit on the web server.

Then there is the ugly situation where the connection is sluggish. There will have to be a static wait time to see if an HTTP request comes through. If that is, say, 10 seconds, then that is 10 seconds one would have to wait before the multiplexer would hand things off to SSHD. But what if something hiccups and the HTTP request doesn't go  through quickly enough? Then a whole new request would have to be made by the browser. Ick.

---

### Post by craigp84 on 2007-05-12
Hi Frosty,

> A cheap way is to add an iptables rule that will rewrite packets coming from a specified source port to go to your SSH server.

Unfortunately there's no feature of OpenSSH to specify a source port to bind to when making an outbound connection (nor tectia's ssh client either). Have a look at connect(2) to see why (you'll need to apt-get install manpages-dev first). Note that -b on OpenSSH does not allow port specification, only source IP, so 12.34.56.78:5000 will bork out.

I don't believe rerouting to another port to be cheap either in IPTables present in 2.6 kernels, i remember a mate telling me how this is done, and i remember it wasn't great, can't remember the specifics to say why though unfortunately. They'll be docs covering this on the netfilter site if you want to figure out the reason.

> the chance of some web browser randomly selecting

As above, the userspace process doesn't choose the source port.

> You'll have to add an outgoing rule too to make sure the packets look proper.

I'm not really sure i understand this bit.

> There are other methods of multiplexing ports

Yeah there are, but to be honest I'm not aware of any that would be too useful here :(

> Forgetting about possible source port rewrites from a NAT or something along the way, of course

Well, yeah, there's that too - but that's mainly linux that does that. PIXies don't do this by default for example.

> Watching for incoming connetions and handing them off based on what happens would be the best way

No i disagree, can you imagine how much worse the internet would be for schools etc. if 2 x completely different protocols & content could legitimately go to the same port at the same time. Oh this is just bad bad bad!

Best case would be to get an exception raised through his business for the relevant ports to be opened on their firewall to allow his packets out :-)

The rest of your second post sounds like you turning the gun on yourself :-) i don't want you to do that! But i do agree with your arguments against.

Cheers.

Craig

---

### Post by Frosty Cold Drink on 2007-05-12
> **craigp84 said:**
> Unfortunately there's no feature of OpenSSH to specify a source port to bind to when making an outbound connection (nor tectia's ssh client either). Have a look at connect(2) to see why (you'll need to apt-get install manpages-dev first). Note that -b on OpenSSH does not allow port specification, only source IP, so 12.34.56.78:5000 will bork out.

So, on closer inspection, I see all of the binds in the help text don't do what my brain lapse made me think they did. Oops :)

And then there was netcat.

> ...
     -p local port number (CS)
             When connecting to a remote service, this is the port from which
             the connection will originate.  When listening for remote
             clients, this specifies the local port on which to listen.


I don't know how well this would work, though I think it would be managble. Having to use netcat would be a pretty big inconvenience though.

> I don't believe rerouting to another port to be cheap either in IPTables present in 2.6 kernels, i remember a mate telling me how this is done, and i remember it wasn't great, can't remember the specifics to say why though unfortunately. They'll be docs covering this on the netfilter site if you want to figure out the reason.
I do, as this seems odd. Its on the reading list. Little NAT boxes seem to do this withough too much difficulty, but then they are a bit more specailzed.

> As above, the userspace process doesn't choose the source port.
I'm sure I pulled this off somehow at some point, not that it is typical. I know some FTP servers throw thier data connections from a single, selected port.

> Yeah there are, but to be honest I'm not aware of any that would be too useful here :(
Me neither. I checked first :)

> No i disagree, can you imagine how much worse the internet would be for schools etc. if 2 x completely different protocols & content could legitimately go to the same port at the same time. Oh this is just bad bad bad!
Oh yes of course. I mean in the context of this situation. I even get particuarly peeved when people change default ports for services.

> Best case would be to get an exception raised through his business for the relevant ports to be opened on their firewall to allow his packets out :-)
Yes but that would be reasonable, and we are dealing with computer security... plauged by people with FAS, and filled with misconceptions, distrust, and doubt.

> The rest of your second post sounds like you turning the gun on yourself :-) i don't want you to do that! But i do agree with your arguments against.
I tend to get subconsciously masochistic when it comes to tech. Oh well :)

---

### Post by craigp84 on 2007-05-12
> I'm sure I pulled this off somehow at some point

Oh yeah it's definately possible to choose a local port to connect from in other apps, as per netcat and even the everyday DNS resolver (older DNS servers are setup only to pay attention to stuff from source port 53). Also you can use the raw sockets interface to do pretty much *anything*.

Just not with these apps :-)

> I don't know how well this would work, though I think it would be managble. Having to use netcat would be a pretty big inconvenience though.


You could use the ProxyCommand directive of OpenSSH to make it transparent:

~/.ssh/config:

```
Host my.host.com
  ProxyCommand nc -p 7884 %h %p
```

Would mean that everytime you connected to my.host.com (ssh my.host.com), the source port would be 7884.

But remember, this is a bad approach. Just say no :-)

---

### Post by Frosty Cold Drink on 2007-05-12
> **craigp84 said:**
> But remember, this is a bad approach. Just say no :-)

Yeah but if you have to you have to :)

Thinking about it trying to get 2 IP addresses from an ISP would work (even though they don't like to do this unless you are a over paying business customer). The  web server could bind to one IP address, and SSH to the other. It would cause some local issues sure, but its a lot cleaner than rewriting packets based on source port.

A consumer level NAT would make this a bit more difficult, though.

---

### Post by MrHorus on 2007-05-13
> **Frosty Cold Drink said:**
> Yeah but if you have to you have to :)

Thinking about it trying to get 2 IP addresses from an ISP would work (even though they don't like to do this unless you are a over paying business customer). 

That somewhat depends whereabouts in the world you are and how nice your ISP is.

I'm in the UK for example and i'm with Plusnet and I managed to obtain 8 IPs from them simply by asking :)

---

### Post by Frosty Cold Drink on 2007-05-13
> **MrHorus said:**
> That somewhat depends whereabouts in the world you are and how nice your ISP is.

I'm in the UK for example and i'm with Plusnet and I managed to obtain 8 IPs from them simply by asking :)

Yeah US Internet goodness is pretty far behind Europe and the densely populated areas of Asia. But FIOS is coming! :)

---

