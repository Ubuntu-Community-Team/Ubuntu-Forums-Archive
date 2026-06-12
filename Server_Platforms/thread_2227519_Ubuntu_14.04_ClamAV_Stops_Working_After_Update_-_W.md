---
title: "Ubuntu 14.04: ClamAV Stops Working After Update - Works After A Server Restart"
date: 2014-06-02
forum: Server Platforms
---

### Post by Robin_Wilson on 2014-06-02
Hello

I have installed a Postfix/Dovecot email server with ClamAV and SpamAssassin and it all works ok until it comes to the daily update task.

Increasingly after the server runs the daily update it seems to knock ClamAV off and this error is logged in the mail log:

```
[COLOR=#222222][FONT="Verdana"]CLAMAV: couldn't connect to: /var/run/clamav/clamd.ctl: Connection refused[/FONT][/COLOR]
```

This causes all incoming mail to get stuck in the queue until I reboot the server after which all the email is processed.

Please can someone tell me the best way to troubleshoot this and stop it happening?

Thanks
Robin

---

### Post by Robin_Wilson on 2014-06-02
Actually I'm wondering if I'm too low on memory and if that might be why.

I can't start the service as I get a can't allocate memory error:
/etc/init.d/clamav-daemon start

```

Error: mpool_malloc(): Can't allocate memory (262144 bytes).
LibClamAV Error: cli_ac_addpatt: Can't allocate memory for next->trans
LibClamAV Error: cli_parse_add(): Problem adding signature (3).
LibClamAV Error: Problem parsing database at line 56909
LibClamAV Error: Can't load main.ndb: Malformed database
LibClamAV Error: cli_tgzload: Can't load main.ndb
LibClamAV Error: Can't load /var/lib/clamav/main.cvd: Malformed database
LibClamAV Error: cli_loaddbdir(): error loading database /var/lib/clamav/main.cvd
ERROR: Malformed database

```

I pay for a VPS and it only has 1GB of ram which I thought would be enough for a mail server and hosting a few websites on Apache
I have just worked out how to enable a swap file so maybe that will fix it.
The memory wasn't full but was at 78% which is quite high.

It now shows 65% and the swap usage is 0%

---

### Post by Robin_Wilson on 2014-06-05
Hello

I have now resolved my problem.

The problem was just lack of memory.
I had installed dropbox and it was continually using all the available ram and cpu.
I removed it and things returned to normal.

I mapped a remote network drive for Box instead and that seems a better replacement for Ubuntu One.

---

### Post by edooze on 2014-11-01
> **Robin_Wilson said:**
> Hello

I have now resolved my problem.

The problem was just lack of memory.


Seconded. Had ~300MB free on my server, and thought it would be anything but this. Have upgraded the RAM as this was the only answer I could find, and it solved the problem. Who'd've thought that ~0.23mb would be the problem.

---

