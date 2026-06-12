---
title: "Aptitude vs Apt-Get"
date: 2006-04-22
forum: The Cafe
---

### Post by aysiu on 2006-04-22
As I demonstrate [here](http://www.ubuntuforums.org/showpost.php?p=945406&postcount=7), aptitude is preferable to apt-get if you install and then uninstall a lot of applications.

There are a lot of threads about apt-get v. aptitude, and almost all of them come to that same conclusion:
[http://www.ubuntuforums.org/showthread.php?t=162114](http://www.ubuntuforums.org/showthread.php?t=162114)
[http://www.ubuntuforums.org/showthread.php?t=131922](http://www.ubuntuforums.org/showthread.php?t=131922)
[http://www.ubuntuforums.org/showthread.php?t=117394](http://www.ubuntuforums.org/showthread.php?t=117394)
[http://www.ubuntuforums.org/showthread.php?t=91535](http://www.ubuntuforums.org/showthread.php?t=91535)
[http://www.ubuntuforums.org/showthread.php?t=66995](http://www.ubuntuforums.org/showthread.php?t=66995)
[http://www.ubuntuforums.org/showthread.php?t=37736](http://www.ubuntuforums.org/showthread.php?t=37736)

Now, my first question: is there a downside to aptitude (as opposed to apt-get)? If so, what is it?

Second question: if there is no downside, why does almost every Ubuntu guide out there ask users to *apt-get* stuff instead of *aptitude* installing/removing stuff?

---

### Post by helpme on 2006-04-22
[QUOTE=aysiu]
Now, my first question: is there a downside to aptitude (as opposed to apt-get)? If so, what is it?
[/QUOTE]
I think the downsides are pretty clear.
1. The graphical frontends are frontends to apt, not aptitude, so if you manage your software from the command line and via synaptic and gnome-app-install you'll end up with a mixed environment, which is a mess.

2. I never really tried aptitude, so correct me if I'm wrong, but from what I understand it's claim to fame is that it also gets rid of all the dependencies when you uninstall an application. Now this is of course great, however I'm not entirely sure if this isn't problematic when it comes to meta-packages. For example, if you want to get rid off something that ubuntu-desktop depends so this will lead to ubuntu-desktop being uninstalled. Now, couldn't there be the problem that when ubuntu-desktop and dependencies get uninstalled you'll get rid of a lot more software than you actually wanted to?

---

### Post by aysiu on 2006-04-22
[QUOTE=helpme]I think the downsides are pretty clear.
1. The graphical frontends are frontends to apt, not aptitude, so if you manage your software from the command line and via synaptic and gnome-app-install you'll end up with a mixed environment, which is a mess.[/quote] I don't see how it's a mess. I use Synaptic, apt-get, and aptitude, and I've never run into any problems.

> 
2. I never really tried aptitude, so correct me if I'm wrong, but from what I understand it's claim to fame is that it also gets rid of all the dependencies when you uninstall an application. Now this is of course great, however I'm not entirely sure if this isn't problematic when it comes to meta-packages. For example, if you want to get rid off something that ubuntu-desktop depends so this will lead to ubuntu-desktop being uninstalled. Now, couldn't there be the problem that when ubuntu-desktop and dependencies get uninstalled you'll get rid of a lot more software than you actually wanted to? I'm not 100% sure, but I don't think that's the case. For example, in the link I posted above, here's an excerpt: ```
user@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[b]The following packages are unused and will be REMOVED:
  kspread libwv2-1c2[/b]
The following packages will be REMOVED:
  kword
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 19.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 80478 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing libwv2-1c2 ...
user@ubuntu:~$
``` It's removing those dependencies because they're "unused." So my guess is that if they were... used... they would stay, but I haven't tested that theory yet.

---

### Post by htinn on 2006-04-22
[QUOTE=aysiu]Second question: if there is no downside, why does almost every Ubuntu guide out there ask users to *apt-get* stuff instead of *aptitude* installing/removing stuff?[/QUOTE]

I think more people are familiar with apt-get, so it naturally gets used more. That being the case, if you value consistency there's no question which tool should be in your documentation.

---

### Post by helpme on 2006-04-22
[QUOTE=aysiu]I don't see how it's a mess. I use Synaptic, apt-get, and aptitude, and I've never run into any problems.
[/QUOTE]
Well, maybe mess is to hard a word, but if for example you install somethings with apt and then some with aptitude, wouldn't it mean that stuff installed with apt would not be managed by aptitude? For exmaple, you install program a using apt, which needs library x, then get rid of program a, which leaves library x on your computer. Now you install program b with aptitude, which also requires library x. After that you decide you don't need program b after all and remove it with aptitude. Contrary to what you might expect, wouldn't library x still be on your machine? 

[QUOTE=aysiu]
 I'm not 100% sure, but I don't think that's the case. For example, in the link I posted above, here's an excerpt: ```
user@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[b]The following packages are unused and will be REMOVED:
  kspread libwv2-1c2[/b]
The following packages will be REMOVED:
  kword
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 19.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 80478 files and directories currently installed.)
Removing kword ...
Removing kspread ...
Removing libwv2-1c2 ...
user@ubuntu:~$
``` It's removing those dependencies because they're "unused." So my guess is that if they were... used... they would stay, but I haven't tested that theory yet.[/QUOTE]
I think this is a problem for meta-packages, not for normal packages, as meta-packages don't only rely on libraries, but on the high level apps themselves.
For example, let's say ubuntu-desktop relies on the gimp. Now if you install ubuntu-desktop with aptitude and then uninstall something with aptitude that also gets rid of ubuntu-desktop, wouldn't that also mean that gimp will be uninstalled, or am I simply wrong here?

---

### Post by 5-HT on 2006-04-22
[quote= aysiu]
... [/quote] 

Good question.
As htinn mentioned, maybe because Aptitude just isn't as well known?
I don't think there are any downsides to Aptitude, at least none that I've encountered.
I use it pretty much exclusively instead of Synaptic/Apt.

[quote=helpme]Well, maybe mess is to hard a word, but if for example you install somethings with apt and then some with aptitude, wouldn't it mean that stuff installed with apt would not be managed by aptitude? For exmaple, you install program a using apt, which needs library x, then get rid of program a, which leaves library x on your computer. Now you install program b with aptitude, which also requires library x. After that you decide you don't need program b after all and remove it with aptitude. Contrary to what you might expect, wouldn't library x still be on your machine? [/quote] 
Yes, it would be still there (but it would not mess anything up).

Basically, if you want to take advantage of Aptitude's automatic dependency handling when removing packages, you'll need to have (well...no, there is a way around this) installed said package with Aptitude (or else how would it know?).

However, you can, at any time, mark packages as 'automatically installed'.
When this flag is set, any packages that are marked in that manner will be uninstalled when they are no longer depended upon by any other package.
This is exactly what Aptitude does itself when installing packages.


General tip: If you want to use Aptitude, it's easiest to just install and uninstall using aptitude.

[quote= helpme] For example, let's say ubuntu-desktop relies on the gimp. Now if you install ubuntu-desktop with aptitude and then uninstall something with aptitude that also gets rid of ubuntu-desktop, wouldn't that also mean that gimp will be uninstalled, or am I simply wrong here? [/quote]

Yup, you are right. 
If you want to get around this, just mark the packages you want to keep (or all) depended upon by the metapackage as 'manually installed'.

---

### Post by transactionlogfiller on 2006-04-22
I ran into difficulties when I installed gaim2 beta because I tried removing the old gaim and it told me xubuntu-desktop was broken, and offered to fix it every time I installed/updated anything else. If I try and remove xubuntu-desktop it wants to remove lots of other things that I use all the time, so I'm not convinced it can tell which packages are unused effectively.

That said, I do prefer to use aptitude over apt-get. I never use synaptic so I'm not too worried about the mess.

---

### Post by aysiu on 2006-04-22
I guess I have a lot of the same questions as helpme does--I'm not myself that well-versed in *aptitude*, and that's why I asked if there are any known (not suspected) downsides.

Well, I think I may just keep recommending *apt-get* for general things (until I've had more time to play around with *aptitude*) but still recommend *aptitude* for metapackages and also to people who really like a "clean" system but also like to install and uninstall a lot of stuff.

---

### Post by John.Michael.Kane on 2006-04-22
aysiu you might be on to something with this.  could a user get the same results installing deborphan, and configuring an "Orphan" filter under synaptic.

---

### Post by aysiu on 2006-04-22
[QUOTE=SD-Plissken]aysiu you might be on to something with this.  could a user get the same results installing deborphan, and configuring an "Orphan" filter under synaptic.[/QUOTE] I don't know.

---

### Post by engla on 2006-04-22
Another piece of the puzzle requested -- the history?

Which is older aptitude, or apt-get? And why do they overlap so much if they weren't conceived at the same time?

---

### Post by Mustard on 2006-04-22
I'm pretty pleased with aptitude myself, but I can't see any consistent way to promote its use amongst new users without creating confusion.

It's like trying to advise people to use checkinstall when compiling from source.  The majority of the HOW TO's give the generic methods, while a particularly useful command gets overlooked at a stage when people are probably needing it the most (after installing stuff they never really wanted or knew what it did).

*bing* *light bulb goes on*

Well, we could have an 'Advanced Installation Guide' of some kind, that covers both aptitude, checkinstall, and common methods of searching for dependencies when compiling from source ie apt-cache show, apt-cache search, aptitude show, aptitude search.  :)

---

### Post by Hoffmann on 2006-04-25
[QUOTE=aysiu]As I demonstrate [here](http://www.ubuntuforums.org/showpost.php?p=945406&postcount=7), aptitude is preferable to apt-get if you install and then uninstall a lot of applications.

There are a lot of threads about apt-get v. aptitude, and almost all of them come to that same conclusion:
...
Now, my first question: is there a downside to aptitude (as opposed to apt-get)? If so, what is it?

Second question: if there is no downside, why does almost every Ubuntu guide out there ask users to *apt-get* stuff instead of *aptitude* installing/removing stuff?[/QUOTE]

In order to updgrate Ubuntu, for example from Ubuntu 5.10 (Breezy Badger) to Ubuntu 6.06 (Dapper Drake), which alternative is the best:  apt-get or aptitude?

Hoffmann

---

### Post by aysiu on 2006-04-25
[QUOTE=Hoffmann]In order to updgrate Ubuntu, for example from Ubuntu 5.10 (Breezy Badger) to Ubuntu 6.06 (Dapper Drake), which alternative is the best:  apt-get or aptitude?

Hoffmann[/QUOTE] I don't think it matters. You're not going to *sudo aptitude remove ubuntu-desktop* and then somehow restore your computer to Breezy from Dapper.

---

### Post by Hoffmann on 2006-04-25
[QUOTE=aysiu]I don't think it matters. You're not going to *sudo aptitude remove ubuntu-desktop* and then somehow restore your computer to Breezy from Dapper.[/QUOTE]

I got you.

Thanks,
Hoffmann

---

### Post by gingermark on 2006-04-25
I remember looking for a front-end (like synaptic) for aptitude - and of course it is aptitude itself, but it's console based.

But if aptitude can do everything that apt can, and add functionality, hopefully eventually a Synaptic-like frontend will emerge (pardon the pun - would be funnier if we were using Gentoo) for it.

---

### Post by Zyphrexi on 2006-04-25
Mustard: > Well, we could have an 'Advanced Installation Guide' of some kind, that covers both aptitude, checkinstall, and common methods of searching for dependencies when compiling from source ie apt-cache show, apt-cache search, aptitude show, aptitude search. 

that would be fantastic, on a side note, that kind of stuff should go into a ubuntu doc package or something. I know about the starter guide and all, but there are simply so many priceless guides the community has made, it really seems a shame not to add them as a package. I mean the wealth of info is so huge, that could help new users understand the differences between aptitude and apt. I remember trying aptitude once... It was terrible, I completely (nearly) destroyed ubuntu. Since then I've simply been too afraid to try it again.

---

### Post by Hoffmann on 2006-04-25
[QUOTE=Zyphrexi]Mustard: 

that would be fantastic, on a side note, that kind of stuff should go into a ubuntu doc package or something. I know about the starter guide and all, but there are simply so many priceless guides the community has made, it really seems a shame not to add them as a package. I mean the wealth of info is so huge, that could help new users understand the differences between aptitude and apt. I remember trying aptitude once... It was terrible, I completely (nearly) destroyed ubuntu. Since then I've simply been too afraid to try it again.[/QUOTE]

Zyphrexi:

Could you explain more your bad experience with aptitude? That explanation would be very useful, I guess.

Hoffmann

---

### Post by Zyphrexi on 2006-04-26
well it was back when I first started with ubuntu, and ubuntu was my first debian experience, so mainly the interface was confusing, and to tell the truth I think I might have put in debian repositories. From someone unfamiliar with debian, using aptitude is a big jump. Sorry I can't go into detail, memory is a bit foggy. A nice howto might help with the aptitude scariness factor.

---

### Post by claydoh on 2006-04-26
Just try running aptitude with no arguments (as a cli alternative to synaptic) and try figuring it out:
```
 sudo aptitude
```
That is probably another reason.

---

### Post by Mustard on 2006-04-26
I tend to get into more trouble with the interface, than I do when I simply use it as a command line alternative to apt-get.  When I use the aptitude interface I can work out how to select a package to install, but I have no idea how to 'unselect' a package that I have mistakenly marked for install.  It seems to remember them as well.

---

### Post by user1397 on 2006-06-13
This thread is for sharing your experiences with the two methods of installing with the terminal, apt-get and aptitude.  

Personally, i've used apt-get far more, since most of the wiki and ubuntuforums.org instructions are written with apt-get, not aptitude. 

I've only really used aptitude for installing the kubuntu-desktopand the xubuntu-desktop packages.  I wanted to uninstall them later, so I just did a simple ```
sudo aptitude update && sudo aptitude remove kubuntu-desktop [or xubuntu desktop]
``` and that removed all the packages that were part of those desktop packages.  So, uninstalling stuff with aptitude (well at least big things) is easier than with apt-get.

I have noticed though, that when I try to install something with aptitude, for example k3b, it also tries to remove "unused packages".  It called the gstreamer-0.8-mad package "unused", and it wanted remove it, even though it had to have been used because i do listen to music!  So that kind of bugged me.

---

### Post by gsdefender on 2006-06-13
As an addicted Debian sid user, I find apt-get scriptability very powerful. Just my 5 cents.

---

### Post by G Morgan on 2006-06-13
I use apt-get because generally I know all the packages I want to install. I tend to only use aptitude if I've got no X server access.

---

### Post by bruce89 on 2006-06-13
I always use aptitude, since I don't want a whole load of unused libraries all over the place.

---

### Post by sharkboy on 2006-06-13
aptitude can be used from the command line too, and is in my experience more intelligent than apt-get when it comes to resolving complex dependencies. For instance, aptitude is recommended by debian when upgrading from woody to sarge, and as a debian sid user, I very rarely have encounter troubles at all after I started doing aptitude dist-upgrade instead of apt-get dist-upgrade every day.

---

### Post by 5-HT on 2006-06-13
+1 for aptitude.

Aptitude is very flexible and is great at managing packages thanks to automatic/manual install flags.
I do a server install from the CD, and use aptitude for everything else after that.

For those who feel like checking it out, there is a great walkthrough explaining _all_  of Aptitude's features. The guide can be found in /usr/share/aptitude/README, or by entering 'aptitude' at a prompt, and go to the 'help' menu).

There is one default setting that I always change before using Aptitude: by default, it treats recommended packages as dependencies. 
If someone is planning on installing a large metapackage (e.g. ubuntu-desktop), treating recommends as dependencies results in _many_ more packages being installed (though they may be handy/wanted) than would be otherwise.

The procedure for changing the default 'treat recommends as dependencies' is documented in the help guide (can be done in Aptitude's config file, or via the pseudo-GUI).

---

### Post by basketcase on 2006-06-13
I used aptitude for the first time the other day in command line when apt-get did not install what I was looking for.  

Other than that, it has always been apt-get and I love it!

---

### Post by pianoboy3333 on 2006-06-13
It seems though, that smartpm may be taking over, if it copies characteristics like keeping track of unused libs and such, but with a command and gui interface, it could possibly rock the house. [http://labix.org/smart](http://labix.org/smart)

---

### Post by Jucato on 2006-06-13
I'm trying to get used to the whole aptitude business, because I think it handles packages and dependencies more intelligently than apt-get. However, I think I have to edit aptitude's config so that it won't treat recommended packages as dependencies (thanks for the info 5-HT).

As for smartpm, I'm going to keep a close eye on that one. It seems to be the ultimate package manager front-end. But I'm not entirely sure if it handles metapackages/dependencies the same way or better than aptitude. Also, even their own FAQ admits that it is quite resource intensive.

(Shameless plug: Some of my own thoughts about the different package managers, their pros and cons: [http://www.ubuntuforums.org/showthread.php?t=190985](http://www.ubuntuforums.org/showthread.php?t=190985))

---

### Post by 5-HT on 2006-06-13
> **Fenyx]I'm trying to get used to the whole aptitude business, because I think it handles packages and dependencies more intelligently than apt-get. However, I think I have to edit aptitude's config so that it won't treat recommended packages as dependencies (thanks for the info 5-HT).[/quote] 
To do that, you could add ```
aptitude::Recommends-Important "false" said:**
> Shameless plug: Some of my own thoughts about the different package managers, their pros and cons: [http://www.ubuntuforums.org/showthread.php?t=190985]("http://www.ubuntuforums.org/showthread.php?t=190985"))  
Thanks for the review!

---

### Post by user1397 on 2006-06-13
[quote=5-HT]To do that, you could add ```
aptitude::Recommends-Important "false"; 
``` to either: 
i) ~/.aptitude/config (will be sourced if using sudo)
ii) /etc/apt/apt.conf (the user's config will take precedence over this one)

Or just fire up aptitude and click the relevant option under Options -> Dependency handling.[/quote]do you think this will fix that annoying problem of mine, where it wants to remove "unused packages" when trying to install or uninstall something with aptitude?

---

### Post by 5-HT on 2006-06-14
[quote=erik1397]do you think this will fix that annoying problem of mine, where it wants to remove "unused packages" when trying to install or uninstall something with aptitude?[/quote] 
No, that option will not prevent Aptitude from removing unused packages.

However, there is an option in Aptitude to have it not remove unused packages automatically.
When that option is  set, Aptitude *basically* becomes apt-get in terms of functionality.

The easiest way to configure Aptitude to not automatically remove unused packges is to fire it up in text-based-GUI mode ```
 sudo aptitude 
``` 
Options -> Dependency Handling -> uncheck "Remove unused packages automatically"

You can also configure the option in Aptitude's config file(s). 
The relevent syntax can be found in /usr/share/aptitude/README.

If you don't want to completely disable Aptitude's unused dependency handling - which is a big part of what makes the program so great -  a different option would be to mark the packages you want to be always kept - unless you manually remove them - as 'manually installed'.

Hope that helps

---

### Post by aysiu on 2006-06-14
Basically, I think you should use whatever suits you.

If you don't want the package manager removing unused packages automatically, just use *apt-get*. That doesn't mean you have to use *apt-get* all the time--just when you don't want smart dependency handling.

If you install a package with the possibility that you might later on want to remove the package *and* its accompanying dependencies, it's always a good idea to install it with *aptitude*, just in case.

---

### Post by user1397 on 2006-06-14
[quote=aysiu]Basically, I think you should use whatever suits you.

If you don't want the package manager removing unused packages automatically, just use *apt-get*. That doesn't mean you have to use *apt-get* all the time--just when you don't want smart dependency handling.

If you install a package with the possibility that you might later on want to remove the package *and* its accompanying dependencies, it's always a good idea to install it with *aptitude*, just in case.[/quote]Good way to summarize this thread, aysiu.

---

### Post by aysiu on 2006-06-22
I've written up a little spiel about aptitude, for easy reference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by rai4shu2 on 2006-06-22
This kind of begs the question: why remove anything?

If I use a library for one application, then decide I don't like that particular application, what is the likelihood that I will nevertheless want to use another application that also uses that library? I would say that the chances are pretty good.

---

### Post by aysiu on 2006-06-22
Well, for some people, it's a hard drive space issue, especially if you have a drive or partition that's 6 GB or less.

For others, it's a weird compulsion to just have their systems "clean."

For certain packages, it's not just a matter of a few libraries--metapackages like *kubuntu-desktop*, for example. If someone decides, "Ew. I hate KDE. I just don't want any of that on my system any more," ```
sudo apt-get remove kubuntu-desktop
``` will do essentially **nothing**.

---

### Post by rai4shu2 on 2006-06-22
I'm not sure I'm comfortable with the idea of removing an entire desktop worth of packages.

In any case, the issue of space limitations is getting to be less and less important with hard drives getting cheaper all the time.

---

### Post by aysiu on 2006-06-22
If you're not comfortable removing an entire desktop, don't remove it.

What you're talking about has nothing to do with *apt-get* versus *aptitude*. As you originally stated: > why remove anything?

Well, you, apparently, shouldn't remove anything. But others have their reasons.

I happen to have a 160 GB hard drive, but there *are* users with only 6 GB or less.

I don't mind having three desktop environments installed, but there *are* other users who prefer to have only one installed.

And something that hasn't been mentioned--for those who *dist-upgrade* to Edgy, why waste the bandwidth and download time to upgrade a whole bunch of programs you don't use?

Again, you can speak for yourself personally, and **you** may never remove programs, but others have their own reasons for wanting to uninstall programs.

---

### Post by rai4shu2 on 2006-06-22
I really don't see what dist-upgrade has to do with apt-get vs aptitude.

---

### Post by aysiu on 2006-06-22
[QUOTE=rai4shu2]I really don't see what dist-upgrade has to do with apt-get vs aptitude.[/QUOTE]
It doesn't, but then neither does your question about why remove anything?

If you don't ever want to remove any packages ever, then it doesn't really matter how you install them.

All I'm saying is that just because you, rai4shu2, never remove packages, it doesn't mean other users will never remove packages. There are plenty of people who have small hard drives, have obsessive-compulsive disorder about lingering packages, or just hate certain desktop environments after trying them and want them removed.

*dist-upgrade* has to do with your original question. If I install and try 50 programs I no longer use and no longer want to use, that's 50 more programs a dist-upgrade will redownload and install in addition to the regular upgrade packages. Why waste the bandwidth and time to download and install the newer versions of those 50 programs you don't use?

Well, that's what happens if you never remove them.

---

### Post by nalmeth on 2006-06-22
Aysiu, it's funny, because you have gone ahead and made the awesome Pure-Gnome / Pure-KDE guides. 

So incase someone has erroneously installed kubuntu with apt-get, and don't like it, at least they will have that to fall back on.

Personally, I've taken the habit of trying to complicate users as little as possible. If a person wants to install kubuntu, or any other similar metapackage, and I'm the first to respond, I will recommend aptitude. But if the person has already used apt-get, via someone elses suggestion, or just wants to install a simple media player, I'll try to stick with what they've learned, and help them sort out the issue with commands they are already acquainted with. 

The last thing we want (and which does often happen) is for 6 people to recommend 6 different ways to do one simple thing. The confusion is overwhelming for a new person. As they explore they will find there are advantages from more advanced commands like aptitude and checkinstall.

---

### Post by aysiu on 2006-06-23
Those pure Gnome and pure KDE guides aren't flawless. One user here, for example, used one of those guides and found it had uninstalled Apache, MySQLServer, PHP and a few other things, and when she or he reinstalled those things, they weren't working properly.

If you install with *aptitude*, only the dependencies that aren't being used by other programs will be uninstalled. If you use my pure-Gnome and pure-KDE guides, anything that isn't the vanilla *ubuntu-desktop* or *kubuntu-desktop* might get taken out.

---

### Post by nalmeth on 2006-06-23
Really. . .
Just one person had this happen? Breezy or Dapper? 
Did they track down what caused those packages to be removed, and further broken?

I don't use any of the LAMP stuff, but no one likes breakage.

Got a link for that?

---

### Post by aysiu on 2006-06-23
[Here's a link for it](http://www.ubuntuforums.org/showpost.php?p=1157477&postcount=40). Maybe you can help the person out.

---

### Post by rai4shu2 on 2006-06-23
Okay, well I'm starting to see your point. But can we really make a tool standard that doesn't have Super Cow Powers? ;)

---

### Post by aysiu on 2006-06-23
[QUOTE=rai4shu2]Okay, well I'm starting to see your point. But can we really make a tool standard that doesn't have Super Cow Powers? ;)[/QUOTE]
I think maybe we can.

---

### Post by bruce89 on 2006-06-23
*aptitude* is a lot better, I have used ever since I found about it.  I hope that SMART will be a graphical way of the same thing that *aptitude* does.
[QUOTE=rai4shu2]Okay, well I'm starting to see your point. But can we really make a tool standard that doesn't have Super Cow Powers? ;)[/QUOTE]
Aptitude has easter eggs, try the following: (one line at a time)
```
aptitude moo
aptitude -v moo
aptitude -vv moo
aptitude -vvv moo
aptitude -vvvv moo
aptitude -vvvvv moo
aptitude -vvvvvv moo
```

---

### Post by camelgrass on 2006-08-20
[COLOR=Black]What is the difference between aptitude and apt-get in the command-line for installing packages? Which one should I use?

Thanking you, Marty
[/COLOR]

---

### Post by tribaal on 2006-08-20
I highly suggest that you use aptitude, as it handles dependencies much better when *removing* packages.

Ubuntu still includes apt-get and people usually refer to it because it's the first and oldest common ancestor for package management in debian-based systems.

So you can safely change apt-get for aptitude in command lines people post around this forum.

- trib'

---

### Post by camelgrass on 2006-08-20
I was wondering about that. In most docs and forums I have only seen* apt-get *refered to, but then in some places people recommend using *aptitude*.

It's a wonder *aptitude *isn't refered to more?

Thanks for clearing that up anyway mate.

---

### Post by Perfect Storm on 2006-08-20
Old habits from older user which new users takes to them.

Usually when I want to install a single or two libs/applications I use apt-get, but when I want to installing something that requires alot of diffrent libs I use aptitude.

---

### Post by tribaal on 2006-08-20
I use aptitude all the time.
They are really equivalent, except aptitude does the removal better. So why not use aptitude in all cases, just in case you then someday need to remove something? :)

- trib'

---

### Post by Perfect Storm on 2006-08-20
Never been a problem in my case. So I use what's easy to write ;)

---

### Post by daniel of sarnia on 2006-08-20
Question, why is apt-get still in ubuntu when aptitude is so much better. Do you think it could be left out in the future?

---

### Post by az on 2006-08-20
> **daniel of sarnia said:**
> Question, why is apt-get still in ubuntu when aptitude is so much better. Do you think it could be left out in the future?

1- Lots of people have been using apt-get for years and have not had problems.

2- Lots of things are a frontend to APT (synaptic, Add-Remove programs, Adept, Linspire's click'n'run, etc...).  Not a lot of things are a frontend to aptitude, AFAIK.

3- Matt Zimmerman is the maintainer of the libapt package for Debian.  He is also the chief technical officer for Ubuntu.

There have been a lot of things that are being worked on for Edgy, look at the specs for Edgy in launchpad.  I beleive that the ones that involve package management (Things like binary diffs for packages, so you don't haveto download the whole package to get the updates, etc...) probably involve improving APT?

---

### Post by morequarky on 2006-08-20
"easier to write"

Make an alias for aptitude that is short and quick and use the alias. :)  no more "difficult writing"

---

### Post by Perfect Storm on 2006-08-20
I know. But I still prefer apt-get, nothing wrong with aptitude. It's just what I'm used too. :KS

---

### Post by camelgrass on 2006-08-20
Problem is it causes confusion for newbie's like me ;).

---

### Post by aysiu on 2006-08-20
> **camelgrass said:**
> Problem is it causes confusion for newbie's like me ;).
That's why education is a good thing:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

I think it mainly has to do with old habit.

---

### Post by az on 2006-08-20
> **camelgrass said:**
> Problem is it causes confusion for newbie's like me ;).

The Doc Team have styleguides which help this.  Any documentation that is styleguide-compliant will not mention any specific package manager, but just say "use any method to install the following packages" and provide a link to the package management documentation pages.  

The user gets to pick and not think that the reson their application is not working is because it was not installed with one package manager or the other (which makes no difference).

---

### Post by andb on 2006-09-12
What are the relative advantages and disadvantages of using apt-get versus aptitude? aptitude seems to be the unanimous winner to me, especially the removal of no-longer-needed packages... Im suprised anyone gives advice with apt-get. Is it just because aptitude is missing the super-cow powers?

---

### Post by ashrack on 2006-09-12
am also interested in this. 
And why doesnt synaptic work more similar to APTITUDE when removing packages? So that it also removes packages not needed anymore

---

### Post by someguyouknow on 2006-09-12
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by kwalo on 2006-09-12
I use both aptitude and apt-get.
apt-get for upgradeing and aptitude for installing/removeing packages. I really like aptitude's removeal of dependencies. However aptitude has one more feature: when one package has Recommends field, aptitude will install packages from that field, as it does with depends field. If you don't want to install recommended packages, use --without-recommends option, like this:
```
sudo aptitude install --without-recommends pakckage
```

---

### Post by anaconda on 2006-09-12
apt-get is used and recommended mostly by older linux users, who haven't gotten to know aptitude yet, or they just recommend it because it comes "automatically"

Old habits die slowly.

---

### Post by elettronicha on 2006-09-12
aptitude is newer and more powerful, deals better with dependencies, removes unneeded deps, is more configurable, has nice logs in /var/log/aptitude, has a semi-graphical GUI. Also Debian users seggest it.

---

### Post by ashrack on 2006-09-13
so how come SYNAPTIC isnt using APTITUDE as its back end?

---

### Post by kewldude606 on 2006-10-01
If we are writing something for the wiki, should we use apt-get or aptitude in the code segments?

Example:
To start, you must install dependancies with:
sudo apt-get install frankenstein

or 

To start, blah blah:
sudo aptitude install frankenstein

---

### Post by Bloodfen Razormaw on 2006-10-01
Aptitude is the recommended tool for installing packages, and has been since it was introduced.  It provides more features than apt-get, is more consistent, and has a nice interface.

---

### Post by aysiu on 2006-10-01
I believe *aptitude* should be recommended except in rare cases where it wants to "hold back" packages unnecessarily.

It handles the removal of dependencies better. More details here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

I do believe, though, that--for it to function properly--you have to update first: ```
sudo aptitude update
sudo aptitude install frankenstein
```

---

### Post by buckethead27 on 2006-11-06
Which is better? Aptitude or apt-get? When you say what you choose, please explain your reason.

---

### Post by taurus on 2006-11-06
I am going to move this to Cafe and by the way, aptitude and there is no reason.  It just IS...  [-(

---

### Post by tribaal on 2006-11-06
Aptitude of course, because it resolves removal dependencies.

- trib'

---

### Post by Titus A Duxass on 2006-11-06
Silly question, silly poll.
Aptitude.

---

### Post by pattymnaish on 2006-11-06
> **tribaal said:**
> Aptitude of course, because it resolves removal dependencies.

I agree completely.

---

### Post by Iarwain ben-adar on 2006-11-06
> **pattymnaish said:**
> I agree completely.

+1


Iarwain

---

### Post by peak_performance on 2006-11-06
How come there are two different commands if/when one is "better"? And if aptitude is better, how come it seems as is everyone uses apt-get? :) I've wondered about this one for a while.

---

### Post by buckethead27 on 2006-11-06
> **peak_performance said:**
> How come there are two different commands if/when one is "better"? And if aptitude is better, how come it seems as is everyone uses apt-get? :) I've wondered about this one for a while.

Agreed. That was my next question :)

---

### Post by Anonii on 2006-11-06
aptitude. But I'm using apt-get, because I'm lame, a bad example, and bored to wait the extra 4~ seconds that aptitude takes in the start.

---

### Post by Buffalo Soldier on 2006-11-06
apt-get. It's autoremove function seems to be working nicely in removing orphan packages in Edgy. I'm sure it will get better in ubuntu 7.04 :)

---

### Post by HW_Hack on 2006-11-06
I'm pretty liberal -- been around the block a few times - but I have no idea what you're voting on .... I think its shameful:mrgreen:

---

### Post by argie on 2006-11-06
apt-get, just because I'm used to it.

---

### Post by Spif on 2006-11-06
I'm using apt-get because I never really found out what the difference is. When you install applications with Synaptic, do you use apt-get or aptitude?

---

### Post by xyz on 2006-11-06
I vote aptitude.
Among other things, installing and therefore removing using aptitude is considered 'better' because it removes all the dependencies that were needed!

---

### Post by el_itur on 2006-11-06
> **Spif said:**
> I'm using apt-get because I never really found out what the difference is. When you install applications with Synaptic, do you use apt-get or aptitude?

I belive it would be only apt since apt-get, aptitude and synaptic ar just diferent front-end's for the same apt api.

For the poll, I don't use any of thos, I'm GUI-dependent.

---

### Post by OffHand on 2006-11-06
It depends... sometimes aptitude is too radical.

---

### Post by skymt on 2006-11-06
aptitude, because I prefer the interactive interface to Synaptic.

---

### Post by Ramses de Norre on 2006-11-06
Absolutely aptitude, I don't like all the unused dependencies apt-get leaves on my system.
With aptitude you can add and remove software and be sure that nothing is left (this is when using purge).

Also: aptitude is better with dependencies in general.

---

### Post by KhaaL on 2006-11-06
aptitude, for the interface and how it handles dependencies

---

### Post by kuja on 2006-11-06
apt-get, because aptitude tries to be too smart.

---

### Post by aysiu on 2006-11-06
*aptitude* in general for reasons explained here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

*apt-get* for some specific cases where *aptitude* tries to act too smart.

---

### Post by chaosgeisterchen on 2006-11-06
I solely use **aptitude** because it handles dependencies way better, if I for instance install a solitary application with GNOME-dependencies (while using KDE) I also get rid of the whole GNOME desktop upon removing this package. 

apt-get would leave behind a lot of orphaned packages.

---

### Post by Christmas on 2006-11-06
I like apt-get better and use it only.

---

### Post by katgfan on 2006-11-06
Well i use only apt-get and thats it.

---

### Post by zek725 on 2006-11-09
Quoting the advantages of **aptitude** regarding dependencies, what happens if I *install *with **apt-get** then *uninstall *with **aptitude**? Will **aptitude** still perform the same?

---

### Post by chaosgeisterchen on 2006-11-09
A mixture in usage may result in a dependency hell and broken package database. It's highly recommended **not** to use them both, use either or.

---

### Post by Nonno Bassotto on 2006-11-09
In abstract aptitude is better, but I voted for apt-get since it has a decent graphical frontend (synaptic). I prefer to lose a little more time to care about libraries when I uninstall something, but have a graphical tool. Of course aptitude witha decent gui would be the best.

By the way, what about Smart?

---

### Post by EdThaSlayer on 2006-11-09
Aptitude is better. Better handling with the packages.

---

### Post by frodon on 2006-11-09
I'm neither an apt-get nor an aptitude expert so i can't really say which one is better and especially based on what ?

As for unremoved dependencies i don't care, my ubuntu partition is 20Go and i have 450Go for datas, so leaving several Mo of unremoved dependencies is not a problem for me.
In general i would prefer apt-get because the synaptic interface just rocks, it's intuitive and really easy to use.

---

### Post by chaosgeisterchen on 2006-11-09
As far as I know orphaned packages can slower your system.

@Synaptic: Does it really base on apt-get? I always thought it was based on **dpkg** itself.

---

### Post by aysiu on 2006-11-09
> **chaosgeisterchen said:**
> As far as I know orphaned packages can slower your system. I've never seen evidence of this.

Can you link to some documentation on this... or some benchmarks?

---

### Post by chaosgeisterchen on 2006-11-09
It's only subjective experience. I do not know what I do wrong but my system becomes awfully slow after installing a number of extra packages.

---

### Post by shining on 2006-11-09
> **chaosgeisterchen said:**
> It's only subjective experience. I do not know what I do wrong but my system becomes awfully slow after installing a number of extra packages.

Even if many of these packages are services that are automatically run, they would be mostly sleeping if you don't use them, so they wouldn't take any cpu cycle. Only some memory would be used, but there shouldn't be a big difference.
If they aren't, there shouldn't be any differences afaik, except of course some disk space used.

---

### Post by jeffrey.mezic on 2006-11-09
Hi All,

(FYI I'm still a noob at installing packages.)

Question: I use Synaptic Package Manager almost exclusively. From what I can tell, its the GUI front-end of apt-get. But what is this Aptitude? Does it have a GUI front end? 

I feel like I'm only interested in the GUI because all of the options available to me are presented at the same time. I can search via categories, type in a search for packages, scroll through a list of packages, and read their descriptions, etc.

How would one find a list of packages available in the repositories using apt-get (via the command line) or aptitude? If a link is available that has all this information, I would be grateful. I've read [http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude") but it didn't quite answer my question about a GUI front end for aptitude.

---

### Post by aysiu on 2006-11-09
The GUI frontend for *aptitude* isn't pretty or fully point-and-click. If you want to see it, just type ```
aptitude
``` in the terminal.

---

### Post by BLTicklemonster on 2006-11-09
Aptitude, dude. Because it rhymes.

And it asks questions that help you install stuff. At least it did when I installed my nvidia driver from tseliot. When I was using apt-get, it just dorked out and said there were unresolved dependencies, but when I used aptitude, it asked me if I wanted to actually work around the problem. I have the best nvidia drivers now.


... but then, apt-get does have super cow powers... 


```
This APT has Super Cow Powers.

```

---

### Post by xyz on 2006-11-09
> **aysiu said:**
> The GUI frontend for *aptitude* isn't pretty or fully point-and-click. If you want to see it, just type ```
aptitude
``` in the terminal.
Hi...glad to cross PATHs with you here...gives me an opportunity to say how much I learned (am learning) from your ...cats!!
It never occured to me to type "aptitude" in a terminal...so is it like opening 'sort of' Synaptic and going Orphaned+Delete or Residual+Delete_whatever?

---

### Post by aysiu on 2006-11-09
Glad you found the Psychocats Ubuntu site helpful.

I'm not sure I know what you're asking, though, regarding Orphaned+Delete and Residual+Delete...

---

### Post by xyz on 2006-11-10
Sorry I wasn't clear about this.
In Synaptic, I can create a filter which I'll name "Orphaned" or any other name. Clicking on "Orphaned" will show a list of stuff I can delete.
When I click on "Status" and, I think it's called, "Residual conf", I can also remove what I find in there.

Now typing "aptitude" in a terminal, a window opens.
How do I handle it? Same as explained above where I can delete/remove unnecessary stuff?

I hope I was able to make myself a bit clearer.
Thanks.

---

### Post by chaosgeisterchen on 2006-11-10
Never got to get any use out of the aptitude 'GUI'. Therefore I do not use it.

---

### Post by aysiu on 2006-11-10
> **xyz said:**
> Sorry I wasn't clear about this.
In Synaptic, I can create a filter which I'll name "Orphaned" or any other name. Clicking on "Orphaned" will show a list of stuff I can delete.
When I click on "Status" and, I think it's called, "Residual conf", I can also remove what I find in there.

Now typing "aptitude" in a terminal, a window opens.
How do I handle it? Same as explained above where I can delete/remove unnecessary stuff?

I hope I was able to make myself a bit clearer.
Thanks.
As far as I know, there's no filter or view of orphaned packages in *aptitude*, but if you're using *aptitude*, there's also no need for such a view as there won't be any orphaned packages.

That's why people use *aptitude* because it removes unused dependencies when removing applications.

If you still have lingering orphans, you can use *gtkorphan* or *deborphan* to isolate those.

---

### Post by zek725 on 2006-11-11
> **aysiu said:**
> As far as I know, there's no filter or view of orphaned packages in *aptitude*, but if you're using *aptitude*, there's also no need for such a view as there won't be any orphaned packages.

That's why people use *aptitude* because it removes unused dependencies when removing applications.

If you still have lingering orphans, you can use *gtkorphan* or *deborphan* to isolate those.

I don't know why (probably due to installation using apt-get) but I see **1 broken** in aptitude. how do i correct that?

---

### Post by aysiu on 2006-11-11
Have you tried this? ```
sudo aptitude -f install
``` If that tries to be too smart, which it does sometimes, you can try this. ```
sudo apt-get -f install
```

---

### Post by BrokeBody on 2006-11-11
It's a matter of choice. They are both good. :)

---

### Post by pichalsi on 2006-11-11
well i use apt-get, i dont rly know how to use the aptitude "gui" and am 100% ok with apt-get.

---

### Post by bionnaki on 2006-11-11
I use apt-get because aptitude can be a pain to type sometimes. I dont care about purging dependencies.

---

### Post by jonesyp on 2006-11-11
Aptitude, becuase it makes things so easy!  No missing depenencies!

---

### Post by araz on 2006-11-15
> **tribaal said:**
> Aptitude of course, because it resolves removal dependencies.

- trib'

I agree completely.

---

### Post by Freddy on 2006-11-15
apt-get, cause I can't spell aptitude :-).   /// Freddan

---

### Post by aysiu on 2006-11-15
> **Freddy said:**
> apt-get, cause I can't spell aptitude :-).   /// Freddan
That's the best reason I've heard yet!

---

### Post by skymt on 2006-11-15
> **bionnaki said:**
> I use apt-get because aptitude can be a pain to type sometimes. I dont care about purging dependencies.

I have it aliased:```
alias apt="sudo aptitude"
alias apti="apt install"
alias aptr="apt remove"
```

---

### Post by Freddy on 2006-11-17
> That's the best reason I've heard yet!
Well I cant help it, it's just so damn hard.

---

### Post by angrykeyboarder on 2006-11-18
cuz Aptitude is a newer application.  And in Linux we like to have 43 ways to accomplish a task. :-)

---

### Post by karamba_kid on 2006-11-18
This thread has made me want to switch to aptitude becuase disk space is important for me right now because I'm running low in /home.  If I marked all my packages as installed with the "automatic" flag in aptitude (I already have a simple script) and then went on and continued to use aptitude updates and package managment would I run in to many problems?

---

### Post by shining on 2006-11-18
> **karamba_kid said:**
> This thread has made me want to switch to aptitude becuase disk space is important for me right now because I'm running low in /home.  

Is your /home a separate partition?
In this case, using aptitude, which might remove some unneeded dependencies, won't have any effect to the space used in /home, only in /

---

### Post by karamba_kid on 2006-11-18
> **shining said:**
> Is your /home a separate partition?
In this case, using aptitude, which might remove some unneeded dependencies, won't have any effect to the space used in /home, only in /
It sure is. When I installed I decided to use LVM.

```
alex@trillville:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg1-root  7.9G  370M  7.2G   5% /
varrun                252M  144K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  144K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             177M   21M  147M  13% /boot
/dev/mapper/vg1-home   75G   56G   16G  79% /home
/dev/mapper/vg2-backup
                       73G   43G   27G  62% /media/hdb1
/dev/mapper/vg1-tmp   1.9G   36M  1.8G   2% /tmp
/dev/mapper/vg1-usr    22G  2.7G   18G  13% /usr
/dev/mapper/vg1-var   3.0G  741M  2.1G  26% /var
```

---

### Post by glotz on 2006-11-18
> **OffHand said:**
> It depends... sometimes aptitude is too radical.
> **kuja said:**
> apt-get, because aptitude tries to be too smart.
> **aysiu said:**
> *apt-get* for some specific cases where *aptitude* tries to act too smart.
Please do elaborate.

---

### Post by aysiu on 2006-11-18
> **glotz said:**
> Please do elaborate.
[Here](http://ubuntuforums.org/showthread.php?p=1761017#post1761017)'s an example.

---

### Post by ciscosurfer on 2006-11-18
> **Buffalo Soldier said:**
> apt-get. It's autoremove function seems to be working nicely in removing orphan packages in Edgy. I'm sure it will get better in ubuntu 7.04 :)You can deborphan/gtkorphan for that.

And my vote is for Aptitude -- it's really just a better front-end.  Of course, sometimes, apt-get is my preferred app as it doesn't pull in every extra recommended package(s) that I may or may not need.  

:-)

---

### Post by glotz on 2006-11-18
> **aysiu said:**
> [Here](http://ubuntuforums.org/showthread.php?p=1761017#post1761017)'s an example.
Interesting but I have to say I don't have a clue why would it have liked to uninstall those packages. I think this is relevant to this thread.

---

### Post by aysiu on 2006-11-18
> **glotz said:**
> Interesting but I have to say I don't have a clue why would it have liked to uninstall those packages. I think this is relevant to this thread.
It's trying to be smart about what packages to keep and which to remove.

Sometimes, as I said before, it tries to be a little *too* smart.

So for those situations, I'd use *apt-get* instead.

---

### Post by glotz on 2006-11-18
So it's basically random? Or do we know why?

---

### Post by ciscosurfer on 2006-11-18
> **aysiu said:**
> [Here]("http://ubuntuforums.org/showthread.php?p=1761017#post1761017")'s an example.Thanks for the nod, btw. :D

---

### Post by FyreBrand on 2006-11-18
> **aysiu said:**
> [Here](http://ubuntuforums.org/showthread.php?p=1761017#post1761017)'s an example.
Thanks for that example.  Several times I have had this problem.  I never knew that Synaptic/Adept could mess with aptitude. The worst time this happened was on a dist-upgrade from Dapper.  Since I had a lot of customization and I used adept with aptitude there was a lot of breakage.

If I understand properly mixing everyday use of apt-get and aptitude can cause dependency confusion between the two.

Does this also apply to the graphical front ends like adept and synaptic?  Mostly I've used aptitude but occasionally I've used adept or synaptic.  Would people say this is generally a bad practice?

---

### Post by moore.bryan on 2006-11-18
> **aysiu said:**
> *aptitude* in general for reasons explained here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

*apt-get* for some specific cases where *aptitude* tries to act too smart.
*i second this sentiment.  sometimes, aptitude is too smart for its own good.*

---

### Post by angrykeyboarder on 2006-11-19
```
You can deborphan/gtkorphan for that.
```

I've had problems with deborphan. It often wants to remove "orphaned" packages that aren't orphaned at all.

---

### Post by shining on 2006-11-19
> **FyreBrand said:**
> Thanks for that example.  Several times I have had this problem.  I never knew that Synaptic/Adept could mess with aptitude. The worst time this happened was on a dist-upgrade from Dapper.  Since I had a lot of customization and I used adept with aptitude there was a lot of breakage.

If I understand properly mixing everyday use of apt-get and aptitude can cause dependency confusion between the two.

Does this also apply to the graphical front ends like adept and synaptic?  Mostly I've used aptitude but occasionally I've used adept or synaptic.  Would people say this is generally a bad practice?

I also had this problem several times with aptitude, so I would also like to know more about it. I think it's indeed when mixing apt-get and aptitude usage, and I don't think there is the same problem with synaptic, but I'm really not sure. Maybe a bug should be reported.

---

### Post by namah on 2006-11-19
I find apt much easier to use

---

### Post by aysiu on 2006-11-19
> **namah said:**
> I find apt much easier to use
Can you explain what you mean by that? Give a few examples?

---

### Post by deanlinkous on 2006-11-19
less letters to type :)
apt-get

---

### Post by aysiu on 2006-11-19
> **deanlinkous said:**
> less letters to type :)
apt-get
I don't find that easier, actually.

*tq@zk%r* is also fewer letters than *aptitude*, but *aptitude* is easier for me to type because it's a real English word and has no punctuation in it.

---

### Post by shining on 2006-11-19
> **deanlinkous said:**
> less letters to type :)
apt-get

Actually no, apt-get is one more letter :)
apt-g<tab>
apti<tab>

---

### Post by mips on 2006-11-19
> **shining said:**
> Actually no, apt-get is one more letter :)
apt-g<tab>
apti<tab>

Very true ;)

---

### Post by deanlinkous on 2006-11-19
OUCH!
cause I am old school and apt was what I am use to! 

Okay, I make a promise to start using aptitiude from now on!

Anyone use wajig or gdebi very much?

---

### Post by shining on 2006-11-19
> **aysiu said:**
> Can you explain what you mean by that? Give a few examples?

I'm not sure what namah meant, but I originally thought aptitude only has its ncurses interface, and not a cli one also.
And I don't find aptitude ncurses interface very intuitive, compared to ncmpc or rtorrent for example, which I appreciate a lot.
So I found it easier to just type apt-cache search foo and apt-get install foo, or apt-get update/upgrade.
I only find out recently you could type the same with aptitude, so well, there is no difference :)

---

### Post by namah on 2006-11-20
> **shining said:**
> I'm not sure what namah meant, but I originally thought aptitude only has its ncurses interface, and not a cli one also.
And I don't find aptitude ncurses interface very intuitive, compared to ncmpc or rtorrent for example, which I appreciate a lot.
So I found it easier to just type apt-cache search foo and apt-get install foo, or apt-get update/upgrade.
I only find out recently you could type the same with aptitude, so well, there is no difference :)

Well yes, I guess I forgot about the cli option with aptitude. When I tried it I to was turned off by the ncurses interface and in the long run I'm just used to apt-get and prefer it out of habit.

---

### Post by aysiu on 2006-11-23
I recently found out about *apt-get autoremove **packagename***, and I have to say that makes me a fan of *apt-get* now, especially because of those weird situations where *aptitude* tries to be too smart (for some mysterious reason).

---

### Post by glotz on 2006-11-23
Couldn't find that on the man page?

---

### Post by aysiu on 2006-11-23
> **glotz said:**
> Couldn't find that on the man page?
Actually, no. Please let me know if you find it. ```
APT-GET(8)                                                          APT-GET(8)



NAME
       apt-get - APT package handling utility -- command-line interface

SYNOPSIS
       apt-get [-hvs] [-o=config string] [-c=file] {update | upgrade |
               dselect-upgrade | install pkg... | remove pkg... |
               source pkg... | build-dep pkg... | check | clean | autoclean}


DESCRIPTION
       apt-get is the command-line tool for handling packages, and may be conâ&#8364;
       sidered the userâ&#8364;&#8482;s "back-end" to other tools  using  the  APT  library.
       Several  "front-end"  interfaces  exist,  such as dselect(8), aptitude,
       synaptic, gnome-apt and wajig.


       Unless the -h, or --help option is given, one  of  the  commands  below
       must be present.


       update update  is  used  to  resynchronize the package index files from
              their sources. The indexes of  available  packages  are  fetched
              from the location(s) specified in /etc/apt/sources.list. For exâ&#8364;
              ample, when using a Debian archive, this command  retrieves  and
              scans  the  Packages.gz files, so that information about new and
              updated packages is available. An update should always  be  perâ&#8364;
              formed  before  an upgrade or dist-upgrade. Please be aware that
              the overall progress meter will be incorrect as the size of  the
              package files cannot be known in advance.


       upgrade
              upgrade  is  used to install the newest versions of all packages
              currently installed on the system from the sources enumerated in
              /etc/apt/sources.list.  Packages  currently  installed  with new
              versions available are retrieved and upgraded; under no  circumâ&#8364;
              stances  are  currently  installed packages removed, or packages
              not already installed retrieved and installed. New  versions  of
              currently  installed  packages  that  cannot be upgraded without
              changing the install status of another package will be  left  at
              their current version. An update must be performed first so that
              apt-get knows that new versions of packages are available.


       dselect-upgrade
              dselect-upgrade is used in conjunction with the traditional  Deâ&#8364;
              bian  packaging  front-end,  dselect(8). dselect-upgrade follows
              the changes made by dselect(8) to the Status field of  available
              packages,  and  performs  the  actions necessary to realize that
              state (for instance, the removal of old and the installation  of
              new packages).


       dist-upgrade
              dist-upgrade  in addition to performing the function of upgrade,
              also intelligently handles changing dependencies with  new  verâ&#8364;
              sions  of  packages;  apt-get  has a "smart" conflict resolution
              system, and it will attempt to upgrade the most important  packâ&#8364;
              ages  at  the  expense  of less important ones if necessary. The
              /etc/apt/sources.list file contains a  list  of  locations  from
              which  to  retrieve  desired package files. See also apt_preferâ&#8364;â&#8364;
              ences(5) for a mechanism for overriding the general settings for
              individual packages.


       install
              install  is followed by one or more packages desired for instalâ&#8364;
              lation. Each package is a package name, not  a  fully  qualified
              filename  (for  instance,  in  a  Debian GNU/Linux system, libc6
              would be the argument provided, not libc6_1.9.6-2.deb) All packâ&#8364;
              ages  required by the package(s) specified for installation will
              also be retrieved and installed. The /etc/apt/sources.list  file
              is  used to locate the desired packages. If a hyphen is appended
              to the package name (with no intervening space), the  identified
              package  will  be  removed  if it is installed. Similarly a plus
              sign can be used to designate a package to install. These latter
              features  may  be  used  to override decisions made by apt-getâ&#8364;&#8482;s
              conflict resolution system.

              A specific version of a package can be selected for installation
              by  following the package name with an equals and the version of
              the package to select. This will cause that version to be locatâ&#8364;
              ed  and selected for install. Alternatively a specific distribuâ&#8364;
              tion can be selected by following the package name with a  slash
              and the version of the distribution or the Archive name (stable,
              testing, unstable).

              Both of the version selection mechanisms can downgrade  packages
              and must be used with care.

              Finally,  the  apt_preferences(5) mechanism allows you to create
              an alternative installation policy for individual packages.

              If no package matches the given expression  and  the  expression
              contains one of â&#8364;&#8482;.â&#8364;&#8482;, â&#8364;&#8482;?â&#8364;&#8482; or â&#8364;&#8482;*â&#8364;&#8482; then it is assumed to be a POSIX
              regular expression, and it is applied to all  package  names  in
              the  database. Any matches are then installed (or removed). Note
              that matching is done by substring so  â&#8364;&#8482;lo.*â&#8364;&#8482;  matches  â&#8364;&#8482;how-loâ&#8364;&#8482;
              and  â&#8364;&#8482;lowestâ&#8364;&#8482;.  If this is undesired, anchor the regular expresâ&#8364;
              sion with a â&#8364;&#8482;^â&#8364;&#8482; or â&#8364;&#8482;$â&#8364;&#8482; character, or create a more specific regâ&#8364;
              ular expression.


       remove remove  is identical to install except that packages are removed
              instead of installed. If a plus sign is appended to the  package
              name (with no intervening space), the identified package will be
              installed instead of removed.


       source source causes apt-get to fetch source packages. APT will examine
              the  available packages to decide which source package to fetch.
              It will then find and download into the  current  directory  the
              newest available version of that source package. Source packages
              are tracked separately from binary  packages  via  deb-src  type
              lines  in the sources.list(5) file. This probably will mean that
              you will not get the same source as the  package  you  have  inâ&#8364;
              stalled  or  as  you  could install. If the --compile options is
              specified then the package will be compiled to a binary .deb usâ&#8364;
              ing  dpkg-buildpackage, if --download-only is specified then the
              source package will not be unpacked.

              A specific source version can be  retrieved  by  postfixing  the
              source  name with an equals and then the version to fetch, simiâ&#8364;
              lar to the mechanism used for the package  files.  This  enables
              exact matching of the source package name and version, implicitâ&#8364;
              ly enabling the APT::Get::Only-Source option.

              Note that source packages are not tracked like binary  packages,
              they  exist  only  in  the  current directory and are similar to
              downloading source tar balls.


       build-dep
              build-dep causes apt-get to install/remove packages  in  an  atâ&#8364;
              tempt to satisfy the build dependencies for a source package.


       check  check  is  a  diagnostic  tool; it updates the package cache and
              checks for broken dependencies.


       clean  clean clears out  the  local  repository  of  retrieved  package
              files.   It   removes   everything   but   the  lock  file  from
              /var/cache/apt/archives/  and  /var/cache/apt/archives/partial/.
              When  APT is used as a dselect(8) method, clean is run automatiâ&#8364;
              cally. Those who do not use dselect  will  likely  want  to  run
              apt-get clean from time to time to free up disk space.


       autoclean
              Like  clean,  autoclean  clears  out the local repository of reâ&#8364;
              trieved package files. The difference is that  it  only  removes
              package  files that can no longer be downloaded, and are largely
              useless. This allows a cache to be maintained over a long period
              without  it  growing  out  of  control. The configuration option
              APT::Clean-Installed will prevent installed packages from  being
              erased if it is set to off.


OPTIONS
       All  command  line options may be set using the configuration file, the
       descriptions indicate the configuration option to set. For boolean  opâ&#8364;
       tions  you  can  override  the  config  file  by  using  something like
       -f-,--no-f, -f=no or several other variations.


       -d, --download-only
              Download only; package files are only retrieved, not unpacked or
              installed. Configuration Item: APT::Get::Download-Only.


       -f, --fix-broken
              Fix;  attempt  to  correct  a system with broken dependencies in
              place. This option, when used with install/remove, can omit  any
              packages  to permit APT to deduce a likely solution. Any Package
              that are specified must completely correct the problem. The  opâ&#8364;
              tion is sometimes necessary when running APT for the first time;
              APT itself does not allow broken package dependencies  to  exist
              on a system. It is possible that a systemâ&#8364;&#8482;s dependency structure
              can be so corrupt as to require manual intervention (which  usuâ&#8364;
              ally  means  using dselect(8) or dpkg --remove to eliminate some
              of the offending packages). Use of this option together with  -m
              may  produce  an  error  in some situations. Configuration Item:
              APT::Get::Fix-Broken.


       -m, --ignore-missing, --fix-missing
              Ignore missing packages; If packages cannot be retrieved or fail
              the  integrity  check after retrieval (corrupted package files),
              hold back those packages and handle the result. Use of this  opâ&#8364;
              tion  together  with -f may produce an error in some situations.
              If a package is selected for installation (particularly if it is
              mentioned  on  the  command line) and it could not be downloaded
              then  it  will  be  silently  held  back.  Configuration   Item:
              APT::Get::Fix-Missing.


       --no-download
              Disables  downloading  of packages. This is best used with --igâ&#8364;â&#8364;
              nore-missing to force APT to use only the .debs it  has  already
              downloaded. Configuration Item: APT::Get::Download.


       -q, --quiet
              Quiet;  produces  output suitable for logging, omitting progress
              indicators. More qâ&#8364;&#8482;s will produce more quiet up to a maximum  of
              2.  You can also use -q=# to set the quiet level, overriding the
              configuration file. Note that quiet  level  2  implies  -y,  you
              should  never  use  -qq without a no-action modifier such as -d,
              --print-uris or -s as APT may decided to do  something  you  did
              not expect. Configuration Item: quiet.


       -s, --simulate, --just-print, --dry-run, --recon, --no-act
              No  action;  perform a simulation of events that would occur but
              do  not  actually  change  the   system.   Configuration   Item:
              APT::Get::Simulate.

              Simulate  prints  out  a series of lines each one representing a
              dpkg operation, Configure (Conf), Remove (Remv), Unpack  (Inst).
              Square  brackets  indicate broken packages with and empty set of
              square brackets  meaning  breaks  that  are  of  no  consequence
              (rare).


       -y, --yes, --assume-yes
              Automatic  yes to prompts; assume "yes" as answer to all prompts
              and run non-interactively. If an undesirable situation, such  as
              changing  a  held  package,  trying to install a unauthenticated
              package or removing an essential  package  occurs  then  apt-get
              will abort. Configuration Item: APT::Get::Assume-Yes.


       -u, --show-upgraded
              Show  upgraded  packages;  Print out a list of all packages that
              are to be upgraded. Configuration Item: APT::Get::Show-Upgraded.


       -V, --verbose-versions
              Show full versions for upgraded and installed packages. Configuâ&#8364;
              ration Item: APT::Get::Show-Versions.


       -b, --compile, --build
              Compile source packages after  downloading  them.  Configuration
              Item: APT::Get::Compile.


       --ignore-hold
              Ignore  package  Holds;  This  causes  apt-get  to ignore a hold
              placed on a package. This may  be  useful  in  conjunction  with
              dist-upgrade to override a large number of undesired holds. Conâ&#8364;
              figuration Item: APT::Ignore-Hold.


       --no-upgrade
              Do not upgrade packages; When used in conjunction with  install,
              no-upgrade  will prevent packages on the command line from being
              upgraded if they  are  already  installed.  Configuration  Item:
              APT::Get::Upgrade.


       --force-yes
              Force  yes;  This  is  a dangerous option that will cause apt to
              continue without prompting if it is doing something  potentially
              harmful.  It  should  not  be used except in very special situaâ&#8364;
              tions. Using force-yes can potentially destroy your system! Conâ&#8364;
              figuration Item: APT::Get::force-yes.


       --print-uris
              Instead of fetching the files to install their URIs are printed.
              Each URI will have the path, the destination file name, the size
              and  the  expected md5 hash. Note that the file name to write to
              will not always match the file name on the remote site! This alâ&#8364;
              so works with the source and update commands. When used with the
              update command the MD5 and size are not included, and it  is  up
              to  the  user  to decompress any compressed files. Configuration
              Item: APT::Get::Print-URIs.


       --purge
              Use purge instead of remove for anything that would be  removed.
              An  asterisk  ("*") will be displayed next to packages which are
              scheduled to be purged. Configuration Item: APT::Get::Purge.


       --reinstall
              Re-Install packages that are already installed and at the newest
              version. Configuration Item: APT::Get::ReInstall.


       --list-cleanup
              This  option  defaults  to  on, use --no-list-cleanup to turn it
              off. When on apt-get will automatically manage the  contents  of
              /var/lib/apt/lists to ensure that obsolete files are erased. The
              only reason to turn it off is  if  you  frequently  change  your
              source list. Configuration Item: APT::Get::List-Cleanup.


       -t, --target-release, --default-release
              This  option controls the default input to the policy engine, it
              creates a default pin at priority 990 using  the  specified  reâ&#8364;
              lease  string.  The  preferences  file may further override this
              setting. In short, this option lets you have simple control over
              which  distribution packages will be retrieved from. Some common
              examples might be -t â&#8364;â&#8364;&#8482;2.1*â&#8364;â&#8364;&#8482; or -t unstable. Configuration  Item:
              APT::Default-Release;  see  also  the  apt_preferences(5) manual
              page.


       --trivial-only
              Only perform operations that are â&#8364;&#8482;trivialâ&#8364;&#8482;. Logically  this  can
              be  considered  related to --assume-yes, where --assume-yes will
              answer yes to any prompt, --trivial-only will answer no. Configâ&#8364;
              uration Item: APT::Get::Trivial-Only.


       --no-remove
              If  any  packages  are  to be removed apt-get immediately aborts
              without prompting. Configuration Item: APT::Get::Remove.


       --only-source
              Only has meaning for the source and  build-dep  commands.  Indiâ&#8364;
              cates  that  the given source names are not to be mapped through
              the binary table. This means that if this option  is  specified,
              these  commands  will  only accept source package names as arguâ&#8364;
              ments, rather than accepting binary package names and looking up
              the    corresponding   source   package.   Configuration   Item:
              APT::Get::Only-Source.


       --diff-only, --tar-only
              Download only the diff or tar file of a source archive. Configuâ&#8364;
              ration Item: APT::Get::Diff-Only and APT::Get::Tar-Only.


       --arch-only
              Only process architecture-dependent build-dependencies. Configuâ&#8364;
              ration Item: APT::Get::Arch-Only.


       --allow-unauthenticated
              Ignore if packages canâ&#8364;&#8482;t be authenticated and donâ&#8364;&#8482;t prompt about
              it. This is usefull for tools like pbuilder. Configuration Item:
              APT::Get::AllowUnauthenticated.


       -h, --help
              Show a short usage summary.


       -v, --version
              Show the program version.


       -c, --config-file
              Configuration File; Specify a configuration  file  to  use.  The
              program  will  read the default configuration file and then this
              configuration file. See apt.conf(5) for syntax information.


       -o, --option
              Set a Configuration Option; This will set an arbitary configuraâ&#8364;
              tion option. The syntax is -o Foo::Bar=bar.


FILES
       /etc/apt/sources.list
              Locations   to   fetch   packages   from.   Configuration  Item:
              Dir::Etc::SourceList.


       /etc/apt/apt.conf
              APT configuration file. Configuration Item: Dir::Etc::Main.


       /etc/apt/apt.conf.d/
              APT   configuration   file   fragments    Configuration    Item:
              Dir::Etc::Parts.


       /etc/apt/preferences
              Version  preferences file. This is where you would specify "pinâ&#8364;
              ning", i.e. a preference to get certain packages from a separate
              source or from a different version of a distribution. Configuraâ&#8364;
              tion Item: Dir::Etc::Preferences.


       /var/cache/apt/archives/
              Storage area for retrieved package  files.  Configuration  Item:
              Dir::Cache::Archives.


       /var/cache/apt/archives/partial/
              Storage  area  for package files in transit. Configuration Item:
              Dir::Cache::Archives (implicit partial).


       /var/lib/apt/lists/
              Storage area for state information  for  each  package  resource
              specified     in     sources.list(5)     Configuration     Item:
              Dir::State::Lists.


       /var/lib/apt/lists/partial/
              Storage area for state  information  in  transit.  Configuration
              Item: Dir::State::Lists (implicit partial).


SEE ALSO
       apt-cache(8),   apt-cdrom(8),   dpkg(8),  dselect(8),  sources.list(5),
       apt.conf(5),    apt-config(8),    The    APT    Userâ&#8364;&#8482;s     guide     in
       /usr/share/doc/apt-doc/, apt_preferences(5), the APT Howto.


DIAGNOSTICS
       apt-get returns zero on normal operation, decimal 100 on error.


BUGS
       APT  bug  page: http://bugs.debian.org/src:apt. If you wish to report a
       bug in APT, please see /usr/share/doc/debian/bug-reporting.txt  or  the
       reportbug(1) command.


AUTHORS
       Jason Gunthorpe, APT team.



Linux                          29 February 2004                     APT-GET(8)
```

---

### Post by Circus-Killer on 2006-11-23
apt-get has never failed me.

---

### Post by glotz on 2006-11-23
> **aysiu said:**
> Actually, no. Please let me know if you find it. 

I meant I couldn't find it there. The question was, how did you learn about it? :D

---

### Post by aysiu on 2006-11-23
> **glotz said:**
> I meant I couldn't find it there. The question was, how did you learn about it? :D
I found it in [this thread](http://ubuntuforums.org/showthread.php?p=1795909#post1795909).

Yeah, I have no idea how people pick up these things when they're no in the *man* page...

---

### Post by glotz on 2006-11-23
Thanks. Brand new stuff I figure.

---

### Post by danielph on 2006-12-20
Just flicked through this thread as I was installing gnome on a server base install. I normally use aptitude as it seems to be better. Just as a comparision I have an example I thought I should share.

When using aptitude from a server install with just some xvideo drivers loaded I typed
```
 sudo aptitude install gnome-core
```427 newly installed packages and also a gamin dependency conflict.
118MB/154MB with 624MB used after unpacking.

```
 sudo apt-get install gnome-core
```297 packages newly installed
47.6MB/72.7MB with 371MB used after unpacking

Aptitude is pulling many more packages in on just installing gnome-core. A big difference. It makes me wonder if the apt-get is incomplete or aptitude is installing a lot of stuff I don't really need or want.
Can anyone explain this difference please?

---

### Post by Reshin on 2006-12-20
Aptitude marks recommended packages as dependencies

---

### Post by raul_ on 2006-12-20
sorry, i don't feel like reading 15 pages so i don't know if this has been brought up but...sometimes aptitude tells you to run an apt-get command when it can't handle something, so...i guess i would use aptitude most of the times, but it's not (maybe just yet?) 100% bullet proof, since it needs a little help from apt-get

---

### Post by danielph on 2006-12-20
> **Reshin said:**
> Aptitude marks recommended packages as dependenciesAh ha. Thanks for that.

A little research and you can use -R to stop this or change  ~/aptitude/config (/etc/apt/apt.conf in apt)

---

### Post by dbbolton on 2006-12-20
aptitude.

---

### Post by mcduck on 2006-12-20
I've had some troubles using Aptitude, for example the last time I used it to install Kubuntu-desktop and day after that tried to remove KDE again Aptitude wanted to remove about half of my system.

I like apt-get, deborphan has helped me to remove orphaned dependencies and with the apt-get's new autoremove feature I don't really see any reason to use Aptitude.

---

### Post by rocknrolf77 on 2006-12-22
What do you use. apt-get or aptitude ? Aptitude handles dependencies better so i just wondered how many people use apt-get and why?  :)

---

### Post by Reshin on 2006-12-22
[http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get](http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get)

---

### Post by rocknrolf77 on 2006-12-22
> **Reshin said:**
> [http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get](http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get)

Searched for several things about aptitude vs apt-get. Haven't seen that poll. :) The forum is getting a lot of users and threads now. The bigger the forum the more ubuntu users so nothing negative with that, just that searching the threads gives you (maybe too many hits).

---

### Post by AlanRogers on 2006-12-22
I use Aptitude at the command line, which I usually use if I'm trying out anything new, so I can uninstall with impunity. If Aptitude had a good graphical interface, I wouldn't use anything else.

---

### Post by aysiu on 2006-12-22
> **Reshin said:**
> [http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get](http://www.ubuntuforums.org/showthread.php?t=294135&highlight=aptitude+vs+apt-get)
Merged.

---

### Post by qalimas on 2006-12-22
I favor aptitude, and manage my applications via Konsole.  Something I like about Aptitude is typing just 'sudo aptitude' in a server install gives you a sort of GUIish frontend, and if you have the program that lets you use the mouse in terminal, it's pretty nifty =)

---

### Post by AlanRogers on 2006-12-23
> **aysiu said:**
> Well, for some people, it's a hard drive space issue, especially if you have a drive or partition that's 6 GB or lessI'm one of those - running Ubuntu 6.06 on a 400Mhz, 512MB, 8GB machine and it runs fine. I'll be starting another thread to hopefully get an answer to the pickle I've now put myself in. I prefer aptitude while I'm learning but I'm not afraid of the CLI. I've already reinstalled several times, as I try out different configurations, including a text-only install server and adding packages on top.

---

### Post by aysiu on 2007-01-10
Now that I'm using Edgy, I think I'm going to go back to using *apt-get* instead of *aptitude*. Sometimes *aptitude* tries to be too "smart" and remove packages I don't want it to remove. And now (as of Edgy) *apt-get* has the *autoremove* option to remove unused dependencies.

---

### Post by Quillz on 2007-01-10
I prefer apt-get.

---

### Post by Pobega on 2007-01-10
I personally **always** use aptitude, I'm very anal when it comes to unused libraries on my computer and I'd rather have them taken off than wasting space.

---

### Post by FyreBrand on 2007-01-12
I'm testing out how apt-get works for me.  I did a reinstall and have only used apt-get with no aptitude or adept installer.  I've never really used the ncurses interface of aptitude.  I just like how it functions in the konsole.

These are couple of observations I've made so far:
1. Aptitude is much friendlier to new users.  It makes all the decisions for you and seems to allow greater flexibility with suggested and recommended packages.

2. It seems apt-get installs fewer packages as it doesn't automatically include recommended or suggested packages, but only what's required for the installed packages functioning.  I like this because it doesn't install a bunch of unnecessary packages.  I don't like it because I'm often not sure what recommends or suggests I should manually add if any.  I still don't know what the difference between a suggest and a recommend is so I need to learn that.  Thus why I feel it's a little less gentle for the less experienced person.

3. I haven't found a way to search packages using apt-get.  I just read the man pages so maybe more complete documentation will explain how.  So I still use "aptitude search" and "aptitude show" to find package names and descriptions.  If apt-get doesn't have a search feature I would consider that a big drawback.  I certainly question whether it has super cow powers if it lacks search. (just kidding)

4. As far as I can tell aptitude lacks the build feature that apt-get has.  I really like that feature.

I'm still not very comfortable with apt-get, but it's only been a few days so I have to give it more time.

---

### Post by rai4shu2 on 2007-01-12
You use apt-cache to search for packages, dpkg -S to search for files in the packages.

---

### Post by FyreBrand on 2007-01-12
rai4shu2 - Thanks for the information.  I like that command a lot.  It provides a lot of information.

---

### Post by Nikron on 2007-03-08
Personally, I use apt-get since it has super moo cow powers.  Which one do you use more often?  Or which one did you use for which kind of tasks?

---

### Post by Pugwash on 2007-03-08
I use aptitude, I read somewhere that its better. No idea why though.

---

### Post by Nikron on 2007-03-08
> **Pugwash said:**
> I use aptitude, I read somewhere that its better. No idea why though.

Well, it is a higher level interface.  I suppose that makes it easier to use.

---

### Post by TheRingmaster on 2007-03-08
aptitude remembers dependencies. so when you want to install a program with lots of dependencies like kde, you have a MUCH easier time uninstalling it later.

---

### Post by raublekick on 2007-03-08
i just stick with apt-get. i know aptitude has better dependancy handling, but I generally don't install things that require its use (such as removing KDE).

---

### Post by aysiu on 2007-03-08
I've merged this with the other thread on the same topic.

I'm keeping the new poll, though, since *apt-get* now (as of Edgy Eft) has the *autoremove* feature, which puts it on par with *aptitude*.

For posterity, I've attached the old poll, though, that got lost in the merger.

---

### Post by FyreBrand on 2007-03-08
Thanks for resurrecting this thread.  I've been thinking about posting back in it for a while now.

I started out using aptitude because it simplifies the dependency process.  On install, by default, it pulls in recommends and maybe suggests (I'm not sure about that part though).  This is really helpful for a newer user because it's a lot just to get familiar with package management let alone try and understand dependencies.  It does handle package removal and cleaning okay, but sometimes it's a little too smart for it's own good.  When this happens it wants to remove important packages and can even prevent new package installation until it's had it's "problem" solved.

When I first read this thread I decided to start using apt-get as an experiment and to compare.  At first I didn't like it because it doesn't automatically install recommends and suggests.  That meant I had to make decisions about what additional packages to install.  This made it harder, but in the end I learn more about the packages I choose to install.  It also means I install a lot less baggage packages.  This started to really sell me on apt-get.

For example I installed a very simple development web server.  It was a standard Apache2, PHP, MySQL stack.  When I installed this with aptitude a ton of extra packages I didn't need were installed such as postfix.  I didn't want or need a mail server and even though I configured it not to do anything it was still there taking up space and running as a service taking up resources.  When I install the AMP stack with apt-get mailx and postfix are recommended packages and don't get installed by default.  In fact there are several other packages that don't get installed that I don't need.

You can configure the apt config file to change any default behavior but the fact is that apt-get uses a more conservative install philosophy and I like that.  It only installs the packages you need to actually get the application running.

Apt-get also does autoremove and purging quite well.  I've had far fewer dependency glitches with apt-get and as a result smoother dist-upgrades.

One thing I still use aptitude for is searching.  Aptitude has a great searching tool.  Apt-cache is good but aptitude offers a few more pieces of information.  When you "aptitude search" a package I like how it tells you the install status of that package.  It also searches packages a little more restrictively and I like that because the list is shorter and usually with more relevant results.  When you "aptitude show" a package it not only tells you all the details apt-cache has, but also if the package is installed.  I do use apt-cache but normally only to compare what I find with aptitude's search.

---

### Post by BarfBag on 2007-03-09
I prefer apt-get over aptitude.

Aptitude claims that it handles dependencies better, but from my experience - it tries too hard.  I've had quite a few packages that didn't run after upgrading/installing them with it.

---

### Post by mal on 2007-03-09
This has been a great discussion, but I'd like to throw in a new question:

Since Synaptic is the Ubuntu standard GUI installation tool, is there any way to configure it to behave like Aptitude (or apt-get -autoremove)?

I find Synaptic useful when searching for packages but often use apt-get or aptitude for installing and uninstalling from the command line.  It would be good if Synaptic would also clean up unused dependancies like Aptitude does.


Mal

---

### Post by FyreBrand on 2007-03-09
> **mal said:**
> This has been a great discussion, but I'd like to throw in a new question:

Since Synaptic is the Ubuntu standard GUI installation tool, is there any way to configure it to behave like Aptitude (or apt-get -autoremove)?

I find Synaptic useful when searching for packages but often use apt-get or aptitude for installing and uninstalling from the command line.  It would be good if Synaptic would also clean up unused dependancies like Aptitude does.


MalIt's been a while since I've used Synaptic, but I think the option "completely remove" will do that.  Try this as a test.  Find an application with only a few dependencies that aren't tied to other apps.  Install it with Synaptic and then select "completely remove" and see if it removes the depends as well.  I would like to know if it works.

---

### Post by Quillz on 2007-03-09
I've never tried Aptitude, actually. I might use it over Adept if the latter keeps timing out on large updates, though.

---

### Post by mal on 2007-03-09
> **FyreBrand said:**
> It's been a while since I've used Synaptic, but I think the option "completely remove" will do that.  Try this as a test.  Find an application with only a few dependencies that aren't tied to other apps.  Install it with Synaptic and then select "completely remove" and see if it removes the depends as well.  I would like to know if it works.

FyreBrand,

You might be right, but I thought "completely remove" was equivalent to the "apt-get --purge remove" option and that this removes all configuration files, etc. associated with each package.

I guess I should do some experimenting to figure out how Synaptic behaves with the different available options.

Mal

---

### Post by FyreBrand on 2007-03-09
> **mal said:**
> FyreBrand,

You might be right, but I thought "completely remove" was equivalent to the "apt-get --purge remove" option and that this removes all configuration files, etc. associated with each package.

I guess I should do some experimenting to figure out how Synaptic behaves with the different available options.

MalYeah that could be true.  I can't remember, but if you feel like doing the experiment I would like to hear the results.  Like I said it's been quite a while since I've used Synaptic.

---

### Post by yigal.weinstein on 2007-03-09
aysiu geese I just knee jerk voted for aptitude but upon reading the dependency considerations in the new apt-get I think its a toss up and who doesn't want super cow powers.  Maybe I will have to start using apt-get.  Does apt-cache have as good an ability as aptitude search for finding packages with given traits?

---

### Post by Enigmus on 2007-03-09
I use apt-get just about all the time. I have only used Aptitude twice. Still, if I want to view packages by a list if I don't know for sure on something, then yeah. I'd agree that Aptitude has it's pluses. But since I usually know what I want, I just find apt-get to be a lot easier.

---

### Post by Ramses de Norre on 2007-03-09
The only disadvantage I know is the already pointed out meta-package removal thing (which mostly is an advantage, but sometimes a disadvantage...)
As you can see, when I want to remove ubuntu-desktop (or any of it's packages) other packages I frequently use like OOo, gedit, gconf-editor, ... are also removed.

So I always use aptitude instead when removing packages as ubuntu-desktop.
```
ramses@icarus:~$ sudo aptitude remove ubuntu-desktop 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  apport apport-gtk at-spi avahi-daemon binfmt-support bittorrent 
  bluez-cups bluez-pin bluez-utils brltty brltty-x11 bsh bug-buddy 
  cli-common contact-lookup-applet cupsys-driver-gutenprint dc 
  diveintopython edgy-community-wallpapers edgy-gdm-themes 
  edgy-session-splashes edgy-wallpapers ekiga eog esound evolution-exchange 
  evolution-webcal example-content f-spot festival festlex-cmu 
  festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support 
  foo2zjs foomatic-db-hpijs fping gaim gaim-data gcalctool gconf-editor 
  gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python 
  gnome-accessibility-themes gnome-btdownload gnome-cups-manager 
  gnome-keyring-manager gnome-mag gnome-nettool gnome-orca 
  gnome-screensaver gnome-spell gnome-system-tools gnome-themes 
  gnome-volume-manager gray-theme gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gthumb gtk2-engines gtk2-engines-ubuntulooks 
  gucharmap hal-device-manager hotkey-setup hpijs hplip hplip-data 
  human-cursors-theme human-gtk-theme human-icon-theme human-theme 
  hwdb-client-common hwdb-client-gnome industrialtango-theme 
  landscape-client language-selector language-selector-common 
  legacyhuman-theme lftp libatspi1.0-0 libavahi-core4 libbeecrypt6 
  libbluetooth2 libbrlapi1 libbtctl4 libdaemon0 libdbus-1-cil libestools1.2 
  libgadu3 libgconf2.0-cil libgimp2.0 libglade2.0-cil libglew1 
  libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-mag2 
  libgnome-speech3 libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a 
  libgnomevfs2-bin libgpod0 libgtk2.0-cil libgutenprint2 libgutenprintui2-1 
  libhsqldb-java libicu34 libjline-java libmdbtools libmeanwhile1 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libopal-2.2.0 
  libopenobex-1.0-0 libportaudio0 libpt-1.10.0 libpt-plugins-alsa 
  libpt-plugins-v4l libpt-plugins-v4l2 librpm4 libscim8c2a libsensors3 
  libservlet2.3-java libsnmp-base libsnmp9 libsqlite3-0 libstlport4.6c2 
  libuniconf4.2 libwpd8c2a libwvstreams4.2-base libwvstreams4.2-extras 
  libxalan2-java libxevie1 libxmlsec1 libxmlsec1-nss libxmlsec1-openssl 
  libxplc0.3.13 libxt-java min12xxw mono-common mono-gac mono-jit 
  mono-runtime nautilus-sendto onboard openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer outdoors-theme 
  pkg-config pnm2ppa powernowd python-apport-utils python-at-spi 
  python-problem-report python-uno python-virtkey python-xml rdesktop 
  readahead resilience-theme rhythmbox rpm rss-glx scim scim-gtk2-immodule 
  scim-modules-socket screen screensaver-default-images serpentine 
  silicon-theme slocate sound-juicer ssh-askpass-gnome tangerine-icon-theme 
  tango-icon-theme tango-icon-theme-common tomboy totem tsclient 
  ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk 
  ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts 
  ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho 
  ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-oriya-fonts 
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg 
  ubuntu-artwork ubuntu-docs ubuntu-sounds update-notifier usplash 
  usplash-theme-ubuntu vino vnc-common whois wvdial xcursor-themes 
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xorg xsane 
  xsane-common xscreensaver-data xscreensaver-gl xvncviewer zip 
The following packages will be REMOVED:
  ubuntu-desktop 
0 packages upgraded, 0 newly installed, 253 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 765MB will be freed.
Do you want to continue? [Y/n/?] 


```

PS: when you count the keystrokes needed to install a package when using tab completion, you'll see you type less with aptitude ;)

---

### Post by igknighted on 2007-03-09
Now that apt-get has autoremove, whats really the difference?  Aside from it takes one more step to get rid of the orphaned dependencies?

---

### Post by aysiu on 2007-03-09
> **igknighted said:**
> Now that apt-get has autoremove, whats really the difference?  Aside from it takes one more step to get rid of the orphaned dependencies?
Not everyone's using Edgy Eft. Many people are still on 6.06 (Dapper Drake).

---

### Post by Nikron on 2007-03-09
The only problem I've ever had with apt-get is when I removed xbindkeys once.  It for some reason wanted to auto remove my network-manager package... which I obviously need =P

Aptitude I dislike because it tends to spit out more text than apt-get, which can get annoying.

---

### Post by Izkata on 2008-03-14
> **aysiu said:**
> Not everyone's using Edgy Eft. Many people are still on 6.06 (Dapper Drake).

I feel this thread deserves a bump, as I just ran across [this](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux) post on Lifehacker.  They're using aptitude in this post, whereas they've previously always used apt-get....

So I checked something out:

```
izkata@Izz:~$ sudo aptitude install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  dpatch fakeroot kbuild libxalan110 libxerces27 module-assistant 
  patchutils virtualbox-ose-modules-2.6.22-14-generic virtualbox-ose-source 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en 
The following NEW packages will be installed:
  dpatch fakeroot kbuild libxalan110 libxerces27 module-assistant 
  patchutils virtualbox-ose virtualbox-ose-modules-2.6.22-14-generic 
  virtualbox-ose-source 
0 packages upgraded, 10 newly installed, 0 to remove and 2 not upgraded.
Need to get 9614kB of archives. After unpacking 31.7MB will be used.
Do you want to continue? [Y/n/?] n

```

```
izkata@Izz:~$ sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox-ose-modules-2.6.22-14-generic instead of virtualbox-ose-modules-generic
The following extra packages will be installed:
  libxalan110 libxerces27 virtualbox-ose-modules-2.6.22-14-generic
Suggested packages:
  xalan
Recommended packages:
  virtualbox-ose-source
The following NEW packages will be installed:
  libxalan110 libxerces27 virtualbox-ose
  virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 8574kB of archives.
After unpacking 28.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n

```

So...  If package tracking for removing packages was the only difference (which was added to apt-get in Edgy anyway), why is there a difference here?  This thread is still one of the top Google results for the search:  "apt-get" aptitude

EDIT:  Okay, semi-idiotic me.  This thread is 20 pages and the last page didn't really answer my question, which is why I made this post - but my question was partially answered on page 19 by FyreBrand.

I only say "partially", though, because even adding the packages apt-get suggests to the install line...  The package names match up perfectly, but the amount to be downloaded and the space it will take up after unpacking still differs.  (Granted it's only by a very tiny amount, but I still wonder why as they both should be doing the same thing at that point)

---

### Post by aysiu on 2008-03-14
> **Izkata said:**
> I feel this thread deserves a bump, as I just ran across [this](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux) post on Lifehacker.  They're using aptitude in this post, whereas they've previously always used apt-get....

So I checked something out:

```
izkata@Izz:~$ sudo aptitude install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  dpatch fakeroot kbuild libxalan110 libxerces27 module-assistant 
  patchutils virtualbox-ose-modules-2.6.22-14-generic virtualbox-ose-source 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en 
The following NEW packages will be installed:
  dpatch fakeroot kbuild libxalan110 libxerces27 module-assistant 
  patchutils virtualbox-ose virtualbox-ose-modules-2.6.22-14-generic 
  virtualbox-ose-source 
0 packages upgraded, 10 newly installed, 0 to remove and 2 not upgraded.
Need to get 9614kB of archives. After unpacking 31.7MB will be used.
Do you want to continue? [Y/n/?] n

```

```
izkata@Izz:~$ sudo apt-get install virtualbox-ose virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox-ose-modules-2.6.22-14-generic instead of virtualbox-ose-modules-generic
The following extra packages will be installed:
  libxalan110 libxerces27 virtualbox-ose-modules-2.6.22-14-generic
Suggested packages:
  xalan
Recommended packages:
  virtualbox-ose-source
The following NEW packages will be installed:
  libxalan110 libxerces27 virtualbox-ose
  virtualbox-ose-modules-2.6.22-14-generic
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 8574kB of archives.
After unpacking 28.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n

```

So...  If package tracking for removing packages was the only difference (which was added to apt-get in Edgy anyway), why is there a difference here?  This thread is still one of the top Google results for the search:  "apt-get" aptitude
I'm not sure what you're trying to say. In your examples, you didn't remove anything--only installed (or were about to install).

In any case, most of the advantages of *aptitude* have been made moot by the advent of *autoremove* to *apt-get*, as of Ubuntu 6.10 (a year and a half ago).

---

### Post by koenn on 2008-03-14
I didn't read the 194 posts here, so maybe this has been mentioned before : 1 downside of aptitude compared to apt-get is that aptitude by default treats "recommends" (recommended packages, not real dependencies but something along the lines of 'if you install xyz, you probably also going to want abc and dfg) as dependencies, 
This is probably a configurable option that happens to be on by default, so maybe it doesn't count as a downside to apt, but it can unexpectedly  pull in a lot of extra packages if you don't pay attention. 

You can make apt-get behave the same way by calling it with the --with-recommends option

---

### Post by Unanimated on 2008-08-21
I just use apt-get more because it's easier to type than aptitude. With aptitude I sort of have to think about what I'm typing, but with apt-get I know what I'm typing, so I think it's a little faster. I also have localepurge installed, so I really don't need to worry about dependency removal.

---

### Post by cardinals_fan on 2008-08-21
I vote slapt-get :)

---

### Post by doorknob60 on 2008-08-21
Aptitude (Ooh I tied up the poll 69-69 :lolflag:). I can install stuff and when I remove it later (if I do), then it makes sure all the crap that came with it goes away, assuming I don't need it for other programs. It just works better, and apt-get can cause headaches with that sort of thing (uninstalling DE's...yeah). Also, it's recommended by the Debian devs over apt-get :)

---

### Post by Vivaldi Gloria on 2008-08-21
But no one uses apt-get on its own. You can't even search with it. You also use the other apt-* tools: apt-cache, apt-file, apt-rdepends, apt-key etc. Can aptitude match all these? I doubt that.

Btw, how do you do the following with aptitude?

```
apt-rdepends <package>
```

List all recursive dependencies, i.e. list deps, deps of deps, ... so on.

```
sudo apt-get build-dep <package>
```

Install packages needed to install <package> from source.

```
apt-get --print-uris install <package>
```

Get the download adress of the package. 

```
apt-cache dump
```

Gives info about ALL packages.

```
apt-cache stats
```

All about package numbers.

```
apt-cache showsrc <package>
```

Deps & build deps.

---

