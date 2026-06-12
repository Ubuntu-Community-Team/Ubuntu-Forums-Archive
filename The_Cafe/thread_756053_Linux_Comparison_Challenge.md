---
title: "Linux Comparison Challenge"
date: 2008-04-15
forum: The Cafe
---

### Post by CAGibby on 2008-04-15
Hello, 

I am new to this form (and to linux for that matter).  I just ran across you guys and I am working on a project that you may be able to help me with.

I want to know if you guys have any ideas on how to test different versions of linux against each other, other than subjective ratings by users.  I have found a few ways I might be able to find these easily enough.

For instance I am trying to get at a way to compare number of bugs, number of crashes, etc.  Preferably some way that I could test for myself (set up a distribution, observe number of crashes in a certain period of time)

Of course something like number of bugs could also be seen as a sign of their popularity (more bugs found = more eyes looking), and getting crashes may not be as easy as it would be if I were comparing windows's for instance, but I'll deal with that kind of stuff later if necessary.

So, Does anyone have a suggestion for me?  I'm open to any ideas you guys are willing to share.

Thanks,
Chris

---

### Post by aysiu on 2008-04-15
If you're going to compare bugs, I think it'd make more sense to compare how quickly the bugs are patched once they're discovered and how many outstanding (not-yet-fixed) bugs there are. It may also be a good idea to look at percentages in terms of the severity of the bugs, and which ones are security-related.

---

### Post by CAGibby on 2008-04-15
Thanks for the ideas, aysiu.  I'll have to think about them some more before I can decide on anything.

To clarify, what I am trying to do is to compare the distributions themselves independent of the support/community that they receive (to the extent that it is even possible to do so).

The question that I wanted to ask is if the most popular distributions are in any way "better" than the less popular ones. (i am just looking for the way to measure "better"). The theory being that, (independent of other factors), the community will come to the "right" decision.  Essentially voting with their usage.  Now I know that technically "better" isn't accurate, and that ideally, there are multiple distributions that could account for the diverse needs and desires of users.   This is the research question that I am investigating.

I should add that this is all theoretical, so budget and time aren't necessarily factors (I can consider them later if necessary).

What I was hoping for was to have a way to test each of them separately.  For instance have identical rigs, each with its own distribution, and give them some sort of stress test and counting errors/tracking them all for a set amount of time.  Unfortunately, as I am a rookie, I have no idea what sort of test I would use.

Also, if there are any problems that define a "better" vs "worse" distro for you guys, please share. (i.e. X was not compatible with Y software/hardware, or This could not handle A B or C very well, but That could...).

Thanks for taking the time to read my questions, and I welcome any input I can get.

Chris

---

### Post by smartboyathome on 2008-04-15
I would say stick with more popular distros like Ubuntu, Fedora, or OpenSUSE (the latter most people recommend against due to the novell-microsoft deal). They are more popular because they are the best at their job, and are easier to use. Once you learn enough about Linux, try out other distros, or customize yours to your liking.

---

