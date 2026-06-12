---
title: "SimpleKDE is it realy a light weight."
date: 2006-05-14
forum: The Cafe
---

### Post by Omnios on 2006-05-14
I found this on the web looking for Linux windows and it sounds real interesting. First off some links.
[http://www.simplekde.org/node/8]("http://www.simplekde.org/node/8")

[http://www.eweek.com/article2/0,1759,1939259,00.asp?kc=EWRSS03129TX1K0000616]("http://www.eweek.com/article2/0,1759,1939259,00.asp?kc=EWRSS03129TX1K0000616")

```
What is SimpleKDE?

SimpleKDE is a GNU/GPL licensed, lightweight desktop environment for UNIX and UNIX based operating systems like Linux, FreeBSD, and OpenSolaris. Shortly it provides a graphical user interface on top of UNIX shells. SimpleKDE is not written from scratch; in fact, it is a fork of well known, powerful desktop environment KDE. SimpleKDE, inherits the powerful features of its ancestor, but provides a more usable and faster environment. The project is currently maintained by Turkix Foundation; all other KDE developers , fans are welcome to join the development. SimpleKDE is in no way a competitor to KDE, but an unofficial, complementary sub-project, that shares its codebase with the community, according to GNU/GPL.
```
 Anyways I can not find any hard spects on system requirements, ram requirements or how it runs on older systems. Im kind of hoping it will run on like 128 megs or so and have a lower processor load, I have run KDE and Gnome on a p2-350 with 256megs ram and gnome was suprisingly runable. Does anyone have some information on SimpleKDE as it might be just what is needed for a win98, winme replacement without having to stock up on expencive ram.

 I got an inkling that Mark would realy like this if it can meet lower system spec requirements.

---

### Post by DarthMandeep on 2006-05-14
Why not just use IceWM or JWM? You can still run KDE and Gnome programs.

---

### Post by Omnios on 2006-05-14
Yet another link, this ones talkes on how they think SimpleKDE will not become mainstream unless a major distro takes it up and how it is more windows like etc.
[http://basu715.weblogs.us/archives/134]("http://basu715.weblogs.us/archives/134")

  Anyways my main thing is about having a desktop aimed at windows 98/ME erra computers with about 128megs ram, also mostly for window to Linux converts and though Xubuntu and other light weights might be nice, manyu of these converts just cant handle most of the lgiht weights. Configing them etc. When I fist started just over a year ago I could not even find an article on how to config ice, though Xubuntu is pretty good now. Basicly it boils down to having a watered down lightwieght " KDE "to run on slightly older machines with 128 or so megs ram. not legacy gear. That brings me to another question im still searching for the system requirements for SimpleKDE as I can not seem to find them yet.

---

### Post by Jucato on 2006-05-14
AFAIK there are no system requirements yet because there has been no release yet, alpha or beta, judging by the lack of a link on their website.

SimpleKDE is a fork of KDE. But unlike Xfce, SimpleKDE is really just based on KDE (while Xfce is actually based on GTK+, not GNOME). But it's actually doing more than just basing on and customizing KDE for faster performance, it's actually changing some of the libraries that are installed. Here's a not-so-bright opinion on SimpleKDE: [http://www.desktoplinux.com/articles/AT3601556298.html](http://www.desktoplinux.com/articles/AT3601556298.html)

But anyway, I still wish them the best on their project, as it seems to try to answer one of KDE's "problems" (I say "problems", because it seems that some people's experience of KDE is not as bloated as some say).

As for a solution to your problem: I'm not really sure if changing window managers (from KWin to IceWM) would solve the problem because the "bloated" libraries would still be there. Have you tried Xfce? It's the lightest DE out there. If you still prefer KDE, there are options to trim down some visual effects so as to minimize resource usage. Run kpersonalizer and select the options that you want. Also, KDE4, which should arrive (as beta) late this year, promises a lot of trimming down due to the switch to Qt4. This might be something to look forward to.

EDIT: As for making KDE look more Windows-like, there are many ways to do that, without having to switch to SimpleKDE. For a Start menu similar to XP, there's a KDE app called Kbfx which can be themed to make your panel look like anything, or like Windows XP.

---

### Post by ComplexNumber on 2006-05-14
> Here's a not-so-bright opinion on SimpleKDE: i think its quite the opposite. they've got it spot on. its yet another fork and yet another potentially troublesome areas for everyone(including vendors etc) except hardcore kde users who have a pressing need to use kde but without all the krap. there's plenty of choice on linux as it is. perhaps too much for the good of linux in the long run. here is the appropriate summary of SimpleKDE:
[FONT=Arial,Helvetica][SIZE=3]> So, SimpleKDE developers, may I ask that you reconsider "forking" the code and work to get your improvements into the main KDE libraries? If that doesn't work for you, at least please contact the good people at the Desktop Linux Working Group and work with them to make sure that your project can work and play well with the Portland Project initiative.

Seriously, you'll be glad you did, and so will the rest of the Linux desktop community.[/SIZE][/FONT]

---

### Post by briancurtin on 2006-05-14
[QUOTE=Omnios]Yet another link, this ones talkes on how they think SimpleKDE will not become mainstream unless a major distro takes it up and how it is more windows like etc.
[http://basu715.weblogs.us/archives/134]("http://basu715.weblogs.us/archives/134")[/QUOTE]
making things more "windows like" is the worst possible thing ever.

---

### Post by ComplexNumber on 2006-05-14
[quote=briancurtin]making things more "windows like" is the worst possible thing ever.[/quote] agreed. KDE is windows-like enough as it is. its not as if windows is the epitome of userbility, so i don't see why they should keep on plunging head first in that direction. they would be better off using some imagination instead.
i really hope they just give up on SimpleKDE because its going to end up doing more harm to linux than good.

---

### Post by Omnios on 2006-05-14
[QUOTE=briancurtin]making things more "windows like" is the worst possible thing ever.[/QUOTE]

 I didnt say being Windows like is a good thing, then again as stated it is a link where someone was stating there personal opinion that it was more windows like. Then again I wont commet on that till I try it as I found many users perspective on windows like has nothing to do with windows but rather on what they think Linux should be.

---

### Post by Omnios on 2006-05-14
There are many great light weights out there but most are difficult to config and may not meet the specific likes and or might just be disliked by the potential user. The great thing about Linux is the vast amount of personal choices out there.

  I am not thinking of myself pertaining to SimpleKDE rather thinking of offering another choice to new novice Linux users. As I read more about it it is early in development and that development seems to be very slow. Now would it actually fill a nitch I do not know as I have not tryed it as of yet. Now this dependency thing I'm not sure about that but if it actually does cause problems then that potentially could kill it right there. No use having a desktop where you can not properly install stuff on it. 

 Anyways SimpleKDE would only be viable if it can run well on 128megs ram based on that I have run Gnome rather well on a P2-350 with 256megs ram and ran about the same speed that win98 ran on it. The only niche I see it filling is as a possible replacement for someone with 128megs ram which will not run Gnome well from what I have reed and possibly a win 98/ME convert. 

 Lastly could it fill a nitch for a light weight desktop then again there are other  lighter desktops but based on KDE's popularity this may go a long way then again as mentioned in the posts here may have serious problems that even being a fork of the popular KDE will not solve. 

 Now as the title states is it realy a lightweight? Or even a viable one

---

### Post by ComplexNumber on 2006-05-14
for the lightweight department, there are plenty of window managers that can do the job far better than SimpleKDE ever could such as blackbox, fluxbox,  or even xfce.
this SimpleKDE effort is more of a desktop political thing rather than serving any useful or practical purpose.

---

### Post by nalmeth on 2006-05-14
I would try it for sure. I've found KDE to be bloated in area's, though it get's more flak than it deserves. I can comfortably use kde with 128 megs of ram.

I don't think anyone will be able to answer your question though, if it is not yet released at all??

I hope to hear some news about possible release soon

---

### Post by claydoh on 2006-05-14
[Well there are files from last july on sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=138671&package_id=152098&release_id=341700")  :D based on kde 3.4.1

---

### Post by Ptero-4 on 2006-07-05
[QUOTE=briancurtin]making things more "windows like" is the worst possible thing ever.[/QUOTE]

I agree with you there. And making it FULLY Mac like would be a good choice.

[QUOTE=ComplexNumber]agreed. KDE is windows-like enough as it is. its not as if windows is the epitome of userbility, so i don't see why they should keep on plunging head first in that direction. they would be better off using some imagination instead.
i really hope they just give up on SimpleKDE because its going to end up doing more harm to linux than good.[/QUOTE]

I think they should stop trying to make every DE they touch a Windoze-clone. But I don't hold my breath for that, and you shouldn't either. As there are very big political/commercial interests in making linux DE's Windoze-lookalikes, and the companies involved in this are very big ones (M$, Disney, RIAA/MPAA, the U$ gov, etc...).

---

