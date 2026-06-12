---
title: "Disco Dingo: &quot;HTML5&quot; video support with Firefox"
date: 2019-03-18
forum: Ubuntu Development Version
---

### Post by ubname on 2019-03-18
Hi,

I know that using Ubuntu 18.04 or 18.10 I can stream rainews24, but this does not work in 19.04,
is there something I need to install to make it work? (I prefer not to install flash),


[ATTACH=CONFIG]282813[/ATTACH]

Thanks!

---

### Post by SeijiSensei on 2019-03-18
I'm using 19.04 and don't have this problem. I just visited rainews.it with Firefox, and the video played. I do not have Flash installed.

As a first step, rename the .mozilla directory in $HOME to mozilla.old, then try again. 

```

cd $HOME
mv .mozilla .mozilla.old

```

If that doesn't help, try reinstalling Firefox.

---

### Post by ubname on 2019-03-18
I resolved installing ubuntu-restricted-extras, thanks for the help!

---

