---
title: "Giving CREDIT, where/when CREDITS is due"
date: 2006-11-09
forum: The Cafe
---

### Post by dannyboy79 on 2006-11-09
A little info, I am completely new to linux. First Distro is Ubuntu Dapper, I think I first tried Flight 5 back in March, so needless to say, I am what you call a newbie. I am now using Dapper, I believe the exact name of the download was 6.06.1.

I came to this forum for help on pretty much anything and everything related to linux in general and obviously Ubuntu specific things. I recieved great help installing and setting up my ftp server using proftpd 1.2.10-27. I set it up using TLS as I thought it would be a good idea to encrypt the password when I sent it to my server, no annoynomous access here! There is a great how-to for proftpd with user access that I used in these forums. The author of the how-to helped me along the way and he is a very nice person. We PM'd each other several times regarding folder access limits, write limits etc etc. Well, one day I noticed that there were updates, so I clicked on the little orange icon and I wanted to review them before I clicked install. I noticed that proftpd had an upgrade (this is apparently due to my sources.list having the backports enabled) and I thought, "man, i just installed it, hopefully it doesn't screw it up!" So I upgraded and proftpd asked me if I wanted to keep my current cong file or use the new one supplied. Well I don't know what happened but I screwed something up and ended up just doing a sudo aptitude remove proftpd && aptitude purge proftpd and did everything again. Well I got it back to the way it was but I noticed that this time, when I would restart the server, it didn't ask me for the passphrases for the server.ca and key.ca or whatever those 2 files are, it's because if you want proftpd to use tls the key is actually encyrpted within those files. That's funny? It used to always ask me for the passphrases prior to me upgrading to version 1.3?? So I thought I would go back to the guy that has helped me with proftpd all along, the author of the how-to, I sent a pm to him. He told me to erase my cert folders and redo all the tls stuff. I did it all again step by step and it still wasn't working, I mean the server was working fine, it was the fact that when I chose to restart the server after changing some settings, it didn't ask me for the passwords. I asked him how I would know if the password I send to the ftp server was actaully using tls and he said, it would say it while it's logging in, well, it wasn't working with tls. So he said that if I re-did all the tls steps over correctly, which I did, I actually did them like 3 different times, he couldn't help me anymore, so off to gogle I went. After hours and hours and forums upon forums I finally established that Proftpd version 1.3 that's in the Dapper Repo's does NOT have mod_tls.c and a few others like sql compiled into it!! What gives? So I again went back to the guy who wrote up the proftpd how-to (he is a forum moderator I forgot to mention this), I informed him of my findings and he confirmed that I was correct and that he would write a bug report (see here; [https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735)and](https://launchpad.net/distros/ubuntu/+source/proftpd/+bug/68735)and) inform the developers. I thought, WOW, I am a newbie and I figured this out??? I was so happy with myself. I wrote a thread immediately, (here it is: [http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd)) trying to get the word out to people so that they WOULDN'T upgrade (if they have backports enabled) if they wanted to use TLS and they didn't want to have to compile version 1.3 from source. All of a sudden I see a thread started by the author of the proftpd how-to (the guy that I had informed this security issue to) that states that the proftpd version in Edgy doesn't have mod_tls compiled in. So I posted a comment asking for my credit or props for being the one who actually found this out. He PM's me telling me he doesn't know what I am talking about and how he doesn't like my tone and that he doesn't know what credit I am looking for. Well I am pretty frustrated by this obsurd accusation so I start copying and pasting all the PM's that went back and forth between him and I regarding this matter and he still won't acknowledge that I should get credit for this! I mean, come on, I am a newbie, you would think that a forum moderator would have the decency to give a linux n00b/newbie some credit for this??  

So, my question is, should the thread that warned of proftpd in Edgy not having tls compiled into it have credited the person who originally found and documented this security flaw with the version 1.3 which is in the Dapper backport Repo's as well as the Edgy repo's? 

Next question, was it acceptable for me to ask that he give me credit, I figured he may have just not remembered my screen name or maybe even forgot about our whole conversation (although I don't see how you can forget that since it was only a week ago)?

Thank you if you read this and respond.

---

### Post by dbott67 on 2006-11-09
Well, it would be nice to give credit where credit is due, however, you can rest easy knowing this: you were able to figure out the problem on your own.  It is good that you are learning how to search effectively, trouble-shoot and ultimately help yourself.

As for the person who posted the bug report, he did not appear to take credit himself, he just did not acknowledge that it was you who pointed out the problem.  I honestly don't know if the Launchpad is generally used to 'credit' the finder of the bug (unlike most MS patches that credit eEye or other person that finds a vulnerability) or if it's just a somewhat anonymous place to post bugs.  My advice --- don't lose any sleep over it.

The internet-at-large may not know about your findings, but YOU do (and so do I).

Good detective work, Sherlock Holmes! :)

