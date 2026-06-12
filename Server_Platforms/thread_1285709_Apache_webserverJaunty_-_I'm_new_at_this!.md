---
title: "Apache webserver/Jaunty - I'm new at this!"
date: 2009-10-08
forum: Server Platforms
---

### Post by six30two on 2009-10-08
Whoo. Okay. So... In a nutshell, I've just picked up some classes this semester to get me going on computer/tech stuff. One professor has asked me to do some side work to get some Unix and some webdev under my belt super-fast. So I'm flying by the seat of my pants, and trying to get a server running so I can work on it.

I have Jaunty Server running, LAMP is installed, along with openssh and a few other packages. I got Apache2 PHP5 installed.

I had a friend of mine try to SSH in from outside of my network, and he got in (to the password prompt, at least, and my machine was responding to ping before that), so I'm assuming my server is active and visible. At least through SSH and Ping, both inside and out of my personal network.

But my problem is, now, that I can't bring up any of my server test pages at all with my external IP. When I type in my internal IP address into a browser, it connects fine and shows the test pages. When I type in my external ip my browser spits me right into my router setup utility.

How can I set this up so that when someone uses a browser to look up my server's IP address, they are, instead, redirected to my test pages on the server itself, instead of my router settings?

Things I HAVE done:
port forwarded port 22 (for SSH, I think?)
port forwarded 8080 to 80 (for Apache?)

Or am I completely unable to visit my web from INSIDE my network using my external IP - will it always direct me to my router settings, or am I doing something wrong? Basically, I just don't want to use my external IP from outside of my network and be spit into my router settings. Bad idea. Currently, I have no way to test this outside of my network - and no, I'm not handing out my server IP, don't ask ;P

---

### Post by ZXQ on 2009-10-08
I'm no expert, but it sounds like you're using the router IP, not your external IP.

From inside your network, hit the website [www.whatsmyip.org](www.whatsmyip.org) and use that, see if that changes things.

---

### Post by six30two on 2009-10-08
Okay, nevermind.

I got it all worked out.
I wasn't aware external IPs didn't work inside the network. I don't have much experience with home networking. Still learning ^^;

---

