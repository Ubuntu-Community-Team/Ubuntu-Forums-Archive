---
title: "What runlevels for MySQL (using sysvconfig)"
date: 2005-01-27
forum: Server Platforms
---

### Post by Toasty on 2005-01-27
I am installing / configuring MySQL and since Ubuntu doesn't have chkconfig (the instructions I have are for RedHat) I have had to install sysvconfig to set the runlevel. My question is what should I set the MySQL runlevels to?

Currently the settings for MySQL are:

Runlevel  -  Value
      0       -    K20
      1       -    K20
      2       -    S20
      3       -    S20
      4       -    S20
      5       -    S20
      6       -    K20

When looking at the next stage of the config it seems that at least runlevel 3 should be S90, please can someone help...

Thanks. And, sorry if the above is a bit vague.

---

### Post by Rottweiler on 2005-02-02
[QUOTE=Toasty]
  Runlevel  -  Value
        0       -    K20
        1       -    K20
        2       -    S20
        3       -    S20
        4       -    S20
        5       -    S20
        6       -    K20
  
 When looking at the next stage of the config it seems that at least runlevel 3 should be S90, please can someone help...[/QUOTE]Perhaps I'm not understanding your question, but is there a problem with the runlevels above? All the multiuser runlevels are S20 which would normaly be fine. Is there some reason you need to change it?
  
 The runlevel '3' stuff you're probably reading is specific to Red Hat. Ubuntu boots to runlevel 2 normally and there's no particular reason to change it. Just make sure '2' is set like you want. I'm not aware of any particular problem with the defaults.

---

### Post by Toasty on 2005-02-02
Thanks Rottweiler!! I was just following guide... I'll take your advice and just make sure runlevel 2 is set right.

---

