---
title: "How to send emails from Virtualbox guest with VM hostname instead of VM IP in header"
date: 2015-04-24
forum: Virtualisation
---

### Post by cyber4994 on 2015-04-24
Hi all,

I tried to send emails from an Ubuntu Virtualbox guest with an email client (not a server).

The header of messages sent does not contain the VM hostname but the VM IP address :

Received from   [10.0.2.15] ([my IP address]) [...]
X-ME-Helo        [10.0.2.15]

I first tried NAT mode and then Bridged networking mode, but same result...

Is there a solution to display the VM hostname instead of the VM IP address ?

Thank you.

---

### Post by SeijiSensei on 2015-04-24
The upstream SMTP server has to be able to resolve your IP address into a hostname.  Otherwise you'll get the numeric address in headers.

I'd imagine it would work better in bridged mode, if the upstream server knows to use your router as its DNS resolver.  Modern routers can act as a DNS server for the hosts they serve via DHCP.  Adding an entry to the upstream server's /etc/hosts for your IP and hostname might also help, but I can't say for sure.

---

### Post by cyber4994 on 2015-04-24
Hi SeijiSensei,

What do you mean exactly by upstream server ? I do not have access to the SMTP server, that is owned by my ISP.

I modified the hosts file of the VM host, but no result in NAT mode nor in Bridge mode.

Are you sure that the upstream SMTP server has to be able to resolve the VM IP address into a hostname ?

Should not this hostname be directly transmitted by the email client to the SMTP server ?

Thanks.

---

### Post by cyber4994 on 2015-04-25
Hi all,

I still think about my problem... It looks like a trivial question, but I have found no thread nor tutorial about it.

In Bridged mode, the VM is like another computer on the network.

Usually, when your computer is behind a router or an ADSL box using NAT, its hostname is well mentionned in email headers sent with an email client like Thunderbird.

So the problem could rather come from Virtualbox and/or its network adaptaters.

If someone managed to send emails from a Virtualbox VM with its hostname in headers (rather than its IP address) I would very interested to know how, and others would also.

But perhaps it is just impossible, if Virtualbox prevents the VM to transmit its hostname.

---

### Post by SeijiSensei on 2015-04-25
> **cyber4994 said:**
> What do you mean exactly by upstream server ? I do not have access to the SMTP server, that is owned by my ISP.
First, you have to tell us how you are mailing these messages.  Are you using a mail client?  A command-line mailer like heirloom-mailx?  I presume it is configured to use the ISP's SMTP server as a relay host?

There are only two places headers are added.  One is by the email client during the process of composing the message.  The other is by any upstream SMTP servers, which will add the "Received" headers that appear at the top of the final message.  You can't control how those upstream machines treat your hostname and address.  If your IP does not resolve to a valid hostname, you're likely to see IP addresses in the headers they add.

If the VM is connected using bridged networking, there is no reason it should be treated any differently than a simple physical server on the same network.

You really need to show us a complete set of headers from one of these messages so we can tell what headers you are talking about.

---

### Post by cyber4994 on 2015-04-25
Hi SeijiSensei,

I own a computer behind a router, with a Virtualbox VM that runs Ubuntu. I try to send emails from this VM with a mail client (Thunderbird), using the SMTP server provided by my ISP.

As previously explained, it works fine, but the header of emails sent mentions the VM local IP address (10.0.2.15) instead of the VM hostname. Recipients who watch the header can read :

Received        from [SMTP hostname] ([SMTP IP address]) [...]
Received        from [10.0.2.15] ([my computer IP address]) [...]
X-ME-Helo      [10.0.2.15]
X-ME-Date      Sat, 25 Apr 2015 15:43:38 +0300
X-ME-IP         [my computer IP address]
MIME-Version  1.0

Even in Bridged networking, emails sent with Thunderbird do not contain the VM hostname but the VM local IP address in their header.

So I would like to know if there is something to change in Ubuntu and/or Virtualbox, in order to have headers sent with the VM hostname.

Thanks.

---

### Post by SeijiSensei on 2015-04-27
I'm guessing all of these headers were added by the ISP.  Mail servers can add any headers they want if they start with "X-".  I've never seen "X-ME," and it's certainly not something added by Thunderbird.  What's more puzzling is why your ISP sees your computer as having a 10 address.  Don't you have a router between you and the ISP?  It looks like your computer is talking directly to the ISP with its 10 address.  Usually the ISP would only see the public IP address on the outside of your router.

---

### Post by cyber4994 on 2015-04-27
I tried another SMTP server, with a regular account of course. In NAT mode and Bridged networking mode, emails headers are now :

Received from [SMTP hostname] ([SMTP IP address]) [...]
Received from [VM IP address] (unknown [my computer IP address]) [...]
MIME-Version 1.0

The hostname is always absent, and this is even clearly indicated ("unknow"). No "X-ME", so these additions were well added by the previous SMTP server.

As my computer is behind a router (so there is well a router between me and my ISP), I also tried a direct connection to Internet, however the result is exactly the same.

I suppose that SMTP servers see the VM as having a 10 address because they are able to know its existence but unable to obtain its hostname. So the problem could well come from Virtualbox and/or its network adaptaters.

If someone managed to send emails from a Virtualbox VM with its hostname in headers, please just tell us !

Thanks.

---

