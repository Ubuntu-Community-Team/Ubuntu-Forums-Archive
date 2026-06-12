---
title: "List of CVE's, weekley check."
date: 2022-11-18
forum: Security
---

### Post by civilpolisen on 2022-11-18
We used to set up a tool and routines based on these things at [https://github.com/BBVA/ust2dsa](https://github.com/BBVA/ust2dsa)

We had this brilliant Whitelist check as well!

[PHP]$ debsecan --suite $(lsb_release --codename --short) --source https://raw.githubusercontent.com/BBVA/ust2dsa/data/ 
--whitelist fossa_whitelist.txt |grep -v fixed|grep -v "low urgency" |sort -n | uniq -u >> $(date +%Y-%m-%d).txt
[/PHP]

However, these things do no longer work. How can we replace this line of code in the script!?

---

