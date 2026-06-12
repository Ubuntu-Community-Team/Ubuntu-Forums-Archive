---
title: "Samba - &quot;share&quot; mode by default"
date: 2008-01-02
forum: Ubuntu Brainstorm
---

### Post by lunarcloud on 2008-01-02
Samba is great, but often I'll spend about a month on a new system wondering why all the other linux boxes in the house show up on my mac's shared section except mine. Then I remember that I have to use kcontrol to go set samba to "share" mode rather than "user" mode.

It should be "share" mode by default. I could understand if samba was installed by default that it'd be a potential security risk, but it isn't and it's a setting you cannot find in the system settings that the everyday user will see. To properly share folders with samba, they must be visible!

One must see the inconvenient nature of this default.

---

### Post by Tsingi on 2008-01-03
It might not be the most convenient setting, but it is the most secure setting.

Creating a Linux desktop for the average man is an admirable goal.  Making it work like the virus trap windows is, by default, is a bad idea.

Consider a beginning ubuntu user with all the defaults open to sharing wandering into a hostile wireless environment, or even connecting to the internet if you make insecure all the other defaults as well.

No, the decision to share what's on your computer with others, and allowing others to alter what's on you computer should be a conscious deliberate one, not the default.

---

### Post by chrisccoulson on 2008-01-03
I thought user mode security was the way Windows behaved by default anyway? Certainly with boxes I've set up, users trying to access shares remotely need a login account on the machine hosting the shares, with which they authenticate with (unless the share is specifically set up to be accessible by everyone)

---

