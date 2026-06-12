---
title: "My first non Ubuntu Linux distro..."
date: 2009-07-05
forum: The Cafe
---

### Post by Muffinabus on 2009-07-05
I'm about to install Arch, try out some more 'advanced' Linux and see how well I fare.  I feel weird about moving away from Ubuntu though, I feel guilty somehow.  What if I like Arch?!  What if I want to actually *keep* it on my system instead of Ubuntu?!  It's kinda scary!

Well, the CD is in the tray... bye.

---

### Post by the8thstar on 2009-07-05
I think it's going to be a *while* before you do. I'm taking the same road myself, so good luck to you.

---

### Post by moster on 2009-07-05
Try it, and when you come back on Ubuntu, you will never want to leave again :)

I do not know if I downloaded right Arch but installation looked like some distro from 1999. I wil not tol you rest because first hand experience is best ;)

---

### Post by tjwoosta on 2009-07-05
> Try it, and when you come back on Ubuntu, you will never want to leave again

I do not know if I downloaded right Arch but installation looked like some distro from 1999. I wil not tol you rest because first hand experience is best 

lol...

Arch doesnt come with a desktop environment, or anything really, only CLI. You have to install and setup your own environment.  You choose whichever wm you want with whatever apps you like.

Its not something you can just pop in a live cd and click a few times to get to a desktop.

---

### Post by tuskenraider on 2009-07-05
i took the HUGE leap and moved to mint... I love it..  because its sooooo different than ubuntu... haha

i love ubuntu... but the visuals and the way mint is setup appeals more to me...

btw... i know its based on ubuntu.. :lolflag: 

tusken

---

### Post by RiceMonster on 2009-07-05
> **Muffinabus said:**
> What if I like Arch?!  What if I want to actually *keep* it on my system instead of Ubuntu?!  It's kinda scary!

Well, the CD is in the tray... bye.

So? What does it matter what distro you use?

> **moster said:**
> Try it, and when you come back on Ubuntu, you will never want to leave again :)

I do not know if I downloaded right Arch but installation looked like some distro from 1999. I wil not tol you rest because first hand experience is best ;)

