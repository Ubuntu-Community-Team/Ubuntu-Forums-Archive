---
title: "Two additional programs that need to come with Ubuntu"
date: 2008-04-07
forum: Ubuntu Brainstorm
---

### Post by kingleer on 2008-04-07
Greetings, I think it would be very convenient if Ubuntu came installed with: 

aptoncd - Ubuntu needs a backup tool and this could be part of the solution. 

aptoncd.sourceforge.net/ 

"APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection." 




and 



Gmountiso - this would let people mount .iso etc without needing to use the terminal. Remember joe6pack is intimidated by the terminal and anything that can be done with a click will make his life easier. 

[http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/](http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/)


Neither one of these programs is very large so I can't think of a reason not to include them. Ubuntu would still be able to fit on a cd if it came included with these programs. 



Also, a nice third program would be firestarter. Ubuntu is secure as is, but a good firewall would make some people feel more comfortable.

---

### Post by NightwishFan on 2008-04-07
I know firestarter and gmountiso are in the repos. I think the devs have a reason for not including them by default though.

---

### Post by bfakefree on 2008-04-07
the ability to move your stuff over without downloading from internet is a brilliant idea, every time Ubuntu crashes you have to sit for hours for downloads on the re-install

---

### Post by smartboyathome on 2008-04-07
The problem here is that, unless you have another Ubuntu install which will download the dependancies, you have to gather them yourself. This may be useful for some, but I don't know if it would be for everyone.

---

### Post by lexen on 2008-04-07
While both of those programs appeal to a relatively small audience, Gmountiso is something that will really make ubuntu a lot more usable.  aponcd on the other hand only helps after the OS breaks.  If you are trying to plan ahead to that extent, you should just download it from the repositories.

---

### Post by bruce89 on 2008-04-07
> **kingleer said:**
> Gmountiso - this would let people mount .iso etc without needing to use the terminal. Remember joe6pack is intimidated by the terminal and anything that can be done with a click will make his life easier. 

[http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/](http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/)

Useless in Hardy, all archive files can be mounted by an option in the right click menu.

---

### Post by rogerdean on 2008-04-25
aptoncd is key for those who install without net access. then they can get their system complete from a cd. but no use if you have to download aptoncd first! +1 from here

---

### Post by GuitarRocker2562 on 2008-04-25
> **bruce89 said:**
> Useless in Hardy, all archive files can be mounted by an option in the right click menu.

where? I just tried, not there.

---

### Post by caryb on 2008-04-25
That aptoncd is brilliant! thanks for the heads up! I have approx 60 Kubuntu machines to support at work & this will save ton's of bandwidth! I don't know if it should be installed by default as the target audience is small bet it should be in the repo's if the licensing permits:guitar:


Cary

---

### Post by smartboyathome on 2008-04-25
> **caryb said:**
> That aptoncd is brilliant! thanks for the heads up! I have approx 60 Kubuntu machines to support at work & this will save ton's of bandwidth! I don't know if it should be installed by default as the target audience is small bet it should be in the repo's if the licensing permits:guitar:


Cary

It already is in the repos. :)

---

### Post by bruce89 on 2008-04-25
> **GuitarRocker2562 said:**
> where? I just tried, not there.

Seems to have disappeared.

---

### Post by Xyem on 2008-04-29
> **caryb said:**
> That aptoncd is brilliant! thanks for the heads up! I have approx 60 Kubuntu machines to support at work & this will save ton's of bandwidth!

If you have a server available, why not just use the 'approx' apt cache/proxy? It is pretty easy to set up and requires no change to the client machines ( besides setting the apt clients to use the server as a HTTP proxy ) and only minor changes on the server. Works great on my home server :)

---

