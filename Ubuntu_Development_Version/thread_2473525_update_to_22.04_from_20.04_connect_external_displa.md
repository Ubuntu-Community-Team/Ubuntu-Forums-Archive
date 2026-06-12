---
title: "update to 22.04 from 20.04 connect external display sometimes blank screen"
date: 2022-04-06
forum: Ubuntu Development Version
---

### Post by tbc2022 on 2022-04-06
i update to 22.04 from 20.04, everything is fine, expect external display sometimes black screen, Back to normal after a few seconds. check journalctl log an error.
> kernel: i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun

[ATTACH=CONFIG]290249[/ATTACH]

thanks for your help

it's black screen, misspell in topic sorry

---

### Post by tbc2022 on 2022-04-18
i add kernel param 'intel_iommu=on,igfx_off' three days ago, until now everything is fine.

---

