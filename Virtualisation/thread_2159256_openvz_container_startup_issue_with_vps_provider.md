---
title: "openvz container startup issue with vps provider"
date: 2013-07-02
forum: Virtualisation
---

### Post by flakzeus on 2013-07-02
I rent a small openvz container from a company for which the last several years has worked fine. Well, yesterday it decided to bite the dust. I can use the console to get access to the server but networking and hardly any of the services are starting up. nginx and mariadb are starting but there is no networking and if I run "runlevel" it will return "unknown". 

This is 11.04 natty. 

If I could startup networking manually and copy the data off, I'd be happy.

---

### Post by Habitual on 2013-07-02
This provider you pay money to provide support?

---

### Post by CharlesA on 2013-07-05
Natty is EoL. Why you'd run a non LTS release on a VPS, is beyond me.

Granted that doesn't help your situation, as Natty has been End of life since October 28, 2012, you haven't been receiving any updates.

See if you can work with the provider to get a backup of your data and then go from there.

---

