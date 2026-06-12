---
title: "access.log available over HTTP = bad idea?"
date: 2009-01-22
forum: Server Platforms
---

### Post by swharden on 2009-01-22
Is there any reason NOT to make access.log available via HTTP?  I'm thinking of making a PHP script which reads the last 20 lines of access.log and making it visible to the public for demonstration purposes.  Beside invading the privacy of certain people (showing IPs and perhaps what they Google for to find me), are there any problems this could be caused?  Is this dangerous??

---

### Post by Dr Small on 2009-01-22
I can't think of anything off the top of my head, other than the general public will be able to see who the last people were viewing your website, IP addresses, useragents and all.

I do this on my Dad's website (only, it shows the entire log for the day) and it sits behind a .htaccess file requiring authentication. But I would assume that it's OK so long as you don't care if people are viewing it.

---

