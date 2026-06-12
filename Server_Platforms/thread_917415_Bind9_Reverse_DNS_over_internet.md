---
title: "Bind9 Reverse DNS over internet"
date: 2008-09-11
forum: Server Platforms
---

### Post by Geran on 2008-09-11
Hello.

I am trying to get my DNS server set up properly. So far so good, but the last obstacle is the PTR records. They will only work if I directly point myself to the DNS server as my DNS server from my computer, otherwise, no DNS records will come through. I'm guessing this is because of the company I used to register my DNS on the internet, but I'm wondering if it could be something else.

Please give any ideas.

G

---

### Post by Vegan on 2008-09-11
Have you tried using a top level DNS authority to check if you are properly being distributed?

Last time I reviewed the topic there were about 17 primary authoritative DNS hosts.

---

### Post by Geran on 2008-09-11
What exactly do you mean by top level DNS authority? A tool or website that analyzes your domain settings? I think I have, and it proves that I am not being properly distributed. Its becoming more and more certain that that is the issue, bad DNS registration, it was fairly cheap and I think it only provides basic features.

---

