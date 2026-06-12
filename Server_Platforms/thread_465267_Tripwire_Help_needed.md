---
title: "Tripwire Help needed"
date: 2007-06-05
forum: Server Platforms
---

### Post by PetePete on 2007-06-05
Im setting up tripwire on my server, I've edited the policy file to report no errors, but each time I run tripwire --check it reports 1 violation, being /etc/tripwire

Now i presume this is because /etc/tripwire/someConfigFile is getting changed when I run the updates, how do I stop this showing up as a violation?


Thanks

---

### Post by PetePete on 2007-06-05
hmmm well after numerous tripwire --update 's its now started the not show any violations.

only thing i did different was run the commands from my home directory and not the /etc/tripwire folder. maybe that was it.

---

