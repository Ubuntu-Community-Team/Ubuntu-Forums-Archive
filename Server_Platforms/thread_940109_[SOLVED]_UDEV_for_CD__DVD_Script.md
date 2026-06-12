---
title: "[SOLVED] UDEV for CD / DVD Script"
date: 2008-10-06
forum: Server Platforms
---

### Post by thomascrabs on 2008-10-06
Not certain where best to post this so sorry if it could be in a better place.

I have a desktop PC running latest ubuntu that I am using as a media-server to my PS3. I have a script that I use to backup any CD's or DVD's I buy. X Windows is not running on it so every time I need to back something up I need to SSH to it :mad:. 

What I want is a way to run this specific script whenever a CD / DVD is inserted without user interaction :confused:. (The script detects if it is a CD or DVD)

Having done a lot of hunting around, using a UDEV script seems to be the best option. I have tried a couple of basic scripts but nothing seems to work. 

Does anyone have something that might help me or help with creating a script that will run when CD / DVD is inserted.

Please ask if you need more details!

---

### Post by thomascrabs on 2008-10-09
Well I have ended up sorting this one out anyway. After finding out about HAL I've managed to get a HAL script to kick off my script. Easy when you know how!

Big thanks to this site!

[http://wdawe.com/index.php/running-a-shell-script-when-a-dvd-is-ins?blog=1](http://wdawe.com/index.php/running-a-shell-script-when-a-dvd-is-ins?blog=1)

---

