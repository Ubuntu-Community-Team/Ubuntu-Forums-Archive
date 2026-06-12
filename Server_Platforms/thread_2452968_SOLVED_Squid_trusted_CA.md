---
title: "SOLVED Squid trusted CA?"
date: 2020-10-31
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2020-10-31
I've got a squid proxy running in Docker. I did my own CA and it's doing the ssl bump / peek and slice. I'm wondering can I buy a cert for it same way one does a website so that it works transparently and I could invisibly proxy my whole lan without having to import certs to each machine / browser?

---

### Post by LHammonds on 2020-10-31
If you have your own certificate authority, why isn't the root from that server set as trusted on all of your LAN machines?  Kinda defeats the point of having an internal CA.

Does the domain exist on the Internet?
If so, you could use Let's Encrypt to automate the cert renewal (for free).
If not, you need to use your internal CA and setup the trusts.

LHammonds

---

### Post by SeijiSensei on 2020-10-31
> **Tadaen_Sylvermane said:**
> I've got a squid proxy running in Docker. I did my own CA and it's doing the ssl bump / peek and slice. I'm wondering can I buy a cert for it same way one does a website so that it works transparently and I could invisibly proxy my whole lan without having to import certs to each machine / browser?
Last time I looked into this for a client I used a self-signed certificate on the server and on the client. However there are a number of discussions about using a Let's Encrypt certificate with Squid: [https://www.google.com/search?q=letsencrypt+squid+proxy](https://www.google.com/search?q=letsencrypt+squid+proxy). Clients wouldn't need a certificate in this case I suspect, since LE certs can be used on regular SSL websites like my [https://www.politicsbythenumbers.org/](https://www.politicsbythenumbers.org/).

---

### Post by Tadaen_Sylvermane on 2020-10-31
> [COLOR=#000000]If you have your own certificate authority, why isn't the root from that server set as trusted on all of your LAN machines? Kinda defeats the point of having an internal CA.[/COLOR][COLOR=#000000]

I do and that's how it's working at the moment. I was hoping to find a way that wouldn't involve me putting a cert on each machine, just using one of the commercial authorities so that I could transparently do my whole lan without a whisper. But the more I think about it the more I realize that is likely not possible, and or should be due to how easy it would be for someone with nefarious purposes to do whatever they come up with.

This is just an at home setup for a max of 6 people, 3 families of 2 in 3 separate buildings but on the same piece of land and same internet connection, 6-7 computers total. The goal was to maximize what little bandwidth we have available here. Our internet options are limited in this area so every extra kb i can free up is that much more for someone to do something that isn't already proxied.[/COLOR]

---

### Post by Tadaen_Sylvermane on 2020-11-01
I just went ahead and stuck with my own CA. Put a reminder on my calendar to make new cert in 11 months and wrote a script to make it easy. 

Some other googling suggested that what I was looking for isn't really possible due to how ssl works.

Got my whole lan save one Mac on the proxy.

---

### Post by LHammonds on 2020-11-01
> **Tadaen_Sylvermane said:**
> I just went ahead and stuck with my own CA. Put a reminder on my calendar to make new cert in 11 months and wrote a script to make it easy.
You should only need to import the root CA onto each machine one time.  From that point forward, any certs issued by the CA will be trusted.  I would issue a cert that was valid for 10 years and be done with it. ;)

LHammonds

---

