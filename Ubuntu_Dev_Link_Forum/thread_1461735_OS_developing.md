---
title: "OS developing"
date: 2010-04-24
forum: Ubuntu Dev Link Forum
---

### Post by pizzadude223 on 2010-04-24
I am running xubuntu, where would I go on there to edit my main OS codes. I wish to attempt to make something called twobuntu where you have a file panel on your left side and open applications and desktop on the right side. Thanks for any help.

---

### Post by schauerlich on 2010-04-26
```
echo $PATH | tr ':' '\n'
```

Probably a good place to start.

Also:

```
man apt-get
```

[http://www.gnu.org/prep/ftp.html](http://www.gnu.org/prep/ftp.html)
[http://kernel.org/](http://kernel.org/)
[http://www.x.org/wiki/DeveloperStart](http://www.x.org/wiki/DeveloperStart)

---

