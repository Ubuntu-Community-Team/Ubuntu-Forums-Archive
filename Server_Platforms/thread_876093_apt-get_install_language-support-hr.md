---
title: "apt-get install language-support-hr"
date: 2008-07-31
forum: Server Platforms
---

### Post by aljosa on 2008-07-31
apt-get install language-support-hr on gutsy resulted in:

 6150 ?        R     93:38 localedef --no-archive --magic=20051014 -i hr_HR -c -f UTF-8 hr_HR.UTF-8

kill -9 is not working, after reboot i've tried "dpkg --configure -a" and "apt-get --reinstall install language-support-hr" with same result.
localedef takes 100% cpu and it can't be killed.

any idea/tip what i can do?

---

