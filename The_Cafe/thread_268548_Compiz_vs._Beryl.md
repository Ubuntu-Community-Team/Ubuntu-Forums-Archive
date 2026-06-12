---
title: "Compiz vs. Beryl"
date: 2006-09-30
forum: The Cafe
---

### Post by caspian on 2006-09-30
I've used Compiz for quite a while, and have been very pleased with it. I've never used Beryl -- but I'm wondering what it has to offer. That is, what advantages does Beryl have over Compiz? For those of you who use Beryl -- do are you pleased with it (over Compiz?)

I'm wondering whether I should make the switch.

Thanks!

---

### Post by mostwanted on 2006-09-30
Have you used the Compiz in Edgy or the one from the unofficial repos in Dapper (beerorkid.com)? Because Beryl is just the continuation of those two.

The regular Compiz is like Beryl (= current Edgy Compiz and the unofficial Dapper Compiz), but doesn't have blur, animations, CGWD themes or the CSM configuration utility.

---

### Post by tagra123 on 2006-09-30
> **caspian said:**
> I've used Compiz for quite a while, and have been very pleased with it. I've never used Beryl -- but I'm wondering what it has to offer. That is, what advantages does Beryl have over Compiz? For those of you who use Beryl -- do are you pleased with it (over Compiz?)

I'm wondering whether I should make the switch.

Thanks!

I was actually able to get Beryl to install. Compiz seemed to have problems with unmet depenendcies.

---

### Post by _simon_ on 2006-09-30
Just to clarify, Compiz Quinn has become Beryl

