---
title: "Non-pae kernel?"
date: 2011-12-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by scradock on 2011-12-18
I'm trying to install Precise in Virtualbox, running under ubuntu. The installation fails to start (from the i386 liveCD iso) because VBox claims that it needs a kernel without PAE.

Is there an install available with the non-pae kernel? I couldn't find one, even for Oneiric...

Or is this a different problem?

---

### Post by MoreOrLess on 2011-12-18
I think you need to check a box in Vbox to enable the host's PAE support [http://www.virtualbox.org/manual/ch03.html#settings-processor](http://www.virtualbox.org/manual/ch03.html#settings-processor)

---

### Post by 3Miro on 2011-12-18
How much memory have you allocated to the Virtual machine, unless you have 3-4GB allocated, you Ubuntu shouldn't be trying to start PAE.

---

### Post by scradock on 2011-12-18
> **MoreOrLess said:**
> I think you need to check a box in Vbox to enable the host's PAE support [http://www.virtualbox.org/manual/ch03.html#settings-processor](http://www.virtualbox.org/manual/ch03.html#settings-processor)

Thanks! just found it....

---

### Post by scradock on 2011-12-18
> **3Miro said:**
> How much memory have you allocated to the Virtual machine, unless you have 3-4GB allocated, you Ubuntu shouldn't be trying to start PAE.

Yes, that is odd - I had allocated 1024 MB....

But I think VBox was complaining the other way around - I hadn't checked the PAE box in Settings, but the kernel was the pae-enabled one.

Just saw that the non-pae kernel is to be continued for Precise - but is there an install image with it?

---

