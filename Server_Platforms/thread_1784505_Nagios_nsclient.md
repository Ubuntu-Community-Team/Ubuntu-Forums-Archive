---
title: "Nagios nsclient"
date: 2011-06-17
forum: Server Platforms
---

### Post by tapi0n on 2011-06-17
I'm not sure if this is the appropriate forum to post this but I've got a question about nagios. The nsclient to be more specific.

I noticed that some servers where we run the nsclient the cpu usage goes up to 100%, making it impossible to work on. Now this doesn't happen on every server and it doesn't seem to be hardware related either (some old servers do it, but newer ones too).

Could this be because of the use of external scripts (got em from nagios exchange so I'm surprised that noone mentioned this in replies should this be the case)? I seriously have no idea where to start looking to be honost.

---

### Post by linkageless on 2011-06-21
In the past I've been aware of various problems with nsclient on windows. As far as I'm aware nsclient++ is the one to use though, I seem to remember one or two alternatives but for nrpe use on windows this was the best one.

IIRC - you can get logging from nsclient++ and you'll have the usual windows tools for problem diagnosis (whatever those are). My only other suggestion is to disable successive plugins until the problem goes away, then re-introduce the last plugin to see if it comes back. Then take that plugin on it's own and see if the high cpu returns.

I imagine that nsclient++ would (similar to other nagios components) have a configurable timeout (say 10 seconds) for running plugins. If that isn't kicking in, then either it's a problem with nsclient itself, or the plugin is spawning something that isn't being killed off.

---

