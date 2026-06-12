---
title: "Buildserver on 14.4 and final host on 16.4"
date: 2017-04-20
forum: Ubuntu Application Development
---

### Post by weltenbummler on 2017-04-20
Hey there,
I'm trying to build a C++ program on a Ubuntu 14.4 and running the binary on 16.4.
The libs are linked dynamical.
On both machines I build my third party libraries on this OS.
Running the 14.4 compiled binary under 16.4 results in the first line of the program ( main function ) to:
```
undefined symbol: _ZN4Poco3Net11HTTPMessage8HTTP_1_1E
```

I've kind of an idea whats happening, but I'm not sure about it, I only know this not a good Idea at all. 
```
ldd -d -r 
``` shows more undefined symbols on the 16.4 machine with the 14.4 binary. All those Symbols are part of the third library.

Soooo, there are a couple of questions:
What is happening?
Why is it not working? ( the third party libs are compiled on both machines )
Is there a way how to cross compile it on a 14.4 for a 16.4?
Would a static linking solve the problem?
Or maybe is there a topic or a phrase which I can put into google to get some how smarter and solve this problem my self or get good book to look into?

Every help or hint is highly appreciated!
thx

---