[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

[http://blog.beryl-project.org/](http://blog.beryl-project.org/)

If you have been using Compiz Quinn then you can either stick with what you have knowing there will be no further updates or move across to Beryl.

---

### Post by jr.gotti on 2006-09-30
Maybe it's just me, but at first Beryl seemed extremely slow/buggy. But for some reason it fixed itself, and everything is up to par. I guess I just had to change some defaults. Now I like it more than compiz...it has more of a "finished product" feeling, with all the configuration options.

---

### Post by gnomeuser on 2006-09-30
[Dave Reveman on Beryl](http://lists.freedesktop.org/archives/compiz/2006-September/000487.html)

Reading that I'm never going to touch Beryl, I like things to be done right because we have to support it for a long time and chasing down bugs in a bunch of hacks is a waste of time. I was rather stunned when they announced the fork based on "non cooperation from Dave", I've followed the mailinglist and I have not seen Quinn Storm submit any patches or partake in the design discussion so I'm not clear as to where that claim comes from.. it just frankly strikes me as lying.

All things considered Compiz works great here, Dave Reveman, Kristian Høgberg and Søren Sandmann have all done a great job, it's very stable and featureful. The only thing I miss is the blur plugin from Beryl and the ability to use XV output but I understand that getting Xinerama support into Compiz is more important right now and that Dave wants to do that right. I have a great respect for people who will take the time to do things right and innovate while doing it (Compiz Xinerama support is more than just multiple monitor support, it does all kinds of useful stuff)

---

### Post by hanzomon4 on 2006-09-30
:confused: Ok...... Well Beryl is great very polished once you have your system setup right.

---

### Post by Kindred on 2006-09-30
I very much appreciate the work that has been done on removing any Gnome dependencies (yuck gconf), that for one makes me a fan of Beryl and its developers.  I also much prefer the accompanying GUI and am very impressed with the speed at which those folk work.  Also seems to be very community orientated, never a bad thing.

---

### Post by PriceChild on 2006-09-30
Personally i prefer Beryl... it does more.. it looks better :)

---

### Post by John.Michael.Kane on 2006-09-30
There both hacks. what it comes down to is which group can produce a better product, back said product on the architecture's that people will choose to run. also offering the enduser a way install said program with the least amount of issues.

Then theres the scripts that are writen to install these hacks which should work with all updates/upgrades that these packages may endure,however that does not always seem to be case as those who use xgl/ect know. 

Theres alot of room for improvment but if those incharge of these factions don't want to hear what endusers are asking for or need to beable to help with the testing of these programs then these programs will not get anywhere.

---

### Post by tageiru on 2006-09-30
> **Kindred said:**
> I very much appreciate the work that has been done on removing any Gnome dependencies (yuck gconf), that for one makes me a fan of Beryl and its developers.  I also much prefer the accompanying GUI and am very impressed with the speed at which those folk work.  Also seems to be very community orientated, never a bad thing.
Using gconf does not make Compiz depend on GNOME. Throwing out gconf, which works well, on such false grounds is not a sign of rational development decisions.

I fear that in this case "community oriented" means fast paced development of high profile features with poor technical decisions.

---

### Post by Kindred on 2006-09-30
> **tageiru said:**
> Using gconf does not make Compiz depend on GNOME. Throwing out gconf, which works well, on such false grounds is not a sign of rational development decisions.

I fear that in this case "community oriented" means fast paced development of high profile features with poor technical decisions.

I never meant to imply that Compiz depends on GNOME, sorry if you got that impression.  Gconf is more than enough for me, though, and seemingly the Beryl developers too.  I like the way they think.

---

### Post by gnomeuser on 2006-09-30
> **tageiru said:**
> Using gconf does not make Compiz depend on GNOME. Throwing out gconf, which works well, on such false grounds is not a sign of rational development decisions.

I fear that in this case "community oriented" means fast paced development of high profile features with poor technical decisions.


Agreed, especially since Dave merged some code to fix the "make gconf optional" bit. It was not that it wasn't there it was just broken, probably due to lack of testing on part of non-gconf users.

[http://lists.freedesktop.org/archives/compiz/2006-September/000491.html](http://lists.freedesktop.org/archives/compiz/2006-September/000491.html)

I'm personally a gconf man, I love the way every option is easily bundled in a tree structure which is easy to edit. It's also easy to hook into for application developers so those options you want exposed can be with a minimum of code. The worse of the performance issues have been ironed out so today gconf is probably the best scheme we have to solve that problem.

---

### Post by Anduu on 2006-09-30
Personally I have recieved a huge improvement performance wise.

Using compiz I was getting a steady 60 frames per second using the built in benchmark.Since switching to Beryl and removing all the compiz stuff I am getting over 100 fps :p

---

### Post by gnomeuser on 2006-09-30
> **Anduu said:**
> Personally I have recieved a huge improvement performance wise.

Using compiz I was getting a steady 60 frames per second using the built in benchmark.Since switching to Beryl and removing all the compiz stuff I am getting over 100 fps :p

I seriously doubt that figure and the explaination you give for the performance increase. Is it not more likely that the beryl people altered the benchmark code I'm not saying they cheat but if it's not the same benchmark it's not a fair comparison.

Regardless I'd love to see some hard data on that because if it's true we absolutely need to pin it down, a rough 80-100% increase in speed just doesn't seem likely and if it is I'd love to find the deeper cause.

---

### Post by Anduu on 2006-09-30
> **gnomeuser said:**
> I seriously doubt that figure and the explaination you give for the performance increase. Is it not more likely that the beryl people altered the benchmark code I'm not saying they cheat but if it's not the same benchmark it's not a fair comparison.

Regardless I'd love to see some hard data on that because if it's true we absolutely need to pin it down, a rough 80-100% increase in speed just doesn't seem likely and if it is I'd love to find the deeper cause.

It is not only the numbers...everything seems much smoother.

For example:
Remember that zoom feature they added which zoomed the cube out on rotate?I had to turn it off with Compiz because it caused an ugly hitch/delay for me...now it works smooth as butter.

---

### Post by hanzomon4 on 2006-10-01
I'm sorry but as an end user gconf-editor sucks. BSM has a good layout and it works everytime, where as with gconf I would get some weired behavior from time to time.

And can someone explain why you consider beryl to be "a bunch of hacks"?

I'm no programmer but Quinn's and the other's work amazes me, I think that the fork will allow them to turn out an even better product... why? Well they no longer have to worry about upstream changes screwing everything up, come to think of it that was the only time compiz-quinn gave me a hard time.

I just think beryl has a much brighter future then compiz-vanilla.

---

### Post by gnomeuser on 2006-10-01
Well I'm currently trying to apply my fading C skills to reading the blurfx plugin (as that's the only interesting addition to beryl in my mind). It seems to me that it's filled with magic numbers without any comments. 

I dunno, I find it hard to read, then again I'm used to reading Linux kernel code and they enforce a strict policy of documenting with comments. I guess I'm spoiled that way but I can't really grasp what's going on nor the reasoning behind a lot of the settings..

The only way forwards seems to be grabbing the old google and finding an OpenGL specification followed by a lot of looking up what stuff does. I doubt I'll stay awake for the entire 4500 lines. 

I'd definitely like more comments especially for the magic numbers but the author deserves much credit for sticking to the coding style which adds to the readability. 

Oh and I can definitely see why the scale plugin acts differently, the code between the two are vastly different, the beryl one definitely needs some love to fix the indentation, it flutters all over the place. It's also about 700 lines longer than the original so I doubt you can make a sensible comparison between the two.

---

### Post by tageiru on 2006-10-01
> **gnomeuser said:**
> I'm personally a gconf man, I love the way every option is easily bundled in a tree structure which is easy to edit. It's also easy to hook into for application developers so those options you want exposed can be with a minimum of code. The worse of the performance issues have been ironed out so today gconf is probably the best scheme we have to solve that problem.
I think most developers that have worked with gconf appreciates the power that it gives. Most people that complain about it are Windows users put of by its superficial similarity to the registry.

---

### Post by gnomeuser on 2006-10-01
> **tageiru said:**
> I think most developers that have worked with gconf appreciates the power that it gives. Most people that complain about it are Windows users put of by its superficial similarity to the registry.

I tend to agree, especially when you ask these people what they want in it's place and the best answer you can get is something along the lines of .ini files from back in the Windows 3.11 days. This of course ignores the performance hit you take from reading single files like this. Gconf supports storing in a database and in a tree structure both a more efficient solution than ini files scattered all over the disk and still not a binary database like the Windows registry.

Now I imagine you could do a superfast binary version of gconf based on the fact that keys don't change often, so you could build the binary and rebuild it on demand when a change is made. This would normally be when new software is installed, updated or a setting is manually changed, all cases where you would be ready to take a minor hit for the rebuilding. I believe Enlightenment 17 actually handles themes like this for performance reasons. So is my thinking flawed I wonder?

Regardless, I have yet to see a gconf complaint that is not "it's the windows registry" which is entirely false and shows a great misunderstanding of the design goals in gconf. And for developers  it's great, I'd even argue that it's good of users as well since you get a great degree of control over your desktop within the same interface, all keys are documented (or at least can be) and given the ease of use for developers there's a good change non essensial options will be added to gconf rather than being dropped entirely (or added to the interface KDE style which does tend to clutter it a bit).

---

### Post by mcduck on 2006-10-02
> **tageiru said:**
> I think most developers that have worked with gconf appreciates the power that it gives. Most people that complain about it are Windows users put of by its superficial similarity to the registry.

Actually, all of the Compiz-Quinnstorm/Beryl-developers complaining about gconf seem to be KDE users, and don't want to install gconf just to get compiz/beryl working..

Anyway, it seems to me that many people here are comparing compiz-quinnstorm with Beryl, and that doesn't really make any sense as they are the same thing. You should compare Beryl with the vanilla Compiz..

I'm using Beryl myself, as I always liked Quinnstorm's compiz packages more than the vanilla versions. Seems to work great, and they seem to have done quite some fixes to the code during this 'feature-freeze' preceeding the Beryl release. Altough it's been some time since I last time tried the vanilla Compiz so perhaps my opinion doesn't count here ;)

---

### Post by chestnut1969 on 2006-10-08
Funny, I've moved from Compiz to Beryl (with latest Nvidia drivers), and have taken a massive performance hit.

I've reconfigured much of the special effects, for a minimal increase in performance.

For the time being anyhow, Edgy with Beryl [on my machine] runs very similar performance wise to dare I say it Vista RC1 with all the Aero bells and whistles.

Compiz ran far slicker for myself.. until I can figure out why my machine is now running like a dog.

On the plus side, Beryl was a breeze to install, and seems more polished than Compiz (that always required to some degree a bit of hacking)

---

### Post by NoTiG on 2006-10-08
personally i disagree with the fork and use compiz for that reason. but i have tried both and berly supported themes... while the compiz theme i tried for compiz didnt work

---

### Post by quincy_the_penguin on 2006-10-28
Beryl works perfectly for me in Kubuntu, and I could get it set up much easier then Compiz.

---

### Post by shlomi on 2006-11-10
> **NoTiG said:**
> personally i disagree with the fork and use compiz for that reason. but i have tried both and berly supported themes... while the compiz theme i tried for compiz didnt work

Personally, I disagree with this war entirely. Both these programs are competing, and this competition is nothing but good for us. Forget all this traditions, and "how things should have been done". This is a pointless war that only helps us stay behind. The only judgment that we must make (for any program what so ever) is how well it operates, and how good the developers interacts with US, the users, to make it better. Anything else, will just brings us back to a fundamentalistic war about meaningless principles, what have no use in advancing our future. 

Let the best one make the less better one become the best. And vice-versa!

Shlomi

---

### Post by dannyboy79 on 2006-11-10
> **gnomeuser said:**
> [Dave Reveman on Beryl](http://lists.freedesktop.org/archives/compiz/2006-September/000487.html)

Reading that I'm never going to touch Beryl, I like things to be done right because we have to support it for a long time and chasing down bugs in a bunch of hacks is a waste of time. I was rather stunned when they announced the fork based on "non cooperation from Dave", I've followed the mailinglist and I have not seen Quinn Storm submit any patches or partake in the design discussion so I'm not clear as to where that claim comes from.. it just frankly strikes me as lying.

All things considered Compiz works great here, Dave Reveman, Kristian Høgberg and Søren Sandmann have all done a great job, it's very stable and featureful. The only thing I miss is the blur plugin from Beryl and the ability to use XV output but I understand that getting Xinerama support into Compiz is more important right now and that Dave wants to do that right. I have a great respect for people who will take the time to do things right and innovate while doing it (Compiz Xinerama support is more than just multiple monitor support, it does all kinds of useful stuff)

Ok, above someone states, "Just to clarify, Compiz Quinn has become Beryl". Yet when I read this link about Dave Reveman, it states that he is continuing to work on Compiz etc etc. I have read from another person that Compiz won['t ever be updated. Can anyone provide some FACTS here as to compiz, beryl, window decorators for these, managers for compiz or beryl features etc etc. i used compiz and xgl back when it was beerorkid.com or whatever, and I liked it a lot, I installed it as a different session but have since reainstalled ubuntu and have not redone the compiz thing. So I am hoping for some clarification here. thank you.

---

### Post by chaosgeisterchen on 2006-11-10
Compiz from the beeorkid.com-repository was already the release enhanced by team around QuinnStorm.

---

### Post by dannyboy79 on 2006-11-10
> **chaosgeisterchen said:**
> Compiz from the beeorkid.com-repository was already the release enhanced by team around QuinnStorm.

huh?

Ok, above someone states, "Just to clarify, Compiz Quinn has become Beryl". Yet when I read this link about Dave Reveman, it states that he is continuing to work on Compiz etc etc. I have read from another person that Compiz won't ever be updated. Can anyone provide some FACTS here as to compiz, compiz quinn beryl, window decorators & managers for these.

---

### Post by ejos on 2006-11-10
***_Clarification:_***
It all started with Compiz. This was developed by Novell. Then QuinnStorm started modifying the code from Compiz, and eventually made releases of Compiz-Quinn. Normal Compiz was still in development at this time. QuinnStorm then changed the name of his project from Compiz-Quinn to Beryl. Normal Compiz is still in development as is Beryl.

---

### Post by zootreeves on 2006-11-10
Beryl maybe more exciting and easier to use now, but most of the new code that is going in is because it's buggy/hackish (thats why it's not in compiz as well). I think in the long term compiz will be the most stable and so ultimately will "win" the war

---

### Post by drFUNK on 2006-11-10
> **ejos said:**
> QuinnStorm then changed the name of his project from Compiz-Quinn to Beryl.

Correction: **Her** project.;)

---

### Post by chaosgeisterchen on 2006-11-10
One cannot say which will 'win' as there is no real 'winner' without real competition.

---

### Post by PriceChild on 2006-11-10
Also it depends who you're asking on whether Beryl's code is hackish or not...

What is fact though is that beryl's code is a maze if you're new and havent' got experience in it.... not much documentation :)

---

### Post by keithk on 2006-12-22
I'm still pretty much a newb but I was able to get beryl up and running without any issues. I like the look and feel of it and it seems to play well with everything but frostwire. If there's an easy fix for that issue I'd like to know about it. I was concerned about the video driver thing with edgy and thought that beryl would cause alot of problems but was wrong and now I'm quite pleased with the outcome.

---

### Post by Jaygo333 on 2007-01-09
I love what you did there. 
How did you manage to get Beryl to work so smoothly. 
Been trying last couple of days without success.
I even Reinstalled Ubuntu more than five times jsut for Beryl.

My windows Decorator keeps disappearing and a really good question,
How do you change the beryl theme you have there.
Benn trying to change tmeme but dont see the effect. I click the mtheme I want in the 
theme manager but nothing happens. 
Please, I want XGL, (Beryl/ Compiz I dont want to enter debate)

gonna reinstall Ubuntu now. Have fun

---

### Post by laosboyme on 2007-01-11
I've got beryl on ubuntu dapper and it has no problem ](*,)  I would like to switch to compiz but its hard to install I've tried compiz --replace and I got no windows! Please help me install Compiz on AIXGL

---

### Post by awakatanka on 2007-01-11
I use what is most simple to install and configure and at this moment it is beryl. Compiz is to hard to get to work and configure.

And for there holy war its good for us. beryl uses code from Compiz and Compiz uses plugins from beryl. otherway around seems to be a problem because license they use. Beryl uses gpl and compiz uses gpl and mit if i'm correct.

---

### Post by Quillz on 2007-01-11
I prefer Beryl.

---

### Post by stimpack on 2007-01-11
Beryl was super easy for me to setup, even if I do not understand if I did the best thing.

 I mean I saw guides for Compix+XGL/Beryl+XGL/Beryl+AIGLX/Beryl+NvidiaBeta etc... I followed Beryl+AIGLX but I have no idea what this means or if the the best setup for Nvidia user on Edgy Eft.

Anyway it works, was simple, but its not for everyday use, slows down google earth and world of warcraft, so not yet, but when I have some friends over, its good to show off.

---

### Post by Eddie Wilson on 2007-01-11
From what I've read and been told is that Beryl is not supported on Dapper anymore. If you go to any Beryl site you will see that is true. The same goes for Compiz. The old Beryl 0.1.1 will work on Dapper, but no upgrades. I've even been told to upgrade to Edgy if I want to use  Beryl. That sounds stupid. Hell Dappers only been out for 6 months. Not very good support. By the way if you do try to use the latest version of Beryl or Compiz you will be reinstalling your system. So much for LTS.](*,) 
Eddie

