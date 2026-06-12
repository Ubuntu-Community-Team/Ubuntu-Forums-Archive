---
title: "pin on chipcard device not accepted"
date: 2011-07-10
forum: Security
---

### Post by averlon on 2011-07-10
Hi,
the headline looks like I do not know my pin anymore. Be ensured - I know it.

Already since a number of years I use a digital signatur with a qualified certificate issued from a german authority (D-Trust) according and supporting german law.
Up to some time ago, I did this on Windows.
Now I changed to Ubuntu still with a windows running on virtualbox for some applications not available on linux.

I had a 32bit installation of ubuntu and everything went well.
Now I changed to a new HW and installed ubuntu 11.04 64bit.
The windows is still a 32bit installation.

I wasn't able to find a software on linux to digitally sign e.g. .pdf-documents with that "Qualified Signature" so I stay doing this in windows environment.

But since ubuntu 64bit this does not work anymore.

Naturally, the HW, the "Reiner-SCT cyberJack Komfort" is connected to ubuntu including the latest drivers.
The HW works, since I can do e.g. HBCI online banking with a chipcard (also still running on windows) without problems.

When signing a document I am prompted for a PIN.
The used software, "Digiseal Office" offers two possibilities: a) pin via chipcard reader or b) pin via pc keyboard.

Regardless what I select, the pin is stated as wrong - and believe me - it is the correct one.

When I select the alternative b), there is a input field to enter the pin via the keyboard.
This input field gets grayed out once I hit more then 6 digits.

That lets me conclude that the underlying middleware, ubuntu pcscd, probably does not accept more then 6 digits in a pin prompt.

As I said before: with 32bit it worked.
It must have a link to the 64bit implementation - I guess.

Does onyone have similar experiences somewhere?

---

