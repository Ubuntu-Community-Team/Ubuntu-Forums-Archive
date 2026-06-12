---
title: "Tor - RunAsDaemon"
date: 2011-02-12
forum: Security
---

### Post by with23nails on 2011-02-12
From [Tor alpha Manual]("https://www.torproject.org/docs/tor-manual-dev.html.en"):

>  RunAsDaemon 0|1
If 1, Tor forks and daemonizes to the background. This option has no effect on Windows; instead you should use the --service command-line option. (Default: 0)
But what that exactly means? What is the difference between Tor being and not being a daemon? According to [Wikipedia]("https://secure.wikimedia.org/wikipedia/en/wiki/Daemon_%28computer_software%29") (I know, but give me a chance!) daemon:
 > is a computer program that runs in the background, rather than under the direct control of a user; they are usually initiated as background processes.But even with that option in my [FONT=Courier New]torrc[/FONT] left at 0 Tor seems to be running in the background, no? I mean it don't really requires any attention from me - it's starting during boot and is running just fine without me poking around with it. And I'm not using Vidalia so what is the story with Tor as a daemon?

---

### Post by with23nails on 2011-02-13
I'm embarrassed now as I figured it out and it is quite simple... Tor is started by [FONT=Courier New]init[/FONT] script which is making sure it runs as daemon but not through [FONT=Courier New]torrc[/FONT] file instead think about it as similar to starting Tor with [FONT=Courier New]--RunAsDaemon 1[/FONT] argument.

---

