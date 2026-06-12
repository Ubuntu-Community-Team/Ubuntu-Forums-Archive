---
title: "paritioning for web-server"
date: 2008-11-15
forum: Server Platforms
---

### Post by ShirishAg75 on 2008-11-15
Hi all, 
  Does anybody know what an ideal partitioning scheme be for a small multi-site home web server and if anything I need to remember about the same.

---

### Post by Philio on 2008-11-15
The default really should be fine for this!
you might want to have a separate partition for your files in /home but not essential.

---

### Post by ShirishAg75 on 2008-11-16
The problem is what is the default?

For a desktop I usually do 

/ - for everything else

/boot - for a separate boot partition 

/home - for my stuff 

swap - 1.5 times the memory . 

Now for webserver I guess 

/var - for one can put the files there . Isn't /var/www/ supposed to be where one puts files for the webserver

/var/log :- Where all the logs 

So /var probably a separate partition and it should be big (I'm guessing)

The other things apart from apache would be ssh, ftp and dns which I would also need to configure right?

I know these are 2 different questions but wanna get a hang of what things are needed & what I need to do before-hand

---

