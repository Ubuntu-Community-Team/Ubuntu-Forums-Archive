---
title: "Shared Desktops - An &quot;Open&quot; Working Environment"
date: 2008-05-30
forum: Ubuntu Brainstorm
---

### Post by Gripp on 2008-05-30
Firstly,
Yes, you can use things like VNC to take control of another users desktop - that is not my aim here.
and I'm not certain that this is the correct audience for such a suggestion - i think it may even have to be a mixture of Xorg, kernel and flavor. but here goes:

**The Bottom Line: (first)**
To be able to have multiple users on the same desktop simultaneously - multiple pointers, cursers, etc. all within a subnetwork of coarse (something like this over the web is years from possible...)

**The Why**
I work at a firm that does a lot of drafting and that sort. While the use of AutoCAD on linux is a hurdle in and of itself, I wont get into that here.. communication is key and hard to sustain when everyone is concentrating on their computer all day long.  Often times you dont get to catch mistakes that they have made until after everything is done and on paper in front of you.  

imagine if instead of getting up and jabbing my finger at another users screen while explaining something to them, or having to get them to close out of a file so that I can make some changes... or having to wait til the finish of hours of work to see that they didn't completely understand the thought process going into something...  I can just jump on their desktop and work right along side of them.... What if multiple people could do this?

Imagine that you have some big rush job, and a lot of custom details that need to be created and might have even been fully thought through by this point.  you could have two or three people working on the paper space/view of a project creating details side by side, and they would know what they have created matches with what the other user has done.

** The How (?)**
I am envisioning something like the Desktop Cube or Wall, but when you look Pull away from your desktop you see other people working on theirs!  Just like you might see a movie playing on your other desktop as it stands.  Their would be no need to know computer names, IPs or ask permission (after some initial setup of coarse)and if you snap to their screen your mouse and keyboard are active on their machine! i.e. you dont "take over" for them.  And they can do the same with your machine.  At the very least this would definitely cut down on the jerking around on the computer stuff :)  But hopefully it would make things like catching mistakes early, communicating and explaining ideas easier.  

To keep things clear, maybe the users initials could appear next to the pointer and/or cursor for each person. And for some amount of security maybe certain apps could be blacked out from others' view, at the admin's discretion, like email - i.e. any windows related to the email app would just appear as black boxes to other users. 

For that matter, wouldn't it be cool if you could move windows from one desktop to another, just like the normal one-user multiple desktop?!  Hmm, maybe that would be annoying... have some random window pop up on your screen suddenly.. almost rude in a way.  but still maybe a useful idea! what if i just want to take something back to my desktop right quick to work something out without the others.  Maybe?

there would also be the big elephant of threading programs like Autocad to transparently work with two different commands from two different users at the same time.  (rather than having to take turns inputting commands...) but i cant see that has impossible. and if someone like Autodesk saw the potential for a new market like this, i'm sure they would jump right on it. 

A very far out idea for sure! but I know I would find it extremely useful!  at the least it would save me from getting out of my desk so much to show people stuff... (and visa versa) 
and I would imagine that this would boost linux in the commercial sector dramatically given that most engineering and architectural firms would love something like this. 


**The end**
Just A Thought. Hopefully I'll see something like this in a "few" years :biggrin:

---

### Post by irrdev on 2008-05-31
Neat idea, but I don't think there would be enough demand to implement it. Also, this wouldn't be a Ubuntu feature, but more likely a GNOME or KDE feature. You might also be able to achieve this through a highly modified Remote Desktop Client. I doubt it would ever work though, as security would be severely breached. Still, it is an interesting idea. I could definitely see myself using this at university.

---

### Post by smartboyathome on 2008-05-31
This could possibly be done using a huge variant of MultiX, which allows multiple X cursors. I would think this would make things messier though, since large companies (which this is intended for?) would have a lot of people, and they would be working on each other's desktops.

Also, might want to look at a thin client, it does something similar to this.

---

### Post by Gripp on 2008-06-06
i'm thinking more like maybe small teams of people.

like a group of 4 or 5 working on the same project.
then maybe people can join their "group" as desired maybe..  maybe you would need permission to join the group, then not after that? (until you left the group of coarse)


yeah, it would be a massive project.  i'm not sure it would even be limited to just gnome or xorg or ubuntu...

kind of its own little animal

and, yeah, i know too much work for something that may not have as much application for the general public as it would for my specific situation... but i've had the thought a few times so i figured i might as well throw it out there!

---

### Post by Rufe0 on 2008-06-07
Sounds like it would be best to have a central huge server where all the actual computing takes place, then low power desktops which just basicaly get sent the desktop from the server.

---

### Post by d_eckert on 2008-06-10
Sounds a bit like how a multi player game works to me:
all the keyboard/mouse/etc input data from each client computer is sent to a server for processing and the changes are sent back out to all the clients which update their displays.

Handling multiple clients modifying the same data (eg two people editing a document in open office) at the same time would probably be the hardest part.

---

