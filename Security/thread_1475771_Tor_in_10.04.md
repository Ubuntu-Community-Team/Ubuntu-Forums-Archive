---
title: "Tor in 10.04"
date: 2010-05-07
forum: Security
---

### Post by JugglinPhil on 2010-05-07
I tried to set up TOR following these instructions: [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)
No when I activate the TOR Button in Firefox I get an error message as you can see in the screenie. Can anybody help me out with this one?

---

### Post by unmole on 2010-05-07
Check if you have configured Polipo correctly. Go to System>Administration>Network Tools and go to Port Scan and enter 127.0.1.1 as host. Port 8118 must be open.

---

### Post by Soul-Sing on 2010-05-07
Some sites will/can refuse/block TOR.

---

### Post by JugglinPhil on 2010-05-08
> **unmole said:**
> Check if you have configured Polipo correctly. Go to System>Administration>Network Tools and go to Port Scan and enter 127.0.1.1 as host. Port 8118 must be open.
I did the scan and there was no output whatsoever, so I assume it is not configured correctly?

---

### Post by mkvnmtr on 2010-05-08
Try restarting Firefox. If that does not do  it restart the computer.

---

### Post by JugglinPhil on 2010-05-09
> **mkvnmtr said:**
> Try restarting Firefox. If that does not do  it restart the computer.
Thanks that actually did it, didn't think it could be **that** easy...
Should have thought of that myself..

---

### Post by gregnorc on 2010-05-09
> **JugglinPhil said:**
> Thanks that actually did it, didn't think it could be **that** easy...
Should have thought of that myself..

For anyone else reading this:

You needed to restart the polipco daemon... you had edited the config file, but the daemon was still working with the old version. It's in the instructions, but easy to miss (same thing happened to me). Restarting the computer also restarts the daemon, hence Tor working after a restart...

For future reference, the command is:
```
/etc/init.d/polipo restart
```

---

