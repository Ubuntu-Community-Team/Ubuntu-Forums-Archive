---
title: "VM box - can't drag and drop"
date: 2020-12-19
forum: Ubuntu/Debian BASED
---

### Post by Perfect Storm on 2020-12-19
Greetings,

I'm running Deepin and have kubuntu in vm box. The problem is I can't exchange files between the two. Yes, I have set the option to "Bidirectional" in the drag and drop option, but nothing happens. I'm running the latest version of VM box.

regards

---

### Post by #&amp;thj^% on 2020-12-19
Did you first set-up a "Shared Folder"?
Also Guest addition is needed.

---

### Post by Perfect Storm on 2020-12-19
Shhared folder is set up.
I'm not sure how to set up guest. I can't find anything in the options regarding guest set up?

---

### Post by #&amp;thj^% on 2020-12-19
My bad; [https://linuxize.com/post/how-to-install-virtualbox-guest-additions-in-ubuntu/](https://linuxize.com/post/how-to-install-virtualbox-guest-additions-in-ubuntu/)
I found the link I wanted: [https://gist.github.com/estorgio/1d679f962e8209f8a9232f7593683265](https://gist.github.com/estorgio/1d679f962e8209f8a9232f7593683265)

---

### Post by Perfect Storm on 2020-12-19
Thanks.

---

### Post by #&amp;thj^% on 2020-12-19
> **Artificial Intelligence said:**
> Thanks.

:)
I'll be waiting to see the [SOLVED] portion.

---

### Post by Perfect Storm on 2020-12-19
> **1fallen said:**
> :)
I'll be waiting to see the [SOLVED] portion.

Never! Muwhahahahaha :P

---

### Post by #&amp;thj^% on 2020-12-19
> **Artificial Intelligence said:**
> Never! Muwhahahahaha :P

:lolflag:

---

### Post by TheFu on 2020-12-19
What is VM Box?

---

### Post by Perfect Storm on 2020-12-19
> **TheFu said:**
> What is VM Box?

VM Virtualbox. Just shorten down. :P

---

### Post by Perfect Storm on 2020-12-19
Another problem. It says I have no permission to the Shared directory.

[https://i.imgur.com/0UTlfvPh.png]("https://i.imgur.com/0UTlfvPh.png")

[http://i.imgur.com/UwmhJrth.png]("http://i.imgur.com/UwmhJrth.png")

---

### Post by Perfect Storm on 2020-12-19
SOLVED!!!

run this command in VM:
```
sudo adduser $USER vboxsf
```

---

### Post by TheFu on 2020-12-20
> **Perfect Storm said:**
> VM Virtualbox. Just shorten down. :P

Ah. I'd only seen it shortened to vbox.
Last time I used it, the vboxsf driver didn't handle file locking in an expected way. That cased issues with some editors.

---

