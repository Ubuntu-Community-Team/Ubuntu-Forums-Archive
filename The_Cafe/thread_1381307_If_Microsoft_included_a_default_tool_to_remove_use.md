---
title: "If Microsoft included a default tool to remove user installed programs?"
date: 2010-01-14
forum: The Cafe
---

### Post by Techsnap on 2010-01-14
What would you do if Microsoft included an application by default which claims to remove "cruft" and leaves the system as clean as possible. The way it does this is search through what is installed and then decides to remove anything and everything that you've installed manually yourself? Be it Opera, Skype, Flash, Adobe Reader, anything like that. 

What is your opinion on that?
What do you think others will think?

Since a lot of people figured, I'm talking about Computer Janitor. I want to know why this application is doing what it's does when there was a bug report filed before 9.04 was released yet it still does this. They overhauled the GUI for 9.10 but they never fixed it from removing user installed software!

**Update - Why it does this**

```
class UnsupportedPackagesPlugin(computerjanitor.Plugin):

    """Plugin to find packages no longer supported by Canonical.
    
    An unsupported package is one that is no longer available in the
    archive.
    
    Unfortunately, this heuristic is unable to treat packages installed
    manually (via dpkg), or from sources (such as PPAs) that are no longer
    in sources.list.

    """
```

As we can see it cannot determine which unsupported packages need to be removed, therefore this program is incomplete and flawed and backs up why it shouldn't be included by default.

---

### Post by doas777 on 2010-01-14
my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

my thought, is that like most ms apps on my wintel boxen, I would not run such an app, and if I did, I would do it for a reason, and be careful about it.

---

### Post by Tristam Green on 2010-01-14
> **Techsnap said:**
> What would you do if Microsoft included an application by default which claims to remove "cruft" and leaves the system as clean as possible. The way it does this is search through what is installed and then decides to remove anything and everything that you've installed manually yourself? Be it Opera, Skype, Flash, Adobe Reader, anything like that. 

What is your opinion on that?
What do you think others will think?

Why am I asking? I'll follow it up in a while after I've seen some replies.

Why, I think there'd be an Interwebs something-storm.

---

### Post by NoaHall on 2010-01-14
> **doas777 said:**
> my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

my thought, is that like most ms apps on my wintel boxen, I would not run such an app, and if I did, I would do it for a reason, and be careful about it.

And what if it came with your system by default, aimed at newbies, or it was the first time you had used the Microsoft operating systems?

---

### Post by lisati on 2010-01-14
I wouldn't trust some of the offerings available to do a cleanup.

---

### Post by alphaniner on 2010-01-14
> my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

My guess is he *was* being attentive and *didn't* let janitor bork his system even though it often tries so hard to do so.

Anyway, I would poop a brick and mail it to Redmond.

---

### Post by BinarySpill on 2010-01-14
Something like that would get reported, i mean word would get around quick

---

### Post by Zoot7 on 2010-01-14
> **Techsnap said:**
> What is your opinion on that?
I would be rather alarmed and annoyed at the same time.
> **Techsnap said:**
> What do you think others will think?
I would imagine others would be aswell.

> **Techsnap said:**
> Why am I asking?
Methinks you're referring to a certain app that is installed by default on a certain OS that these forums are dedicated to. Am I right? :tongue:

---

### Post by forrestcupp on 2010-01-14
They do.  It's called Add/Remove Programs.  The only difference is that you can only remove one program at a time.

---

### Post by mamamia88 on 2010-01-14
> **forrestcupp said:**
> They do.  It's called Add/Remove Programs.  The only difference is that you can only remove one program at a time.

beat me too it and you can only remove programs not add them

---

### Post by TheNosh on 2010-01-14
> **forrestcupp said:**
> They do.  It's called Add/Remove Programs.  The only difference is that you can only remove one program at a time.

maybe you need to read the OP rather than just the title.

---

### Post by Queue29 on 2010-01-14
> **forrestcupp said:**
> They do.  It's called Add/Remove Programs.  The only difference is that you can only remove one program at a time.

Read the OP. We're not talking about tools designed to remove programs. We're talking about a tool that recommends and removes programs (or "cruft" as this particular program deliberately leads you to believe) *for you.* (And is included in the default Ubuntu install)

---

### Post by chillicampari on 2010-01-14
Add/remove programs is pretty straightforward in it's description. Now if I'm using a cleanup/optimization tool I'd only expect stuff like temp files, leftover junk and things like that removed and would be unpleasantly surprised if it removed the actual programs.

---

### Post by alexfish on 2010-01-14
Automated for you

apt-get remove allthatismicrosoft

---

### Post by Grifulkin on 2010-01-14
> **doas777 said:**
> my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

my thought, is that like most ms apps on my wintel boxen, I would not run such an app, and if I did, I would do it for a reason, and be careful about it.

I doubt techsnap borked his system, just saying.  He's a slacker I think he can use Ubuntu.

---

### Post by toupeiro on 2010-01-14
It sounds like you want self-cleaning dirt.  Have fun with that idea. :)

---

### Post by juancarlospaco on 2010-01-14
Yeah, a program that removes all user-installed software, Drivers included, 
nice...

---

### Post by Techsnap on 2010-01-15
> my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

Of course I didn't break my system, I did it intentially! Because I just want to know how an application like this managed to make its way into the default Ubuntu installation when it's evident that it is a load of old crap. I also think that if Microsoft included an application which claimed to remove "cruft" and it remove any programs you installed yourself, most people here would rip them to pieces.

---

### Post by fancypiper on 2010-01-15
I found that the add/remove software in Windows left lots of cruft laying around which was very difficult to locate and remove by hand, so I wouldn't use it, myself.

Oh, I forgot, I haven't used Windows in years!

---

### Post by Techsnap on 2010-01-15
> I found that the add/remove software in Windows left lots of cruft laying around which was very difficult to locate and remove by hand, so I wouldn't use it, myself.

That's not answering the question.

---

### Post by Grenage on 2010-01-15
> I also think that if Microsoft included an application which claimed to remove "cruft" and it remove any programs you installed yourself, most people here would rip them to pieces.

You're right; they probably would, but that doesn't make it right.

---

