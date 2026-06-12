---
title: "Xampp will not start on boot"
date: 2010-09-29
forum: Server Platforms
---

### Post by jawsykilla on 2010-09-29
Okay, I have recently set up my web server using the LAMPP package for Ubuntu. Now I'm running Ubuntu Server 10 so my machine boots into the console and not gdm. Also I have my machine autologin as root so I can simply turn my server on and not mess around with logins. Now I created a simple shellscript for starting lampp and then I put it into etc/init.d/, chmod -x file.sh     to give it executable permissions, then I update-rc.d file.sh defaults    but nothing happens on startup. It simple takes me to the console and nothing more happens. I have to manually start lampp on every bootup. Any ideas?

Cheers,
Jordan

---

### Post by jawsykilla on 2010-09-29
Okay, I have solved my own problem somehow. The way to do it is

1) Navigate to /etc/init.d  eg    'cd /etc/init.d/'
2) Create a new file with nano eg 'nano'
3) Put the following into the file
#!/bin/sh
/opt/lampp/lampp start

4) Give execution permission to the file eg 'chmod +x lampp'
5) Check this by typing 'ls -l lampp'   , the filename should be green if it worked
6) now use the following command to add it to startup runlevels 'update-rc.d -f lampp defaults'

That is what I did and it worked. You could always create a file to stop XAMPP on shutdown. Use this same method above but in the file put 'stop' in replace of 'start'. Then use sysv-rc-conf to make it only run in levels 0 & 6.

Good luck.
Cheers,
Jordan

---

