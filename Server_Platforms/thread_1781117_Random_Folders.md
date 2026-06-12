---
title: "Random Folders?"
date: 2011-06-13
forum: Server Platforms
---

### Post by mortified_pengiun on 2011-06-13
I have a web server set up with apache2 and ubuntu server.  I'm also using samba to map the network drive to my Windows machine.  

My main directory on the server is /media, and I'm getting a random folder in there called PATAKH~Y.  However, it's only on my Windows machine.  I SSHed into the sever, and that directory is not listed.  In Windows, I deleted everything from it, but when I go to delete the folder itself, it says directory not empty.  Nothing is inside this folder, and a dir command shows nothing, however the folder is showing as over 45gb!

Anyone know what this is?

---

### Post by BkkBonanza on 2011-06-13
Make sure you show hidden files when you look at it in Windows. If using Explorer then you need to set the View options for the folder. My guess, offhand, is that you have hidden files in there.

That filename is a "compact" 8 letter version of a longer filename (maybe with spaces) that shows up when when a program can't handle the full filename (older programs or poorly supported/deficient ones). Usually in Explorer it will show as full long name and at the command prompt it will as well, so I'm assuming you are using some tool that can't show full names when it shows the shortened one. You'll need to figure out which folder/file is the matching full-name one for that abbreviated one.

---

