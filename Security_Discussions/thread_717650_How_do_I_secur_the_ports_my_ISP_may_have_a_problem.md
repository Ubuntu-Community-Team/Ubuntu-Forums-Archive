---
title: "How do I secur the ports my ISP may have a problem with"
date: 2008-03-07
forum: Security Discussions
---

### Post by vsiege on 2008-03-07
I have a router that allows traffic to my server on a vaiety of the ports mentioned below. I was looking to secure my server some more but Im at a loss on how to do the. Below is is a table taken from my ISP security page. It is stated that they will scan for these issues:> Port 21: FTP - Unsecured Proxy Applications may allow third parties to "bounce" through your computer to another part of the Internet, making it appear to orginate from YOUR computer. Also, many anonymous FTP servers have serious security holes in them which may allow an attacker to gain control of your PC.
Port 23: Telnet - Some "WinGate" type proxy applications open the default telnet port and may allow proxy attacks.
Port 25: SMTP - Unsecured Mail Servers may allow Hijacking - This is when a third party relays mail through your mail server (usually it's Spam) without your permission. Our scanning process DOES attempt to test your mail server to see if it is vulnerable to third-party relay. If your mail server is found to be open to third party mail relay, the accounts 'root', 'postmaster', and 'administrator' @your.ip.address will receive a mail message about what steps you MUST take to secure your machine.
Port 80: WWW - Some proxy applications can be used in Denial of Service attacks on other websites (such as "pay" sites). An attacker can "bounce" through your server, and then attack a third party, again making it appear as if YOU were the attacker. Some proxies also allow "pass-through" applications, such as SMTP and NNTP, to occur to your default SMTP or NNTP server. This allows outside parties to utilize Road Runner resources to spam, again making it look as if YOU are the culprit.
Port 80: Nimda Virus - Nimda is a complex mass mailing virus which spreads itself in attachments called README.EXE which can affect Windows 95, 98, ME, NT4, and 2000 users. This scan is to determine and notify the customers of their current infection if any.
Port 119: NNTP - Unsecured NNTP (News) Proxy servers can be used by spammers to send thousands of Usenet messages through your computer, to your news server, making it appear as if YOU had done it.
Port 81: WWW Proxy - Same as Port 80 above.
Port 1080: SOCKS versions 4 & 5 - Same as Port 80 above.
Port 3128: SQUID Web Proxy - Same as Port 80 above.
Port 4480: Proxy+ - Same as Port 80 above.
Port 6588: AnalogX - Same as Port 80 above.
Ports 8000, 8080, & 8081: WWW Proxy - Same as Port 80 above.Again,I dont have some of these ports open. At the moment I have 80, 25, 5900, 443 ,  20, 21 and 115.

---

### Post by Dr Small on 2008-03-07
So what is the problem?

---

### Post by vsiege on 2008-03-07
just looking to secure my server more.

---

### Post by Dr Small on 2008-03-07
As long as you make sure the services that the ports are open for, are tight and secure, you should have no problems.

---

### Post by vsiege on 2008-03-07
Well to be more specific:
How can I secure postfix (Port 25)?

What kind of malicious behavior can I stop over port 80?

---

