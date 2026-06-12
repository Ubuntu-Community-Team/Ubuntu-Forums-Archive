---
title: "Jack and Skype at Same Time?"
date: 2008-04-22
forum: Ubuntu Studio
---

### Post by Ouoertheo on 2008-04-22
Hello,
I'm wondering if there is a way to get jack and skype to work at the same time. I'm trying to be able to broadcast live music produced in real time from my computer to a friend and jack won't start up while skype is alive.
Is it possible to get the two to play nice?

Oh yeah, I'm Using Ubuntu Studio 7.04 AMD64 if that helps.

Thanks in advance :)

---

### Post by Stochastic on 2008-04-22
What you'll need to use is a sound server called Port Audio, and to do that I think you'll need to recompile both skype and jack to get them to recognize it (not even sure it's possible with 7.04).  The good news is that Port Audio is fully implemented in Hardy (which releases in two days).

---

### Post by eric71 on 2008-04-23
This page has some suggestions and links concerning oss2jack:

[http://alsa.opensrc.org/index.php/JACK](http://alsa.opensrc.org/index.php/JACK)

---

