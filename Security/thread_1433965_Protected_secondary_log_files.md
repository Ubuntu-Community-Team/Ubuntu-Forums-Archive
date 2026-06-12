---
title: "Protected secondary log files"
date: 2010-03-19
forum: Security
---

### Post by Webnet on 2010-03-19
Is it possible to somehow setup a secondary group of log files that log every action taken on the server where your average user wouldn't know that they're being logged.  Perhaps if a hacker got in and messed around or something you'd be able to see what they did, but they wouldn't have permission to modify the file.

---

### Post by unspawn on 2010-03-22
There's several ways to log information (shell history, 'script', 'screen -L', Rootsh, Sudosh, BaSH logging patch, THC vlogger, ttyrec, SE Linux, GRSecurity et cetera) each with their pros and cons but since you offered the example of having an account of what commands an intruder performed I should emphasise that any logging effort only makes sense if it is part of a wider FOV in terms of security. 

A lot of "common" attacks, apart from those nasty VNC(-ish) or SSH ones, are performed through the web stack. So not (publicly) running outdated, unmaintained or vulnerable versions of software and properly hardening your machine should be your first target. If you think MoSCoW (prioritisation) then the kind of logging you're looking for is not a "must have", it's a "could have". 

Most attacks over the 'net, successful or not, will be preceded by lots of recon so letting something like Logwatch report regularly (plus actually reading those emailed reports) makes it easier to weed out the noise and take action well before the trouble starts. *Prevention is better than cure* and all that.

Finally if a compromise leads to the attacker gaining root account rights then syslog, or any log file, will be at its mercy. Making syslog log to an impenetrable remote syslog server gives you a better chance at maintaining log integrity. 

If you want something to read security-wise check for instance the "Securing Debian" manual as a lot of it still applies today.

---

