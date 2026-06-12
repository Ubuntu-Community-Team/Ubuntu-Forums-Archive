---
title: "Kubuntu 10.10 Guest on VirtualBox Very Slow!"
date: 2011-01-15
forum: Virtualisation
---

### Post by jonesyp on 2011-01-15
Hello,

I run Virtual Box on my Vista 32Bit Dell Studio laptop and Kubuntu as a guest runs really slow.  Ubuntu 10.10 runs fine on the same machine.

Any ideas gratefully accepted.

I'm using the latest VirtualBox and have the Guest Additions installed. The laptop has 4GB Ram, and a 256MB Graphics Card, and 2.6Ghz CPU.

Thanks

Peter Jones
[www.simplysowseeds.co.uk](www.simplysowseeds.co.uk)

---

### Post by redrumrogue on 2011-02-01
I have just found the same issue with my new Kubuntu VM.  I think it is the desktop effects which seem to be enabled by default.  If you disable the effects altogether (go to system settings -> desktop effects) you should find it makes a big difference.  With a bit of experimenting you should find an acceptable middle-ground with the effects.  Also, try going to system settings -> application appearance -> Fine Tuning tab ... and adjust the display resolution / CPU setting.

Hope this helps.

---

### Post by bkelly65us on 2011-02-02
I turned off both the desktop effects and the nepomuk search.  Helped a little.

---

