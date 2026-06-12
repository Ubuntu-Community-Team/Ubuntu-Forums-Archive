---
title: "Flash crashing browsers: solved (for me)"
date: 2009-03-21
forum: The Cafe
---

### Post by hisotaso on 2009-03-21
Well recently, like in the past few days, my browsers (opera and firefox) have been crashing on flash sites. I was racking my brain trying to remember recent updates and any changes i had made that might be relevant. 

I eventually came across a bug report that said samba wins name resolution was causing crashes in browsers with flash. I dont have the link handy, but im sure you can find it, anyway i remembered that i was trying to mount a new drive using wins in samba the other day, and a part of that was adding "wins" to a line in nsswitch.conf in the /etc file. I removed "wins" from that line and have not had a crash since.

I had never had an issue with my browsers crashing before this week, and since it started it has been consistent, once i removed that line, problem solved. Also its just as easy to mount drives in fstab using the ip as it is using the name, so i wasnt using wins anyway. thought this may help someone.

---

