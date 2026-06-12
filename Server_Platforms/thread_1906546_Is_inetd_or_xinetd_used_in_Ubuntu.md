---
title: "Is inetd or xinetd used in Ubuntu?"
date: 2012-01-09
forum: Server Platforms
---

### Post by Rob_H on 2012-01-09
I have a small program that should be started whenever a connection is made to a particular TCP port from localhost. And I want its standard I/O streams to be bound to that network connection.

This sounds like a perfect fit for xinetd. But I was surprised to see that it is not installed by default on my Ubuntu box. Does Ubuntu use a different "super-server"? What's the convention for this kind of service process? Thanks.

---

### Post by Lars Noodén on 2012-01-09
Neither are installed by default, even on the Ubuntu Server Edition.  So you are free to choose xinetd and it won't conflict with anything.

---

### Post by Henry Cooper Avel on 2012-12-05
Yes, but WHY it is not installed by default?

---

### Post by SeijiSensei on 2012-12-05
This is an old thread so it may be locked, but to answer your question, most services these days simply run as daemons.  Partly that is for performance reasons on machines handling lots of traffic, but it also reflects a greater devotion to security among developers of server software.  

No one would consider wrapping Apache in xinetd, for instance, because of the extra overhead involved, and because most any security controls you might implement via xinetd are available within Apache itself.

---

