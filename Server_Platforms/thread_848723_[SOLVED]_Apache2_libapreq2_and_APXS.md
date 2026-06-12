---
title: "[SOLVED] Apache2 libapreq2 and APXS"
date: 2008-07-03
forum: Server Platforms
---

### Post by paulpc on 2008-07-03
I installed the package 'libapreq2', but whenever I dereference the 'Apache2::Request' module in a mod_perl script, it crashes with

'/usr/sbin/apache2: symbol lookup error: /usr/lib/perl5/auto/APR/Request/Apache2/Apache2.so: undefined symbol: apreq_handle_apache2'.

This is because the symbols in library /usr/lib/libapreq2.so.0.3 have been stripped-out as nm revealed: 

'nm: /usr/lib/libapreq2.so.3: no symbols'

So, I'm now trying to build the library from source code, but I need a copy of 'apxs' in order to do this. 

Can anyone supply me with a copy of the apache2 extension tool 'apxs' ? It would be greatly appreciated.

Thanks,

---

### Post by paulpc on 2008-07-07
I've found the problem. Please refer to my other thread 'Apache2 undefined symbol' for the solution.

Ta,

---

