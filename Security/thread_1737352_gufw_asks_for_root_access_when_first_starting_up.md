---
title: "gufw asks for root access when first starting up?"
date: 2011-04-23
forum: Security
---

### Post by Mojo McCracken on 2011-04-23
I just installed gufw and was in quite a hurry. A root acces prompt came up as I started gufw for the first time, and I quickly responded with appropriate password. All I saw in this hurry was that it had something to do with the usr/share directory.

So, here's my question: Does gufw require root access when first starting up? And if so, why?

Thanks in advance.

---

### Post by Paddy Landau on 2011-04-23
Unlike a Windows setup, you do not install a firewall. Linux comes with a built-in firewall. All firewall programs (including gufw) are simply ways to *access* the firewall in order to make changes.

Therefore, when you start gufw, it needs root access in order to make any changes. When you exit gufw, the changes remain, because gufw is not a firewall but rather access to the Linux firewall.

So, yes, you need root access whenever you start gufw, but you do not need to start gufw to start the firewall.

BTW, the firewall rules are stored in something called *iptables*. If you make a real mess-up, I believe you can reset to the default settings with the command
```
sudo iptables -F
```

---

### Post by Rubi1200 on 2011-04-23
Just to add to what Paddy Landau has already said, here are some links with very useful information; definitely worth taking the time to read.
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Mojo McCracken on 2011-04-23
Thanks for the answers, although I was quite aware that gufw wasn't the actual firewall.

One thing I can't figure out, though is why gufw only need me to enter me password once. Is this stored for gufw to access when starting up again?

---

### Post by Paddy Landau on 2011-04-23
When you enter your password, the system remembers it (by default 15 minutes I think). After 15 minutes, you would have to enter it again.

However, once gufw has been given the go-ahead, you won't have to enter your password again until you close gufw even if it is more than 15 minutes.

Some programs are more careful than this; for example the Ubuntu Software Centre.

---

### Post by Mojo McCracken on 2011-04-23
I see. Thanks a bunch and have a nice day!

---

### Post by Paddy Landau on 2011-04-23
Pleasure. You too.

Please mark the thread as Solved if we have answered your questions. Thanks.

---

