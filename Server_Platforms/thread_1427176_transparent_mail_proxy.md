---
title: "transparent mail proxy"
date: 2010-03-11
forum: Server Platforms
---

### Post by matji on 2010-03-11
Hi 

We have a small office network with an ubuntu server gateway and some win clients. Our mail server is at the ISP. I want to save all the incoming and outgoing mail messages. It would be great if the clients dont need to change their settings in email client programs.

What program should I use? Can I configure postfix or other mail server to work as a transparent proxy?? Is there a tutorial??

Thanks in advence!

---

### Post by HubertB on 2010-03-11
You have to configure your MTA (which happens to be postfix, exim or whatever you like) to use a smarthost. In your case, your smarthost is your ISPs mail server. Unfortunately, I don't know how to setup a configuration like this, but googling for "postfix smarthost" should get you close to the solution :-)

---

### Post by matji on 2010-03-12
Thank you!
Finally I found something.
I redirected in iptables the 25 port to gateway 25 port where postfix listen. In postfix.conf I added the 

always_bcc = [EMAIL="xy@example.org"]xy@example.org[/EMAIL]

line and now all mail sent by the client. I receive at [EMAIL="xy@example.org"]xy@example.org[/EMAIL] and I dont need to reconfigure my clients.
I have to do something with the received mails too.

---

