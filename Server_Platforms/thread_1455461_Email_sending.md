---
title: "Email sending"
date: 2010-04-16
forum: Server Platforms
---

### Post by fortune2008 on 2010-04-16
Can someone tell me a reason why only two domains email that i send doesnt go to the spam folder in yahoo all the others go to spam

---

### Post by fortune2008 on 2010-04-16
This is what i was really trying to say

```
All mail i sent from other domains in my virtual host is being reconized as spam but my server is at chatalker.com any mail from lets say from chatalker.com,triniwiz.com,wizdigg.info isn't notice as spam but my other domains like trinivybz.com and so on the emails are seen as spam by yahoo and others.

this is what my txt record look like
[CODE]v=spf1 a ptr ip4:190.93.75.216 mx:mail.chatalker.com ~all
```[/CODE]

---

### Post by HermanAB on 2010-04-16
Use 'dig' to test your DNS and ensure that you have a PTR record for all domains.

---

### Post by fortune2008 on 2010-04-16
whats dig

---

### Post by lisati on 2010-04-16
You might also want to check if the domain names are listed on a black list somewhere, which isn't necessarily your fault. Have a look at [http://debouncer.com](http://debouncer.com)

---

