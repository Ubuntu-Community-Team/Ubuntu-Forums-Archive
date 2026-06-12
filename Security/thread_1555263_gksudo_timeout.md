---
title: "gksudo timeout"
date: 2010-08-17
forum: Security
---

### Post by svaens on 2010-08-17
Hi guys, 

quick and easy ( i suspect) question:

did the timeout for gksudo get its default increased with the last update (i updated this morning a 'just in' update several important looking components, 18th august 2010) ?

I use gksudo regularly, having an application that needs to start with such permissions (truecrypt for one). And suddenly it seems like directly after login, it didn't ask for password, and hasn't asked for password since in the times i've re-tested it. 
I am sure it would timeout after about 5 minutes before, and now, I think i read somewhere it is now 15 minutes? 

Has it changed?

---

### Post by CharlesA on 2010-08-17
The default for sudo and gksu has always been 15 minutes.

---

### Post by svaens on 2010-08-17
ok, thanks. 

I wonder, a simple google search doesn't seem to yield any documentation which gives me that magical figure of 15 minutes.p
And I have had a bit of a browse through the gnome site, and not found it. No search functionality to dig into it either looking for keywords. 

Where should I find such information, so I don't have to go asking stupid questions here in the forums? i.e., what do you do when google isn't doing it?

---

### Post by svaens on 2010-08-17
silly incorrect content removed

---

### Post by cariboo on 2010-08-17
According to [this]("https://help.ubuntu.com/community/RootSudoTimeout") howto, the timeout is still 15 minutes.

---

