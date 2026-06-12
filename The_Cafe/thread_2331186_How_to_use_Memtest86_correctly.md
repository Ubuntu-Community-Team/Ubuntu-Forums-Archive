---
title: "How to use Memtest86 correctly"
date: 2016-07-19
forum: The Cafe
---

### Post by tech291083 on 2016-07-19
Hi Friends,

I was interested in checking my RAM and thus I used two tools called Memtest86 and Memtest86+, which came on Ultimate Boot CD 5.3.5, but despite running them for 5/6 passes (spanning 2+ hrs), the tests did not seem to end, although no error were shown thus far, so I am wondering as to what should one do in terms to settings in order to make sure these tools run properly and show errors correctly? 

What is the ideal no of passes? What other parameters/settings/configurations must in place?

Thanks.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)


[http://www.memtest86.com/](http://www.memtest86.com/)

---

### Post by sudodus on 2016-07-19
Run the test overnight (let it repeat the tests over and over if the computer is fast enough). One error is too much.

Reboot and feel happy, if no error is found next morning :-)

Otherwise, identify the failing RAM stick (if more than one), and replace it :-(

---

### Post by frostschutz on 2016-07-19
If memtest manages a single full pass then you have good chances it won't be bad but there are no guarantees unfortunately. Memory errors can be annoying and sometimes not occur for days (or be only triggered within Linux itself, not by the memtest).

Memtest tries to emulate various ways of how memory might be accessed but it's a different story when actual programs use memory. See rowhammer for an extreme use case...

---

### Post by mastablasta on 2016-07-20
2 or 3 passes should be enough. if there is something really bad, then it Will show after the first or second pass.

---

### Post by tech291083 on 2016-07-20
> **mastablasta said:**
> 2 or 3 passes should be enough. 

OK. I get this, thanks.

---

### Post by tech291083 on 2016-07-20
> **frostschutz said:**
> 
If memtest manages a single full pass then you have good chances it won't be bad but there are no guarantees unfortunately. Memory errors can be annoying and sometimes not occur for days...


This is scary, but worth paying attention to, thanks.

---

