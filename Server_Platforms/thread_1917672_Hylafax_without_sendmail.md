---
title: "Hylafax without sendmail"
date: 2012-01-30
forum: Server Platforms
---

### Post by vroby67 on 2012-01-30
I just migrated from sendmail to postfix. Hylafax ceased working (stopped sending the emails with received faxes). Digging here and there, while removing and reinstalling hylafax, I discovered it shall find sendmail (or a compatible smtp) to work properly. It seems to be possible remove the request for sendmail installing hylafax from the source, but the only difference is that you can specify the path for sendmail binary.
I found some references on the procedures to make hylafax working with postfix, but all starting after a working hylafax setup.

Has someone an advice?

Thanks and ciao

---

### Post by vroby67 on 2012-01-30
Kick me in the pass...

Exceeding during cleaning operations after sendmail removing, I also removed the sendmail substitution program of postfix.
Restored the clean postfix setup and all is done.

Thanks anyway.

---

