---
title: "How could we send a notification from the terminal?"
date: 2015-12-02
forum: Ubuntu Phone and Tablet
---

### Post by ZICODIAN on 2015-12-02
In Ubuntu desktop, we can send a notification to the system using a command like the following:

```

notify-send "hello world"

```

I'm setting up a bunch of scripts running on my telephone and would like to know how to get them to create little notifications in the drop-down notifications of Ubuntu Touch. What'd be a good way to do this?

---

### Post by krusty8 on 2015-12-09
You can just use notify-send in ubuntu touch. It works for me. Sometimes it is *that* easy ;)

---

### Post by ZICODIAN on 2015-12-27
Super, thanks for that!

Also, for others reading, I got **notify-send **installed in the following way:

```

sudo apt-get -y install libnotify-bin

```

---

### Post by matt_symes on 2015-12-27
Hi

If this question has been answered for you then please mark the thread as SOLVED using the thread tools menu under post #1.

This will help others looking for a similar solution to you.

Kind regards

---

