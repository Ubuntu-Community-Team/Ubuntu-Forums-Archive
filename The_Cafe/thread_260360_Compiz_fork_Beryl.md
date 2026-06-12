---
title: "Compiz fork: Beryl"
date: 2006-09-18
forum: The Cafe
---

### Post by hanzomon4 on 2006-09-18
This excerpt from [compiz.net]("http://www.compiz.net/topic-4591-beryl-informations-announcement") kinda explains everything....

[quote=iXce]Greetings everyone!

Beryl has been announced earlier than planned, and nothing clear and complete has been published, to explain the reasons and the goals of the fork. I'll do my best to perform that.

First and foremost, let's enlighten the reasons of the fork.

Compiz went out in the early weeks of this year, and immediately interested some third-party developers, willing to improve it, by adding their own features and plugins. Quickly the interest grew and the newly founded branch, compiz-quinnstorm, began to become really different from official compiz. During this summer, and during the last few weeks, some major additions were done in compiz-quinnstorm, bringing a whole new decorator, cgwd, which was designed to be fully themable, and a new settings backend, csm, which intended to drop most of the gnome deps - there were other reasons for this, but this is not our current subject. Consequently, we reached a situation where it's quite impossible to come back.

Lots of people suggested to send our patches to the mailing list. Well, first it'd be quite impossible to send all the changes upstream, since some of them are really deep (csm), or are related to a lot of code/plugins (xinerama). Furthermore, it's really unsure that David would happily accept these patchs. I'm even nearly sure that most of them would be rejected. Check the Xinerama issue ; David is willing to implement his own stuff. He added a kind of Xinerama support inside Xgl, which does not look to be compliant with the one that is currently inside Xorg. And don't even think about csm/gconf problem, I fear Novell won't ever accept to drop gconf.

Then, the communication problem. As you may have noticed, the mailing list is not very busy, David has never really published what he was intending to do and implement on a long term plan. No official roadmap, no official goals. Has anyone ever seen David posting on the forums, or on IRC? Never. He maybe does not like forums or IRC, but, well, we all here do, and it sounds to be a sufficiant reason to say that our views about communication are different. Forking gives us the opportunity to introduce our own roadmap, our own goals, our own release cycle...

Last but not least, the problem of distro integration. The current compiz package in Ubuntu Universe (on Edgy) is a compiz-quinnstorm, and that created a debate because some people thought that the official compiz should be in there, since it is official and appeared to be more stable. About debian, similar problems prevent it's inclusion. It appeared that the only solution to get our branch inside distributions was to really fork, so that official compiz and the community tree would be considered as two different projects.


Now that you all know why this happened, let's highlight what we are going to do.

We've been doing pretty bad in terms of organisation until now. To be realistic, we may even say that it was a real mess. Now that we have our own project, we'll be able to set our "rules". Coding style, goals, roadmap, release cycle, all that will be clearly defined. We mainly plan to have two branches, a stable one, that would only be affected by critical bug fixes, and an unstable one, with new features bug, obviously, bugs that would have not yet been catched.

Bug fixing is now a priority, since we'll have to produce "stable" releases, and not only "bleeding edge" releases, that often looks really unpolished, as we used to do.

Documentation will also be one of our main goals. We'll definitely try to build a solid developer documentation, and to comment the code as much as possible. In addition, we'll also try to get some complete howto's, as simple as possible and covering as much distributions as possible.

Feature addition will obviously be done as well, we'll try to do our best with that, listening to the community - you. Just publish your ideas if you feel they're smart. We'll mainly focus on usability from now on, but some clever eye-candy is always welcome. We'll also try to do things smoother than before, and we'll take care that sudden changes such as the csm introduction won't happen again.

Notice that we will still keep synched with upstream as long as it'll be possible.

Just a few words about how the project will be managed. We'll try to move the patch publication to the bug tracker, so that we'll have a clean place to submit patches and keep the updates. We'll also try to move all the bug reports inside the bug tracker so that it'll be much easier to catch them. A mailing list will be open as well, with announcements, and another one for technical discussions. Forums will be used for end user communication : discussions, howtos comments, plugin development previews/discussions... Wiki will be used for documentation and howtos. Additionnaly, a blog will be set up to keep a kind of changelog that will be readable by everyone, so that there will be a place where anyone can stay aware of the changes. The main difference will be that the forums will only feature discussions, the wiki documentation, the bug tracker technical data, the blog for news, and the mailing lists more formal communication.

