---
title: "Compiz Enabled Bounced back 2 login"
date: 2011-08-03
forum: Ubuntu Studio
---

### Post by sandman3838 on 2011-08-03
Hello



I'm sorry to say!

I'm sad to report!

But my COMPIZ is hosed?
  :confused:


Doing the usual upate manager changed something.  Now when I open Ubuntu 10.10 64bit right when my desktop opens up I get bounced right back to sign in.  Next I went into UB in safe mode and stated switching off one item at a time in the Startup Applications and the culprit turned out to be COMPIZ.  To fix this I ran:



1. Remove compiz repository

2. apt-get purge compiz compiz-core

3. apt-get install compiz compiz-core



Didn't help?



Perhaps it's something with my video driver.

At the moment it stands at:

Linux-x86_64   280.13



Do any of you have any suggestions, or if you need the read out of something for some more info, please just ask.



Thank you for your time and help.



Sincerely,

---

### Post by sandman3838 on 2011-09-04
After posting this I went and inatlled Ubuntu 10.10 to another HD saving my original to grab files from.  I have noticed that since doing a clean install to 10.10 and not using 10.04 updating to 10.10 things have been running just fine.  Thanks you.

---

