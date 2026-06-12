---
title: "will pre release versions be upgraded to the final release version via APT"
date: 2018-02-04
forum: Ubuntu Development Version
---

### Post by Andrew_Welham on 2018-02-04
If i start some work on the Ubuntu 18.04 version after (March 1st, 2018 &#8211; Feature Freeze), will it updated via apt bring this version up the final release state when available ?
Many Thanks

---

### Post by flocculant on 2018-02-04
what do you mean 'start some work' ?

an installed 18.04 will get updates to it's packages until it is released - then it will receive updates as is normal for a released version.

---

### Post by Andrew_Welham on 2018-02-04
Apologies, for any confusion what i mean is, will the pre release version be the same as the final released version when the apt updates are applied.

For example if i started work on a production server on a release candidate , will it be the same as the final release (using apt update released by the the the product goes live), of will i need to start again with the production release

---

### Post by flocculant on 2018-02-04
Should be - though with updates coming through more regularly now there is no guarantee that what you see now is what will be the final release.

I'd not use the current state in production - what happens if something fails spectacularly and you can't gain any access to it ... 

Bear in mind that, ignoring some wrong titles in this sub-forum, Ubuntu doesn't do Alpha's, Ubuntu dev releases are all pre-Final Beta (when they actually test a milestone)

---

### Post by Andrew_Welham on 2018-02-04
i would not put it into production. Simply want to me ahead of the curve for when the final release is available. Thanks for info though

---

