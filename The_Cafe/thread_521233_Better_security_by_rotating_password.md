---
title: "Better security by rotating password?"
date: 2007-08-09
forum: The Cafe
---

### Post by DeusEx on 2007-08-09
Just brainstorming here: say there's a passwordsystem in which the user has password that rotates every day. I am thinking of a password that depends on the date, meaning the user has a static basic password which is easy to remember, and that there's a part the user calculates using, say,  the date.

The advantage is that there now is a timelimit in which the password has to be cracked. As long as the password (or encryption) is strong enough, the password can't be cracked in time.

How usefull would this be?

---

### Post by nocturn on 2007-08-09
I think that systems based on one-time password fit the bill better, but Kerberos protects to a large extent against this too (not by time-limitting the password, but by protecting it and authenticating with tickets that expire).

---

### Post by lisati on 2007-08-09
A few years ago the company I worked for at the time set up their security system in such a way that every few months you had to change  your password. What you chose was up to you, but the system retained sufficient information to make sure that if you did decide to rotate your password, the cycle wasn't too short.

---

### Post by popch on 2007-08-09
> **DeusEx said:**
> ... the user has a static basic password which is easy to remember, and that there's a part the user calculates using, say,  the date.

How usefull would this be?

If the easily remembered part is longish and the calculated part is short, then the password is not much more secure than the easily remembered part. Let's say your password started with macHines and ended with the day part of the current date + 3. Today's password would then be macHines12 which is not all that secure.

In addition, you might be unable to login at or near midnight.

OTOH, if the calculated part was longer or more difficult to calculate (and/or would yield not only digits but upper and lower case letters and other stuff), you would risk miscalculating your password du jour and thus blocking your account. 

Also, depending on your algorithm, you might think that the calculated password is more difficult to crack than it really is.

---

