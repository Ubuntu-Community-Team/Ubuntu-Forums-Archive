---
title: "Console Privacy Method?"
date: 2011-10-28
forum: Security
---

### Post by jbo5112 on 2011-10-28
In my default .bash_logout file (in /etc/skel and thereby every user account), it runs the clear_console program when I log out.  The comment says "When leaving the console clear the screen to increase privacy", however this also clears the screen when I log out of an ssh session.  There was a decent chance I wanted to keep that information on my screen.  Yes, I can probably scroll back to see it, but that only lasts until I type something.

This privacy can instead be accomplished by placing a few control characters at the begging of /etc/issue, and leaving the default log out so that it does not clear the screen.  With the clear handled by /etc/issue, it is more difficult and unlikely for anyone to disable the console clearing and leave something inappropriate (obscene or confidential) for the next user, not that people use the console much.  It's also good practice to enforce proper security policies from a privileged account, where it's harder to change, instead of hoping users will leave an annoying practice in place.

Does anyone know why Ubuntu chose the method they did for clearing the console?  I agree with clearing the console, but I get tired of changing the method on every new install to keep my screen from being cleared when I log out of ssh.  There are other shell/console defaults that annoy me, but this one doesn't make any sense.

If you're curious how to clear the console with /etc/issue, run "clear >> /etc/issue" as root.  This adds the control characters to the end of the issue file, then edit the file to move the new bottom line to the top (tested to work in vim).

I much prefer this method.  I did not file a bug report on this, since I assume someone has a good reason for configuring Ubuntu to run this way, but the only possibilities I can think of would be ignorance, my method possibly not working with some Unicode or international settings, or someone really wanting to leave a console greeting to the next console user.

---

