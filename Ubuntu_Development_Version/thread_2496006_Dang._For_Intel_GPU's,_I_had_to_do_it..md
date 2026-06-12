---
title: "Dang. For Intel GPU's, I had to do it."
date: 2024-03-11
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2024-03-11
I don't usually recommend to users to install a DEV Cycle version to normal Users, but... I had to.

Intel's new Ultra CPU's have ARC as it's iGPU. Supported by Linux Kernels 6.6 and newer. Today's current Mantic kernel is still 6.5 series.

I'm still working with the upstream intel Graphics Engineer teams on their 3rd party graphics drivers. For OOT (Out Of Tree kernel support), we are still working on 6.5 series... I just finished sending them an email on that. So there is that in a nutshell.

I was hoping to have them all to speed before the Noble release... Maybe still. Noble looks good for their other 3rd party drivers so far.

---

### Post by MAFoElffen on 2024-03-11
Explanation: OOT kernel support is when LTS kernels in Ubuntu use the HWE enablement stack changing kernels to newer...

Then things start to fail in the 3rd party world (my niche is for graphics support)... Like NVidia, AMD and Intel.

Intel 3rd party driver starting failing since Sept 2023, when 22.04 HWE went to 6.2. About the time we got that figured out, then 22.04 HWE went to 6.5 series... LOL

---

