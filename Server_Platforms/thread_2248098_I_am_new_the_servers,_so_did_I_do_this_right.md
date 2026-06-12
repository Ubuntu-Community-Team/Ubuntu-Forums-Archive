---
title: "I am new the servers, so did I do this right?"
date: 2014-10-12
forum: Server Platforms
---

### Post by jupeliks on 2014-10-12
Me and my friend decided to boot up one of our old PCs and start a ubuntu server on it, and we actually managed to get it to work. Now, we both are very new to all this server-related stuff, so I'm very suspicious did we do everything right, so here's a little recap, and I'd hope answer to one question: Did we do it right? Or is there some horrible mistake that will crash down the whole internet. (:D)

The server is at my friend's place and there his network has somewhat basic router, into which we connected the server. We installed Ubuntu Server 12.04 with OpenSSH without any major issues and first thing we did was manually set up a static IP address and nameserver for the server. It was some basic 192.168.100 internal IP due to the router, and friend confirmed that after that he managed to connect to the server from his PC with the internal IP. Also update and upgrade worked fine. Next up we accessed the routers settings and forwarded port 22 to the server and after that I was able to connect to the server with PuTTy. Next was Apache2, MySQL, PHP5 and some other things (we were following some step-by-step tutorial for it) and got a working webpage (after forwarfing port 80 to the server). At this point we were really excited that we got everything working without any major hiccups. Lastly we set up a TS3 server running (we created a seperate account into the server, that runs it) and forwarded the 3 required ports for it and we even tested minecraft server (forwarded port 25565), which also to our surprise worked (eventhough the minecraft server crashed, since we didn't have enough memory to run it).

So there's that. I hope we did everything right :s I am rather suspicious about the fact that you can connect to the website, ts3 and minecraft with the same exact IP o_O I thought that you would have to set up separate IP for all of them or something (so you could have subdomain like mc.something.com and ts.something.com).

Small offtopic question also: I installed vnstat for the server and made a .php page, where i can easily go check the network usage, and I only used this:
[PHP]<plaintext>
<?php
$netusage = shell_exec("vnstat");
echo "$netusage";
?>[/PHP]
Is this good? Is there a better way? if i tried to echo the vnstat into a <p> it just threw it all into the same line. with plaintext it showed the output properly.

---

### Post by TheFu on 2014-10-12
No, you cannot crash the internet from home internet.  Only a major ISP can cause huge issues like taking over a netblock by accident and redirecting all traffic meant for one place to somewhere else. [http://arstechnica.com/uncategorized/2008/02/insecure-routing-redirects-youtube-to-pakistan/](http://arstechnica.com/uncategorized/2008/02/insecure-routing-redirects-youtube-to-pakistan/) explains.

Ok - ssh rocks completely.  Please load **fail2ban** and never use passwords. Use key-based ssh authentication over the internet.  Securing ssh is relatively easy. [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

Running any PHP website on the internet is asking for trouble - especially by non-professionals.  While you are learning, it is best to require an ssh-tunnel to access the website. Definitely [read this]("https://www.owasp.org/index.php/PHP_Security_Cheat_Sheet") on php web-app security.

Using shell-exec is a great way to get hacked currently. It is probably running /bin/bash which is constantly being patched for new attack vectors, almost daily. It even has a fancy name and has been on most of the news world-wide. [https://en.wikipedia.org/wiki/Shellshock_%28software_bug%29](https://en.wikipedia.org/wiki/Shellshock_%28software_bug%29)

Just because something works, that doesn't mean it is "best practice" or secure.  Be afraid, be paranoid.  Have a plan for what happens after the system, then network are hacked.  Do you have a plan?  What happens to all the other computers on that network when they all are hacked too?  Will the parents be happy?  

The first time I got hacked was quite the eye opening experience.  When a link system gets hacked, lots of things happen.  For example: [http://draios.com/fishing-for-hackers/](http://draios.com/fishing-for-hackers/)  Awareness is the first step.

Oh ... and have fun too!

---

