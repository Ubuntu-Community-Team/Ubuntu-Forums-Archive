---
title: "Sessions should be password protected?"
date: 2008-05-17
forum: Security
---

### Post by dmacdonald111 on 2008-05-17
I have put an idea to the ubuntu brainstorm regarding the sessions in ubuntu. You can jump over there to see the details and vote/comment/both by going here;

[http://brainstorm.ubuntu.com/idea/8693/](http://brainstorm.ubuntu.com/idea/8693/)

Basically put, the idea is;

To password protect;

Start Menu > System > Preferences

---

### Post by Monicker on 2008-05-17
I do not understand why you would need this.  If your computer is unattended and you leave your graphical sesison open, somebody could just as easily open a file browser or terminal and start deleting all of your files.  Just lock your desktop if you are going to be away from your machine.

---

### Post by hyper_ch on 2008-05-17
I agree with Monicker on that

---

### Post by dmacdonald111 on 2008-05-18
Perhaps the post is not clear enough as there seems to be some confusion over how access is gained. I am not worried about someone walking up to my desk and changing the sessions (although it would be annoying). I mentioned in the post 'an outsider or someone on the network', which I was meaning a hacker.

I also cannot see how sessions are deemed less important than, say, time and date which requires admin privileges to change, when sessions can contain some very important setups.

---

### Post by Monicker on 2008-05-18
How is someone going to hack your graphical session from "outside" and get into that menu?  Unless you have some kind of poorly implemented remote desktop function running, they will never see your graphical session.  That leaves other avenues of attack, such as exploitable/poorly secured services.  If I managed to "hack" your ssh password, I would still be able to get into your home folder, where all of your user specific settings are stored, and modify your settings or delete your files.  If I managed to get root access by "hacking" your system, then again it does not matter, because then I could change anything on your system.  There are several applications which are dependent on the system having a correct date and time - kerberos comes to mind - so it is deemed something which requires admin access in order to change.  You can't say the same of user preferences in Sessions.

So again, why password protect something which is specific to YOUR account and session settings, if you are already logged in as that user?

---

