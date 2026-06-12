---
title: "Problem with mail server"
date: 2009-04-01
forum: Server Platforms
---

### Post by lamme on 2009-04-01
Hey I have recently started a mail server on my Ubuntu 8.04 (hardy heron) machine and need some help with mail server. I have Postfix, Dovecot, and Squirrel mail. I can send a message via squirrelmail to my own localhost but not to other domains and other networks. Can anyone tell me what I need to do to send and recieve email with others? Thanks

---

### Post by HermanAB on 2009-04-01
Most mail problems are due to a bad DNS configuration.  You must have a static IP address, A, PTR and MX records, otherwise your mail will be bounced by everyone you send it to.

---

### Post by lamme on 2009-04-01
I have a static ip address, but can you tell me how to create and setup the MX records and everything else we need?  I have searched everywhere and have got no where...I appreciate the help, Thanks

---

### Post by hictio on 2009-04-01
> **lamme said:**
> I have a static ip address, but can you tell me how to create and setup the MX records and everything else we need?  I have searched everywhere and have got no where...I appreciate the help, Thanks

Start by reading this [Email Services](https://help.ubuntu.com/8.04/serverguide/C/email-services.html), the chapter 13, of the [Ubuntu Server Guide](https://help.ubuntu.com/8.04/serverguide/C/index.html).

Do you have a domain already? If you do, who handles it? Can you use their service to setup all the DNS info (MX, PTR, A records).

---

### Post by LiQuidAiR on 2009-04-08
> **lamme said:**
> Hey I have recently started a mail server on my Ubuntu 8.04 (hardy heron) machine and need some help with mail server. I have Postfix, Dovecot, and Squirrel mail. I can send a message via squirrelmail to my own localhost but not to other domains and other networks. Can anyone tell me what I need to do to send and recieve email with others? Thanks

First, how are you connecting to your server?  Are you on the actual server using a monitor and keyboard or using a remote management tool such as SSH?

I'll gather some MX record data to show.

---

### Post by LiQuidAiR on 2009-04-08
Can you post your bind configuration?

usually located at /etc/bind/

If you've made any customization to these files please post them here and let me analyze them.

---

### Post by hyper_ch on 2009-04-08
herman: static ips are not required. If one has no static IP the mail just needs to be relayed.

---

