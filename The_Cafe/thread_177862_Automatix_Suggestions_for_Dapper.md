---
title: "Automatix Suggestions for Dapper"
date: 2006-05-16
forum: The Cafe
---

### Post by georgetoon on 2006-05-16
So, if someone is using Breezy and has Automatix installed and then upgrades to Dapper, then Automatix will no longer work?  Will all the plug-ins previously installed from Automatix work in Dapper?

---

### Post by nalmeth on 2006-05-16
Have you collaborated with Iandefor at all? His bumps script is the closest thing yet for dapper. It was buggy buggy buggy at first, but I use it for fresh dapper install's (will be using again in couple of days). 

Sorry if I missed a thread discussing this already. 

Also, now that sun-java is available in multiverse, this helps out big time.

I don't know what I am capable of contributing, unfortunately... Hopefully I will find something I can help with.

---

### Post by arnieboy on 2006-05-16
[QUOTE=nalmeth]Have you collaborated with Iandefor at all? His bumps script is the closest thing yet for dapper. It was buggy buggy buggy at first, but I use it for fresh dapper install's (will be using again in couple of days). 

Sorry if I missed a thread discussing this already. 

Also, now that sun-java is available in multiverse, this helps out big time.

I don't know what I am capable of contributing, unfortunately... Hopefully I will find something I can help with.[/QUOTE]
When the Breezy cycle started, quite a few softwares dependent on Java would not work on Blackdown's version and had severe incompatibilities. Hence we had to resort to pulling Sun's version 1.5 from the plf repositories. At the fag end of the Breezy cycle however, these softwares (read azureus, frostwire etc) have released versions which are compatible with Blackdown's version and Automatix for Breezy itself does not pull 1.5 any more unless explicitly requested (in one of its options).

---

### Post by arnieboy on 2006-05-16
[QUOTE=georgetoon]So, if someone is using Breezy and has Automatix installed and then upgrades to Dapper, then Automatix will no longer work?  Will all the plug-ins previously installed from Automatix work in Dapper?[/QUOTE]
Automatix currently will not work on Dapper. This thread is dedicated to releasing a version of Automatix which works on both Breezy and Dapper. 
Yes, all plugins which work on Breezy (installed from the current version of Automatix) will work on Dapper.

---

### Post by mstlyevil on 2006-05-16
[QUOTE=georgetoon]So, if someone is using Breezy and has Automatix installed and then upgrades to Dapper, then Automatix will no longer work?  Will all the plug-ins previously installed from Automatix work in Dapper?[/QUOTE]

You will have to upgrade all the codecs to gstreamer 10.

---

### Post by arnieboy on 2006-05-16
[QUOTE=mstlyevil]You will have to upgrade all the codecs to gstreamer 10.[/QUOTE]
mstlyevil: gstreamer0.8 also works on Dapper. version 0.10 is an add-on rather than an upgrade on Dapper.

---

### Post by mstlyevil on 2006-05-16
I see.

---

### Post by prizrak on 2006-05-16
Quick question, is the Automatix also beta since Dapper is?

---

