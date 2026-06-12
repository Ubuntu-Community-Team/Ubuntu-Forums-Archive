---
title: "UFW Conf File"
date: 2016-06-21
forum: Security
---

### Post by ulrichkenneth on 2016-06-21
Hello All, 

I am looking for the Source Code for UFW. I am actively using it and it seems that I can't get the help I am looking for so I'm seeing if I can take this path.

I have my logging set to full. I am wanting the UFW AUDIT entries to be sent to ufw.log rather than disable it from being logged at all.

Yes, I know how to disable the entries from kern.log. No that is not what I want. I want those entries to be redirected.

Could someone point me to the UFW Conf File so that I can track down what I need to do?

---

### Post by Habitual on 2016-06-21
/etc/ufw/ufw.conf < --- make backup before editing.
See also [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

