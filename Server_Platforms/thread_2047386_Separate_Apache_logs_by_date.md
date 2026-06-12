---
title: "Separate Apache logs by date"
date: 2012-08-24
forum: Server Platforms
---

### Post by deekthesqueak on 2012-08-24
Currently I am using log rotate to manage my apache logs.  I am looking to move my logs into a folder structure that represents the current date.

So currently logs get put in /var/log/apache2/ and get rotated every day with logrotate

What I would like to do is /var/log/apache2/<year>/<month>/<day>/{access, error}.log

Is this something apache can do by default or do I need to use logrotate with the right directives?

---

### Post by SeijiSensei on 2012-08-25
I think the answer is none of the above.  You'd probably need to write a custom bash script to do that.

---

