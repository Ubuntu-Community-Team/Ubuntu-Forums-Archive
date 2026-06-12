---
title: "PPPoEconf not detecting modem"
date: 2011-09-05
forum: Server Platforms
---

### Post by Chrus on 2011-09-05
So linksys have stopped making the ADSL modem we normally use and we're been forced to start using a netcomm modem. Concidering features and price, it was the only reall option.

So we set the modem up in bridge mode with a ubuntu box taking care of PPPoE. Only problem is running pppoeconf with the netcomm plugged in results in no devices being found. We have to connect to our linksys, run pppoeconf, then swap back to the netcomm and everything works from there.

Is there a way to tell pppoeconf to not bother scanning for modems, just go ahead and set up on eth0? It would be nice to not have to rely on another modem to get these things set up.

Thanks

---

