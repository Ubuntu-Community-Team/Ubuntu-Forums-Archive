---
title: "Apache2 question"
date: 2012-10-03
forum: Server Platforms
---

### Post by george5729 on 2012-10-03
Hi everyone,

I am trying to test my Apache2 web server from the WAN side using this web site:

[http://hidemyass.com/](http://hidemyass.com/)

I have forwarded port 80 on my router, and I'm fairly sure it's not blocked by my ISP.

[http://xxx.xxx.xxx.xxx:80](http://xxx.xxx.xxx.xxx:80)

But when I enter my global ip address to view my apache2 web server, it doesn't work.

localhost is working from the LAN side. And I just need to know if this is a good way for testing the WAN side.

Can somebody with apache2 working please let me know?

---

### Post by albandy on 2012-10-03
> **george5729 said:**
> Hi everyone,

I am trying to test my Apache2 web server from the WAN side using this web site:

[http://hidemyass.com/](http://hidemyass.com/)

I have forwarded port 80 on my router, and I'm fairly sure it's not blocked by my ISP.

[http://xxx.xxx.xxx.xxx:80](http://xxx.xxx.xxx.xxx:80)

But when I enter my global ip address to view my apache2 web server, it doesn't work.

localhost is working from the LAN side. And I just need to know if this is a good way for testing the WAN side.

Can somebody with apache2 working please let me know?

Did you test it from other local machines?

---

### Post by Prospero2006 on 2012-10-03
Hello,
If you have access to a remote shell of some sort, use nmap. 

  -I'd recommend setting up something like a Rackspace cloud server instance if you can for remote shell access. You can spin up a simple cloud-based Ubuntu server for something like 1 penny per hour. If you don't use it, you don't pay. I'll spin up a server every so often as needed. It's a great resource in my opinion. 

 -This website seems to work well also:
        [http://nmap-online.com](http://nmap-online.com)
   
 -Try an online ping also:
        [http://ping.eu/](http://ping.eu/)

I hope that's helpful

---

### Post by SeijiSensei on 2012-10-03
> **Prospero2006 said:**
> Hello,
If you have access to a remote shell of some sort, use nmap.

Or use [nmap-online]("http://nmap-online.com/") if you feel [they]("http://www.matousec.com/matousec/about-us.php") are trustworthy.

---

### Post by Cheesemill on 2012-10-03
> **george5729 said:**
> But when I enter my global ip address to view my apache2 web server, it doesn't work.
Trying to access your web site using its external IP from inside your network wont work, If you are on a machine on your internal network you have to access it using its internal IP address.

To test if your site is working OK externally you have to test it from outside your network, I usually just pop down the road to my library to use their internet (you could also use a smart phone as long as it's not using your wi-fi).

---

### Post by volkswagner on 2012-10-03
> **Cheesemill said:**
> Trying to access your web site using its external IP from inside your network wont work, If you are on a machine on your internal network you have to access it using its internal IP address.

To test if your site is working OK externally you have to test it from outside your network, I usually just pop down the road to my library to use their internet (you could also use a smart phone as long as it's not using your wi-fi).

The OP mentioned using "hidemyass.com" which is a free proxy which should simulate an outside request.

As mentioned you need to make sure your port is not blocked by isp (go to canyouseeme.org from any machine inside your lan) and is properly forwarded via your router.

---

