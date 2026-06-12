---
title: "Ubuntu Kylin website!"
date: 2022-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by LwIh%*7 on 2022-08-07
Is it just me or is the Ubuntu Kylin website down? I couldn't access it for the last few months now even on my Tablet device. Is anyone else experiencing the same issue with accessing the website? Funny thing is also when OpenKylin got released I was able to access that website and try out the system on one of my computers but even now I can't access that website also now.

---

### Post by guiverc on 2022-08-08
I can say it's not just you.

Last Thursday (4th August) was the initial (expected) release date for Ubuntu 22.04.1 LTS, and there was discussion (#ubuntu-flavors) of problems reaching Ubuntu Kylin representative(s) & accessing the web site, with many (*who tried*) unable to reach it, with errors seeming to vary on location of the enquirer.

 One user noted it was last "*crawled*" by google on 1st August 2022 so was working then, but 22.04.1 had other issues (*thus the delay till 11th August*) and the issue with Kylin wasn't resolved to my knowledge (*though very possible I missed some details as Kylin wasn't a concern of mine*).
[I]
fyi: I note 403 errors for some trying to peruse Ubuntu Kylin's website in IRC readback, but discussion on the Kylin status I suspect (recall?) was in more than the one room I'm viewing the readback on.[/I]

---

### Post by LwIh%*7 on 2022-08-08
At least its not just me noticing it, I'm starting to wonder if it might be the ISP blocking access the website because of the OS being designed for "Chinese" users even though the OS is made by Canonical a British company. The way I can't access it is similar to what my ISP did with some websites that were blocked like rt.com so it gets me wondering if its because of the ISP. Shame we can't find that information out! I also find it strange that OpenKylin has had the same issues since the OS has been released and the repositories on the system are down as well and can't update the system on my test system.

---

### Post by TheFu on 2022-08-08
There are a number of "down for me" websites that will check if a website is down just for you or for everyone else.
[https://downforeveryoneorjustme.com/](https://downforeveryoneorjustme.com/) is one.  Google found it.
[https://down.com/](https://down.com/) is another.
[https://isitdownorjust.me/](https://isitdownorjust.me/) and another.
[https://isitdownorjustme.net/](https://isitdownorjustme.net/) and another.

Of course, if the goal was also to get someone related to that project to respond, perhaps they will see this thread, but I wouldn't hold my breath. 
[http://cdimage.ubuntu.com/ubuntukylin/releases/22.04/release/](http://cdimage.ubuntu.com/ubuntukylin/releases/22.04/release/) has the download, but since 22.04.1 was delayed due to issues with snaps, I'd check back in a week.

```
$ ping ubuntukylin.com
PING ubuntukylin.com (124.126.103.228) 56(84) bytes of data.
^C
--- ubuntukylin.com ping statistics ---
6 packets transmitted, 0 received, **100% packet loss**, time 5111ms

```

And yes, where the DNS pointer for the domain is not responding to pings, so it is down at a network layer. That IP resolves to an IP in Beijing. Take that however you like.

---

