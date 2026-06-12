---
title: "limit login attempts"
date: 2011-01-15
forum: Security
---

### Post by arapaho on 2011-01-15
I'd like to limit login attemts for specific user. I've found information in manpages:
[http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/limits.conf.5.html)
but I'm not sure if this '@' is purposly there, so would be that correct?
```
aparaho        -       maxlogins       4
```
or
```
@aparaho        -       maxlogins       4
```
Maybe '@' is a group syntax? I'm confused.

What happens after 4 failed loggins? Is it enough to restart system to get another login attempts?

Are there any other values that it is reasonable to limit for safety reasons?

---

