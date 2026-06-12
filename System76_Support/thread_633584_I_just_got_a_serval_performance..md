---
title: "I just got a serval performance."
date: 2007-12-06
forum: System76 Support
---

### Post by Royal_Pwner on 2007-12-06
Arrived 5-10 minutes ago. I booted it up, and all I get is a blank screen with a blinking white underscore. What do I do?

---

### Post by ectospasm on 2007-12-06
This is only a guess, but your display manager doesn't appear to be running, or it's running on a different virtual terminal.  If you hit ALT-F7 or ALT-F8 you should get to the virtual terminal where it's running.  If you don't see anything on F7-F12, you can hit ALT-F1 (or CTRL-ALT-F1) and you should be able to login and launch GDM or KDM.  Just login, and "sudo -i" to give you a root shell so you can launch GDM/KDM/etc.  Do this in the root shell:

/etc/init.d/gdm start

Remember, this is only a guess, so your situation may be different.

---

### Post by Royal_Pwner on 2007-12-06
It's resolved. Thanks.

---

### Post by Royal_Pwner on 2007-12-06
New problem now. I've got 3 updates that won't get downloaded. I can post a screenshot if needed.

---

### Post by Royal_Pwner on 2007-12-06
Nevermind. It works now.

---

### Post by ryanVickers on 2007-12-06
sorry, but I have to ask what exactly this is?  Your all talking about it like it's a noun, but the word "performance" means how well/fast/efficiently something does it's job really... :confused: if some one could clear this up for me ... :p
and "several performance"?  once again, don't get this because of what I said above, but ... lol

---

### Post by theologian aaron on 2007-12-06
the term "serval performance" refers to a model of laptop sold by [system76]("http://www.system76.com").    It is being used as a noun, because it is, in this case, a part of the noun.

Is this really all that strange?

---

### Post by ryanVickers on 2007-12-06
nope!  Makes perfect sense now! (but it is a strange name...) :p!

---

### Post by tgalati4 on 2007-12-07
Serval is four-legged mammal that eats penguins.  (When it can.)

---

