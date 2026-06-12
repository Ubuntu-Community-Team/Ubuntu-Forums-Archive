---
title: "Authentication token manipulation error when using numericals in password"
date: 2010-04-25
forum: Security
---

### Post by atakacs on 2010-04-25
Folks

I'm having a rather strange problem

Using the passwd command I get an "Authentication token manipulation error” when changing  passwords if the new password contains a numerical value (i.e. digit 0..9). No error otherwise...

So "password" would work
password99 will result in "Authentication token manipulation error".

I tried to google this without success (so far ?).

This is "stock" Ubuntu 9.04 server

any suggestion / idea welcome

alexT

---

### Post by cdenley on 2010-04-26
Num lock? There shouldn't be any problem with numbers in passwords. I had numbers in my password when I used 9.04. You're probably entering the original password wrong or something.

---

### Post by atakacs on 2010-04-26
I agree it should work... yet 100% reproductible... FWIW it's a VMWare virtual machine if anyone cares to have a look...

---

### Post by cdenley on 2010-04-26
> **atakacs said:**
> I agree it should work... yet 100% reproductible... FWIW it's a VMWare virtual machine if anyone cares to have a look...

I'll have a look at a vmware image.

---

### Post by cdenley on 2010-04-26
I installed jaunty on a virtual machine, and failed to reproduce your problem.

-set password to "password99" with "passwd"
-set password to "secret99" with "passwd"
-set password to "passwd99" with "sudo passwd"

No matter what, it works as expected. I still believe you are doing something wrong, like entering the current password incorrectly.

---

### Post by Grim76 on 2010-04-27
Make sure to use the numbers that are above the letter keys.  I have seen some weird responses to numbers being entered from the number pad at times.  Just an idea, but something that I have seen in the past.

---

### Post by cdenley on 2010-04-28
> **Grim76 said:**
> Make sure to use the numbers that are above the letter keys.  I have seen some weird responses to numbers being entered from the number pad at times.  Just an idea, but something that I have seen in the past.

If you don't have num lock on, which was why it was the first thing I mentioned. I think in jaunty, ubuntu would turn off my num lock, but the LED on my keyboard would remain on.

---

