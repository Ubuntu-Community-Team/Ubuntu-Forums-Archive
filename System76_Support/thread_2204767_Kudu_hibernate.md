---
title: "Kudu hibernate"
date: 2014-02-10
forum: System76 Support
---

### Post by kevin53 on 2014-02-10
I just got my Kudu Professional and love it so far.

I noticed that "hibernate" is not an option in the power settings.

is there a way to get it to hibernate?

---

### Post by untrustytahr on 2014-02-11
Disclaimer: I don't have a kudu (mine is a gazelle) so I don't know if there's anything about the hardware that would be needed to be activated in BIOS and I'm not currently running Ubuntu so YMMV.Hibernate is not supported by default because of the possibility of data loss if you didn't save your work before hibernating and the hibernation failed for some reason.  That said, it works perfectly fine for me.  You can test it and enable it in menus following this:  [https://help.ubuntu.com/13.10/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/13.10/ubuntu-help/power-hibernate.html)

---

### Post by kevin53 on 2014-02-12
thanks untrustytahr.  it hibernates fine with the pm-hibernate command.  I put in the pkla file and the hibernate function is enabled in the power settings screen.

but when I let the battery run down it warns that it is hibernating just before it turns itself off, but then powering back up starts a fresh boot.

no big.  I'll just use the command when I want to hibernate.

---

