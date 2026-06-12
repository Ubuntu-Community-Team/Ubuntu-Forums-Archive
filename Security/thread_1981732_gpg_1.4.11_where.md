---
title: "gpg 1.4.11 where?"
date: 2012-05-17
forum: Security
---

### Post by ottosykora on 2012-05-17
How can I install in 12.04 gpg 1.4.11 or 1.4.12?

It was removed from the repositories apparently?


I need allow compitibility with pgp263 and this is only possible with gpg 1 and not with gpg2.

---

### Post by thnewguy on 2012-05-17
The gpg application is available in the 12.04 repositories. You can install version 1.4.11 by running
sudo apt-get install gpg

---

### Post by Vereinfachen on 2012-05-17
thnewguy is wrong.

The package is called gnupg (it is version 1.4.11). :)

Install it using
```
sudo apt-get install gnupg
```

---

### Post by ottosykora on 2012-05-17
yes you are dead richt, I was also searching for gpg and this name is used for the gpg2 only apparently.

Thanks

---

