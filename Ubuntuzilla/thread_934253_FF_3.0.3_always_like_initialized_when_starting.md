---
title: "FF 3.0.3 always like initialized when starting"
date: 2008-09-30
forum: Ubuntuzilla
---

### Post by Zajeec5u on 2008-09-30
Hi,
  since updating from FF 3.0.2 to 3.0.3 FF behaves likes a fresh install everytime I'm starting it.
ubuntuzilla notified me about the update, I quit FF 3.0.2, started it with sudo, let it restart.
Since then it's like having a new profile, licence agreement showing up etc..
Any idea what's going on?
It's still Ubuntu 7.10 I'm using.

Thanks, Michael.

---

### Post by nanotube on 2008-10-01
hi
if you started it with "sudo" rather than with "gksudo", that would be the cause of the problem. some of the files in your profile would now be owned by root, which would prevent it from updating them.

run the following command:
```
sudo chown -R yourusername:yourusername /home/yourusername/.mozilla
```

(replace "yourusername" with your actual username, of course)

and that should take care of this problem.

---

### Post by Zajeec5u on 2008-10-02
Hi, thanks for responding!
I think I checked the file properties in the profile folder, so I'll re-check.

Thanks a lot, Michael.

---

