---
title: "howto restart ufw with every dsl &quot;redial&quot; ?"
date: 2008-07-28
forum: Security
---

### Post by _xymox_ on 2008-07-28
hi there.

my first post.. i an like to thank for this great forum and the useres..
till now.. i found everything here discussed but now i got a (i think) easy to solve question.
hope that i hit the right section.

i use ufw for my dsl connection...

but every time.. i get a 24h disconnect ufw gets disabled..

is there a easy way. got get ufw enabled or restarted at a redial?

tried to add code to some scripts. but it looks like i didn't found the right one...

every suggestions is appreciated.

thanks alot!

---

### Post by compiledkernel on 2008-07-28
best I could figure would be to time it right. Assuming you can figure out when the 24h dialout drops occur, you could just cron the restart of ufw to accomodate this. Of course, nothing is so simplistic as that, but that would be a start.

---

### Post by _xymox_ on 2008-07-28
thanks,

but this does not look like a reliable solution for my problem to me.

i used to use openbsd and freebsd as firewall..
hey had scripts like ppp-up ppp-down... 
wich got called after the connection opens or drops... 

is there anything similar in ubuntu?

---

### Post by kdorf on 2008-07-28
If you put an executable script in /etc/network/if-pre-up.d/ it should execute right before an interface comes up (your dsl).

---

### Post by _xymox_ on 2008-07-28
that sound like something i looked for,
thanks a lot kdorf,

to start the firewall.. if-up.d sounds more logic to me.. 
because the interface is up then, or am i wrong?

---

### Post by kdorf on 2008-07-28
It doesn't really matter a whole lot. The only difference is "if-pre-up.d" starts BEFORE your connection is active, and if-up.d starts immediately after.

---

