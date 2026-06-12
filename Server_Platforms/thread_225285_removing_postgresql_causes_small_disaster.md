---
title: "removing postgresql causes small disaster"
date: 2006-07-29
forum: Server Platforms
---

### Post by pelgrim on 2006-07-29
configuring postgresql to your needs is just a nightmare in ubuntu
if you're install it with synaptics.

ok, got the brilliant idea to remove it with synaptics
and install it manually, I have experience installing it manualy
in mandrake, so this should at least put me back in control over
my databasetool.

But ...
Synaptics has errors removing postgresql,
leaving it "broken", meaning postgresql is still there,
but it's not possible to run the database anymore.
To make matters worse,
if I try to remove postgresql now with synaptics,
it gives an error with the message
do run dpkg --configure -a,
synaptics fails to start without running first this command.

What the heck !!!

All I did was a day long trying to get postgresql to run descently
changing the .conf files, and now I have this as a result ? :-& 

Please help me out,
I lost almost a week now changing from a mandrake server to a ubuntu server,
I go insane ...

---

