---
title: "Using a hosted server as a private proxy of sorts?"
date: 2007-12-04
forum: The Cafe
---

### Post by PartisanEntity on 2007-12-04
I am not sure what the terminus technicus is but basically here in the office, only port 80 is open. So I am unable to check my emails on my hosted server because the webmail runs on a different port. (Asking the IT department is out of the question since we have strict IT policies.)

I was wondering if there was some kind of script or software package that could be uploaded to my hosted server so that I could check my emails from the other port on port 80?

I don't mean something like squirrel mail, but a kind of hosted browser or something like that?

Thanks.

---

### Post by PriceChild on 2007-12-04
What about tunneling?

Not sure what you mean by "hosted server", but if you could get ssh to that server on port 80 then you could forward any connection and port through that.

---

### Post by PartisanEntity on 2007-12-04
Sorry what I actually meant is that I have a hosted site.

---

