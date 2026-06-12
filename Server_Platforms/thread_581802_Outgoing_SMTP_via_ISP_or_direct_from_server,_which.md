---
title: "Outgoing SMTP via ISP or direct from server, which do you recommend."
date: 2007-10-19
forum: Server Platforms
---

### Post by maw1key on 2007-10-19
Hi All,

While I am setting up my Postfix server I was trying to decide wether or not to use my ISP as the outgoing SMTP server or just use our machine.

The machine has plenty of power: opteron dual core with 2Gb memory on a tyan MB, so I don't think that any overhead of sending the mail directly from the machine would slow it down.

I am more interested in the pros and cons of both.

I know that if I use my ISP's server it would be responsable for the queing of the mail and lessen the risk of being accidentally blocked by spam blockers, but we would be reliant on a 3rd party server for outgoing.  This should be no big deal though we get our service from XO communications.

Thanks in advance and I am sure I will have more questions to follow.

---

### Post by MJN on 2007-10-19
There would be little, or no, performance differences either way as your server still needs to have an SMTP dialogue with your ISP's mail server just as it would the destination mail server if 'dealing direct'. Okay, there's no DNS lookups to be done and your ISP's might be close (on-net) however this is not all that relevant.

The key differences, in my mind, are as you've touched on - reliance on a 3rd party and the risk of blacklists. This latter point goes both ways though - if you're on, say, a dynamic IP then you're gonna be on a whole load of RBLs that list such ranges whereas your ISP's mail server won't be. That said, your ISP's mail sever is also used by all its other customers and hence may (will?) from time to time be put on other RBLs due to abuse.

All in all if you're on a static IP then I'd say go for it. If not use your ISP as a relayhost.

Mathew

---

### Post by maw1key on 2007-10-19
Thank you Mathew,

You have a good point and yes we do have a static IP so, I am going to set it up to send SMTP outgoing instead of using our ISP.

I can always change it at a latter date.

---

### Post by johng4 on 2007-10-20
I always opt to use my SMTP servers since I can authenticate to them no matter what ISP I may be using, and I tend to be fairly mobile.

Otherwise I use my ISP's SMTP for simplicity sake.

---

