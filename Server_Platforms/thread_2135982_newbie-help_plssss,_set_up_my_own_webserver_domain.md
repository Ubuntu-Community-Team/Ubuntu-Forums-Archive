---
title: "newbie-help plssss, set up my own webserver domain from namecheap.com"
date: 2013-04-16
forum: Server Platforms
---

### Post by totoy on 2013-04-16
Hi, anyone...please help.
I want to make my own web server and I wanna know about hosting my own thing. I bought a domain name at namecheap.com but still hasn't been up.
I installed ubuntu server 12.04. and installed LAMP on it, ssh, webmin, and a bunch of security measures like ufw and follow most of this tutorial on how to secure my server ([http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics](http://www.thefanclub.co.za/how-to/how-secure-ubuntu-1204-lts-server-part-1-basics)). I can access my server from another pc inside my network with no problems, except for copy/paste files through filezilla(thats another problem thread)
After all that, I installed ddclient in order for me to deal w/ my isp's dynamic ip(as most home subscibers have).
I tried a bunch of configuration on ddclient.conf and still my site won't show up.
I donno if I installed too many security measures to begin with that now it's difficult to access the server from everywhere...or my ddclient.conf is configured wrong.
##my ddclient config:
daemon=300
ssl=yes
protocol=namecheap
use=web, web=checkip.dydns.com/, web-skip='IP Adress'
server=dynamicdns.park-your-domain.com
login=*******.com
password='********************'
@

note: installed my ubuntu server on a virtualbox running on win7, intel i5, 16gb mem.

---

### Post by TheFu on 2013-04-16
I can't tell where you are having issues from the description.  Sorry, it probably is very clear and I just haven't had enough caffeine today.
[http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](http://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site)  explains what is needed to have a website. Hopefully, it is clear and understandable.

Securing a server on the internet usually cannot be performed with a single computer, IMHO.  I see attacks all the time on my little blog, so you'll want to patch all the time -  weekly - as the longest period of non-patching.

It is unclear to me what namecheap has to do with DNS or ddclient.  ddclient needs to be communicating with your DNS provider. If you aren't paying for a DNS provider, then that could be what is missing from your setup?  Perhaps?

This [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) might be helpful in troubleshooting your public IP connection too.

---

### Post by darkod on 2013-04-16
It can probably work as it is, but I would really try to simplify the setup in your place.

1. You have the server on a VBox. What's the point? If you want webserver available to the public, you can't simply turn it on/off when ever you like (actually you can, it's your own server, but again, what's the point of that???). You need a dedicated machine, even an older one would do. But don't involve VBox. For example, if you left the default network setting in VBox to NAT mode, that could create issues. It should be in Bridged Mode as minimum, so that the VM is like directly in your local LAN.

Apart from the above, lets run quickly over the things you need:
2. You have an internet router at home, right? All traffic arrives at the router first. Unless you set the server/win7 machine in some sort of DMZ, you will need to forward port 80 and 443 if you want SSL traffic to the private IP of the server.
3. Some ISPs block port 80 for residential customers, exactly for the reason to block them from running servers at home. Have you confirmed port 80 is not blocked? You can do that at [www.canyouseeme.org]("http://www.canyouseeme.org") for example.
4. Don't bother too much with security especially if the server is not in a DMZ. You have to make a difference between a server on a public IP and a server at home behind your router. Most routers have built-in, enabled firewall. And as stated above, all traffic arrives to the router first. So who are you protecting against with ufw when no one can even reach your server unless you let it with port forwarding on the router? And you need to forward port 80 and 443 anyway since without it the traffic will never reach your server. And you can't block them with ufw, if you do no one will be able to open your websites.
As for other ports, no real need to block them on the server since they are blocked on the router and not forwarded. Most tutorials to protect webservers are for servers directly on the internet. If your case is not the same, it doesn't apply.
5. Does namespace.com have some sort of control panel? If you had a static public IP that's where you would set up the IP so that it can send the web requests to your server. Not sure how you can configure it with the ddclient, you'll need to investigate that.

That's from the top of my head right now...

---

### Post by TheFu on 2013-04-16
Good points from Darko, but a domain registrar usually has a record for the DNS server(s) for the domain, not the IP address itself, unless you bought an all-in-1 hosting, dns, domain package.  At least that has been my limited experience.

I agree that running a web server under virtualBox is less than ideal, but I disagree that running it virtualized is not a great idea.  VirtualBox is great for a desktop-on-desktop solution, but not-so-great for server-on-desktop or server-on-server virtualization.  

However, if you are not pretty familiar with networking, adding in the complexities of VMs could make things just a little too difficult to setup.  All my servers are virtualized, the physical hosts are just setup to run virtual machines only - currently only KVM is used for servers now, but I've used Xen and ESXi previously for a few years.  Only Xen paravirtual VMs caused any issues in that time. When Xen sucked, it really sucked - wouldn't boot.  When it worked, it was extremely stable.  Both ESXi and KVM never have caused any issues at all.

---

### Post by totoy on 2013-04-19
Hi guys, thanks so much for replying to my thread so quickly...sorry for the delayed reply, my internet was down for a day due to some dudes tried sabotaging the telecoms and electricity in my area.
Anyways I am not an expert on networking but fairly familiar and experienced with it, I completely understand running a Ubuntu server on VM but it is just for temporary while I'm done assembling my simple server machine. I know how to install the OS behind a VM w/ no problems with the physical NIC. My only thing is I haven't used the dns client: ddclient before. I was wondering if anyone here knows how to set it up so I can have my server up and running. That why I posted my config so if anyone knows how to correct it pls let me know coz I'm stuck :( ..for now.
Yes my port 80 is open. Set it up from the router side.
Yes namecheap.com have control panel and I already set it up there, Pretty straight forward and I use their DNS server.

thanks

---

