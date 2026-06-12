---
title: "Asus T100TA touchscreen driver"
date: 2014-06-07
forum: Ubuntu Development Version
---

### Post by vadim6 on 2014-06-07
Hi,
I have an Asus T100 and I got ubuntu installed on it.
T100 has a atmel MXT1664T touchscreen controller onboard which have a dedicated driver atmel_mxt_ts. Generic i2c_hid is loaded instead(touch is working).
My question is why the generic i2c_hid driver is used instead of atmel_mxt_ts?
Can I switch between them?

Thanks,
Vadim B

---

