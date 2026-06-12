---
title: "How do I allowing all user sessions to use programs i installed with wine"
date: 2010-05-07
forum: Wine
---

### Post by Zireth ZH on 2010-05-07
I got a bunch of programs installed with wine but they dont appear on other user sessions... I created a session for my little brother as "desktop user" the only thing that wine shows is notepad.. i cant even browse the C:

---

### Post by cogadh on 2010-05-07
By default, Wine creates its fake Windows directory in the current user's home directory and all applications are installed there. Wine is not really designed to be used across multiple user accounts and technically if you want one app to be available to two different users, you have to install it twice; once under each user account.

However, it may be possible to use the wineprefixcreate command to create a fake Windows directory in a location shared by multiple user accounts. You would likely have to manually create all the shortcuts so that they are available to each user and I'm not sure how using a single Wine prefix with multiple users affects the Wine registry. You might be better off just doing the default and installing everything in each account.

---

### Post by Zireth ZH on 2010-05-07
bump

---

### Post by Zireth ZH on 2010-05-07
thats a prob..... the prob is that my home folder has only 4 gb free.. how do i increse this size?

---

### Post by cogadh on 2010-05-07
Did you set your home directory on its own partition with a fixed size? Otherwise, the only limit is the size of the hard drive you have Linux installed on and if that is reporting that you only have 4GB free, then your only option is to buy a bigger hard drive.

> **Zireth ZH said:**
> bump
Um, why?

---

