---
title: "Ubuntu's main server vs my country of origin's server? What's the difference?"
date: 2021-01-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2021-01-27
[IMG]https://i1.wp.com/itsfoss.com/wp-content/uploads/2013/04/Failed-to-download-repository-information-Ubuntu-13.04.png?fit=486%2C173&ssl=1[/IMG]

I had been having this issue since yesterday, so there's something wrong with the Ubuntu server from my country of origin, so I've switched to Ubuntu's main server today and was able to get updates.

[IMG]https://i.stack.imgur.com/YGtwc.png[/IMG]

Is there a difference to using Ubuntu's main server over the server from my country of origin?

Thanks.

---

### Post by simon-webb on 2021-01-28
Absolutely no difference in terms of the software installed: they're identical copies. The only advantage to local servers is that they're often a bit faster. It also helps spread the load on the main servers to have people use their local ones, so it's always a good thing to try...but it won't hurt your system at all to use the main servers. Your local one might have had temporary problems: you could always try again later.

---

### Post by guiverc on 2021-01-28
A copy of the mirrors, and the best site I know of to view the current status with regards *up-to-date* or behind is

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

At times different sites can show hours (or even days) behind, and the odd site can have *unknown* which means the counter has overflowed (*and thus problems are to be expected*).

The list is updated regularly, but if I have issues, it's where I go first.

The primary benefit for going with a local mirror is speed, the disadvantage can be they can on occasion be behind (*the main server*) as already stated by @simon-webb

---

### Post by basushaunak on 2021-01-31
Was wondering if there is a way by which Ubuntu's software updater can detect the fastest mirrors from say a list 20 mirrors and use the fastest one?

---

