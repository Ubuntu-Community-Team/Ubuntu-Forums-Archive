---
title: "[SOLVED] uconv - character set conversions"
date: 2007-09-19
forum: Repositories &amp; Backports
---

### Post by refdoc on 2007-09-19
uconv was/is a command line utility which I occasionally used to make cyrillic or greek readable to me. It would change texts written in e.g. Cyrillic letters into the transliterated latin equivalent. 

I do distinctly remember using it on Ubuntu on my last ibook so, preumably 60.6 or 5.10- and yet I can not find it anymore in my current installation (7.04 i386) - neiher in my baseline install nor in the repositories.

Am i slowly dementing, has it been taken out of the repositories or is it renamed? Any help will be hugely appreciated.

Thanks

---

### Post by refdoc on 2007-09-19
Ok, solved.

 [http://download.icu-project.org/files/icu4c/3.8/icu4c-3_8-RHEL5-gcc4_1_1.tgz](http://download.icu-project.org/files/icu4c/3.8/icu4c-3_8-RHEL5-gcc4_1_1.tgz)

then 

 fakeroot alien --to-deb icu4c-3_8-RHEL5-gcc4_1_1.tgz

then 

 dpkg -i icu4c*deb

---

### Post by olejorgen on 2007-09-19
I have uconv installed on a non-upgraded feisty
```
dpkg -S uconv
libicu36-dev: /usr/bin/uconv
libicu36-dev: /usr/share/man/man1/uconv.1.gz
firefox: /usr/lib/firefox/components/uconv.xpt
firefox: /usr/lib/firefox/components/libuconv.so
```
So I guess installing libicu36-dev should do the trick too

PS: apt-file is a nice tool if apt-cache search does not returns any hits, and you know the binary should be available

```

sudo apt-get install apt-file
sudo apt-file update
apt-file search bin/uconv
>>libicu36-dev: usr/bin/uconv

```

---

### Post by refdoc on 2007-09-26
Thanks that worked fine.

But what a weird place? I thought -dev files are only headers!!!

---

### Post by olejorgen on 2007-09-26
Yes, a bit strange... Anyway, remember to mark thread as solved (thread tools -> mark as solved)

---

