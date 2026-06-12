---
title: "help me configure BIND9"
date: 2008-07-26
forum: Server Platforms
---

### Post by maxidrom11 on 2008-07-26
I am migrating from shared hosting to dedicated server ...

I encounter many problems configuring DNS with BIND9 

I have Ubuntu Server

I already installed apache2-php5-mysql 

I have domains registered at godaddy.com 

How do I configure stuff using BIND 9 to point my godaddy domains to the server. I need at least two NS records  
NS1.domain.com 
NS2.domain.com 
how do I do this? please show me the way step by step

---

### Post by windependence on 2008-07-26
You don't need a DNS server at all to do what you want. Go into the Godaddy control panel for your domains and set up your DNS there. If you get stuck, call them, they are very good at helping you get set up.

Once again, you do NOT need to run BIND9 at all. Just set up your A record at Godaddy and use their nameservers.

-Tim

---

