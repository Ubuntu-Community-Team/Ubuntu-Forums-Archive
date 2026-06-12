---
title: "I'm stuck"
date: 2007-01-26
forum: Server Platforms
---

### Post by cap10kirk on 2007-01-26
I'm in a bind here. I built a server using the The Perfect Setup ubuntu LTS. I installed ISPConfig on the the server. Suprisingly (very), the server worked great. I used Go Daddy as my DNS server. However, I was using comcast as my internet provider. After a few weeks they called to inform me that I needed to upgrade to a business account. Cool. Now I have a gateway type modem where both my PC and my server are hooked up to. I now have a static IP address. But now i'm confused (very). Do I configue my ISPConfig using my static IP or my gateway IP address? The gateway IP is what shows on the net. I foward my port to 80. Also, do I have to edit any files using my static IP address? I'm a newbie at this stuff, so any assistance is greatly appreciated.

Thanks in advance,
Kirk

---

### Post by geek_Man on 2007-01-26
I would think you would configure it with your static IP. Am I an expert? No. But I'd give it a try.

---

### Post by chrisfay on 2007-01-27
> Do I configue my ISPConfig using my static IP or my gateway IP address?

What are you trying to configure that requires you to specify the IP? Unless you have services configured to respond on seperate IP's you should only need to specify ports and hostnames; DNS takes care of the routing to your WAN/Gateway IP and your router should take care of routing to your internal LAN/Static IP you have setup.  

> I foward my port to 80

You mean you've forwarded port 80 to your server's static LAN IP?

---

