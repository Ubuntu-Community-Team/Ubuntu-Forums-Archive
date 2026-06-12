---
title: "Linux is really just a cruel joke, right?"
date: 2010-03-07
forum: Testimonials &amp; Experiences
---

### Post by WhyIsLinuxSoCruel on 2010-03-07
Greetiings,

So, I decide to try this linux stuff out.  I grab me a few ISOs of distros, burn 'em to CD and install 'em each on a removable HDD.

Sounds pretty simple, right?  Well, it hasn't been for me.

I'll just stick with Ubuntu 9.10 in this post.

1.  I notice when I get my installs done that I can only successfully burn the ISOs at 4X speed.  Hmmm.... I think....  That's weird!  Must be a HW error.  So after about three days of research I find that there is some sort of feud going on between people between cdrecord vs. this thing called wodim.

What do I have on all my distros?  Looks like cdrecord.  Oops!  Nope.  It's actually wodim masquerading as a link named cdrecord!

Now I don't know what is going on, so I revert to XP and install it.  What do you know?  Nero 7 under XP burns as fast as my media will support 16X for DVD-R and 8X for DVD+R.  Cd-Rs burn at some silly fast speed like 52X.

I switch back to Linux to see if I'm making errors cause 3AM has rolled around again and I've got nothing accomplished other than installing XP, and Ubuntu 9.10 has errors if I try to burn either DVD media faster than 4X or CD-Rs faster than 8X.  I give up.

2.  So I deal with my ISO images that take forever to burn under Linux and decide to try to get two machines (192.168.1.101 and 192.168.1.106) running Ubuntu 9.10 to talk to each other over ethernet.  Ping works great both ways.  Cool!  

I then try to telnet from one to the other.  Oops!  Looks like I forgot to install telnetd.  Telnetd seems to install OK when I try it yet the connection is still refused on both machines.  I do some more research and 3AM rolls around again.  Seems like telnetd is included, but it's not supported.  I need to use xinetd.  Nope.  That info must be wrong or old.  I give up.

3.  I think TOR sounds pretty cool, so I look into it and Privoxy.  I research them and install them.  Cool!  The tor test gives me a green box and says I am using Tor successfully.  Then I find a URL that says DO NOT USE THE TOR THAT COMES WITH CANONICAL!!!!  USE THE LATEST AND GREATEST TOR AND PRIVOXY FROM THEIR OWN HOME PAGES.  So I uninstall Tor and Privoxy that I just installed that came with Ubuntu and go get the other stuff.  3AM rolls around again, but this time I've successfully installed the latest and greatest Tor and Privoxy and all seems to be fine.  I retire to bed victorious!

A few days later I fire up the Ubuntu box and, since I'm a good little user, I check for any updates.  Yep there are updates.  Cool!  I install them.  OMFG!!!!  It uninstalled the newest Tor and Privoxy and replaced them both with the older stuff from Canonical.  I give up.

...

So here I am.  It's 2:45 AM and I've only learned one thing about Ubuntu 9.10 and Linux in general over the last few weeks:

I have no idea what info to trust on the web sites out there!

And Ubuntu has this extra layer of abstraction where searching for 9.10 is not good enough.  I need to know if it's Creepy Chameleon or Korkys Kloset or Zeppos Zippo.  Why call it 9.10 if that's not what you're going to call it later?  Even when I find out the pre-school alliteration name and use that instead of 9.10, I find that the info on what needs to be installed or done to solve a problem is still directly contradictory on tons of web sites.

I'm trying here, guys.  I really am trying, but this is wearing me down.

I don't really care so much about Tor and Privoxy, but I'd like to at least get either 1 or 2 solved.  

For an OS that is patterned after 1970's Unix, there are sure a ton of inconsistencies.

I also forgot to mention that I've bought about 6 Linux books, but they don't seem to be any good.  The info looks great in the book but there's always something different between distros or versions of the same distro.

I was really, really hoping Win 7 would be the first windows I could skip buying, but now I'm not so sure.  Linux always ends up beating me up and leaving me clueless at 3 AM, dog-tired and with nothing to show for it.

I'm using the following mobos:

Asus A7N8X (1 machine) (Athlon XP 3000+)
Asus A7N8X-E Deluxe (Athlon XP 3200+) (2 machines) and
Asus A7V333 (Athlon XP 3000+) (3 machines)

Each machine has at least 1.5 GB of memory and all HW works great when XP is running on it.  That's not a cheap shot at Linux.  I'm simply trying to show that I don't believe there to be a HW problem.  memtest can run for days without any errors on each machine as well.

Sorry if I sound like a jerk, but I've been knocked around pretty bad here pretty consistently.  

Any help is GREATLY appreciated!

Well, I see it's 3AM, so as usual, my Linux shift is over for now.

Peace!

---

### Post by GregBrannon on 2010-03-07
Now that you've gotten that off your chest - and that's a good thing - perhaps you could break down your questions / problems into single-portion, bite-sized posts.  I think you'll get a better response and the right help.

It sounds to me like you have A LOT to show for your efforts and are simply at the tweaking stage.

Good luck!

---

### Post by AnimalMagic on 2010-03-07
Ha ha! I sympathise! :-)

Try Mint - seems to be Ubuntu without the bugs, though the green theme can be hard to get used to...

You can switch off updates for selected products which would stop the issues with TOR. Can't quite remember how, so someone else would have to advise...

It's worth persisting. I'm no zealot, windows and linux are just tools and I use both as required, but if it came down to it, I would use linux by preference.

---

### Post by soul_rebel on 2010-03-07
There is an APT archive for tor that will let you easily install it and keep it updated to the very latest release. I think you will easily find it.

Then I like to tell you a hard truth about linux: it takes at least a year to get good at using it, but if you stick with it long enough you will get some pretty nice computer skills you won't get in ten years of windows.
I use it since 2004 and I still learn a lot, but now I can do the craziest things. Just keep going. Never boot windows for something you know how to do in linux and each week choose something new to learn.

---

### Post by HermanAB on 2010-03-07
Hmm, well, Ubuntu is 'Linux for Masochists'.  If you want 'Linux for Dummies' then you should install Mint, Mandriva or Puppy.

---

### Post by hansdown on 2010-03-07
> **HermanAB said:**
> Hmm, well, Ubuntu is 'Linux for Masochists'.  If you want 'Linux for Dummies' then you should install Mint, Mandriva or Puppy.

Much better phrased, than I would do.

Kudos HermanAB.

---

### Post by BenAshton24 on 2010-03-07
> Linux is really just a cruel joke, right?
Aww, we've finally been caught out :(

---

### Post by wojox on 2010-03-07
#1 I always burn at the lowest speed possible. You get a better more precise burn.

#2 To have 101 and 106 log on and talk to each other, you need to install ssh server on both/either machine. ssh client is already there.

#3 See here: [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor) install the ppa's.

---

### Post by Fenris_rising on 2010-03-07
Ubuntu is great IMHO I started with 8.04 and am now at 9.10 all has been well other than self induced destruction =D

Updates are listed so check them and untick anything you don't want udated by the canonical repo's.

Stick at it. Things will get easier as you get better versed in the 'whys and wherefores'

Burning OS ISO's I have always burned at a slow speed on windows and Linux. It is safer and less likely to be effected by Murphy's law.

I am no Linux expert but with determination and this forum the transition and continued use to Linux Ubuntu has been fun, even when challenging, and I am free of windows.

good luck

Fenris

---

