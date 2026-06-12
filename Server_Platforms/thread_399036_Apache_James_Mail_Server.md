---
title: "Apache James Mail Server"
date: 2007-04-01
forum: Server Platforms
---

### Post by smeel on 2007-04-01
I would like to set up a mail server on my Ubuntu installation. I have heard about various implementation, but particalry intrested in the apache James mail server.

Can the James mail server be installed on Ubuntu? If so how is this done? Can it be done via apt-get?

Many thanks

Jason

---

### Post by kidders on 2007-04-01
Hi there,

Something just happened to me that made the internet feel very small, all of a sudden. I googled for suggestions on your problem & came across [http://ubuntuforums.org/showthread.php?p=2375784](http://ubuntuforums.org/showthread.php?p=2375784), which wasn't terribly inspiring.

It's not an officially supported application, but since it would be running in a VM, there's only so much damage you could do to your system by running it! Judging from the documentation, the thing pretty much seems to install itself though ... is there a specific issue that's causing you trouble?

One thing worth mentioning is the fact that the 'J' in the name presumably means the server will be slow, unwieldy, and wildly inefficient. I can't help wondering if there's a particular reason you want to run a mail server written in Java of all things! Aside from being faster and more robust, using something more standard would give you access to a far wider support base, should you run into difficulty.

However, to answer your questions more directly:

> Can the James mail server be installed on Ubuntu?Yes.
> If so how is this done?[http://james.apache.org/server/2.3.0/installation_instructions.html](http://james.apache.org/server/2.3.0/installation_instructions.html)
> Can it be done via apt-get?Not readily, it seems.

---

### Post by ethan@xmlstandards.org on 2007-04-01
Burning the midnight oil here in London,

Just performed a test installation on Windows XP to see how it would fare and will shortly do another on a test box (Ubuntu Dapper Server), will post back results once completed.

PS. Why do you want to use James?

Only curious.

---

