---
title: "The Ubuntu community is guilty of ignoring real problems."
date: 2007-12-22
forum: The Cafe
---

### Post by Palmyra on 2007-12-22
In some places, constructive criticism is appreciated.  In many places, constructive criticism is worth a lot more than praise.  I don't know that is the case here, in this community, and even the greater Linux community.

I'll deal with only one example here.  Many Linux users are quick to play down anything that suggests dependency hell still exists (and having to compile software yourself), and love to point to the supposed wonders of apt-get.  They swear that there are a few, if any, applications that still result in dependency hell.

Well, I'll give you a few examples.

1.  wxDownload Fast has been giving me lots of segmentation fault errors, so it appears only compiling it is an option.  Oh well...guess what?  I appear to be missing something wxDownload Fast requires.  Okay...looking for this little thing, run around, find it, install it, another problem springs up, and so on.  Yes, I have looked for a Deb file.  Yes, I have been on Synaptic.  Notice that I have to say yes to these things, because you're often shot down with something you apparently missed yourself.  The user is to blame, not the problem.  

2.  OpenOffice Writer was having some weird font issues.  Some say that you need to compile it yourself.  Too much trouble there.  Yes, people have looked into this problem.

Admittedly, it seems these problems are becoming less common, but to deny the truth is just ludicrous.   No, I am not looking for solutions in this thread.  I am just saying the following: stop whining about Windows, and let's get our hands dirty with fixing bugs.  As I have said in another thread I created, which was hardly noticed, Windows doesn't make segmentation faults go away, it doesn't make Firefox lighter, it doesn't make Nautilus integrate better with other applications, etc.  It seems to me more time is spent talking about how bad Microsoft and Windows are than talking about real problems, *now*.

PS:  Please don't offer solutions to the above mentioned problems.  Please focus on the point of this thread.

---

### Post by Linuxratty on 2007-12-22
You hit the nail on the head...I agree!:)
:KS:KS:KS=D>

---

### Post by ~LoKe on 2007-12-22
The developers are the ones ironing out problems like this.  Most of what you'd see in these support forums are attempts at solutions.  

Obviously people like me can't hand you a fix when one hasn't been created.

And yes, of course there are still problems; that's why this forum exists.  There will always be problems and there will always be people trying to find a solution. 

If you feel there's a serious problem which needs to be tended to, use launchpad to search for an existing bug, and if none exists, make one.

---

### Post by p_quarles on 2007-12-22
I think the whole point of a support forum is to provide solutions to problems like these, not to talk about how annoying they are. Yes, there's a vocal minority, I think, that likes to ignore or deny any possible problems with GNU/Linux. And then there's another vocal minority -- perhaps including yourself -- that complains that this denialist vocal minority is evidence that Linux users can't take criticism. 

Look: I'm not a programmer. I can't fix wxDownload for you, and I'm guessing that this is also true of the vast majority of people responding to threads about problems with individual applications. This does not mean that I am "blaming" you for the problem, it just means that if you ask a question, I will give you the answer I know how to give. Don't take it personally, and don't take it to mean that I think everything about Linux is platinum-plated yumminess.

Btw, the specific error with wxD that you encountered is different from the one currently open on Launchpad. You should be sure to add your data:
[https://bugs.launchpad.net/ubuntu/+bug/157460](https://bugs.launchpad.net/ubuntu/+bug/157460)

---

### Post by LaRoza on 2007-12-22
> **Palmyra said:**
> In some places, constructive criticism is appreciated.  In many places, constructive criticism is worth a lot more than praise.  I don't know that is the case here, in this community, and even the greater Linux community.

I'll deal with only one example here.  Many Linux users are quick to play down anything that suggests dependency hell still exists (and having to compile software yourself), and love to point to the supposed wonders of apt-get.  They swear that there are a few, if any, applications that still result in dependency hell.


Constructive criticism is usually appreciated, but with FOSS software, too much talk gets you a "do it yourself". The software is the result of largely volunteers and is a wonderful development in computers. 

I have **never** had trouble on Ubuntu with dependency issues. Of course, with the tens of thousands of packages available, a few instances of having to actually do something other than pressing enter are worth it.

---

### Post by Nano Geek on 2007-12-22
And also, if you want to compile a program yourself, just run this before you do.```
sudo apt-get build-dep <program-name>
```That will get all the dependences in 9/10 cases. 

Have Fun. :)

