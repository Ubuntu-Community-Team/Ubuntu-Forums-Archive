---
title: "domain name"
date: 2009-07-02
forum: The Cafe
---

### Post by zorocke on 2009-07-02
I'm thinking about setting up a server, but I am a little confused about domain names. Can I host my own domain name using bind 9 or would I still need to register it somewhere?

---

### Post by Sublime Porte on 2009-07-02
Do you actually have a need to host the dns service itself?

Perhaps you mean you just want to map a domain name to your box's ip?

You only need bind if you're going to run your own dns server, so you can manage your own dns, for instance if you had a block of ip addresses and needed to manage dns for them.

---

### Post by Dr. C on 2009-07-02
You would need:

1) To register your domain in a top level domain eg .com, .net, .org etc. or your country code eg .ca, .us, .co.uk etc. This is accomplished by using a domain registrar.

2) 2 static IP's for the domain's DNS (Domain Name Servers) They can be both on the same box.

3) A server with suitable software. Ubuntu running Bind9 is just fine for this.

---

### Post by .Maleficus. on 2009-07-02
Or, you can go with a dynamic DNS provider and not worry about any of that.  Check out [DynDNS]("http://www.dyndns.com/").

---

