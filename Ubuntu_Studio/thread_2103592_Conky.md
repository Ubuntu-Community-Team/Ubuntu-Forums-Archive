---
title: "Conky"
date: 2013-01-10
forum: Ubuntu Studio
---

### Post by Heavy Mars on 2013-01-10
Hi, im new in this world of Linux and Ubuntu Studio, i'll need  all your pacience and knowledge.
The issue i want to fix this time is the automatic start of Conky (with theme Lua). After read a lot of information i installed this effect to enhance the aesthetics of my desktop, but always in each time calling by the terminal. Could some one tell me what is properly action to do for the automatic start of Conky?

      MY OS IS UBUNTU STUDIO!, so, take that like a reference.

---

### Post by CrocoDuck on 2013-01-10
Hi. Just add conky to "Application Autostart". Go to "Settings Manger", choose the "Session" voice, then go to the "Application Autostart" tab. Add a new application, feed the prompt with the infos: you must put into the command option the command you are usually write into the terminal. In my case I put Conky as name, Conky as description and conky as Command. Some reference: [http://docs.xfce.org/xfce/xfce4-settings/start](http://docs.xfce.org/xfce/xfce4-settings/start) , [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq) .

---

### Post by ajgreeny on 2013-01-10
To make sure that conky does not start until the DE is up and running properly you may need to use the command ```
conky -p 10
```which pauses for 10 seconds after executing the command to start conky.  Use a different number for the pause if necessary.

---

### Post by Heavy Mars on 2013-01-10
> **CrocoDuck said:**
> Hi. Just add conky to "Application Autostart". Go to "Settings Manger", choose the "Session" voice, then go to the "Application Autostart" tab. Add a new application, feed the prompt with the infos: you must put into the command option the command you are usually write into the terminal. In my case I put Conky as name, Conky as description and conky as Command. Some reference: [http://docs.xfce.org/xfce/xfce4-settings/start](http://docs.xfce.org/xfce/xfce4-settings/start) , [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq) .

finally i solved the problem, thanks again folks!!!

---

### Post by Heavy Mars on 2013-01-10
[QUOTE=ajgreeny;12448917]To make sure that conky does not start until the DE is up and running properly you may need to use the command ```
conky -p 10
```which pauses for 10 seconds after executing the command to start conky.  Use a different number for the pause if necessary.[/QUOTE

&#65279;finally i solved the problem, thanks to both of you!!!!!!

---

