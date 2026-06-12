---
title: "Why is the net-tools not included by default?"
date: 2020-06-16
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2020-06-16
For a desktop client i can understand not including this package, but in a server environment why would you not want to be able to run the [FONT=courier new]ifconfig[/FONT] command is there a pre-installed alternative?

---

### Post by The Cog on 2020-06-16
I think ifconfig is deprecated, and the ip command set (such as **ip address show** or **ip -s addr sh**) are the replacement.

---

### Post by TheFu on 2020-06-16
**ifconfig** has been deprecated for years, replaced by **ip**.
**man ip** to learn more.

---

### Post by pqwoerituytrueiwoq on 2020-06-16
Thanks

---

