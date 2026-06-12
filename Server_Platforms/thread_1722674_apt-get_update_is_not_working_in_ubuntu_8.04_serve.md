---
title: "apt-get update is not working in ubuntu 8.04 server"
date: 2011-04-06
forum: Server Platforms
---

### Post by Anandhkumar on 2011-04-06
Hi everyone,

I am a newbie to ubuntu. I installed ubuntu 8.04 server edition in my PC to deploy a web application. After the installation was complete i typed apt-get update in the terminal.

It's throwing error messages like

[FONT=Times New Roman][B]* Failed to fetch

* Unable to connect to in.archive.ubuntu.com

* Some index files failed to download, they have been ignored, or old ones used instead.

* You may want to run apt-get update to correct these problems[/B][/FONT]


But when i try it again i get the same issues.


Kindly let me know am i missing anything.


Thanks in advance

Anandh

---

### Post by BbUiDgZ on 2011-04-06
I'm not sure the repo's for 8.04 are still supported

you may want to use 10.04 which is the latest LTS

---

### Post by Anandhkumar on 2011-04-06
Thanks fr your reply.

Ubuntu 8.04 server edition has got support till April 2013.

[COLOR=RoyalBlue]_[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)_[/COLOR]

I dont see that as a problem.

---

### Post by Anandhkumar on 2011-04-06
Moreover i get the same problem with 10.04 server edition also. 

Can someone please let me know am i missing something..?


Thanks,
Anandh

---

### Post by BbUiDgZ on 2011-04-06
> **Anandhkumar said:**
> Moreover i get the same problem with 10.04 server edition also. 

Can someone please let me know am i missing something..?


Thanks,
Anandh
is the network cable plugged in?
If so do you have an IP? ```
ifconfig -a
```
Do you need a proxy server to access port 21 or 80?
Do you havea default gateway set?
Whats the output of
```

cat /etc/network/interfaces

```

---

