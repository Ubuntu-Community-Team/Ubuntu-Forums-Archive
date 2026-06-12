---
title: "synaptic no history"
date: 2015-07-04
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-07-04
At least here synaptic either doesn't keep a history or if it does it  doesn't display anything

---

### Post by PaulW2U on 2015-07-04
I see the same here. Time (to search) for a bug report? ;)

Edit: You've already done it - [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471445) :p

---

### Post by ventrical on 2015-07-04
+1

---

### Post by mc4man on 2015-07-04
The logs are being created in /root/.synaptic/log, just not viewable in synaptic

---

### Post by ajgreeny on 2015-07-04
+1
Same here.

I had not noticed this before; is it something that has just happened, or has it been like this from the start?

EDIT:
I have just looked again, and searched for something I know I have installed using synaptic, and noticed the message that it was found.  It looks as if the left hand pane is just narrow and invisible, and I have just dragged the pane division to the right and full history is visible again.

Unfortunately it looks as if you have to do this every time you use it as the pane-divider moves far left after a restart of synaptic.

Give it a try!  I hope I'm right and it works for all of you as well.

---

### Post by ventrical on 2015-07-04
> **ajgreeny said:**
> +1
Same here.

I had not noticed this before; is it something that has just happened, or has it been like this from the start?

EDIT:
I have just looked again, and searched for something I know I have installed using synaptic, and noticed the message that it was found.  It looks as if the left hand pane is just narrow and invisible, and I have just dragged the pane division to the right and full history is visible again.

Unfortunately it looks as if you have to do this every time you use it as the pane-divider moves far left after a restart of synaptic.

Give it a try!  I hope I'm right and it works for all of you as well.


Good eye.

---

### Post by mc4man on 2015-07-04
> **ajgreeny said:**
> +1
  It looks as if the left hand pane is just narrow and invisible, and I have just dragged the pane division to the right and full history is visible again.

Unfortunately it looks as if you have to do this every time you use it as the pane-divider moves far left after a restart of synaptic.

I should have checked..
Seems it's a new variation on the gtk3 issue that started in 14.04 or so. Though before the dates area was just small, you could see at least part of the date. (- If you have have a 14.04 or 14.10 install you can see what I mean, never checked in 15.04
So in the case of 14.04 to see full dates you'd need to expand every time, for 15.10 the same deal, pulling over is not persistent

Will adjust bug, forget if I ever filed one in 14.04, probably not.

---

### Post by dino99 on 2015-07-05
Seems related to [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471509](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1471509)

---