### Post by Techsnap on 2010-01-15
[https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/458872](https://bugs.launchpad.net/ubuntu/+source/computer-janitor/+bug/458872) There's a bug from before Ubuntu 9.04 was released.

Not only has it been ignored, it was still included in both 9.04 & 9.10. I can understand Computer Janitors point in it removing usless dependencies and fixing config files, that would be a good application for end users, if it was done properly. However in its current state there is no way this application should have been included in Ubuntu by default!

---

### Post by JBAlaska on 2010-01-15
Well, now you can make another Ubuntu bashing Video...

---

### Post by Techsnap on 2010-01-15
I still want to know why it's there though.

---

### Post by Grifulkin on 2010-01-15
> **JBAlaska said:**
> Well, now you can make another Ubuntu bashing Video...

Lolz, he had a reason to bash Ubuntu, it does pull in useless dependencies.  Well that is any Debian system really.  So... yeah.

---

### Post by dmillerct on 2010-01-15
There are lots of programs out there for windows that claim to do this already.

You have to give this one points for the name they chose:

[http://www.pcdecrapifier.com/]("http://www.pcdecrapifier.com/")

---

### Post by Techsnap on 2010-01-15
That program is third party and it's also not included with Windows by default.

---

### Post by forrestcupp on 2010-01-15
> **TheNosh said:**
> maybe you need to read the OP rather than just the title.

> **Queue29 said:**
> Read the OP. We're not talking about tools designed to remove programs. We're talking about a tool that recommends and removes programs (or "cruft" as this particular program deliberately leads you to believe) *for you.* (And is included in the default Ubuntu install)

Read my post.  I did read the OP.  That's why I said what the difference is.  I just thought it was inevitable that someone would say that, so I might as well be the one. ;)

And there are 3rd party apps that do exactly what the OP wants.  It's not really in MS's interest to have that built in.

---

### Post by John Bean on 2010-01-15
> **Techsnap said:**
> I still want to know why it's there though.

No you don't. Be honest; you just want to stir up a bit of fun for the popcorn eaters as they wait for the expected outraged response from the Ubuntu fanboys :-)

To be fair I don't know why it's there either... but since I don't use it (along with a lot of the other stuff in the default install) I don't agonise over it. I just use what I want and don't use what I don't.  Maybe I'll remove it when I get a round tuit... or maybe not. Who cares?

---

### Post by Techsnap on 2010-01-15
> No you don't.

Seriously, I do want to know why it's there, why would they include something which doesn't work properly, it just doesn't make sense, there no reasonable explanation as of yet.

---

### Post by Frak on 2010-01-15
Oh, do you mean Virtual Richard M. Stallman, err, Computer Janitor* ?

---

### Post by John Bean on 2010-01-15
> **Techsnap said:**
> Seriously, I do want to know why it's there, why would they include something which doesn't work properly, it just doesn't make sense, there no reasonable explanation as of yet.

That didn't stop MS forcing IE on the world... or even a whole OS like Vista for that matter.

There are lots of software included in OS distributions that doesn't work properly - for some value of "properly"; the "Janitor" is but one of them.

---

### Post by doas777 on 2010-01-15
> **Techsnap said:**
> I still want to know why it's there though.for the most part janitor is a graphical front end for ```
sudo apt-get autoremove && sudo apt-get clean
```now don't get me wrong, i'm disappointed with janitor as well, as it always offers to remove stuff i need, but at the same time, there are plenty of apps for windows that do simillar stuff. most of them are security focused and are often far more cryptic than janitor. I remember one time I spent a day and a half tracking down some odd RootKitRevealer traces, that were ultimatly just driver hiding by DaemonTools. on several occasions antivirus apps have deleted my copies of the sysinternals suite (as psexec, pskill, and pslist can be considered hacker tools/unwanted user programs). spybot and ccleaner have on occasion removed hkey entries that some of my apps needed, etc.

I am certain that MS would make such a program part of the standard install, if they used an repo system like apt.

finally, sorry if my post seemed overly harsh, but i've seen you around, and sometimes your posts seem to be more snap than tech.

---

### Post by NoaHall on 2010-01-15
> **John Bean said:**
> That didn't stop MS forcing IE on the world... or even a whole OS like Vista for that matter.

There are lots of software included in OS distributions that doesn't work properly - for some value of "properly"; the "Janitor" is but one of them.

I'm going to "lol" at this post. Vista was not forced upon ANYONE. You could choose to use it, or choose not. You don't have to use IE either. But IE won't remove the other browsers you've installed, or remove flash.

---

### Post by John Bean on 2010-01-15
> **NoaHall said:**
> I'm going to "lol" at this post. Vista was not forced upon ANYONE. You could choose to use it, or choose not. You don't have to use IE either. But IE won't remove the other browsers you've installed, or remove flash.

Neither will janitor, unless you CHOOSE to use it and CHOOSE to allow it to remove them. I certainly wouldn't use it, and I agree its default behaviour is unforgiving, but it does seem to do exactly what was intended.

Incidentally the early versions of IE silently and without permission reinstated themselves as the default browser if you installed (say) Netscape; this behaviour disappeared only when court rulings intervened. There's always been badly behaved software and probably always will. But nobody forces it - including janitor - on ANYONE ;-)

---

### Post by Icehuck on 2010-01-15
> **John Bean said:**
> Neither will janitor, unless you CHOOSE to use it and CHOOSE to allow it to remove them. I certainly wouldn't use it, and I agree its default behaviour is unforgiving, but it does seem to do exactly what was intended.

Incidentally the early versions of IE silently and without permission reinstated themselves as the default browser if you installed (say) Netscape; this behaviour disappeared only when court rulings intervened. There's always been badly behaved software and probably always will. But nobody forces it - including janitor - on ANYONE ;-)

Why are you defending something that's obviously broken? You're whole argument comes down to, "so what, you don't have to use it."

---

### Post by Techsnap on 2010-01-15
> That didn't stop MS forcing IE on the world... or even a whole OS like Vista for that matter.

Guess what, I don't care, that's not the topic of this thread, at least IE doesn't remove your software.

> Neither will janitor, unless you CHOOSE to use it and CHOOSE to allow it to remove them. I certainly wouldn't use it, and I agree its default behaviour is unforgiving, but it does seem to do exactly what was intended.

Nowhere in the documentation does it say it's going to remove all third party packages.

> and I agree its default behaviour is unforgiving

Yet again, I ask, Why is it included then?

---

### Post by doas777 on 2010-01-15
> **Icehuck said:**
> Why are you defending something that's obviously broken? You're whole argument comes down to, "so what, you don't have to use it."
because thats what you do when someone willfully misuses a program and then posts a rant complaining about it. 

software should do exactly what you tell it to do. if it does, then it works, and any problems are pebcak. if it doesn't, then you have a bug.

---

### Post by doas777 on 2010-01-15
> **Techsnap said:**
> 
Yet again, I ask, Why is it included then?
and yet again we state that it is a graphical frontend for apt clean and autoremove.

---

### Post by Icehuck on 2010-01-15
> **doas777 said:**
> because thats what you do when someone willfully misuses a program and then posts a rant complaining about it. 

software should do exactly what you tell it to do. if it does, then it works, and any problems are pebcak. if it doesn't, then you have a bug.

Willfully misuses a program? Install a packages not form the repositories, and computer janitor want's to remove it. How is that misusing the program? Why is this even included?

---

### Post by Tristam Green on 2010-01-15
> **doas777 said:**
> and yet again we state that it is a graphical frontend for apt clean and autoremove.

autoremove removes uninstalled, unused packages.  it does not remove live programs.

---

### Post by doas777 on 2010-01-15
> **Icehuck said:**
> Willfully misuses a program? Install a packages not form the repositories, and computer janitor want's to remove it. How is that misusing the program? Why is this even included?

straight from the horses mouth:
[http://ubuntuforums.org/showpost.php?p=8668163&postcount=18](http://ubuntuforums.org/showpost.php?p=8668163&postcount=18)

scroll up one post for the why

---

### Post by NoaHall on 2010-01-15
> **doas777 said:**
> because thats what you do when someone willfully misuses a program and then posts a rant complaining about it. 

software should do exactly what you tell it to do. if it does, then it works, and any problems are pebcak. if it doesn't, then you have a bug.

So you're saying, that having a application, aimed at those who don't know what they are doing, which removes applications like Flash, Opera, Skype, should be included, and if they are removed, it's the users fault for not using it right? Nice one.

---

### Post by Techsnap on 2010-01-15
> and yet again we state that it is a graphical frontend for apt clean and autoremove.

apt-get clean and apt-get autoremove DO NOT REMOVE USER INSTALLED PROGRAMS!

---

### Post by doas777 on 2010-01-15
> **Tristam Green said:**
> autoremove removes uninstalled, unused packages.  it does not remove live programs.

your right, one of the other things janitor does, is to query dpkg to look for deb installed packages, that are not associated with a repo. that is a secondary design goal.

---

### Post by doas777 on 2010-01-15
> **NoaHall said:**
> So you're saying, that having a application, aimed at those who don't know what they are doing, which removes applications like Flash, Opera, Skype, should be included, and if they are removed, it's the users fault for not using it right? Nice one.

your making a lot of assumptions. what about gparted? should it not be included because it could break a system if someone uses it wrong? read post 18. the op specifically did it anyway despite knowing that he would not desire the output/

---

### Post by NoaHall on 2010-01-15
> **doas777 said:**
> your making a lot of assumptions. what about gparted? should it not be included because it could break a system if someone uses it wrong? read post 18. the op specifically did it anyway despite knowing that he would not desire the output/

So you're saying it's fine that this software removes used software, despite being there claiming to remove and tidy old software?

---

### Post by Techsnap on 2010-01-15
gparted is only on the livecd, it's not misguiding either.

---

### Post by Tristam Green on 2010-01-15
> **doas777 said:**
> your right, one of the other things janitor does, is to query dpkg to look for deb installed packages, that are not associated with a repo. that is a secondary design goal.

querying them is fine.  uninstalling them is not.

---

### Post by sydbat on 2010-01-15
> **Techsnap said:**
> gparted is only on the livecd, it's not misguiding either.Um...no. While it is not installed by default, it is easy enough to do so via Synaptic.

---

### Post by Icehuck on 2010-01-15
> **sydbat said:**
> Um...no. While it is not installed by default, it is easy enough to do so via Synaptic.

I thought they were arguing about the default installed packages?

---

### Post by Techsnap on 2010-01-15
Well then you're knowingly installing it, it's not part of the default install set then, like computer janitor is.

---

### Post by doas777 on 2010-01-15
> **NoaHall said:**
> So you're saying it's fine that this software removes used software, despite being there claiming to remove and tidy old software?

thats not what it says for me:

> 
Package will be **removed**
Package is no longer supported: it is no longer in the package archive. (it may also have been installed from an unofficial archive that it no longer available. in that case you may want to keep it.)


says it loud and clear. besides that is one of the things that autoremove does. it looks for packages that are no longer in the repos, and then looks for updates to them, and checks for depends and recomends. if there are none, it asks if it can remove that package.

---

### Post by sydbat on 2010-01-15
> **Icehuck said:**
> I thought they were arguing about the default installed packages?Ahhh...my bad...

---

### Post by Eisenwinter on 2010-01-15
> **sydbat said:**
> Um...no. While it is not installed by default, it is easy enough to do so via Synaptic.
That still isn't installed by default.

As far as Janitor goes, I can't really say anything, since I haven't used it.

I have heard various complaints (not just from this thread) about it, though.

---

### Post by Techsnap on 2010-01-15
Yes I know it says that, but what I'm saying is, why is it a default application for a distro which claims to be newbie friendly, if people need that functionality then they'll install computer janitor manually.

---

### Post by Eisenwinter on 2010-01-15
Obviously, to get an absolutely accurate answer, you'll have to ask the Ubuntu developers why they chose to include it.

I don't think we can get a real answer for "Why?", on this forum, since none of these people chose to include it in their default install.

---

### Post by fewt on 2010-01-15
> **doas777 said:**
> because thats what you do when someone willfully misuses a program and then posts a rant complaining about it. 

software should do exactly what you tell it to do. if it does, then it works, and any problems are pebcak. if it doesn't, then you have a bug.

You mean the program that is currently offering to remove two software packages that I developed (which are both packaged as debs by the way), playonlinux, virtualbox, and getdeb-repository?

I can see how just running an app that offers to uninstall my software for me is misusing it (not).

An application should not offer to break your system.  First, they are packaged as signed debs so they shouldn't be suspect.  Second, even if they were, they should be unchecked.

If it looked in /opt or in /usr/local and determined that I had orphaned software without being linked to a package, yes please offer to remove it.

If it looked in ~ and found files I hadn't used in 6 mos, let me know.

No DO NOT offer to remove my software.

It's not that difficult to figure out.

Computer Janitor is broken.

---

### Post by fewt on 2010-01-15
> **doas777 said:**
> straight from the horses mouth:
[http://ubuntuforums.org/showpost.php?p=8668163&postcount=18](http://ubuntuforums.org/showpost.php?p=8668163&postcount=18)

scroll up one post for the why


sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

'nuff said.

---

### Post by NoaHall on 2010-01-15
Newbie: "OMG THIS OS IS SO COOL!"
Newbie: "I wonder if there's a application like ccleaner for it"
Newbie: "Hm... Computer Janitor, that sounds good!"
Newbie: "Remove old versions of applications which aren't supported? Sure!"
Newbie: "OMG!!! WHERE HAS MY APPLICATIONS GONE??? THIS SUCKS, I'M GOING BACK TO WINDOWS!"
doas777: "It's your fault. You can't even use software properly"

---

### Post by fewt on 2010-01-15
> **doas777 said:**
> your right, one of the other things janitor does, is to query dpkg to look for deb installed packages, that are not associated with a repo. that is a secondary design goal.

Complete and utter crap.  Most users have at least 1 package not associated with a repo.

---

### Post by Eisenwinter on 2010-01-15
> **NoaHall said:**
> Newbie: "OMG THIS OS IS SO COOL!"
Newbie: "I wonder if there's a application like ccleaner for it"
Newbie: "Hm... Computer Janitor, that sounds good!"
Newbie: "Remove old versions of applications which aren't supported? Sure!"
Newbie: "OMG!!! WHERE HAS MY APPLICATIONS GONE??? THIS SUCKS, I'M GOING BACK TO WINDOWS!"
doas777: "It's your fault. You can't even use software properly"
LOL.

I really laughed out loud reading that, awesome.

---

### Post by Techsnap on 2010-01-15
NoaHall, you're exactly right.

---

### Post by doas777 on 2010-01-15
there is a big differance between a newbie asking for help, and a guy posting a rant masqurading as a question.

---

### Post by Techsnap on 2010-01-15
Because most people would not approve of it that's why!

---

### Post by NoaHall on 2010-01-15
> **doas777 said:**
> there is a big differance between a newbie asking for help, and a guy posting a rant masqurading as a question.

So you're saying that people shouldn't care that there's harmful software included in the default install aimed at newbies? And if the point is raised, it should only be done by someone who has completely ruined their system?

---

### Post by doas777 on 2010-01-15
> **NoaHall said:**
> So you're saying that people shouldn't care that there's harmful software included in the default install aimed at newbies?

look at the subject line to the thread. does that seem snarky or constructive?

that said, i never use janitor, for exactly the reasons claimed here. I don't like it, and no I would not have put it in there. 

but i would not start a thread invoking the name of the evil one, just to get folks attention. I would also not have tried to "trick" the audience into the response i desired. that is underhanded and nonconstructive. the basis for the argument is that new users cannot be relied upon to read warning messages. that to me sounds like linsux propaganda.

---

### Post by Techsnap on 2010-01-15
> I would also not have tried to "trick" the audience into the response i desired.

There's no trick here, I want to know if people would be pissed off Microsoft included something like this.

>  i never use janitor, for exactly the reasons claimed here.

The question still continues, does anyone know what the damn purpose of it removing user installed applications are!

---

### Post by doas777 on 2010-01-15
> **Techsnap said:**
> There's no trick here

from your opening post:
> Why am I asking? I'll follow it up in a while after I've seen some replies.

clearly a debate trap. you posed a straw man (MS), and asked everyone what would be worse, all as setup to then claim that it was ubuntu.

---

### Post by Techsnap on 2010-01-15
Since most people figured, I changed the topic. Read it.

> all as setup to then claim that it was ubuntu.

Well done, have a cookie.

---

### Post by NoaHall on 2010-01-15
> **John Bean said:**
> The sole purpose of the OP appears to be a bit of harmless trolling (and to boost popcorn sales):
:-)

No, it's not trolling, it's a very, very valid point.
The fact that you are all failing to reply with a good reason why it should be included, and why it shouldn't be removed, proves that. It also goes to show that you refuse to see the bad in Ubuntu, when you would see it as "evil" and "OMG M$ DONE IT AGAIN!" if it was Microsoft.

---

### Post by Eisenwinter on 2010-01-15
> **John Bean said:**
> The sole purpose of the OP appears to be a bit of harmless trolling (and to boost popcorn sales): 

:-)
Disagreeing with you != Trolling

---

### Post by John Bean on 2010-01-15
> **NoaHall said:**
> No, it's not trolling, it's a very, very valid point.
The fact that you are all failing to reply with a good reason why it should be included, and why it shouldn't be removed, proves that.

If it walks like a duck... Whatever ;-)

---

### Post by Techsnap on 2010-01-15
Read the first post in the link you posted. It explains the whole thing. It's not trolling because it's valid, and as NoaHall has said, nobody has pointed out why it's installed by default, but people have pointed out that it shouldn't do what it does.

---

### Post by doas777 on 2010-01-15
> **Eisenwinter said:**
> Disagreeing with you != Trolling

<snip>

---

### Post by d3v1150m471c on 2010-01-15
> **doas777 said:**
> my guess is your asking because you borked your system by not being careful and attentive while using the janitor.

my thought, is that like most ms apps on my wintel boxen, I would not run such an app, and if I did, I would do it for a reason, and be careful about it.

I concur.

---

### Post by Techsnap on 2010-01-15
If I wasn't on Linsux, I'd still be posting this, because I think it's terrible what the program does. If you read the thread on Linsux, I ask the same question, why is it installed by default.

---

### Post by John Bean on 2010-01-15
> **Eisenwinter said:**
> Disagreeing with you != Trolling

I'm not at all sure there's any disagreement, certainly not about the merits or otherwise of the "janitor" - I'd certainly never use it as I said earlier.

But the discussions in another place that led to the OP here *just to see the reaction, *marks it for what it is: a bit of a harmless troll. All good fun.

---

### Post by NoaHall on 2010-01-15
> **John Bean said:**
> I'm not at all sure there's any disagreement, certainly not about the merits or otherwise of the "janitor" - I'd certainly never use it as I said earlier.

But the discussions in another place that led to the OP here *just to see the reaction, *marks it for what it is: a bit of a **harmless troll**. All good fun.

You're very judgemental, aren't you? He wasn't trolling, he was serious.

---

### Post by lisati on 2010-01-15
> **chillicampari said:**
> Add/remove programs is pretty straightforward in it's description. Now if I'm using a cleanup/optimization tool I'd only expect stuff like temp files, leftover junk and things like that removed and would be unpleasantly surprised if it removed the actual programs.

> **dmillerct said:**
> There are lots of programs out there for windows that claim to do this already.

You have to give this one points for the name they chose:

[http://www.pcdecrapifier.com/]("http://www.pcdecrapifier.com/")
Depending on what you're doing, making a "decrappifier" for Windows *can* be easy. (Hint: if you're making a program to clean out temporary files, use the %temp% environment variable to discover where you should be looking for them. Absolute path names to the %temp% folder can vary according to Windows version and logged in user.)
> **doas777 said:**
> there is a big differance between a newbie asking for help, and a guy posting a rant masqurading as a question.
I've seen statements masquerading as questions and vice versa too.... :)
> **Techsnap said:**
> 
Well done, have a cookie.
Do I need to turn off "AdBlock"?

---

### Post by fancypiper on 2010-01-15
Hmm.. I have flash, opera, a couple of compiled programs installed and my computer janitor found nothing to remove.

Is mine broken?

---

### Post by Tristam Green on 2010-01-15
before the lock, in I am.

Techsnap has a valid point about Computer Janitor.  I'll say this much about it - it's a good idea with half-done implementation.

---

### Post by NoaHall on 2010-01-15
> **fancypiper said:**
> Hmm.. I have flash, opera, a couple of compiled programs installed and my computer janitor found nothing to remove.

Is mine broken?

It depends. I think if you install using a deb, and it doesn't install a repo, then it wants to remove them.

---

### Post by doas777 on 2010-01-15
let me pose this one to you then: how would you feel about linux recording every time you used a given app, so that it can tell if it is still used regularly? windows tries to do this (right hand collumn in appwiz.cpl), but always fails. most of the programs I use daily are marked as "Used: Rarely" "Last used: 2/14/2007". 
so it both doesn;t work, and is a huge privacy vulnerability. now that would cause a ruckus...

---

### Post by doas777 on 2010-01-15
> **fancypiper said:**
> Hmm.. I have flash, opera, a couple of compiled programs installed and my computer janitor found nothing to remove.

Is mine broken?
if you installed them via the repos (ubuntu-restricted-extras for instance) then it will not show. only if you installed from a deb that does not add a repo entry to recieve updates through.

---

### Post by doas777 on 2010-01-15
> **Tristam Green said:**
> before the lock, in I am.

Techsnap has a valid point about Computer Janitor.  I'll say this much about it - it's a good idea with half-done implementation.
on that, we can agree

---

### Post by Tristam Green on 2010-01-15
> **doas777 said:**
> on that, we can agree

What, the first or the second part?

Because if you agree with the second part, you contradict everything you've been touting as great grand and wonderful thus far.

---

### Post by John Bean on 2010-01-15
> **Techsnap said:**
> Read the first post in the link you posted. It explains the whole thing. It's not trolling because it's valid, and as NoaHall has said, nobody has pointed out why it's installed by default, but people have pointed out that it shouldn't do what it does.

I read it, but straw men are appearing at every turn so let me clarify my position.

1. Your post on linsux was rather good and certainly not a troll, neither would it have been had you posted it here. But...

2. The post you actually made here was a mildly mischievous troll.

'Nuff said, by me anyhow.

---

### Post by Techsnap on 2010-01-15
> let me pose this one to you then: how would you feel about linux recording every time you used a given app, so that it can tell if it is still used regularly?

Why do people round here always have to come up with something completely different, that's not what I'm asking, this discussion is about COMPUTER JANITOR, that is a different subject.

The way round here seems to be "well Windows does worse so who cares about Computer Janitor" Well that's no way to gain marketshare is it!

---

### Post by fancypiper on 2010-01-15
IIRC, I have installed at least one .deb that isn't in the repositories. I installed the 64 bit flash with the download from the Adobe site, but it isn't marked to remove. I try to limit my software to the ones in the repositories, but there is always a couple of faves I just gotta have.

Anyhow, that was the first time I had even noticed the program.  I have always cleaned up with sudo apt-get autoremove.

I'm confused but my system is still humming.

BTW, the popularity contest is off by default, I had to enable it.

---

### Post by doas777 on 2010-01-15
> **Tristam Green said:**
> What, the first or the second part?

Because if you agree with the second part, you contradict everything you've been touting as great grand and wonderful thus far.

not really. I agree with his point, but not his methods. janitor does not work the way I would like it to, but that does not mean that it is as flawed as the op implies. in social networking you get what you give, and if you give me a rather transparent rant, as acting thinly veiled propaganda supporting an ideology that I fundementally disagree with, then yes, you will get some flak from me.

---

### Post by Techsnap on 2010-01-15
> I installed the 64 bit flash with the download from the Adobe site

Last time I installed x64 Flash there were no .deb packages available.

> janitor does not work the way I would like it to, but that does not mean that it is as flawed 

It removes all user installed applications, it's flawed, I even made a video showing it doing so.

---

### Post by thatguruguy on 2010-01-15
I use x64 Flash, and it doesn't appear in Computer Janitor.

I haven't used Windows 7, I gave up when Vista came out.  When you remove a program in Windows 7, does it completely remove it, including all changes made to the Registry?  Or do you still have to clean the Registry by hand?

---

### Post by lisati on 2010-01-15
> **thatguruguy said:**
> I use x64 Flash, and it doesn't appear in Computer Janitor.

I haven't used Windows 7, I gave up when Vista came out.  When you remove a program in Windows 7, does it completely remove it, including all changes made to the Registry?  Or do you still have to clean the Registry by hand?

Sounds like you've been around Windows a while: I noticed a similar need for manual deletion of some stuff way back with Windows 98SE....

I have no idea about Windows 7, having never used it.

---

### Post by chillicampari on 2010-01-15
> **lisati said:**
> Depending on what you're doing, making a "decrappifier" for Windows *can* be easy. (Hint: if you're making a program to clean out temporary files, use the %temp% environment variable to discover where you should be looking for them. Absolute path names to the %temp% folder can vary according to Windows version and logged in user.)

...

Thanks lisati, that's good to know! But what I was trying to say is that when I'm using a cleaner  (I don't write my own) for getting rid of odds and ends junk  I only expect it to remove the junk files, and not try to uninstall entire programs.

---

### Post by Techsnap on 2010-01-15
> i use x64 flash, and it doesn't appear in computer janitor.

thats because x64 flash isn't a .deb how many more times!

---

### Post by thatguruguy on 2010-01-15
> **Techsnap said:**
> It removes all user installed applications, it's flawed, I even made a video showing it doing so.

What do you mean, exactly, when you write, that it removes ***all*** user installed applications?  Do you mean everything that wasn't part of the initial installation?  Do you mean stuff installed by hand, or through non-ubuntu repositories?

For instance, I've installed stuff like Duke3D, which doesn't show up in Computer Janitor.  Shouldn't it?  I've added stuff from getdeb that doesn't show up in Computer Janitor.  Shouldn't all of those applications show up?

Please elucidate.

---

### Post by lisati on 2010-01-15
> **chillicampari said:**
> Thanks lisati, that's good to know! But what I was trying to say is that when I'm using a cleaner  (I don't write my own) for getting rid of odds and ends junk  I only expect it to remove the junk files, and not try to uninstall entire programs.

I wouldn't want decrappifiers to remove programs either. Maybe have them bring suspect stuff to my attention so I can decide what to do. :)

---

### Post by thatguruguy on 2010-01-15
> **Techsnap said:**
> thats because x64 flash isn't a .deb how many more times!

But, you specifically stated ***all*** user installed applications.  Did you mean ones that weren't distributed as .debs?

---

### Post by doas777 on 2010-01-15
> **lisati said:**
> I wouldn't want decrappifiers to remove programs either. Maybe have them bring suspect stuff to my attention so I can decide what to do. :)

my thoughts exactly. and suprisingly enough, even in it's broken state, janitor does exactly that. the only real problem is that it checks the box by each app by default. the issue here, though, is that you do actually have to read what the app is telling you, which seems to be the source of frustration.

---

### Post by thatguruguy on 2010-01-15
> **lisati said:**
> Sounds like you've been around Windows a while: I noticed a similar need for manual deletion of some stuff way back with Windows 98SE....

I have no idea about Windows 7, having never used it.

I've been around Windows since 3.1.

---

### Post by thatguruguy on 2010-01-15
> **doas777 said:**
> my thoughts exactly. and suprisingly enough, even in it's broken state, janitor does exactly that. the only real problem is that it checks the box by each app by default. the issue here, though, is that you do actually have to read what the app is telling you, which seems to be the source of frustration.

Agreed.  It's wrong for anyone or anything to expect you to think.

---

### Post by Techsnap on 2010-01-15
> through non-ubuntu repositories?

Yes.

> But, you specifically stated all user installed applications.

Well it's obvious it would be .debs because if you knew anything about how the OS you're using works you would have realised  that Computer Janitor is making use of APT.

> the issue here, though, is that you do actually have to read what the app is telling you, which seems to be the source of frustration.

The source of frustration is why is it detecting these apps to begin with, it doesn't make sense, why is it configured in such a way that it does this? It's not apt-get autoremove because that is not what autoremove does.

---

### Post by thatguruguy on 2010-01-15
It's not "obvious", because you specifically said "all".  I assume that people understand the definition of common words.  The word "all" is not the same as the word "some".

I installed "Smokin' Guns" from playdeb.  Shouldn't it be in Computer Janitor?

---

### Post by Shpongle on 2010-01-15
Sure Id be formatting it anyway ;-)

---

### Post by thatguruguy on 2010-01-15
By the way, do you still have to manually edit the Registry in Windows in order to completely remove applications?

---

### Post by Techsnap on 2010-01-15
> It's not "obvious", because you specifically said "all". I assume that people understand the definition of common words. The word "all" is not the same as the word "some".

Computer Janitor makes use of apt, which in turn would not count applications you've installed manually through other means if you did not use a deb or manually insert this into apts database. You never particularly install flash x64 to begin with because all you're doing is copying the plugin from one location to another thus there's no actual installation going on. 

Same thing applies if you compile something from source or run it through its own installer it will not be in the apt database thus it will not show up in Computer Janitor for removal. Happy Now?

---

### Post by thatguruguy on 2010-01-15
Also, I know for a fact that I installed blender as a .deb from blender's site.  Shouldn't it be in my Computer Janitor listing?

---

### Post by doas777 on 2010-01-15
> **Techsnap said:**
> Yes.



Well it's obvious it would be .debs because if you knew anything about how the OS you're using works you would have realised  that Computer Janitor is making use of APT.



The source of frustration is why is it detecting these apps to begin with, it doesn't make sense, why is it configured in such a way that it does this? It's not apt-get autoremove because that is not what autoremove does.

seriously, wouldn't you like to be able to get a list of all installed software, regardless of origin? i sure would.

---

### Post by NoaHall on 2010-01-15
> **thatguruguy said:**
> Also, I know for a fact that I installed blender as a .deb from blender's site.  Shouldn't it be in my Computer Janitor listing?

See in your /etc/apt/sources.list if there's a blender repo.

---

### Post by thatguruguy on 2010-01-15
> **Techsnap said:**
> Computer Janitor makes use of apt, which in turn would not count applications you've installed manually through other means if you did not use a deb or manually insert this into apts database. You never particularly install flash x64 to begin with because all you're doing is copying the plugin from one location to another thus there's no actual installation going on. 

Same thing applies if you compile something from source or run it through its own installer it will not be in the apt database thus it will not show up in Computer Janitor for removal. Happy Now?

So, Computer Janitor does not remove ***all*** user installed applications?  Now I'm confused, given how strongly you stated your position before.  Which is it?

---

### Post by Techsnap on 2010-01-15
> Also, I know for a fact that I installed blender as a .deb from blender's site. Shouldn't it be in my Computer Janitor listing?

I don't know anything about blender, does it add a repo along with the .deb installation. Also this isn't the point, still people seem to not realise I want to know why it's listing any manually installed .debs in the first place, since nobody seems to know the answer they're nitpicking and coming up with excuses.

---

### Post by thatguruguy on 2010-01-15
> **NoaHall said:**
> See in your /etc/apt/sources.list if there's a blender repo.

Nope.

---

### Post by lisati on 2010-01-15
> **thatguruguy said:**
> So, Computer Janitor does not remove ***all*** user installed applications?  Now I'm confused, given how strongly you stated your position before.  Which is it?
On the rare occasion that I've used the Janitor, it automatically selects **all** the applications it lists. I think this is what is being referred to.

---

### Post by chillicampari on 2010-01-15
> **lisati said:**
> I wouldn't want decrappifiers to remove programs either. Maybe have them bring suspect stuff to my attention so I can decide what to do. :)

Agreed! :)

Here's where it gets confusing, at least on my end. I don't actually have Computer Janitor installed so I'm going by screenshots and what I've read. But the way it's worded it looks like it's suggesting to remove the .deb packages, which to me seems like it will just clear out the original install files I downloaded and probably don't need anymore (if that makes sense), and if I go ahead I lose the actual programs.

---

### Post by Techsnap on 2010-01-15
[http://www.youtube.com/watch?v=qEP0UQAGzSM](http://www.youtube.com/watch?v=qEP0UQAGzSM) Watch the video I posted, if nothing is making sense so far perhaps this will.

---

### Post by thatguruguy on 2010-01-15
> **Techsnap said:**
> I don't know anything about blender, does it add a repo along with the .deb installation. Also this isn't the point, still people seem to realise I want to know why it's listing any manually installed .debs in the first place, since nobody seems to know the answer they're nitpicking and coming up with excuses.

I'm not making any excuses.  I'm questioning your statements.  There's a difference.  You made a pretty strong statement, and I'm trying to get you to back it up.

I understand that you feel that you have the absolute right to have everyone agree with you. You're mistaken in that belief.

---

### Post by thatguruguy on 2010-01-15
> **lisati said:**
> On the rare occasion that I've used the Janitor, it automatically selects **all** the applications it lists. I think this is what is being referred to.

Maybe that's what is being referred to, but it's not what he wrote.

---

### Post by Techsnap on 2010-01-15
I don't want anyone to agree with me, I still want to know why it does this. For goodness sake.

---

### Post by thatguruguy on 2010-01-15
Is that the real issue here?

Techsnap, would you be happier if the boxes in Computer Janitor were unchecked?

---

### Post by thatguruguy on 2010-01-15
> **Techsnap said:**
> I don't want anyone to agree with me, I still want to know why it does this. For goodness sake.

Why it does what, exactly? Remove all user installed applications?

Because, you know, it doesn't.

---

### Post by Techsnap on 2010-01-15
It removed all the .deb files I installed, watch the video. Why does it remove any .deb files, people here just don't want to admit that such a piece of **** is part of the default Ubuntu install. It should list ANY of these.

---

### Post by d3v1150m471c on 2010-01-15
Respectfully, this is absolutely ridiculous. Computer janitor **has a list of what it will remove. **Bottom line up front - If you use this application and it delete something you didn't want to delete then it's your own fault. Read, Read, and Read some more. Problems associated with this application are **user error** and not system error. If you don't like it, delete it or even more simple, just don't use it. I can understand this calibre of heat if ubuntu breaks on an update or something of the like and again, to a degree, people should be more familiar with what they are putting on their computers and what they run and do not run on their computers. Secondly, everyone on this forum uses ubuntu **on their own prerogative.  **If you have a problem with ubuntu, don't use it or find a way to fix the problem. It seems to me you simply come to this forum to put down this operating system and have absolutely nothing to offer the community. We like ubuntu, you don't. get over it.

---

### Post by lisati on 2010-01-15
I think we're at risk of getting derailed here, sidetracked by semantics. Here's the first post in this thread:

> **Techsnap said:**
> What would you do if Microsoft included an application by default which claims to remove "cruft" and leaves the system as clean as possible. The way it does this is search through what is installed and then decides to remove anything and everything that you've installed manually yourself? Be it Opera, Skype, Flash, Adobe Reader, anything like that. 

What is your opinion on that?
What do you think others will think?

Since a lot of people figured, I'm talking about Computer Janitor. I want to know why this application is doing what it's does when there was a bug report filed before 9.04 was released yet it still does this. They overhauled the GUI for 9.10 but they never fixed it from removing user installed software!

---

### Post by thatguruguy on 2010-01-15
So, would "unchecking" the boxes make you happy, techsnap?  Is that the problem?

---

### Post by Techsnap on 2010-01-15
> So, would "unchecking" the boxes make you happy, techsnap? Is that the problem?

Don't reply to this thread unless you're going to tell me what makes Computer Janitor determine which packages to remove, please! We've determined it's not apt and we've determined it's not every single .deb now, so lets find out why it's doing this and then we can probably file a bug report which will most likely be ignored. 

If you read the original article and watched the video you'd see that I pointed out that Computer Janitor does have tick boxes and does state to the user that they will be removing the applications.

---

### Post by d3v1150m471c on 2010-01-15
> **Techsnap said:**
> Don't reply to this thread unless you're going to tell me what makes Computer Janitor determine which packages to remove, please! We've determined it's not apt and we've determined it's not every single .deb now, so lets find out why it's doing this and then we can probably file a bug report which will most likely be ignored. 

If you read the original article and watched the video you'd see that I pointed out that Computer Janitor does have tick boxes and does state to the user that they will be removing the applications.

See above

---

### Post by NoaHall on 2010-01-15
> **Techsnap said:**
> Don't reply to this thread unless you're going to tell me what makes Computer Janitor determine which packages to remove, please! We've determined it's not apt and we've determined it's not every single .deb now, so lets find out why it's doing this and then we can probably file a bug report which will most likely be ignored. 

If you read the original article and watched the video you'd see that I pointed out that Computer Janitor does have tick boxes and does state to the user that they will be removing the applications.

Closed source, perhaps. Maybe vrms was the right name for it, after all.

---

### Post by thatguruguy on 2010-01-15
So, this thread isn't part of your overall rant?  You're seeking clarification about the algorithms employed by Computer Janitor to determine which applications should be considered safe to remove?

Because it doesn't seem like you're looking for answers.  It seems like part of your overall rant.

Please don't refer me to your youtube video again.  Your whiny voice makes me cringe.  SRSLY.

---

### Post by d3v1150m471c on 2010-01-15
Also, what makes you think you have any authority to tell anyone on this forum what they can and cannot respond to? Is microsoft paying you to troll? They should probably hire someone who can do the job properly.

---

### Post by Techsnap on 2010-01-15
> Your whiny voice makes me cringe. SRSLY

Haha, you'll know not to watch them again then.

---

### Post by thatguruguy on 2010-01-15
Now we agree!

EDIT: Although if you hire spokesmodels to read the text, I will reconsider.

---

### Post by d3v1150m471c on 2010-01-15
I thought they were a good laugh.

---

### Post by chillicampari on 2010-01-15
> **Techsnap said:**
> [http://www.youtube.com/watch?v=qEP0UQAGzSM](http://www.youtube.com/watch?v=qEP0UQAGzSM) Watch the video I posted, if nothing is making sense so far perhaps this will.

Thanks! At 4:26-4:40 you demonstrate one of the things I would be confused about (in post #115) if I were to use this. Now I would probably look more (and ask about it in the forums), but to me it really implies it's going to simply clean up junk left over from the install/temp files.

---

### Post by Techsnap on 2010-01-15
```
class UnsupportedPackagesPlugin(computerjanitor.Plugin):

    """Plugin to find packages no longer supported by Canonical.
    
    An unsupported package is one that is no longer available in the
    archive.
    
    Unfortunately, this heuristic is unable to treat packages installed
    manually (via dpkg), or from sources (such as PPAs) that are no longer
    in sources.list.

    """
```

So I looked at the source code and from the source code we can see that it will remove any "unsupported" packages from the system. So it's just backing it up when I say it's flawed, look at the code. This application is fine to be in the repos but it should definitely not be installed by default.

---

### Post by Regenweald on 2010-01-15
I have to agree with the op on this one from personal experience. The first time I used computer-janitor early last year, it removed quite a few thing it shouldn't have. Largely due to the fact that it's functions were poorly documented.

If you name something "janitor" I'm going to assume "clean-up" and since the description said clean up and optimize, when I saw my third party apps listed, I incorrectly assumed that it was going to clean my package cache and not remove my programs, Logically, because I already had Add-Remove and Synaptic to do that. We now also have the Software-Centre, so why have yet another app removing apps I installed in one fatal swoop ?

The janitor was poorly designed and implemented, If it's behavior is still as I described, I'm even more surprised.

---

### Post by Techsnap on 2010-01-15
For now it shouldn't remove any packages which are marked unsupported (as we can see from the source it's going to remove a lot of software that users manually install), I can understand a program like this being in Debian Sid or Fedora RawHide not a stable release that end users are supposed to use. It's been like this since 9.04 and has not been changed.

---

### Post by d3v1150m471c on 2010-01-15
Again, it tells you what it does so don't use it. Why is that an incredibly difficult task? Hell man, you might as well complain about it installing minesweeper, too. I'm super serial! 

**EXCELSIOOORRRRR!**

---

### Post by d3v1150m471c on 2010-01-15
lol sorry... been watching a little too much al gore on south park ;)

---

### Post by 23meg on 2010-01-15
Originally, Computer Janitor determined whether a package was "cruft" or not by looking at whether it's available in the APT repositories enabled on the system, since there was really no better heuristic. Later, it was modified to take into account the "automatically removable" status too, at the cost of not removing some actual "cruft", that is, packages that actually get obsoleted from one Ubuntu release to the next, in an effort to reduce false positives.

---

### Post by Techsnap on 2010-01-15
> Again, it tells you what it does so don't use it. 

As we can see from the source code, it's far from complete. So why is it installed by default with a misleading name?

---

### Post by d3v1150m471c on 2010-01-15
sweet, a team member :D. I've been expecting this on this thread for a while now.

---

### Post by d3v1150m471c on 2010-01-15
> **Techsnap said:**
> As we can see from the source code, it's far from complete. So why is it installed by default with a misleading name?

I'm failing to see what's so misleading about it. Computer Janitor...Hmm...probably removes unnecessary things on my computer. Infact, the first time i used ubuntu i opened it to see what it was like and immediately noticed this : "hey, this will remove something i don't want it to...hmm guess i won't use it." 

Incredibly difficult, i know.

---

### Post by Techsnap on 2010-01-15
A lot of new users are not going to know what is supposed to and not supposed to be removed.

---

### Post by d3v1150m471c on 2010-01-15
Can they not read the language they installed ubuntu with? Let's take a pole

---

### Post by fewt on 2010-01-15
> **d3v1150m471c said:**
> I'm failing to see what's so misleading about it. Computer Janitor...Hmm...probably removes unnecessary things on my computer. Infact, the first time i used ubuntu i opened it to see what it was like and immediately noticed this : "hey, this will remove something i don't want it to...hmm guess i won't use it." 

Incredibly difficult, i know.

Please stop arguing as if you are an authority.  "Don't use it" is not the right answer to an application that will break computers.

On mine it is asking to uninstall virtualbox, Eee PC Utilities, and lots of other things that will break my PC.  Unsuspecting new users may not know this and execute it.

It's malicious, even if only so through ignorance of it's function.

---

### Post by NoaHall on 2010-01-15
> **d3v1150m471c said:**
> Can they not read the language they installed ubuntu with? Let's take a pole

Right, okay, as you obviously haven't read all the thread, I will say this again.

Newbie: "OMG THIS OS IS SO COOL!"
Newbie: "I wonder if there's a application like ccleaner for it"
Newbie: "Hm... Computer Janitor, that sounds good!"
Newbie: "Remove old versions of applications which aren't supported? Sure!"
Newbie: "OMG!!! WHERE HAS MY APPLICATIONS GONE??? THIS SUCKS, I'M GOING BACK TO WINDOWS!"
d3v1150m471c:"It's your fault, you couldn't properly read the language you installed with"

---

### Post by fewt on 2010-01-15
> **d3v1150m471c said:**
> Can they not read the language they installed ubuntu with? Let's take a pole

Poll, not pole.

---

### Post by d3v1150m471c on 2010-01-15
Quid pro quo : maybe you who has the tag "developer" as his/her signature should make sure this thread isn't about bashing this operating system. Especially something you're claiming to develop. I take pride in this operating system, it's developers, and this community. I can respect you want me to word things differently, but please take into consideration the intent of this thread because i personally think it's maliciously intended.

---

### Post by d3v1150m471c on 2010-01-15
> **fewt said:**
> Poll, not pole.

ty

---

### Post by fewt on 2010-01-15
> **d3v1150m471c said:**
> Quid pro quo : maybe you who has the tag "developer" as his/her signature should make sure this thread isn't about bashing this operating system. Especially something you're claiming to develop. I take pride in this operating system, it's developers, and this community. I can respect you want me to word things differently, but please take into consideration the intent of this thread because i personally think it's maliciously intended.

Why, you are and others are the ones that are wrong here.  I don't work on "Ubuntu", and I agree that Computer Janitor should be pulled.

:KS

---

### Post by Techsnap on 2010-01-15
> should make sure this thread isn't about bashing this operating system.

The OS includes a broken application by default which even documents this fact in the sourcecode, perhaps we should all just be happy with that fact :)

---

### Post by lisati on 2010-01-15
> **fewt said:**
> Poll, not pole.
Random musing: It's sometimes tempting to get a pole out and wave it around wildly when things get heated (not saying that we need to here) :)

---

### Post by sliketymo on 2010-01-15
It would not be any worse than MS installing something without your knowledge,ie dotnet plugin on Firefox.In any case,I would still use Revo un-installer,and Ccleaner,and as is always the case when cleaning a system,look before you leap.

---

### Post by d3v1150m471c on 2010-01-15
> **NoaHall said:**
> Right, okay, as you obviously haven't read all the thread, I will say this again.

Newbie: "OMG THIS OS IS SO COOL!"
Newbie: "I wonder if there's a application like ccleaner for it"
Newbie: "Hm... Computer Janitor, that sounds good!"
Newbie: "Remove old versions of applications which aren't supported? Sure!"
Newbie: "OMG!!! WHERE HAS MY APPLICATIONS GONE??? THIS SUCKS, I'M GOING BACK TO WINDOWS!"
d3v1150m471c:"It's your fault, you couldn't properly read the language you installed with"

You're right. It needs a surgeon general's warning.

---

### Post by Frak on 2010-01-15
> **d3v1150m471c said:**
> Again, it tells you what it does so don't use it. Why is that an incredibly difficult task? Hell man, you might as well complain about it installing minesweeper, too. I'm super serial! 

**EXCELSIOOORRRRR!**
Correct answer to another argument. The argument is "Why is it included by default". If it is a maintainance program, like it is advertised, why does it just remove applications that Canonical doesn't approve of? Why do they include that? "This application removes applications we believe are not ours." It leads people to think they have to run it like a maintaince program, which it is, and then it removes custom packages they installed. Why include it at all?

---

### Post by d3v1150m471c on 2010-01-15
It tells you what it's uninstalling. Again, i honestly don't see the issue with this.

---

### Post by fewt on 2010-01-15
> **d3v1150m471c said:**
> It tells you what it's uninstalling. Again, i honestly don't see the issue with this.

OK then, thanks for the input. :D

---

### Post by Techsnap on 2010-01-15
>  Again, i honestly don't see the issue with this.

It has a restrictive nature, even if it is due to a technical limitation commented in the source then it shouldn't have been installed by default. As me and many others have said on first glance people are going to think of it as a junk cleaner removing old and unsupported packages, newer users may not know that what it's listing is actually the latest version of the app which they have installed, they're going to assume that it's an old version because that is what it's telling them. 

For this very reason, it shouldn't be included by default, if someone wants it, let them install it manually from the repos.

---

### Post by NoaHall on 2010-01-15
> **d3v1150m471c said:**
> It tells you what it's uninstalling. Again, i honestly don't see the issue with this.

Then I'm very glad you aren't a admin for a computer network. Or a computer, from the sounds of it, for that matter.

---

### Post by d3v1150m471c on 2010-01-15
Now that I can agree with. It's not a necessary program and if people want it then let them add it themselves.

---

### Post by d3v1150m471c on 2010-01-15
I have some stuff to take care of. You guys take care. BBL :D

---

### Post by Frak on 2010-01-15
> **d3v1150m471c said:**
> I have some stuff to take care of. You guys take care. BBL :D
*ehem*

WHY DID YOU POST THAT. Note the non ! ending.

---

### Post by Techsnap on 2010-01-15
> Now that I can agree with. It's not a necessary program and if people want it then let them add it themselves.

Which me and others have posted loads of times.

---

### Post by lisati on 2010-01-15
> **d3v1150m471c said:**
> I have some stuff to take care of. You guys take care. BBL :D

Cool story, dude!

---

### Post by NoaHall on 2010-01-15
> **d3v1150m471c said:**
> Now that I can agree with. It's not a necessary program and if people want it then let them add it themselves.

17 pages on, he finally gets it.
I personally think he was aggravating so that this thread would be closed.

---

### Post by cariboo on 2010-01-15
Synaptic doest the same thing, it marks debs installed from other sources, as being locally installed or obsolete. The only difference is that they are not marked for removal by default.

I think the devs are giving the new user the benefit of the doubt, they assume that the user knows what they have installed, and if there is something on the list they want to keep, they (the user) will remove the check mark, and remove whatever is still marked.

---

### Post by chillicampari on 2010-01-15
@cariboo907, it makes sense it would mark those packages in Synaptic because it's in the context of package management, but if I'm in Computer Janitor, what I would expect (by the way it presents itself) is to be working with junk files only.

---

### Post by Frak on 2010-01-15
> **chillicampari said:**
> @cariboo907, it makes sense it would mark those packages in Synaptic because it's in the context of package management, but if I'm in Computer Janitor, what I would expect (by the way it presents itself) is to be working with junk files only.
I agree, make it useful. Make it show log files, or cached crap, not some package it thinks I shouldn't have.

---

### Post by cariboo on 2010-01-15
> **chillicampari said:**
> @cariboo907, it makes sense it would mark those packages in Synaptic because it's in the context of package management, but if I'm in Computer Janitor, what I would expect (by the way it presents itself) is to be working with junk files only.

I guess someone would have to define junk first. From the Help-->about screen:

> This application helps you find and remove software packages you might not need anymore. It also suggests configuration changes that might benefit you.

I don't see anywhere in there where it says it cleans up junk files.

See screenshot:

---

### Post by Frak on 2010-01-15
> **cariboo907 said:**
> I guess someone would have to define junk first. From the Help-->about screen:



I don't see anywhere in there where it says it cleans up junk files.

See screenshot:
Com-pu-ter
Computer

Jan-i-tor
Person that cleans up messes before, during, or after a facility has been used. This involves cleaning up messes, collections, and hazards in the facility.

---

### Post by chillicampari on 2010-01-15
I give up.

---

### Post by JBAlaska on 2010-01-16
I think some of you fail to see the point of the OP, I mentioned it in my post #23

> **Techsnap said:**
> [http://www.youtube.com/watch?v=qEP0UQAGzSM](http://www.youtube.com/watch?v=qEP0UQAGzSM) [COLOR="Red"]Watch the video I posted[/COLOR], if nothing is making sense so far perhaps this will.

And there you have it...:P

---

### Post by Techsnap on 2010-01-16
If you bothered to read through the rest of the thread you'd see that I looked at the source code and then found out why it was doing this and it just further backed up what a ridiculous decision it was to include by default. Although you're labeling this as rant which it is because it shouldn't be included by default you've been given more than enough proof to why. 

Check out some of the other rants on Youtube, where nobody posts facts they just make stuff up from not knowing what they're doing. As you can see from this thread we've found the reason why and it seems that the devs obviously know why too (as we can see in the source code) which makes it even more odd that it is included by default when it is quite obviously flawed by design.

I don't know what determines which software gets put in the default Ubuntu install set but it seems to me that other decent stuff has been suggested but declined [check the brainstorm site], however a flawed and broken app has been included by default now and it just so happens that Canonical have made it. 

Now it's obvious they can do this because it's their OS. But since so many people have decided to bring up other Windows arguments all the time, what makes Canonical think they can do the same thing as Windows allegedly does?

Whether you like it or not, this application is incomplete, does something which the devs have commented that it shouldn't do but does because there's no other way of doing it. Which should then have meant that the application goes in the repos but not the default install set. 

It is a problem as others have said, because it says it removed old and unsupported versions of software quite clearly. A lot of new users are going to believe this because it's installed by default, has Canonicals name slapped on the about box so it seems like it's a friendly application giving people a helping hand. However what they won't know is "unsupported" doesn't mean an old version of the software in that sense, it means Canonical unsupported which will then remove any of their "unsupported" software. Sure you can say it's the users fault but it's a computer janitor claiming to remove cruft and unsupported packages, it's VERY misleading to new users and this is the whole rant. If after 18 pages, a youtube video and an article with pictures at Linsux explaining the problem in depth and you still haven't realised well please tell me you're not a sysadmin. 

No matter what people think, Computer Janitor is flawed and broken by design because it has to be, there's no other way of doing it and it definitely should not have been included in the default install. It got given a GUI change between 9.04 and 9.10 but it's still fundamentally broken.

---

