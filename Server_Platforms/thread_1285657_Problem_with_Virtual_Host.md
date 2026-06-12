---
title: "Problem with Virtual Host"
date: 2009-10-08
forum: Server Platforms
---

### Post by btaylor101 on 2009-10-08
I have successfully installed jinzora and when I navigate to the localhost/jinzora2, everything works fine. When I attempt to place a virtual host directing it to jukebox.localhost, I can log in, but don't get all of the graphics and songs will not play. I thought it was a permissions issue so I set the home directory to 777. Still no joy. Any thoughts on this would be greatly appreciated.

---

### Post by btaylor101 on 2009-10-08
Turns out the problem is with some relative links in the Jinzora code. It is calling certain files from a directory of /var/www/jinzora2/jinzora2/... instead of just looking in the jinzora2 folder. Not an apache or Ubuntu thing.

---

