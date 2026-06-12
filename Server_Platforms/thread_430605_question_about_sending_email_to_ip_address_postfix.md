---
title: "question about sending email to ip address postfix"
date: 2007-05-02
forum: Server Platforms
---

### Post by nephish on 2007-05-02
lo there, 
i am using postfix as our company email server, 
it seems to be working just fine, except when i try to use it to send an email out of the lan to an ip address.

for example 1234@123.456.789.123
will fail
but [email]1234@somedomain.com[/email] 
will work.

is there something i can do about this ?

thanks

---

### Post by MJN on 2007-05-02
Sure - wrap the IP address in [ ] e.g. **1234@[123.456.789.123]** then Postfix won't perform an MX lookup on the 'domain'.

Mathew

---

### Post by nephish on 2007-05-02
wow, thanks, 
will put it to use tomorrow.

---

