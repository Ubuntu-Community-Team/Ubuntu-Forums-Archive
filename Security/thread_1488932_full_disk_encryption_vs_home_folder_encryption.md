---
title: "full disk encryption vs home folder encryption"
date: 2010-05-20
forum: Security
---

### Post by hellz99 on 2010-05-20
I'm getting a new laptop in a week or so and wondering which way to go as far as encryption.  The two options seem to be full disk via the alternate and/or home disk.

I'm looking to secure my personal data without interfering with performance as much as I can.  I'm leaning toward the home folder encryption, but I was wondering if I'd be missing a major benefit by not going with full disk.

Any opinions on this? 
What are most laptop users going with?

---

### Post by wieman01 on 2010-05-20
If you want to protect your personal data only, then do /home only for performance reasons. If you are a paranoid, also encrypt root so nobody can install spyware on your PC while you are not at home. :-)

I recommend /home only.

---

### Post by OpSecShellshock on 2010-05-20
It's not really a matter of which is better, but of which more suits your specific needs. For example, how likely is it that someone else could get physical access to it? If it never leaves the house then /home should be fine (though that's not really what laptops are all about I suppose). If it does leave the house, but you don't expect it to leave your sight/possession at any time, then /home should also be OK.

Also, it depends greatly on the nature of the personal data itself. Does the data need to be stored locally on the system in order for you to carry out whatever function you plan to with it? If not, there's always the option of keeping it on external media and leaving that at home when you've got the laptop out with you (and encrypted on the external drive, if you like).

Either way, the thing to do is first accurately identify the likely risks that are specific to your situation, *and then* act accordingly. Unless of course you're also genuinely interested in experimenting with various information security approaches, which I always like to encourage. :)

---

### Post by HermanAB on 2010-05-21
As mentioned above, the more you encrypt, the more difficult it will be for an attacker with full access to your computer, to subvert it.

However, someone with full access to your computer will always be able to subvert it one way or another.

So even for government use with secret classification, we just encrypt /home and /swap and ensure that /tmp is using tmpfs (a RAM disk).

---

