---
title: "Outbound SMTP via postfix question"
date: 2010-05-26
forum: Server Platforms
---

### Post by Gaprofitt on 2010-05-26
:PHi All,

I have a question..

I have just built an internal postfix server for sending mail only, it's not accessible outside our network.  I will be sending from our domain, abc.com.  Rewriting the from field to abc.com is turned on in the postfix config.

A friend is telling me this will not work as they will do reverse lookups on our domain.  What does this mean?  Obviously the domain the email is sent from is a valid domain. If they do a lookup from the IP the mail came from it would be global crossing, our internet provider?  These outbound emails are critical client reports, I want to make sure they are not seen as spam.

Thanks,

Greg

---

### Post by m4tth3wv on 2010-05-26
Here's one example of why reverse DNS is helpful:

[http://www.spamhaus.org/faq/answers.lasso?section=ISP%20Spam%20Issues#128]("http://www.spamhaus.org/faq/answers.lasso?section=ISP%20Spam%20Issues#128")

---

