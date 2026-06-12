---
title: "Idiot-proof, Flawless, Super-easy Automatix2 Installer"
date: 2007-09-30
forum: The Cafe
---

### Post by ryanVickers on 2007-09-30
I've heard it all "ooo, it's too hard to install!", and "don't use it!  It wrecks your system!", and "it adds un-safe repositories!", blah, blah, blah, I don't care what you *_think_* about it, I'm just providing the **simplest** way to install this if you *want* to.  If your looking for a *discussion* on it, go somewhere else :)

Now, to get to the point - simply download, extract and run [this script]("http://www.hotlinkfiles.com/files/434093_cq8ng/autox2installer.gz") of mine, and you'll see that no further instruction is necessary - it's the easiest thing on earth!

What you have to know to use it:
-What version of Ubuntu your running (currently supported: dapper, edgy, and feisty)
-What architecture you have (32 or 64 bit)
If you get it wrong, it will just say so, and you just need to try another one - no harm done - simple as that!

Well, OK, if you want to talk about it, go ahead, but I saw a very un-biased poll by an _**admin**_ here on Ubuntu Forums, and about 96% of people had received good service from automatix, and it did **not** mess up their system! :p

---

### Post by aysiu on 2007-09-30
So now people need a script to install another script to install other things?

Just install others things without the script to install the script--that's what I say. Or use Linux Mint if you can't be bothered.

---

### Post by mlentink on 2007-09-30
That may very well be. 
Alas..., I am one of the 4% (though I sincerely doubt it&#347; not more than that) that had to reinstall because of a mess-up. 
It may very well be visitors to this thread might want to read [this]("http://ubuntuforums.org/showthread.php?t=519872"). And that's official.

---

### Post by aysiu on 2007-09-30
By the way, I'm the moderator (not admin) who created [the unbiased poll](http://ubuntuforums.org/showthread.php?t=518244&page=8), and it's actually 64% (87 out of 135) of Automatix users who had no problems, not 96%.

---

### Post by ryanVickers on 2007-09-30
> **aysiu said:**
> So now people need a script to install another script to install other things?...

yeah, pretty much! :lolflag:

But you have to admit, it's pretty nice!  You would not **believe** how many people just can't get it to install properly because of bad instructions etc.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by ryanVickers on 2007-09-30
> **aysiu said:**
> By the way, I'm the moderator (not admin) who created [the unbiased poll]("http://ubuntuforums.org/showthread.php?t=518244&page=8"), and it's actually 64% (87 out of 135) of Automatix users who had no problems, not 96%.

ok then, forgot

---

### Post by n3tfury on 2007-09-30
> **ryanVickers said:**
>  If your looking for a *discussion* on it, go somewhere else :)



lol, ok champ.

---

### Post by jtbl on 2007-09-30
That poll probably isn't very accurate, unless it had at least a few hundred thousand voters.  The Automatix user base is estimated at about 2 million users and most of those 2 million we never hear from.

---

### Post by Frak on 2007-09-30
> **jtbl said:**
> That poll probably isn't very accurate, unless it had at least a few hundred thousand voters.  The Automatix user base is estimated at about 2 million users and most of those 2 million we never hear from.
I've had no problems with it. 

It messing up anything is a blatant lie. It only downloads from the repos, so you are then saying the repo's are crap. Earlier versions were bad, but they have been heavily refined.

Seriously, all it is was someone who had a great popularity got mad at arnieboy (he wasn't the nicest person) and then ranted about his program. Everybody else followed the popularity and bandwagoned the opinion to its non-existant flaws.

I saw it happen, give it a rest. The poll doesn't lie.

---

### Post by ryanVickers on 2007-09-30
thankyou!

---

### Post by ryanVickers on 2007-09-30
If you like this script, than try out my other scripts/projects (signature)!

---

### Post by antisocialist on 2008-01-11
> **jtbl said:**
> That poll probably isn't very accurate, unless it had at least a few hundred thousand voters.  The Automatix user base is estimated at about 2 million users and most of those 2 million we never hear from.

the whole point of a poll isnt to ask every single person in a certain group a question so you can be exact, its to ask randomly selected users of that group the question. think of it this way;

you could try to ask everyone in the whole country if they like their president, or you could ask everyone at the place you work if they like the president, they both get you relatively similar percentages as far as answers go, but one of them is actually possible to do

---

### Post by macogw on 2008-01-11
> **Frak said:**
> I've had no problems with it. 

It messing up anything is a blatant lie. It only downloads from the repos, so you are then saying the repo's are crap. Earlier versions were bad, but they have been heavily refined.

Seriously, all it is was someone who had a great popularity got mad at arnieboy (he wasn't the nicest person) and then ranted about his program. Everybody else followed the popularity and bandwagoned the opinion to its non-existant flaws.

I saw it happen, give it a rest. The poll doesn't lie.

Actually, a *developer* read every single line of code and found places where it passes the -y flag which automatically says "yes" on apt-get remove, which means it might automatically uninstall things you didn't want to remove and other spots where it set the permissions on some directories wrong (ex: world-writable which is really bad for security).

---