### Post by CAGibby on 2008-04-15
I'm sorry, I don't think I was clear enough.  I have been looking into getting my feet wet with this stuff for a little while, and that is how I found this site, but I the reason for this post was a class project. (I spend so much of my study time looking up stuff like this anyway, I thought I'd cheat on this one...)

I need to write a research proposal for a class I am taking, and I thought this would be an interesting topic.  I am far from being an expert in this area, so I am not sure how to best measure the differences.  

So, while I am still looking around for the best thing for ME, I would appreciate input on how to test them for this question.

Chris

---

### Post by tvtech on 2008-04-15
well first off there are 600+ distributions of linux by certain counts.  it's ultimately customizable.  so your going to be looking at the big distro's  

also think about the commercial versions like Xandros  and Linspire
-non free linux

ubuntu
fedora
OpenSuse
slackware
- free linux

checking each one out take into account installation stats
usage stats
program availability  i.e. native installer package availability .rpm .deb etc.
frequency of updates ubuntu has a new release every six months
how current the kernal is  "the foundation the system is built on"
what type of security problems they have and how frequently vulnerabilies are found and patched.  
those are all things to take into consideration.  

myself Ubuntu is by far the easiest to use and has the simplest package manager but overall support i.e. programmers creating native install packages for it's debian understructure is spotty at best.

---

### Post by LaRoza on 2008-04-15
It will be hard to compare bugs.

Perhaps you can go by kernel's, instead of distros.

---

### Post by saulgoode on 2008-04-15
Rather than make it a competition, why not keep it as a comparison? Try to objectively examine the focus and strengths of the various distros -- any determination of what is "better" is invariably subjective. 

Is a simplified, intuitive installation more important than being able to deploy a common configuration across multiple workstations? Is having rock solid stability more important than having the latest available features? Is great support focused on a single platform better than broad support for multiple deployments? Is having shining puppy graphics more important than ready access to features? Is having great technical documentation more important than easy-to-follow howtos?

It is all dependent upon the wants of the user. A particular distro is not necessarily better than another, it depends upon the criteria the user weighs in his decision.

---

### Post by gn2 on 2008-04-15
What you are asking is impossible to answer

Which is better, Apples or Oranges?

It's all about taste and suitability.

Not all distros will work with all hardware.

In my case with a laptop that is eight years old I have very exacting requirements.

Almost all distros are totally useless because they won't even install.

On my desktop PC, not all distros will recognise the network adapter.

A distro that is no use to me will be perfect for someone else so at the same time any distro can be both excellent and utterly useless.

You can't make apple pie with oranges and you can't make marmalade with apples.
You just need to find the right distro for the user's needs.

---

### Post by CAGibby on 2008-04-15
Thanks, that is exactly the kind of stuff I was looking for.  

Just a few clarifications:

I was thinking about doing the top 5 or 10 free distributions. I found this article : [http://www.desktoplinux.com/news/NS8454912761.html](http://www.desktoplinux.com/news/NS8454912761.html) and I was thinking of using the list as a starting point. 

Also, perhaps competition is not the best way to look at it.  What I was really hoping for was to have multiple things to look at, and average them in to give each one an overall score.  This would give a better picture of each one, and would attempt to cover the competing priorities problems.  

So, given the compatibility issues, do you guys think that a decent measure of overall effectiveness would be to have an array of hardware and see how many issues come up?  Are these problems common enough for this to be useful?

Thanks for everything so far, this has been very informative.  And I am certainly open to more suggestions.

—Chris

---

### Post by cardinals_fan on 2008-04-16
It's very important to consider the audience of each distro.  Slackware's installer isn't as easy for a beginner as Ubuntu's is, but brand new users aren't Slackware's target audience.  If you give each distro a 'score' what would you do in this case?  Mark down Slack for not having a hand-holding gui installer?

I think the best option is to do individual, IN-DEPTH reviews of each distro.  In other words, spend a week *exclusively* on each chosen distro.  Point out the facts about the distro, and let people make up their own minds.  This way isn't easy, but you can't truly understand a distro with a couple hours experience.

---

### Post by koenn on 2008-04-16
As others pointed out, you can't decide which distro is best untill you've defined "best", and that will always be subjective or depending on the target group you have inn mind.

I suppose you could compare distros on objective criteria such as
-how long does it take too install it ?
-what do you get as a result when accepting all defaults during install ?
-how many decisions do you have to take during an install ?
-how fast does it boot ?
-how much disk space those a default install take ?
- what are the minimum/recommended system requirements ?
. ...

of course, you'll also have to weigh those : the time it takes to install a system is of minor importance cause ideally you only do it once. (excpt for Ubuntu ; every 6 months  :) , or if you're planning a roll-out of 1000 desktops )

I can imagine you could also get a test group of people without Linux experience, give them a default install of the most popular distros, and see how long it takes / how much trouble they have to perform a given set of tasks (find something in google, send an email, get a chat session going, play music, create a  spreadsheet and save it, ...)
just how you set up a test like that and e.g how you avoid that the experience the testers gain during the first tests improves their results on distros later in the test is, of course,  your problem  :)

---

### Post by kvk on 2008-04-16
I think it depends on the parameters that you are comparing. Are you looking at ease of use for the general, non-tech user? Ease of initial set-up? Number of software applications that will run on a given distro? Or are you looking at the ways in which each distro affects processor threads and the time necessary to run given benchmark tests? Some of that gets into hardware, of course, and isn't your focus.

---

### Post by Trail on 2008-04-16
> **gn2 said:**
> Which is better, Apples or Oranges?

Oranges of course. Apples and Windows are annoying.

---

### Post by gn2 on 2008-04-16
> **Trail said:**
> Oranges of course. Apples and Windows are annoying.

You've fallen for the obvious mistake, the correct answer is melons.

---

### Post by gn2 on 2008-04-16
> **CAGibby said:**
> have an array of hardware and see how many issues come up?  Are these problems common enough for this to be useful?

Perhaps if you did that you would just find out which of the selected hardware was more suited to Linux rather than which distro is "better"

What you are trying to do is really difficult because as the old saying goes, you can't please all the people all the time.

---

### Post by CAGibby on 2008-04-16
Hmm.  Thanks for the assistance.

After some thought, I think I want focus on brand new users, as that will make things easier.

And Koenn, I like the suggestions, and I will be thinking about using some or all of them.

Right now, I am thinking of a combination of amount of a few of the objective criteria (boot time, size requirements, etc.) and I also like the idea of timing the new users as well.  I would like to keep the subjectivity to a minimum, and I think time is a pretty effective measure (all thinks considered...) 

Hmmm.  That's a lot to consider.  Thanks!

And of course if anyone else can shed some light, I'm still open.

I can't say thanks enough, I appreciate the input from all of you guys.

---

