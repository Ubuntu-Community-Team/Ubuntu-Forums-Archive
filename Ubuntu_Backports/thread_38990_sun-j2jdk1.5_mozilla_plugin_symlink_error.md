---
title: "sun-j2jdk1.5 mozilla plugin symlink error"
date: 2005-06-02
forum: Ubuntu Backports
---

### Post by crvendramini on 2005-06-02
Hi

I want to report a little problem after install sun-jdk1.5 via backports. The symlink to mozilla plugin isn't correct,  and the browser can't  find it out of the box.

Apt installs the symlink in "/etc/alternatives/firefox-javaplugin.so" and points to "/usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so".

But the correct path to mozilla (or firefox) javaplugin is:

"/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so"

After edit the respective symlink path to mozilla/firefox plugin, the browser could find it  and presented  through "about:plugins".

Well, that's all....

---

### Post by RastaMahata on 2005-06-02
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so

---

### Post by crvendramini on 2005-06-03
[QUOTE=RastaMahata]sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so[/QUOTE]

I did it before, but I think that the package must be  corrected.

Thank you,,,

---

### Post by RastaMahata on 2005-06-08
[QUOTE=crvendramini]I did it before, but I think that the package must be  corrected.

Thank you,,,[/QUOTE]
 I hope it does in the next release :)

---