### Post by TenPlus1 on 2010-03-07
Your not stuck with using Brasero/wodim to burn your discs, the repository has xfburn and k3b if you wanna try other burning programs...  I use XfBurn and it can burn full speed but as mentioned before, burning at high speed sometimes results in a dodgy disc...

---

### Post by eriktheblu on 2010-03-07
Cruel joke? No a cruel joke would would be to sell you an operating system for $100-300 US that is excessively vulnerable malware, comes prepackaged with entirely useless software, and has a non-standards-compliant browser that cannot be removed.

---

### Post by ankspo71 on 2010-03-07
I can understand the frustrations. I was also frustrated with such things as cd burning speed, and also some other differences between windows and Linux, like the performance differences between windows and Linux flash players in which I had to upgrade my hardware to resolve. 

I'm not sure why your tor and privoxy were reinstalled with older versions, but one thing I can think of is that you installed one version supported by Ubuntu, then Ubuntu suddenly later decided that it is no longer going to support it. However, I haven't experienced that particular problem except for when I upgrade from one Ubuntu version to another newer version of Ubuntu.

Is there any reason why you don't choose to dual boot between windows and Linux? When I first started using Linux that is what I chose to do. That made it much easier to get used to using Linux instead of diving right in. Note that this way you will be able to burn cds at maximum speed (with windows), as long as you copy your files over to the windows partition/(directory) first, because by default windows can't read linux partitions.

For transferring files between computers, Ubuntu is now making it easier with Ubuntu One which has 2gb of free storage (I think), then there is [http://www.dropbox.com/](http://www.dropbox.com/) that allows you to do the same with the same amount of space. I never had to share devices or use a VNC type of setup so I don't know how well those work.

Good luck.

---

### Post by WhyIsLinuxSoCruel on 2010-03-12
> **ankspo71 said:**
> I can understand the frustrations. I was also frustrated with such things as cd burning speed, and also some other differences between windows and Linux, like the performance differences between windows and Linux flash players in which I had to upgrade my hardware to resolve. 

Thanks.  I know it's not just Linux or Ubuntu.  Like they say: Learning anything worthwhile takes time and effort.  If it were easy, then nobody would even be using Windohs.

> **ankspo71 said:**
> I'm not sure why your tor and privoxy were reinstalled with older versions, but one thing I can think of is that you installed one version supported by Ubuntu, then Ubuntu suddenly later decided that it is no longer going to support it. However, I haven't experienced that particular problem except for when I upgrade from one Ubuntu version to another newer version of Ubuntu.

I'm not quite sure how that happened either.  I do know it happened, though.  I'll revisit those later, though.  They're not a priority for me.

> **ankspo71 said:**
> Is there any reason why you don't choose to dual boot between windows and Linux? When I first started using Linux that is what I chose to do. That made it much easier to get used to using Linux instead of diving right in. Note that this way you will be able to burn cds at maximum speed (with windows), as long as you copy your files over to the windows partition/(directory) first, because by default windows can't read linux partitions.

Ah, sorry, I should have mentioned.  I have about 5 machines all with removable HDDs so I am swapping between and among XP, Vista, and all the flavors of Linux whenever I want.  I also invested in a couple of KVM switches so I can save some space.  

I always keep one machine running XP connected to the internet for web searching purposes even when I'm playing with Linux.  I've dual booted before and only narrowly avoided disaster several times.  It was after enough close calls to my data on my Windows partitions that I decided to keep the two animals separate, and only run one at a time.  My machines are not great, they're all circa 2002 or so, but they're good enough for me, so I'm pretty pleased with the setup.

> **ankspo71 said:**
> For transferring files between computers, Ubuntu is now making it easier with Ubuntu One which has 2gb of free storage (I think), then there is [http://www.dropbox.com/](http://www.dropbox.com/) that allows you to do the same with the same amount of space. I never had to share devices or use a VNC type of setup so I don't know how well those work.

Ah, OK.  It's just that I thought Linux would have some sort of mechanism built in for easy sharing files between computers.  I guess there is in Ubuntu.  Another user just mentioned it to me today, so I will check that out.  

My big problem is that I'm not satisfied doing things only through the GUI.  I've always been a fan of the command line, and new users tend to hate that, so it's a little tougher for me to find info.

I want to know what's going on "behind the gui curtain" so my position is different than many other folks new to Linux.

Many thanks for taking the time to reply!!  I greatly appreciate it.  I will keep on struggling since I know things will inevitably get easier.  It's just really rough sometimes when you've had three unsuccessful nights in a row that kept you up until 3AM and you learned basically nothing.

> **ankspo71 said:**
> Good luck.
Thanks.  I'm going to need it!!  :)

Thanks again!

Rick

---

### Post by spiderbatdad on 2010-03-12
I'll just add: It gets easier.

---

### Post by anewguy on 2010-03-12
Okay, I may be remembering something incorrectly here, but I thought you could use Samba to share files between computers?

Best of luck - as it has already been said, it just takes a while and fighting 1 battle at a time, and things get easier.

Dave ;)

---

### Post by achase79 on 2010-03-12
The reason the programs (tor) may have gotten overwritten is that you installed using synaptic or apt and then installed from source without removing it from synaptic first.  I always use checkinstall to create a .deb file when I compile from source.  As long as you correctly set the version when prompted in checkinstall, you won't have more upgrade issues.

---

### Post by MSich on 2010-03-12
I'm a relative Linux newbie but I have learned a few things that make my experience better.  I jumped into Fedora about 8 years ago and I didn't know enough about it.  It was frustrating and I ended up going back to Windows after a month or so.  Three years ago I jumped back into Fedora and muddled through for 3 years without learning much.  As I was leaving Fedora behind I got some great advice and it's been a fun experience ever since.

You sound a lot more savvy then me, but here it is anyway.

1. Read first, read second, read third install fourth.
2. Don't search all over the web, when all the answers are right here in the forums.  Ask the users, they know the answer.  If you don't get what you need, ask again, the answer is here.
3. Don't try to customize everything all at once.  Work on one thing until it works the way you want, and then move on to something else.

Basically, the guys and gals on these forums have taught me everything I need.  Stick with it, and you'll be glad you did.

---

### Post by swoll1980 on 2010-03-12
I use Nero Linux it's only $15 I got mine for free. It works really well, and is worth every cent of that $15

---

### Post by aviedw on 2010-03-13
It seems every new linux experience promotes a rant. Its simply the nature of the learning curve. I've had my many and they're all expected. But for future reference word your questions in simple and direct terms and if anybody knows how to help they will. This forum is the best support system i have ever experience period.

---

### Post by cariboo on 2010-03-13
This is not s support question, more an opinion piece. Moved to T&E

---

### Post by J_Stanton on 2010-03-13
> **AnimalMagic said:**
>  Try Mint - seems to be Ubuntu without the bugs, though the green theme can be hard to get used to...  To me, Mint is ubuntu with unneeded. If you can't figure out ubuntu, you are not a computer person in the least. You need someone to hold your hand.

---

### Post by armandh on 2010-03-13
every body is a noob at the beginning
I was lucky, 7.04 just worked.

so I knew right off how good it could be.

I have since learned my biggest source of failed installs are worn out cd/dvd drives.

second place goes to crappy on board video. [S3 or no 3D]

some things are not fixable
and forget the old and obscure
trust me 
it is not worth the time.

but for most good compatible hardware
OOTB Ubuntu is a slam dunk!
even if today, the failed install looks like a cruel joke.

---

### Post by stalkingwolf on 2010-03-13
I second K3B it works for me.  Mint also has its uses, as do the 15 or so other distros i have copies of.  Mostly forensic and tool distros but also
lite and various others.  Two that I have found interesting and fun are UE
 and SuperOS.

---

### Post by zugu on 2010-03-13
Ha ha, oh wow. You want to experience the strong anonymity Tor provides by using modified, unofficial, outdated packages in the Ubuntu repositories. Now this is a really good joke.

You should **_never_** rely on downstreams for critical security and anonymity software like Tor or TrueCrypt. Always get your stuff from the primary source.

---

### Post by uRock on 2010-03-13
I think I will be staying with buying Lenovo desktop machines. I did not have any of those problems. I burn CDs and DVDs at top speeds and they come out flawless.

Changing to Linux is like parking a Mustang and getting into a Lamborghini. They are both built differently and they both handle differently. It takes a lot of getting used to, but once your done, you can be happy.

---

### Post by sixthwheel on 2010-03-13
> **Linux is really just a cruel joke, right?** 			 			

No

---

### Post by uRock on 2010-03-13
> **sixthwheel said:**
> No

The title does imply a troll.

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
Please, folks, if all your reply is going to do is toot your own horn and add no value, do all of us normal folks a favor and please refrain from posting anything.

To all the many others who have posted help, I greatly appreciate it.  Many thanks.

Now I'm off to find if this site has a killfile or "ignore user" feature so I'm not distracted by the self-consumed folks around here.

---

### Post by uRock on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> 
Please, folks, if all your reply is going to do is toot your own horn and add no value, do all of us normal folks a favor and please refrain from posting anything.

To all the many others who have posted help, I greatly appreciate it.  Many thanks.

Now I'm off to find if this site has a killfile or "ignore user" feature so I'm not distracted by the self-consumed folks around here.

Maybe posting in the proper section will get you better help. Next time you may want to use a better approach for asking for help. And yes on your UserCP page there is an ignore user applet.

---

### Post by _h_ on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> Now I'm off to find if this site has a killfile or "ignore user" feature so I'm not distracted by the self-consumed folks around here.

Right here: [http://ubuntuforums.org/profile.php?do=ignorelist](http://ubuntuforums.org/profile.php?do=ignorelist)

:)

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
"Ignore List" found and updated.

Ah.....  Feels much better.

---

### Post by uRock on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> "Ignore List" found and updated.

Ah.....  Feels much better.

It does tend to be helpful. Good luck on your endeavour for happiness.;)

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **_h_ said:**
> Right here: [http://ubuntuforums.org/profile.php?do=ignorelist](http://ubuntuforums.org/profile.php?do=ignorelist)

:)

