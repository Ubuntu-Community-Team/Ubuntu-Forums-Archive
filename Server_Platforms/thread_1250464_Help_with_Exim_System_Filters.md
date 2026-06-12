---
title: "Help with Exim System Filters"
date: 2009-08-26
forum: Server Platforms
---

### Post by the ev on 2009-08-26
I'm having trouble making a filter that does the following...

I need a filter that is a SYSTEM WIDE filter that sets the bounce email to a specific email address.  Again, I want every message sent through my MTA (Exim4) to have one email address for all bounces.

I tried:
```

# Exim filter
deliver $recipients errors_to the_one@email.address

```

in /etc/exim4/filters/bounces.filter

And I tried enabling it like:
(in /etc/exim4/update-exim4.conf.conf)
```

...
system_filter = /etc/exim4/filters/bounces.filter

```

... but no luck. I get back "/etc/exim4/update-exim4.conf.conf: 32: system_filter: not found" when I try to restart exim.

How can I do this? Thanks for the help!

---

