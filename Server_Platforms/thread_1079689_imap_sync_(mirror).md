---
title: "imap sync (mirror)"
date: 2009-02-24
forum: Server Platforms
---

### Post by Eagleon on 2009-02-24
Hi Everyone,

I want to make a local mirror of my remote IMAP server (provided by my shared hosting service). I have been looking at a few tools for this, but not sure which one is suitable for me. I have a local dedicated server for personal use that I want to sync my remote IMAP to, and then use my mail client on a different machine to access that local copy only. If I delete anything, get an e-mail, etc... the changes I make the the local server copy should be made to the remote copy as well (and vice versa). Also, it would be nice to have backup features as well. Preferably, I would want it to run as a cron periodically checking my mail and updating both the remote and local versions. So far, I have looked at isync (mbsync), imapsync and offlineimap. 

Any thoughts? Thank you in advance...


EDIT: one more thing, obviously the local server mirror should have a consistent format that is compatible with an IMAP server (Postfix?), so I can serve the e-mails on my local network.

---

### Post by Eagleon on 2009-02-25
*bump*

no one has any ideas?

---

### Post by Oliver Crow on 2010-07-23
isync will synchronize remote IMAP folders to local Maildir folders. 

[http://isync.sourceforge.net/](http://isync.sourceforge.net/)

---

### Post by Eagleon on 2010-07-24
Hi there,

thank you for the reply. It's been months... :) ...well I did try this tool if I recall correctly. There was a problem because the origin server was Courier and destination was Dovecot. The Maildir format (for sub folders) did not match and there were some problems. How did I solve it? Basically I just added both servers to Evolution and manually did a copy paste for each account one by one. Probably not the "correct" way to migrate and definitely not practical... but I only had about 10 accounts to migrate so it wasn't too bad, and worked great.

---

