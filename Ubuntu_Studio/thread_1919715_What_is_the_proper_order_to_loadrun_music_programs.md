---
title: "What is the proper order to load/run music programs in?"
date: 2012-02-03
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-02-03
I want to use:

JACK - (do I?  or would I do as well without it?)

Patchage - ( seems to need JACK running first, 
 ..............I really like the newer display with curved lines in Ubu 11.10. Can I port this version to Ubu 10?)

Ardour - (Just started to get a grip on this, and want to learn it for sound-on-sound, track recording)

Hydrogen - (awesome drum machine, but is there a way to get more than 32 drum sounds at a time?)

Meterbridge - (looks cool and I'm used to this kind of studio meter)

Guitarix - (obviously for the effects)

Rackarrack - (again, effects: is there a 24/96 studio reverb out there in software?)

This was the order I was loading them intuitively. 
But now I see in some threads this might actually be wrong, or a backwards order, and cause problems.

What is the real proper order to run these things in, if I want to use them together, interconnect them, and record the result in Ardour?

Also, what purpose or use is LMMX studio?   Does it also have to be installed and running?

Do I need to run alsamixer (or Gnome alsamixer) before starting?

Totally confused here, partly by the fact nothing seems to be working yet...

---

### Post by jejeman on 2012-02-03
If you use applications that use jack, then you need to run jack first.
For the rest order is not important, exept if you want to recreate the session. Then Ardour should be the last one to start, because it remembers conncetions to/out it.
> Also, what purpose or use is LMMX studio? Does it also have to be installed and running?You meant LMMS? Thats a aplication like FL Studio, you don't need it, if you don't use it.
> Do I need to run alsamixer (or Gnome alsamixer) before starting?No, you can start them at any time.

---

### Post by nazaroo2 on 2012-02-03
Thank you for your explanation about the order.

So I guess I did have it almost right, that I should run JACK first.

However, right now, JACK won't start, (see my other thread),
so I can't move to the next step, which is get the Xonar DG to provide recording input to the computer...
Perhaps if the order of loading/running is not an issue, 
then you might have an idea what my current holdup is...
thanks

---

### Post by nazaroo2 on 2012-02-03
I now have another question:

When I try to stop JACK, I get a warning: 
[COLOR=Navy][B]"Some client audio applications are still active and connected.
Do you want to stop the JACK audio server? Y / N "[/B][/COLOR]

This seems to suggest it is wrong or stupid to shut off the JACK,
before shutting down all the other programs. 

**So is there a proper order to shut down all the programs too?**

---

### Post by jejeman on 2012-02-04
You can ignore jack warning, nothing bad will happen. But you should save your projects first.

---

### Post by nazaroo2 on 2012-02-04
> **jejeman said:**
> You can ignore jack warning, nothing bad will happen. But you should save your projects first.

Thanks for this info.  This is very helpful.
There's a lot to learn regarding this idea of using a computer to record.

---

### Post by sgx on 2012-02-04
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

use the 4th and 8th links at the list
on this wiki page, to setup jackd, and qjackctl.

in general, the connections in qjackctl will be the
same as one would use in real hardware, only more versatile.

---

