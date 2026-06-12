---
title: "What's your preferred method of installing software in Ubuntu?"
date: 2005-12-04
forum: The Cafe
---

### Post by aysiu on 2005-12-04
I'm deliberately making this not a multi-choice poll (you get only one option) because I want to know the **preferred** choice. I've tried to cover as many I can think of, though, and I plopped in an "other" just to be comprehensive.

You can take *preferred* however you like it--"If I had a choice, I would use..." or "I most frequently use..."

---

### Post by atoponce on 2005-12-04
I definitley use Synaptic as my preferred choice for a couple of reasons.  First, I don't always know the correct name of the software that I need to install, so searching in Synaptic helps.  Also, when installing software with Synaptic, I can see other versions or different software that I may be interested in installing.  Case in point, when installing Java, not only did I not know the proper apt-get name, but I stumbled across Jython which interested me, and got installed as well.  Second choice would definitely be apt-get as it is easy to pull up a terminal, and type it in.  It is quick and painless.

---

### Post by aysiu on 2005-12-04
I forgot to mention mine: apt-get. Preferred in the sense that if I have a choice, I would use it. It's quick, and it's fun (I like typing instead of using the mouse, and I get to see all the text scroll by for everything).

After that would be Synaptic Package Manager if I don't know the exact name of what I'm looking for.

Luckily for me, I rarely need a package that exists outside the Ubuntu repositories. My needs are very basic. I need email, internet, some light word processing, and music. I do a bit of terrible website design, but that's all hand-coded.

---

### Post by ad noiseam on 2005-12-04
Synaptic for me, as I don't like to type things in the terminal and I use Gnome.

