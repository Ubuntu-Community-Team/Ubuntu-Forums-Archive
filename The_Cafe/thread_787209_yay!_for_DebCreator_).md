---
title: "yay! for DebCreator :)"
date: 2008-05-08
forum: The Cafe
---

### Post by madjr on 2008-05-08
[IMG]http://www.cmsoft.net/debcreator/screenshots/debcreator-0.3.9.4-1.png[/IMG]

[IMG]http://www.cmsoft.net/debcreator/screenshots/debcreator-0.3.9.4-5.png[/IMG]


oh yeah, this why ubuntu rocks!

less excuses everyday for soft devs to not create and include **.deb** packages

[http://www.cmsoft.net/debcreator/#screenshots](http://www.cmsoft.net/debcreator/#screenshots)



ps. the developer is looking for someone to help him create a mockup for the control fields

> Mock-up
I really don't like how the control fields are presented to the user. If you have any idea how to do this without adding complexity to the user interface than just send your mock-up to bobyjoe0_[at]_yahoo.fr

---

### Post by kindofabuzz on 2008-05-08
checkinstall does the same thing.

./configure
make
sudo checkinstall

boom, you have a .deb

---

### Post by fktt on 2008-05-08
> **kindofabuzz said:**
> checkinstall does the same thing.

yeah, and thats all fine and dandy, but now theres an option for those winy people who only want to use guis. :p

---

### Post by 23meg on 2008-05-08
> **kindofabuzz said:**
> checkinstall does the same thing.

./configure
make
sudo checkinstall

boom, you have a .deb

..which doesn't even handle dependencies and will do all sorts of nasty things to people's systems if you distribute it as is.

I haven't looked into DebCreator, but my experience with other GUI tools for creating packages is that they do not encourage their users to respect the packaging policies for the major distributions whose package formats they create, let alone making them mandatory. The usual result is bad packaging that does more harm than good ("My upgrade failed; Ubuntu is not ready for the desktop!!!11").

I will not argue that proper packaging cannot be done via a GUI, as I'm not very familiar with the existing GUI tools, but the nature of the job is one that requires a level of care, standards adherence and technical knowledge that goes beyond the kind of "ease" that traditional GUI tools are meant to provide. As [LaserJock]("http://ubuntuforums.org/member.php?u=18410") [once said]("http://ubuntuforums.org/showpost.php?p=4135400&postcount=34"), in the light of the fact that "the Debian Policy manual, which all Debian and Ubuntu official packages must adhere to, is 152 pages long and often requires human judgment", the concept of "easily" creating healthy packages "with a few clicks", while sounding attractive, needs to be met with a dose of skepticism. 

It's also highly debatable whether entering the exact same depends and build-depends syntax (which one is supposed to know in the first place) into a GUI text box is any "easier" than typing it up in a text editor.

---

### Post by gsmanners on 2008-05-08
DebCreator is fairly lacking. In particular, it doesn't seem to have the ability to do custom configuration or custom making (which I need most of the time). For my purposes, checkinstall does a much better job.

---

### Post by Changturkey on 2008-05-08
Oh wow, thank you for the great find.

---

### Post by qazwsx on 2008-05-08
> **madjr said:**
> 
[IMG]http://www.cmsoft.net/debcreator/screenshots/debcreator-0.3.9.4-5.png[/IMG]

:confused:
Package creators may prefer little bit more verbosity :).

I have done couple of checkinstall packages that have caused troubles on my machine.

I have great respect towards real packagers. I assume it is not easy job and should never be. One bad package and you may have system wide problems.

---

### Post by -grubby on 2008-05-08
Well for those that argue against this; I think it'd be a great tool for some lesser-experienced users to use on their private computers, and not release to the public

---

### Post by the yawner on 2008-05-08
> **kindofabuzz said:**
> checkinstall does the same thing.

./configure
make
sudo checkinstall

boom, you have a .deb

I thought checkinstall is only used so that you can easily uninstall a compiled software the apt way? Correct me if I'm wrong.

---

### Post by barbedsaber on 2008-05-08
From website

> Download
Version 0.3.9.4

Source: debcreator-0.3.9.4.tar.gz 

lol

---

### Post by pt123 on 2008-05-08
I hate when people post this :
```
./configure
```

when you usually end up having to add parameters to point out where your libraries for specific dependencies are locataed.

---

### Post by FuturePilot on 2008-05-08
> **barbedsaber said:**
> From website



lol


:lolflag: oh the irony.

---

### Post by macogw on 2008-05-09
> **pt123 said:**
> I hate when people post this :
```
./configure
```

when you usually end up having to add parameters to point out where your libraries for specific dependencies are locataed.

Er...dunno what you're doing, but no.  Where did you move your libraries to?  I don't need to add parameters to ./configure unless I'm doing something special...like turning on debug output or I want the binary to be in my home directory, not in /usr/local/bin/

---

### Post by gsmanners on 2008-05-09
You can get a binary version from here:

[http://www.gnomefiles.org/app.php/Deb_creator](http://www.gnomefiles.org/app.php/Deb_creator)

---

### Post by ShodanjoDM on 2008-05-09
> **23meg said:**
> but the nature of the job is one that requires a level of care, standards adherence and technical knowledge that goes beyond the kind of "ease" that traditional GUI tools are meant to provide.

+1

Not that I'm against the GUI for creating packages, but I've read the tutorial to create your own debian packages the "correct" way and although it seems a lot more complicated, I've got the impression that the highly effective dependencies tracking of the apt-get and aptitude really comes from the strict rules of creating the debs. 

Still haven't managed to create a "proper" .deb though... But I'll get there someday.

---

### Post by SupaSonic on 2008-05-09
I used checkinstall yesterday for the first time to build a .deb for wesnoth. It went smoothly, only after that update manager suggested that I 'upgrade' wesnoth from version 1.4 to version 1.1.

---

### Post by macogw on 2008-05-09
> **ShodanjoDM said:**
> +1

Not that I'm against the GUI for creating packages, but I've read the tutorial to create your own debian packages the "correct" way and although it seems a lot more complicated, I've got the impression that the highly effective dependencies tracking of the apt-get and aptitude really comes from the strict rules of creating the debs. 

Still haven't managed to create a "proper" .deb though... But I'll get there someday.

There were 2 hours spent on "how to package" during OpenWeek.

---

### Post by Cherry Cotton on 2008-05-09
> **23meg said:**
> It's also highly debatable whether entering the exact same depends and build-depends syntax (which one is supposed to know in the first place) into a GUI text box is any "easier" than typing it up in a text editor.

It's really daunting, though. When you have a GUI text box, it holds your hand at least a little bit by telling you what information it needs. I've been learning (trying) to do packaging and a big obstacle is that it's hard to find anything that will generate a "typical" set of Debian config files that I can use as templates. Entering everything in from a blankness feels like doing laser surgery on a live frog. At least with some prompts letting you know what to do, you have fewer opportunities to screw up.

...Also, I have ADD, and any kink in the process is another opportunity for it to derail entirely in my mind (this is something that regularly makes me want to kick UI designers repeatedly for thinking "one more click," "one more menu," or "one more text box" is never a bad thing). I'm not really defending DebCreator... I've never used it. I just know that, when I started to use TurboGears, it helped me immensely that I could easily generate a blank website from a script and build from there. There are few things more intimidating, to me, than a blank page that I'm supposed to turn into a mission-critical configuration scheme. In fact, when I make an HTML document, I typically start with the doctype and empty html, head, and body tags for this reason. I find a blank page terrifying.

So, while it does sound like DebCreator goes too far in this direction, hand-holding is important, or I'll completely lose interest and then I might as well have not even started. Learning packaging is rough, and there doesn't seem to be a clearly defined path for it (though Maco pointing out the Ubuntu Open Week is helpful). I'm certainly not saying that everything should happen with "one click" or, worse, a Microsoft-style wizard ("it looks like you're trying to resolve a dependency"... shudder). I just hope we don't let the fact that packaging is complicated--and complicated for good reasons--get in the way of making the learning process easier on people, even people who, unlike me, don't have ADD and aren't distracted by the slightest--ooh, what's that?!

;)

---

### Post by ShodanjoDM on 2008-05-09
> **macogw said:**
> There were 2 hours spent on "how to package" during OpenWeek.

Missed it... :(

Is there any wiki or other written docs about it?

---

### Post by madjr on 2008-05-09
> **ShodanjoDM said:**
> Missed it... :(

Is there any wiki or other written docs about it?

oh yeah am interested too.

---

### Post by aamukahvi on 2008-05-09
> **ShodanjoDM said:**
> Missed it... :(

Is there any wiki or other written docs about it?

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

---

### Post by macogw on 2008-05-14
> **ShodanjoDM said:**
> Missed it... :(

Is there any wiki or other written docs about it?

Chat logs: [https://wiki.ubuntu.com/MeetingLogs/openweekhardy/PackagingA](https://wiki.ubuntu.com/MeetingLogs/openweekhardy/PackagingA)

Also, yes, there is a way to generate a typical set of debian files as a template.  The debhelper command does it.

---

### Post by samwyse on 2008-05-14
Judging by the first screen, it seems like the most annoying thing is not covered by the program (installing libraries needed for compiling). The rest is just three standard commands on the CLI.

---

### Post by macogw on 2008-05-14
> **samwyse said:**
> Judging by the first screen, it seems like the most annoying thing is not covered by the program (installing libraries needed for compiling). The rest is just three standard commands on the CLI.
You don't really need to install them...just find out what they are.  Make the source package and upload it to your PPA, or if you don't want to wait for the build farm, throw it through pbuilder and let it get all the libs.

---

### Post by mhh91 on 2008-08-28
everytime i use this thing,i get this message,what can i do to avoid it??


Unable to detect the top source directory in the archive. This should be something like <name>-<version>

---

