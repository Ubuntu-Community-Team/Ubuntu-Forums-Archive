---
title: "Why are there so many versions of wine in use?"
date: 2012-05-18
forum: The Cafe
---

### Post by Chiel92 on 2012-05-18
Hi,

Don't know if this is the right place to discuss this, but I think it won't annoy anyone here :)
I wonder why the older versions of wine are not covered by the newer ones.
Some application run only on older versions, but not on the newest release.
Why is that? :???:

---

### Post by Bandit on 2012-05-18
Because when you fix one thing in WINE it breaks compatibility with other windows programs. Thus not a single version of wine works with every program. So you end up having to have 2 or 3 versions some times to get your win software to function their best.

---

### Post by EnGorDiaz on 2012-05-18
> **Bandit said:**
> Because when you fix one thing in WINE it breaks compatibility with other windows programs. Thus not a single version of wine works with every program. So you end up having to have 2 or 3 versions some times to get your win software to function their best.

i dont get that though do they have to break code to make way for new programs thats abit dumb to be honest and it isnt really a compatibility layer if that is being done

---

### Post by bruno9779 on 2012-05-18
> **EnGorDiaz said:**
> i dont get that though do they have to break code to make way for new programs thats abit dumb to be honest and it isnt really a compatibility layer if that is being done

Wine is mostly based on reverse engineering, Windows source isn't exactly Open, you know?

If Windows was an Open source project, a full compatibility layer would have probably been finished years ago, and it would only need maintaining and some eventual bug-fixes.

---

### Post by Chiel92 on 2012-05-18
> **bruno9779 said:**
> Wine is mostly based on reverse engineering, Windows source isn't exactly Open, you know?

If Windows was an Open source project, a full compatibility layer would have probably been finished years ago, and it would only need maintaining and some eventual bug-fixes.

I see the problem. Thanks for your reply!

So if I get it right: 
developing wine = coding blindly and see if it works afterwards. And if it doesnt work, then modify the code in a smart way, such that it might work... 

(pretty wearisome business ;) )

---

### Post by Bandit on 2012-05-18
> **Chiel92 said:**
> 
So if I get it right: 
developing wine = coding blindly and see if it works afterwards.

Yep. When they change or add something in the code to make a different program work, sometimes that breaks a previous program from working like it should or at all.

---

### Post by sloggerkhan on 2012-05-18
Lots of windows software doesn't even work in the same ways between different versions of windows and other bits of windows have insane special cases to maintain support for the way some legacy apps abuse their API. I think there's a famous case of on API pretending to let an Adobe app patch core OS stuff at runtime just so it would keep working on newer versions of Windows.

---

### Post by donkyhotay on 2012-05-18
Even windows itself often loses backwards compatibility between versions. I had a friend that had lots of trouble trying to play old DOS games using winXP until I showed him DOSbox works. I have another friend that had more issues playing starcraft(1) on win7 then I did with wine. Now you take wine into the mix which is reverse engineered without the original source code, updates much more often, it's no surprise different versions work better with various programs. It's one thing I like about playonlinux, it really helps to compartmentalize all the various versions of wine. It's kind of a waste of space but HDD's are cheap these days and it's better then the headache of a wine update breaking a program that was working right and took forever to configure in the first place.

---

### Post by georgelappies on 2012-05-18
> **donkyhotay said:**
> Even windows itself often loses backwards compatibility between versions. I had a friend that had lots of trouble trying to play old DOS games using winXP until I showed him DOSbox works. I have another friend that had more issues playing starcraft(1) on win7 then I did with wine. Now you take wine into the mix which is reverse engineered without the original source code, updates much more often, it's no surprise different versions work better with various programs. It's one thing I like about playonlinux, it really helps to compartmentalize all the various versions of wine. It's kind of a waste of space but HDD's are cheap these days and it's better then the headache of a wine update breaking a program that was working right and took forever to configure in the first place.

Playonlinux is the way to go for sure.

---

