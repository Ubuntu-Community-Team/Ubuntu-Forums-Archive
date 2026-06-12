---
title: "Evolution Email 3.21 Can't Add Signature Automatically or Manually"
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by benjamin-selzer on 2016-09-28
Greetings! Pleased to be here.

Having trouble with Evolution 3.21 (I know it's in final beta). I cannot add a signature. When I go to do this, and click Save & Close, nothing happens. When I X out of the window, nothing happens. I am forced to *killall evolution* to exit.

So I thought I would add it the old fashioned way. I copied my "signatures" folder out of **/.config/evolution/** from another system running Evolution 3.20 and pasted it into the same location in the new system. However, I'm surprised that when opening Evolution back up, it doesn't see this signature that I've manually added.

Anyone have any luck with adding a signature in 3.21 either the proper way or using my hack? Any idea why Evolution won't see it since I've put it in the right place?

Thanks,
B.

---

### Post by jbicha on 2016-09-28
Thanks. [Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=772150") filed.

---

### Post by benjamin-selzer on 2016-09-28
Great, thanks, but any idea how to add a signature manually using file manager in the meantime?

---

### Post by Frogs Hair on 2016-09-28
Moved to *Ubuntu Development Version*

---

