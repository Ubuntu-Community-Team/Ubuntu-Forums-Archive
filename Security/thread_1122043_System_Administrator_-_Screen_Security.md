---
title: "System Administrator - Screen Security"
date: 2009-04-10
forum: Security
---

### Post by ki4jgt on 2009-04-10
I recently installed the Windows Share program for windows networks. At my old school, the system administrator of the windows network, was allowed to view the screen of anyone on the school network. I was wondering if my boss could do the same on the corperation's wireless network. If so, what can I do to bar him access to my screen, I mean I know he can basically view my online activity, but I'm considering joining a communications network, that by federal law is required to be view by only me.

---

### Post by bodhi.zazen on 2009-04-10
If you are asking about Ubuntu we can help.

If you are asking about Windows I would direct you to a windows forum.

With Linux (Ubuntu) it is possible to view your sessions if your system admin has root access.

You could easily limit that with apparmor.

---

### Post by ki4jgt on 2009-04-11
I have it installed but how do I configure it?

---

### Post by bodhi.zazen on 2009-04-11
configure apparmor ?

Read the sticky and make a profile for your application.

Restrict access to xhost and ~./Xauthoruity in the profile for your application.

---

### Post by ki4jgt on 2009-04-11
I'm a complete beginner to Ubuntu, not computers in general, just Ubuntu I've been in the windows world too long. Where is the "STICKY" and how do I read it? SORRY FOR IGNORANCE

---

### Post by hyper_ch on 2009-04-11
the sticky are the topics on top of each forum that are seperated from the rest.

---

### Post by bodhi.zazen on 2009-04-11
To be honest you probably do not need to de anything at all.

If your sysadmin is untrustworthy there is nothing you can do except restrict physcial access to your Ubuntu box.

If your sysadmin knows how to connect to X remotely I think it is safe to assume that they can do do if they have physical access to your box no matter what you do.

---

### Post by ki4jgt on 2009-04-11
OK thnx

---

