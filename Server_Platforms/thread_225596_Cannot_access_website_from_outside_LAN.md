---
title: "Cannot access website from outside LAN"
date: 2006-07-30
forum: Server Platforms
---

### Post by bwiewiora on 2006-07-30
Here is my problem: I setup an Ubuntu Dapper box to act as a basic web and ftp server, I installed Apache2 and proftpd and everything seemed fine.  At my computer I could open firefox and go to the domain name I registered and it took me to my site.  I also was able to FTP from another network, so that works fine.  When I tried to go to my domain name from another network, however, I got a time-out message.  Here's what I've tried so far:

1. Forwarded port 80 on my router to the server.
2. Tried accessing the site from the public address when on another network, no dice.
3. Tried changing the port to 81 and other random ports (in case me ISP was blocking 80).  Still no dice when trying from another network.

What I really don't get is that the log on my router doesn't even register that I'm trying to access my server when I try from another network.  This makes me think that the request isn't even reaching my router.  

Any ideas?

---

### Post by Dr. Nick on 2006-07-30
my isp block port 80, if you just set your apache to say port 81 it still will not work unless you specify port 81 while typing in the address for example

[www.mysite.com:81](www.mysite.com:81)

I think that is correct syntax, I dont have a server up anymore, but remember when I did you always had to put the port number on the address. That may be why your router doesnt recgonize it since your isp blocks it first

---

### Post by bwiewiora on 2006-07-30
Yah, that's what I tried, and I still got nothing.  I tried with 81, and then some other random too for good measure.

---

### Post by chrisfay on 2006-07-30
> When I tried to go to my domain name from another network, however, I got a time-out message. 

Do you mean you tried from another computer on your home network or one that uses a completely different WAN IP? 

You havn't explained how your DNS is setup or if someone else is running your DNS but, if you are having problems with requests being routed to your pc using your domain, you may check to make sure your zone records are pointing to your WAN IP.

use: [http://www.dnsreport.com/](http://www.dnsreport.com/) to test if your DNS is configured correctly.

When you successfully accessed your pc with FTP did you use:

[ftp://user@domain.com](ftp://user@domain.com) or
[ftp://user@ip](ftp://user@ip)

If you can access it using your IP but not your domain than you probably have a misconfigured DNS.

---

### Post by chrisfay on 2006-07-30
> [www.mysite.com:81](www.mysite.com:81)

I think that is correct syntax, I dont have a server up anymore, but remember when I did you always had to put the port number on the address. That may be why your router doesnt recgonize it since your isp blocks it first

If you have access to your DNS zone records all you have to do is add the port there in your A record. Any request for you site will be routed through that port so you don't have to add it when you type it into a browser.

---

### Post by Dr. Nick on 2006-07-30
> **chrisfay said:**
> If you have access to your DNS zone records all you have to do is add the port there in your A record. Any request for you site will be routed through that port so you don't have to add it when you type it into a browser.


Cool, thanks for sharing. I dont think I could have done it though as I was just using one of them dynamic dns sites like tzo for image hosting, But if i ever get a real site ill remember that

To the OP, you may just put your server computer into the dmz on the router temporarily to make sure that their isnt some router config mesing it up.

try this site and do a prt test to see if port 80 is open on your ip, if its not then you will know your isp blocks
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by bwiewiora on 2006-07-30
Chris:

Dnsreport.com checked out okay (nice link, thanks).  The ftp request I did was using the IP, but I just tried using the domain name and that worked too.  By another network I mean another public WAN IP address.  When I try on that other IP I do both the domain name and the ip, and neither work.  

Dr. Nick:

I tried putting my server on the DMZ, same result.  The link you gave (another nice one, thanks) showed port 80 as being in stealth, so it seem like the ISP is blocking.  When I changed to 81 and restarted apache, grc said 81 was open, so that was good.  When trying to connect from another network (different public IP), via direct IP:81 or domain.com:81, still got a time-out.  

This is weird, isn't it?

Thanks to both of you for your time, by the way.

---

### Post by drivel on 2006-07-30
Is your ISP blocked the connect from outside lan?

---

### Post by chrisfay on 2006-07-30
Are you behind a router or a firewall?

If behind a router, you need to port forward to your internal static ip.

If behind a firewall, you need to open the correct ports.

---

### Post by bwiewiora on 2006-07-30
Drivel: I know that my ISP blocks port 80, so I've tried it on other ports and it still doesn't work.  

Chris:  I have the ports forwarded in my router, and it still doesn't work.  I even put my server in the DMZ, and still no dice.

Could it be something in my hosts file?  Here's what's there now:

127.0.0.1	localhost
127.0.1.1	Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by gjivan72 on 2006-07-31
Try adding your local ip address to ports.conf 
Normally its 
Listen PortNumber

Try 

Listen Local IP Address:PortNumber
Example:192.168.0.123:81

Worked for me

---

