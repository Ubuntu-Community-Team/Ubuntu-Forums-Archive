---
title: "rsync, how not to log &quot;Links&quot; ?"
date: 2010-04-01
forum: Server Platforms
---

### Post by rbalaa on 2010-04-01
Hello,

I'm running rsync and outputting the log to a file using --log-file  option. I am also using the --link-dest option, which in turn is adding  the hard link creation output for EVERY file in the log file. I want to  ONLY show the actual file transfer (if any) that take place.

In the 'log format' section of rsyncd man page [here ]("http://linux.die.net/man/5/rsyncd.conf")I  assume you can do this, I just can't make sence about the code. If  someone has better experience with reading it, can you please assist ?

Thanks in advance.

---

### Post by KiLaHuRtZ on 2010-04-01
Don't use the log option, just use full verbosity and append it to a file.

```
rsync -a[COLOR="Red"]v[/COLOR] /src/ /dst/ [COLOR="Red"]> /tmp/somefile.log[/COLOR]
```

---

### Post by KB1JWQ on 2010-04-01
Technically >> is append, > is overwrite.

---

### Post by rbalaa on 2010-04-01
> **KiLaHuRtZ said:**
> Don't use the log option, just use full verbosity and append it to a file.

```
rsync -a[COLOR=Red]v[/COLOR] /src/ /dst/ [COLOR=Red]> /tmp/somefile.log[/COLOR]
```

I tries this with >> however my files that are ONLY getting a hard link change are still being listed. I want to only log the actual transfers that's happening. I'm going nuts trying to figure out what I'm doing wrong.

Thanks.

---

