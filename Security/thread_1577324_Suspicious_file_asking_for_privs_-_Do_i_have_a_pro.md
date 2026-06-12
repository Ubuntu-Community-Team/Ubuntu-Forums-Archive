---
title: "Suspicious file asking for privs - Do i have a problem?"
date: 2010-09-18
forum: Security
---

### Post by HelloIndustries on 2010-09-18
i got this as i started my system:

> the application ' /bin/sh '/tmp/tmpY1jmKj'' lets you modify essential parts of your systemI cancelled it, then had dropbox complained about privs (so i suspect it might be linked), then had another, similar dialoge and another dropbox complaint.

I also don't seem to be able to paste text...

---

### Post by CharlesA on 2010-09-18
It sounds like you got something trying to run a shell script and asking for root privlages. In any case, delete the script and see if dropbox still gives you those errors.

---

### Post by HelloIndustries on 2010-09-18
> **CharlesA said:**
> It sounds like you got something trying to run a shell script and asking for root privlages. In any case, delete the script and see if dropbox still gives you those errors.

i'll give that a try next reboot :)

---

### Post by CharlesA on 2010-09-18
As long as you didn't punch in yer password, you'll be ok. :)

---

### Post by HelloIndustries on 2010-09-18
actually, i can't find the script.

---

### Post by CharlesA on 2010-09-18
If you already rebooted, /tmp/ is emptied automatically.

---

### Post by HelloIndustries on 2010-09-18
well, from what i can tell based on observation, it looks to have been something to do with dropbox starting up and checking for updates (i use dbupdater to keep up with the latest builds). It hasn't occurred on reboot.

---

