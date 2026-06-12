---
title: "Exporting project lmms and Zynaddsubfx"
date: 2010-11-09
forum: Ubuntu Studio
---

### Post by GendeDios on 2010-11-09
//
Hi. Why when I export my project in lmms to .wav using the ZynA... it synthe return to its standard configuration and also the .wav lost all my configuration done into lmms. What do I should do to lmms export all my configuration done into ZynA...
Thanks for your help.

Edit: I realize that this happen with "wind" -> bank, and I don't know perhaps something else, but just I need Wind.
//

---

### Post by GendeDios on 2010-11-10
//
Well, somebody with something idea?
//

---

### Post by sgx on 2010-11-12
Are you trying to record the output of lmms?
If you choose jackd for lmms audio server,
try the timemachine recorder, use qjackctl to connect
the output of lmms to the input of time machine.

To record with a .wav start timemachine with

timemachine -f wav

Press record on timemachine, then press play on the lmms.

timemachine --help  to show a few options.
Cheers

---

### Post by GendeDios on 2010-11-12
Yes, I don't see other way. Perhaps be one bad configuration with the wind bank. Thanks friend.

---

