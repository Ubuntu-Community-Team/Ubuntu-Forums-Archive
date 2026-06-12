---
title: "How to Schedule Email in Ubuntu?"
date: 2010-06-17
forum: Server Platforms
---

### Post by rstackhouse on 2010-06-17
I have Postfix and Procmail installed on Hardy. 

Are there any tips/tutorials for sending out scheduled email?

My main use case for this would be sending out a Tweet and an email at the same time.

Any help would be greatly appreciated.

Thanks,

Robert

---

### Post by Bachstelze on 2010-06-17
You can do that in a cron job:

```
* * * * * echo "Message." | mail -s Subject foo@bar.org
```

Of if you need soething more sophisticated, do a shell script and run thzt in cron.

---

### Post by rstackhouse on 2010-06-17
I guess I was pretty vague in my earlier description. I was looking for a way to delay sending one off emails by h hours and m minutes.

---

### Post by rstackhouse on 2010-06-17
This may be what I was looking for. Replacing curl w sendmail: [http://www.marksanborn.net/howto/schedule-a-tweet-with-one-comnand-in-linux/](http://www.marksanborn.net/howto/schedule-a-tweet-with-one-comnand-in-linux/)

---

