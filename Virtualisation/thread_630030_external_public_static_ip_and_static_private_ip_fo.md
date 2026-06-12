---
title: "external public static ip and static private ip for lan - need help setting up"
date: 2007-12-02
forum: Virtualisation
---

### Post by lollylegs on 2007-12-02
i have a static ip address from isp so that i can host a home webserver (apache) and i have set up a static private ip adress on lan.  have pointed public static ip
eg router to private ip on lan via portforwarding but have set it up right, because when i type in my domain name it just rings up router.  I really need help please as i cant get pulic ip to recognise private ip

---

### Post by bwald on 2007-12-02
When you say you pointed the WAN IP (the one assigned from your ISP) to your LAN IP (assigned from your router) you mean you set your router to give your computer a static IP address and not use DHCP?  If this is the case, then your computer might be blocking the ports.  Have you installed apache yet?  What do you see when you try to go to your WAN IP address?

---

### Post by Tteddo on 2007-12-03
After you get your site to show up on the private IP like the above poster said, then you need to forward port 80 to the private IP address. I have mine working exactly like this. For instance I can go to [http://192.168.0.141/](http://192.168.0.141/) on my private network in any browser and it brings up the same as my domain from the outside.

---

### Post by lollylegs on 2008-11-18
Thanks for all the replies.

Just so I get my head around this, does it mean that:

Even though when I type my external ip assigned by isp 123.2.xxx.xx and it brings up my router, when I get my domain name I have to point it to my static lan 10.1.1.x not my external static ip.

I want to setup small webhosting for five virtual name sites and I thought I had to have a static external ip to achieve this.

I have already set up port forwarding to static lan but cannot be seen from outside.

Regards
Marea (lollylegs)
Australia

---

### Post by Tteddo on 2008-11-18
No, you point your domain name (s) (in the DNS server for it) to the external IP address from your ISP (which is your router's IP address, i.e. 123.2.xxx.xx). Then, inside your router, you forward port 80 to the machine on your private network that hosts your website (i.e. 10.1.1.x).
You have to have a DNS server do point your domain though. Also a static IP will help also. My ISP never changes my IP Address though so I just don't worry about it.

So, to summarise:
At the registrar, you point your domain(s) to a DNS server you can control.
In the DNS server, you point the WWW CNAME to the IP address your ISP gives you (your router's IP address).
Then in your router, you forward port 80 to the machine on your LAN that hosts your website.

Wow, I just noticed that this was from a year ago! That's funny!

---

### Post by bodhi.zazen on 2008-11-18
> **lollylegs said:**
> Thanks for all the replies.

Just so I get my head around this, does it mean that:

Even though when I type my external ip assigned by isp 123.2.xxx.xx and it brings up my router, when I get my domain name I have to point it to my static lan 10.1.1.x not my external static ip.

I want to setup small webhosting for five virtual name sites and I thought I had to have a static external ip to achieve this.

I have already set up port forwarding to static lan but cannot be seen from outside.

Regards
Marea (lollylegs)
Australia

Let me try to explain. Think of this as an address. To simplify, on the Internet you get an IP address from our Internet Provider. This IP address can be assigned static or via dhcp.

If you want someone to find your address, you need to be listed in the phonebook, or with computers you need a domain or DNS server, something like godaddy or dyndns. Make an account there and you will have a domain name, point that to your public IP address. If your public ip address is assigned by dhcp and changes, there may be methods of automatically updating your DNS.

Now when some looks you up by domain_name.com they will be directed to your public IP address by the DNS server and thus to your router.

Now you also have a private network. Your router gives a "private" IP address to each box on your LAN. To direct traffic comming from your Public Domain/IP Address to your servers on your LAN you configure your router to forward port 80 to your server(s). Now you *may* have an issue here in that some routers will only allow you to forward 1 instance of port 80, so to serve 5 web servers on your LAN you will need some kind of proxy server. You can use apache, pound, or squid to proxy serve ...

HTH

---

### Post by lollylegs on 2008-11-21
Hi tteddo
I know it may seem funny that I have reposted this a year later, but gave up because I didn't get information that I could understand being a complete newbie a year ago.  I am still a newbie but thanks to you wonderful people putting it in language that  I can understand and having read a lot more about the subject I think I can set it up this time.
Thanks again for your help
Regards
Marea (lollylegs)
Australia:lol:

---

