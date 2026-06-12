---
title: "Update to language-pack-en-base has messed up locales"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by Irihapeti on 2016-03-26
Those of you who use a local other than en_US.UTF-8, en_AUS.UTF-8, en_UK.UTF-8, en_CA.UTF-8, please see [https://bugs.launchpad.net/ubuntu/+source/language-pack-en-base/+bug/1562279](https://bugs.launchpad.net/ubuntu/+source/language-pack-en-base/+bug/1562279)

To check if it affects you, run the command
```
locale
```

If you get a mixture of locales in the output, e.g. en_US.UTF-8 for some things and your own locale for others - or for that matter, en_US.UTF-8 for everything (and it's not what you're wanting to use), please click on "this bug affects me"

It's made a mess of my en_NZ.UTF-8 locale.

As included in the bug report, the "locale" command, after fiddling with Language Support, now shows:

```

LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_NZ.UTF-8
LC_TIME=en_NZ.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_NZ.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_NZ.UTF-8
LC_NAME=en_NZ.UTF-8
LC_ADDRESS=en_NZ.UTF-8
LC_TELEPHONE=en_NZ.UTF-8
LC_MEASUREMENT=en_NZ.UTF-8
LC_IDENTIFICATION=en_NZ.UTF-8
LC_ALL=

```

Immediately after the update, *everything* showed en_US.UTF-8

---

### Post by sudodus on 2016-03-27
Maybe this bug is related: [http://launchpad.net/bugs/1549529](http://launchpad.net/bugs/1549529) 'The keyboard is still installed as US-English even if another language is selected during the installation'

---

### Post by arapaho on 2016-04-01
Thank you for reporting. There is also perhaps related bug:
[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1560577](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1560577)

My problem is fixed. Solution in the above bug link. Restarting system might be needed.

Some useful commands
[http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue)

---

### Post by sudodus on 2016-04-01
Thanks *arapaho*, for linking to the bug report that solved your problem :-)

---

### Post by Irihapeti on 2016-04-01
Apparently, mine is not a bug but a feature. The idea seems to be to reduce the number of language packs needing to be maintained.

I probably need to install the latest daily ISO and see what defaults I get before I can make a meaningful comment.

---

