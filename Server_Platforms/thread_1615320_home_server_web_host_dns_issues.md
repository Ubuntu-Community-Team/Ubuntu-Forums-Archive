---
title: "home server web host dns issues"
date: 2010-11-06
forum: Server Platforms
---

### Post by AuthorizedAgent on 2010-11-06
Goal: use server with Ubuntu Server as home server for web hosting.

have: server, domain name, static ip

I am not understanding how to piece it all together. I have filezilla and putty in place to do all work.

i have read the dns section on the ubuntu guide. if this is the directions i need to follow i am lacking understanding.

any help would be very appreciated.

thank you

---

### Post by wongo888 on 2010-11-06
Are you asking how to set up Bind?

Otherwise, you need to get your domain name service going and point your domain A record to your static IP. I'd just use a service for this like DynDNS.

Once your domain is resolving to your IP, you need to ensure that your port 80 traffic goes to your server machine. Usually this means setting up port forwarding on your router/firewall device.

[http://portforward.com/](http://portforward.com/)

Once your forwarding traffic within your LAN, you need to configure Apache to respond to the requests.

Done and doner.

K

---

### Post by AuthorizedAgent on 2010-11-06
i have bind installed and "trying" to configure it. learning process.

what i am trying to do is use the server as a host for the website. do i even need bind?

so what you are saying i can use a third party to resolve the ip with the domain name/name server?

EDIT: used DynDns. Everything works great.

Thanks

---

### Post by wongo888 on 2010-11-07
You def could set up Bind to do this, but my point was that using a third-party DNS service like DynDNS will get you resolving your IP quicker and with greater reliability due to their global redundancy.

It sounds like you have everything under control now anyway. Don't forget to mark this thread as solved if you have no further questions.

---

