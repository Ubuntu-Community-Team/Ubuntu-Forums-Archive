---
title: "Create A or CNAME Record using RNDC utility"
date: 2008-01-03
forum: Server Platforms
---

### Post by sujathab on 2008-01-03
Hi all,

I am totally new to RNDC concepts. I need to create a A record or CNAME record for a zone using rndc utility from a command prompt.

What is the command i should execute in the prompt to add the record?

how do i check with a command whether it has been added or not?

Any help is very much appreciated. I am totally struck.

Thanks a lot

Sujatha

---

### Post by andol on 2008-01-03
Are you sure rndc is the tool you want? Gotten the impression that it is primarily to start, stop, refresh, etc etc the daemon. How about taking a look at nsupdate?

---

