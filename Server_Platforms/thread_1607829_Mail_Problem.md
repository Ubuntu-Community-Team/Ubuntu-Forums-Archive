---
title: "Mail Problem"
date: 2010-09-28
forum: Server Platforms
---

### Post by viperce on 2010-09-28
Hi all, I am new to Linux (complete noob) but i somehow managed to get squid proxy server installed. 
My problem is my email in outlook express has stopped working (incomming pop3 server is mail.webmail.co.za)
 
I think i need to install a pop proxy to get this going, can someone recommend a pop proxy that is easy to configure or anything else that could resolve this
 
thanks

---

### Post by viperce on 2010-10-28
Hi all,

I have installed Ubuntu server & set it up as a proxy server which is working fine,
only problem i am having now is my windows clients can not download from their gmail webmail & hotmail servers using Ms outlook. Could someone please help me with this i have no idea how to fix this.

I have 2 network cards eth0 internal lan <--- and eth1 --> router

---

### Post by ArgusVision on 2010-10-28
Ok dumb starter question. Can they get to those sites with a browser? (They aren't blocked by any ACL's?) Also are SMTP, IMAP and/or POP3 blocked?

---

### Post by viperce on 2010-10-28
Hi all,

I have installed Ubuntu server & set it up as a proxy server which is working fine,
only problem i am having now is my windows clients can not download from  their gmail webmail & hotmail servers using Ms outlook. Could  someone please help me with this i have no idea how to fix this.

I have 2 network cards eth0 internal lan <--- and eth1 --> router

If you dont know could someone steer me in the right direction..

---

### Post by s.fox on 2010-10-28
Threads merged. Please do not create duplicate threads. Thank you.

---

### Post by viperce on 2010-10-28
Yup can get into the sites no problem using the proxy server....
how do i check if SMTP, IMAP and/or POP3 blocked? i havint blocked them but im not sure if they blocked by default

---

### Post by ArgusVision on 2010-10-28
You said you're using this as a proxy server, what proxy service are you useing? Squid perhaps?

---

### Post by viperce on 2010-10-28
ye using squid proxy server

---

### Post by viperce on 2010-10-28
i setup squid using Webmin interface since i am a noob it seemed to work better for me :)
i can access webmin/gmail no problem through Squid proxy server.
however if i try checking for mail using ms outlook cannot connect to your incomming (POP3) e-mail server, i think i need to forward the ports or something but im not sure..

---

### Post by ArgusVision on 2010-10-28
Ok I'm not a squid expert but I have worked with ACLs before, and webmin (nice tool by the way). Give me a few minutes to check something. A place to start, that was coincedentally in my RSS feed just now, is [http://www.linux.com/learn/tutorials/373872:weekend-project-set-up-squid-on-linux-as-a-caching-web-proxy](http://www.linux.com/learn/tutorials/373872:weekend-project-set-up-squid-on-linux-as-a-caching-web-proxy) not what you're looking for but...

---

### Post by ArgusVision on 2010-10-28
Take a look at your squid.conf file

```
sudo gedit /etc/squid/squid.conf
```
Look for an entry 

```
acl Safe_ports port 25 # smtp
```

There should also be an entry that allows IMAP or POP3 depending on what you're using.

It should look like
```
acl SSL_ports port 443 563 # https, snews
```

Except change the port number. 
Look here for standard port numbers. [http://www.emailaddressmanager.com/tips/mail-servers.html](http://www.emailaddressmanager.com/tips/mail-servers.html)

I seem to recall googles port number not being standard though...
You might want to check the settings in your mail client.

---

### Post by ArgusVision on 2010-10-28
You can probably access that ACL list from webmin, but since I'm not right in front of it I can't remember exactly how to get there.

---

### Post by SeijiSensei on 2010-10-28
It sounds like you're proxying all traffic through Squid.  Is that really what you want (need) to do?  I only proxy HTTP and let all the other services connect directly by masquerading their private IP addresses at the router using iptables.  

Using a proxy cache like Squid only makes sense if you have a slow connection and lots of clients, where caching can improve performance, or where you want to control access to web services.  Most of the applications I have using Squid are designed for the latter purpose, for instance, blocking downloads of remote executable files by using Squid ACLs.

---

### Post by ArgusVision on 2010-10-28
I suppose you can Google easily as I can, but here are a couple of sites that might help.

[http://wiki.squid-cache.org/SquidFaq](http://wiki.squid-cache.org/SquidFaq)

[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by viperce on 2010-10-29
> **SeijiSensei said:**
> It sounds like you're proxying all traffic through Squid.  Is that really what you want (need) to do?  I only proxy HTTP and let all the other services connect directly by masquerading their private IP addresses at the router using iptables.  

Using a proxy cache like Squid only makes sense if you have a slow connection and lots of clients, where caching can improve performance, or where you want to control access to web services.  Most of the applications I have using Squid are designed for the latter purpose, for instance, blocking downloads of remote executable files by using Squid ACLs.


ye i wanted all the traffic to go through squid, is it not possible to forward traffic on port 110 or 995  through to my router/Internet & bypassing squid?

---

### Post by viperce on 2010-10-29
thanks for all the help Argus.....i added all the ports to the acl list rebooted & it still does not work :(
any other ideas?

---

### Post by viperce on 2010-10-29
just something i picked up while i been trying to sort this out, a few weeks ago i installed a program called firestarter in ubuntu desktop & setup connection sharing through firestarter, for a few minutes it was actually working all traffic on 110 & 993 were being routed directly to webmail & gmail. i got all excited thinking finally i solved the problem then it stopped working (i did not change any settings) and i have been trying ever since to get it going again with no luck :'(

---

### Post by viperce on 2010-10-29
is it posible to do this with masquerading in linux?

---

### Post by SeijiSensei on 2010-10-29
> **viperce said:**
> is it posible to do this with masquerading in linux?

Yes, that was the point of my earlier posting.

If eth0 points to the outside interface and eth1 points to the inside interface, then a simple iptables rule like this

```
iptables -t nat -A POSTROUTING -i eth1 -o eth0 -j MASQUERADE
```

will rewrite the source address of all traffic sent from inside to outside so it looks like it's coming from the router itself.  That's how most routers handle outbound traffic today.  As I said, there are good reasons to use Squid in some circumstances, but it's not really designed to proxy all traffic.

There are lots of howto articles on iptables and NAT; just Google.

---

