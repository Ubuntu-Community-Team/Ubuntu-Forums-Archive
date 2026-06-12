---
title: "remote acess gui tool"
date: 2007-07-04
forum: Server Platforms
---

### Post by kevinlang21 on 2007-07-04
what is, in your opinion, the best gui remote access tool for linux?

---

### Post by vmikalinis on 2007-07-06
To do what?  Remote desktop?  There are many to access different packages.  What are you trying to work with?

---

### Post by kevinlang21 on 2007-07-07
im trying to ssh into a server. i use putty for windows, but im trying to get away from windows. im thinking of using virtualbox and running putty that way, but i'm not sure if i have a windows cd. I don't think putty works for linux, because they didn't port pageant to linux? is there a replacement for that?

---

### Post by bmathis on 2007-07-07
I use putty to ssh into my linux server and I also use Webmin when its needed.

putty is in the repositories... do a apt-cache search putty and you should see 3 packages available.

---

### Post by MikeDX on 2007-07-07
open a terminal and type

[PHP]
ssh [hostname/ip]
[/PHP]

and voila. I assume you might want to use putty to manage your hosts though, but for day to day needs, I just use the ssh command line tool

---

### Post by kevinlang21 on 2007-07-07
i have to use a key, which i generated with putty gen. is there an equivalent in linux though?

---