KPackage (which I didn't know about) seems to be the exact same thing for KDE, though, votes for both might actually reflect the same wishes.

---

### Post by aysiu on 2005-12-04
[QUOTE=ad noiseam]
KPackage (which I didn't know about) seems to be the exact same thing for KDE, though, votes for both might actually reflect the same wishes.[/QUOTE] I think KPackage, Adept, Add Applications, and Synaptic are really all the same thing--graphical (and searchable) frontends for apt-get. They are different, though, in terms of their interface.

---

### Post by Wolki on 2005-12-04
Synaptic. It's not optimal, but powerful, and I like that. apt-get is nice if I know the exact name, and if I'm in the command line anyway. gnome-app-install is where I look first if I'm looking for a graphical application, though.

---

### Post by Koobi on 2005-12-04
i use apt-get when i know exactly what i want to install. my second preference is aptitude since it apparently handles dependencies better.
my last choice is synaptic but i avoid it as much as possible since it seems to be the least safest choice, dependencies wise, anyway.

---

### Post by arpunk on 2005-12-04
[QUOTE=Wolki]Synaptic. It's not optimal, but powerful, and I like that. apt-get is nice if I know the exact name, and if I'm in the command line anyway. gnome-app-install is where I look first if I'm looking for a graphical application, though.[/QUOTE]
You can use apt-cache for knowing the exact name. For me its faster when i do it in a terminal, so i rather use apt-get.

---

### Post by az on 2005-12-04
I always pimp Synaptic to new users, becaus ehtat it the way it shoudl be done.  You should not have to drop down to a shell to get things done.

I, however, only use really old hardware and I find apt-get quicker.  Not to mention that I often install boxes without a GUI.

You did not mention dselect.  The great thing about dselect is that you can select a meta package, and then remove some of it's dependancies and it will still keep the others.  Aptitude and Synaptic all remove the dependancies once the meta package is on the list.  Dslect does not work that and ans that is it's advantage for that particular situation.

---

### Post by Kvark on 2005-12-04
My perferred way when I have an idea of what I'm looking for is "apt-cache search <keyword>", "apt-cache show <package>" and "sudo apt-get install <package>".

But when I'm not sure what I want then it's time to click around in Synaptic until I stumble across something interesting.

---

### Post by Vlammetje on 2005-12-04
synaptic, because I can look for apps of which I do not know the name (most apps in my case) and because it sorts dependencies where possible.

---

### Post by Koobi on 2005-12-04
[QUOTE=Kvark]My perferred way when I have an idea of what I'm looking for is "apt-cache search <keyword>", "apt-cache show <package>" and "sudo apt-get install <package>".[/QUOTE]


thats good info. i didn't know this. it should be on ubuntuguide.org

---

### Post by SilentCacophony on 2005-12-04
As the first (and as yet only) to choose aptitude, I may as well pipe in. :)

I prefer it for several reasons. AFAIK, it still does a better job of removing otherwise unneeded dependencies when uninstalling apps, without the need for another app to do that.

It can be used very much like apt-get for quick use of installing known package names, and can also be run in full-screen interactive mode for browsing the package lists.

Being a console tool also makes it rather low on resource usage, and I can fly through name searches and such on it, where graphical tools like Synaptic leave me feeling impatient.

Overall, I find it to be a rather well-rounded tool for software installation, and I use it exclusively for installations, removals, and updating.

---

### Post by Virak on 2005-12-04
Synaptic, although I occasionally use apt-get when I already know the name of the package I'm looking for, and I've also got a few programs compiled from source.

---

### Post by aysiu on 2005-12-04
[QUOTE=azz]
You did not mention dselect.[/QUOTE] I didn't really know about dselect, but thanks for mentioning it. In any case, I think the max options on a poll is ten items, so I'm hoping "other" will cover it.

---

### Post by az on 2005-12-04
[QUOTE=Koobi]thats good info. i didn't know this. it should be on ubuntuguide.org[/QUOTE]
It is on the wiki documentation page:

[https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo)
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

[QUOTE=aysiu]I didn't really know about dselect, but thanks for mentioning it. In any case, I think the max options on a poll is ten items, so I'm hoping "other" will cover it.[/QUOTE]

It is kinda like using vi instead of nano.  Geeky.

---

### Post by Stormy Eyes on 2005-12-04
I use apt-get. Always have, always will.

---

### Post by jadugarr on 2005-12-04
Aptitude all the way.  

Of course I compile all packages not available in a repo or as a debian package.

---

### Post by newbie2 on 2005-12-04
huh? nobody for automatix?...not good then?
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by GreyFox503 on 2005-12-04
Definitely Synaptic, because of the organization and searching abilities to find software.

One poll option I didn't see:  some programs you can download come compiled, but still have an installer you run through (like firefox, UT2004, and Enemy Territory).   They are associated with no package manager, but can still install themselves, similar to Windows.

---

### Post by ssam on 2005-12-04
synaptic becuase i can't spell

---

### Post by qalimas on 2005-12-04
Most often, I use synaptic, but if I know what I'm going for and I know the name, the terminal and the apt-get command are fine.  I mainly use Synaptic just to browse and see if anything catches my eye ;)

---

### Post by arnieboy on 2005-12-04
automatix cannot be compared with apt-get or synaptic.. it uses the power of apt-get, dpkg and wget (among others) to get **a few things** done quickly and efficiently. Not a well thought of poll..
Automatix does not have its own installation engine.. well for that matter so doesnt synaptic (which is just a GUI wrapper on apt-get)... its like comparing apples and oranges..

---

### Post by erikpiper on 2005-12-04
Definatley apt-get,
but synaptic for window shopping!

---

### Post by r4ik on 2005-12-04
Apt-get when i know what i want and howto.
Synaptic for some searching around when i dont.
Automatix just works.

---

### Post by darkmatter on 2005-12-04
apt-get and compile....I'm a CLI child...

---

### Post by 23meg on 2005-12-04
I find apt more practical, but after my fresh install I've started using just synaptic, because I like the fact that it keeps a history of everything I install/remove. If I found a way to keep track of every install/uninstall/upgrade performed with apt-get along with exact date and time, I'd go back to apt.

And whenever I compile something I use checkinstall.

---

### Post by Suzan on 2005-12-04
I prefer Synaptic. It's easy, it works.

And - I like GUIs! ;-)

---

### Post by Biased turkey on 2005-12-04
Synaptic

---

