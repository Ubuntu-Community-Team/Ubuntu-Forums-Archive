---
title: "Ubuntu Vs Ubuntu Server edition"
date: 2011-01-13
forum: Server Platforms
---

### Post by 0000_soldier on 2011-01-13
Hey peeps,

I did a search on forums, but i would really like to know the difference between ubuntu desktop edition and Ubuntu server edition. All i know is that the server edition has no GUI, other than that what are the main differences?

Eventually I would like to run a server, however i am using LAMP configuration in a VM for development with tomcat and mod_jk. eg will consequences exist in migrating to Ubuntu server edition?

:confused:
Thanx

---

### Post by matt_symes on 2011-01-13
Hi

They have different kernel optimised for different tasks such as scheduling.

As you have stated the server has no GUI as that will waste resources, but one can be installed if you like.

They also come with different services and packages installed as default.

But they are essentially the same and you can run the desktop edition as a server if you so wished (at the expense of performance and other things).

Kind regards

---

### Post by Johnsie on 2011-01-14
The installer also has a set of option to choose which server-type applciations you want to run. So it's convenient to set up a lampp out of the box. In my experience server and desktop are as good as each other, but my server doesn't have heavy loads.

---

### Post by James78 on 2011-01-14
And to sum up the last 2 posts; the server edition is optimized for servers, where the desktop edition is for desktops. They can be interchangeable, although generally it's not recommended to run a server on your desktop machine (UNLESS you're just using it for testing your web applications and whatnot, then it's a development server), and it's not recommended to use a GUI on the server (as said earlier, this is a big waste of resources, and isn't needed, which is why server editions do not come with a GUI, but you can use webmin and virtualmin if you need help configuring things with a web GUI)

---

