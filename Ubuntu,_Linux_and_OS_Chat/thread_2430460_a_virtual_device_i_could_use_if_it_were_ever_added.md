---
title: "a virtual device i could use if it were ever added to the kernel"
date: 2019-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-11-02
a virtual device i could use if it were ever added to the kernel would have 2 variations, one as a character device, and one as a block device.  i would these /dev/block-b and /deb/block-c.  opening, as permitted, would always succeed.  non-blocking mode is, also, always permitted.  multiple opens are always allowed.  any process that does a read or write will always block.

one use case i have is to use the character version as a terminal.  it would pause an input much like a tty when the keyboard is not used.

---

### Post by jetsam on 2019-11-16
That's one of those "so simple I'm surprised it's not done that way already" ideas.  Very unix-think.  Much --wow.  (sorry) 

I wonder if it would have security implications.  It's such an abstract and general idea it's hard to guess what its use cases and limitations would be.  It would obviously be useful to learn driver development with, as a dummy driver for early code if nothing else.  It actually sounds like it would make a good chapter one in a "how to develop drivers for Linux" book.

---

