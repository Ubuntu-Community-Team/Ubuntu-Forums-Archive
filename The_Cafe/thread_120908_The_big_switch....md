---
title: "The big switch..."
date: 2006-01-23
forum: The Cafe
---

### Post by varunus on 2006-01-23
I've always been a big GNOME fan.  I've tried to use KDE multiple times, starting with the 2.0 series (where I actually did use it for a while), and then again with the 3.0 series.  Every 3.x version I've used has sent me back to GNOME with a bad taste in my mouth.  I just...didn't like it.  It felt so cluttered and clunky; configuring the interface to my liking took forever, as I had to dig down to the deepest recesses of the Control Center.  GNOME took very little time to configure and get working, and just worked for me.  For a long while, I was pure GNOME.

Then, after seeing poofyhairguy's Knome guide, when installing kwin, I saw that it would need a bunch of other KDE dependencies.  So I took the plunge.  I installed kubuntu-desktop, and logged out and in.  I went ahead and got KDE 3.5 as well.

And it blew me away.

Configuring the thing was still a pain; but much less so.  I was able to more easily navigate through the control center somehow, but a lot of difficulties still remained.  (I think this is KDE's thing they need to work on the most for 4.0.)  (A notice to anyone who tries out KDE:  to configure konqueror's single/double click behavior, its in the MOUSE control panel, not konqueror's. :( )However, once I got KDE set up (which took around an hour to get everything fine tuned, much longer than GNOME), using it was a breeze.  The eye candy, even without compositing, was very nice; the panel tooltips are great, menu's can be made translucent without XRender, and the interface just overall looks polished.  Amarok was great (though Rhythmbox's new DAAP support still makes it nice), Kopete has improved a lot since KDE 3.0, and I loved how integrated Konqueror felt for once.  The stupid sidebar, that usually plagues the application, was off in Kubuntu.  I loved how integrated it felt; PDFs opened in the browser window, as did movie files, with no need for mozplugger.  And finally, I noticed something; several of the bugs I had noticed in GNOME were *gone*.  Cedega did not complain anymore about fullscreen games; I always got CS: Source crashes on the GNOME side of things if I ran it fullscreen.  Compositing was much more stable and developed.  I even got Kat, a replacement for Beagle, working through the repositories.  And thankfully, any GTK apps I couldn't lose simply changed appearance to look like QT ones thanks to the GTK-QT engine!

I do miss the GNOME HIG in a lot of cases; Amarok has a lot of clunkiness to it, as does Konqueror (I haven't figured out how to set two homepages - one for my home folder, one for google, depending on what mode i'm running it in).

I think I'm going to have to stick with KDE, despite my longtime GNOME loyalties.  After you get it configured and don't have to touch the control center again, its great to use...and 3.5 is much faster than previous iterations.


Has anyone else gone through a desktop epiphany like this one?  I urge you, longtime GNOME users; take KDE for a test drive.  Set it up with two panels the way GNOME does, and it feels like home (and is a lot nicer IMHO). Make yourself use it for a week or two, and post your experiences with it.  And KDE users, do the same with GNOME.  Try it out, make yourself use it for a few weeks.  You might be surprised by the result.

---

### Post by nobodysbusiness on 2006-01-23
I used KDE with Mandrake when I started with Linux. When I switched to Ubuntu, I decided to give Gnome a try, and it worked very well for the year I used it. Recently, I read about how Linus preferred KDE, so I decided to give it a try again. Unfortunately, I didn't like it. There were some annoying little bugs in it that just bothered me. I switched back to Gnome after a few weeks. Don't get me wrong--the KDE apps are WAY better--but the Gnome desktop itself is superior, in my opinion. Much more polished. I don't know why some people always try to run only Gnome apps when they're in the Gnome desktop. K3B is the best CD burner, and it works fine in Gnome, so I use it. KDE apps in the Gnome desktop is the way to go.

---

### Post by super on 2006-01-23
i'm actually gonna switch to back to kde for a little while also.

i also used it awhile back (about 2 years) when i was running gentoo and mandrake. in terms of features, it was great. but i just thought is looked too cluttered and plasticky.

but lately i've been browsing some [gorgeous kde screenshots]("http://kde-look.org/usermanager/search.php?username=bonafide") (i really like befree) and it seems to look a lot better. plus it has amarok!

i'm gonna take it for a twirl, and see how i like it. :cool:

---

### Post by poofyhairguy on 2006-01-23
[QUOTE=varunus]
Then, after seeing poofyhairguy's Knome guide, when installing kwin, I saw that it would need a bunch of other KDE dependencies.  So I took the plunge.  I installed kubuntu-desktop, and logged out and in.  I went ahead and got KDE 3.5 as well.

And it blew me away.
[/QUOTE]

I'm glad my guide helped someone with something. 

Personally despite its many options and features I can never get KDE to a point I like it more than Gnome. I like kwin more and some KDE apps more (K3B) so I use those in Gnome. Each to their own.

By the way, you can run Gnome applications in KDE. If you want them to look nice also run this program with this command:

```
gnome-settings-daemon
```

---

### Post by tufkakf on 2006-01-24
I can understand how you feel. I find myself using both Gnome and KDE because I actually like both. They both have their weaknesses and strengths.

@nobodysbusiness:
I of course don't know which problems you had, but from my experience a lot or the problems are not kde, but kubuntu specific (for example, running things as root not working). However, using the half-official kde3.5 from kubuntu fixes a lot of these problems.

@poofyhairguy:
Running gnome-settings-daemon always caused font troubles for me, as Gnome and KDE use different dpi settings. That is, in Gnome you can adjust it them on a per user basis, while KDE inherits them from the X settings. What fixed this problem for me was telling KDM to use the same dpi settings as the ones Gnome uses, in case anybody else is experiencing this problem.

Edit: And one other thing. If you are running a lot of kde apps in Gnome and are bother by how slow they start initially, run kdeinit & on you session startup. This will make all you kde apps start a lot faster.

---

### Post by PenguinZdravko on 2006-01-24
I've used KDE for about 3 weeks in november 2005. I like very much the KDE apps (I'm using amaroK in GNOME), but I like GTK. This is why I use some KDE apps, but I use also GNOME.

---

### Post by briancurtin on 2006-01-24
i started on KDE in SuSE a few days after windows took a crap on my computer. i just went straight into it, no dual booting (well i technically did for a week, but never logged into windows). i really liked it and used it for about 6 months, but liked to change it up and was also having some problems (my fault) and im now using WindowMaker. the reason i use it is kind of geeky, but its fun and i like it a lot. i might stick with it for a while.

---

### Post by Vlammetje on 2006-01-24
I started with GNOME in Oct 2005 and for the sake of trying things out switched to KDE about 1.5 months later. Tried it for a week and a half and decided I really wasn't comfortable with it. Back to GNOME, haven't looked back since. I much prefer the GNOME desktop, with some KDE apps added to it :)

