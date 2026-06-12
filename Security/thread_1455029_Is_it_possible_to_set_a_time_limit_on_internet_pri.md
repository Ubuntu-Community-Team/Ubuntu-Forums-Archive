---
title: "Is it possible to set a time limit on internet priveleges with Ubuntu 9.04?"
date: 2010-04-15
forum: Security
---

### Post by socref on 2010-04-15
Hi, everyone.

Posting in this section of the forums since I really did not know where else might be more appropriate.

I'm trying to help my daughter set up her computer using 9.04.

Is there a way to create a guest account and have Ubuntu "automagically"  limit the amount of time the user can access the Internet? So, for example, could she set up an account for her son and limit his Internet access to an hour at a time?

Thanks for your wisdom.
socref

---

### Post by bodhi.zazen on 2010-04-15
You can do this most easily, IMO, with iptables.

You can also do this with squid (a proxy server).

Hard to know if iptables or squid is harder to learn.

[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)

Just add a match to that

iptables -m owner --uid-owner son_name .... -j

---

### Post by 2hot6ft2 on 2010-04-15
I don't think it's quite what you're looking for but assuming it is now 18:00 and your Daughter wants on the computer, you can enter ```
sudo shutdown -h 19:00
``` The system will shut down in one hour!
:lolflag:

---

### Post by socref on 2010-04-15
> **2hot6ft2 said:**
> I don't think it's quite what you're looking for but assuming it is now 18:00 and your Daughter wants on the computer, you can enter ```
sudo shutdown -h 19:00
``` The system will shut down in one hour!
:lolflag:

She might like that. Simple.  :)

Thx.

Does her system have to be set to a 24 hour clock for this to work?
What if she's on the standard U.S. system of 12 hours a.m. and p.m.?
socref

---

### Post by socref on 2010-04-15
> **bodhi.zazen said:**
> You can do this most easily, IMO, with iptables.

You can also do this with squid (a proxy server).

Hard to know if iptables or squid is harder to learn.

[http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html](http://www.cyberciti.biz/tips/iptables-for-restricting-access-by-time-of-day.html)

Just add a match to that

iptables -m owner --uid-owner son_name .... -j

Thanks! Appreciate the reply.
socref

---

### Post by 2hot6ft2 on 2010-04-15
> **socref said:**
> She might like that. Simple.  :)

Thx.

Does her system have to be set to a 24 hour clock for this to work?
What if she's on the standard U.S. system of 12 hours a.m. and p.m.?
socref
Welcome.
Does her system have to be set to a 24 hour clock for this to work?
No

What if she's on the standard U.S. system of 12 hours a.m. and p.m.?
The system still sees it as a 24 hour clock no matter how the clock displays it. So use the 24 hour format for the command.
Enjoy

---

### Post by kostkon on 2010-04-15
A good solution that a simple user (e.g. a parent) could use is *Gnome Nanny* (it's similar to what windows offers for parent control).

An article about it [here]("http://www.webupd8.org/2010/03/gnome-nanny-parental-control-takes-care.html") and the PPA is [here]("https://launchpad.net/~nanny/+archive/ppa").

Hope that helps.

---

### Post by socref on 2010-04-15
> **2hot6ft2 said:**
> Welcome.
Does her system have to be set to a 24 hour clock for this to work?
No

What if she's on the standard U.S. system of 12 hours a.m. and p.m.?
The system still sees it as a 24 hour clock no matter how the clock displays it. So use the 24 hour format for the command.
Enjoy

Thanks. Really appreciate this response.
socref

---

### Post by socref on 2010-04-15
> **kostkon said:**
> A good solution that a simple user (e.g. a parent) could use is *Gnome Nanny* (it's similar to what windows offers for parent control).

An article about it [here]("http://www.webupd8.org/2010/03/gnome-nanny-parental-control-takes-care.html") and the PPA is [here]("https://launchpad.net/~nanny/+archive/ppa").

Hope that helps.

Yes, many thanks. I will pass this info to her. A great help.
socref

---

### Post by 2hot6ft2 on 2010-04-15
You're welcome. I kinda like kostkon's app. in case she wants more control like which websites and stuff they can access. You may want to let her know about both options. That way she can decide what kind of control it is she really wants.

LOL, I see you were on that while I was typing.

---

### Post by HermanAB on 2010-04-16
Howdy,

There is also the PAM-Time module, but messing with PAM is dangerous.  PAM is a very sensitive girl...

---

### Post by socref on 2010-04-16
> **HermanAB said:**
> Howdy,

There is also the PAM-Time module, but messing with PAM is dangerous.  PAM is a very sensitive girl...

Just learning Ubuntu, so need to stick with the simple stuff.  :)

Thx
socref

---

