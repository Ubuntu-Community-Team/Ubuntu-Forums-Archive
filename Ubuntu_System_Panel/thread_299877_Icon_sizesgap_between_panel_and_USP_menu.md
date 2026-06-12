---
title: "Icon sizes/gap between panel and USP menu"
date: 2006-11-14
forum: Ubuntu System Panel
---

### Post by Henry Rayker on 2006-11-14
Hello!

I'm using a laptop and, as such, screen real estate is kind of short. Basically, what I would like to be able to do is get all of the icons to be pretty small. I'm thinking about 16x16, I believe. I got the Places icons to be that small (it was actually not related to this, I believe, but a setting change I made in GNOME). The Applications are a tad big, and the system area, they are WAY too large. Isn't there some way to have all of the icons the same size, and follow a set of rules?

Also, my panel is smaller than the default, but USP seems to believe otherwise. When I open the USP panel, I have a pretty large gap between the edge of my panel and the USP menu. Is there a way to keep this in line with my panel?

---

### Post by Henry Rayker on 2006-11-15
no ideas?

---

### Post by Malac on 2006-11-16
Download USPconfig from :
[http://www.ubuntuforums.org/showthread.php?t=272372](http://www.ubuntuforums.org/showthread.php?t=272372)

or

Open gconf-editor (Applications->System Tools->Configuration Editor)
and navigate to
/apps/usp/apps_icon_size and change it to 1
/apps/usp/place_icon_size and change it to 1
Any others will be in the /apps/usp/plugins/<name of plugin> if they have the option, not all do at the moment.
I don't think Settings/Computer Buttons have the option as they display info as well.
However, USPcomputer also available from the previous link, let's you hide any of the buttons you don't need.

Position problem 
/apps/usp/panel_size try changing it to 1.
Hope this helps.

---

### Post by M7S on 2006-11-17
Changing /apps/usp/panel_size it to 1 leaves me with a gap. -3 does the job though. Odd that you can use negative numbers while zero doesn't work.

---

### Post by Henry Rayker on 2006-11-17
Changing to 1 worked for me. I guess it just depends on how much smaller your panels are made?

I'm going to work at the USPcomputer plugin, I guess, to try to get the icons  smaller. We'll see how this goes.

---

### Post by Tiede on 2006-11-23
Any solutions for the gap problem? I am also having this issue, and my mouse is set on focus. Which mean everytime I open USP, if I don't pay attention, when I go to actually browse the menu, it closes because the underlying window got back in focus while the cursor was in the gap...
Any solutions to this little annoyance?

---

### Post by M7S on 2006-11-24
As said above: in gconf-editor change /apps/usp/panel_size to 1. If that still leaves a gap (as it did for me) try -3. 

IT would be great if USP wouldn't autoclose as soon as you leave the window when you use mouse set on focus. Instead it could close when you click somewhere outside USP.

---

### Post by chanders on 2006-11-24
This menu type problem is one that I would like the any developer out there to take a look at. I still cant find out how to achieve this in Python. It seems that when USP is set to type 'dock' it does not propogate events. So this means that USP had to be set to type 'menu' which brings these problems...

Hopefully someone will help out with this before USP2 hits..

---

