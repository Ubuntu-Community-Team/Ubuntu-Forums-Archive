---
title: "Samba 4 as a PDC / Ubuntu - Zentyal HOME DIRECTORIES no access."
date: 2014-11-18
forum: Server Platforms
---

### Post by george84 on 2014-11-18
Just wondering if anyone here has any experience with using Samba4 as a domain controller under Ubuntu. I am using Zentyal specifically but the same would apply to someone that applied the Zentyal packages to an Ubuntu install. I have everything working more or less right but there is a strange problem with the home directories not mapping and even when specifying the path it fails to access it.

Im not sure if this is the proper forum for this but it's worth a try. I have written on the Zentyal forums but haven't gotten anything useful yet.

---

### Post by joebeasley on 2014-11-20
Check the [samba]("https://www.samba.org/samba/docs/using_samba/ch09.html") manual to make sure your settings for [home] are correct.

---

