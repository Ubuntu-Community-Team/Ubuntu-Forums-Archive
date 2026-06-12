---
title: "Auto-sign-in to Guest"
date: 2010-02-16
forum: Security
---

### Post by user2037 on 2010-02-16
Is it possible to auto-sign-in to the guest account? How about only after a delay?

Is it possible to add a Guest entry to the user list at the GDM welcome screen?

---

### Post by cariboo on 2010-02-17
Yes it is, but I wouldn't do it. Go to System->Administration->Login Screen. to set it up.

---

### Post by user2037 on 2010-02-18
There is no guest option available. Apparently I'll need to configure a guest user.

---

### Post by cariboo on 2010-02-18
Yes, you will have to create a guest user. If you do, make sure you set the permissions of your home directory to 700, so the guest user can't snoop around your home directory.

---