Thanks, but I already found and updated it.

I'm good to go.

---

### Post by _h_ on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> Thanks, but I already found and updated it.

I'm good to go.

Not a problem. Have fun. ^^

---

### Post by pbpersson on 2010-03-13
> **wojox said:**
> #1 I always burn at the lowest speed possible. You get a better more precise burn. 


+1, mostly because I hate to find errors down the road and then have to deal with them later.  I start the burn and go have a cup of coffee or surf the web.  :)

---

### Post by juancarlospaco on 2010-03-13
What does a no0b to try to install and use without configure all the  advanced features and daemons like these?

---

### Post by uRock on 2010-03-13
> **pbpersson said:**
> +1, mostly because I hate to find errors down the road and then have to deal with them later.  I start the burn and go have a cup of coffee or surf the web.  :)
Same here. My external burn only has the option for 40 something power and 52X, but it always gets a good burn. The internal burner is set for 4X.

---

### Post by pbpersson on 2010-03-13
> **AnimalMagic said:**
> 

Try Mint - seems to be Ubuntu without the bugs, though the green theme can be hard to get used to...


There are many here who would argue that belief although I partially believe that which is why I am using Mint on two machines here.  Although I customized the theme on my main machine as one of my first tasks.

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **iRock said:**
> Maybe posting in the proper section will get you better help. 

I think if you'll take the time to review the thread, you'll see that an admin of some type MOVED the thread here.  I didn't select this section.

If you have a problem with the thread being here, talk to that admin.

Now back you go!

---

### Post by pbpersson on 2010-03-13
When I first started using Linux years ago it was Mandrake and I got on the forums and ranted and raved about all the problems.

Now everything just works for me.....I think I gained some knowledge and Ubuntu/Mint has gotten much better.  I jumped on this bandwagon at Feisty Fawn.

However, I just use my machine for standard stuff - file sharing, printing, surfing, photo editing, creating music CDs and movie DVDs, creating web pages, writing software, uploading/downloading files on the web, instant messaging, email. games.....nothing really too advanced.

---

### Post by uRock on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> I think if you'll take the time to review the thread, you'll see that an admin of some type MOVED the thread here.  I didn't select this section.

If you have a problem with the thread being here, talk to that admin.

Now back you go!

You were complaining, not asking for help. That is what this section is for. I have respect for the Admins and Mods here and their decisions. Generally when someone asks for help from volunteers, they are nice and respectful.

---

### Post by uRock on 2010-03-13
...

---

### Post by pbpersson on 2010-03-13
> **eriktheblu said:**
> Cruel joke? No a cruel joke would would be to sell you an operating system for $100-300 US that is excessively vulnerable malware, comes prepackaged with entirely useless software, and has a non-standards-compliant browser that cannot be removed.

Windows also is full of many bugs, some of them years old, and most of the articles on the Microsoft web site give you solutions that take hours to wade through and are the wrong answers.

I know.....to many it sounds just like Linux but that is my point - any advanced OS is going to be difficult once you get into more advanced topics.

---

### Post by pbpersson on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> En Inglés, por favor?

Original sentence:
What does a no0b to try to install and use without configure all the advanced features and daemons like these?

My translation:
Why would a newbie try to install and use without first configuring all the advanced features and daemons which were mentioned?

Although I am still not certain that makes sense....:confused:

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **pbpersson said:**
> When I first started using Linux years ago it was Mandrake and I got on the forums and ranted and raved about all the problems.

Now everything just works for me.....I think I gained some knowledge and Ubuntu/Mint has gotten much better.  I jumped on this bandwagon at Feisty Fawn.

However, I just use my machine for standard stuff - file sharing, printing, surfing, photo editing, creating music CDs and movie DVDs, creating web pages, writing software, uploading/downloading files on the web, instant messaging, email. games.....nothing really too advanced.

Yeah, I know it'll all fall into place.  Thanks.  It's just that sometimes it can wear ya down when you've had a few nights in a row until 3 AM and basically accomplished nothing.

But, come on, telnet?  How hard should that be?

I've forgotten what site it was, but some guy responded to that with basically:

"OMG!  Telnet!  Don't use that, noob!  You'll get 133t haxxored!!!  You should use ssh!!"

I didn't say anything, but I found it funny that he never even considered that I could be on a test network that was physically separate from the internet using machines that had no data I cared about on them.

It never dawned on the guy that I was simply trying to walk before I ran, and that maybe, just maybe, I could always disable or un-install telnet after I was done playing with it.

I guess the warning or a simple caveat would have been nice, but to tell someone that they basically shouldn't ever use good old telnet under any circumstances seems a bit of an over-reaction to me.

Thanks again!

---

### Post by pbpersson on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> 

I guess the warning or a simple caveat would have been nice, but to tell someone that they basically shouldn't ever use good old telnet under any circumstances seems a bit of an over-reaction to me.

