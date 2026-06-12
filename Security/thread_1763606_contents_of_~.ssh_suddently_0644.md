---
title: "contents of ~/.ssh suddently 0644"
date: 2011-05-20
forum: Security
---

### Post by colonelmandrake on 2011-05-20
Hello,

Earlier today I could successfully ssh into various servers using private key authentication as per usual.

Then I did these things:

* allow another user to view my desktop via remote desktop
* install regex-utils deb from here: [http://www.nongnu.org/regex-markup/](http://www.nongnu.org/regex-markup/)
* install rkhunter package and run sudo rkhunter --check and sudo rkhunter --update (yes in that order)

When I then tried to ssh into another server, ssh complained my key had permissions 0644! WTF.

Should I be worried?

Thanks for your attention,
Col. M

---

### Post by wojox on 2011-05-20
Reset the keys:

```
sudo chmod 600 ~/.ssh/id_rsa
sudo chmod 600 ~/.ssh/id_rsa.pub
```

Reset hosts:

```
sudo chmod 644 ~/.ssh/known_hosts
```

Reset directory:

```
sudo chmod 755 ~/.ssh
```

---

### Post by colonelmandrake on 2011-05-20
> **wojox said:**
> Reset the keys:

```
sudo chmod 600 ~/.ssh/id_rsa
sudo chmod 600 ~/.ssh/id_rsa.pub
```

Reset hosts:

```
sudo chmod 644 ~/.ssh/known_hosts
```

Reset directory:

```
sudo chmod 755 ~/.ssh
```

Thanks for your speedy reply!

Actually I know how to fix the permissions, but I am worried that my key was compromised. Any idea why it suddenly had the wrong permissions?

Thanks
Col. M

---

### Post by wojox on 2011-05-21
> **colonelmandrake said:**
> Thanks for your speedy reply!

Actually I know how to fix the permissions, but I am worried that my key was compromised. Any idea why it suddenly had the wrong permissions?

Thanks
Col. M

Well Col. M installing regex-utils wouldn't do that. rkhunter checks file permissions, I don't think it would change them. At least not without confirmation. I don't run rkhunter, is there a log file you could look at?

Maybe it was your friend just messing with you through VNC. :p

---

