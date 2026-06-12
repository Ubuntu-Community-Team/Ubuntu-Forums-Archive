---
title: "How to reset a User's password?"
date: 2016-06-01
forum: Ubuntu Studio
---

### Post by javierdl on 2016-06-01
I found this [instructions]("http://www.psychocats.net/ubuntu/resetpassword") for Ubuntu classic back in 2012. It advises to hold down Shift while booting up as the 1st step. Problem is doing that won't bring me to the alternative boot choices it says it would. 
How can I reset the password of one of my users then?

Thanks,

JDL

---

### Post by steeldriver on 2016-06-01
Booting to recovery mode is only necessary when you don't have any other means to execute commands with elevated (root) privileges, for example because you have lost your only administrative account password.

I assume since you are referring to "one of" your users, that is not the case here? so you should just be able to do
```

sudo passwd someuser

```

from your regular login shell

---

### Post by javierdl on 2016-06-01
Thank you so much steeldriver, that worked perfectly! :)

JDL

---

