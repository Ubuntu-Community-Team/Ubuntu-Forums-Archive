---
title: "Windows client update group policy with samba pdc?"
date: 2008-04-02
forum: Server Platforms
---

### Post by cpthk on 2008-04-02
I have 100 windows client loggin in samba domain controller. Every time I am trying to change a setting in windows group policy. Is it so painful to change on every windows. Is there anyway that windows can update the most recent setting of group policy itself?

Thanks.

---

### Post by netlogic on 2008-04-02
Yes, it can.  It will not be an instant gratification like Windows.
It is described in the chapter six from the official Samba guide.
[www.samba.org](www.samba.org)

---

### Post by cpthk on 2008-04-05
> **netlogic said:**
> Yes, it can.  It will not be an instant gratification like Windows.
It is described in the chapter six from the official Samba guide.
[www.samba.org](www.samba.org)

But from my test only very limited options will work, others like "Prevent roaming profile changes from propagating to server" will not work. Even though I edit *.adm myself.

About the guide you are saying, is it this one? I don't see anything related to this in chapter 6. Can you point out which page, which paragraph?

Thanks you so much.

---

