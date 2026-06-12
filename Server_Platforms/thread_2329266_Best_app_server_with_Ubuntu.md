---
title: "Best app server with Ubuntu"
date: 2016-06-29
forum: Server Platforms
---

### Post by mike_l2 on 2016-06-29
I am a recent convert from Microsoft.  I have worked with Ubuntu/Codeblocks for the last couple of months in C++.
I  am building a web app that will provide services to native clients on  the entire range of client platforms, including iPhone and Android.  I  plan to use secure websockets (WSS) for connection and have begun  development in C++ on Ubuntu.
Can anyone advise the best app server(s) to look at?  Basic requirements are:
•    Support for WSS.  Bidirectional input/output, continuous connection.
•     Low overhead.  No HTML needed.  All communications are binary stream.   App functions can be called directly from input queue.
•    Most  message lengths will be short.  Very little graphics content from  server.  Occasional long message for file upload/download segment(s).
•    Work well in Ubuntu.
•    Scalable.
•    Robust – must handle connection & queue anomalies correctly.

---

### Post by howefield on 2016-06-29
Moved to "*Server Platforms*" forums. Not sure it si the right fit but better than General Help where it was posted.

---

