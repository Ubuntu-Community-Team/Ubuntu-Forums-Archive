---
title: "separation of workspaces"
date: 2008-07-25
forum: Ubuntu Brainstorm
---

### Post by boblemur on 2008-07-25
i dont know if anyone agrees but i would like to be able to treat my different workspace more separately than is currently available.

for example, pidgin even if i have my contact list open and all my windows open on a different desktop new one will still always open on the current desktop...

would be cool if you would have different wallpapers and desktop items for each desktop so you could keep a workspace dedicated for one thing (ie work on this one desktop, music and videos on another)... 

also if you would be able to open an application in full screen on a new temp workspace, like for example a virtualbox could open itself up on a new workspace....

if this is all possible already somehow... id love to know how :)

---

### Post by smartboyathome on 2008-07-25
This isn't possible at all right now. I have seen one solution before, but it was for KDE and it involved killing Konqueror (KDE's desktop), changing the desktop folder's symlink, and then starting Konqueror again when you switch. Imagine that with Nautilus, and it is very messy. Imagine going even farther with that to settings and such like you talk about now, and you might as well just get a supercomputer.

---

### Post by zekopeko on 2008-07-25
you could try compiz's window placement/matching plugins. i believe that you can make apps open on specific workspace.

---

### Post by smartboyathome on 2008-07-25
> **zekopeko said:**
> you could try compiz's window placement/matching plugins. i believe that you can make apps open on specific workspace.

Not what they want. They want separate settings and such on different workspaces.

---

### Post by boblemur on 2008-07-26
almost like having separate x sessions on each desktop (obviously without being so completely segregated of course...)

:) a super computer would be nice.... have you got a spare one i could have :p

yeh i just think that if you are going to have separate workspaces, you should be able to allocated work to different spaces (ironically) 

how it just seems like a space to send applications when one task bar gets to cluttered...

in saying this i really like them... however...

alt + tab (or switching between windows) and changing workspaces currently do exactly the same thing... they are just called different thinks (basically) almost like just named differently.

for them to really be a different feature rather than just a fancy task tray grouping scheme they need to be able to be separated more and also for them to be able to be treated as different desktops that interact rather than just coppies... in my opinion... 

also, dual moniters should be able to have one workspace on each screen, maybe there is a reason its not possible... but it just seems logical that you should be able to let the second monitor take a different workspace rarther than either copy the screen or extend one workspace

---

### Post by smartboyathome on 2008-07-26
Actually, I think what you want can be done if you want separate X sessions. Try GTK Xephyr located [here]("http://ubuntuforums.org/showthread.php?t=620003"). Try starting a basic Window Manager before you do this, and then start (I am assuming gnome) on each workspace using gnome-session in the command box. The only problem is that it will take up tons of memory and CPU, which can get troubling. :(

---

### Post by boblemur on 2008-07-26
yeh it is a problem because my computers starting to get along :p its not got a huge ammount of memory and i dont want it to start pushing me into swap space, i was thinking something simmular, if i wanted to change this... ie programm this into the window manager:

where would i start?
what packages would i need to edit?
how do i get the code for gnome? 
and things like that and then how do i rebuild it into the os?

i know its a rarther huge task, but still how would one go about doing it?

---

### Post by smartboyathome on 2008-07-27
> **boblemur said:**
> yeh it is a problem because my computers starting to get along :p its not got a huge ammount of memory and i dont want it to start pushing me into swap space, i was thinking something simmular, if i wanted to change this... ie programm this into the window manager:

where would i start?
what packages would i need to edit?
how do i get the code for gnome? 
and things like that and then how do i rebuild it into the os?

i know its a rarther huge task, but still how would one go about doing it?

You would have to look at modifying GNOME itself. Changing how each piece of GNOME behaves when you switch workspaces.

---

### Post by boblemur on 2008-07-27
and where would i get gnomes code from??

and how would i rebuild it again? and reinstall it??

---

### Post by smartboyathome on 2008-07-27
You would probably want to get it from GNOME's SVN site. Talk to someone else though. Also, I would recommend you go with a source-based distro if you are serious about this, since that would teach you how to build it and such. I recommend slackware. :)

---

### Post by boblemur on 2008-07-27
what do you mean source based???

---

### Post by smartboyathome on 2008-07-27
I mean it compiles the programs for you. Slackware, for example, doesn't handle dependancies, it just compiles stuff for you. You have to compile extra programs to do that. It DOES, however, handle installing and thus allows you to be able to modify the source, compile and install, and manage the install easier than on Ubuntu.

I would suggest you not take this on if you aren't up to having to learn a lot to do this. It is going to be a monumental task, which will take you a while to do. It is not one which you can get done in a week, more like a month or more probably with all you have to modify.

---

### Post by galileon on 2008-07-28
> 
 A window-matching utility, inspired by Sawfish's "Matched Windows" option and the lack of the functionality in Metacity. Metacity lacking window matching is not a bad thing &#8212; Metacity is a lean window manager, and window matching does not have to be a window manager task.

Devil's Pie can be configured to detect windows as they are created, and match the window to a set of rules. If the window matches the rules, it can perform a series of actions on that window. For example, I can make all windows created by X-Chat appear on all workspaces, and the main Gkrellm1 window does not appear in the pager or task list. 

[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

---

### Post by boblemur on 2008-07-29
however the problem with this is... i then have to define the rules for each program.... i was more looking for a way to govern all programs at once... for example...

if i have one program... any of its children must spawn on the desktop the parent is on...

i guess they are very little things but they would remove a huge ammount of annoyance

---

### Post by aeg1s on 2008-11-16
> **zekopeko said:**
> you could try compiz's window placement/matching plugins. i believe that you can make apps open on specific workspace.
Thanks zekopeko!  That suggestion helped me...

---

