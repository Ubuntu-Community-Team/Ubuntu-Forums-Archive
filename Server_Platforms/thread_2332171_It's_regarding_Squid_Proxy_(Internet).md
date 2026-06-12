---
title: "It's regarding Squid Proxy (Internet)"
date: 2016-07-29
forum: Server Platforms
---

### Post by slkamath on 2016-07-29
Hi
  
We are using majority ubuntu systems in our premises.
  
We also use Ubuntu Server for internet with Squid Proxy. Recently we changed our mail server, because of this we have to give direct internet for every system. So my concern here is users can open any site because of direct internet. I checked with our mail providers they told us that through proxy mails will not work.
  
So how I can assign only for mails (like Thunderbird or any other mail client) full internet and while browsing internet should not work without proxy.

Thanks in advance

Lokesh Kamath

---

### Post by TheFu on 2016-07-29
Proxy mails don't work?  Huh?  What is a "proxy mails"?

Webmail will work through a proxy, just that the proxy won't be able to see inside SSL encrypted traffic without "special", often expensive, HW.  Read up on BlueCoat. It might be possible to install a cert on every system and have all SSL traffic get a MITM process so there are 2 SSL encrypted jumps.

email can be relayed from an internal postfix setup to external systems. This is how email works around the world.

So, please clarify what you mean.

---

### Post by SeijiSensei on 2016-07-29
Like TheFu, I can't really tell what happened from the description you provided.

First, programs like Thunderbird use protocols like SMTP, POP3 and IMAP.  Your Squid proxy would have to be weirdly configured for it to interfere with any traffic to these ports.  It should only be listening for traffic being sent to HTTP port 80 on external servers, and perhaps if you have the funky SSLBump stuff configured correctly, traffic to port 443 on external servers for HTTPS.  Perhaps you have your network configured to deny users access to the outside on any ports other than 80 and 443.  Can a desktop user telnet to a remote machine on an arbitrary port, e.g., "telnet gmail-smtp-in.l.google.com 25"?

Are you running Squid in "transparent" mode?  Does the proxy box use a firewall rule like
```
iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --destination-port 3128
```
Is the new mail server outside your local network, like at a hosting facility?  If so, you can add a rule that will forward traffic to that server before Squid touches it.  Suppose the remote server is 10.10.10.10.  Try a ruleset like this:
```
iptables -t nat -A PREROUTING -o eth0 -p tcp -d 10.10.10.10 -j ACCEPT
iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j REDIRECT --destination-port 3128
```
Does that help?  If not, we need a lot more information about how the network and its services are arranged.

---

