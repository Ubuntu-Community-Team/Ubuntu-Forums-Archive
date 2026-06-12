---
title: "Did this happen to you with recordMyDesktop ?"
date: 2010-05-23
forum: The Cafe
---

### Post by alket on 2010-05-23
I recorded something and looked like this when i played it with Totem or VLC

[IMG]http://img179.imageshack.us/img179/3619/screenshotoutxogv.png[/IMG]

But, If i upload to Youtube or insert it to OpenShot or Convert it , it looks like this:

[IMG]http://img180.imageshack.us/img180/1889/screenshotopenshotdefau.png[/IMG]

Do this happen to you , or its just me, I even tried it to another pc , how can i fix this ?

---

### Post by dragos240 on 2010-05-23
What format is it in. Use ffmpeg -i recordmydesktop.file recordmydesktop.ogg, I'm certain that'll work, assuming you have ffmpeg, but I haven't seen anything like it.

---

### Post by alket on 2010-05-23
No, i tried everything I could find, nothing works so far.

---

### Post by retro89 on 2010-05-23
mencoder -idx file.ogv -ovc lavc -oac mp3lame -o file.avi

replace file with the name of your file

---

### Post by dragos240 on 2010-05-23
> **babaroga said:**
> No, i tried everything I could find, nothing works so far.

Why not post a link to the file. I'll convert it.

---

