---
title: "Auto add to hosts.deny"
date: 2008-04-04
forum: Server Platforms
---

### Post by chris.davies on 2008-04-04
How do i go about stopping IP addresses (specifically mine) from being added to hosts.deny?

Regards,

Chris.

---

### Post by hyper_ch on 2008-04-04
put yours into hosts.allow ?

---

### Post by HermanAB on 2008-04-04
Simple, don't run whatever the heck it is that is doing that...

---

### Post by Oldsoldier2003 on 2008-04-04
> **hyper_ch said:**
> put yours into hosts.allow ?

+1
 It wont stop DenyHosts from adding you to the deny list but it will allow you to login since hosts.allow will overide hosts.deny

---

### Post by netlogic on 2008-04-04
> **HermanAB said:**
> Simple, don't run whatever the heck it is that is doing that...

LOL...
you are funny. I agree.

---

### Post by chris.davies on 2008-04-04
It seems im on the hosts.allow and hosts.deny list and still cant login via ssh.

Is it possible my server could be setup in the order 'deny,allow' checking the deny list and blocking my login because im on the deny list without even considering that im on the allow list?

How would i check this?

---

