---
title: "Extra SMTP to forward mail"
date: 2009-03-25
forum: Server Platforms
---

### Post by lucaspr on 2009-03-25
I've got a server at home. Some config specs:

Installed ubuntu 8.04.2 (called it vmwareserver) and installed VMware Server 2 
Virtual machine called zimserver installed Jeos 8.04 and Zimbra

IP Adresses vmwareserver : 192.168.7.240
            zimserver    : 192.168.7.242
            router       : 192.168.7.1
DNS is installed on the VMwareserver.
Port mapping : 2525 to 192.168.7.242

Now the problem. My ISP is blocking port 25. So I created an account by rollernet and configured things to set the forwarding of mail. But (of course) zimbra is listning to port 25 not 2525. My router is not capable of mapping outside port 2525 to inside port 25 (otherwise this thread would not be here :))

My thoughts:
configure Postfix to listen to 2525 on vmwareserver and forward mail from my domain to my zimbra server (port 25). Is this a working solution or (much simpler) can I just configure Zimbra to listen to port 2525?

Any thoughts?

---

### Post by BkkBonanza on 2009-03-25
I don't know about Zimbra so I can't comment on that. Most programs can configure their listening port so I don't know why it wouldn't be able.

But on a simple level. Most DNS registrars nowadays have a mail forwarding service. I know mine (name.com) provides that for free. I just use my DNS control panel to forward mail at my domain (or any of subdomain of course) to any place I wish. 

So eg. any mail for mail.mydomain.com port 25 gets forwarded to myhomeserverip port 2525. One setting and it's done, bypassing port 25. When any mail program tries to deliver mail to you it looks up the DNS and gets a server (at name.com in my case) which accepts the mail and forwards it to my ip:2525.

Seems like the easiest solution to me. Also some services offer backup mail servers  that will hold mail for you if your server is down and deliver it later. Perfect for dynamic ip sites.

---

### Post by lucaspr on 2009-03-27
> **BkkBonaza said:**
> I don't know about Zimbra so I can't comment on that. Most programs can configure their listening port so I don't know why it wouldn't be able.

But on a simple level. Most DNS registrars nowadays have a mail forwarding service. I know mine (name.com) provides that for free. I just use my DNS control panel to forward mail at my domain (or any of subdomain of course) to any place I wish. 

So eg. any mail for mail.mydomain.com port 25 gets forwarded to myhomeserverip port 2525. One setting and it's done, bypassing port 25. When any mail program tries to deliver mail to you it looks up the DNS and gets a server (at name.com in my case) which accepts the mail and forwards it to my ip:2525.

Seems like the easiest solution to me. Also some services offer backup mail servers  that will hold mail for you if your server is down and deliver it later. Perfect for dynamic ip sites.


I did just that. I only used rollernet.us for forwarding the mail to my home IP on port 2525. But my problem is my router. It just doesn't have an outside port and an inside port, in the port forwarding section. I it only capable of forwarding ports. the same on the internet as on my local lan. And Zimbra isn't accepting port 2525 (yet)... I don't know if it is capable of accepting mail on port 2525. Just the forwarding is on port 2525.

And if Zimbra is able to listen on port 2525, what about local delivery? That's why I would like another SMTP (postfix or sendmail or whatever) to accept the mail on port 2525 and send it to my Zimbra server on port 25. That way my local delivery won't change in any way. But maybe my thinking is wrong and it can all be done much easier.. I don't know :)

---

### Post by BkkBonanza on 2009-03-27
That's strange. All the routers I've used had two entries for port. One for incoming and one for where to forward to. But oh well.

You can use an iptables command to forward port 2525 to 25 within your own machine. I have this on my machine to handle a redirect for one of my virtualbox machines. The command below should work, but you also need these ports open if you are running a firewall on your machine. This command just routes the packets, but won't work if the ports are blocked.

iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 2525 -j REDIRECT --to-port 25

I believe to test this you need to run it sudo. You probably want it to boot with that rule in which case you could add it near the end of /etc/rc.local (which runs at the end of booting).

---

### Post by lucaspr on 2009-03-28
> **BkkBonaza said:**
> That's strange. All the routers I've used had two entries for port. One for incoming and one for where to forward to. But oh well.

You can use an iptables command to forward port 2525 to 25 within your own machine. I have this on my machine to handle a redirect for one of my virtualbox machines. The command below should work, but you also need these ports open if you are running a firewall on your machine. This command just routes the packets, but won't work if the ports are blocked.

iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 2525 -j REDIRECT --to-port 25

I believe to test this you need to run it sudo. You probably want it to boot with that rule in which case you could add it near the end of /etc/rc.local (which runs at the end of booting).

I should have checked this forum before starting searching this morning... Would have saved me a few hours iptables strugling. But as you suggested to rules in iptables were indeed sufficient. I opened up port 2525 in iptables and than added your line to redirect things....

Thanx for your answer though! I've I checked this thread earlier I would have know the answer sooner!! :D

Now I stumbled upon this page :

[http://www.go2linux.org/iptables-port-26-redirection-accept-email-on-another-port](http://www.go2linux.org/iptables-port-26-redirection-accept-email-on-another-port)
Which holds the same info!

(f.y.i. I have a Zyxel NBG460N which works like a charm, but does not have an internal port and external port just a port..)

---

