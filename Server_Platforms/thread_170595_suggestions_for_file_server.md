---
title: "suggestions for file server"
date: 2006-05-04
forum: Server Platforms
---

### Post by roddyguk on 2006-05-04
hi all, before i ask my question i just want to point out im quite new to linux (about 2 months) and ive been running ubuntu on my laptop and debian on an old p2 machine

right what i want to do is setup my old pc which i can stick under the stairs with my router to share all my music and videos across my network

also i want to make a couple of scripts so that when i put a dvd in the drive it will automaticly rip it to an AVI file with the correct film name and share it, also the same with audio cd's (make a folder with the correct name and make the mp3's there)

can you suggest some software i can use to set all this up and also i havent go a clue about writing scripts so could someone please give me a hand with that?

cheers

---

### Post by neouser99 on 2006-05-04
as far as the sharing stuff goes, samba works great, easy to setup.

the scripts on the other hand... my first guess would be a 5 minute cron or something that would check to see if there is something in the drive.. upon doing it, if cd in drive, lauch script that would create a lock file, then begin ripping what is in there, spitting the drive out when it is done. i am also not quite at that level with scripts, but i will tell you that google is awesome at teaching things :)

-neo

---

### Post by Peter76 on 2006-05-05
If you are only running Ubuntu; the easiest thing to do is to setuo a ssh-server; in Dapper nautilus is able to mount over ssh; the share then just sits on your desktop and the only thing you have to do is install the ssh-server on you server.

---

