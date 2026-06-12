---
title: "Init scripts"
date: 2007-02-20
forum: Server Platforms
---

### Post by rpr on 2007-02-20
Hi,

I want to make my console azureus startup as a service on boot.
Anyone who has some good tutorials on how to create init scripts?

Thanks in advance;

---

### Post by jtc on 2007-02-20
I don't have any tutorial, but I can give you a good place to start.

```
man start-stop-daemon
```

That, and looking at some of your existing init-scripts should go a long way. Some of them are actually rather well-commented.

It does help being somewhat familiar with writing shellscripts thought.

---

