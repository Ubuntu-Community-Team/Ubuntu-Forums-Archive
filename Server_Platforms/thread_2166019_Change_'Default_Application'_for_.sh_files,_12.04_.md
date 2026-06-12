---
title: "Change 'Default Application' for .sh files, 12.04 server"
date: 2013-08-07
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2013-08-07
Hi all

Prior to 12.04, I believe, you were able to set the 'Open With' application of xyz.sh to be 'cron', as well as 'Allow executing file as program'.

Cron is not listed under 'Other Applications' so how do you enable xyz.sh to run as a cron job?

TIA

---

### Post by TheFu on 2013-08-07
Set the permissions on the file to have "execute."
Also, the first line of the script needs to point at the real interpreter to be used. A few examples:
```
#!/bin/sh
```

```
#!/bin/bash
```

```
#!/usr/bin/env perl
```

Also, cron doesn't inherit many environment variables, so any that you need, should be set inside the script.

---

### Post by ChrisRChamberlain on 2013-08-07
TheFu

Thanks for your reply

The crontab looks like ```
*/5 * * * * /var/data/bin/myfile.sh
```

So should it look like? ```
#!/bin/sh */5 * * * * /var/data/bin/myfile.sh
```

---

### Post by ChrisRChamberlain on 2013-08-07
Post in haste, repent at leisure

What I should have put was  ```
*/5 * * * * #!/bin/sh /var/data/bin/myfile.sh
```

---

### Post by TheFu on 2013-08-07
a) you can edit replies. No need for a new one.

b) Sorry. I did a poor job explaining.  In UNIX/Linux, the extension has **nothing** whatsoever to do with anything ... except for a few GUI programs. Cron ignores it completely as do every other program.  This isn't MS-Windows. That first line (see my examples) is what tells the OS which interpreter to use for a script. It needs to be placed inside the script file - myfile.sh - in this case.  For command completion reasons only, a Linux shell program may pay attention to file extensions ... but that is all. It is the **execute** bit that really matters.

It is critical  that the file to be run has execute permissions.  If you do a **ls -al**, the results should look like this for your script file:
```
-rwxr-xr-x  1 root root    1939 Feb  8  2012 zcat
```
Obviously, with different owner, group, date and filename, but the "x" in the owner permissions is **absolutely critical.**  Understanding file permissions is an important skill for Linux users. Google for "linux permissions tutor" to learn more. A beginning level is all you need - 3 minutes to learn - tops.

---

### Post by ChrisRChamberlain on 2013-08-08
TheFu

Thanks for your input and explanations.

I have left the crontab as it was before as the first line in xyz.sh is ```
#!/bin/bash
```so it works without changing the default application.

---

### Post by TheFu on 2013-08-08
> **ChrisRChamberlain said:**
> TheFu

Thanks for your input and explanations.

I have left the crontab as it was before as the first line in xyz.sh is ```
#!/bin/bash
```so it works without changing the default application.

Just so we are clear - there isn't an idea of a "default application" like you believe on Linux.  It is something added by just a few programs. Extensions generally don't matter on Linux for programs. It is the file permission "execute" setting and , for scripts, the first line which tells the OS which script interpreter to use.

Try this: Rename your file from "myfile.sh" to "myfile" or any other filename with any different extension. Try the run the file. It will still work - well, maybe not work, but it will behave the same as before - fail or work the same. ;)  If you change the first line to a different programming language, it will fail regardless of the extension.

There may be a "default application" inside a file-chooser ... but that is just 1 program, not the OS. I don't use Unity or Nautilus, so I don't know about them, but for PCmanfm, to control the default extensions for it, there is a text file under ~/.config/ somewhere. It applies only to that 1 program.
Similarly, bash has "command completion" that looks at extensions too.  It is 100% separate from anything PCmanfm uses, but hopefully, consistent.

I hope that clarifies more and doesn't confuse.

---

### Post by ChrisRChamberlain on 2013-08-08
TheFu

Alas the dreaded Windows mindset :(

Linux certainly has a different interpretation to the phrase 'Default application' and is a trap for those of us conditioned by years of exposure to the Windows experience.

So, onwards and upwards...

---

