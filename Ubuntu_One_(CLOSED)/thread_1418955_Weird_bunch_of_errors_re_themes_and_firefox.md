---
title: "Weird bunch of errors re: themes and firefox"
date: 2010-03-01
forum: Ubuntu One (CLOSED)
---

### Post by hypnoticstate on 2010-03-01
Hi, I just reinstalled ubuntu one after I removed it a couple of weeks back and its just not playing ball, I have attached a screenshot showing the gui error and the console error.

I am using 9.10

---

### Post by joshuahoover on 2010-03-01
> **hypnoticstate said:**
> Hi, I just reinstalled ubuntu one after I removed it a couple of weeks back and its just not playing ball, I have attached a screenshot showing the gui error and the console error.

I am using 9.10

Thanks for including the screenshot! Based on that message, it sounds like Ubuntu One can't find Firefox to open the URL that leads you to add your computer to your Ubuntu One account. First, check System->Preferences->Preferred Applications and make sure your browser of choice is listed correctly there. If it looks OK there, then try the following from a terminal session: 

xdg-open [https://one.ubuntu.com](https://one.ubuntu.com)

If you can't open a URL using the command above then Ubuntu One won't be able to either.

Thanks,

Joshua

---

### Post by hypnoticstate on 2010-03-01
Thx so much joshua, i've been stumped several times since i started using ubuntu and it was a matter of pride never to ask for help ;)

many thx my friend, this fixed my problem.

the cause was, i had installed a website grabber, "webhttrack" which had installed seamonkey to do its dirty work, there was the conflict. Just apt-get remove both offending culprits and everythings working fine now, thank you !!!

---

