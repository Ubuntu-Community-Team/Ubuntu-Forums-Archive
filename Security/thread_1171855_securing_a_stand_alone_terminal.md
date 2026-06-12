---
title: "securing a stand alone terminal"
date: 2009-05-27
forum: Security
---

### Post by redman88 on 2009-05-27
okay so i am putting a stand alone terminal together for work. I have been asked to make it so that the workers can only fill out some reports and print some documents. I would like to make it so that they can't even save. so i am not quite sure if the question should go here or some were else.

---

### Post by cariboo on 2009-05-27
You may want to have a look at pessulus, From the synaptic description:

> pessulus enables the system administrator to set mandatory settings in
GConf, which apply to all users, restricting what they can do, which may
be of particular usefulness for kiosks (internet cafes, for example).

Examples of what can be locked down are the panels (no changes in the panel
configuration are allowed, locking their position and their contents), some
of their functions individually (disabling screen locking and log out), the
web browser (disabling specific protocols, arbitrary URLs, forcing the user
to be in fullscreen mode), among many others.

---

### Post by redman88 on 2009-05-28
thanks i will look into that further

---

