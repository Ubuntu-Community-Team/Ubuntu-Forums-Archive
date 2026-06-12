---
title: "Capital Letter in User Name?"
date: 2011-08-31
forum: The Cafe
---

### Post by Zethioth on 2011-08-31
So, I wanted to put this in this thread because it's a simple matter. But how come I can't capitalize the first letter? I like to grammatically correct, and whenever I log on I hate saying my name in all lower-cases. It's annoying. Is their a way to change it?

---

### Post by lykwydchykyn on 2011-08-31
Well, I would assume that restriction is there for a reason, so I can't vouch that you won't have problems doing this, but try this at a terminal:
```

sudo adduser --force-badname MyName

```

Then follow the prompts to complete the information.

---

### Post by BrokenKingpin on 2011-09-02
Depending on your login manager you can have it list all the users using the full name instead of the actual username. Then you can just click the user and put in the password.

---

