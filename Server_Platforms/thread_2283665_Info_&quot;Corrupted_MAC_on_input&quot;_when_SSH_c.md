---
title: "Info: &quot;Corrupted MAC on input&quot; when SSH connecting"
date: 2015-06-23
forum: Server Platforms
---

### Post by cboling on 2015-06-23
*I found another thread for which this might be an appropriate reply, but it was closed (and I failed to find any other threads that I felt were suitable), so I'll post here in case the information proves useful to someone.*

After an upgrade, I found that I could no longer connect to a particular server via SSH; I would immediately get a "Corrupted MAC on input" message.  Debug messages didn't seem to shed any light on the situation.

Knowing that it was an old server (not updated in years, and thus running an old version of OpenSSH) I looked at the options for MACs and found that, like ciphers, there were a whole lot of new ones that were being used in preference to older ones.

I looked at the list, tried an old-plain-looking one at random:

[INDENT]ssh -m hmac-sha1 *user*@*host*[/INDENT]

and was able to connect fine!  So...apparently whatever MAC they're agreeing to use is broken on that old daemon -- or at least they disagree on the details of the implementation...

---

