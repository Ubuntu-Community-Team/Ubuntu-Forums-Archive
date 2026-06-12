---
title: "Ubunctu Customization Kit (UCK) customize_iso error"
date: 2008-04-23
forum: Ubuntu Customization Guide
---

### Post by JohnnyXmas on 2008-04-23
Hey All,

I'm using the Ubuntu Customization Kit to create a LiveCD that includes a bunch of Bash Scripts I wrote. When I run this:

```
sudo ./customize_iso
```

I get this:

```
Error while copying boot files (  boot/16x16.fnt boot/ar.tr boot/back.jpg boot/be.tr boot/bg.tr boot/bn.tr boot/bs.tr boot/ca.tr boot/cs.tr boot/da.tr boot/de.tr boot/el.tr boot/en.tr boot/eo.tr boot/es.tr boot/et.tr boot/eu.tr boot/fi.tr boot/fr.tr boot/gl.tr boot/he.tr boot/hi.tr boot/hr.tr boot/hu.tr boot/id.tr boot/init boot/it.tr boot/ja.tr boot/ka.tr boot/ko.tr boot/ku.tr boot/lang boot/langlist boot/log boot/lt.tr boot/lv.tr boot/message boot/mk.tr boot/ml.tr boot/nb.tr boot/nl.tr boot/nn.tr boot/pl.tr boot/pt_BR.tr boot/pt.tr boot/ro.tr boot/ru.tr boot/sk.tr boot/sl.tr boot/sq.tr boot/sv.tr boot/ta.tr boot/th.tr boot/tl.tr boot/tr.tr boot/uk.tr boot/vi.tr boot/zh_CN.tr boot/zh_TW.tr  ) to /remaster-iso/isolinux/, error=1
```

STDERR reports this:

```
cp: target `/remaster-iso/isolinux/' is not a directory
```

I went in and manually created the directory, even went as far as chmod 777, but this did not help. Ideas?

---

### Post by JohnnyXmas on 2008-04-23
Nevermind, I figured it out. I was invoking the scripts individually, instead of using the main script from /usr/lib/uck

---