---

### Post by adam.tropics on 2007-12-22
Palmyra you seem to be suggesting we are in some sort of mass denial! Honestly, things do get fixed, and I think many people will tell you that 'dependency hell doesn't exist' thing, because it's not something that has affected them personally. Not all things can be fixed at once however, and I suppose one of the ideas behind triage is to prioritize fixing things that negatively impact the most users. So at a guess, per your examples, the Open Office issue would probably attract more attention.

As to whether or not the community, either here or as a whole is guilty of anything at all...? Look we all do what we can. Could we do more? For sure, (nearly time for those new year's resolutions!) but as far as I am aware we are not going out of our way to mislead you as to the existence of problems.

---

### Post by 23meg on 2007-12-22
[QUOTE=p_quarles]Btw, the specific error with wxD that you encountered is different from the one currently open on Launchpad. You should be sure to add your data:
[https://bugs.launchpad.net/ubuntu/+bug/157460](https://bugs.launchpad.net/ubuntu/+bug/157460)[/QUOTE]

No, that bug isn't legitimate, since wxDownload Fast isn't in Ubuntu; it should be filed in [the project's own bug tracker]("http://sourceforge.net/tracker/?group_id=106901&atid=645951"). I'll close it.

---

### Post by 23meg on 2007-12-22
[QUOTE=Palmyra]
1. wxDownload Fast has been giving me lots of segmentation fault errors, so it appears only compiling it is an option. Oh well...guess what? I appear to be missing something wxDownload Fast requires. Okay...looking for this little thing, run around, find it, install it, another problem springs up, and so on. [/QUOTE]

This is a free software application that's not in Ubuntu's repositories, right? If it *were* in the repositories, you wouldn't have to compile it, need dependencies, go looking around for it, suffer from segfaults, so on. And if it's free software, and fulfills a real use case, it should be in the repositories. 

Now that the "real problem" is defined well (application xyz isn't in Universe), here's what to do about it: 

[list][*]If you know how to package software, [package it, and submit it for inclusion in the repositories]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages#head-3b4a39acc527ae992fb5ebf6704f11b3828ce0a6"). You don't have to be a developer; many Universe packages are made by[ people who aren't official Ubuntu developers]("https://launchpad.net/~ubuntu-universe-contributors").


[*]If you don't, [file a needs-packaging bug]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages#head-3e14a980f129a7e1f22dddcababc80d0c683d990") (similar to [this]("https://bugs.launchpad.net/ubuntu/+bug/178194")) and request it for inclusion in the next release, so that people looking for software to package can know that it's needed and pick it up.[/list]

Remember that there are things you can do about real problems.

---

### Post by p_quarles on 2007-12-22
> **23meg said:**
> No, that bug isn't legitimate, since wxDownload Fast isn't in Ubuntu; it should be filed in [the project's own bug tracker]("http://sourceforge.net/tracker/?group_id=106901&atid=645951"). I'll close it.
My bad. I think I was confusing it with D4x, which is in the repos.

---

### Post by undine on 2007-12-22
Pfft, whatever.

---

### Post by Spike-X on 2007-12-22
> **Palmyra said:**
> 
PS:  Please don't offer solutions to the above mentioned problems.  Please focus on the point of this thread.

Pointless whining?

---

### Post by macogw on 2007-12-23
> **LaRoza said:**
> I have **never** had trouble on Ubuntu with dependency issues. Of course, with the tens of thousands of packages available, a few instances of having to actually do something other than pressing enter are worth it.

Nor have I.  Solaris is a monster though.  GCC can't be untar'd because Solaris's tar is broken, so that has to be compiled first.  Test is implemented wrong in their /bin/sh too so ./configure's end up breaking when you try to compile other stuff, so you have to compile GNU Bash first...so much yak shaving

---

### Post by EdThaSlayer on 2007-12-23
I have had segmentation faults in the past, which was impossible for me to fix. Just try your best to tell launchpad or the developers about this error, they could try to fix it for you. Sometimes there are workarounds through segmentation errors, which can be found by just typing your error in google or searching the developers forums. We are a bit ignorant, but that comes with our whole idea of linux being the BEST, but it isn't yet as it still needs a lot of more work.

---

### Post by popch on 2007-12-23
> **Palmyra said:**
> In some places, constructive criticism is appreciated.  In many places, constructive criticism is worth a lot more than praise.  I don't know that is the case here, in this community, and even the greater Linux community..

YMMV. I don't know that this is not the case here in this forum. I have seen quite a few threads were people very openly discussed flaws or outright bugs in the distro or in applications in the repos. 

As you point out, there are also people who go into denial or who think pointing out a flaw is poor behaviour.

As others have pointed out: this is a community of users with varying degrees of experience. Asking for support on products which are not part of the default distro might be chancy.

In short: I accept your point of view. I do not agree that this community has the 'structural problem' you perceive.

---

### Post by DeadSuperHero on 2007-12-23
I've had many errors with dependancy hell, but that's only because I tend to try to use core files from Debian Sid, or I try installing two packages with the exact same thing.
The best way (for me)  to fix this is to just do:
sudo aptiude install (somereallysmallprogram), enter password,   hit Y, then Yes, and it solves the problem.

---

### Post by plun on 2007-12-23
> **Palmyra said:**
>   I am just saying the following: stop whining about Windows, and let's get our hands dirty with fixing bugs.  As I have said in another thread I created, which was hardly noticed, Windows doesn't make segmentation faults go away, it doesn't make Firefox lighter, it doesn't make Nautilus integrate better with other applications, etc.  **It seems to me more time is spent talking about how bad Microsoft and Windows are than talking about real problems**, *now*.

PS:  Please don't offer solutions to the above mentioned problems.  Please focus on the point of this thread.

Well... "bulls eye", thanks !!   :)

Open Source devs often uses a strange "singing in the rain" attitude...and they are backed up from a community minority.

For example.

- 4 different Firefox versions because of Mozillas license...:)

- Forked/closed projects because of no leadership, or weak "one man" projects.

- Bad focus on "upstream"....

and so on....

---

### Post by averagebeatboy on 2007-12-23
A great post.  We should stay in our own backyards and stop looking at how green or yellow the lawn id next to us -- I know a pretty bad metaphor -- but I think we all get the point.

Happy Holidays to all!

---

### Post by toupeiro on 2007-12-23
the "Ubuntu community" is not the representative of the worlds open source software library or their developers, we are advocates of one operating system that brings them together in a way we feel is much more user friendily than other options available to us.   We can contribute to some of those affiliated, unaffiliated, or distribution independent projects, as many of us do, but we do so on our own conditions, which may or may not include the Ubuntu OS.  Specifically charging the "Ubuntu community" with granular project work (or, specialized support), like you describe, also takes away from the greatly needed pool of generalized support that is required to maintain a community like this.  There may be some better suited to do both, but its not the sole responsibility of the "Ubuntu community".  This is peoples limited time you are indirectly referring to, and I for one don't appreciate being grouped in a label of guilty of negligence to a community I support in my small amount of free time I have.  I'm not angry, I am just trying to show you a different point of view.  I am most likely not the only one who feels this way.  

The "Ubuntu community" is not representative of aptitude, we advocate its usage because it does, in most cases, resolve dependency issues.  Is it a perfect science?  no.  Is that the fault of  the Ubuntu community that its not a perfect science?  not in the least!  Does your complaint exist across all facets of software, including very expensive Microsoft ones.  You better believe it does!  Basically, I think that putting your charges on the  "Ubuntu community" is misplaced, uninformed, and unfair.

The "Ubuntu community" does its best represent the voices of the Ubuntu user base.  I, as one of those many voices, know I have written about segmentation faults before, and I know they are not always software dependency based.  They can just as easily be permissions based, or even hardware based.  My point is, by choosing to recompile, you are basically making your own choice of using a ten pound sledge for a job that may only require a screwdriver, a reduced frustration level, and Google.

The community might not have the answer to everyones  problems, but that does not mean you are being ignored.  Some people may be researching whatever problem you feel is being ignored on the web, which by the way, is the exact same thing you could be doing for yourself.  I think the only problem here, is your perception if you think the Ubuntu community is guilty of anything you just outlined.

---

### Post by floke on 2007-12-23
Sorry to go off the point (on which I agree) - but have you tried axel?

---

### Post by bufsabre666 on 2007-12-23
> **Spike-X said:**
> Pointless whining?

exactly what i thought, honestly ive never had a problem these forums havent solved in about 20 minutes at most

---

### Post by averagebeatboy on 2007-12-23
I agree with Ag ....

...I was just saying that if we concentrate on our own backyards and not Windows it would make the moderators jobs a heck of a lot easier.  I understand  that the moderators have to work with what they have  which is given to them by Canonical or Ubuntu (I am not sure of the corporate structure.)  But for volunteering your valuable time and trouble to share it with us for this OS is something that would never have gotten Ubuntu to where it is.

I just want to take this time to point out to the users (myself included) this is not WINDOWS it is UBUNTU!  And to give a heart-felt thanks to these volunteers without whom I probably would have given up on Ubuntu a while back.

Just keep it on the subject guys and make the administrators on down an easier time in dealing with problems  with Ubuntu ... not comparing it with Windows.

I made that mistake a few days ago and offer up my largest apologies to all who help with Ubuntu while I have a childish "fit."

May all administrators and down to users have the best of the Holidays and try to not bitch about this or that that no one on these volunteer boards can help with.

They do tell you ... to wait and think about it before putting it on your machines.  Read up on Ubuntu; come to the boards and just look at some of the postings; especially those that may relate to your machine(s), et cetera.  It makes a much more pleasant experience when and if you do make the plunge.

At all costs, avoid something like the childish tantrum I threw threatening to take Ubuntu off of 10 machines.  Like anyone could care! The answer I got (even though mine was anything but pleasant) was pleasant and understanding.  These volunteers are not perfect but since my time of using Ubuntu they sure do come close.

Again, have a very pleasant Holidays and unite behind Ubuntu let us not make the mistake of fracturing it.

Cheers,

Averagebeatboy  :guitar:

P.S.  Use the maxim when you post: "You can catch a lot more bees with honey than you can with vinegar."

---

### Post by original_jamingrit on 2007-12-23
Hi

This is directed at the OP and the general point of this thread.

The things you say are true.  There are some general problems in the design of the system.  Ubuntu as a distro is intended to make things easy for you, but in order for that to work you will need to make some concessions, and do things in the way they are provided.  Ubuntu does this by preventing you from running in root, and by only using Ubuntu-approved and tested applications in the repos.  This is, of course, not to say that you shouldn't experiment, or use Ubuntu for things that most Ubuntu users would not.  Just keep in mind that in order to do that you will need to bypass those safegaurds put in place with the average user in mind.  So don't complain too much if you get burned.  Just like in the early stages of compiz and beryl development; if you break it with unstable software, you get to keep both halves.  In the states case, there's plenty of other repositories other than the Ubuntu repos available.

If this still bothers you, then maybe you would like to try experimenting with other, more intermediate-user distros, maybe Debian or Gentoo.  I'm sorry you're not satisfied here, but perhaps your goals are different than the Ubuntu Community's at large.

---

### Post by lost4now on 2007-12-23
I am one of those who gave up on ubuntu and went back to windows. Everyone who tries to use ubuntu isn't interested in modifying the DNA of some slippery bug. They also get a bit tired of being flamed and put down for laying their problem out for the world to criticise and get an ignorant juvenile response. 

Just maybe it is time for the powers that be to back off the mad rush to where ever they are rushing and take a look at the big picture and make what they have already released work. That is spelled "function without having to screw around with it"

When an officially supplied app doesn't work then it is as much the fault of the operating system as it is the app. Face it folks. ubuntu aint prime time ready and probably never will be. Unless you want to spend half your time fine tuning ubuntu probably isn't your best choice either. It just takes some of us longer to figure that out than others.  

This board touts umpteen thousand questions and answers. What small percentage of them are really solutions to problems. Those of you with the huge bean counts that think they are really helping might do better writing tutorials if you are are knowledgeable as you think.

With that off my chest I do feel better. Have a nice Christmas.

---

### Post by popch on 2007-12-23
> **lost4now said:**
>  Have a nice Christmas.

Thank you, and same to you.

---

### Post by p_quarles on 2007-12-23
> **lost4now said:**
> I am one of those who gave up on ubuntu and went back to windows. Everyone who tries to use ubuntu isn't interested in modifying the DNA of some slippery bug. They also get a bit tired of being flamed and put down for laying their problem out for the world to criticise and get an ignorant juvenile response. 
If you were flamed or insulted here, you should have reported it to the staff. 

> Just maybe it is time for the powers that be to back off the mad rush to where ever they are rushing and take a look at the big picture and make what they have already released work. That is spelled "function without having to screw around with it"
The "powers that be"? Who would that be? The developers? What part of this alleged "big picture" do you think they are missing? 

> When an officially supplied app doesn't work then it is as much the fault of the operating system as it is the app. Face it folks. ubuntu aint prime time ready and probably never will be.
Yes, I agree. But every operating system in existence has shipped with default applications that present seriously disruptive problems for users. If a bug-free OS is the criterion for "prime time ready," then I'm afraid that software in general isn't ready. 

> Unless you want to spend half your time fine tuning ubuntu probably isn't your best choice either. It just takes some of us longer to figure that out than others.
Some of us simply haven't had problems that required us to fine tune our systems before it works. In my personal experience, I've had more difficulty getting things to work in Windows to my liking than I have in Linux. That's not to "criticize" your experience or "flame" you -- it's just acknowledging the obvious fact that mileage may vary. 

> This board touts umpteen thousand questions and answers. What small percentage of them are really solutions to problems. Those of you with the huge bean counts that think they are really helping might do better writing tutorials if you are are knowledgeable as you think.
What makes you think anyone would read them? The vast majority of questions asked here are already well-documented in various places. People ask questions here because they're not sure what they're looking for, or don't quite understand how to use the tutorials they've read. 

> With that off my chest I do feel better. Have a nice Christmas.
You too.

---

### Post by Presto123 on 2007-12-23
*Sigh*

I have already mentioned this before, and as some people here have stated: we are doing this on our own time, free to you. There are so many questions people ask, that many people are trying to get to. Unfortunately, many of you want us fellow users to hand you the computer in perfect state on a silver platter. Not everyone's experiences will be the same, either.

The Ubuntu community is trying to devote their time to help you as much as they can...seriously, no one, to the best of my knowledge, is getting paid to help you.

This is also an open forum and despite how much you dislike it, we will have our own opinions and I personally don't care how some people feel about it. I honestly hate Windows, sorry, it is my opinion with my own reasonings and experiences with it. 

Lets look at it this way, if you are devoting your time to helping others, wouldn't you want a place to talk about OTHER things besides JUST the OS? Especially if you have gotten to enjoy your fellow OS people?

I know I am guilty of being defensive of the Ubuntu OS because it was very simple for me as a previous Windows user to get to know and I love the fact that it is a free and community contributed system.

We, the community, are not the problem and very few here have the elitist issues. In my beginnings with Ubuntu 3 months ago, I cannot remember anyone being downright mean with me because I was new or anything...there were a FEW that were cranky, but it's like life. You're dealing with REAL people, not some corporate slaves purely involved in 1 aspect of the OS.

---

