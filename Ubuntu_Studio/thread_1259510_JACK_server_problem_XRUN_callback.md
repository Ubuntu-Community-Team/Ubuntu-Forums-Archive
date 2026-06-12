---
title: "JACK server problem XRUN callback"
date: 2009-09-06
forum: Ubuntu Studio
---

### Post by vkranendonk on 2009-09-06
hi, I've been having problems with setting up my jack server. I can first of all only start it true the terminal by using 'jackd -d alsa -d hw:0', otherwise it gets the error 256:

```
  p, li { white-space: pre-wrap; }  [COLOR=#990099]18:35:16.227 killall jackd[/COLOR]
 jackd: no process killed
 [COLOR=#999999]18:35:16.635 Post-shutdown script terminated with exit status=256.[/COLOR]

```When I start it up in the terminal and look at the message box it gives the following output, and keeps doing that every second:

```

18:30:47.911 XRUN callback (30 skipped).
18:30:49.914 XRUN callback (30 skipped).
18:30:51.917 XRUN callback (31 skipped).

```I have Ubuntu 9.04. I have Ubuntu 9.04. How can I fix this? or is the XRUN callback not a problem?

---

