---
title: "Security/Privacy in Ubuntu"
date: 2006-04-29
forum: Server Platforms
---

### Post by Suslisko on 2006-04-29
I'm new to Linux and I have a few questions about privacy. What about web filtering like the one in Winlike firewalls. Cookie, Java, ActivX etc. and what about sending privet info by my browser? Are there applications in Ubuntu to control this ?  And the second thing I don't know if Firestarter is running when I log in. Can someone help. Thanks in advance

---

### Post by 23meg on 2006-04-29
Take a look at privoxy for filtering; it's in the repositories. Cookies and other browser-specific things operate as specified in your browser preferences and depend on your browser rather than your OS, so security and privacy-wise there isn't any theoretical difference between using a specific browser (Firefox?) in Ubuntu and another OS unless rare OS-specific security flaws arise, and those are quickly discovered and patched anyway.

Firestarter does run when you log in, with the options you last specified. You can check its status by typing ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by kaamos on 2006-04-29
> And the second thing I don't know if Firestarter is running when I log in. Can someone help. Thanks in advance
```
sudo /etc/init.d/firestarter status
```

---

### Post by Suslisko on 2006-04-29
Thanks for the info.

---

