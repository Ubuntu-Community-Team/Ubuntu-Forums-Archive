---
title: "Improving Ubuntu"
date: 2006-01-25
forum: The Cafe
---

### Post by tufkakf on 2006-01-25
Reading through these forums can be a very frustrating experience.

One gets the impression that on the one hand there are a lot of posters who don't have a lot of experience with Linux, which doesn't and probably shouldn't stop them from making posts where they tell us what Linux needs. The funny thing is thoughthat in a lot of cases they mention things that are not Linux specific, but Ubuntu specific, that is, they mention functionality that is provided by most other distros targeted at the desktop, but not yet by ubuntu.

On the other hand there are a lot of posters who'll instantly flame anyone daring to make a suggestion about how to improve Ubuntu. Very often you'll read the little gem that linux is not windows, which is of course true, but of course also doesn't mean that things could not be improved.

Now, I think it is pretty obvious that there are areas in which Ubuntu can and should improve and reading the mailing lists and the wiki should make it obvious to anyone that the Ubuntu devs themselves agree on this. After all, that's why there are improvements in every new release of Ubuntu.

So I thought it would be a fun little exercise to discuss where Ubuntu could and should improve. And before anyone jumps at my throat, telling me that this alone will not help, let me tell you, I'm aware of this, but so what?

So, let's start, shall we?

* DSL
One of my pet peeves with Ubuntu is the lack of an easy and consistant way to configure and manage *dsl connections. While sudo pppoeconf sure isn't hard, this is something that clearly should be integrated into the gui, just like other network related settings are. Add to this that there is no easy, integrated way to start your connection by hand or to configure it to start automatically on demand and I think it's pretty obvious that there is room for improvement. Which leads me to my next point.

* Lack of gui tools
Everybody who ever ran other desktop oriented linux distributions should be aware of the fact that Ubuntu does provide a lot less gui config tools than other distributions. Now, I would absolutely agree that there doesn't have to be a tool for every possible task, at least not installed by default, but I still think that some more nice config tools would be a good thing. 
For example, what is really missing from Ubuntu is a nice and easy way to configure X. If you look around this forum, you'll find dozens of threads by people having problems with this and while on other distributions they'd just have to start a graphical config tool and make the changes reguired there, on Ubuntu they either have to use dpkg-reconfigure, or mess around with xorg.conf manually.

* Desktop interoperability (sp?)
Finally, one of my absolute pet peeves with desktop linux in general, desktop interoperability between gnome and kde sucks. This is of course not so much an Ubuntu problem, as it is a general problem, but other distros at least make sure that there is a common theme for kde and gnome or that kde and gnome apps at least use the same font settings, which isn't the case in Ubuntu.
Again, this is very much an upstream problem, which seems to finally be addressed by project portland (one of the most exciting recent developments for the free desktop, imho), but Ubuntu doesn't even do the little things that can be done right now.

Comments?

---

### Post by endersshadow on 2006-01-25
* DSL
I don't have any experience with using DSL on any distribution, so I can't make any input, and I'll take your word for it.

* Lack of GUI Tools
What GUI tool is there for configuring X?  I really don't know, and I'm asking.  Other distributions have it?  I have never seen anything for handling xorg.conf in another distribution, but perhaps it's because I've never had to use it.  If there is such a program, and are you sure it's not in the repositories if it exists?  And if it's not, and it works well, we should petition the developers to release it in Dapper.

* Desktop Interoperability
With Dapper, Canonical is focussing on doing this very thing and making Kubuntu an interoperable sister of Ubuntu.  Unfortunately, for Hoary and Breezy, Kubuntu was just kind of a side project, but Shuttleworth has made it a priority to bring Kubuntu up to speed.

---

### Post by tufkakf on 2006-01-25
[QUOTE=endersshadow]
* Lack of GUI Tools
What GUI tool is there for configuring X?  I really don't know, and I'm asking.  Other distributions have it? I have never seen anything for handling xorg.conf in another distribution, but perhaps it's because I've never had to use it.  If there is such a program, and are you sure it's not in the repositories if it exists?  And if it's not, and it works well, we should petition the developers to release it in Dapper.
[/QUOTE]
There are a lot, which is probably part of the problem, as they are all more or less distribution specific. For example, Suse does have sax2 and Mandriva also has such a tool, though I don't know it's name.
Recently there has been some discussion on the dev mailing list about using the tool Fedora provides for this.
Personally I think using and promoting distribution independend tools would be the best way. For example, kde guidance is working on an easy config tool for X and getting a solution based on this into ubuntu certainly would be great.

[QUOTE=endersshadow]
* Desktop Interoperability
With Dapper, Canonical is focussing on doing this very thing and making Kubuntu an interoperable sister of Ubuntu.  Unfortunately, for Hoary and Breezy, Kubuntu was just kind of a side project, but Shuttleworth has made it a priority to bring Kubuntu up to speed.[/QUOTE]
Hm, from what I read they are focusing on making Kubuntu better, which is great btw., however I didn't read anything about addressing the points I mentioned, that boil down to kde apps better integrating into Gnome and vice versa. But I might simply be uninformed here.

---