### Post by endersshadow on 2006-05-16
[http://ubuntuforums.org/showthread.php?t=138889](http://ubuntuforums.org/showthread.php?t=138889)

I'm a lotta bit upset that you didn't at least look into this before hand.  Iandefor has put a lot of work into BUMPS, and it is only getting better.  I think that the automation efforts would be best aimed there.  He's already got Ubuntu and Kubuntu packages in one program.

---

### Post by endersshadow on 2006-05-16
[http://ubuntuforums.org/showthread.php?t=138889](http://ubuntuforums.org/showthread.php?t=138889) - Iandefor has already started such a thing.  BUMPS.  He's been working on it and has advanced it plenty since its initial creation.

I would suggest that automation efforts be focused on BUMPS instead of reinventing the wheel.

---

### Post by arnieboy on 2006-05-16
[QUOTE=endersshadow][http://ubuntuforums.org/showthread.php?t=138889](http://ubuntuforums.org/showthread.php?t=138889) - Iandefor has already started such a thing.  BUMPS.  He's been working on it and has advanced it plenty since its initial creation.

I would suggest that automation efforts be focused on BUMPS instead of reinventing the wheel.[/QUOTE]
You are welcome to join any effort you wish. 
We are not reinventing any wheels here.. please try to stick to the topic of this thread.

---

### Post by endersshadow on 2006-05-16
[QUOTE=arnieboy]You are welcome to join any effort you wish. 
We are not reinventing any wheels here.. please try to stick to the topic of this thread.[/QUOTE]

I am sticking to the topic of this thread.  Dapper has completely new packages and methods for what the original Automatix did.  I think if you could add the functionality of Automatix and the support that it garnered over the past few months to BUMPS, we could have an amazing tool for beginners when Dapper hits release in June.  It seems to me a better use of community resources and intellect to have one automation system rather than everybody vying for their own egos.  The point here is to create a great script that works.  Automatix evolved from humble beginnings to a great and multifacetted program.  And you didn't do it alone.  Iandefor has put a ton of work into BUMPS already, and if the real point is to make a great automation script, the community helping, supporting, and adding to BUMPS is the easiest and best path to that, in my opinion.  You're calling on the community to build you a new Automatix, but it's already been done and being done.  BUMPS has had some initial success, but I feel that with community support and additions it can become for Dapper everything that Automatix was and more.

And that is right on point with this thread.

---

### Post by briancurtin on 2006-05-17
i agree with endersshadow, and i dont even use ubuntu anymore. i still read the forums a lot since they are pretty active during my boring days, and ive read into Iandefor's project. ive even checked out some of his code before to see what hes up to. it looks like a great project and the dude has put a lot of work. i hope to see his program get a lot of use, and get some help so it can become more widely used. 

i think focusing on BUMPS would be a much better thing seeing the progress that was already made

---

### Post by nalmeth on 2006-05-18
BUMPS rules. If automatix hasn't even been started yet then I would have to agree that BUMPS should be the base of the next automa-script. Iandefor has worked hard to make it in the absense of anything similar for dapper, and I support him and his project. He patiently helped me out and other's when his script was young and buggy, and there already are people who have contributed to his project, like endersshadow. 

Why disregard it and start over when we already have at least most of the work done? Why don't we *all collaborate* on project's that are already off the ground rather than start new ones for the some purposes? 

BTW, arnieboy was the OP when I first replied, what's the deal with that?
Has the thread been changed or something?

---

### Post by mstlyevil on 2006-05-18
[QUOTE=nalmeth]BUMPS rules. If automatix hasn't even been started yet then I would have to agree that BUMPS should be the base of the next automa-script. Iandefor has worked hard to make it in the absense of anything similar for dapper, and I support him and his project. He patiently helped me out and other's when his script was young and buggy, and there already are people who have contributed to his project, like endersshadow. 

Why disregard it and start over when we already have at least most of the work done? Why don't we *all collaborate* on project's that are already off the ground rather than start new ones for the some purposes? 

BTW, arnieboy was the OP when I first replied, what's the deal with that?
Has the thread been changed or something?[/QUOTE]

The issue is not up for debate since Iandefor and arnieboy refuse to compete.  Iandefor has stated Automatix should be concentrated on by the community since it has a different direction and is more familliar to users. BUMPS is going to continue but as a simpler script for just basic multimedia.

Believe it or not I am currently testing the new development version of Automatix and it works on both Breezy and Dapper. It is not as hard as you think to get Automatix ready in time for Dappers release. Automatix is off the ground and has been far longer than BUMPS. This is not an issue since there will be a Automatix ready for Dapper in a couple of weeks.

This issue was resolved this morning and there is no point in keeping it going. Iandefor supports Automatix and arnieboy supports BUMPS. If the leaders of these two projects can make peace then the rest of the community needs to also.

There will be some news concerning the BUMPS project here real soon. For those of you who love BUMPS, you will be pleased with the news.

---