### Post by Graham_Willis on 2016-07-30
**[COLOR=#000000][[B][COLOR=#000000]@slkamath:[/COLOR]**]("https://ubuntuforums.org/member.php?u=1032393")[/COLOR][/B] isn't it just a misunderstanding between you and your mail providers? Normally squid will have nothing to do with mail traffic and mail traffic will go as usual, that is as if squid was not there at all. But, on the other hand, we can't be sure, perhaps you have some kind of highly customized configuration. However, I suppose that you believed that all the traffic is proxied and you said it to your mail providers and it is why they gave you the response that it wouldn't work. However - it might be worth checking if webmails will work properly (and perhaps it is what your intended question actually was).

---

### Post by slkamath on 2016-08-01
Thanks for your reply.

It's not proxy mails, What i meant was If I put proxy server IP & Port in Thunderbird, Mails are not working. But for Internet If I put Proxy details in Firefox it's working.

We have TLS certificate for sending and receiving mails. Port # is 587. 

I hope I cleared my question.

Lokesh Kamath

---

### Post by slkamath on 2016-08-01
[COLOR=#000000]**SeijiSensei **[/COLOR]Thanks for your reply.

I configured proxy details in Thunderbird Preferences - Advanced - Network - Settings.
If I do the same thing in Firefox, Internet is working.

SMTP port we are using is 587

Lokesh Kamath

---

### Post by slkamath on 2016-08-01
[COLOR=#DD4814][COLOR=#000000][Graham_Willis]("https://ubuntuforums.org/member.php?u=2026579") [/COLOR][/COLOR][COLOR=#000000]Thanks for your reply.[/COLOR]

[COLOR=#000000]It's not proxy mails, What i meant was If I put proxy server IP & Port in Thunderbird, Mails are not working. But for Internet If I put Proxy details in Firefox it's working.[/COLOR]

[COLOR=#000000]We have TLS certificate for sending and receiving mails. Port # is 587. [/COLOR]

[COLOR=#000000]I hope I cleared my question.[/COLOR]

[COLOR=#000000]Lokesh Kamat[/COLOR]

---

### Post by SeijiSensei on 2016-08-01
It sounds to me like the firewall isn't configured to "masquerade" any outbound traffic.  Once again I'll ask, Can a desktop user telnet to a remote machine on an arbitrary port, e.g., "telnet gmail-smtp-in.l.google.com 25"?  More importantly, what about "telnet your.mail.server 587"?  

There's no reason to push this traffic through Squid.  Just let internal hosts connect directly to the mail server through the firewall.

Just to add more confusion, port 587 is for unencrypted mail submission.  SSL-secured SMTP services use port 465 unless the server operator has a non-standard configuration.  You should also need to connect to the server's IMAP port on 143, or to the SSL-secured IMAP service on port 993.

---

### Post by slkamath on 2016-08-02
Thanks once again [[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] 
[/COLOR]
When i try to telnet from desktop I am getting error message: telnet unable to connect remote host: connection timed out. (if the settings in proxy enabled)

If I give without proxy then it's giving message that connected to laxmielectronics.com

Lokesh Kamath

---

### Post by SeijiSensei on 2016-08-02
> **slkamath said:**
> Thanks once again [[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] 
[/COLOR]
When i try to telnet from desktop I am getting error message: telnet unable to connect remote host: connection timed out. (if the settings in proxy enabled)
What host are you trying to connect to?  On what port?  Again Squid shouldn't be having anything to do with this connection.

> If I give without proxy then it's giving message that connected to laxmielectronics.com.

Again what command did you use?  What server name?  What port?

Does that organization have some relationship to yours?  Is it the remote mail server?  You really need to provide some context to these answers because I at least am in the dark.

Are you responsible for the configuration of your network?  If not, you need to talk with whomever set up the firewalling.

---

### Post by slkamath on 2016-08-02
> **SeijiSensei said:**
> What host are you trying to connect to?  On what port?  Again Squid shouldn't be having anything to do with this connection.

I used the below command
[B]
telnet mail.laxmielectronics.com 587 [/B]


Again what command did you use?  What server name?  What port?

Does that organization have some relationship to yours?  Is it the remote mail server?  You really need to provide some context to these answers because I at least am in the dark.

**I work for laxmielectronics. We took hosting from bigrock.in **

Are you responsible for the configuration of your network?  If not, you need to talk with whomever set up the firewalling.

I am responsible for configuration. (We have already configured firewall, I am not the person who configured). 

We have put IP address in shorewall then only Full internet will work else we have to put proxy in that system, then only few sites will work.

Lokesh Kamath

---

### Post by SeijiSensei on 2016-08-04
> **slkamath said:**
> [B]I am responsible for configuration. (We have already configured firewall, I am not the person who configured). 
Once again the firewall is probably responsible.  Is it configured to masquerade outbound traffic to the Internet, for instance via a MASQUERADE rule in iptables?

> telnet mail.laxmielectronics.com 587 
Works for me:
```

$ telnet mail.laxmielectronics.com 587 
Trying 162.251.80.14...
Connected to laxmielectronics.com.
Escape character is '^]'.
220-cp-3.webhostbox.net ESMTP Exim 4.86_1 #1 Thu, 04 Aug 2016 12:11:54 +0000 
220-We do not authorize the use of this system to transport unsolicited, 
220 and/or bulk e-mail.

```

You need to talk to the person who configured the firewall.  It's blocking legitimate outbound traffic it should be passing (and masquerading).

---

### Post by slkamath on 2016-08-04
> **SeijiSensei said:**
> Once again the firewall is probably responsible.  Is it configured to masquerade outbound traffic to the Internet, for instance via a MASQUERADE rule in iptables?


Works for me:
```

$ telnet mail.laxmielectronics.com 587 
Trying 162.251.80.14...
Connected to laxmielectronics.com.
Escape character is '^]'.
220-cp-3.webhostbox.net ESMTP Exim 4.86_1 #1 Thu, 04 Aug 2016 12:11:54 +0000 
220-We do not authorize the use of this system to transport unsolicited, 
220 and/or bulk e-mail.

```

You need to talk to the person who configured the firewall.  It's blocking legitimate outbound traffic it should be passing (and masquerading).

**Thanks once again.**
Telnet is working for me too, but condition is i give that IP in shorewall - firewall rules and i have to full permission then only it will work. 

I want to thanks once again for your kind support. I will check with the person who has configured Firewall. If my problem will get solve I will update here.

Take care.

Lokesh Kamath

---

### Post by slkamath on 2016-08-16
Thanks to everyone.

My problem has solved. I did some changes in Shorewall. 

You can close the thread.

---

