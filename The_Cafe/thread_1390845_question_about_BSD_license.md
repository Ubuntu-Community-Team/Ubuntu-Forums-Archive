---
title: "question about BSD license"
date: 2010-01-26
forum: The Cafe
---

### Post by q.dinar on 2010-01-26
it is said in BSD license that user can redistribute it but should keep this license.
in articles in web it is said that BSD-licensed things can became proprietary.
so how it is possible that it became proprietary if company that wants to make it proprietary should use same license for it saying "you can redistribute this and you should keep this license" ?

[http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses) :

```
 Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
```

what i understand from saying "proprietary" - when user is not allowed to sell it to other people not having permission from owner company, not allowed to disassemble program, modify and use without permission of owner company.
but from what i read in BSD license it looks like these must be allowed for all users, so how it can became proprietary.

probably i understand something wrong.

---

### Post by gnomeuser on 2010-01-26
The BSD license specifically allows someone to take the code, bundle it up as a binary and never show anyone the code nor any changes they might have made to it. All that is required is that the copyright notice is somehow displayed.

For a long time (untill at least Windows 98SE) Windows shipped the TCP/IP stack from FreeBSD with changes and acknowledged this by printing the copyright notice.

---

### Post by DoctorMO on 2010-01-26
All you have to do is abide be the license terms and the terms in the BSD license don't say anything about derivative works.

Say I make hamburgers without a bun, I give them away with a BSD license.

Some guy by the name of McDonald comes along and takes my hamburgers and slaps them onto buns and sells them for profit.

What's happening is that while users technically have the right to have the hamburger for free, they have no rights on the bun or anything else that it was shipped with. So in effect the hamburger becomes subject to the more restrictive terms of the bun.

---

### Post by ssam on 2010-01-26
its just the copyright lines that need to be retained, not the licence.

its like the Attribution clause in CC

---

### Post by q.dinar on 2010-01-26
thank you.

i understand now.

the string
"Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met"
is not itself condition that must be used with any redistribution, it is only a condition in the BSD license with wich it can be distributed before it becomes proprietary.

---

### Post by blueshiftoverwatch on 2010-01-26
I've always kind of wondered what exactly the point of the BSD licence is. It's basically just public domain except you have to give the original author credit. Why not just cut out the attribution clause and release the code as public domain instead?

Besides, from what I've read someone can take an open source licence, break the terms of usage, and get away with it most of the time. So if you wrote an application and put it under the BSD licence and someone used the code but didn't give you credit. Would you actually even bother to track down that person and sue him over it?

---

### Post by DoctorMO on 2010-01-26
FLOSS license compliance is an important legal work that should be continued. See the problem is that traditional companies are not enlightened enough to realise that holding all the rights to software is detrimental to development, holding some of the rights and collaborating is far superior.

It gets more stupid when the companies attempt to break say the GPL, they are both economically and legally shooting themselves in the foot.

---