-DAve

---

### Post by woedend on 2006-11-09
while it is nice to give credit where it's due, its generally more of a nice gesture than anything else.  Demanding credit is kinda childish to me.  Just be glad that you figured it out and could help others, thats what community is all about really.  
As a counterpoint, imagine if EVERY line of help had credit to it.  That is, everytime someone answered a question, they had to search the forums AND the internet to find who actually figured it out first.  And, what if perhaps someone else figured this TLS thing out beforehand, and then in turn demanded credit back.  just gets to be messy.
but good work anyhow.

---

### Post by PriceChild on 2006-11-09
Thread moved to Resolution Center so that dannyboy79's issues with the moderating staff can be resolved.

He has been notified the thread has been moved here.

**ONLY dannyboy79 and the Forum Administrators are permitted to reply below this post!**

---

### Post by dannyboy79 on 2006-11-09
There is absolutely NO REASON the should have been moved here. I want a LEGITAMANT DOCUMENTED REASON why this was moved. I put it in the Cafe because I want to hear what others have to say about giving credit where it is deserved and if I was out of line to ASK for credit, I never ever demanded it. I have broken no rules and for this to be moved here is simply an abuse of power by the moderator and I want this returned to either the backyard for everyones feedback or back in the Cafe. Thank you.

---

### Post by KiwiNZ on 2006-11-09
I will look at this and respond in due course

---

### Post by dannyboy79 on 2006-11-09
> **KiwiNZ said:**
> I will look at this and respond in due course


thank you.

---

### Post by dannyboy79 on 2006-11-09
Two simple questions for everyone

1. The scenario, you inform someone about a security issue with a newly provided deb in the repo's. They go off and start a thread informing everyone about the issue and not mention your name at all. They also post that same security issue in 2 other locations throughout the forums and not once mention that you were the one that informed them about it.

1. The question, would you be disappointed with this person and had wished they would've mentioned your name at least once? (Key ingredient, you are a linux n00b who after hours of research found this security issue within the compiled deb)

2. The scenario, it just so happens that this actually occured to me today! I posted a comment within the thread ASKING, NOT demanding, for some credit. 

2. Question, would you have done the same thing, if not, what would you have done if anything? (Again keeping in mind how stoked you would be regarding the fact that less than 6 months ago you knew absolutely nothing about linux!)

Note: I wish I could be more detailed but the first time I posted these questions I had included the whole story that unraveled to get my point accross and it was moved to the resolution center stating the reason being, well, I can't tell you why, otherwise this thread might get moved as well.

---

### Post by matthew on 2006-11-09
In the open source community you will find two extremes on this issue as well as the majority of people somewhere in between them. 

Some will say "credit me for everything I say, do, or even think" and it becomes akin to crying out for attention and the spotlight.

Others will say "you should always try to do what you can to help others whether anyone notices or not." This can lead to hurt feelings and burnout.

Bottom line ***for me personally***: I would be happy to have helped someone else whether acknowledged or not, although it is certainly nice when efforts are appreciated and noted. Striving for recognition makes people look petty and small but never giving recognition does the same thing. In other words, it's all about balance and gracefulness.

---

### Post by po0f on 2006-11-09
dannyboy79,

You should have GPL'd your solution.  As such, it is public domain, and you lose all credit.  Sorry.

Seriously, I believe you should get credit, but are you really all that worried about it?  Bug finding is everyone's job and everyone should benefit, so in the end it doesn't matter.

When programming, I always at least add a comment to someone's contribution with their name and point of contact (from a forum/IM/whatever) next to whatever code the person helped me with.  It makes me feel better, but most of the time people really don't care, so meh.

---

### Post by 23meg on 2006-11-09
> 1. The question, would you be disappointed with this person and had wished they would've mentioned your name at least once?I would, but 
> 2. The scenario, it just so happens that this actually occured to me today! I posted a comment within the thread ASKING, NOT demanding, for some credit.

2. Question, would you have done the same thing, if not, what would you have done if anything? I wouldn't go to any greater length than giving them a notice of my disappointment privately.

---

### Post by shining on 2006-11-09
I don't think I would care, the only thing I care about is that bugs are found and fixed, it's the only thing that matters, and that will benefit to all.
Of course, credits are always welcome, especially when you spent a long time on something, and did a good job. But well, I never think I do (a good job), so..

---

