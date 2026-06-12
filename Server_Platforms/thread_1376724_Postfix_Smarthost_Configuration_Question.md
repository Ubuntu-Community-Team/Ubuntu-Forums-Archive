---
title: "Postfix Smarthost Configuration Question"
date: 2010-01-09
forum: Server Platforms
---

### Post by nycterfin on 2010-01-09
Hello.  Sorry if this has been answered elsewhere on the forums but I've searched around here on the forums and google for a definitive answer to my question but still haven't found one.  I was wondering if I were to configure postfix with a smarthost (I believe that's the term, but I could be wrong as I'm still new to this) to relay mail through my ISP's (comcast, which requires you to authenticate with a username and password as far as I can gather) smtp server will the from: field of emails sent from email accounts (say [email]user@mydomain.tld[/email]) handled by postfix have [email]user@mydomain.tld[/email] or will it have [email]customer@smtp.comcast.net[/email].  Hopefully it appears that the email originated from [email]user@mydomain.tld[/email], but if that is not the case is there a workaround to achieve desired results, preferably a workaround that does not have attached a monthly fee?

Thank you for your time and effort in advance.

---

### Post by noway2 on 2010-01-09
It will appear from user@yourdomain.  If you look at the detailed headers it will show as passing through your ISP's smtp server in addition to all the other hops along the route.

You may not need to log in to relay through their SMTP server.  Being attached to their network may be enough as they may have a my_networks parameter set in their allow configuration.

---

### Post by nycterfin on 2010-01-09
Thank you, noway2.  That was just the answer that I was looking for.  I've got two more questions now.  The MX records for my domain should be pointed at the IP on which the computer running postfix is, correct?  And you mentioned reading the headers of the emails.  How would I do this?

Thanks again in advance.

---

### Post by noway2 on 2010-01-10
Yes, the MX should point to the mail server(s).  I put that in plural as you can run back up servers in which case the priority number in the MX record will be lower.

As far as checking the headers, you email program will have a setting for that, under views or options.  For example, I use Evolution and under view I set it to display all headers.

---

