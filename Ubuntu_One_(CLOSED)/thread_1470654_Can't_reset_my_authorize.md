---
title: "Can't reset my authorize"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by pureroot on 2010-05-03
i remove the machine's connected via ubuntuone account
but ubuntuone-client (look like) use last reference author. 
and ubuntuone-pref. freeze... (it can't pass authen.)

three process's still run:
- ubuntuone-login
- ubuntuone-preferences
- ubuntuone-syncdaemon

hope help...;-)

---

### Post by pureroot on 2010-05-03
> **pureroot said:**
> i remove the machine's connected via ubuntuone account
but ubuntuone-client (look like) use last reference author. 
and ubuntuone-pref. freeze... (it can't pass authen.)

three process's still run:
- ubuntuone-login
- ubuntuone-preferences
- ubuntuone-syncdaemon

hope help...;-)

oh!
when i use ubuntuone via rhythmbox 
it's ask me for add machine and 
now i can setting new ubuntuone account

... ubuntuone-preference's not freeze 

pardon, i'm noob

---

### Post by joshuahoover on 2010-05-03
> **pureroot said:**
> oh!
when i use ubuntuone via rhythmbox 
it's ask me for add machine and 
now i can setting new ubuntuone account

... ubuntuone-preference's not freeze 

pardon, i'm noob

I'm sorry to hear Ubuntu One isn't working properly for you. You normally shouldn't have to do this but since we're experiencing issues on the server side, you may need to. Open a terminal session (Applications->Accessories->Terminal) and run:

killall ubuntuone-login ubuntuone-syncdaemon ubuntuone-preferences

Then try to open System->Preferences->Ubuntu One. In the mean time, we're working on fixing the server issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

My apologies for the inconvenience and thank you for your patience.

Joshua

---

### Post by pureroot on 2010-05-29
No problem, I'm support Ubuntu ... 
Ubuntu Cheer!!!

> **joshuahoover said:**
> I'm sorry to hear Ubuntu One isn't working properly for you. You normally shouldn't have to do this but since we're experiencing issues on the server side, you may need to. Open a terminal session (Applications->Accessories->Terminal) and run:

killall ubuntuone-login ubuntuone-syncdaemon ubuntuone-preferences

Then try to open System->Preferences->Ubuntu One. In the mean time, we're working on fixing the server issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

My apologies for the inconvenience and thank you for your patience.

Joshua

---

