---
title: "Deleted computer from ubuntu one"
date: 2009-11-18
forum: Ubuntu One (CLOSED)
---

### Post by mpsz on 2009-11-18
HI I deleted my netbook from the list of computers in ubuntu one.
Now I want to add it again and I can't.
There's no add computer webpage.
I tried uninstalling and intalling again ubuntu one but nothing changed.

Any suggestion?

---

### Post by andrea000 on 2009-11-18
open the terminal applications->accessories->terminal
and run this command

> u1sync --authorize

the ubuntuone webpage should open asking you to add
your pc.

---

### Post by mpsz on 2009-11-19
Thanks! Worked perfect.:p
I have only on more problem, when the ubuntu client starts it has cheked the broadband use limit to 0.
So it can't connect until I uncheck it.
How can I change this to be permanent.

Regards,

---

### Post by joshuahoover on 2009-11-24
> **mpsz said:**
> Thanks! Worked perfect.:p
I have only on more problem, when the ubuntu client starts it has cheked the broadband use limit to 0.
So it can't connect until I uncheck it.
How can I change this to be permanent.

Regards,

This sounds like a problem that should be fixed in the latest PPA release. Can you do a system update, restart the Ubuntu One client, and try setting the bandwidth preference again?

Thank you,

Joshua

---

### Post by jakslev on 2009-11-24
> **andrea000 said:**
> open the terminal applications->accessories->terminal
and run this command



the ubuntuone webpage should open asking you to add
your pc.

Damn! you are not only hot.. you solved my problem!!!

---

### Post by Tiede on 2010-05-05
hmmm... andrea's fix seems to have done it (thanks)

However, when I first typed it in the terminal, I was told that the command could not be found and to install it using "apt-get install ubuntuone-client-tools"

I checked, and it appears it is not a dependency of ubuntunone... Out of curiosity, is this normal, joshua...

---

### Post by joshuahoover on 2010-05-05
> **Tiede said:**
> hmmm... andrea's fix seems to have done it (thanks)

However, when I first typed it in the terminal, I was told that the command could not be found and to install it using "apt-get install ubuntuone-client-tools"

I checked, and it appears it is not a dependency of ubuntunone... Out of curiosity, is this normal, joshua...

Yes, this is expected. The ubuntuone-client-tools package is separate because it's main purpose was to help with testing. In some edge cases, users have found it necessary to try to force authorization. The other way to force authorization is to delete the computers associated with your Ubuntu One account ([https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)), delete the "Ubuntu One token" in Applications->Accessories->Passwords and Encryption Keys, and then run "u1sdtool -c" in a terminal session. Again, either of these solutions (u1sync or the steps I outlined) should be necessary but with upgrades, server side issues, etc. they sometimes are.

Thank you,

Joshua

---

### Post by hellomezzy on 2010-05-06
thanks! I was having this problem also, but typing that into Terminal fixed it.

---

### Post by Tiede on 2010-05-06
> **joshuahoover said:**
> Yes, [t]he ubuntuone-client-tools package's main purpose was to help with testing.[..]
The other way to force authorization is to
[list]
[*]delete the computers associated with your Ubuntu One account ([https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)), [*]delete the "Ubuntu One token" in Applications->Accessories->Passwords and Encryption Keys, [*]and then run "u1sdtool -c" in a terminal session. [/list]

Joshua

Ok. Understood!
And, yes, btw, everything now works.

---

### Post by Kevin Kent on 2010-05-07
All working for me now. Thanks Andrea for fix.

---

