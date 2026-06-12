---
title: "Fake UBUNTU repository!!!"
date: 2009-12-16
forum: Security
---

### Post by azlk on 2009-12-16
Please be informed, I've found this ***FAKE Ubuntu repository*** tonight while searching PEAR package:
**[COLOR=Red]http://packages.ubunut.com/[/COLOR]**
Pay attention to the end of URL!
I think it's worth to write email to abuse@... or somewhere else?
I'm afraid many beginners coming from windows are not used to be careful enough while surfing...

---

### Post by kostkon on 2009-12-16
It seems [to be legit]("http://www.whois.net/whois/ubunut.com")... Just redirects to packages.ubuntu.com.

---

### Post by insane_alien on 2009-12-16
its also owned by canonical.

---

### Post by cdenley on 2009-12-16
```

cdenley@ubuntu:~$ host packages.ubunut.com
packages.ubunut.com has address 91.189.94.219
cdenley@ubuntu:~$ host packages.ubuntu.com
packages.ubuntu.com has address 91.189.94.219

```

---

### Post by Seq on 2009-12-16
Also note this is why signed repositories are so important. If somebody mistyped that into their sources.list, they would have receive a warning when updating about not having a GPG key on-file for that repository.

---

