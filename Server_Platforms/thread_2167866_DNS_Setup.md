---
title: "DNS Setup"
date: 2013-08-15
forum: Server Platforms
---

### Post by albert_wesker2 on 2013-08-15
I currently have setup on my server one domain [https://globalprivacysolutions.pw](https://globalprivacysolutions.pw) and have a master zone BIND dns record for it. I would like to set up another domain for another website of mine proactiveitsolutions.ca.

Now my question is do i need two different master zones for the two domains or can I enter in the host information for proactiveitsolutions.ca

---

### Post by SeijiSensei on 2013-08-16
Each domain requires a separate zone file with a corresponding "zone {}" entry in named.conf.

---

