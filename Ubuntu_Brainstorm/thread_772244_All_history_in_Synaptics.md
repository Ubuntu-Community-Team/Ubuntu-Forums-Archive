---
title: "All history in Synaptics"
date: 2008-04-28
forum: Ubuntu Brainstorm
---

### Post by csseurg6 on 2008-04-28
Hello,

in Synaptics, why we don't see the history of installs that we have make with the terminal?

(so, my idea on brainstorm: [http://brainstorm.ubuntu.com/idea/7010/](http://brainstorm.ubuntu.com/idea/7010/))

++

---

### Post by smartboyathome on 2008-04-28
I think this may work for the few times people have problems and can't remember what they installed, but other than that I don't see it being used.

---

### Post by csseurg6 on 2008-05-08
VOGT wrote:

> The best way to implement this is probably to change the current code in apt that writes out /var/log/apt/term.log to /var/log/apt/term-$date.$time.log and add a header there similar to the header in the synaptic log. Then we can just point synaptics logviewer to /var/log/apt/ and we get the added benefit of having full terminal logs in synaptic too.

:)

---

