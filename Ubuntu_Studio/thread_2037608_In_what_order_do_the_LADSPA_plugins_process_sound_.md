---
title: "In what order do the LADSPA plugins process sound in jackrack?"
date: 2012-08-05
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2012-08-05
When I put more than one plugin into jackrack, is there a specific order in which they process the sound signal?  Is it top to bottom, for example?

---

### Post by sgx on 2012-08-05
Hi, there's a good tutorial for jackrack, you can change plugin order,
save and load racks etc  scroll down the page a bit:

[http://www.penguinproducer.com/2011/09/using-jack/](http://www.penguinproducer.com/2011/09/using-jack/)

Cheers

---

### Post by ubnewbie2 on 2012-08-05
Thanks.  That verified that the top ones should process first.   My testing didn't seem to indicate that, but that might have been just a weird plugin.  I'll try again.

---

### Post by sgx on 2012-08-06
Not as easy, but using ordinary qjackctl connections,
removes any arbitrary limits of a rack gui.

calf, invada, and mda are also good plugins collections.

Using Ardour/Qtractor and saving sessions with various plugin chains intact is another option, if multi-track recording is needed.

Cheers

---

### Post by ubnewbie2 on 2012-08-06
> **sgx said:**
> Not as easy, but using ordinary qjackctl connections,
removes any arbitrary limits of a rack gui.

calf, invada, and mda are also good plugins collections.

Using Ardour/Qtractor and saving sessions with various plugin chains intact is another option, if multi-track recording is needed.

Cheers

I am using qjackctl connections but jack-rack only makes two input/output connections (before and after the whole chain) available, nothing intermediate like lv2rack.  So unless there's an alternative to jack-rack (other than Ardour - although I have tried that and it works), or standalone jack apps for the plugins (but I am not aware of many)...

---

