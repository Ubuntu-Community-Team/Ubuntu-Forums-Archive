---
title: "Lastb entry and terminal, bug? My own error? Or worse?"
date: 2006-06-10
forum: Server Platforms
---

### Post by RavenOfOdin on 2006-06-10
Usually, I don't get these kinds of things popping up.

But just a while ago, in Ubuntu and doing some random checks, I typed in "lastb -aix" at a console and got this:

```

UNKNOWN    Fri Jan 9   17:30-17:30 (00:00) 0.0.0.0

```

Normally I would have considered this very bad, but doing a check of my authorization log I found this:

```

06.09.2006    05:30:05    localhost login[9819] (pam_unix) authentication failure; logname= uid=0 euid=0 tty=tty2 ruser= rhost=
06.09.2006    05:30:05    localhost login[9819] (pam_unix) check_pass: user unknown
06.09.2006    05:30:07    localhost login[9819] (pam_unix) FAILED LOGIN(1) on tty1 for 'UNKNOWN', user not known to the underlying authentication module.

```

chkrootkit and rkhunter both didn't turn up anything unusual, the former save for a java file in /usr/lib/jvm which was put there by AVG.

Then, I remembered that I was playing around in the console trying to get dselect running from a terminal, and get KDM down, so I could remove guarddog correctly. . .It had been giving me trouble.

When I switched using Ctrl-Alt-F1 I saw nothing but a black screen and the blinking cursor in the middle of the screen. Switching to F2 made the black cursor move up a few lines.

After I pressed Enter twice, the terminal would line by line start to show itself. :confused: until I got to readability.

So. . .
The title of the thread explains it all. What the sweet heck happened?!!?

I've never seen the blank terminal and dis/reappearing lines trick in my LIFE, and it may well be that I at a login prompt (though I didn't know it since the screen was blackened) pressed Enter, thereby giving rise to an incorrect login notice? I wasn't hooked up to the Internet at the time so this is a much more logical solution than a crack attempt on my machine. Has anyone else experienced a bug like this where the terminal just blinks out and doesn't come back until a press or two of Enter?

If this isn't a bug. . .Could any malicious applications that y'all know of cause something like that, and how do I check for them?

---

