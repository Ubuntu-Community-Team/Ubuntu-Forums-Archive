---
title: "help with accessing my server over the internet"
date: 2012-09-10
forum: Server Platforms
---

### Post by nuclearj on 2012-09-10
Ok I need help with accessing my server over the internet.

I have a fresh install of Ubuntu Server 12.04 64 bit with ssh and webmin installed. I've forwarded port 22 on my router to the ip address of the server.

I am trying to connect over the 3G network of my android phone using connectbot. I can connect with connectbot when I am on my home wifi connection but when I turn off the wifi and try to use 3G, the connection times out.

What gives? I've been trying for two weeks now and this is driving me nuts! Please let me know what extra info you might need.

P.S. these are some info I have been referencing.  Am I understanding this correctly, does local port forwarding create the tunnel I need to access my server over the internet securely?



[http://www.openssh.org/faq.html#2.11](http://www.openssh.org/faq.html#2.11)

[http://ubuntuforums.org/showthread.php?t=902762](http://ubuntuforums.org/showthread.php?t=902762)

---

### Post by volkswagner on 2012-09-10
You need to verify your ISP is not blocking port 22.

From any computer on your LAN go to [canyouseeme.org]("http://canyouseeme.org") and check if port 22 is open.

---

### Post by Frankincense93 on 2012-09-10
> **nuclearj said:**
> I can connect with connectbot when I am on my home wifi connection but when I turn off the wifi and try to use 3G, the connection times out.

Assuming your server is also on your home wifi; you use the local ip to connect to the server over wifi, i.e 192.168.1.1. But when using your phone over 3g, you are not connected locally, so you must use the servers external ip (what you can find at whatismyip.org).

---

### Post by nuclearj on 2012-09-10
> **Frankincense93 said:**
> Assuming your server is also on your home wifi; you use the local ip to connect to the server over wifi, i.e 192.168.1.1. But when using your phone over 3g, you are not connected locally, so you must use the servers external ip (what you can find at whatismyip.org).

Yes thanks, when I was at work I tried a few ip addresses including the one i found at whatismyip; but to no avail.

---

### Post by nuclearj on 2012-09-10
> **volkswagner said:**
> You need to verify your ISP is not blocking port 22.

From any computer on your LAN go to [canyouseeme.org]("http://canyouseeme.org") and check if port 22 is open.

I started looking to that route a while ago but in my hack and slash ADD fashion, went another direction.  I did check it out and this is what I got:

```
Error: I could not see your service on 184.xxx.xxx.xxx on port (22)
Reason: Connection timed out

```

Does a timed out error mean it is blocked?  If so, should I open a non-standard port and connect through that?  Or are there other solutions?

---

### Post by kennethconn on 2012-09-11
> **nuclearj said:**
>  Am I understanding this correctly, does local port forwarding create the tunnel I need to access my server over the internet securely?
 
Just from reading your posts, I suspect that you are not 100% certain of your home networks external IP address. Tunnelling is not required if you just wish to ssh into your server external over the internet.
 
So try and get external ssh access to your server sorted first. Once you know your external IP as handed out to you by your ISP, any attempts to connect to it from outside (such as your work PC) should get there because of the port forward rule you created on your router.
 
Try this on a device other than your phone. If attempts to connect from multiple devices are all failing, then you know the problem is not with your phone.

---

### Post by nuclearj on 2012-09-11
> **kennethconn said:**
> Just from reading your posts, I suspect that you are not 100% certain of your home networks external IP address. Tunnelling is not required if you just wish to ssh into your server external over the internet.
 
So try and get external ssh access to your server sorted first. Once you know your external IP as handed out to you by your ISP, any attempts to connect to it from outside (such as your work PC) should get there because of the port forward rule you created on your router.
 
Try this on a device other than your phone. If attempts to connect from multiple devices are all failing, then you know the problem is not with your phone.

Thanks for that.  It is not my phone, router, or the settings.  I found out that my ISP provider Clearwire blocks like every port.  I found this workaround/fix.  I'll look over it later and digest it.  But in the mean time if some one could give me the cliff notes on it...

[http://wuhzat.wordpress.com/2011/01/11/ethernet-hub-as-a-network-troubleshooting-device/](http://wuhzat.wordpress.com/2011/01/11/ethernet-hub-as-a-network-troubleshooting-device/)

Thanks everyone!  Feels good to get somewhere on this.

---

### Post by kennethconn on 2012-09-11
> **nuclearj said:**
> I found out that my ISP provider Clearwire blocks like every port.

Every port or just service ports?

---

### Post by nuclearj on 2012-09-12
> **kennethconn said:**
> Every port or just service ports?

I think it is every.  I opened port 3030 and then used the canyouseeme.org website and it gave the same timeout error.

---

