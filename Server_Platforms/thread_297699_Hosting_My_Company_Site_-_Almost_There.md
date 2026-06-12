---
title: "Hosting My Company Site - Almost There"
date: 2006-11-11
forum: Server Platforms
---

### Post by huggy77 on 2006-11-11
my linux server is built
apache, firestarter and email are running perfect.

have my static ip


now i have to put it on the outside - so i can hit it from anywhere with [www.foo.com](www.foo.com) and i have some questions.

?do i need a second level domain name?

?besides an A NAME, MX RECORD and CNAME what esle will i need to have at my disposal when i change my DNS info with go daddy?

?what ports should if forward with my router ?

i am about done with my bind setup... the above questions are based upon my actuallys seting up bind9 correctly...

any advice is welcome.

---

### Post by elst on 2006-11-12
If your DNS records are being hosted by an outside provider the only inbound connections you should allow are for the services that you want outside systems to access. Obviously ports 80 (HTTP) and 443 (HTTPS) for the Web server.

"www" should just be an DNS alias (CNAME) to the real server address - it's a convention to register www as a name for your main Web server, rather than a technical requirement as such.

"Email" covers several different things, so I can't really advise there without knowing what configuration you have.

---

### Post by huggy77 on 2006-11-13
for email i have a working courier/postfix setup that allows for imap and pop.  Are you saying that as long as i port forward correctly from the router i wont need bind?

---

### Post by rickyjones on 2006-11-13
If you're hosting the box at your office, and the DNS is with Godaddy, then I recommend the following:

* Create an A record for www - point this to your public IP.
* Create an MX record (preference = 10) and point this to your public IP address.

Now watch as it works :).

IF your public IP is dynamic then you'll want to use some sort of dynamic domain name system (dyndns.org for example) to keep track of it. Create a CNAME to this dymamic address and then point the MX/A records to this CNAME. Dirty, but it works.

-Richard

---

### Post by huggy77 on 2006-11-13
not dyanmic - the ip is static... i will try it out.

---

