---
title: "Anyone here with microsoft clustering experience?"
date: 2008-12-16
forum: Windows
---

### Post by Metallion on 2008-12-16
The thing is we need one service to wait at least one minute after its dependencies are started. Does anyone know of a wait to delay its startup?

Just creating a new dependency service that runs a .bat file with sleep in it doesn't work. The cluster sees the batch file as started and just starts the other service while the batch is sleeping.

I think I thought about was to make my service dependent of a dummy service and not let the cluster autostart the dummy. Then I could run a batch file that sleeps and afterwards starts the dummy. But for this it must be possible to make a dependency that's not autostarted. Is this possible?

Thanks :)

---

