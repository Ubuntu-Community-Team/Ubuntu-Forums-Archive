---
title: "fluxus"
date: 2008-10-05
forum: Ubuntu Studio
---

### Post by tylerisfat on 2008-10-05
Ok, so bear with me as I'm rather a noob. I had Ubuntu 8.04, and i then installed the ubuntu studio packages over that. everything went fine.

Just tonight i downloaded a fluxus package, and installed it, and it installed correctly.

But how the hell do i open it? I can't find it anywhere, and I can't find any help on the web. can someone help me track it down and figure out what i'm missing?

---

### Post by Stochastic on 2008-10-05
By Fluxus I'm assuming you mean this: [http://www.pawfal.org/fluxus/](http://www.pawfal.org/fluxus/)

So welcome fellow livecoder! :)  (I'm a beginner chuckist myself)

A lot of the small applications that aren't in Ubuntu's regular repositories will not appear in your application menu (it's up to the package creator to put it there - not the system).  So to start these programs you simply need to open a terminal and type in the program name (by doing this, the system will look for an executable in the /usr/bin file - where any successful installation should put the executable).

You could also create a launcher as described here: [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher) but I'd assume a program like fluxus would be controlled via the terminal anyways, so it's less clutter to look at if you just manually start it.

---

### Post by tylerisfat on 2008-10-05
> **Stochastic said:**
> By Fluxus I'm assuming you mean this: [http://www.pawfal.org/fluxus/](http://www.pawfal.org/fluxus/)

So welcome fellow livecoder! :)  (I'm a beginner chuckist myself)

A lot of the small applications that aren't in Ubuntu's regular repositories will not appear in your application menu (it's up to the package creator to put it there - not the system).  So to start these programs you simply need to open a terminal and type in the program name (by doing this, the system will look for an executable in the /usr/bin file - where any successful installation should put the executable).

You could also create a launcher as described here: [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher) but I'd assume a program like fluxus would be controlled via the terminal anyways, so it's less clutter to look at if you just manually start it.


Thanks. Thats helpful indeed.

---

