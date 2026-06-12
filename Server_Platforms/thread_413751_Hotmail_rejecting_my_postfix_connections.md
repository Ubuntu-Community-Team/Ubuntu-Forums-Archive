---
title: "Hotmail rejecting my postfix connections"
date: 2007-04-19
forum: Server Platforms
---

### Post by vael on 2007-04-19
My mail server war running fine, but now I can send emails to anywhere, anydomain but hotmail is not accepting my connections. What can I do?

This are my last logs about it:

Apr 19 10:41:02 mailserver postfix/smtp[8766]: connect to mx3.hotmail.com[65.54.244.200]: Connection timed out (port 25)
Apr 19 10:41:32 mailserver postfix/smtp[8766]: connect to mx2.hotmail.com[65.54.244.168]: Connection timed out (port 25)
Apr 19 10:42:02 mailserver postfix/smtp[8766]: connect to mx4.hotmail.com[65.54.244.232]: Connection timed out (port 25)
Apr 19 10:42:03 mailserver postfix/smtp[8766]: 7C8E576409E: to=<lolis_saenz@hotmail.com>, relay=none, delay=1708, delays=1558/0.01/151/0, dsn=4.4.1, status=deferred (connect to mx4.hotmail.com[65.54.244.232]: Connection timed out)
Apr 19 10:56:47 mailserver postfix/smtp[9336]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Apr 19 10:56:47 mailserver postfix/smtp[9337]: connect to mx3.hotmail.com[65.54.245.72]: Connection timed out (port 25)
Apr 19 10:57:17 mailserver postfix/smtp[9336]: connect to mx2.hotmail.com[65.54.245.40]: Connection timed out (port 25)
Apr 19 10:57:17 mailserver postfix/smtp[9337]: connect to mx4.hotmail.com[65.54.245.104]: Connection timed out (port 25)

I have NOT changed configurations

Help
:confused:

Thanx

---

### Post by bmathis on 2007-04-19
If youre getting a NDR back from them stating that you cant send because of an internal list, then youre screwed. The only way to get off of that list is to pay them some money for their domain tools or wait about a month for them to take you off.

A couple of my domains get thrown on the list from time to time

---

### Post by MJN on 2007-04-20
It doesn't sound like he's getting as far as NDR's as there's no connection even being made.
 
Potential causes of this are numerous - Hotmail screwing up their MX records (again), Hotmail mail servers being swamped with incoming mail (again!), transient network problems between you and Hotmail's servers, or perhaps even your IP being on their blacklist (as mentioned above) however I would hope that Hotmail would reject at the SMTP stage rather than filtering at the network level (for all but the most known hardcore spammers).
 
Are you still having the difficulties or has it all passed now? You could try relaying via your ISP's SMTP server to partially rule out the spam trap and *possibly* the network troubles (depending on where your ISPs server sits).
 
Mathew

---

### Post by uid0 on 2007-04-20
Hmmmm.  

"Connection timed-out"

That usually means that you're not even making it through the initial TCP handshake.  Fire-up tcpdump or Wireshark and capture a connection attempt.   Sounds suspiciously like a firewall/IDS or router ACL might be the cause.

---

