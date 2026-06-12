---
title: "Firefox shows saved passwords without authentication"
date: 2010-10-08
forum: Security
---

### Post by blagosphere on 2010-10-08
if you go to Edit > prefs > security  and choose to show saved passwords they are displayed without entering root pw. This seems to be a huge security hole. How do we fix this?

---

### Post by The Cog on 2010-10-08
Firefox keeps its saved passwords in/under your home directory. There is no need for the "root" or admin password to gain access. In fact, even users who don't have access to root are allowed to use firefox. 

Firefox does however have an option to password protect all the passwords (Edit -> Preferences -> Security -> Use a master password) in which case you have to enter the master password every time you start firefox. Once started, I can't remember if it wants the password again before you use "show passswords" on not. It would probably be better if it did, just in case someone else gets to your desk while you're away getting a coffee.

---

### Post by bodhi.zazen on 2010-10-08
Either that, or encrypt your home directory.

---

### Post by lovinglinux on 2010-10-08
Is not a security hole, is a convenience option. As already explained, you can encrypt Firefox's passwords using a Master password. Just look for that option in FF's preferences Security tab.

---

### Post by blagosphere on 2010-10-10
Convenience is a good thing; however, i find i am unable to say yes to anyone who needs to "hop onto the internet" using my computer anymore. Requiring a master pass to open FF is a bit much. The option needs some tweaking IMO

---

### Post by bodhi.zazen on 2010-10-11
> **blagosphere said:**
> Convenience is a good thing; however, i find i am unable to say yes to anyone who needs to "hop onto the internet" using my computer anymore. Requiring a master pass to open FF is a bit much. The option needs some tweaking IMO

Indeed.

If you wish to share your computer, check out the "guest" account.

---

### Post by lovinglinux on 2010-10-11
> **bodhi.zazen said:**
> Indeed.

If you wish to share your computer, check out the "guest" account.

You could also create a Firefox guest profile.

---

### Post by bodhi.zazen on 2010-10-11
> **lovinglinux said:**
> You could also create a Firefox guest profile.

True.

I am always shocked by these kinds of threads. It is as if the light bulb is going off for the first time.

"Hey if someone access my computer / account s/he has access to my data".

Physical access = root access and the only "real" protection one has is encryption.

Alternates to encryption include separate accounts (one per user) , guest accounts, and Linux permissions.

---

### Post by Elfy on 2010-10-11
You could also, of course, not actually use the option.

---

