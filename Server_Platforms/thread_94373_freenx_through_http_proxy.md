---
title: "freenx through http proxy"
date: 2005-11-23
forum: Server Platforms
---

### Post by diebels on 2005-11-23
I'm running freenx server at home, and want to connect to it from a windows client at work behind a http proxy.

I'm already running putty at work, since the proxy administrator was nice and added port 22 to SSLPorts. 

Can I do the same with an windows nxclient? Can it be setup to run through a http proxy?

I can't find any options for proxy type "http", and proxy port number in the nxclient.

I've also seen somebody talking about making a socks proxy with putty that the nxclient can connect through. How would I do that?

---

### Post by cactus on 2005-11-23
nxclient runs through ssh (port 22).
what made you think it used http?

---

### Post by diebels on 2005-11-23
[QUOTE=cactus]nxclient runs through ssh (port 22).
what made you think it used http?[/QUOTE]
Nothing made me think it used http. I want it to use it.
Putty (windows ssh-client) also runs through ssh port 22. But since I'm at work and behind a http proxy, I must run everything through this.
Putty runs through the http proxy with "HTTP CONNECT" requests, after I configured it in the GUI to use HTTP proxy with a certain address and port. And is communicating fine with my ssh-server listening to port 22 at home.

So the questions are:
Can nxclient use http proxy?
Can nxclient use socks proxy setup with putty?
How do you setup a socks proxy with putty?

---

### Post by cactus on 2005-11-23
oh. well, it is just tcp traffic. 
slap it through stunnel or something. that should be more or less transparent to the client programs.
ps. is he proxying https as well, because if not, than that would be a preferred port to tunnel over..no proxy would be a speed increase most likely.

---

### Post by diebels on 2005-11-23
[QUOTE=cactus]oh. well, it is just tcp traffic. 
slap it through stunnel or something. that should be more or less transparent to the client programs.
ps. is he proxying https as well, because if not, than that would be a preferred port to tunnel over..no proxy would be a speed increase most likely.[/QUOTE]
All ports but the proxy port is blocked by a firewall. All traffic must go through the proxy port. So if the http proxy is 10.0.0.1:8080 , I would run
```
stunnel -d 10.0.01:8080 -l nxclient
```?

---

### Post by cactus on 2005-11-24
dunno. it was just a thought, and *should* work. 
I have never tried to tunnel through an http proxy myself though. 
Have you tried a google search? "stunnel through http proxy" or something maybe

---

