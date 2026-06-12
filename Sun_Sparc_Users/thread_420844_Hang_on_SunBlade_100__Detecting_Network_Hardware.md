---
title: "Hang on SunBlade 100 / Detecting Network Hardware"
date: 2007-04-24
forum: Sun Sparc Users
---

### Post by jdeisenberg on 2007-04-24
The latest release (19 Apr 2007) successfully detects the USB keyboard [that's where it hung up before], but now hangs when it gets to "Detecting Network Hardware".  I have a SunBlade 100, using the latest OBP.

Any suggestions?

---

### Post by jdeisenberg on 2007-05-16
Problem solved. I'm posting this in case anyone else has the same issue:

1) The machine had only 128MB memory. No wonder it had problems.

2) I've found that typing the following at the [FONT="Courier New"]boot:[/FONT] prompt helps immensely:
   [FONT="Courier New"] install ide=nodma[/FONT]

---

