---
title: "Updating Firefox using Dapper 6.06"
date: 2006-06-09
forum: The Cafe
---

### Post by gatekeeper on 2006-06-09
Hi Folks,

I am running Kubuntu 6.06.

Can anyone tell me what I need to do to update Firefox to the latest version?

Thanks in advance.

---

### Post by aysiu on 2006-06-09
This terminal command: ```
sudo aptitude update && sudo aptitude install firefox
``` The only problem with that is that they just updated to 1.5.0.4, and when 1.5.0.5 comes out or 2.0 comes out, Ubuntu's repositories will always be a week behind or a few days behind.

If you want to always have the most up-to-date, use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) instead.

---

### Post by John.Michael.Kane on 2006-06-09
gatekeeper if the answer comes from aysiu you can beat it's the right answer since it's the only one that matters.:rolleyes:

---

