---
title: "Apparmor profile for Windows (Wine) application"
date: 2012-08-06
forum: Security
---

### Post by KenSharp on 2012-08-06
Hi,

I'm hoping someone can help me with this. I have created an Apparmor profile for the [Gómezpeer]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6636") which I run under Wine. I only run three apps under Wine on my main machine so I only want to limit this one application.

```
@{WINE}=/home/user/.wine

"/home/user/.wine/drive_c/Program Files/Gomez/GomezPEER/bin/GomezPEER.exe" {
        /@{WINE}/* rwix, # Allow access to the .wine directory
}
```

Apparmor seems to like this and I have seen no problems as yet. The problem being that AFAICT this will simply allow the application to access @{WINE}, and will not perform any kind of deny.

What I want to do is allow the application to only access the .wine directory, denying access to any other part of the filesystem (Wine can still access the necessary libraries).

```
deny /* rw,
```
will not work as deny rules take precedence.

According to the man pages the caret **^** can be used as a NOT argument (e.g. **[^.]** means "all files that are not . files").

Annoyingly this does not seem to work for full paths.

```
deny [^/@{WINE}] rw,
```
This throws an error.
> AppArmor parser error for /etc/apparmor.d/gómezpeer in /etc/apparmor.d/gómezpeer at line 9: Found unexpected character: '['

I must be missing a trick here. Can anyone point me in the right direction?

---

