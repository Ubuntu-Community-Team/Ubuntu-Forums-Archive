---
title: "adding new domains to BIND"
date: 2012-12-12
forum: Server Platforms
---

### Post by Toriku on 2012-12-12
I have a DNS chache/primary server running on my network, it seems to work fine, I can type in its name into my browser and it points to its own apache server, but I want to add another domain for another apache server on the network. (Ultimately I want to achieve virtual hosting on this second machine as well).

 It isn't clear how I add more domains from all the material I've found on the internet, does it need its own zone or not for eg. How can I add another domain and IP to the servers records?

---

### Post by SeijiSensei on 2012-12-12
Yes, you will need another zone file, and a "zone" declaration in named.conf that points to the zone file.

```

zone "example.com" IN {
     type master;
     file "zone.example.com";
};

```

Make sure you have all the required semicolons; named is very picky about that.

---

