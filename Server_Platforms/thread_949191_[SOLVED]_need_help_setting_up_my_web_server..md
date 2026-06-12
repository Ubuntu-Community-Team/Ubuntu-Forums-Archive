---
title: "[SOLVED] need help setting up my web server."
date: 2008-10-15
forum: Server Platforms
---

### Post by sTpny on 2008-10-15
Hi everyone,

I've got a LAMP system working for localhost on my personal computer, which is behind a telus router, and I want to be able to access it from the internet. I've got a dynamic ip, so I used no-ip to get penguinmigrations.myvnc.com to point to my telus routers current ip. The address then showed my routers home page, which wasn't what I wanted. I found out that I needed to enable port forwarding for http requests on port 80, so that requests for webpages get sent to my computer from the router. I think I did this, but I'm not sure. I had my cousin browse to my address from his machine, and he gets.. 

Gateway Timeout

The following error occurred:

[code=GATEWAY_TIMEOUT] A gateway timeout occurred. The server is unreachable. Retry the request. 





--------------------------------------------------------------------------------

Please contact the administrator. 


Locally, I still get my routers page, but I think that external requests are being forwared to my computer, and my computer is just not accepting them. So I guess what i need is some help configuring my server, and possibly my router as well. I'm a newbie at this stuff, and I don't want to break things while trying to fix them, so please, could someone in the know please help me? What do I need to do to get this working? You will probably need to see some config files to help. which ones? 

Please and Thanks

Tony

---

### Post by Drezard on 2008-10-16
[A] Make sure you can ping the internet ip and you get a response. 

[B] Next, make sure the 'remote access' on your router is either disabled or changed to something other then port 80

[C] Then make sure you browse it locally

[D] Make sure (using portforward.com) you have actually port forwarded the ports correctly. 

Return to here with results :)

Daniel

---

### Post by sTpny on 2008-10-18
When you say pig the ip, do you mean the ip assigned to me by my ISP. If so, its super fast here on the LAN, but from elsewhere on the Internet, it times out.. no responce. So, i'm stuck on A. grrrr.. 

Thanks btw.

---

### Post by cariboo on 2008-10-18
Try [canyouseeme]("http://www.canyouseeme.org/") to see if the port you forwarded is open. It wouldn't surprise that Telus blocks everything.

Jim

---

### Post by golond on 2008-10-18
Hi sTpny,

When setting up my first web server recently, I ran into buckets of headaches trying to get people outside my network to access the server.  In the end, it turned out that on top of all the normal server configuration, that my ISP (RCN, if anyone cares) was blocking all incoming traffic on port 80.  That seems to be the standard operating procedure for a large percentage of providers.

Fortunately, no-ip provides not only solutions for dynamic ips, but can help with port forwarding as well.  Try configuring apache to accept connections on another port (8080 seems to be a standard alternate port for http), set up your router to forward that port to your server, and see if you have better luck getting the communication lines open.

Best of luck to you.

---

### Post by mbeach on 2008-10-18
The fact that your friend used to get to your router's html page would suggest to me that your isp may not be blocking port 80 (or 8080 depending on your router).  When you are setting up your forwarding, does your pc have a static ip on your internal network?

---

### Post by golond on 2008-10-18
In response to mbeach's comment, I got the impression that you were getting the router's page when trying to browse to your server from within your network, and that any attempt your cousin made timed out.  If your isp IS blocking port 80, you'll still be able to see your own server from your network (since your http request is most likely bounced immediately back to you without running into the port filters), but outside users won't get any sort of response.  So, if your cousin did get a response out of your network router, then mbeach is 100% right. If not, give a different port a try.

---

### Post by sTpny on 2008-10-18
This is what I got from canuseeme...

Error: I could not see your service on 75.157.85.254 on port (80)
Reason: Connection refused


I also tried a couple of other ports.. 


Error: I could not see your service on 75.157.85.254 on port (8080)
Reason: Connection timed out

and ...


Error: I could not see your service on 75.157.85.254 on port (1525)
Reason: Connection timed out


I think this means that port 80 is blocked and I'll need to redirect to another port with no-ip, and set my server to use that port, not that I know how to any of it. I'll likely need more help on this.

Thanks, 

Tony.

---

### Post by sTpny on 2008-10-18
Thanks Golond, 

I think thats it.  The isp is just blocking port 80, so I'll need to use an alternate one. Trouble is, I know nothing about configuring apache. I just clicked on Apache2 and php5 in the ubuntu repos, and my server sort of just worked. I say sort of only because I had to figure out where to put the pages, and then I had to learn a bit about file permissions to give myself the ability to write to the www directoy. I'll figure it out, but a hint might be nice.

Tony.

---

### Post by sTpny on 2008-10-18
Hi mbeach,

Honestly, I'm not sure if my internat ip is static or not. The router assigns the ip's and its set to keep them for infinate time, so I guess its static, except for maybe if I reboot or if the power goes out, but I couldn't see an actual 'static' like option anywhere in the routers settings.  

Looking back at my chat history in pigeon, I notice that I may have misunderstood when my cousin said that he could see my routers setup page.  I had asked him two questions, and he might have been saying yes to the other, which could explain why I've been having trouble with this... 

I thought it would be easy.. 

stupid me.

Tony.

---

### Post by sTpny on 2008-10-18
I'm not sure whats wrong, and there may have been a miscommunication with my cousin when we were talking about him seeing my router. Later, it was another cousin who didn't get any response at all. So it could be that my ISP is blocking port 80, or it might be that my apache config is not responding to requests from the outside world. It could even be both. I expect that I will wait for comments before trying anything else. I've got lots of other things to do today, and the sun is shining.

---

### Post by agray on 2008-10-18
As far as your IP addresses go, if your router is handing them out, then it's not static.  To set up a static IP address for you server, you'll have to do it on your server.  You'll also need to setup the gateway to point to your routers IP address.

---

### Post by golond on 2008-10-19
Hey Tony,

Search through your configuration file /etc/apache2/ports.conf (or possibly apache2.conf or httpd.conf, depending on your installation) for a line that reads "Listen 80".  That directive tells apache to accept http requests on port (whatever).  You can list as many ports as you like on subsequent lines using the same format. I added the line "Listen 8080" to mine just after the default entry, letting me listen on both 80 and 8080.

---

### Post by sTpny on 2008-10-20
A big thanks friend. You've just made my life a whole lot easier.

---

### Post by sTpny on 2008-10-21
Hi Guys,

I still couldn't get my computer to serve to the web, but I stumbled upon 000hosting, which has free php and mysql, which is perfect for me, so I'm not going to bother with this server stuff anymore. I did try though, and I thought it should work, but now I notice that my localhost is broken, I can't even see my pages on my computer with [http://localhost/](http://localhost/), apache2 gives a page not found error, yet I can get to /phpmyadmin, so it looks like I either caused a problem, or there was an underlying problem with my system to begin with. Thanks again.

---

