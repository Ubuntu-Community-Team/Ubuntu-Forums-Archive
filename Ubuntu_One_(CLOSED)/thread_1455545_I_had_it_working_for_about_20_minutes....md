---
title: "I had it working for about 20 minutes..."
date: 2010-04-16
forum: Ubuntu One (CLOSED)
---

### Post by Jive Turkey on 2010-04-16
..since I installed Lucid beta 1 two weeks ago.  After deleting the password in Accessories > Passwords etc. I was able to connect and add my computer.  It started crashing agian though.  I can't even start the preferences window.  Running "ubuntuone-preferences" in a terminal does nothing.  I get crash messages after rebooting for couchdb and/or ubuntuone, and I think my apparmor rules are keeping me from using launchpad correctly to report it.

Any suggestions?

---

### Post by Jive Turkey on 2010-04-16
I thought this might be useful information too (screenshot):

---

### Post by duanedesign on 2010-04-16
When launching 'ubuntuone-preferences' from the Terminal does anything get printed to the Terminal?

Probably be best if you could try again to file a bug.

You can use the following command to file a bug using apport.

```
ubuntu-bug ubuntuone-client
```

If that doesnt work you can go to:

[https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

Some information that would be helpful in solving your issue.
1. From a terminal session (Applications->Accessories->Terminal) run: tar -cjf ~/Desktop/syncdaemon-logs.tar.bz2 c~/.cache/ubuntuone/log/
2. Attach ~/Desktop/syncdaemon-logs.tar.bz2 to the bug report
3. Also attach your ~/.cache/desktop-couch/log/desktop-couch-replication.log

If you post any code into the Forums please sure to wrap it in "```
 
```"

thank you,
duanedesign

---

### Post by Jive Turkey on 2010-04-18
I ended up doing a fresh install with lucid beta2 for other reasons.  It works now as far as I can tell.  I will test further and report bugs, so thanks for the instructions above.

---

### Post by joshuahoover on 2010-04-19
> **Jive Turkey said:**
> I ended up doing a fresh install with lucid beta2 for other reasons.  It works now as far as I can tell.  I will test further and report bugs, so thanks for the instructions above.

Thank you for the follow up. I'm happy to hear things are working for you now with Beta 2. If you see this error again, please let us know via a bug report as Duane gave directions for. This provides us with key debug logs that we need to help determine the cause of the issue.

Thank you,

Joshua

---