### Post by PriceChild on 2006-11-09
This issue is currently being handled in the Forums Resolution Center: [http://www.ubuntuforums.org/showthread.php?t=296337](http://www.ubuntuforums.org/showthread.php?t=296337)

The original thread was moved there. The final decision will be made by KiwiNZ.

---

### Post by matthew on 2006-11-09
> **PriceChild said:**
> This issue is currently being handled in the Forums Resolution Center: [http://www.ubuntuforums.org/showthread.php?t=296337](http://www.ubuntuforums.org/showthread.php?t=296337)

The original thread was moved there. The final decision will be made by KiwiNZ.I don't think the issue is so much about wanting to resolve the specifics in this case. 

I think the original poster's feelings were hurt and he wants some comfort and understanding or at least some perspective assistance in case his expectations were out of sync with reality.

---

### Post by NeoLithium on 2006-11-09
I dont know; I'd be just plain happy that I helped out the whole community in general; I never ask for any thanks or credit for it; which makes when it DOES happen, all the much better. Just cause someone's name isn't highlighted somewhere, does that give you any less satisfaction? It shouldn't; really, know in yourself that you did something quick and helped out the whole project.

Congratulations on finding it.

---

### Post by dannyboy79 on 2006-11-09
> **matthew said:**
> I don't think the issue is so much about wanting to resolve the specifics in this case. 

I think the original poster's feelings were hurt and he wants some comfort and understanding or at least some perspective assistance in case his expectations were out of sync with reality.

thank you for actually understanding matthew. they moved my first thread and they had no reason to! The thread was not trying to point out that I had a problem with a person, that wasn't my goal at all, my objective was to find out what others would have done and if I was out of line with what I did. i only had to include the story and what occured between myself and then person so that the people giving their opinions would be able to make an educated opinion based on the facts.

---

### Post by KiwiNZ on 2006-11-10
Two Threads merged

---

### Post by frodon on 2006-11-10
Question, what would happen in this thread if each person would ask for credits for finding a bug ? :
[http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364)

And how handle duplicate bugs, who was the first ? who to credit in this case ?

Seriously, if you find a bug and chose to share it then you do it for the community and to help others not for the glory, if you did it for the glory you should really not report bugs as it's a common use to not credit the person who find the bug.

As for the thread you talked about i remind you that since the moment you asked for credits i deleted it to let you open your own and thus get the glory you're looking for, thing you didn't even take the time to do.

---

### Post by matthew on 2006-11-10
> **dannyboy79 said:**
> thank you for actually understanding matthew. they moved my first thread and they had no reason to! The thread was not trying to point out that I had a problem with a person, that wasn't my goal at all, my objective was to find out what others would have done and if I was out of line with what I did. i only had to include the story and what occured between myself and then person so that the people giving their opinions would be able to make an educated opinion based on the facts.Just so it's clear, I really don't think anything wrong happened. You pointed out a bug (good job noticing it, btw...that's a good feeling, isn't it?). You told someone who told someone else and also posted so that others could know how to avoid/fix the problem. That was your ultimate goal, wasn't it? 

I don't think it was an intentional slight when your name wasn't mentioned. 

In these cases sometimes the original bug finder is mentioned but usually he isn't, often because more than one person finds it and also because the ultimate objective is a good product, not a ribbon for your chest or a certificate of achievement for your wall. We have some people who find as many as a dozen bugs in one day. Can you imagine the logistical and community relations nightmare it would cause if each of them said loudly, "Hey, wait a minute! I found that!! You have to mention my name here too." 

The overwhelming majority of people who find/report bugs are doing it to give something back to a community that has given them so much and consider what they have done as more of a thank you than something worthy of attention.

I hope that helps with some perspective. :)

---

### Post by wieman01 on 2006-11-10
In economics you'd call this a **multiplier effect**. You tell someone who - in return - tells someone else. Innovator, imitator, if you know what I mean. That's a very basic principle & I am glad to see economics (well, it's more applied social studies if you ask me) do play a role in the forum. 

This way many can benefit from one smart idea. In my opinion this is the very spirit of Ubuntu. The credit goes back to the community.

That's my two penny worth.

---

### Post by dannyboy79 on 2006-11-10
> **frodon said:**
>  Question, what would happen in this thread if each person would ask for credits for finding a bug ? :
[http://ubuntuforums.org/showthread.php?t=283364](http://ubuntuforums.org/showthread.php?t=283364)
Well, did the person who is asking for the credit, actually communicate the bug to you? Most likely not, you simply took info that you learned and info that you saw others document and you put it in 1 place. 

> **frodon said:**
> And how handle duplicate bugs, who was the first ? who to credit in this case ? This is not even close to the same situation, it wasn't about who found this bug first, it was the whole point that I found and it and informed you about it. I documented it here ([http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=286147&highlight=proftpd)) and instead of you adding to this thread you went off and created your own thread and didn't point out that this was found and pointed out to you by myself. That's what all you guys are missing here. If someone found it before me than great. If that person who found it would have told me about it, then when I went to TELL YOU about it, I would have said, so and so found that, "blah blah". I have seen plenty of forums that state, "I ended up solving blah blah because of blank told me to do this or blank pointed me to this thread, which I feel is the right thing to do.

> **frodon said:**
>  Seriously, if you find a bug and chose to share it then you do it for the community and to help others not for the glory, 
I agree, I never once did it for the glory or demanding credit, the point of all this was because when I "asked" you to mention my name or for some credit, you acted as if you didn't know what I was talking about and states that you didn't know what credit I was looking for. 

> **frodon said:**
>  if you did it for the glory you should really not report bugs **as it's a common use to not credit the person who find the bug.**  That's just not true, I see people saying thanks to others for finding and solving things all the time.


> **frodon said:**
> As for the thread you talked about i remind you that since the moment you asked for credits i deleted it to let you open your own and thus get the glory you're looking for, thing you didn't even take the time to do. 
Which is what I don't understand, why would you delete something that was helping the community? It wouldn't have been hard to simply mention the fact that I pointed this out to you. As far as posting my own thread and you saying that I haven't taken the time to do this, that's just false, I posted a thread a week before your's, it's link is above.

> **matthew said:**
>  I don't think it was an intentional slight when your name wasn't mentioned. 
I agree, the main point is that when I "asked" for my name to be mentioned, it was acted as if he didn't know what I was talking about and said he didn't know what credit I was looking for.

> **matthew said:**
> Can you imagine the logistical and community relations nightmare it would cause if each of them said loudly, "Hey, wait a minute! I found that!! You have to mention my name here too."  
Again, that's not even close to this situation, if 10 people found a bug, and then 1 of them, person Y, saw in launchpad or somewhere that the bug was posted by person X and it just so happened that the only reason person X knew about the bug was because person Y informed them about it, then yes, person X should have mentioned that person Y told them about the bug. So my whole point was a name should be mentioned when the person actually informed the person who is posting the bug, not just that they found the bug as well, there's a huge difference. I do appreciate your perspective but I am simply trying to clarify the situation which appears as though no one is truely understanding.

---

### Post by matthew on 2006-11-10
Sigh. Dude, whether you intend to or not you are coming across as petty and small. This really is a meaningless controversy and foolish conversation. 

I gave you the benefit of the doubt that you were confused on how these things go and tried to explain (along with others) the basic philosophy of bug finders, etc. The fact is it probably takes more work to report a bug to the developers than it does to find one, furthermore you were given the opportunity to make your grand post and get all the credit yourself if you wanted to and you declined. You have been treated with kindness and fairness and have repaid that with complaints and all-around grumpiness. That's a real shame.

I am now convinced you are just out trolling for a fight. I'm done with this conversation and I recommend everyone else just let it fizzle out as well. Bye.

---

### Post by dannyboy79 on 2006-11-10
> **matthew said:**
>  Sigh. Dude, whether you intend to or not you are coming across as petty and small. This really is a meaningless controversy and foolish conversation. 
At least you agree that this situation is a controversy. I totally wish it would've gone differently. Needless to say these forums are a great resource it just turns out that courtiousness and just plain doing the "right" thing by others might not be the first thing on people's minds.

> **matthew said:**
> I gave you the benefit of the doubt that you were confused on how these things go and tried to explain (along with others) the basic philosophy of bug finders, etc. The fact is it probably takes more work to report a bug to the developers than it does to find one, 
I thank you for explaining this, I can see how people feel about bug reporting and giving credit when it should be given, that was my goal. 
> **matthew said:**
>  furthermore you were given the opportunity to make your grand post and get all the credit yourself if you wanted to and you declined. 
For the I don't know how manyth time, I did, it is here: [http://www.ubuntuforums.org/showthre...hlight=proftpd](http://www.ubuntuforums.org/showthre...hlight=proftpd)
> **matthew said:**
>  You have been treated with kindness and fairness and have repaid that with complaints and all-around grumpiness. That's a real shame. 
To be honest, no, I wasn't treated with fairness, not at first anyway. My thread was wrongfully moved for no reason. Luckily the admin moved it back after making a rational reasonable decision on whether or not it should be put back in the Cafe. As far as me complaining, if you quote me complaining once then I'll have to apologize but I don't recall complaining at all, not once! I have actually kept my cool throughout this whole thing and am not grumpy. If I have come across as being grumpy that just isn't so and you have read into something that wasn't there.
> **matthew said:**
> I am now convinced you are just out trolling for a fight. I'm done with this conversation and I recommend everyone else just let it fizzle out as well. Bye. 
Nope, you're the one who actually understood where I was coming from and why I posted this, now you're changing your mind? Huh, I am in no way looking for a fight, merely ensuring that people can understand the situation from my point of view.

---

### Post by KiwiNZ on 2006-11-10
OK I have seen enough of this senseless rotating argument. I am putting it to rest .

---

