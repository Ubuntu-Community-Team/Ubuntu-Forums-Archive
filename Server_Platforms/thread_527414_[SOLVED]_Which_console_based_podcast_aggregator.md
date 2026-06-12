---
title: "[SOLVED] Which console based podcast aggregator?"
date: 2007-08-16
forum: Server Platforms
---

### Post by chrismyers on 2007-08-16
Hi there,

I'm looking for a console based podcast aggregator for my non-gui server.

I want to be able to set it & forget it & have my selected podcasts downloaded for me to listen to later.

Maybe something that can be kick-started by crontab once a week or so.

Is there anything that does this?

Cheers :)

---

### Post by netlogic on 2007-08-16
Bashpodder is very configurable. If you are migrating from your existing gui podcatcher such as ipodder and icepodder that support history and favorites through OPML file, try podget and hpodder. It would be a simple migration. I find podget  to be more mature.

---

### Post by chrismyers on 2007-08-17
> **netlogic said:**
> Bashpodder is very configurable. If you are migrating from your existing gui podcatcher such as ipodder and icepodder that support history and favorites through OPML file, try podget and hpodder. It would be a simple migration. I find podget  to be more mature.

Excellent :) Many thanks.

Podget does exactly what I need & easily works with crontab.

I tried hpodder first simply because it was in the repositories - I failed to get it working with crontab (like others in the forums).

Thanks again.

:grin:

---

