---
title: "Automatic notification of available updates."
date: 2009-09-30
forum: Server Platforms
---

### Post by rnodal on 2009-09-30
Hello all,

Is there an "ubuntu way" of getting an email notification whenever there are packages available for update?

I was planning on writing a perl script to run it as a cron job that will send me an email everyday with the amount of packages that are available for update and which ones. 

Any recommendations on how to accomplish this?

Thank you very much for your time.

-r

---

### Post by cariboo on 2009-10-01
Have a look at apticron, it is in the repositories. It will email you when there are updates available.

I'm running 9.04, in the motd it tells you when there are updates available when I look in remotely.

---

### Post by gobbledigook on 2009-10-01
but why does it not tell you when you log in locally? is this something that will be implemented soon? not that i need it particularly... was just wondering about the inconsistancy ;)

---

