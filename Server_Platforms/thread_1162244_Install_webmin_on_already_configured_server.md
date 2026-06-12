---
title: "Install webmin on already configured server?"
date: 2009-05-17
forum: Server Platforms
---

### Post by lexthoonen on 2009-05-17
Hi,
 
i rent a dedicated server at fasthosts.co.uk (not for long anymore by the way) and it came with ubuntu 6.06 and their(?) matrix control panel. I set up some websites and users and databases etc. After a while I upgraded to ubuntu 8.10 which works fine, but the matrix panel thing doesn't work on it, I found out then.
 
Can I now install webmin and will it pick up the configurations so far? Or is there a way I can find out if it will? And worst scenario: could it destroy the current configuration?
 
(I know ispconfig is only to be installed on fresh/new servers)
 
Thanks.

---

### Post by zemon_ on 2009-05-17
I think you should only do this on a fresh install

---

### Post by bigbearomaha on 2009-05-17
because you asked...

Webmin can be installed on existing servers and will detect in most cases the current settings.. This is because Webmin uses the already existing config files for said apps and services.

 so If the config files in question are done a certain way, Webmin will merely show  you what is there.

---

### Post by lexthoonen on 2009-05-17
That sounds encouraging, thanks!
 
(because you replied...)

---