---

### Post by javalight on 2007-02-18
> **keithk said:**
> I'm still pretty much a newb but I was able to get beryl up and running without any issues. I like the look and feel of it and it seems to play well with everything but frostwire. If there's an easy fix for that issue I'd like to know about it. I was concerned about the video driver thing with edgy and thought that beryl would cause alot of problems but was wrong and now I'm quite pleased with the outcome.

Frostwire relies on Java, but Java 6 has a bug when running on beryl. 

If you are using Java 6, follow these instructions for a workaround:
[http://wiki.beryl-project.org/wiki/Java]("http://wiki.beryl-project.org/wiki/Java")

Good Luck

---

### Post by BOBSONATOR on 2007-02-18
I just need to get this out, i cant live without beryl!

---

### Post by hvar on 2007-02-21
> **drFUNK said:**
> Correction: **Her** project.;)
Correction: ***His*** project ;)
[http://www.linux.com/blob.pl?id=adc547f4bd93b3ff4b940701160d2691](http://www.linux.com/blob.pl?id=adc547f4bd93b3ff4b940701160d2691)

---

### Post by tenshi-no-shi on 2007-02-22
What are you people talking about. Compiz is super simple to install and it has a manager just like Beryl to configure/enable it. I just followed the instructions for enableing compisition manager and AIGLX for my vid card and followed the instructions here [http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide]("http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide") and it worked perfectly, and I am using an old ATI card. Also the fact that compiz uses metacity for its themes is wonderful since there is so many to choose from.

I mean I have never used or installed beryl so I can comment on it's installation/use, but it seams like the people complaining about compiz are being overly whiny about it. I am sure that people have just as many horror stories about installing beryl.

Also I freaked because I saw ghosting in my screen after having compiz installed for a bit, so I uninstalled compiz and went back to plain-Jane gnome without any problems, of course it turned out that it was due to the GPU overheating on my video card because the fan wire was lose (The card still works, I think I need to light it on fire and see if it works after that). Anyways I am running Compiz now, not all the time though (because I think that it's pointless, but still it entertains me).

---

### Post by MattSMiddleton on 2007-02-22
I have installed Ubuntu on my laptop several times (I try different distros for a while, or try beta software a lot and sometimes it's easier just to reinstall) and I've never been able to get Beryl to work well.  It always installs great, but it tends to freeze my computer up quite often, which is rather annoying because I have to boot it down by holding the power button.  I have only used compiz once (it is preinstalled to work in Mandriva) and even though the version that they have isn't as flashy, it never froze up on me.  As for now I'll wait for beryl to get a little more stable before I'll give it another try.

---

### Post by Steveway on 2007-02-22
> **hvar said:**
> Correction: ***His*** project ;)
[http://www.linux.com/blob.pl?id=adc547f4bd93b3ff4b940701160d2691](http://www.linux.com/blob.pl?id=adc547f4bd93b3ff4b940701160d2691)
No, **Her** is right.
Even though biologically Quinn is a man she calls herself a woman.
Before the crash she explained herself pretty detailed but those posts got unfortunatly lost.

---

### Post by iam_foo on 2007-02-22
I prefer Beryl. I switched to Beryl following the fork..haven't went back to Compiz. Can't see myself doing that in the future either..unless Beryl really messes things up..which I don't see happening.  I think Beryl has a slight edge over Compiz atm..a few more options and easier installation from what I've heard. Beryl also has some nice unsupported things coming out.

---

### Post by GSF1200S on 2007-04-10
> **hanzomon4 said:**
> I'm sorry but as an end user gconf-editor sucks. BSM has a good layout and it works everytime, where as with gconf I would get some weired behavior from time to time.

And can someone explain why you consider beryl to be "a bunch of hacks"?

I'm no programmer but Quinn's and the other's work amazes me, I think that the fork will allow them to turn out an even better product... why? Well they no longer have to worry about upstream changes screwing everything up, come to think of it that was the only time compiz-quinn gave me a hard time.

I just think beryl has a much brighter future then compiz-vanilla.

I dont like Beyrl's version of gconf, and Im using beryl. Ill probably switch over to compiz for this reason. I mean, it breaks the system. Some of my stuff works off of gconf (metacity if beyrl is disabled for example), while other stuff HAS to be done through beyrl. 

For example- one of my shortcuts is screwed and I cant figure out how to get it working. Under metacity and gconf, I had Ctrl+Alt+Del set up to launch the system monitor (ex windows user). It worked like a charm. Now, with beyrl running, the combo doesnt work. So, I went to the BSM and went to run command 9 (which is what Gconf formally ran system monitor off of), and input the control Ctrl-Alt-Del, and nothing. It highlights the script everytime on the BSM, but system monitor just wont pop up.

See? Granted, im still pretty new to the Linux world, but im confused. How do I make my old script work? If beyrl had left things like compiz did, than I wouldnt have any problems.

Well, I might as well ask, do you all have any ideas? Im seriously thinking about trying compiz. Beyrl is otherwise awesome (I turn most the eye candy crap off)....

---

### Post by blazercist on 2007-04-10
Personally I prefer Beryl for #1. ease of use ( a polished and complete plugin manager) ,#2. ease of use ( most of the popular plugins pre-installed ), #3. Features ( much more tweakablity of plugins e.g. distance from cube face, transparent cube, and more that I can't think of off the top of my head.)

Currently I am using compiz on Feisty because I had problems with beryl ( neither GTK nor emerald was working, not that compiz's window manager worked either im using GTK ) I would run back to Beryl if I could get it working again.

---

### Post by kwaanens on 2007-04-10
This thread may be getting obsolete, now that beryl and compiz are merging back together.

- Ketil

---

### Post by v8YKxgHe on 2007-04-10
Well as they are merging now, there is no Compiz vs Beryl :P

---

### Post by kingof1981 on 2007-07-03
well what should i say... 
i like Beryl much... Compizfusion too... 
Both looking great...  Compiz acting a littlebit faster and smoother then Beryl...
But Beryl can still do much more then Compiz...

Installing Beryl is easy, you find many how to's/script's outthere... and nothing to be  worry about...
Installing Compizfusion well it's easy too, but not quiet so much how to's/script's  (they work)... 

stable or not... hwo cares, everything can be fixed...

the best is to have both...
i do... hehe... bye... have fun folks...

---

### Post by CLI-Linux on 2007-07-09
> **AlexC_ said:**
> Well as they are merging now, there is no Compiz vs Beryl :P

Okay, but if they are merging, which name is taking over the project?  Compiz or Beryl???

***EDIT****

Duh, Compiz Fusion.

---

### Post by viking777 on 2007-08-07
I have three distros running on my laptop two have Beryl with near perfect desktop effects, one has Compiz with absolutely no desktop effects, so if you had the choice which would you choose?

Just in case some bright spark out there can tell me why I can't get Compiz to work I'll give you my setup:

Core2duo laptop 2Ghz
2Gb DDR2 ram
ATI Radeon X1600 graphics card
Latest ATI Driver 8.39.4
Gutsy Gibbon fully updated
In system settings/monitor+display my graphics card is set to 'ati' and my driver is set to 'fglrx'.

Every time I run:

```
compiz  --replace
``` 

I get:

```
       [: 222: Failsafe: unexpected operator
Checking for Xgl: not present.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting
                
```

I was going to replace it with Beryl, but it no longer exists in the Gutsy repositories so I am just stuck with Compiz that doesn't work.

Bring back Beryl:lolflag:

---

### Post by gmaniac on 2007-08-07
It says > Checking for Xgl: not present.
Since you have an ati card no composite can be done.
You must use the Xgl server. It is in every tutorial out there about
Ati cards.

---

### Post by viking777 on 2007-08-07
> **gmaniac said:**
> It says 
Since you have an ati card no composite can be done.
You must use the Xgl server. It is in every tutorial out there about
Ati cards.

Thanks for the reply gmaniac, I am sure it would be quite useful if I knew what it meant.

As for 'every tutorial out there' having something about it I just searched the forums with the following search terms 'ati xgl compiz'.
I got 4 pages of results none of which contained any tutorials at all so I guess they are not as widespread as you suggest.

Thanks for trying anyway.

---

### Post by forrestcupp on 2007-08-07
> **viking777 said:**
> Thanks for the reply gmaniac, I am sure it would be quite useful if I knew what it meant.

As for 'every tutorial out there' having something about it I just searched the forums with the following search terms 'ati xgl compiz'.
I got 4 pages of results none of which contained any tutorials at all so I guess they are not as widespread as you suggest.

Thanks for trying anyway.

[Here](http://ubuntuforums.org/showthread.php?t=488385&highlight=howto+compiz+xgl) is a HowTo to get compiz/fusion working on an ATI card with Xgl.

Because of ATI's crappy driver support, compositing isn't supported, so you can't do compiz with one.  Luckily, there's a program called Xgl which makes an opengl server for you that uses your ATI drivers.  Xgl *does* support compositing which makes it able to run Compiz/Fusion.  Unluckily, you can't really run opengl apps very well while you're using an Xgl server, but that's the only way to do it if you're using the proprietary drivers.

If you wanted to use the open source drivers, you can natively use compositing effects without Xgl.  Unfortunately, the open source drivers don't support all of the opengl extensions that your pretty new video card uses.  So opengl games may be unstable with the open source drivers.

The lesson in this is that ATI is not the best video card to be using in Linux right now, but you can't really do anything about that now.

---

### Post by viking777 on 2007-08-07
I actually found out how to start an xgl session now, it runs but unfortunately compiz --replace just gives me 'segmentation fault core dumped'.

I guess I will have to look at that error now.

Thanks for the link.

---

### Post by viking777 on 2007-08-07
Well I think I know why it won't work but I don't know how to fix it.

Thing is on my system emerald will just not run. If I type /usr/bin/emerald into a terminal it just hangs - nothing happens at all. This probably explains why none of the how-to's work for me, they all assume that emerald will run, well it won't.

I've tried reinstalling emerald and that makes no difference.

This is just taking up too much time.
As I said before, Bring Back Beryl!!!

Replacing a perfectly working window manager with this heap of crap is just mad. I am already a Linux convert and have time to mess with all this, just imagine the reaction of somebody new to this world that just expects things to work like they do in Windows.

Talk about shooting yourself in the foot.

---

### Post by forrestcupp on 2007-08-07
Well, emerald was a Beryl thing.  We are now using an updated Compiz core with some plugins that were adapted from Beryl to work with it.  That is what Compiz/Fusion is.

Emerald does not yet work with CF, but I think they might be working on it.  Uninstall Emerald, and maybe the rest will work correctly.

---

### Post by Steveway on 2007-08-07
What? I'm using Emerald with Compiz-Fusion at the moment.
No bugs whatsoever.

---

### Post by Ultra Magnus on 2007-08-07
> **forrestcupp said:**
> Well, emerald was a Beryl thing.  We are now using an updated Compiz core with some plugins that were adapted from Beryl to work with it.  That is what Compiz/Fusion is.

Emerald does not yet work with CF, but I think they might be working on it.  Uninstall Emerald, and maybe the rest will work correctly.

If you have beryl installed then installing fusion is easy and just type something like 

compiz --replace -c emerald

and you will have compiz fusion with emerald!

---

### Post by igknighted on 2007-08-07
> **forrestcupp said:**
> Well, emerald was a Beryl thing.  We are now using an updated Compiz core with some plugins that were adapted from Beryl to work with it.  That is what Compiz/Fusion is.

Emerald does not yet work with CF, but I think they might be working on it.  Uninstall Emerald, and maybe the rest will work correctly.

I use CF with Fedora and it uses emerald for window decs just fine.  I usually set it to use metacity's win-decs, but either works.

---

### Post by forrestcupp on 2007-08-07
Sweet!  They got Emerald working.  Early on they didn't have it ported to Fusion.  I haven't bothered to check since then.  So when I saw someone was having trouble with it, I assumed they still hadn't gotten it working.

---

### Post by sailor2001 on 2007-08-07
> **Ultra Magnus said:**
> If you have beryl installed then installing fusion is easy and just type something like 

compiz --replace -c emerald

and you will have compiz fusion with emerald!

I believe that is --replace c- emerald

---

### Post by viking777 on 2007-08-08
> **forrestcupp said:**
> Well, emerald was a Beryl thing.  We are now using an updated Compiz core with some plugins that were adapted from Beryl to work with it.  That is what Compiz/Fusion is.

Emerald does not yet work with CF, but I think they might be working on it.  Uninstall Emerald, and maybe the rest will work correctly.

With or without Emerald my system just freezes every time I run compiz --replace.

---

### Post by viking777 on 2007-08-11
Well, today's update to compiz has made some difference and I can now get some of the compiz effects although the way I have to go about it is quite strange.

Firstly I have to start an xgl session - that is expected. I then have to open a terminal and type emerald --replace, I then have to open another terminal and type compiz --replace, what is more I have to leave both of these terminals open as if I close either of them the effects disappear. I have tried the command 'compiz --replace -c emerald' both with and without the '--indirect-rendering' option. These do not work.

I do have a sort of desktop cube the only problem is it is not a cube it is a flat sheet. I know from using beryl that this is a matter of setting horizontal virtual size to 1 but I can find nowhere in the compiz settings manager to achieve this.

The last problem is that when I do this all my fonts and icons go microscopic, almost impossible to read. Easy enough to alter in Firefox with Ctl/+ but that doesn't help with everything else.

Well at least I know the effects work but at the moment they are unuseable.

If you are tempted to offer any solutions, please remember that I am running Gutsy on Kubuntu with an ATI Radeon X1600 video card.

---

### Post by viking777 on 2007-08-11
Well I found the answer to one of those questions at least, open Compiz settings manager, click on general options icon, and in there is a tab called 'desktop size'. Set Horizontal virtual size to 4,  virtual vertical size and number of desktops to 1.

Voila I have a cube.

But how do I get rid of these microscopic fonts?

---

### Post by misfitpierce on 2007-08-11
Indeed when I ran compiz fusion about a month ago I ran Emerald with it fine. At bootup I just had sessions auto hit compiz --replace and emerald --replace

---

### Post by viking777 on 2007-08-11
The answer to the font question seems to be that you have to go to each individual program and manually alter the font sizes - a bit of a bummer but it works.

The only oniy one I haven't managed to crack yet is Firefox. The menus and toolbars that is the font on the web pages can be increased by Ctl/+ (temporarily that is).

---

### Post by viking777 on 2007-08-11
I kinda thought that this might happen, playing around with the settings on my xgl login (the one that runs compiz) totally hosed my kde login, so much so that I have had to resore this mornings disc image to get anything to work again.

I return to the original point of this post, why,oh,why, has beryl been replaced by this piece of nonsense??

---

### Post by tsumiro on 2007-09-19
ima use compiz cuz they seem to be on it.

i tried downloading the newest beryl from their site, and it turned out to be a dead link... so compiz it is.

btw, i looked at the screenshots on compiz and the ones on beryl, and it looks like compiz does more... :lolflag:

---

### Post by RAV TUX on 2007-09-19
> **caspian said:**
> I've used Compiz for quite a while, and have been very pleased with it. I've never used Beryl -- but I'm wondering what it has to offer. That is, what advantages does Beryl have over Compiz? For those of you who use Beryl -- do are you pleased with it (over Compiz?)

I'm wondering whether I should make the switch.

Thanks!Transcend your current existence and become enlightened, enlightenment 17 that is. ;)

---

### Post by Cariboo1938 on 2007-11-04
> **hanzomon4 said:**
> :confused: Ok...... Well Beryl is great very polished once you **[COLOR="Blue"]have your system setup right.[/COLOR]**
I'm about to install Beryl and I wonder what you mean by "**[COLOR="Blue"]have your system setup right.[/COLOR]**" 
What would be absolutely necessary to do?:confused:

---

### Post by bruce89 on 2007-11-04
Beryl is a dead fork, Compiz fusion replaces it.

---

### Post by Cariboo1938 on 2007-11-04
> **bruce89 said:**
> Beryl is a dead fork, Compiz fusion replaces it.
Does it mean it will not be supported by future releases of Ubuntu?

---

### Post by Gremlinzzz on 2007-11-04
They are both fun but after a while i just shut it down.It became whats the word  oh yeah boring. plus it uses resources i don't think it servers a real purpose except as a new toy too show off.:lolflag:

---

### Post by Cariboo1938 on 2007-11-04
> **Gremlinzzz said:**
> They are both fun but after a while i just shut it down.It became whats the word  oh yeah boring. plus it uses resources i don't think it servers a real purpose except as a new toy too show off.:lolflag:
Thanks,
very interesting thought.....
I'm just wondering about the packages I found under the "Installed" status with Synaptic Package Manager:

compiz
compiz-core
...-gnome
...-gtk
...-plugins
and I thought they are there for some reason. 
Then I remembered  what 'bruce89' posted in this thread: > Beryl is a dead fork, Compiz fusion replaces it. 
Then I wondered what the connection would be between compiz and beryl, because all the beryl packages I found under the "Not Installed" status with S.P.M. As you see, I am :confused: 
The 'show off' aspect is OK for me because I see this more as a learning experience and playing with 3D effects. 
But to be honest, I have no clue how to begin with the installation. Maybe you can give me some hints?

---

### Post by Gremlinzzz on 2007-11-04
beryl was easy compiz comes pre installed  this site will help 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by Cariboo1938 on 2007-11-04
> **Gremlinzzz said:**
> beryl was easy compiz comes pre installed  this site will help 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
Thank you Gremlinzzz...
It is a great site and it certainly helps
Thanks again
Cariboo

---

### Post by delfick on 2007-11-04
> **bruce89 said:**
> Beryl is a dead fork, Compiz fusion replaces it.

technically you're incorrect in saying that.

compiz fusion doesn't replace beryl as such

because beryl was it's own window manager

whereas now, we use compiz as the window manager
and compiz fusion is now the extra functionality that was provided by beryl, plus more

as in plugins, configuration system, settings manager.

.....

@Cariboo1938 , if you still have issues trying to get compiz/compiz-fusion up, I suggest doing a search on [forum.compiz-fusion.org](forum.compiz-fusion.org) :D

---

### Post by bruce89 on 2007-11-04
> **delfick said:**
> technically you're incorrect in saying that.

The best kind of incorrectness.

---

### Post by delfick on 2007-11-04
> **bruce89 said:**
> The best kind of incorrectness.

lol

---

### Post by faical117 on 2008-01-18
i think compiz is more stable than Beryl ! :popcorn:

---

### Post by IHATEDLINK on 2008-04-18
I like compiz the most, it's more friendly :)

---

### Post by LaRoza on 2008-04-18
> **IHATEDLINK said:**
> I like compiz the most, it's more friendly :)
[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---

