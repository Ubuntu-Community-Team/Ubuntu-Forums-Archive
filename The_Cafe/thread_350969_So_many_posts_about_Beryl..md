---
title: "So many posts about Beryl."
date: 2007-02-01
forum: The Cafe
---

### Post by marianom on 2007-02-01
I'm surprise to see so many posts of beryl everyday. Clearly it's the piece of soft that more posts have in the entire forum. 
I don't use it so I can't tell but maybe somebody can comment:
Is the documentation for Beryl so poor that people need to search additional help to make it work? Is it that hard to configure? Is it buggy in general or buggy in Ubuntu? Why do you use it if it gives you so many headaches?

I feel that when you have something that takes so many questions everyday, it's time to find a way to get rid of the problem ergo fix it (eg. if the docs are bad, improve them, et cetera).

---

### Post by pyrforos on 2007-02-01
i can say a few thinks about that..Its  by far the most beautifull decorator ever seen...BUT the beryl guys seems that they don't test very well every version of beryl of just they don't care if some people use their pcs for work and they loose their preciouw time to deal with these problems...
Sorry about that guys.. but i cant stand this anymore... :( :( :(

---

### Post by mips on 2007-02-01
> **pyrforos said:**
> i can say a few thinks about that..Its  by far the most beautifull decorator ever seen...BUT the beryl guys seems that they don't test very well every version of beryl of just they don't care if some people use their pcs for work and they loose their preciouw time to deal with these problems...
Sorry about that guys.. but i cant stand this anymore... :( :( :(

Works a charm in Sabayon but I do not use it.

---

### Post by themusicwave on 2007-02-01
I installed beryl a few days ago on my laptop and attempted to do so on my desktop.  It was a horribly painful process that took hours.  I uninstalled it from my desktop since it just seemed to make X crash over and over.  The problem was my ATI card i guess.

On my laptop it installed fine, but is quite buggy.  At times something as simple as opening a firefox window will cause the screen to turn black and the entire computer to lock.  I never saw a total Ubuntu lock until I installed beryl.

And to answer your question about docs, they are kinda bad.  The problem I ran into was ever HOWTO was different, and following a few of them simply toasted X to the point where I was in command line only mode.

Beryl looks pretty, but it is way too buggy for me to continue running it.

---

### Post by eXisor on 2007-02-01
First off, I completely disagree with pyrforus and themusicwave. Beryl is beta software and the formal releases are quite good, on the three systems I tried it on, anyway. The nightly builds suffer from the same malady that all nightly builds have, namely, they're for power users and/or developers to test and help debug.

Having said that, I'll answer the OP's question:

1) Beryl provides a vista equivalent (better IMO) 3d desktop. That is why it is so popular, and there are so many posts. People see it on YouTube and Digg and want it for themselves. 

2) There are many beryl problem posts because beryl requires a working graphics accelerated setup. If you have DRI or XGL running properly, installing and getting beryl setup is easy. So the problem is not beryl, but the prerequisite to being able to use beryl. The same prerequisites are required to run 3d games, but I don't see people blaming WoW when they can't get that going. Go figure.

3) Beryl is beta software, so a few hickups on some systems is to be expected. Only when beryl goes 'live' do you have the right to bleat about this or that problem. Until then be grateful that they don't make you sign up to be a beta tester like many other package devs do.

4) The documentation is a work-in-progress. If you feel you can do better, I'm sure the devs will welcome your vast expertise. Frankly, after my initial setup using various HowTo's here and on the beryl site, I haven't needed the documentation, and I use the nightly svn builds so graciously provided by trevino.

Get real folks. You want the free meal, but want the beryl devs to eat it for you too? If you're not ready for beta software then walk away until you are.

---

### Post by fuscia on 2007-02-01
use automatix (bleeder edition) to install it and you'll be fine. too much 'christmas toy' and not enough 'underwear and socks', for my tastes. and, i still think e17 is prettier.

---

### Post by Brunellus on 2007-02-01
I have posted a [very stern disclaimer](http://www.ubuntuforums.org/showthread.php?t=349732) in Absolute Beginners.'

I don't want to turn anyone away, but I do wish people better understood the risks of using beta software.

---

### Post by Ghil on 2007-02-01
it's Beta, but most people overlook this to have the latest shiny thing. -_-

---

### Post by LostShootingStar on 2007-02-01
I almost "feel bad" for the Beryl developers. while the software looks beautiful, and works 95% of the time (for me), its very closely integrated into X, so any little bug is going to cause big problems, as opposed to other sandalone apps that only have to worry about themselves. I think if it was integrated as part of X, or built with X from the ground up, instead of an addon to X, it would be a lot more stable.

---

### Post by justaguynpc on 2007-02-01
I would have to agree, until yesterday, that is.

I tried Sabayon, and honestly liked it, however, was unable to connect to the internet for some odd reason, so had to leave it in the dust.

It has been a personal goal to try beryl again, but the documentation, opinions, expressed issues, and frustration expressed in the forums kept me from trying it.

Yesterday, however, I decided to give it a go, since I have Kubuntu Edgy on one partition, and Ubuntu Edgy on the other.  I like to swap back and forth for variety, and  ¨tweaking purposes¨.  So, if I was to run into unmanageable issues, I was not without Ubuntu as a whole.  The daunting task was to decide which HOWTO to follow, what opinions were valid, in addition to potential fixes I would be faced with.

Success was found by using the Ubuntu:Edgy wiki.  I am up and running, without any problems.  Was a bit scared to see that while I was running the generic kernel previously, the 386 kernel was installed as part of the beryl package.  Not to fear though, after rebooting, I was able to verify that beryl would run under my generic kernel just as well.  This morning I was faced with updates to the whole beryl install from the day before.  While biting my tongue, I upgraded, still without any noticeable compromise in function, albeit, I now have more plugins, more choices, just more ¨goodness¨.

You will never know unless you try, keeping in mind, as stated earlier, ensure you have the hardware necessary for it not just to work, but work well.  Try not to be too put out by all the posts you read here at the forums, we all have our own level of linux knowledge, and differing experiences.  I was lucky in that my install was without flaw, and I was not needing to post yet another failed beryl thread......

Cheers

---

### Post by hanzomon4 on 2007-02-01
Beryl, or Compiz, is not really the problem...

Both are easy to install but configuring X can be a problem for some. Most people use to use XGL to run beryl/compiz, XGL was(is?) difficult to setup and it can cause problems with watching videos and playing games. Nowadays more people use AIGLX which is much easier to setup and avoids the problems XGL encountered with videos and games. If you have an old ati card(x300?), intel, or nvidia graphics you can use AIGLX, with Nvidia you just install the driver. AIGLX/XGL is basically the accelerated xserver you need to run beryl/compiz, in x.org 7.1 AIGLX is built in. Getting an accelerated xserver is what takes up most howto's as well as adding the particular repos  needed to get compiz/beryl.  

The only thing I had to do to get beryl to run was install the Nvidia drivers and beryl, thats all.... Also the beryl, and compiz, devs do care about problems end users experience, beryl is fixing bugs at break neck speed and I'm sure the same is true for compiz. If you go to the beryl website they have a wiki that explains just about everything  from install to "how to use plugin-x". Why  do you see so many beryl post :confused:  
I guess because it's popular and a highly political topic....

---

### Post by ronmarley1 on 2007-02-01
> **Brunellus said:**
> I have posted a [very stern disclaimer](http://www.ubuntuforums.org/showthread.php?t=349732) in Absolute Beginners.'

I don't want to turn anyone away, but I do wish people better understood the risks of using beta software.
I agree with your caveat Brunellus, with on addition.  Beryl is just now out of ALPHA and into the BETA stage (as of about two weeks ago).

---

### Post by prizrak on 2007-02-01
The documentation is mostly lacking because it is lagging behind releases. For instance the settings manager is completely different from like 2 versions ago. New versions also do break stuff occassionaly. On my system for example my trailfocus rules are followed about 50% of the time despite it working 100% with one of the previous versions.

As has been said it's beta, a very well working beta (better than any proprietary beta I ever seen) but still a beta and is gonna have issues. It does liven up your desktop with very little effort (as long as you have 3D working on your video it will run fine) and is actually quicker than normal desktop. Not to mention there are certain productivity enhancements such as the Expose trick and Alt-tab.

---

### Post by mips on 2007-02-01
> **justaguynpc said:**
> 
I tried Sabayon, and honestly liked it, however, was unable to connect to the internet for some odd reason, so had to leave it in the dust.


What problems did you have ? Maybe post your problem here: [http://ubuntuforums.org/forumdisplay.php?f=166](http://ubuntuforums.org/forumdisplay.php?f=166)

---

### Post by xpod on 2007-02-01
Todays update was the first real issue iv`e had with beryl and although it is a bit of a pain i cant see no reason why i would ever complain about dev`s not doing their job properly.

Complaints about problems being unacceptable for people who use their PC`s for work are just plain silly if you ask me as why would anyone in their right mind risk a work pc with software that does have the potential to cause problems:confused: 

I`ll always be pretty much a "noob" with all this computer & OS lark but some of the comments i see by people who should in fact know better are just beyond belief at times.

Too many people more concerned with outdoing their Vista using colleagues possibly:wink: 

Anyway,even with my missing titlebars the new effects are pretty cool.:D 
Of course though,this isn`t my main setup but just the one i play about on to make sure things are "safe" to do first before i go messing up systems i`d rather not mess up.

---

### Post by fuscia on 2007-02-01
> **Brunellus said:**
> I have posted a [very stern disclaimer](http://www.ubuntuforums.org/showthread.php?t=349732) in Absolute Beginners.'

I don't want to turn anyone away, but I do wish people better understood the risks of using beta software.

is there a standard by which a piece of software is delared 'beta'? it's my vague impression that there isn't, or at least, there is a wide range of interpretation of 'beta', just as debian and ubuntu seem to have differing notions as to what constitutes 'stable'. (i'm more asking than making a point, btw.)

---

### Post by glabouni on 2007-02-01
> **marianom said:**
> Is the documentation for Beryl so poor that people need to search additional help to make it work? 
Is it that hard to configure? 
Is it buggy in general or buggy in Ubuntu? 
Why do you use it if it gives you so many headaches?

IMHO [user documentation for beryl]("http://wiki.beryl-project.org") is good enough considering that beryl is a very active work in progress.

I guess most people who are asking questions about beryl in here have not looked into the documentation, didn't really search the web for a way to fix it by themselves, or simply lack the knowledge to do so.
I guess many are trying beryl after having seen a youtube video and are expecting it to work out of the box. 
The thing is beryl is a work in progress, it is beta software and can break your xserver session. so this is not something you wan't to use if you don't have at least basic knowledge of xorg and how to fix it.

As it is a very active project, It can be very buggy or broken one day, fixed the next day, and new bugs emerge the day after. This is the way it usually works with work in progress.
But release cycle is fast and beryl is constantly evolving.
best way to avoid a bad surprise is to avoid updating a working beryl install. making a systemwide backup before upgrading is recommended.

Once installed It is working out of the box and offers several effects activated by default. not that hard to configure the basics but can be tedious to go deeper without proper knowledge of what you're doing.

Since I've seen [Sun Microsystems' executive vice president 2003 demonstration video of Project Looking Glass.]("http://www.sun.com/software/looking_glass/demo.xml") I firmly believe 3D desktop can add something to my computer experience.

XGL/Compiz under dapper was my first attempt at a 3D desktop on a test machine, I've made a longer ubuntu involved friend discover it and he came back to me telling me about beryl. When I switch my main machine to edgy, I just used beryl instead of compiz as it made things easier. 
To be exact beryl never gave me headaches, xorg configuration and xserver acceleration did, but now it works smoothly on my computer. I know it is beta and I know what beta means so I'm not surprised or upset when it crashes (smoothly that is), or prevent my xserver session from strating. I'm upset at myself for not knowing how to fix it, but I don't blame the beryl guys, I praise them for their work.

oh and beryl allows me to run kiba-dock.


for those interested about project looking glass:
- [youtube video of project looking glass running under ubuntu]("http://www.youtube.com/watch?v=EjQ4Nza34ak")
- [Project Looking Glass official home page]("http://www.sun.com/software/looking_glass/") 
- [wikipedia entry about project looking glass ]("http://en.wikipedia.org/wiki/Project_Looking_Glass")
- [LG3D live cd v3 (Looking Glass 3D Live CD)]("https://lg3d-livecd.dev.java.net/Web-Site/Welcome.html")
- [Sourceforge download page for LG3D live cd]("http://sourceforge.net/project/showfiles.php?group_id=144229")

---

### Post by Brunellus on 2007-02-01
> **fuscia said:**
> is there a standard by which a piece of software is delared 'beta'? it's my vague impression that there isn't, or at least, there is a wide range of interpretation of 'beta', just as debian and ubuntu seem to have differing notions as to what constitutes 'stable'. (i'm more asking than making a point, btw.)
Beryl is "beta" by the developers' own admission.

---

### Post by chipmonk010 on 2007-02-01
I just wanted to add my thanks to the beryl devs. Last release when their were problems the devs responded quickly and even kept users on this forum updated on progress. They really have been handling everything extremely well.

I use beryl on my desktop and it works great with my nvidia graphics card. I like most others think the problem lies with enabling accelerated graphics and a lack of knowledge on the users part. 

I have a suspicion there are 100 time more problems with ati cards then nvidia because of the lack of a really good driver. If i were u id go complain to ati about not having a good linux driver and not releasing the hardware specs for someone else to write one.

---

### Post by DaveArb on 2007-02-01
> **fuscia said:**
> is there a standard by which a piece of software is delared 'beta'? it's my vague impression that there isn't, or at least, there is a wide range of interpretation of 'beta', just as debian and ubuntu seem to have differing notions as to what constitutes 'stable'. (i'm more asking than making a point, btw.)

As Brunellus pointed out, alpha, beta and the like are assigned by the developers. Generally, an alpha release is one that isn't expected to work properly in most circumstances. Back in the Good Old Days, alphas were usually for internal testing only. The beta would be announced when the devs felt like someone outside the group could probably install it and have some chance of most of the features working. This is usually much more liberal in open-source projects, though.

Neither alpha nor beta really have any relation to an individual distribution's view of stable, unstable, testing, or whatever.

/signed/ An old developer ;)

---

### Post by Brunellus on 2007-02-01
> **DaveArb said:**
> As Brunellus pointed out, alpha, beta and the like are assigned by the developers. Generally, an alpha release is one that isn't expected to work properly in most circumstances. Back in the Good Old Days, alphas were usually for internal testing only. The beta would be announced when the devs felt like someone outside the group could probably install it and have some chance of most of the features working. This is usually much more liberal in open-source projects, though.

Neither alpha nor beta really have any relation to an individual distribution's view of stable, unstable, testing, or whatever.

/signed/ An old developer ;)
I had the sense that it went something like this:

ALPHA= "OK guys.  We've only implemented half of the features we set out to implement in the specification.  The latest build crashes and may kill kittens.  But I have some good news--it compiled without any errors!"

BETA=  "Congratulations, team.  We've pretty much feature-complete.  there are a bunch of showstopper bugs, though.  Should be good enough for regular testing, but don't trust your life to it."

RC= "FEATURE FREEZE!  Anything not implemented yet is gonna have to wait.  Squash 'em bugs!"

---

### Post by FuturePilot on 2007-02-01
It's working perfectly for me. The whole install and configuration took me about 5-10 min. Thanks to a nice How To on the forums here.

---

### Post by marianom on 2007-02-01
So, as far as I understand:
1- beryl is in a constant alpha/beta state.
2- users -no matter this- download and install it from, let's say, the night build
3- there are users that don't take time to read warnings or proper docs and go with it and install, apparently not caring about some problems with beryl might stop you from using your machine.
4- fair advice: nobody, at least not me, is saying that beryl is a buggy or bad software: it's a complex thing and takes time to properly set it up.

And that's why there are so many posts in the forums. Is it right?

---

### Post by darkhatter on 2007-02-01
Feisty Fawn is going to change all of this. personally I don't use xgl or alxgl(whatever the red hat version is called) so I think I miss a lot of issues that people have. Some of the older versions gave me problems but the newer ones have been pretty good (by pretty good I mean no more lock ups).

---

### Post by hanzomon4 on 2007-02-01
> **marianom said:**
> So, as far as I understand:
1- beryl is in a constant alpha/beta state.

No it's beta at the moment(2.0 rc1) the 2.0 release is not that far off so to say that it's in a constant beta state is way off. All software is constantly being worked on but if you stay with the official release you shouldn't worry about it.

> **marianom said:**
> 2- users -no matter this- download and install it from, let's say, the night build No install the official release(not svn snapshots) if you have accelerated x setup or you don't mind setting it up. Depending on your hardware this could be painless(nvidia, intel) or torture(ati, well thats what people tell me) 
> **marianom said:**
> 3- there are users that don't take time to read warnings or proper docs and go with it and install, apparently not caring about some problems with beryl might stop you from using your machine. Sort of, most people that install it know about the warnings but want berl/compiz bad enough to ignore those warnings. When some of these users run into problems they ask for help, although some get pissed and curse all of "them fancy effects". Also accelerated X(or driver) problems get unfairly attributed to beryl/compiz leading to the baseless claim that beryl/compiz is beyond buggy and unusable. 
> **marianom said:**
> 4- fair advice: nobody, at least not me, is saying that beryl is a buggy or bad software: it's a complex thing and takes time to properly set it up. Yeah because beryl/compiz is dependent on new stuff like accelerated X and stuff like hardware with closed drivers or non-working(no 3d) open drivers

> **marianom said:**
> And that's why there are so many posts in the forums. Is it right?I guess......

---

