---
title: "installed forked-daad but no media in itunes 12.1.2.27"
date: 2015-04-13
forum: Server Platforms
---

### Post by yann7 on 2015-04-13
Hi all,
i've just installed and configured forked-daapd on an ubuntu server 14.10.
All seems to run fine : My music is scanned, and i can see forked-daad server in itunes 12 (mac OS X 10.10.3) as a shared device/library

But when in itunes i select the forked-daapd server, i see itunes spinning off and then it tells me "no item". I have no errors in forked-daapd logs on the server and i see (debug log) a lot of itunes requests.

Is there a compatibility problem with forked-daapd (V21) with itunes 12.1.2.27 ? Or i'm wrong in my config ?

Thanks in advance

---

### Post by ejurgensen on 2015-04-14
That version of forked-daapd does not work with iTunes 12.1 and above:
[https://github.com/ejurgensen/forked-daapd/issues/100](https://github.com/ejurgensen/forked-daapd/issues/100)

So you will need to upgrade to a newer version (22.3+) - which probably means you will need to build it yourself :(

---

### Post by yann7 on 2015-04-14
Thank you very much ! Found this morning the github source for forked-daad. Just compile it and works great with ITunes 12.1.2.27.

---

