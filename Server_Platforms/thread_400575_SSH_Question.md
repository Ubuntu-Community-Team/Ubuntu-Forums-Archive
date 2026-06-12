---
title: "SSH Question"
date: 2007-04-03
forum: Server Platforms
---

### Post by haloswin2002 on 2007-04-03
Is there any way to limit the times that a certain user can log in?  As it is now, I can be currently logged into my machine as many times as I want.  Is there a way to limit it, server side, so that the user 'me' can only be logged in once?

---

### Post by kidders on 2007-04-03
Hi there and welcome,

The configuration file you want is at **/etc/security/limits.conf**. It would be a system-wide limit though, so I wouldn't recommend setting it to 1 ... it would be completely crippling.

---

### Post by haloswin2002 on 2007-04-04
> **kidders said:**
> Hi there and welcome,

The configuration file you want is at **/etc/security/limits.conf**. It would be a system-wide limit though, so I wouldn't recommend setting it to 1 ... it would be completely crippling.

I havent tested it yet, but this looks like exactly what I want.  You are the man.  Where exactly do you go about finding this stuff, I couldnt find anything on google.

---

### Post by kidders on 2007-04-04
Hehe. :-)

This particular /etc file is very rarely used these days ... I'm really only aware of it because I've been using Linux for quite a while. (Sorry I can't point you to a nice FAQ, or something else useful. :-( )

Its intended purpose is to prevent users eating up too much of a system's resources. (Picture yourself in a US university, some time in the 70s, sharing a Unix box with 5,000 other ... well ... nerds!) These days, such things are less of a concern ... yours is the first post I've seen anywhere that asks this question!

A word of warning though... Don't play around with limits.conf too much, and always make sure you have at least one user (even if it's root) that isn't subject to any restrictions you set.

---

