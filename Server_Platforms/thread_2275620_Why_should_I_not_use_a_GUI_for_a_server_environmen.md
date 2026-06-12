---
title: "Why should I not use a GUI for a server environment?"
date: 2015-04-27
forum: Server Platforms
---

### Post by Aphexlog on 2015-04-27
I never use a GUI on any of my servers - mostly due to hardware restraints
however, I would like to really know why I should not use a GUI on a Linux server
every time I see this topic in forums, people always say "NEVER use a GUI with a server". they never say why and in fact, they usually do not speak about the topic as though they actually even know why (kind of makes me think that they just say that because "that's what they were told")
So... I would like to know. Why should I **not** use a GUI of a Linux server?

Thank you in advance,

---

### Post by QIII on 2015-04-27
Hello!

A couple of quick reasons:

You typically want your server using the fewest resources so it can have them available for what servers do best.

You want to run as few services as you possibly can to increase security by minimizing the attack surface.

---

### Post by Frogs Hair on 2015-04-27
See the documentation . [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by slickymaster on 2015-04-27
*Moved to the ***Server Platforms*** sub-forum.*

Maybe because a traditional graphical interface adds very little to a server as almost everything you do is from the command line anyways (editing files, starting stopping services, installing services). If a need for a graphical interface arises, there are web based solutions such as Webmin for example.

---

### Post by wyliecoyoteuk on 2015-04-27
An Xserver is a network service, (Xwindows can be forwarded over the network for example) which if not required, is an additional opportunity for an attacker.
Graphical interfaces introduce additional complexity which means additional vulnerability.
Plus why use up resources on a graphical interface that is not used?

---

### Post by ofnuts on 2015-04-27
There is a strong tradition in Unix circles to think that everything  that was invented to make life easier since the 1980s is totally  superfluous. This said, if there are no good reasons, there are some decent excuses:


[LIST]
[*]The day you use a GUI, your managers think they can replace you with Jane/Joe from Accounting who knows how to use Windows (only half-joking here).
[*]To provide GUI support you have to add a lot of software, and the disk footprint of the system increases very significantly (pretty lame excuse these days)
[*]You are more likely to botch your whole /etc tree due to a mouse mishap with a GUI than by typing "rm -rf *" at the wrong place.
[*]The way X11 works, you have to open ports on your own computer to let servers connect to it. This also opens it to abuse/pranks by your colleagues :)
[/LIST]

You can of course completely sidestep the issue. Most of your GUI usage can happen on your computer, transparently accessing the files on the server. This is how I work. KDE to the rescue. File explorer, editor, file/directory comparison, disk usage all done pretty much transparently with the added benefit that you can manage several servers in the same window. Comparing the configurations of two servers by just drag'n'drop in Kdiff3 is how I make new converts.

---

