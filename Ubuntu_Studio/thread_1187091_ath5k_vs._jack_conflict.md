---
title: "ath5k vs. jack conflict"
date: 2009-06-14
forum: Ubuntu Studio
---

### Post by om zanka on 2009-06-14
I have ubuntu studio 9.04 with a RT kernel.
When I start jack in real time mode then I get an xrun every 10 seconds.
This effect disappears when I do `sudo rmmod ath5k'.
I have wireless network via ath5k device.
Is it possible to resolve this conflict without module removing?

---

### Post by raboofje on 2009-06-14
I'm not sure, but you might be able to resolve this by giving jack more and your networking less priority. See [http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

---

