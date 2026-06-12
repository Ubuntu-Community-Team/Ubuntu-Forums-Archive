---
title: "questioned about mail server setup"
date: 2007-10-14
forum: Server Platforms
---

### Post by crazyone on 2007-10-14
hi i have been trying to setup a mail server but found out my isp blacks port 25. so what i was woundering if there is a way to get around it so i can setup a mail server for my website. thanks in advance.

---

### Post by MJN on 2007-10-14
You will need to elaborate more on what the situation is and what you want to do.

You say your ISP blocks port 25 - outgoing, incoming, or both?

What do you want your mail server to do - accept incoming mail, send outgoing mail, or both?

Do you have your own domain name? (only truly applicable for incoming mail purposes)

Mathew

---

### Post by crazyone on 2007-10-14
sorry about that. what i want to do with it is set it up so my email for my website and anything else i would want to setup a acount for i can manlly this way i dont get my main email spammed so i cna just delete the acount when it is getting spamed. form what i understand comcast blacks both incomming and outgoing. i would like to be able to get mail and send mail form it so i dont have to keep restting up accounts on gmail or yahoo. hope this helps . and thanks for the fast replie. and i ahve my own domain.

---

### Post by MJN on 2007-10-14
Much clearer now! :)

For your outgoing mail you will need to send it all via your ISP's SMTP server (they will allow port 25 access to this). If you are use Postfix as your MTA then the directive of interest here is [relayhost ]("http://www.postfix.org/postconf.5.html#relayhost") (you'd use something like **relayhost = [address.of.ISPs.server]**)

For incoming mail you have very few options. The most obvious that springs to mind is to use one of the many services that will accept mail on your behalf (i.e. you would point the MX records for your domain at their server(s)) and they will then establish another SMTP connection to your mail server (which should be listening on a different, not 25, port). One such service is no-ip.com's [MailReflector]("http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html") (I have no personal experience of this, or any similar service).

Make sense? Does it send you off in the right direction?

Mathew

---

### Post by crazyone on 2007-10-14
yea that helps alot jsut wondering for the smtp server would it be what i put into my email client like evolution or would i have ot find out what the accual ip address is.thanks again

---

### Post by MJN on 2007-10-14
Yep - same as your client - the name is fine (and preferable in case the IP changes).

Note you must wrap it in [ ] brackets - this stops Postfix looking up the MX records for the name (as it is the A record(s) that it needs).

Mathew

---

### Post by crazyone on 2007-10-14
thankyou for the help now its time for a mail server. lol

---

