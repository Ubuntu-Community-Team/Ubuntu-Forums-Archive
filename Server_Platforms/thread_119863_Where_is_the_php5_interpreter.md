---
title: "Where is the php5 interpreter"
date: 2006-01-20
forum: Server Platforms
---

### Post by jezjones on 2006-01-20
Hi everyone,

I have installed Apache2, mysql 4 and php5 using Aptitude (and some command line apt but that is another story).

It all works!

Now i am trying to install Komodo as a trial to see if it is any good as a php IDE, or at least any better than bluefish or zend studio.

On configuring Komodo it asks for the location of the php interpreter as it cannot find it automatically.

I cannot find it either. It must be that as my apache server gives me the output of phpinfo(); and it was a clean OS install before that so nothing hanging around from the past.

I looked in aptitude to check on the installed files for php5 and it gives a few folders but they dont seem to contain it.

Can anyone point me in the right direction here.


Thanks

Jez

---

### Post by spartas on 2006-01-22
Open a terminal window and type the following. I don't use php5 yet, so I can't just tell you where it is.

```

which php

```

---

### Post by jezjones on 2006-01-23
Thanks for the suggestion, that was what i tried intially and there was nothing found.

The reason i was confused was that i had managed to get php5 on my machine being served from the local web server. It had to be php5 because there was no php before that (clean install).

I have solved this now by installing the php cli package.
Now when i do "which php" or php --version, it does give /usr/bin/php as expected.

Thanks for the help.

---