Finally, please note that this is a friendly fork. We don't have anything against David, and we understand that his hands may be tied due to his work at Novell. We just need more freedom. Thanks David for the wonderful job you did. We'll just try to keep the quality level you introduced.

Thank you for taking time to read this annoucement.

Long live Beryl!

Quick note : please do not ask for beryl packages or ebuilds, we're in the process of fixing many bugs and don't want to release anything broken/unstable at the moment.
Updated 09/18/06 @ 22:10[/quote]

---

### Post by .t. on 2006-09-18
Well; it's all the same to me - just under a different title, and I don't really care what it's called. Anyone know why it's now "Beryl" though?

---

### Post by Brunellus on 2006-09-18
either "Beryl the Peril" of the Beano comics, or [Beryl Burton]("http://en.wikipedia.org/wiki/Beryl_Burton")....?

---

### Post by Sammi on 2006-09-18
[http://http://en.wikipedia.org/wiki/Beryl]("http://http//en.wikipedia.org/wiki/Beryl")

---

### Post by mrgnash on 2006-09-18
As a more adventurous and community driven-project, I look forward to the results :)

---

### Post by ruffneck on 2006-09-18
I'm down with Beryl. Hope they include the 1st release in Edgy as it will replace quinn-compiz that's already in the Universe Repos. 

If they release Beryl 1.0 in time ofcourse.

---

### Post by maniacmusician on 2006-09-18
the ati proprietary drivers dont even let me enable compositing, so i can pretty much forget about compiz/Beryl/XGL. maybe AIGLX will provide me some hope.

---

### Post by TravisNewman on 2006-09-18
> **maniacmusician said:**
> the ati proprietary drivers dont even let me enable compositing, so i can pretty much forget about compiz/Beryl/XGL. maybe AIGLX will provide me some hope.
XGL works fine with ATI prop drivers. AIGLX has troubles with them, and AIGLX totally balks on nvidia cards (until a few months, hopefully), but ATI and XGL work great together.

---

### Post by K.Mandla on 2006-09-18
I was wondering if something like this might happen. Sounds great. I'd love to see something free of the underlying Gnome structure.

---

### Post by maniacmusician on 2006-09-19
> **panickedthumb said:**
> XGL works fine with ATI prop drivers. AIGLX has troubles with them, and AIGLX totally balks on nvidia cards (until a few months, hopefully), but ATI and XGL work great together.
but if the prop drivers don't even let me enable compositing (which is so basic, comparatively), how can I hope to run XGL?

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> the ati proprietary drivers dont even let me enable compositing, so i can pretty much forget about compiz/Beryl/XGL. maybe AIGLX will provide me some hope.

Use the Edgy repos to upgrade your X right on the day of a beta release and you'll be able to run it just fine.

Today, i'm playing with vista aero, compared to AIGLX+compiz, aero is nothing, especially with cgwd, you really should try it. ;)

---

### Post by maniacmusician on 2006-09-19
yeah, i will. I'm hesitant to do an edgy upgrade now or before it gets stable. this is  my main machine, I really really don't want to risk getting my system somehow hosed. 

I'll test it on my school computer, of course though. I'm advocating linux there too...everyone in my comp-tech classes have loved the KDE (Kubuntu) installation i've set up there. People from other tech classes are even starting to use the "linux machine".

---

### Post by SoundMachine on 2006-09-19
> **maniacmusician said:**
> yeah, i will. I'm hesitant to do an edgy upgrade now or before it gets stable. this is  my main machine, I really really don't want to risk getting my system somehow hosed. 

I'll test it on my school computer, of course though. I'm advocating linux there too...everyone in my comp-tech classes have loved the KDE (Kubuntu) installation i've set up there. People from other tech classes are even starting to use the "linux machine".

Just do the X upgrade and you'll be fine, open synaptic, add the repo, mark the upgrades and if you run into problems, you can always downgrade.

Kubuntu really does rock. :cool:

---

### Post by maniacmusician on 2006-09-19
mm i'll try it when it goes into it's next version. whatever's after knot2. 

I installed knot2 (xubuntu) in vmware, it seemed decent. but you can't really get the full effect of it there. I wanted to install it on a school computer, but I wanted to show people there that linux was fully functional and awesome, and i had heard that most kde apps weren't working in edgy yet, so i held off on that lol. i might set up dual boot with edgy and dapper.

---

