---
title: "Info on how mod_ssl...Mine is all weird."
date: 2011-08-22
forum: Server Platforms
---

### Post by HighCommander540 on 2011-08-22
Hello I have a dilemma with either Apache or mod_ssl. I understand that many people recommend to keep the pass phrase on a SSL key file. So I have and when I reboot my machine I have to enter the pass phrase.

A problem has arisen recently, within the last two days, the server stops responding to requests. Nothing comes up except that the server cannot be found.

If I SSH to the box and restart Apache (having to enter the pass phrase) and it runs fine for about a day and then it does it again.

Is this supposed to happen? I don't think so since so many people use it.

---

### Post by pafoo on 2011-08-22
ssl would not have anything to do with that. I run it here on SEVERAL servers. What does the apache logs say?

---

