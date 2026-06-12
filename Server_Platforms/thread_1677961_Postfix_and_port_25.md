---
title: "Postfix and port 25"
date: 2011-01-29
forum: Server Platforms
---

### Post by MightyMe on 2011-01-29
I'm a NOOB setting up Postfix but managed quite well by following the Ubuntu Server guide. I have managed to set it up using SSL but testing a mail client like thunderbird I can also connect to port 25 using no authentication. Connecting using SSL on port 465 by editing "master.cf" file works but 25 i still open.

1. How do I prevent clients to connect to port 25 without authentication?

2. I guess I  have to have port 25 open in order to receive mail from the outside world?

Any help would be much appreciated.

---

### Post by lisati on 2011-01-29
This might help you: [http://www.howtoforge.com/forums/showthread.php?t=28301](http://www.howtoforge.com/forums/showthread.php?t=28301)

---

### Post by MightyMe on 2011-01-29
Thanks for the link. Done most of the things they say in there, so I guess my server is pretty secure. I just dont want to set my my mailserver as an open relay server thats all.
Being able to connect to port 25 without user credentials scared me a bit, but i'm coming from a ip address specified in the "mynetworks" paramter (in main.cf)  so I guess thats ok....?

---

