---
title: "FroFTP is missing?"
date: 2005-12-25
forum: Server Platforms
---

### Post by Connollyir on 2005-12-25
Whenever I try and <apt-get install proftpd proftpd-common ucf> Ubuntu can't find it. I am connected to the internet - is this a common problem among all Ubuntu users or am I alone on it? More importantly, what can I do to get around it and fix it?

Thanks

-Ian

---

### Post by 23meg on 2005-12-26
It's in the Universe repository, which you should enable manually.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by Connollyir on 2005-12-26
[QUOTE=23meg]It's in the Universe repository, which you should enable manually.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)[/QUOTE]

I have enabled the Universe repository, but apt-get wouldn't reach it. In any case, I went around it by finding it on a mirror and converting the .rpm file to .deb and installing it that way.

Thanks for the help though

-Ian

---

### Post by 23meg on 2005-12-26
That shouldn't be your preferred method. Please report the exact errors you're getting with apt.

---

### Post by Connollyir on 2005-12-26
Well it seems I definitely took the hard road - I only enabled the extra repositories on my desktop and forgot to do it also on the server... and then I thought I did so I couldn't see why I couldn't find the packages. Seems it was all user error and lack of sleep :rolleyes: .

Sorry about the alarm.

-Ian

---

