---
title: "Forgotten Thunderbird Master-Password"
date: 2011-01-23
forum: Security
---

### Post by Valkyr333 on 2011-01-23
Hi,

I seem to have forgotten my Master Password in Thunderbird. I created the password but now Thunderbird won't accept it, so I'm locked out of access to my mail and RSS when it comes to Thunderbird. I tried uninstall/reinstall, but the old settings remain and it still expects the same Master Password and obviously won't let me create a new one without it. If I want to fix this, is it safe to assume I need a 'purge' command to get rid of everything that my computer has for Thunderbird?

If so, what would that be? If not, what else would you recommend?

Thanks,

-Val

---

### Post by uRock on 2011-01-23
You may a faster fix at [Mozilla's Forums]("http://forums.mozillazine.org/index.php?c=4").

Cheers,
uRock

---

### Post by Dave_L on 2011-01-23
Thunderbird >> Tools >> Error Console

Paste in Code: 
```
openDialog('chrome://pippki/content/resetpassword.xul')
```

Click Evaluate.

That will produce a dialog asking whether you want to reset your master password.

---

### Post by Valkyr333 on 2011-01-25
> **Dave_L said:**
> Thunderbird >> Tools >> Error Console

Paste in Code: 
```
openDialog('chrome://pippki/content/resetpassword.xul')
```Click Evaluate.

That will produce a dialog asking whether you want to reset your master password.

Thanks, Dan! That fixed the problem completely.

All the best,

-Val

---