Maybe you should do some reading to get an idea of it.
[http://wiki.archlinux.org/index.php/Arch_Linux](http://wiki.archlinux.org/index.php/Arch_Linux)
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

---

### Post by Muffinabus on 2009-07-05
Hehe, I've already run into some problems.  The installer is a bit intimidating, but I do have it successfully installed and running, I just can't get pacman to work, hmph...  It doesn't seem TOO complicated getting a DE running, I'll continue to work on it (:

---

### Post by ddrichardson on 2009-07-05
```
pacman -S gnome
```
Replace gnome with kde or whatever. Remember Arch uses a root account by default.

You should follow the [beginners guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") - its some of the best docs I've seen.

---

### Post by earthpigg on 2009-07-05
i highly suggest trying it in VirtualBox first, if you have only one computer (it sounds like that is the case).

you _will_ need to look at the beginners guide and the install wiki while setting it up.

---

### Post by calrogman on 2009-07-05
> **Muffinabus said:**
> I'm about to install Arch, try out some more 'advanced' Linux and see how well I fare.  I feel weird about moving away from Ubuntu though, I feel guilty somehow.  What if I like Arch?!  What if I want to actually *keep* it on my system instead of Ubuntu?!  It's kinda scary!

Well, the CD is in the tray... bye.

You're going to jump straight from Ubuntu to Arch?!  Good heavens, no.

Try Debian first.

---

### Post by Muffinabus on 2009-07-05
Yeah, I do only have one computer but dual boot XP and my other hard drive with Linux, so right now I'm just temporarily unplugging each hard drive to boot and troubleshoot, ha.

Anywho, yeah, I read up a bunch of stuff before installing and whatnot, just my pacman isn't working and I've no idea why.  I'm currently attempting to get help and troubleshoot that problem on the Arch forums, ha.  You can see that thread here:

[http://bbs.archlinux.org/viewtopic.php?id=75405](http://bbs.archlinux.org/viewtopic.php?id=75405)

---

### Post by Skripka on 2009-07-05
> **calrogman said:**
> You're going to jump straight from Ubuntu to Arch?!  Good heavens, no.

Try Debian first.

Many people do.  Including little old me.


It is all the same-just with different idiosyncrasies and salient details.  With Arch-you have to remember that the only thing that is done for you is that the repos have precomiled binaries.  It is up to the USER to set up their system however they like-and that includes user accounts, fstab, PolicyKit/HAL, and lastly inittab- to name the more critical.

If you can make a good tasting batch of Mac&Cheese, you can build an Arch setup.  It really sounds harder than it is-so long as you are prepared for little hand-holding.

---

### Post by Pogeymanz on 2009-07-05
I see that you've gotten your pacman issue straightened out. Good for you.

I hope you enjoy your Arch experience. No other distro has been able to drag me away from Arch.

---

### Post by swoll1980 on 2009-07-05
> **calrogman said:**
> You're going to jump straight from Ubuntu to Arch?!  Good heavens, no.

Try Debian first.

Why? Installing Arch isn't hard. If you can read instructions. It shouldn't be much of a problem.

---

### Post by lisati on 2009-07-05
> **calrogman said:**
> You're going to jump straight from Ubuntu to Arch?!  Good heavens, no.

We might just as well be asking, "You're going to jump straight from Windows to Ubuntu?", or "what's Windows?"

---

### Post by Muffinabus on 2009-07-05
Hard part: DONE!!!!  (:  That was actually quite rewarding doing everything manually.  I've now got a sudo user logged in with the extremely default Gnome with terrible and ugly fonts and icons!  YAY!  Oh, and sound works (:

This was actually QUITE fun, I'm enjoying it immensely.  Though I am nerdy in that sort of way, where fun is troubleshooting random problems on computers.

---

### Post by doorknob60 on 2009-07-05
@ ugly fonts:
```
pacman -S ttf-ms-fonts ttf-bitstream-vera ttf-dejavu
```

Those are the fonts I always install, they're mentioned in the beginners guide I belive.

---

### Post by Muffinabus on 2009-07-05
> **doorknob60 said:**
> @ ugly fonts:
```
pacman -S ttf-ms-fonts ttf-bitstream-vera ttf-dejavu
```

Those are the fonts I always install, they're mentioned in the beginners guide I belive.

Yep yup, just installed them right before I read your post (:

---

### Post by tjwoosta on 2009-07-05
I can tell you are going to love arch. Almost anything you will ever need, like how to fix the fonts and configuring different stuff, can be found right in the wiki, arch has the best wiki of any distro I have used.

---

### Post by tcoffeep on 2009-07-05
> **Muffinabus said:**
> I'm about to install Arch, try out some more 'advanced' Linux and see how well I fare.  I feel weird about moving away from Ubuntu though, I feel guilty somehow.  What if I like Arch?!  What if I want to actually *keep* it on my system instead of Ubuntu?!  It's kinda scary!

Well, the CD is in the tray... bye.

I was about 3 months into Linux when I made the switch to Arch. I enjoyed it, only because of the Beginner's guide. If I had to figure it out on my own, I'd've been a little put off. Since then, I've moved to Gentoo, but go back and forth between the two.

Good luck! :)

---

### Post by The Jinx on 2009-07-05
I was actually planning to learn how to install / use Arch myself. Do you think an old Celeron 633mhz with 192mb sdram would be able to run Arch on XFCE or Fluxbox? Or should I go the VM route to learn how to use Arch?

---

### Post by stwschool on 2009-07-05
For an older machine I'd say XFCE might not quite be light enough, Openbox, Fluxbox, or if you want a desktop environment go LXDE and you'll be just fine.

---

### Post by The Jinx on 2009-07-05
Between Openbox, Fluxbox and LXDE which one has the lightest footprint?

---

### Post by stwschool on 2009-07-05
OpenBox and FluxBox both use very very few resources. LXDE slightly more, but on the other hand it's a full desktop environment using bugger all memory. I've had Ubuntu + LXDE running on some truly god-awful hardware.

---

### Post by RiceMonster on 2009-07-05
> **The Jinx said:**
> Between Openbox, Fluxbox and LXDE which one has the lightest footprint?

Openbox and FLuxbox use around the same amount of memory. LXDE is just openbox with a bunch crap thrown on top. Just go with regular openbox (or fluxbox, if you prefer that).

---

### Post by stwschool on 2009-07-05
> **RiceMonster said:**
> Openbox and FLuxbox use around the same amount of memory. LXDE is just openbox with a bunch crap thrown on top. Just go with regular openbox (or fluxbox, if you prefer that).
LXDE is indeed just openbox + extras, but for what it's worth, those extras make life simpler, and consume very few resources.

---

### Post by moster on 2009-07-06
> **The Jinx said:**
> I was actually planning to learn how to install / use Arch myself. Do you think an old Celeron 633mhz with 192mb sdram would be able to run Arch on XFCE or Fluxbox? Or should I go the VM route to learn how to use Arch?
Look at this :)

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html]("http://ktown.kde.org/~seli/memory/desktop_benchmark.html")

---

### Post by XubuRoxMySox on 2009-07-06
> **tjwoosta said:**
> lol...

Arch doesnt come with a desktop environment, or anything really, only CLI. You have to install and setup your own environment.  You choose whichever wm you want with whatever apps you like.

And if your conscience bothers you, try the Ubuntu Minimal Install CD and "build your own" custom Ubuntu just as you would build a custom Arch distro! Only easier.

---

### Post by XubuRoxMySox on 2009-07-06
> **RiceMonster said:**
> Openbox and FLuxbox use around the same amount of memory. LXDE is just openbox with a bunch crap thrown on top. 

LOL, not exactly... [LXDE]("http://lxde.org") is a package that comes with it's own file manager and very simple, newbie-friendly graphical interface. It is often accused of not being a desktop environment at all because it is so much more lightweight than even Xfce is, and has few dependencies. It's awesome on low-resource machines.

Openbox is great! If you don't need a graphical desktop environment at all, Openbox works great all by itself.

[Crunchbang]("http://crunchbanglinux.org") is an Ubuntu-based distro that uses only Openbox and has struck a great balance between being lightweight and also fully featured.

---

### Post by fela on 2009-07-06
You know, just because you *can* use Ubuntu without much technical knowledge, doesn't mean that ubuntu *limits* you to this standard. That's the great thing about it, if you *want* to configure everything in the terminal, and not even have a desktop environment it's easily possible even in Ubuntu. So I think Ubuntu is the most universal Linux distro out there.

I think if you use something where you *have* to configure everything through the commandline and such, you are kind of shooting yourself in the foot as you only leave yourself that option (I'm not saying you can't use GUI tools in arch though). But Ubuntu has all these CLI tools, plus great support and great desktop apps!

---

### Post by gjoellee on 2009-07-06
That has to be Fedora, but I don't like yum or RPM packages so I went back to Ubuntu after two days!

---

### Post by tjwoosta on 2009-07-06
The difference with building ubuntu from the ground up is that ubuntu uses the debian package management system, it carries all debians strengths and weakneses. 

Arch takes a more vanilla approach to package management, probably the most vanilla approach to package management. You will have much less problems with dependencies, if any at all. Configs never get overwritten. Its much easier to build packages from source with the help of abs and aur.

In arch you can actually easily remove specific packages without taking a bunch of other unnecessary packages with it, for instance in ubuntu if you try to remove something simple like rhythmbox, or gnome-games it will try to remove ubuntu-desktop and a bunch of other gnome stuff with it. In arch you can add or remove any package you want without taking anything unnecessary with it.  It will never remove any packages that are required by other packages.

Another difference is that arch uses i686 where ubuntu uses i386  (its not a huge difference, but it is noticable.

Dont get me wrong, I have no problems with Ubuntu and I still use it on a couple of machines. But if your goal is building a custom system from the base up and learning the inner workings, Arch is much better suited.  I would reccomend arch to any power users, because thats who its designed for. Just as I would reccomend Ubuntu to any regular users who dont care for building a custom system because thats who its designed for.

---

### Post by Blacklightbulb on 2009-07-06
I tried Arch together with several other distros and also BSD ones and still I like Ubuntu best since the others need hours of configuration (for a noob like me) and still they are less supported and there where no real benefits I was away of (in my case).

---

### Post by nothingspecial on 2009-07-06
> **tjwoosta said:**
>   I would reccomend arch to any power users, because thats who its designed for. Just as I would reccomend Ubuntu to any regular users who dont care for building a custom system because thats who its designed for.

That`s the thing.

I installed Arch and by the time I had finished tweaking it to my liking it was almost exactly the same as my Ubuntu install.

And I found it really boring.

But if you want to feel ultra geeky without actually having to do anything difficult (as long as you can follow instructions) off you go.

---

### Post by tjwoosta on 2009-07-06
Its not about being ultra geeky, its about having complete control and customizability over everything. Its also a great learning process, and its quite fun, which if memory serves is what the OP was looking for.

I can see that some of you dont enjoy learning new distros, or the  installation process, or learning about the internals, you would rather just get down to buisness quickly and thats fine, but the OP wanted to learn a more advanced linux disto, why does everyone have to always come in with comments about how ubuntu is easier and setting up arch is boring. Your obviously not ready for arch but that doesnt mean others arent.

> I installed Arch and by the time I had finished tweaking it to my liking it was almost exactly the same as my Ubuntu install.

Maybe, but it doesnt have to be, its all up to you to choose your own environment. If you choose to make it almost exactly the same as your ubuntu desktop thats what it will be, but its not limited to that.

---

### Post by xXchibidudeXx on 2009-07-06
Hmmm good luck.
Just learn how to use commands, configuring the xorg.conf, and other stuff.
I came from mandriva (rpm based) and i dont know about arch linux but just take your time and use a live CD if possible.

---

### Post by hewbert on 2009-07-06
> **fela said:**
> You know, just because you *can* use Ubuntu without much technical knowledge, doesn't mean that ubuntu *limits* you to this standard. That's the great thing about it, if you *want* to configure everything in the terminal, and not even have a desktop environment it's easily possible even in Ubuntu. So I think Ubuntu is the most universal Linux distro out there.

I think if you use something where you *have* to configure everything through the commandline and such, you are kind of shooting yourself in the foot as you only leave yourself that option (I'm not saying you can't use GUI tools in arch though). But Ubuntu has all these CLI tools, plus great support and great desktop apps!

I concur with this.  I've been using *nix for over a decade now, and ended up installing Ubuntu last fall.  I dig it.  I've used several distributions and some BSD variants, especially FreeBSD.

I've learned a lot along the way and consider myself a "power user."  I don't feel Ubuntu is for "beginners" (while it is beginner-friendly).  Frankly, I just find it easier to use and maintain on my desktop.  I'd spend a lot of effort "building" something else to do what my Ubuntu desktop does out of the box - why bother (for me)?

I wish you luck on your journey into other distributions and possibly other OSes.  The experience is invaluable and will benefit you even if you decide to use a more pre-configured "out of the box" setup later on.

---

### Post by nothingspecial on 2009-07-06
> **tjwoosta said:**
> Its not about being ultra geeky, its about having complete control and customizability over everything. Its also a great learning process, and its quite fun, which if memory serves is what the OP was looking for.

I can see that some of you dont enjoy learning new distros, or the  installation process, or learning about the internals, you would rather just get down to buisness quickly and thats fine, but the OP wanted to learn a more advanced linux disto, why does everyone have to always come in with comments about how ubuntu is easier and setting up arch is boring. Your obviously not ready for arch but that doesnt mean others arent.


Oh I can manage Arch perfectly well thank you very much. I was just relating my experience. I found the install process boring, after all it`s just a matter of following instructions.


> Maybe, but it doesnt have to be, its all up to you to choose your own environment. If you choose to make it almost exactly the same as your ubuntu desktop thats what it will be, but its not limited to that.

There was an earlier post that mentioned the fact that Ubuntu has all the power and customability (is that a word?) of any linux distro. It`s just easy to install and start using ie not boring to set up. I like to use my computer for computing.

Yes trying to remove evolution does try to remove other components of gnome. Either keep it or remove gnome all together then compile it the way you want or install something else. No problem.;)

---

### Post by Eisenwinter on 2009-07-06
> **calrogman said:**
> You're going to jump straight from Ubuntu to Arch?!  Good heavens, no.

Try Debian first.
I think trying Debian isn't such a good idea, because it really isn't that different from Ubuntu.

The experience is virtually the same. Doing a complete installation of Debian (ie, not a minimal install) leads to virtually Ubuntu with more outdated software. That's it.

I've used Debian for around a month as my only system, and it really wasn't very different from Ubuntu, except for the repositories and the applications in them. In general, both distros do things in the exact same way. Debian holds your hand a little less than Ubuntu (as far as the "complete installation" goes).

I think that trying out a distribution which does things in a **completely different way** is better, because it teaches you another approach.

Distributions like Arch will teach you how Linux works inside, also, which is always a big plus for someone who uses Linux as their main system.

---

### Post by tjwoosta on 2009-07-06
> Yes trying to remove evolution does try to remove other components of gnome. Either keep it or remove gnome all together then compile it the way you want or install something else. No problem.

I can see now that its just about impossible trying to reason with people at UF, so I think Ill just crawl silently back into my hole over at OS talk where theres no distro bias. Best of luck to the OP.

---

### Post by RiceMonster on 2009-07-06
> **nothingspecial said:**
> I like to use my computer for computing.

I REALLY wish people would stop saying that. People who use "advanced" distros get to use their computer as well. My gentoo using friend gets to use his computer for computing as well. Yes, if you use an "advanced" distro, you likely spend more time tinkering, but it's not like I don't use my computer for actual work or leisure stuff that isn't tinkering.

I'm not saying you should abandon the "desktop ready" distros, because I understand that some people want things to be set up for them. I use Fedora on my laptop for that reason.

> **nothingspecial said:**
> Either keep it or remove gnome all together then compile it the way you want or install something else. No problem.;)

If you're going to go through all that work, you may as well just use a "do it yourself" distro in the first place.

---

### Post by angry_johnnie on 2009-07-06
Arch is an awesome distribution.  It'll take a little bit longer to configure it the way you want it (unless, of course, the way you want it is a command line install...), but that's part of the fun. :)  [Documentation]("http://wiki.archlinux.org/index.php/Main_Page") is pretty straight forward, and easy to follow.  And, if you don't like it, you can always go back to Ubuntu. :)

---

### Post by nothingspecial on 2009-07-06
> **tjwoosta said:**
> I can see now that its just about impossible trying to reason with people at UF, so I think Ill just crawl silently back into my hole over at OS talk where theres no distro bias. Best of luck to the OP.

I`m not trying to upset anyone, just relating my experience and opinion. And of course I haven`t gone to that trouble. I just (personally, in my humble opinion that I`m not trying to shove down anyone else`s throat, and I have tried arch I promise) didn`t see what the advantage is. I find Ubuntu as customisable as I want it to be.

I did take exception to being told I`m "obviously not ready for arch" which is why my reply was probably a bit spikier than it needed to be.

Any way I don`t actually really care that much. Happy Monday to you all :p

---

### Post by tjwoosta on 2009-07-06
Sorry if it came across that way, I was actually not intentionally directing it at anyone in particular when I said "your not ready for arch".

My opening sentence of that paragraph said "I can see that some of you...". Therefore it should be logical to assume that the rest of that paragraph would be directed towards "some of you", not you in particular.

Any way I dont really care much myself, I just try to make it so everyone gets a fair prespective. When you get a few people who start talking down about something such as trying arch, many others who read it will jump to conclusions without ever trying it and deciding for themselves. 

Whatever, let bygones be bygones right, Im sorry it sounded that I was directing that statement at you. Happy Monday to you as well sir :)

---

### Post by nothingspecial on 2009-07-06
No problem buddy.

And my apologies to you also.

I suppose the whole point of linux is do with it what you will and use it however you like.

Hope you have a good Tuesday too.  :D

---

### Post by hessiess on 2009-07-06
Arch is rolling release, you will love not having to re install all the time and always having the newest version of everything. the fact that it takes longer to install is irelivent as you never need to reinstall it.

---

### Post by Dragonbite on 2009-07-06
Might be fun to play with Arch, sounds like it would remind me of my Gentoo days.  Unfortunately one of the reasons I've come to Ubuntu (and fight myself tooth-and-nail to remain with Ubuntu and not distro-hop) is because I want to spend less time maintaining, tweaking and reading documentation and have it just work!

---

### Post by raronson on 2009-07-06
Experiment.  Play around.  Learn something new.  See a different approach--but first, do it all in a vm in a stable envirnoment...

Arch assumes a higher level of knowledge and experience.  If I remember right, Arch even expressly says so in its official documentation.  The purpose of its minimal install approach and its seemingly lackluster installer is to give the experienced user exactly what he or she wants from the ground up--it's not stricly a desktop system, it's a meta-distribution like Debian, Gentoo, or Linux From Scratch (and Arch basically *is* an automated Linux From Scratch).  Some extra work is required to set up Arch: manually editing config files for services, adding users as root, and using its package manager (Pacman) to finish up the system installation to install whatever the user wants for the intended purpose.  None of this is a big deal if you know your way around.  And going through the experience *makes* you get to know your way around.  

Of it's kind, I think that Arch is probably the finest meta-distribution.  Debian is of course, great, but it's focus is primarly on developing "a free as in freedom" stable GNU/Linux system which requires the desktop user to dip into unstable and testing branches of the release and to add in non-free and commercial repositories to add in the extra functionality that you'd expect from a modern system.  This can make it a little overwhelming at times to maintain and to keep a stable environment.  However, Debian is perhaps the best platform from which to take root, as Ubuntu has done and experienced incredible growth.  Debian also has an important role in maintaining the legacy of GNU/Linux by keep it current and "free as in freedom."

I mentioned Gentoo as well, which you can learn a lot about Linux systems in General from by building the system from scratch and editing every config file of consequence.  Gentoo also has awesome documentation, second only to FreeBSD.  Although Gentoo also has the option of installing many precompiled binaries, its primary method is to compile from scratch--which also helps you learn a lot about building software on Linux systems.  Aside from the novelty of the experience though, I just found that maintaining the system and recompiling X and Gnome on a regular basis wasn't for me.

So at the time that I was into all that, I didn't want to build a system from source, but I did want the freedom to install whatever I wanted and manually configure the system.  In the Linux world, it doesn't get much better than Arch for this.  It's very reminiscient of installing/using FreeBSD (which I also love, but won't tangent out to explain why--unless you want to know).

Ubuntu's focus is different.  It's primarily a desktop system (though the server side is gaining a lot of momentum) with the average user in mind.  It's suitable for everyone regardless of experience and can handle the day-to-day needs for just about everyone on the planet who uses any form of personal computer.  Though, don't mistake this for "dumbed down Linux."  Ubuntu delivers exactly what it focuses on, and has become, in my opinion, the overall finest distribution available.

In Neal Stephenson's short book, "In the Beginning Was the Command Line", he talks about the merits of different OS's to include BeOS, Linux, Windows, and Mac OS (before OS X).  Using systems that "just work" he relates to "going to Disneyland."  I think he says something like, Windows is a Ford Escort, Mac OS is a luxury car, and Linux is a tank.  The escort is suitable for short trips on smooth pavement, while the luxury car is suitable for the same thing howbeit more comfortably, while the tank can negotiate any terrain--and especially the ones that the escort and luxury car can't.  But driving a tank on smooth pavement for short trips is less than ideal, so Neal says that once OS X came out offering UNIX under the hood, he made the switch and uses it for all purposes--including trips to Disneyland.

My experience with OS X was a little different; the interface is nice and everything works well, but the UNIX environment--the very thing that attracted me to it--is gimped.  Try using a terminal to open a file with its default editor, TextEditor.app and you'll see what I mean.  This is only one simple example, and I finally did manage to do it, but in the end, using 'gedit whatever.file' from a terminal requires no jumping through hoops.  Sure, I could install other editors (and did), but why should I have to?  OS X's focus is not UNIX, it's interface, and it delivers what it focuses on.  And if I just want to "go to Disneyland" (life outside the raw environment of the shell), I'll use OS X.  

Though now with Ubuntu's latest release, everything (mostly) "just works" out of the box and by applying my own themes it rivals OS X in asthetics, usability, and interface.  I'm finding less and less reasons to reboot into OS X from my Macbook (I think nostalgia will get the better of me from time to time though).  With Ubuntu, if I want a fully featured modern UNIX system, I have it.  And if I want outside of that environment to look at all the pretty flowers, I have that too.

---

### Post by evermooingcow on 2009-07-06
> **RiceMonster said:**
> I REALLY wish people would stop saying that. People who use "advanced" distros get to use their computer as well. My gentoo using friend gets to use his computer for computing as well. Yes, if you use an "advanced" distro, you likely spend more time tinkering, but it's not like I don't use my computer for actual work or leisure stuff that isn't tinkering.
+1
I'd also like to add:

Since when does tinkering not constitute as computing? This is a biased opinion of those who find it boring.

Tinkering *is* my leisure activity.

---

### Post by hessiess on 2009-07-06
> **evermooingcow said:**
> +1
i'd also like to add:

Since when does tinkering not constitute as computing? This is a biased opinion of those who find it boring.

Tinkering *is* my leisure activity.

+1

---

### Post by nothingspecial on 2009-07-06
> **evermooingcow said:**
> +1
I'd also like to add:

Since when does tinkering not constitute as computing? This is a biased opinion of those who find it boring.

Tinkering *is* my leisure activity.

Fair enough. Like I said, I was a bit annoyed at the time.
:rolleyes:

---

### Post by Pogeymanz on 2009-07-06
You can't really say that Ubuntu is just as tweakable as Arch. Managing daemons and modules is incredibly convoluted in Ubuntu when compared to how simple it is in Arch. Granted, a lot of people wont want to bother doing that, but it is a tangible difference in tweakability.

And the fact that Arch is rolling release is very important to a lot of people, myself included. Try comparing package versions between an up-to-date Ubuntu install 5 months after a release vs. an up-to-date Arch install.

So, even if you install Gnome+Compiz in Arch, if you use it for a month or so, you'll likely become aware of the differences between Arch and Ubuntu.

I'm glad the OP is having success and enjoying himself. That's what it's all about, after all.

---

### Post by nothingspecial on 2009-07-06
> **Pogeymanz said:**
> You can't really say that Ubuntu is just as tweakable as Arch. .

I didn`t.

---

### Post by Pogeymanz on 2009-07-06
I wasn't pointing a finger at you. I was actually referring to fela's post, with which you seemed to agree, actually.

---

### Post by nothingspecial on 2009-07-06
OK I retire. I must be in one of those moods tonight. Probably best if I unsubscribe to this thread.

Night night.

O:)

---

### Post by calrogman on 2009-07-06
> **Skripka said:**
> If you can make a good tasting batch of Mac&Cheese, you can build an Arch setup.  It really sounds harder than it is-so long as you are prepared for little hand-holding.

I can make a decent Mac & Cheese and I don't mind having my hand held, I just attempted to install Arch Linux, first from the CD to update later (the update included a kernel update which resulted in spectacular failure) and then later from FTP/HTTP, this resulted in an entirely unusable system, it freaked out about /dev/fd0 on boot and shut down, fstab had no mention of /dev/fd0 and there was no floppy attached to the VM.

See: [http://bugs.archlinux.org/task/15329](http://bugs.archlinux.org/task/15329)

Debian, on the other hand, in all of my past experiences and despite my abusing it, just works.

-----

Several of my previous attempts to learn about Arch also failed, one of them failed due to bash looking for libreadline.so.4 instead of libreadline.so.5, this was fixed eventually.

---

### Post by Pogeymanz on 2009-07-06
I've heard that Arch is a pain in a VM. I've never tried it, though.

---

### Post by calrogman on 2009-07-06
In that case I'll go buy some really cheap PC from a charity store or something and put Arch on it, if it works better out of a VM, I'll find out.

---

### Post by Muffinabus on 2009-07-07
Just thought I'd update!

I'm still loving Arch!  I love it's complete modularity in the sense that I can remove specific programs from my system without having to worry AT ALL about breaking other dependencies or my system failing!

I love how I don't have to wait for anything to be updated in the repositories.  I had VLC 1.0.0 the moment I found out it was released (:

Their wiki IS great, as someone said earlier.  I didn't like the way the default nautilus behaved, one search on the wiki told me how to modify it to the way I like.  Also got Compiz working finely, that took no effort at all.

I've pretty much gotten my system to the point where I can stop worrying about functionality and start customizing my themes and other eye candy!

---

### Post by Pogeymanz on 2009-07-07
Congratulations!

Welcome to the dark side. You can't ever leave now, I hope you realize that...

---

### Post by Skripka on 2009-07-07
> **Pogeymanz said:**
> Congratulations!

Welcome to the dark side. You can't ever leave now, I hope you realize that...

Who would want to?  After all just for starters there's the never ending Taco bar.

---

### Post by Muffinabus on 2009-07-07
> **Skripka said:**
> Who would want to?  After all just for starters there's the never ending Taco bar.

Mmm, tacos.

---

### Post by behemoth8186 on 2009-07-07
I've tried Arch as well. I installed it on a desktop - had Openbox running, pacman, everything. I never could get Xorg setup properly on my laptop, so I switched again...

I went through Ubuntu (before Arch), Fedora, openSUSE, Crunchbang, Wolvix, GoblinX, Kwort, Gentoo, Sabayon, Zenwalk, Mint, Debian, Mandriva, Knoppix, Vector, etc...and I ended up back with Ubuntu after I bought my new laptop. I grew tired of configuring and re-configuring everything. Good luck with Arch, most people I've heard from love it once they get it working.

---

### Post by moster on 2009-07-08
What is really bothering me about that arch thing is some of their users. As I heard from them what they talk about ubuntu is something like... bloated, slow, vista in linux, too much like vista... That last specially get on my nerves.

I try arch too, I was not really impressed. I think because of few arch users I actually manage to hate him.

edit:
Few days ago I installed full blown Ubuntu on this computer
CPU Duron 1,3 Ghz
512 SDRAM
HDD 15 GB
VGA Geforce 2 MX400 64 MB RAM
It is perfectly usable. Even with compiz effects if you are not pushing resolution above 1024*768. It started using swap only when I open firefox and surf little.
Most of tests phoronix and tuxradar do is done in ubuntu, that has to mean something.

---

### Post by Dragonbite on 2009-07-08
> **moster said:**
> What is really bothering me about that arch thing is some of their users. As I heard from them what they talk about ubuntu is something like... bloated, slow, vista in linux, too much like vista... That last specially get on my nerves.

I try arch too, I was not really impressed. I think because of few arch users I actually manage to hate him.
Yeah, I know what you mean. A couple people from PCLinuxOS really left a bad taste in my mouth and I don't want to even bother using it.  It definitely leaves an impression.

At least now I know a few people who do use it who are helping me through it, but I still have little or no interest at this point.

> **moster said:**
> 
edit:
Few days ago I installed full blown Ubuntu on this computer
CPU Duron 1,3 Ghz
512 SDRAM
HDD 15 GB
VGA Geforce 2 MX400 64 MB RAM
It is perfectly usable. Even with compiz effects if you are not pushing resolution above 1024*768. It started using swap only when I open firefox and surf little.
Most of tests phoronix and tuxradar do is done in ubuntu, that has to mean something.
I must not do much. My Pent. M @1.4 GHz w/512 MB of Ram almost never touches the swap drive.. ever. Hibernate is about the only thing I can think of will use the swap drive at this point.

---

### Post by moster on 2009-07-08
> **Dragonbite said:**
> Yeah, I know what you mean. A couple people from PCLinuxOS really left a bad taste in my mouth and I don't want to even bother using it.  It definitely leaves an impression.

At least now I know a few people who do use it who are helping me through it, but I still have little or no interest at this point.

Sometimes I think that linux community are separated so much that even microsoft could not do it better.
> **Dragonbite said:**
> 
I must not do much. My Pent. M @1.4 GHz w/512 MB of Ram almost never touches the swap drive.. ever. Hibernate is about the only thing I can think of will use the swap drive at this point.

You will really drive that thing till its natural death. :) My box just started his journey with linux. I will see how far it will get.

---

### Post by Dragonbite on 2009-07-08
> **moster said:**
> Sometimes I think that linux community are separated so much that even microsoft could not do it better.


You will really drive that thing till its natural death. :) My box just started his journey with linux. I will see how far it will get.

This system was replacing my Pentium III @ 500 Mhz with 256 MB of Ram which was running Edubuntu from about 2006. I finally got rid of it when I got a number of hand-me-down systems (like the 1.4 GHz laptop).

That's one good thing about Microsoft's new OS versions; people have to get new systems to run them so they don't know what to do with the old ones. I should start setting them up as file servers running Linux for people for a small price.

---

### Post by Pogeymanz on 2009-07-08
> **moster said:**
> What is really bothering me about that arch thing is some of their users. As I heard from them what they talk about ubuntu is something like... bloated, slow, vista in linux, too much like vista... That last specially get on my nerves.

I try arch too, I was not really impressed. I think because of few arch users I actually manage to hate him.

edit:
Few days ago I installed full blown Ubuntu on this computer
CPU Duron 1,3 Ghz
512 SDRAM
HDD 15 GB
VGA Geforce 2 MX400 64 MB RAM
It is perfectly usable. Even with compiz effects if you are not pushing resolution above 1024*768. It started using swap only when I open firefox and surf little.
Most of tests phoronix and tuxradar do is done in ubuntu, that has to mean something.

Yes, and some Ubuntu users piss me off. It's not really the OS's fault.

It's not a matter of opinion; Ubuntu packages are more heavily patched than Arch packages and include dependencies that you don't need. Therefore Ubuntu is more bloated than Arch. Whether or not Arch is slim enough that it's worth it for you... well, that's another question.

In fact, that machine you put Ubuntu on might be noticeably faster with Arch, especially since you're using the big stuff like Gnome and Compiz.

I'm just saying, don't let a few users ruin your opinion of something. Of course, if you don't like tinkering and editing a config file here and there, then Arch just isn't for you- which is fine too.

Linux rules. Not matter what distro. End of story. :guitar:

---

### Post by moster on 2009-07-08
> **Pogeymanz said:**
> Yes, and some Ubuntu users piss me off. It's not really the OS's fault.

It's not a matter of opinion; Ubuntu packages are more heavily patched than Arch packages and include dependencies that you don't need. Therefore Ubuntu is more bloated than Arch. Whether or not Arch is slim enough that it's worth it for you... well, that's another question.

In fact, that machine you put Ubuntu on might be noticeably faster with Arch, especially since you're using the big stuff like Gnome and Compiz.

I'm just saying, don't let a few users ruin your opinion of something. Of course, if you don't like tinkering and editing a config file here and there, then Arch just isn't for you- which is fine too.

Linux rules. Not matter what distro. End of story. :guitar:
I agree with you. We are just discussing some random thoughts :)

Everything depends what feature you look as bloat. To some people it is mono, to other compiz, in the end it do not matter. I mean, it is not right to call some OS bloated if he can run full featured comfortable with 512 memory. That is my whole point.

---

### Post by Eisenwinter on 2009-07-08
> **Pogeymanz said:**
> Congratulations!

Welcome to the dark side. You can't ever leave now, I hope you realize that...
"Once you've tried Arch, there is nowhere else to march" ;)

(I made that up right now, heh)

---

### Post by Pogeymanz on 2009-07-08
All good points.

Hell, you can barely run WinXP on 512MB RAM these days. Once you get all the service packs and load up some antivirus, 512MB gets to be far too little.

I have run Ubuntu on a Celeron@2.53Ghz w/ 512MB RAM and it was a little too slow for my taste until I put XFCE on there instead of Gnome. Now it's beautiful and runs just as quickly as it ever did with WinXP.

---

