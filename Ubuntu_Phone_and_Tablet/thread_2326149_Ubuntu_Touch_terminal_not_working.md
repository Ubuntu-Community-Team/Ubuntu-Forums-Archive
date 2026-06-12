---
title: "Ubuntu Touch terminal not working"
date: 2016-05-28
forum: Ubuntu Phone and Tablet
---

### Post by DonnieHarden on 2016-05-28
I've got a Nexus 4 running Ubuntu Touch 16.04 (r23) with multi rom. I downloaded the terminal app from the Ubuntu store. When I open the terminal I get the logo in the center of the screen, it disappears and the screen turns white. I've searched for answers and reinstalled everyrhing from Ubuntu to the terminal app. I enabled developer options. I cant find anything.

---

### Post by directive0 on 2016-05-30
Same here. Nexus 4, 16.04 (r23). Also did the same things you did; enabling developer options, etc.

---

### Post by slickymaster on 2016-05-30
*Thread moved to **Ubuntu Phone and Tablet**.*

---

### Post by pachugeek on 2016-06-03
Hi,


I have a similar problem. I've a OTA BQ M10 and when I executed Telegram, the first time was ok, but the second time I opened the app, it showed me a White Screen. It's irreversible...


Then I tried to investigate about this and I wanted to install Terminal. But when the installation was finish and I tried to execute, it showed me the same "white screen" and nothing happened.


I think this is a general problem with some configuration state, but I can't try anything (whitout terminal).


Any idea?
Anybody have the same problem?


PS. reinstall the apps don't have any effect, reboot neither.

---

### Post by donquichot2016 on 2016-06-03
If the file manager works, you can delete the the Telegram folders and see if that helps. Enable "Unlock full access" and "show hidden files", then remove: ~/.cache/com.ubuntu.telegram/ and ~/.config/com.ubuntu.telegram/ .
On my phone the problem was two-factor authentication. After disabling that from the Android app, Telegram works fine in Ubuntu Touch.

---

### Post by pachugeek on 2016-06-06
@donquichot2016 thanks for your answer. I tried your solution, but nothing happens.

But my problem was SOLVED when I saw (I'm sure to have looking several times) that I had pending a OTA upgrade. Then all worked perfect.

Thanks again and sorry.

---

