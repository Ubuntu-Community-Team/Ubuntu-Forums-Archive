---
title: "Is PHP (Warty packages) XSLT enabled?"
date: 2005-04-27
forum: Server Platforms
---

### Post by istoyanov on 2005-04-27
I would like to know if the Warty PHP packages are compiled with the option ``–with-sablot'' or ``–with-xslt-sablot''.

Thanks for any hints.

---

### Post by CrustyDOD on 2005-04-27
[PHP]<?
echo phpinfo();
?>[/PHP] 
will tell you :)

---

### Post by istoyanov on 2005-04-27
I haven't installed PHP yet -- that's why I am asking:)

Has anyone gained some experience with Ubuntu PHP?

---

### Post by istoyanov on 2005-05-10
* bump *

---

### Post by LordHunter317 on 2005-05-10
It's in the php4-xslt package.
Searching in synaptic or using apt-cache search would have told you this.

---

### Post by istoyanov on 2005-05-12
[QUOTE=LordHunter317]It's in the php4-xslt package.
Searching in synaptic or using apt-cache search would have told you this.[/QUOTE]

Thanks a *LOT*, **LordHunter317**!!!

I just wasn't aware of XSLT being a separate package, so I asked...

Cheers \\:D/

---

