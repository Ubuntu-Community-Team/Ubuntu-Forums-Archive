---
title: "MySQL Query output size"
date: 2010-03-30
forum: Server Platforms
---

### Post by unavenged on 2010-03-30
Hi,

If we do a query on our sever through PHPmyadmin we get 1300 records but through our PHP code we only get 1172... What could cause this and how could we get it to work right?

Thanks

---

### Post by Ryan Dwyer on 2010-03-30
It'll be something silly. For example, if you're using variables in your query the value might not be what you think it is. Or maybe the PHP code is filtering results after the query. Or maybe PHP isn't connecting to the server/database you think it is. Or maybe the code you're viewing isn't the same file you're accessing through Apache.

I know these sound stupid but they're worth checking.

---

