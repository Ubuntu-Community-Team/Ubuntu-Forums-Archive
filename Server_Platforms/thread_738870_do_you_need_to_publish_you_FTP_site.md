---
title: "do you need to publish you FTP site?"
date: 2008-03-29
forum: Server Platforms
---

### Post by 7aji88 on 2008-03-29
I know this may sound silly, but after setting up my first FTP server ( I'm using proftp with gproftp for the GUI) I tried to upload and download to the site through the local network using the server ip address on the local network and it works fine. My question is how would I upload and download through the internet? do I need some ISP hosting or something like it?? please help, thanks!!

---

### Post by Poleh on 2008-03-29
Well, the thing is your server exists on your internal network and is (probably) not visible to people on the internet. Normally FTP servers would be hosted somewhere with an ISP or a datacenter and have a public ip address so internet users can access the server.

If you want to expose your internal FTP server to the internet you can do this - do some searching on port forwarding which is basically the ability to open a port on your internet router that sends traffic to your FTP server internally.

Good luck, and keep at it!

---

### Post by 7aji88 on 2008-03-30
So what would the server's IP address  be? the internet gateway (the modem) ?  :confused:
thanks !!

---

### Post by Oldsoldier2003 on 2008-03-30
> **7aji88 said:**
> So what would the server's IP address  be? the internet gateway (the modem) ?  :confused:
thanks !!
Yes- as long as you have the ports forwarded to your server use the gateway/routers public ip address. ( Actually this is the IP address for all the computers on your home network that share internet access.)You can also set up dynamic dns (use one of the free services like dyndns.org)  if you want to make life easier for the end users of your ftp server.

---

### Post by 7aji88 on 2008-03-30
thanks a lot :) I'll give it a try

[UPDATE]  I've just tried to connect to the server from a different place and it worked! :) thanks again for help.

---