---

### Post by Ultimo Aliento on 2006-01-24
I started using gnome like 8 months ago, 4 months ago, i hear that KDE have more eyecandy, i installed KDE in one of my sessions ... and i just cant make it work for me, i like many of the features, but for some reason, the simple way of gnome to do everything is more suited for me, i really like Amarok, but amarok works with my gnome so i dont find any good reason to have KDE installed.

---

### Post by AndyCooll on 2006-01-24
Like a number of you on these posts I too for some reason or other prefer Gnome.

I started out using Gnome (Fedora followed by Ubuntu) and I just can't seem to settle with KDE. I do run quite a few KDE apps however (Amarok, Apollon, K3b etc) and indeed often find the KDE apps better.

That's why I like Linux so much, choice. And not only that but even though Gnome and KDE (and Windowmaker, XFCE etc) could be considered  competitiors in many ways they all still ensure that their apps work in differnet windows environments.

I reckon that in the case of most of us our choice will end up a combination of both, i.e Gnome with KDE apps or KDE with Gnome apps!

:cool:

---

### Post by greenway on 2006-01-24
My Linux experience is a composition of several desktops such as KDE, Gnome and Fluxbox. Never really preferred one over the other but maybe that's just me liking to turn things around every once in a while! Anyway, ain't it just great to have a choice between desktop servers? Whenever one of them adds some new features... time to toy around again!

---

### Post by varunus on 2006-01-24
I agree with most of the people's GNOME comments here; I had to tinker with KDE until I got it to a usable point.  (I made a second panel, made it look like GNOME, set Konqueror to double-click, got the GTK-QT engine working so I could still use Firefox, tinkered with the window manager until I liked it, etc...)  But once I got it to a usable point, and I don't have to look at the control center, I really liked it.

If they can work on their configuration system to make it easier (somehow I managed to get a working GNOME-like desktop...) and borrow some of the simplicity, then KDE is going to become the major player, IMO.

---

### Post by el3ktro on 2006-01-30
It was just the other way around for me. I've been an exclusive KDE user for a few years, but it happened that I tried Dapper and I was so impressed about Gnome's simplicity & easiness that I fell in love with it and install Ubuntu right away over my previous Kubuntu. I miss a few of KDEs features like Konqueror's shortcuts (wp, en2de etc.) but thats about it. Gnome is so much easier for me, I have the feeling that I get my work done much quicker because the GUI doesn't get in my way so much. KDE's toolbars & menu madness always annoyed me a little.

But you have my full ack: Everybody should be open to the different desktops. I _never_ tried Gnome because I always told myself I didn't like it, but then I just did it one day and thought oh my gosh why didn't I do this earlier.

Tom

---

