---
title: "GPG Automated Run"
date: 2008-10-23
forum: Security
---

### Post by ao7711 on 2008-10-23
Folks,

I am trying to run GPG encryption but following prompt keep on showing up. This stops me from running it in automated fashion.

Message:

It is NOT certain that the key belongs to the person named
in the user ID.  If you *really* know what you are doing,
you may answer the next question with yes.

Use this key anyway? (y/N) y

I tried to suppress it with following command but –batch command somehow it doesn’t work as expected.

 C:\gnu\ gpg --batch


Any thoughts?

Many Thanks

---

### Post by kevdog on 2008-10-23
You need to sign the key.  Only due this if you are sure the key came from someone you absolutely know.

---

### Post by Dr Small on 2008-10-23
> **kevdog said:**
> You need to sign the key.  Only due this if you are sure the key came from someone you absolutely know.
I thought this was only a problem with level of trust? Generally, I opened GPA and set the level of trust on the key, and never get this type of error. Level of trust isn't the same as signing it, is it?

---

### Post by kevdog on 2008-10-23
> **Dr Small said:**
> I thought this was only a problem with level of trust? Generally, I opened GPA and set the level of trust on the key, and never get this type of error. Level of trust isn't the same as signing it, is it?

I'll have to look in on this -- I don't want to spread FUD.  Thanks for calling me on this.

---

