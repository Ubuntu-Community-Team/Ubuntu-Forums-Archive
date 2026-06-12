---
title: "Stopping Gnome when installed from gnome-core"
date: 2010-07-19
forum: Server Platforms
---

### Post by HittingSmoke on 2010-07-19
I installed Gnome on my server using the gnome-core and xinit packages so I could use MySQL Workbench.

I start up Gnome when I need it via *startx*.

*/etc/init.d/gdm* doesn't exist so I can't use *gdm start* or *gdm stop*

How can I stop Gnome and the X server in this situation?

---

### Post by richardjh on 2010-07-19
The init scripts were replaced with upstart. 

I wrote a blog entry about [preventing services starting automatically]("http://richardjhblog.wordpress.com/2010/06/07/preventing-services-starting-automatically-in-upstart/") which gets a lot of views, showing that this issue is causing a lot of people problems.

Please [read the post]("http://richardjhblog.wordpress.com/2010/06/07/preventing-services-starting-automatically-in-upstart/") if you want a full reply, but in short you need to edit /etc/init/gdm.conf and on line 9 where it says 

```
start on ( ... 
```You need to replace that with 

```
start on [!0123456]
```You can then start gnome using 

```
startx
```only when required.

---

