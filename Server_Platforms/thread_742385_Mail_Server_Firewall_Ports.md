---
title: "Mail Server Firewall Ports"
date: 2008-04-01
forum: Server Platforms
---

### Post by Deathrend on 2008-04-01
I've looked around, and probably looked right over this a few times, but I'm rather stummped.

I have an older PC running Ubuntu 7.10 server, with the Mail server setup from the start, I'm wanting to know exactly what ports I should forward from my ASA to it (For both SSL, and normal IMAP, as well as the ports needed to communicate with other mail servers.

I feel really stupid asking this qestion, as I should probably know it, but I'm tired of guessing, want someone to check my work, per-say.  I'm wanting to host my own IMAP server for my iPhone, currently I use Gmail, and RoundCube (Pointing at gmail) for normal usage (Which is running on another server running LMAP.

Thanks

---

### Post by MJN on 2008-04-02
You will incoming and outgoing port 25 open for SMTP, and possibly incoming port 587 (mail submission port) should you find your remote clients are sat behind ISPs that block outgoing port 25.

For IMAP you will need incoming port 143 which will support unencrypted IMAP access as well as encrypted with the client establishing a TLS connection once connected (using STARTTLS). IMAPS, i.e. IMAP over SSL with the tunnel established first, has its own port of 993.

Mathew

---

### Post by Deathrend on 2008-04-02
I'm stumped then, according to my ASA config, it should work, I currently have:

tcp/imap4 (143)
tcp/smtp (25)
tcp/993
tcp/587

So it seems that I should be able to connect from the outside :/

---

### Post by MJN on 2008-04-02
Yup...

Assuming it is opens up the necessary outgoing ephemeral ports for the responses to get back out.

(I've no experience of the ASA (assuming you're talking about the Cisco piece of security kit) and so cannot comment on whether this is an issue requiring explicit configuration).

Mathew

---

### Post by Deathrend on 2008-04-02
Yes, sorry, Cisco ASA5505.  For now, no outgoing ports are blocked.  I'm wondering if maybe it's just the setup in the mail server.

I could also just be looking over something reallly simple.  What exactly do you have to do to make a user an e-mail, or is it just done by default on a mail server?  I've spent way to many years around exchange..

---

### Post by Deathrend on 2008-04-02
So, I found the "Mail" group, apon adding myself to it, the mail now gets to the server, however I still can't authenticate to it from outside the box.  Using the "mail" command shows me all of my current mail however.

Stumped again -_-

---

