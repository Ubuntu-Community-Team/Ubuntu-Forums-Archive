---
title: "firefox restart problem"
date: 2005-02-25
forum: Ubuntu Backports
---

### Post by fabiang on 2005-02-25
Hi,

i was installed Firefox from backports proyect: [I]Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.5) Gecko/20041209 Firefox/1.0 (Ubuntu) (Ubuntu package 1.0-2ubuntu4-warty99)
[/I]

my problem is
when i install extencions this sayme: *this item will be installed after you reestart firefox*

well i close firefox, i open firefox and the extentions are nos installed (the message is the same). I turn off my notebook, i turn on it and the message are the same...  :confused: 

Some help?

---

### Post by jdong on 2005-02-25
exactly what extensions are you trying to install?

---

### Post by fabiang on 2005-02-25
They are:

- Adblock 0.5.2.039
- Language ES-ar (localizacion para firefox 0.9)

They was selected to download directly from update.mozilla.org

Note: i can't unistall too, the infinity message are : *this item will be unistalled after you reestart firefox*

Thanks a lot

---

### Post by techn9ne on 2005-02-25
I've had that problem too w/ firefox on windows. Its in bugzilla.

Try backing up your bookmarks and deleting the entire mozilla profile directory.

---

### Post by jdong on 2005-02-25
As soon as Firefox 1.0.1 hits Hoary/Sid, I'm backporting it, for the IDN spoofing fix. Hopefully, it'll fix this issue.

---

### Post by fabiang on 2005-02-26
i was deleted ~/mozilla/.firefox and nothing, well i'm waiting for firefox 1.0.1
Thanks

---

### Post by jdong on 2005-02-26
I'm not gonna wait for 1.0.1.... I'm backporting 1.0+dfsgwhatever now. It has a temporary workaround for the IDN bug, but also fixes many other bugs.

---

### Post by perigee on 2009-05-31
seams that ubuntu firefox modifications is out-of-date. When i disable this addon, all works...









Ubuntu 9.04
Firefox 3.0.10

---

