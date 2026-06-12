---
title: "Synaptic Package Manager Repository &quot;Select Best&quot;"
date: 2008-07-03
forum: Ubuntu Brainstorm
---

### Post by RATM_Owns on 2008-07-03
Though it does not make such a difference, I think that when pinging the servers for the "Select Best Server" option in the Repository thing for Synaptic, it remembers the best time and if it takes over that time for a server, it skips it and goes to the next one.

---

### Post by smartboyathome on 2008-07-03
> **RATM_Owns said:**
> Though it does not make such a difference, I think that when pinging the servers for the "Select Best Server" option in the Repository thing for Synaptic, it remembers the best time and if it takes over that time for a server, it skips it and goes to the next one.

I don't quite understand what you are asking, but I think that this would make apt more complicated. Switching from one to the other isn't as simple as just replacing the URL. In fact, in development releases especially, the tool is useless as it detects the down servers as the fastest. Some servers have older versions of the package that you want, so it may even break the download.

---

