---
title: "new vidalia problem"
date: 2011-12-15
forum: Security
---

### Post by ottosykora on 2011-12-15
So far I was using tor with the vidalia gui launcher. All was OK until the recent update of the vidalia part. 

On one notebook, I had problem in starting tor, but somehow it all resolved and I had to tick the use TCP for control port.
(ubuntu 11.04, 32bit)

On other computer with ubuntu 11.04 64bit, I can not get even the client to work, earlier also relay was no problem.

I tried all sorts of combinations, rebooted number of times, checked if tor stil runs (=negative) but still no luck.

When trying to start I get log:

```
Dez 15 18:41:25.001 [Hinweis] Tor v0.2.2.34 (git-c55c166e73d500af). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Dez 15 18:41:25.014 [Hinweis] Initialized libevent version 1.4.13-stable using method epoll. Good.
Dez 15 18:41:25.014 [Hinweis] Opening OR listener on 0.0.0.0:9001
Dez 15 18:41:25.014 [Hinweis] Opening Directory listener on 0.0.0.0:9030
Dez 15 18:41:25.014 [Hinweis] Opening Socks listener on 127.0.0.1:9050
Dez 15 18:41:25.014 [Warnung] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Dez 15 18:41:25.014 [Hinweis] Opening Control listener on 127.0.0.1:9051
Dez 15 18:41:25.014 [Hinweis] Closing partially-constructed listener OR listener on 0.0.0.0:9001
Dez 15 18:41:25.014 [Hinweis] Closing partially-constructed listener Directory listener on 0.0.0.0:9030
Dez 15 18:41:25.014 [Hinweis] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Dez 15 18:41:25.014 [Warnung] Failed to parse/validate config: Failed to bind one of the listener ports.
Dez 15 18:41:25.014 [Fehler] Reading config failed--see warnings above.
```

---

### Post by Cpierce on 2011-12-18
I have the same issue. Everything worked fine until the recent update. Hope someone can help.

---

### Post by Cpierce on 2011-12-18
I just tried your changing the TCP setting and I got mine to work. Thank you, and hope you get yours fixed too.

---

### Post by Jackalux on 2012-03-21
I'm failing to get Vidalia and Tor working on my first ever Ubuntu install.  Sounds like the same error; same error messages.

I used Software Centre to install 'anonymizing overlay network for TCP' (I assume that's Tor, right?) then 'Vidalia'.

Subsequently, running Vidalia, I'm unable to start Tor as 'Vidalia detected that the Tor software exited unexpectedly. Please check message log...' which says 'Warning: Could not bind to 127.0.0.1:[etc]'; 'Warning: Failed to parse/validate config: Failed to bind blah blah blah' and 'Error: Reading config failed--see warnings above'

I've uninstalled both, rebooted and reinstalled.  Same error occurs.

Any chance of an answer for a noob?  Be gentle; I used Unix years ago and have done some programming in my time but Linux geekspeek has began to leave me lost. :confused:  Please don't assume that knowledge of Tor means I have any idea of using/installing packages, tarballs etc.  I last used command lines with DR-DOS when Windows 1 was on the scene.

Thanks (especially to those who take the time to question what just seems obvious to insiders and non-noobs!).
Jackalux

Oh, yeah... Ubuntu 11.10

---

### Post by leclerc65 on 2012-03-21
I think you have to do this

Install sysv-rc-conf:
sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf

scroll over the X's for **tor** and "unselect" them with the spacebar.
Reboot.

---

### Post by Jackalux on 2012-03-22
> **leclerc65 said:**
> I think you have to do this

Install sysv-rc-conf:
```
sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf
```

scroll over the X's for **tor** and "unselect" them with the spacebar.
Reboot.

Genius! Thanks @leclerc65  :D
Would you mind telling me what I just did?  Keen to learn.

For reference, I unchecked boxes 2, 3, 4 & 5

---

### Post by ottosykora on 2012-03-22
the problem is that the recent version of tor are set up so that tor does run on start up, that means when you start the computer the tor starts and runs.
When you start vidalia, then you try to start tor again and con not as it runs again.

The trick is to prevent tor starting on boot so kind of remove it from the list of the programs to be run on start up.

So from now you are able to start tor manually (with vidalia for example).

---

### Post by Jackalux on 2012-03-23
Thanks, ottosykora.

I understand now; that all fits the error messages I was getting.

---