### Post by GeneralZod on 2006-01-25
[QUOTE=endersshadow]* DSL
* Lack of GUI Tools
What GUI tool is there for configuring X?  I really don't know, and I'm asking.  Other distributions have it?  I have never seen anything for handling xorg.conf in another distribution, but perhaps it's because I've never had to use it.  If there is such a program, and are you sure it's not in the repositories if it exists?  And if it's not, and it works well, we should petition the developers to release it in Dapper.
[/QUOTE]

SUSE apparently has one as part of YAST.  Since it's Qt-based, there is very, very little chance of it appearing in the default Ubuntu install; most likely, the wheel will be re-invented.  Yet again.

I agree with most of the OP's points.  What I'd really like to see is standard libraries for configuring things like X, network interfaces (+ wireless features like WPA) that work cross-distro, and are sufficiently well-designed  that it is easy to write a GUI frontend in your language of choice.  

And before anyone jumps down my throat shouting "but Linux is about choice!" and positing various strawmen and slippery slopes about how this will result in the bland, One-True-Toolkit-One-True-DE monoculture that is Windows, I'd say that in some cases there is simply no need for choice - if a library for configuring X provides a comprehensive API for tweaking every aspect of your xorg config, then there is no need for a competitor.  Sometimes, concentrating your efforts into one, working, complete library is better than pouring effort into a whole bunch of different ones that each end up fulfilling a different 80% of the required functionality in completely incompatible ways.  There's a reason there are not 50 implementations of libbz2 for each distro - the "official" one performs it's task so well and is so completely hidden from the user  that there is simply no need to re-invent it.  The same should be true of configuration libraries.

Note again that I'm advocating single *back-end* configuration libraries, *not* stand-alone configuration applications - wrapping these libraries in a GUI of your choice is something I'm in favour of :)

---

### Post by egon spengler on 2006-01-25
[QUOTE=tufkakf]Very often you'll read the little gem that linux is not windows, which is of course true, but of course also doesn't mean that things could not be improved.[/QUOTE]

I think the reason people say this so often is because a lot of the time the "ubuntu needs improvement" threads *are* based on people expecting ubuntu to operate exactly the same as they are used to in Windows. 


[QUOTE=tufkakf]
* DSL
One of my pet peeves with Ubuntu is the lack of an easy and consistant way to configure and manage *dsl connections. While sudo pppoeconf sure isn't hard, this is something that clearly should be integrated into the gui, just like other network related settings are. Add to this that there is no easy, integrated way to start your connection by hand or to configure it to start automatically on demand and I think it's pretty obvious that there is room for improvement. Which leads me to my next point.[/QUOTE]

Not sure if I fully understand all of this. Isn't one of the selling points of *dsl that it's "always on"? In what circumstances do you need to start automatically on demand? Not saying it never happens, just can't think of an example. 

[QUOTE=tufkakf]* Desktop interoperability (sp?)
Finally, one of my absolute pet peeves with desktop linux in general, desktop interoperability between gnome and kde sucks. This is of course not so much an Ubuntu problem, as it is a general problem, but other distros at least make sure that there is a common theme for kde and gnome or that kde and gnome apps at least use the same font settings, which isn't the case in Ubuntu.
Again, this is very much an upstream problem, which seems to finally be addressed by project portland (one of the most exciting recent developments for the free desktop, imho), but Ubuntu doesn't even do the little things that can be done right now.[/QUOTE]

I agree there's more that can be done here. The only qt app I use is albumart, I was using it for a long time with it looking hideous, out of place and with checkboxes that made no sense before I stumbled across a thread that explained how to get a more gnomish look to kde apps.

---

### Post by tufkakf on 2006-01-25
[QUOTE=egon spengler]
Not sure if I fully understand all of this. Isn't one of the selling points of *dsl that it's "always on"? In what circumstances do you need to start automatically on demand? Not saying it never happens, just can't think of an example. 
[/QUOTE]
One example would be people using dsl without a flatrate (Horrible thought, I know, but I actually know people who do this kind of thing). They sure would only want to be connected if a connection is needed.

---

### Post by angkor on 2006-01-25
[QUOTE=tufkakf]
* DSL
One of my pet peeves with Ubuntu is the lack of an easy and consistant way to configure and manage *dsl connections. While sudo pppoeconf sure isn't hard, this is something that clearly should be integrated into the gui, just like other network related settings are. Add to this that there is no easy, integrated way to start your connection by hand or to configure it to start automatically on demand and I think it's pretty obvious that there is room for improvement. Which leads me to my next point.
[/QUOTE]

Maybe it is not what you meant, but can't you just activate and deactivate your eth0 in System -> Administration -> Networking. It works for me turning on / off my connection. (Not that I ever turn it off though ;)).

For your other peeves, There not really problems for me cause I don't use a lot of KDE apps. But I can imagine it would be nice if the apps of both environments were better integrated for those who interchange a lot.

Personally I don't miss a gui tool for configuring X. But I wouldn't mind at all one being made for Ubuntu. It would be great for a lot of newbies out there trying Ubuntu. Then again hardware detection in Linux has become a _lot_ better in the last couple of years. I remember never having X come up after installing Debian in the past and having to configure it manually. In Ubuntu I have never been witthout X after installing it.

Off course Ubuntu can improve, and I'm sure it will. I've seen good improvements coming from Hoary to Breezy and I'm sure Dapper will be an improvement once again.

---