Thanks again!

Personally I hate the command line and have instead decided to install a graphical remote utility as needed on all my Windows and Linux machines so I can remotely control any of them from anywhere.

However, this is project number 137 and I have been ill for a few months so....perhaps I can work on this in the year 2011.  ;)

I did have it working on the Hardy Heron machine in the lights out server room so I could remote into that machine from the master bedroom but my machines have since been totally scrambled.....meaning the hardware that was in that case is now in this case running 64-bit Mint and the hardware now in that server case in the lights out server room is running a different OS and all the machines that were in the bedroom are now elsewhere so it has all gotten very confusing....

---

### Post by pbpersson on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> 

Well, I see it's 3AM, so as usual, my Linux shift is over for now.

Peace!

I know that some think that to use Linux you need to be ready to roll up your sleeves, dig into the OS, and spend hours doing work.  There are some on this forum who have said, "If you don't want to learn about the OS, you should not be using it".  

As far as I am concerned, that is like saying, "If you don't know how an internal combustion engine works, you should not be driving a car" which to me makes no sense.

Now that I have been using Ubuntu for some time, when I want to get something accomplished I look at the various applications and check out the instructions.  If there is an application where you just install, it works, and you are done - that is the one I use.  If there is an application where you spend hours typing stuff at the command line.....forget it, not going to happen.

Am I being lazy?  Well......life is short, I have LOTS of other things I need to get done, and I value my health.....I need eight hours of sleep a night so the 3AM stuff is no longer an option for me.  When I was in my twenties and had more time, sure.....but not now.

Different strokes for different folks.....

Anyway, that is my story and I am sticking to it.  :)

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **pbpersson said:**
> I know that some think that to use Linux you need to be ready to roll up your sleeves, dig into the OS, and spend hours doing work.  There are some on this forum who have said, "If you don't want to learn about the OS, you should not be using it".  

As far as I am concerned, that is like saying, "If you don't know how an internal combustion engine works, you should not be driving a car" which to me makes no sense.

Am I being lazy?  Well......life is short, I have LOTS of other things I need to get done, and I value my health.....I need eight hours of sleep a night so the 3AM stuff is no longer an option for me.  When I was in my twenties and had more time, sure.....but not now.

Different strokes for different folks.....

Anyway, that is my story and I am sticking to it.  :)

1st graf:  That way of thinking makes no sense to me either.  Although, I find it nice if I know some theory about how the ICE works, and if I can do some work on it myself, so much the better.  Again, just an analogy.  I've long since stopped working on cars! :)

2nd graf:  Great points.  Time is short, and it's really our most valuable possession.  I think I just need to know the foundational stuff before I'm ready to trust the GUI, though.  Plus, I've actually found what I suspect may be problems when trying to use the GUI (in other distros, btw).  Of course, I can't say for sure since I'm so new to this stuff, but I can tell you that what I believed to be the command line equivalents went off without a hitch.  

It would seem to make sense since testing all of this stuff is surely almost all automated via scripts.  Although, I freely confess to not being up on current graphical testing methods, so I could very well be wrong.  And I'll be the first to admit as well that I could easily have missed a prior step or two when using the GUI.  Once you have a handle on how things work, bugs aren't too terribly difficult to identify.  If you're brand new, however, I've found it's a totally different story.

Thanks again for all your help and your posts in general.  As I said, this stuff will fall into line, I'm sure.  It's really just a matter of how many bumps in the road I hit on the way.

PS - Love the sig, btw!  :)

---

### Post by yoasif on 2010-03-13
> **WhyIsLinuxSoCruel said:**
> But, come on, telnet?  How hard should that be?

I've forgotten what site it was, but some guy responded to that with basically:

"OMG!  Telnet!  Don't use that, noob!  You'll get 133t haxxored!!!  You should use ssh!!"

I didn't say anything, but I found it funny that he never even considered that I could be on a test network that was physically separate from the internet using machines that had no data I cared about on them.

It never dawned on the guy that I was simply trying to walk before I ran, and that maybe, just maybe, I could always disable or un-install telnet after I was done playing with it.

I guess the warning or a simple caveat would have been nice, but to tell someone that they basically shouldn't ever use good old telnet under any circumstances seems a bit of an over-reaction to me.

Thanks again!
> 
Experts in computer security, such as SANS Institute, recommend that the use of Telnet for remote logins should be discontinued under all normal circumstances, for the following reasons:

    * Telnet, by default, does not encrypt any data sent over the connection (including passwords), and so it is often practical to eavesdrop on the communications and use the password later for malicious purposes; anybody who has access to a router, switch, hub or gateway located on the network between the two hosts where Telnet is being used can intercept the packets passing by and obtain login and password information (and whatever else is typed) with any of several common utilities like tcpdump and Wireshark.
    * Most implementations of Telnet have no authentication that would ensure communication is carried out between the two desired hosts and not intercepted in the middle.
    * Commonly used Telnet daemons have several vulnerabilities discovered over the years.


the guy was trying to help you (maybe he was a bit rude) -- but really, there is no reason to use telnet when ssh is just as easy to use and doesn't have the same issues.

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **yoasif said:**
> the guy was trying to help you (maybe he was a bit rude) -- but really, there is no reason to use telnet when ssh is just as easy to use and doesn't have the same issues.

And you're helping me as well.  And for that I am very grateful.  Thank you.

---

### Post by WhyIsLinuxSoCruel on 2010-03-13
> **pbpersson said:**
> +1, mostly because I hate to find errors down the road and then have to deal with them later.  I start the burn and go have a cup of coffee or surf the web.  :)

You mean you don't verify the downloaded file and the burned media with md5sum?  The horror!! :)

md5sum was something that really impressed me after I learned to use it.  I'm not aware of any MS analog which is actually quite shocking (if true) once you get used to md5sum'ing all the stuff you download.

Now I need to figure out what all this sha1 business is about.  

So much to learn.  So little time.

Cheers!

---

### Post by RT236 on 2010-03-13
Actually, Linux has worked well for me over the years. I'm from a Solaris Unix background.  To me, Linux just keeps getting better and better. The last windows dist. I ever had was Win98SE.  There is really not too much I've found I can not do in Linux

That said, I will certainly admit I'm had times of bashing my head against the wall, but I'm always recovered and so have my computer systems!  From my perspective, Ubuntu is a pretty decent distro.

---

### Post by dagoth_pie on 2010-03-13
> As far as I am concerned, that is like saying, "If you don't know how an internal combustion engine works, you should not be driving a car" which to me makes no sense.

If you don't want to know what a manual gearbox does then you should be driving and auto...

If you don't want to learn what the words "applications", "places" and "system" mean then you should be running windows...

---

### Post by MarcusW on 2010-03-14
I have to say, those were really small problems. (maybe except the telnet thing, but why would you wanna use telnet when there is ssh?)

If you get things like "connection refused", install firestarter or gufw and make sure the ports are open. :)

---

### Post by cariboo on 2010-03-14
Wouldn't be easier to go to System->Administration->Network Tools->Port Scan, and scan the computer the telnet servers is supposed to be running on to check if port 23 is open?

---

### Post by MarcusW on 2010-03-14
> **cariboo907 said:**
> Wouldn't be easier to go to System->Administration->Network Tools->Port Scan, and scan the computer the telnet servers is supposed to be running on to check if port 21 is open?

Isn't 23 for telnet?

---

### Post by Sef on 2010-03-14
> Isn't 23 for telnet?

