---
title: "apache2: php not parsing"
date: 2010-10-18
forum: Server Platforms
---

### Post by bobdobbs on 2010-10-18
Hi all.

I've reinstalled my system and installed apache. I've installed php5. 'a2enmod php5' returns with a message telling me that php5 is already enabled.

However, this code does not parse:

```

</php
phpinfo() ;
/>

```

I get a blank page. When I view the source code for the page, I see the php code.

How do I get php to work?

---

### Post by BkkBonanza on 2010-10-18
Umm. Don't use </ ... /> use <? and ?>

---

### Post by bobdobbs on 2010-10-18
> **BkkBonanza said:**
> Umm. Don't use </ ... /> use <? and ?>

*facepalm*

Christ I'm a dumbass sometimes.

Thanks.

---

### Post by SeijiSensei on 2010-10-18
Can you mark this "solved" now, Bob?

---

