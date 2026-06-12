---
title: "Home Automation"
date: 2009-06-07
forum: Server Platforms
---

### Post by fattymatty on 2009-06-07
I'm moving into a new place in July and was thinking of setting up a home system with my linux server so that i could have everything working together.

  I would like it to be able to do the following:

  - Support Wireless Cameras
  - Support Motion Detection
  - Support ability to record when motion detected and shut down recording when motion no longer detected.
  - Support Wall Panel Controls - ie some sort of touch screen devices i can mount in wall to control system
  - Support Media System so that i can move about the house and it will follow me from room to room
  - Support ability to setup lighting and draps
  - Support ability to configure on/off sequences ie when turn on stairwell light wait 1 minute then turn off light. 
  - Support Insteon
  - support UPNP so i can watch movies on my ps3
  - Support temperature panels

So was wondering if anyone had any ideas of what program would accomplish this or what combination of programs would accomplish this also what would hardware would be the cheapest so that i could have audio play ability in 3 or 4 rooms.

Ive looked at misterhome and seems to be okay but is it outdated and would linuxmce be able to do sequences and auto record when motion detected and which from room to room as you go.

---

### Post by Jekshadow on 2009-06-08
If you know how to code, Linux can literally do anything. Well, I doubt that it could break the laws of physics, bring Einstein back from the dead or have Bill Gates release Windows 7 under the GPL, but you get the idea. 

LinuxMCE supports all of the things you mentioned, some built in, some you might have to create custom scripts for, and others might require whole new drivers, but it can be done. I think most can be done by default.

---

### Post by rocketgeeezer on 2009-06-21
try this:

[http://linuxmce.com/](http://linuxmce.com/)


:popcorn:

---

### Post by mmlinx on 2009-11-11
i use motion for the motion detection part. with allot of coding of my own in bash and php.
I also use espeak in combination with bash and rtorrent. For my weekly downloads :)
Still looking for a good voice command option in Linux. 
Misterhome talks about an IBM product (don't remember the name). 
i noticed that misterhome uses festival for voice output.
Used that in the past but i like espeak more. 
Beter voices etc. and easy to use in my scripts 
Example:
echo "Hi, how can i help you today | espeak en+f2"
currently intergrating motion with joomla slick interface and a custom webinterface for my iphone.  
i'm also looking @ misterhome for the other part. (home automation).
Haven't tried mcelinux yet, but i will soon.
Hope that takes you one step forward.

---