Yes, port 23 is for telnet.

---

### Post by dreamsburnred on 2010-03-15
> **eriktheblu said:**
> ...has a non-standards-compliant browser that cannot be removed.

Windows 7 allows the removal of IE8. W7 in EU even asks to remove it :D.

---

### Post by WhyIsLinuxSoCruel on 2010-03-15
> **MarcusW said:**
> I have to say, those were really small problems. (maybe except the telnet thing


OK, so let's take just the burning CD/DVDs under Linux problem and forget all about the others.  Care to explain to a lowly newb what needs to be done to be able to burn CD/DVD ISO images without errors at speeds that are as fast as what the identical HW does under XP?

Remember, this is a fresh install of Ubuntu 9.10.  Not a single change to it has been made.  I'll even be happy to re-install Ubuntu first so I'm certain that it's an OOTB install, if you'd like.

I'm all ears as to what the solution to this one small problem is.

TIA,

---

### Post by uRock on 2010-03-15
> **WhyIsLinuxSoCruel said:**
> OK, so let's take just the burning CD/DVDs under Linux problem and forget all about the others.  Care to explain to a lowly newb what needs to be done to be able to burn CD/DVD ISO images without errors at speeds that are as fast as what the identical HW does under XP?

Remember, this is a fresh install of Ubuntu 9.10.  Not a single change to it has been made.  I'll even be happy to re-install Ubuntu first so I'm certain that it's an OOTB install, if you'd like.

I'm all ears as to what the solution to this one small problem is.

TIA,

Install compatible hardware. Try asking in the correct sub-forum.

---

### Post by WhyIsLinuxSoCruel on 2010-03-15
> **MarcusW said:**
> I have to say, those were really small problems. (

Well, I guess everybody is busy because, for a small problem, I sure haven't heard much.

And all those friendly staff members were here in this very thread just a day or two ago.  If that many took the time to post in the thread, I wonder what multiple of that number viewed the thread without commenting.

I'll try a couple of things ***I*** thought of.  

When, oops, I mean, if, I find a solution, I'll be sure to post back here in this thread for the benefit of the next unfortunate soul who inevitably has this same small problem.  

That way that person can simply find the solution and not waste a lot of their time.  

I try to help people like that.  What can I say?  It's in my nature to be considerate of others in a ***truly*** helpful way.  I find it saves everyone time vs. others who like to shout from the mountaintops how smart they believe they are without adding any real value to solving the problem at hand.

Cheers!

---

### Post by ankspo71 on 2010-03-16
> I switch back to Linux to see if I'm making errors cause 3AM has rolled  around again and I've got nothing accomplished other than installing XP,  and Ubuntu 9.10 has errors if I try to burn either DVD media faster  than 4X or CD-Rs faster than 8X.  I give up.

This is a regular problem around here actually. People here are regularly told to burn at the lowest speeds possible and if that doesn't help, then they say to try other burning software as advice. This might even be common with all distros. 

I think it's a given that lower speed equals higher quality, but high speed burns isn't supposed to equal ruined cds either. I never had 'that' problem in windows. 

If I'm in a hurry, I'll burn an iso on my wifes xp computer. If I install medibutu's extra dvd package, I have to burn with my wife's computer, because my lose my burning ability completely with 3 different burners... which, of course, is a whole different matter. 

I hope you can get those problems sorted. K3B seems to be a favorite alternate burner for most.

---

### Post by pbpersson on 2010-03-16
> **ankspo71 said:**
> 

I hope you can get those problems sorted. K3B seems to be a favorite alternate burner for most.

That is all I have ever used.  I love K3B.  I thought it was a strange name until I learned what it stood for, then I thought it was a funny name.  :D

---

### Post by uRock on 2010-03-16
> **WhyIsLinuxSoCruel said:**
> Well, I guess everybody is busy because, for a small problem, I sure haven't heard much.

Start a thread in the proper section if you want help.

---

### Post by mastablasta on 2010-03-16
> **WhyIsLinuxSoCruel said:**
>  
md5sum was something that really impressed me after I learned to use it. I'm not aware of any MS analog which is actually quite shocking (if true) once you get used to md5sum'ing all the stuff you download. 
Cheers!
 
Not true. you can do md5sum.

---

### Post by caravel on 2010-03-16
> **mastablasta said:**
> Not true. you can do md5sum.
I can only speak for WinXP, but in that OS you cannot, you would have to download a command line tool separately (you're right though in that, technically that makes it 'possible').

---

### Post by sixthwheel on 2010-03-16
Haven't heard from "WhyIsLinuxSoCruel" in 11 hours.
Perhaps he's  trying to configure his Norton 360. :lolflag::P

---

### Post by RT236 on 2010-03-16
> **WhyIsLinuxSoCruel said:**
> OK, so let's take just the burning CD/DVDs under Linux problem and forget all about the others.  Care to explain to a lowly newb what needs to be done to be able to burn CD/DVD ISO images without errors at speeds that are as fast as what the identical HW does under XP?

Remember, this is a fresh install of Ubuntu 9.10.  Not a single change to it has been made.  I'll even be happy to re-install Ubuntu first so I'm certain that it's an OOTB install, if you'd like.

I'm all ears as to what the solution to this one small problem is.

TIA,

Just FYI- I've used K3B from the Synaptic Package Manager for a number of years with no difficulties.  Also, check out [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by aysiu on 2010-03-16
> **caravel said:**
> I can only speak for WinXP, but in that OS you cannot, you would have to download a command line tool separately (you're right though in that, technically that makes it 'possible'). It doesn't have to be a command-line tool:
[http://www.md5summer.org/](http://www.md5summer.org/)

---

### Post by J_Stanton on 2010-03-16
> **aysiu said:**
> It doesn't have to be a command-line tool:
[http://www.md5summer.org/](http://www.md5summer.org/)

or winmd5sum [http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum)

---

### Post by WhyIsLinuxSoCruel on 2010-03-16
> **mastablasta said:**
> Not true. you can do md5sum.

From a third party app, sure.  I said, "***MS*** analog" (as in, "authored by Microsoft").

Thanks, though, that would have helped if I hadn't already done a web search on, "md5sum windows" and seen the oceans of home brew apps available.

---

### Post by WhyIsLinuxSoCruel on 2010-03-16
> **ankspo71 said:**
> This is a regular problem around here actually. People here are regularly told to burn at the lowest speeds possible and if that doesn't help, then they say to try other burning software as advice. This might even be common with all distros. 

I think it's a given that lower speed equals higher quality, but high speed burns isn't supposed to equal ruined cds either. I never had 'that' problem in windows. 

If I'm in a hurry, I'll burn an iso on my wifes xp computer. If I install medibutu's extra dvd package, I have to burn with my wife's computer, because my lose my burning ability completely with 3 different burners... which, of course, is a whole different matter. 

I hope you can get those problems sorted. K3B seems to be a favorite alternate burner for most.

Whoa, wow!  What is this?  A friendly, polite poster who has no ax to grind, nothing to prove, and no voracious ego to nourish?  Oh, wow is that refreshing.  And you seem honest and helpful as well!!  I don't think I've seen another poster like you other than [pbpersson]("http://ubuntuforums.org/member.php?u=515872") in the "Testimonials & Experiences" section since this thread was plopped here by an admin.

Interestingly, I had seen quite a few posters like that in the "Absolute Beginner" section prior to the admin yanking the thread over there, but it's been rough going since then (with the one exception of the user I mentioned).

Can either of you guys recommend another place (on this site or not) where more people like you hang out?  I've registered on loads of Linux help sites, and they're all pretty good, but if either of you can think of something in particular, I'd love to hear it.

I still haven't looked at this burning issue yet.  My computer spent last night and today downloading a bunch of utilities, ISOs and some other things I found, so I haven't had a chance to play with any of them yet.  I'm hoping to have some results to report later tonight or tomorrow.

Many thanks for letting me know how you personally do thinks in your world.  The more I hear from people, the more I suspect that many people using linux simply put up with slower burning.  That may end up being the case with me as well, but I still want to see if I can get the higher speed burning working under linux because it would save a lot of time in the future.

All of the distros I'v tried behave similarly with all six different sets of HW that I have, but the thing I noticed is that they all rely on wodim to do the burning when the rubber meets the road.  I'm not sure if it's true or not, but I've read in many places that wodim is highly suspect, so I'm not going to try any method that relies on that any more.

Thanks again to you and the other helpful poster here, and the other folks in the "Absolute Beginner" section on the odd chance that they're reading here.

Whatever I find, I'll make sure to post back here for the benefit of others who may find this thread in the future.

Thanks again!

Regards,

---

### Post by WhyIsLinuxSoCruel on 2010-03-16
> **RT236 said:**
> Just FYI- I've used K3B from the Synaptic Package Manager for a number of years with no difficulties.  Also, check out [http://www.medibuntu.org/](http://www.medibuntu.org/)

Almost missed your post for some reason.  Glad I didn't.  

Thanks for this!  I do, indeed, plan on trying out K3B and seeing how it works.  I've never heard of medibuntu (another poster does mention it down thread, though), but I'll make a note to grab that and see what I can find with that as well at some point in the near future.

Thanks again!

Regards,

---

### Post by WhyIsLinuxSoCruel on 2010-03-16
> **pbpersson said:**
> That is all I have ever used.  I love K3B.  I thought it was a strange name until I learned what it stood for, then I thought it was a funny name.  :D

K3B is on my list!!  And I have yet to learn the secret of its name, so I look forward to that as well, now that you mention it.

Thanks again for the help and info!

Regards,

---

### Post by v1ad on 2010-03-16
go download unetbootin and put the iso image on a usb stick and install from there.a lot easier

---

### Post by uRock on 2010-03-16
> **WhyIsLinuxSoCruel said:**
> Can either of you guys recommend another place (on this site or not) where more people like you hang out?  I've registered on loads of Linux help sites, and they're all pretty good, but if either of you can think of something in particular, I'd love to hear it.

You will find quite a few nice people who want to help by posting a non-flaming request for help in the [Sub-Forums : Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327") and the [Threads in Forum : Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326"), but the key is to ask nicely for help, instead of smacking people in the face with insults.

---

### Post by WhyIsLinuxSoCruel on 2010-03-16
> **v1ad said:**
> go download unetbootin and put the iso image on a usb stick and install from there.a lot easier


I will check it out.

Many thanks, kind sir!

---

### Post by Brightneon_Latte on 2010-03-17
You want a cruel Joke? Try suicide Linux...now that's a cruel joke (really)
I'm sorry you are suffering with ubuntu, but with some patience you can go on. I am half windows half linux, but now I'm using more linux than windows, and that's good. With a little patience, trial and error, and some crashes, you will finally achieve an stable OS. Like they say, the narrow path will always be the best one. It may be though, bit it pays itself with time

---

### Post by WhyIsLinuxSoCruel on 2010-03-18
> **Brightneon_Latte said:**
> You want a cruel Joke? Try suicide Linux...now that's a cruel joke (really)
I'm sorry you are suffering with ubuntu, but with some patience you can go on. I am half windows half linux, but now I'm using more linux than windows, and that's good. With a little patience, trial and error, and some crashes, you will finally achieve an stable OS. Like they say, the narrow path will always be the best one. It may be though, bit it pays itself with time

Wow!  The concept of suicide linux is brutal!  Talk about operating without a safety net!

Thanks a lot for the words of encouragement.  I really appreciate it.  I'm still hoping to completely avoid ever using Win7.  That's merely a little personal goal I've set for myself, but I find the idea appealing.

Regards,

---

### Post by johnpap on 2010-03-18
Well, like everybody else is suggesting, it will take a bit to get used to Linux.
I am a designer and the whole adobe cs4 suite doesn't not work with linux full stop, so I have to switch over, but if I had the option I would stick only to linux.... so take a step back, breathe in and start getting used to it man... it's worth it!

---

### Post by prodigy_ on 2010-03-18
I agree with pretty much everything the OP said, except the telnet part. Seriously, who needs telnet when there's SHH? SSH is great. You get SFTP and SSHFS as a free bonus. And you can even bind services, that don't support encryption to loopback/localhost and then forward their ports over SSH connection. Isn't that cool?

But software policy is certainly inconsistent. There are packages in repositories, that look and feel so unfinished, that it hurts. Worse yet, sometimes this alpha-grade crap is even installed by default. Yet to get the latest versions of good, stable apps (like Wine or Transmission) you need to enable a ton of PPAs. Why?

And double-naming (like 9.10/Karmic Koala) is purely an artifact of BSD "geekiness" that has no place in a desktop distro. First, it confuses newbies and serves no real purpose. Second, whenever you have an obscure and rare problem, you'll have to do all your googling twice. Naming policy should be simple, actually, like: "Ubuntu 2009" instead of 9.04 and "Ubuntu 2009 SP1" instead of 9.10. It's easy to understand and easy to remember. Proper positioning would also be easier, like: non-SP releases are bleeding edge with more bugs but also with more functionality, SP releases are stable and conservative. LTS releases should be discontinued. Instead, every couple of years an "Enterprise" version should be released, based on the previous year's SP1 version but extra robust and focused on eliminating bugs and security flaws.

---

### Post by chili555 on 2010-03-18
K3b works perfectly for me. It seems fast enough and I have never throttled it down for any reason. It checks the MD5 sum automagically. I have extracted files and burnt firmware discs for Blu-ray players and all kinds of stuff that the faint-of-heart warned me that would only work in Windows and in a certain $400 version and with a certain SP, whatever that is.

I chuckle when I see Windows fans trying to struggle to burn an .iso. In K3b, I drop in a blank CD, select Burn Image, browse to the file I want and click Burn. After I refresh my beverage, it's done and perfect.

I wouldn't dare ask to use my wife's Windows computer to burn an .iso; she refuses to have Windows in the house.

Linux has a learning curve, as does Windows.

---

### Post by WhyIsLinuxSoCruel on 2010-03-21
> **prodigy_ said:**
> I agree with pretty much everything the OP said, except the telnet part. Seriously, who needs telnet when there's SHH? SSH is great. You get SFTP and SSHFS as a free bonus. And you can even bind services, that don't support encryption to loopback/localhost and then forward their ports over SSH connection. Isn't that cool?

But software policy is certainly inconsistent. There are packages in repositories, that look and feel so unfinished, that it hurts. Worse yet, sometimes this alpha-grade crap is even installed by default. Yet to get the latest versions of good, stable apps (like Wine or Transmission) you need to enable a ton of PPAs. Why?

And double-naming (like 9.10/Karmic Koala) is purely an artifact of BSD "geekiness" that has no place in a desktop distro. First, it confuses newbies and serves no real purpose. Second, whenever you have an obscure and rare problem, you'll have to do all your googling twice. Naming policy should be simple, actually, like: "Ubuntu 2009" instead of 9.04 and "Ubuntu 2009 SP1" instead of 9.10. It's easy to understand and easy to remember. Proper positioning would also be easier, like: non-SP releases are bleeding edge with more bugs but also with more functionality, SP releases are stable and conservative. LTS releases should be discontinued. Instead, every couple of years an "Enterprise" version should be released, based on the previous year's SP1 version but extra robust and focused on eliminating bugs and security flaws.


Preach on, Brother!

---

### Post by Methuselah on 2010-03-21
What a lot of complaining about the most inconsequential things.

Double naming?

It's Ubuntu 9.10 for Octover 2009 and way more logical than most other schemes. Please spare Ubuntu the SP1/SP2/SP&#8734; nonsense.
Karmic Koala, etc are just development codenames because it has to release before the numerical name becomes immutable.
Codenames are used by Microsoft too. Never heard about Windows Longhorn, Blackcomb, Mojave etc

Anyway, the nice thing about Ubuntu is that it costs nothing to try it and hate it and move on. :)
If it's a cruel joke then, fool me once shame on me, fool me twice, you know what they say...
Use what works for you!

---

### Post by prodigy_ on 2010-03-22
> **Methuselah said:**
> Please spare Ubuntu the SP1/SP2/SP&#8734; nonsense.
Just because **you** don't like it?

> **Methuselah said:**
> Karmic Koala, etc are just development codenames
Why aren't they [officially](http://cdimage.ubuntu.com/releases/9.10/release/) dropped for final versions then?

---

### Post by uRock on 2010-03-22
> **Methuselah said:**
> What a lot of complaining about the most inconsequential things.

Double naming?

It's Ubuntu 9.10 for Octover 2009 and way more logical than most other schemes. Please spare Ubuntu the SP1/SP2/SP&#8734; nonsense.
Karmic Koala, etc are just development codenames because it has to release before the numerical name becomes immutable.
Codenames are used by Microsoft too. Never heard about Windows Longhorn, Blackcomb, Mojave etc

Anyway, the nice thing about Ubuntu is that it costs nothing to try it and hate it and move on. :)
If it's a cruel joke then, fool me once shame on me, fool me twice, you know what they say...
Use what works for you!

I agree, I like having the nick names being that half the people can't get the numbers right. Service packs bite. That is all 7 was to Vista, but they got greedy. They actually had the commercials here in Vegas for the Mojave edition.

---

### Post by chili555 on 2010-03-22
Let's see. First Windows had fairly coherent numbers, 1.01, 3.1, 3.51, etc. Then came numbers somewhat reflective of the year they hoped to release, 95, 98, 2000, etc. How exactly did Me fit in to that? Or NT? Now comes XP, meaning what? Then Vista; relating to what? Now comes Windows 7. What does that refer to??

May I assume that, if one of your nits to pick on Ubuntu is naming and version numbers, that you have a full-blown bloody scab with Microsoft?

I'm happier with Ubuntu than I would be with Windows for a variety of reasons. Neither are perfect. If you think Windows is perfect, I can refer you to any number of Windows whiner sites where many users will disagree with you.

If you are not happier with Ubuntu than Windows, I suggest you do one of two things; either contribute to the improvement of Ubuntu by reporting bugs and writing patches, or simply go back to Windows. Maybe complaining about Ubuntu's shortcomings and doing nothing to repair them helps you vent your emotions, but it does little else.

---

### Post by eveningsky339 on 2010-03-22
> **Linux is really just a cruel joke, right?** 			 			

Just think of all the money you wasted!  ;)

---

### Post by J_Stanton on 2010-03-22
> **chili555 said:**
> 

If you are not happier with Ubuntu than Windows, I suggest you do one of two things; either contribute to the improvement of Ubuntu by reporting bugs and writing patches, or simply go back to Windows. Maybe complaining about Ubuntu's shortcomings and doing nothing to repair them helps you vent your emotions, but it does little else.

this.

---

### Post by aviedw on 2010-03-22
Part of finding your way is first being lost. Linux has an identity thats simply different from Windows and Mac os X ( even thought this is unix based as well). It has kinks to be worked out but not at the sake of becoming a Windows copy cat. When newbies come to Linux they should go through the trial of learning. If they dont want to do the foot work then they should go back to windows or mac where everything is on the desktop for them to click. Everybody here who has an affinity for Linux or Ubuntu (to be more specific) were once newbies struggling at first with something as simple as installing a package or adding repositories. Linux comes with a level of freedom that many computer users aren't use to having or frankly want to have or simply are not likely to appreciate. But a true_user will see Linux as an imperfect system, different approach to a similar end. I think newbies should embrace it and not complain about how its different. And if you think its broken or doesn't work as well as it should, commit yourself to improving it. By the very definition of open source, that becomes your basic right.

---

### Post by WhyIsLinuxSoCruel on 2010-03-26
> **chili555 said:**
> Let's see. First Windows had fairly coherent numbers, 1.01, 3.1, 3.51, etc. Then came numbers somewhat reflective of the year they hoped to release, 95, 98, 2000, etc. How exactly did Me fit in to that? Or NT? Now comes XP, meaning what? Then Vista; relating to what? Now comes Windows 7. What does that refer to??

May I assume that, if one of your nits to pick on Ubuntu is naming and version numbers, that you have a full-blown bloody scab with Microsoft?



Please read Prodigy_'s quote one more time:

***   B E G I N  ***
And double-naming (like 9.10/Karmic Koala) is purely an artifact of BSD "geekiness" that has no place in a desktop distro. First, it confuses newbies and serves no real purpose. Second, whenever you have an obscure and rare problem, you'll have to do all your googling twice. 
***    E N D   ***

I didn't tout Microsoft.  I simply questioned a convention I saw being used in Ubuntu that I thought was needlessly adding confusion.

I understand code names and build numbers for their benefits in the alpha and beta cycles.  However, as Prodigy_ said, I don't think they have any place in the released version of the SW.

Why is it that so many of you guys reply to questions from newbies who don't even mention Microsoft with a rant on why the newbies shouldn't assume that Microsoft is the be-all, end-all of consumer SW?  Seems to me like people who do that to newbies are the ones with the bigger issues.  Use you Linux and enjoy it.  Revel in its superiority if you like.  Why launch on others who ask innocent questions, though?  I'll never know.

---

### Post by mastablasta on 2010-03-26
Well to be fair this is also done by Apple. Name can be there for marketing reasons. And to differentiate the product in more than just a number.
 
Newbie can also get online help as well as via call center (only you need to pay for it a little). So no need to do extensive searches if you don't want to. Just ask developers directly.

---

### Post by Gixxy on 2010-03-27
> **HermanAB said:**
> Hmm, well, Ubuntu is 'Linux for Masochists'.  If you want 'Linux for Dummies' then you should install Mint, Mandriva or Puppy.


No SIR! Gentoo is linux for masochists... end of story.

I have compiled my brains to mush....  ;)

---

### Post by pbpersson on 2010-03-27
> **WhyIsLinuxSoCruel said:**
> 

I understand code names and build numbers for their benefits in the alpha and beta cycles.  However, as Prodigy_ said, I don't think they have any place in the released version of the SW.


Does it add confusion?

As far as I am concerned, it is very easy to get 7.10, 8.10, and 9.10 mixed up - they all look pretty much the same to me.

However, confusing a Bashful Badger, Giggly Gopher, and Leaping Lizard would be far more difficult.

I always refer to the releases by their names.  When I first installed Ubuntu it was Feisty Fawn.  I have no idea what version that is (which tells me when it was released) but I could go and look it up if I needed to.

If we were going to drop anything it should be the version numbers, IMO.

---

### Post by stednick on 2010-03-27
Screenshots of Lucid Lynx have recently been released and for better or worse they look similar to the screenshots of Mac os 10.6

[[COLOR="Navy"]Lucid Lynx[/COLOR]]("http://www.debianadmin.com/ubuntu-10-04-lucid-beta-1-screenshots-gallery.html")

---

### Post by uRock on 2010-03-27
> **stednick said:**
> Screenshots of Lucid Lynx have recently been released and for better or worse they look similar to the screenshots of Mac os 10.6

[[COLOR="Navy"]Lucid Lynx[/COLOR]]("http://www.debianadmin.com/ubuntu-10-04-lucid-beta-1-screenshots-gallery.html")

What gives you that impression?

---

### Post by Methuselah on 2010-03-29
Thw code names are seldom used officialy after the version is released.
There is very little in the actual installation that reports itself as Karmic Koala etc.
However, I think many people find the alliterative development codenames easier to remember than dry numbers so the user community continues to use them after release.
Generally, if the codename is later in the alphabet it is a later release.
IMO, if someone finds something as minute as the naming scheme to be an insurmountable difficulty it says more about that person's mindset that it does about Ubuntu.

BTW, this whole thread reeks of flamebait; people haven't been taking it but it does reek.
Who joins a linux forum with a username like that except a troll?
OP apparently had no desire to ask for help in support sections as no sane person would choose such a nickname for that purpose.

---

### Post by uRock on 2010-03-29
I prefer the code name over the number for the fact that so many people mess up the release number, ie. 9.1 or 10.4.

---

### Post by WhyIsLinuxSoCruel on 2010-03-29
> **pbpersson said:**
> Does it add confusion?

As far as I am concerned, it is very easy to get 7.10, 8.10, and 9.10 mixed up - they all look pretty much the same to me.

However, confusing a Bashful Badger, Giggly Gopher, and Leaping Lizard would be far more difficult.

I always refer to the releases by their names.  When I first installed Ubuntu it was Feisty Fawn.  I have no idea what version that is (which tells me when it was released) but I could go and look it up if I needed to.

If we were going to drop anything it should be the version numbers, IMO.

All in what one's used to and how each person's brain prefers to handle things.  It's not the cutesy names that I have a problem with.  It's that half the support posts and discussions on the web use the version numbers, and the other half use the cutesy names.  I really don't care what Ubuntu decides upon, but I really think they should pick ONE convention.  The way things are, it's just adding another layer of abstraction for no benefit whatsoever.

---

### Post by WhyIsLinuxSoCruel on 2010-03-29
> **Methuselah said:**
> Thw code names are seldom used officialy after the version is released.
There is very little in the actual installation that reports itself as Karmic Koala etc.
However, I think many people find the alliterative development codenames easier to remember than dry numbers so the user community continues to use them after release.
Generally, if the codename is later in the alphabet it is a later release.
IMO, if someone finds something as minute as the naming scheme to be an insurmountable difficulty it says more about that person's mindset that it does about Ubuntu.

BTW, this whole thread reeks of flamebait; people haven't been taking it but it does reek.
Who joins a linux forum with a username like that except a troll?
OP apparently had no desire to ask for help in support sections as no sane person would choose such a nickname for that purpose.

The names are seldom used???  Pick a release version (the number) of Ubuntu.  Pick ANY one.  Then do a web search on "Ubuntu" that version number and any error you wish.  See how many hundreds of thousands of hits (if not more) are returned.  If you regard that as "seldom used" then you're using an obscure definition of that first word.

I will agree, though, that, within the distro itself, the names are pleasantly absent.  In the support communities on the entire web, however, it's entirely different.

Is it insurmountable?  Of course not.  Annoying as a crying baby on a 14 hour flight?  Yes.  And it provides as much benefit to new Ubuntu users as that crying baby does to the rest of the passengers on the plane.

Regardless, I don't stop by here because I feel the need to argue.  I'm a new user to Ubuntu and Linux who had some questions.  I posted my experiences and the resulting questions in a beginner forum here.  No arguing happened in this thread until the thread was moved, erroneously IMHO, to this particular forum.  

It's clear the majority of you are not interested in helping newbies.  You seem to be much more preoccupied with telling others why they are wrong (or what user name one should choose) rather than calmly discussing things in a mature manner.  I hope for Ubuntu's sake, none of you ever ends up in PR.

And now I'm back to learning more about linux...  You might remember what that is.  It's more involved than just criticizing.

---

### Post by MarcusW on 2010-03-30
> **WhyIsLinuxSoCruel said:**
> The names are seldom used???  Pick a release version (the number) of Ubuntu.  Pick ANY one.  Then do a web search on "Ubuntu" that version number and any error you wish.  See how many hundreds of thousands of hits (if not more) are returned.  If you regard that as "seldom used" then you're using an obscure definition of that first word.

I will agree, though, that, within the distro itself, the names are pleasantly absent.  In the support communities on the entire web, however, it's entirely different.

Is it insurmountable?  Of course not.  Annoying as a crying baby on a 14 hour flight?  Yes.  And it provides as much benefit to new Ubuntu users as that crying baby does to the rest of the passengers on the plane.

Regardless, I don't stop by here because I feel the need to argue.  I'm a new user to Ubuntu and Linux who had some questions.  I posted my experiences and the resulting questions in a beginner forum here.  No arguing happened in this thread until the thread was moved, erroneously IMHO, to this particular forum.  

It's clear the majority of you are not interested in helping newbies.  You seem to be much more preoccupied with telling others why they are wrong (or what user name one should choose) rather than calmly discussing things in a mature manner.  I hope for Ubuntu's sake, none of you ever ends up in PR.

And now I'm back to learning more about linux...  You might remember what that is.  It's more involved than just criticizing.

You can't really blame people for being jerks in a thread with an OP like this. People who help newbies on their free time don't really respond well to poeple being jerks while asking for help. I mean no offense with this, I'm just saying next time you want help: Ask for help, don't complain. The people who help you are ubuntu USERS just like you, they don't owe you anything.

---

### Post by caravel on 2010-03-30
> **WhyIsLinuxSoCruel said:**
> The names are seldom used???  Pick a release version (the number) of Ubuntu.  Pick ANY one.  Then do a web search on "Ubuntu" that version number and any error you wish.  See how many hundreds of thousands of hits (if not more) are returned.
That actually proves the names work and are much more unique and searchable than the numbers or dates you propose.  Most of the releases are referred to by the first name, i.e. Karmic, Jaunty, Intrepid etc.  So if you do a search for "Ubuntu Karmic" you should get good results specific to that version.  If on the other hand you search for "Ubuntu 9.10", you could easily get results about Ubuntu and some other software that has been at version 9.10.

Debian is similar in that Stable is also known as Debian 5.0 or simply "Lenny".  When searching it's better to search for "Debian Lenny" for the same reasons as those above.

Windows is actually the same in that it has a name (i.e. Vista, XP, 2000, ME, 98SE etc) and a number (NT6.0, NT5.1, NT5.0, 4.90, 4.10 etc,) and a development codename.

Considering Ubuntu is still in the development stage and is an unstable distro, it's understandable that the codenames are used.  It's a minor point and you should probably focus elsewhere.

---

