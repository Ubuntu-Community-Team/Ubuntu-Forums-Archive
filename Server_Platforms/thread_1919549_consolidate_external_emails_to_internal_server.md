---
title: "consolidate external emails to internal server"
date: 2012-02-03
forum: Server Platforms
---

### Post by Repus on 2012-02-03
> X-post since this looked like a more appropriate sub-forum.<


My family has dozens of email accounts scattered across many providers. I'm looking for a way to consolidate them to a local server while keeping the account individuality. 

What I am not looking for is a client solution, the idea isnt to be able to read all the email in a single program but instead to have our local server mirror the contents of the external accounts. 

Any ideas where to start?

Thanks

---

### Post by Repus on 2012-02-03
fetchmail & procmail perhapse? any thoughts?

---

### Post by SeijiSensei on 2012-02-03
[fetchmail]("http://www.fetchmail.info/") is definitely what you want.  It will poll all the servers, get the mail, and deliver it to local user accounts.  I don't think you need procmail for this.

---

### Post by Repus on 2012-02-06
> **SeijiSensei said:**
> [fetchmail]("http://www.fetchmail.info/") is definitely what you want.  It will poll all the servers, get the mail, and deliver it to local user accounts.  I don't think you need procmail for this.

Thanks. 

I should be getting around to it this weekend and will report back if anyone in the future cares to do this and searches the forum

---

### Post by HermanAB on 2012-02-06
Howdy,

Citadel has a fetchmail feature built right in.  So if you run the Easy Install script, then you can have your local mail server running in about 20 minutes.

---

