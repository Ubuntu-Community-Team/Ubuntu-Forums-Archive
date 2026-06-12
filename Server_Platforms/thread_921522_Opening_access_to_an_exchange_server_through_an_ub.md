---
title: "Opening access to an exchange server through an ubuntu router/firewall"
date: 2008-09-16
forum: Server Platforms
---

### Post by fowie on 2008-09-16
I've got a Hardy Server running as my entire home's gateway/router.  It is also used as a firewall, webserver, svn server, ssh, ftp, imap, pop3, smtp, and (internal only) samba server.  However, I needed an exchange server.  I took a second box and set up M$ 2003 server and Exchange.  From inside the LAN it's working great, now I need to open the exchange server to the outside so I can access it from the internet.  So here are the points I'm not quite clear on:

1 - What ports do I need to open for Exchange (probably not the best place to ask this one, so I'm ok if you can't answer that, I'll find that somewhere else)

2 - I've already got clients using IMAP and POP3 for certain domains that my server controls, and I don't want to switch those over to exchange.  Can I specify an iptables rule to forward only traffic for certain domains to the exchange server?  Can you give me an example of that?

So, what forwarding rules do I need to set up so that [email]someone@domain1.com[/email] gets forwarded to the exchange server, but [email]someoneelse@domain2.com[/email] gets handled by the imap server on the ubuntu box like it currently is?

---

### Post by Drezard on 2008-09-17
thats a hard one. do you have a PUBLIC ip shared between them or one each?

---

### Post by fowie on 2008-09-17
I have one public IP that goes to the webserver/firewall/router, and then the exchange server has a static internal IP (192.168.etc.etc...) because it is connected to the internal NIC of the webserver/firewall/router.

---

### Post by koenn on 2008-09-17
Most people I know would never ever under any circomstances consider making an Exchange server accessible to the internet.

your question 1- re what ports, depends on what you want the exchange to do, i.e. what protocols you want it to use. Normally, you only want it to use smtp to send and receive internet mail, and/or pop3 to act as a post office. That's the same config as a normal mail server. 

re 2. you don't route mail by means of a firewall or a router. You use DNS MX records to indicate that 
mail for domain1.com is handled by exchange.domain1.com, and 
mail for domain2.com is handled by mail.domain2.com 
(or whatever names your servers have) 
and the mail servers will work it out by themselves. that's what smtp does.
obviously, you also need a dns solution because apart from the MX records, the servers still need to find out what address exchange.domain1.com and mail.domain2.com are at.

---

### Post by fowie on 2008-09-17
re:re:2  The MX records are already set up and pointing at my public IP address.  The problem is that the exchange server is behind that IP address (behind the firewall/webserver/router box) on a private IP, so the MX records are correct in pointing to the public IP, but once the SMTP request gets to the public IP server, that server needs to know to forward them on to an internal server.  That's the part I'm not sure about.

---

### Post by koenn on 2008-09-17
> **fowie said:**
> re:re:2  The MX records are already set up and pointing at my public IP address.  The problem is that the exchange server is behind that IP address (behind the firewall/webserver/router box) on a private IP, so the MX records are correct in pointing to the public IP, but once the SMTP request gets to the public IP server, that server needs to know to forward them on to an internal server.  That's the part I'm not sure about.
Oh, you're using NAT. I see.

You can't handle this with anything on IP or TCP level (i.e. iptables/packet filtering, port forwarding, routing) because the distinction between the two servers / mail domains happens at application level (i.e. smtp) [unless you have externel LDAP/AD clients, but that's unlikely, in which case you could probably use portmapping. here are some port numbers : [http://searchexchange.techtarget.com/tip/1,289483,sid43_gci1124126,00.html](http://searchexchange.techtarget.com/tip/1,289483,sid43_gci1124126,00.html) ]

Anyway, the usual solution is to let smtp handle this, because smtp is best suited to map mail servers to mail domains. 
This means that on your router/firewall/gateway you'll run a mail server (smtp) that is configured to  accept mail for both domain1.com and domain2.com, and is configured for relaying. According to the final destination of each individual mail msg, it will lookup (DNS MX) which mail server it should relay to, and send it there. This requires internal DNS with MX records that return the real, private addresses of those mail servers.
Be careful not to make it an open relay, i.e. a relay that accepts anything from anywhere and is willing to send it anywhere else. Your relay should only accept mail for your domains.

Since you already have an smtp server, I wonder if you could apply the above concept to it so that mail.domain2.com also accepts mail for domain2.com and relays it to exchange.domain1.com as wel as be final destination for mail destined for domain2.com.
In that case, your firewall should simply direct all smtp (dest port 25) to (address of) mail.domain2.com.

---

### Post by fowie on 2008-09-17
Ok, I'll try that.  What about the other exchange-only services (namely calendaring, possibly webmail) that are using ports that I'm not really using on the external server, what IPtables rule would I need to forward those ports through to the internal exchange server?

---

### Post by koenn on 2008-09-17
> **fowie said:**
> Ok, I'll try that.  What about the other exchange-only services (namely calendaring, possibly webmail) that are using ports that I'm not really using on the external server, what IPtables rule would I need to forward those ports through to the internal exchange server?

webmail is web, http. port 80/tcp. 

exchange can act as an ordinary mail server (smtp, pop3). 

exchange is also a groupware server, that's where all the extras come in. Usually, these are used in an active directory domain where the Exchange users are authenticated by the domain controller, and use MS Outlook to access the Exchange server. That's where all this non-mail connections / port numbers come in (check the link I posted), to let Outlook access shared calenders, public mail folders, mange contact lists, and do all that integration stuff like inviting people to a meeting by mail after  checking their calender for free time and booking a meeting room with overhead projector in the process.
I'm not sure you really want to do this over the internet, I'm not even  sure you actually can.

---

### Post by fowie on 2008-09-17
Yes, you can do it, my university does it for all full-time employees.  That's what I need, but I just wanted an actual code example of what the rule should look like to forward one of those "accessory" ports through to an internal IP.

---

### Post by koenn on 2008-09-17
> **fowie said:**
> Yes, you can do it, my university does it for all full-time employees.  That's what I need, but I just wanted an actual code example of what the rule should look like to forward one of those "accessory" ports through to an internal IP.

roughly something like
```

IF_WAN="eth0"


for P in 112233 445566 12345; do
    iptables -t nat -A PREROUTING -i $IF_WAN -p tcp --dport $P -j DNAT --to-destination 192.168.20.10
done


```
translates to: packets coming in on the WAN-interface (eth0) with a destination port $P tcp, send them to (the same tcp port at) address 192.168.20.10 
note that te list of ports is entirely bogus.

man iptables for more explanations and options

---

### Post by tomasq on 2008-09-17
> **koenn said:**
> webmail is web, http. port 80/tcp. 

exchange can act as an ordinary mail server (smtp, pop3). 

exchange is also a groupware server, that's where all the extras come in. Usually, these are used in an active directory domain where the Exchange users are authenticated by the domain controller, and use MS Outlook to access the Exchange server. That's where all this non-mail connections / port numbers come in (check the link I posted), to let Outlook access shared calenders, public mail folders, mange contact lists, and do all that integration stuff like inviting people to a meeting by mail after  checking their calender for free time and booking a meeting room with overhead projector in the process.
I'm not sure you really want to do this over the internet, I'm not even  sure you actually can.

Exchange allows this now with RPC over HTTP which requires (default configuration) ports 80 and/or 443. It can be placed in a non-encrypted mode for testing, or use SSL for production.

Other than your default HTTP(S) ports, you would not need to open additional ports to your Exchange server (or in most cases, a front-end server) to handle this functionality.

---

### Post by koenn on 2008-09-18
> **tomasq said:**
> Exchange allows this now with RPC over HTTP which requires (default configuration) ports 80 and/or 443. It can be placed in a non-encrypted mode for testing, or use SSL for production.

Other than your default HTTP(S) ports, you would not need to open additional ports to your Exchange server (or in most cases, a front-end server) to handle this functionality.

Didn't know that, thanks.

---

### Post by fowie on 2008-10-01
Ok, and good way to test and see if my packets are really being forwarded to the internal machine?

---

