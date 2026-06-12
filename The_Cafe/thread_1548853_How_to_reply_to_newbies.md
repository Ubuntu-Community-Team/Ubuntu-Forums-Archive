---
title: "How to reply to newbies?"
date: 2010-08-09
forum: The Cafe
---

### Post by sikander3786 on 2010-08-09
Hi everybody.

I was just thinking that the overall impact of Linux on one's mind who has never used Linux is that it is a bit "geeky command line thing". It is GUI friendly but the new users don't know it. Linux's power is its command line but that too, new users migrating from proprietary OS don't care about.

So I feel that when replying to a newbie, one should guide him to the GUI instead of command line e.g, when guiding one to install GIMP, instead of

```

sudo apt-get install gimp

```

he should be guided to the software center.

Another example, when one asks for changing the default boot OS in GRUB, instead of making him edit his GRUB menu.lst file manually, encourage him to install *statupmanager* and he will be happy.

For updates of course, instead of

```

sudo apt-get update && sudo apt-get upgrade

```

we should use update manager, thats what it is built for.

There are many more examples. One should feel about the author's abilities, temperament and experience and reply him accordingly.

GUI is a better option because it will help Linux clear the minds of those who think it is a bit geeky and they fear the command line and therefore stay away from it.

At least that is what I think, what do you guys think?

Regards.

---

### Post by mendhak on 2010-08-09
I think it's unavoidable, though. At some point they'll have to edit files somewhere or use the terminal.  For example - and let me know if there was a better way - in order to get files syncing between a Win7 machine and this Ubuntu machine, I had to add entries to fstab and sometimes have to call sudo mount -a if I turn the Win7 machine on (if Ubuntu is already running), so that the mounted directories are visible to Unison.

---

### Post by sikander3786 on 2010-08-09
It is unavoidable. I agree. But when it can be avoided, it should be avoided. Thats the point.

---

### Post by themusicalduck on 2010-08-09
The problem is that it is much easier to say "type sudo apt-get install gimp into a terminal" than to describe where to find and how to use the Software Centre to someone. If you're replying to a lot of support threads, it gets tiring quite quickly when you're advising people to use the GUI route all the time.

Perhaps in reality it should be easier for users to find these kind of features themselves in the first place? I think things like the Ubuntu Manual Project should be advertised much more than it is since this is basically what it's for.

---

### Post by krishnandu.sarkar on 2010-08-09
> **themusicalduck said:**
> The problem is that it is much easier to say "type sudo apt-get install gimp into a terminal" than to describe where to find and how to use the Software Centre to someone. If you're replying to a lot of support threads, it gets tiring quite quickly when you're advising people to use the GUI route all the time.

Perhaps in reality it should be easier for users to find these kind of features themselves in the first place? I think things like the Ubuntu Manual Project should be advertised much more than it is since this is basically what it's for.

+1

I think suggesting commands are far better then guiding him/her in GUI Method. And what's the problem if someone is saying the command and even suggesting where to run(for those who don't know what and where to find Terminal).

As once in a life time he/she is bound to use Terminal, it's better to suggest him/her Terminal commands. In this way he/she will learn. As I did....thanks to Ubuntu Forum and #ubuntu.

So I think suggesting commands is much better for us and for the user too(who are willing to learn).

---

### Post by aysiu on 2010-08-09
It actually depends. Sometimes it's more appropriate to offer GUI instructions. Other times, it's more appropriate to offer CLI instructions.

More details here:
[The GUI v. CLI Debate](http://www.psychocats.net/ubuntucat/the-gui-v-cli-debate/)

---

### Post by DougieFresh4U on 2010-08-09
> **sikander3786 said:**
> 



For updates of course, instead of

```

sudo apt-get update && sudo apt-get upgrade

```

we should use update manager, thats what it is built for.


I like to use both GUI and command line. Quite a few people use the 'Update Manager' (I stay away from that mess!!)and then come to the forum seeking help because they did a 'partial update' not knowing exactly what 'partial update' meant and it 'borked' their system

---

### Post by lisati on 2010-08-09
Command line vs GUI: another one is Software Center vs Synaptic. As someone already observed, "it depends".

---

### Post by wirate on 2010-08-09
If you always guide them to the GUI, they wont discover the most prominent strength of Linux; the powerful and I would say awesome command line

---

### Post by saulgoode on 2010-08-09
> **sikander3786 said:**
> GUI is a better option because it will help Linux clear the minds of those who think it is a bit geeky and they fear the command line and therefore stay away from it.

At least that is what I think, what do you guys think?
I think if you want "newbies" to be provided with a particular solution to a problem then you should provide them with that solution, not proscribe alternative approaches.

---

### Post by t0p on 2010-08-09
If both methods are applicable, I generally give the command line solution as it is often easier to explain (and, I dare say, understand) and it's a good thing for newbies to get some idea of how to use the CLI.

---

### Post by Linye on 2010-08-09
Using Ubuntu since April and for me CLI is better.

When I ask for help It's easier to open the Terminal and copy/paste something than going around clicking on stuff.

---

### Post by Paqman on 2010-08-09
> **mendhak said:**
> I think it's unavoidable, though. At some point they'll have to edit files somewhere or use the terminal.  

Maybe, but they don't need to be shown how to immediately, especially for tasks where there is a perfectly good GUI.

Being at the bottom of a learning curve sucks, we tend to forget that from our smug position near the top. Stuff like this seems easy and obvious to us, but it's weird and confusing to newbs. We should be bending over backwards to make it as easy as possible for them. 

Unless someone specifically requests a command line tool (and they do) then they should be pointed at the GUI tool. They're far more likely to remember how to use the GUI in six weeks time than they are the command line method. Teaching the GUI teaches self-reliance and builds confidence. With confidence comes the ability to take on more advanced knowledge (such as CLI use). Diving in to the advanced subjects first just intimidates people and drives them away.

It's just basic teaching practice:
[LIST=1]
[*]Move from the known to the unknown
[*]Move from the simple to the complex
[/LIST]

Many people give the CLI method because it's simply less typing for them, and they want to score geek points by getting in the first answer. I think that's lazy and selfish. If you can't be bothered tailoring your advice to the correct level, then don't reply to newbs.

---

### Post by ronnielsen1 on 2010-08-09
One reason against that is not everyone is running gnome, some are running other window managers / de's  

Command line always works

---

### Post by grahammechanical on 2010-08-09
As someone new to giving advice in these forums and as I lack extensive knowledge of the outer workings of Linux, let alone the inner workings, I prefer to give advice based on the GUI and its menus.

I have been following the networking forum. I wonder if some are trying to solve their problems with wireless and networking in too complicated a manner. Ubuntu does what I want and it works. I can also learn how to change things using the menus. From here I can advise others on how to solve their problems.

I have also experienced following command-line instructions only for something to fail. Sometimes you can know so much that you fail to understand how little the other person knows. The answer is simple to you but to people like me it is like a foreign language. I also think that many should do more research before asking questions. The same 'not working' questions are asked again and again.

These forums exist because Ubuntu is not pre-installed. So, anyone installing it needs to learn to do things that they did not need to learn when they first brought the computer.

Regards.

---

### Post by Tibuda on 2010-08-09
> **sikander3786 said:**
> So I feel that when replying to a newbie, one should guide him to the GUI instead of command line e.g, when guiding one to install GIMP, instead of

```

sudo apt-get install gimp

```

he should be guided to the software center.

what about an [apturl](apt:gimp)?

---

### Post by Legendary_Bibo on 2010-08-09
Two words. Shell scripts. It's the in between of both worlds. The user is using a terminal command, and can be told how to set it up with a few clicks.

---

### Post by Tibuda on 2010-08-09
> **Legendary_Bibo said:**
> Two words. Shell scripts. It's the in between of both worlds. The user is using a terminal command, and can be told how to set it up with a few clicks.

and take the risk of running malicious code.

---

### Post by Legendary_Bibo on 2010-08-09
> **danielrmt said:**
> and take the risk of running malicious code.

<snip> Just give them a script so lets say they wanted to install gimp, and shell script would look like this:

```

#!/bin/sh
sudo apt-get install gimp

```

If you chmod it for them then tell them the click through, and it's easier on everyone.

---

### Post by XubuRoxMySox on 2010-08-09
> **ronnielsen1 said:**
> One reason against that is not everyone is running gnome, some are running other window managers / de's  

Command line always works

+1 to that! There are some questions I haven't been able to answer to a newbie's satisfaction just because I'm not familiar with the d e they're using. So I cruise thru the topics for the ones labeled "Xubuntu" and offer the GUI solution usually. But the CLI works regardless of the d e. That's why it's easier to just offer the CLI as a "one size fits all" solution. But it turns alot of newbs off. It used to completely turn me off too when I was brand new and scared to death that I'd mis-type some command and totally disrupt the whole space-time continuum or something.

-Robin

---

### Post by Frogs Hair on 2010-08-09
Being a newbie , either way is ok with me . I enjoy the command line , so learning a new command is always a plus and I prefer that .

---

### Post by donkyhotay on 2010-08-09
Working with newbies both online and in real life I find it much easier to say:
"copy and paste the following command into the CLI"
then it is to say:
"Find application in the upper left hand corner, click on software center, type <program name> into the search, what results do you see? double check your spelling on the search, what do you see now? now click on the one marked <program name>, no not the one marked <something similar> cancel out of that, click on, wait! stop! don't click on that again! <sigh> @#$% it, just copy and paste the following command into the CLI"
GUI is great for people trying to figure stuff out themselves but if someone really has no clue whats going on it's much easier for them to just copy and paste something into the CLI to fix it. They don't have to understand the command to use it and once they have more experience they'll learn how to do things themselves either from the CLI or GUI whichever works best for them.

---

### Post by sydbat on 2010-08-09
> **Paqman said:**
> Maybe, but they don't need to be shown how to immediately, especially for tasks where there is a perfectly good GUI.

Being at the bottom of a learning curve sucks, we tend to forget that from our smug position near the top. Stuff like this seems easy and obvious to us, but it's weird and confusing to newbs. We should be bending over backwards to make it as easy as possible for them. 

Unless someone specifically requests a command line tool (and they do) then they should be pointed at the GUI tool. They're far more likely to remember how to use the GUI in six weeks time than they are the command line method. Teaching the GUI teaches self-reliance and builds confidence. With confidence comes the ability to take on more advanced knowledge (such as CLI use). Diving in to the advanced subjects first just intimidates people and drives them away.

It's just basic teaching practice:
[LIST=1]
[*]Move from the known to the unknown
[*]Move from the simple to the complex
[/LIST]

Many people give the CLI method because it's simply less typing for them, and they want to score geek points by getting in the first answer. I think that's lazy and selfish. If you can't be bothered tailoring your advice to the correct level, then don't reply to newbs.++

> **grahammechanical said:**
> As someone new to giving advice in these forums and as I lack extensive knowledge of the outer workings of Linux, let alone the inner workings, I prefer to give advice based on the GUI and its menus.

I have been following the networking forum. I wonder if some are trying to solve their problems with wireless and networking in too complicated a manner. Ubuntu does what I want and it works. I can also learn how to change things using the menus. From here I can advise others on how to solve their problems.

I have also experienced following command-line instructions only for something to fail. Sometimes you can know so much that you fail to understand how little the other person knows. The answer is simple to you but to people like me it is like a foreign language. I also think that many should do more research before asking questions. The same 'not working' questions are asked again and again.

These forums exist because Ubuntu is not pre-installed. So, anyone installing it needs to learn to do things that they did not need to learn when they first brought the computer.

Regards.Also ++.

I try to help as much as I can, often with a GUI solution. Other times with a CLI solution. It really does depend on where the user is posting and how their question is worded.

Then, if it is a question that has been asked many times, I do a quick search, post one or two similar thread links, and let the OP know that searching is useful. I try not to be condescending (emphasis on try).

---

### Post by MasterNetra on 2010-08-09
> **themusicalduck said:**
> The problem is that it is much easier to say "type sudo apt-get install gimp into a terminal" than to describe where to find and how to use the Software Centre to someone. If you're replying to a lot of support threads, it gets tiring quite quickly when you're advising people to use the GUI route all the time.

Perhaps in reality it should be easier for users to find these kind of features themselves in the first place? I think things like the Ubuntu Manual Project should be advertised much more than it is since this is basically what it's for.

There is this nifty thing called copy and paste. Create your reply for the GUI route, save it in a document and when you need it, open it and copy the contents and paste it onto forum or where ever.

---

### Post by sydbat on 2010-08-09
> **MasterNetra said:**
> There is this nifty thing called copy and paste. Create your reply for the GUI route, save it in a document and when you need it, open it and copy the contents and paste it onto forum or where ever.I like this. I'm going to start doing it. :D

---

### Post by scouser73 on 2010-08-09
I think it's important to give as much detailed assistance to newbies as possible, as not everyone is familiar with the terminal and how to make full use of it.

It's sort of like [[COLOR="Red"]**Paying It Forward**[/COLOR]]("http://en.wikipedia.org/wiki/Pay_it_forward"), if that makes any sense, lol.

---

### Post by mojo risin on 2010-08-09
I think you need to differ between newbies who just want a working system and newbies who are actually also interested in terminals and the make up of a system.

I do remember Dos from my early childhood and I was curious about how the command line looks in here. I am sure interested to learn how to use it and how to improve the system without having to rely too much on oneself.I would say you offer both solutions at first  so the newbie can decide whether he prefers the GUI way or the terminal way.

---

### Post by MasterNetra on 2010-08-09
> **scouser73 said:**
> I think it's important to give as much detailed assistance to newbies as possible, as not everyone is familiar with the terminal and how to make full use of it.

It's sort of like [[COLOR="Red"]**Paying It Forward**[/COLOR]]("http://en.wikipedia.org/wiki/Pay_it_forward"), if that makes any sense, lol.

Not when they first starting out you don't as it may scare them off, many will most likely just become casual users, but when they are comfortable with the OS, you could I suppose supply them with a Beginners guide to the terminal that explains how and why its useful as well as the basics in using it.

---

### Post by sikander3786 on 2010-08-09
> **donkyhotay said:**
> Working with newbies both online and in real life I find it much easier to say:
"copy and paste the following command into the CLI"
then it is to say:
"Find application in the upper left hand corner, click on software center, type <program name> into the search, what results do you see? double check your spelling on the search, what do you see now? now click on the one marked <program name>, no not the one marked <something similar> cancel out of that, click on, wait! stop! don't click on that again! <sigh> @#$% it, just copy and paste the following command into the CLI"
GUI is great for people trying to figure stuff out themselves but if someone really has no clue whats going on it's much easier for them to just copy and paste something into the CLI to fix it. They don't have to understand the command to use it and once they have more experience they'll learn how to do things themselves either from the CLI or GUI whichever works best for them.

I don't think you need to hold one's finger and take him across. Instead I will tell one to go to "Software Center" and search for "GIMP". That's all. He is a newbie to Linux, Ubuntu, not new to computers and OS etc. He will himself figure out where is the button for "Install" and what the package is offering to him (as the description is always there).

It is easy to teach one to use "Software Center" than "apt-get". In software center there is a bit margin of error i.e, spelling. But in apt-get, you have to be dead accurate.

And then when he has to install something else, he will himself go to Software Center and try to do it himself unless some complications arise.

In the beginning I was also getting annoyed when everyone used to tell me to go to terminal and type "etc etc" and my friends, sitting besides me, starring and saying "He is gonna be mad very soon (due to lots of typing, editing files etc)." Then I found that there was a possibility to do almost everything via GUI in Ubuntu and I adopted it.

I agree, CLI has got the learning curve, it is far more stable, accurate and powerful but not for the beginners. A newbie doesn't even know that his password is not going to show up as ***** in terminal when he asks for root privileges and there are many newbies asking about it in the forums and web. Then you have to tell him to just hit enter after typing his password and he "learns".

There are many people arguing in favor of GUI and many against it. Yet one has to think that this is 2010, there is 3D, desktop effects and appealing graphics going on the computer. Linux is also for beginners and home users, not only for geeks and server environments and that will be accomplished only when there is not much typing involved. Everything should be just a few clicks away.

---

### Post by giddyup306 on 2010-08-09
Give them the command line.  If they can't grasp that concept Linux probably isn't for them.  They will need to learn how to use it sooner or later.

---

### Post by MasterNetra on 2010-08-09
> **giddyup306 said:**
> Give them the command line.  If they can't grasp that concept Linux probably isn't for them.  They will need to learn how to use it sooner or later.

Not true, my sister-in-law is the type that doesn't the use the command line but she finds Ubuntu & Mint Easy to use and has no problem with it. She just using it for word processing, surfing the net, and facebook + facebook games.

---

### Post by sikander3786 on 2010-08-09
> **MasterNetra said:**
> Not true, my sister-in-law is the type that doesn't the use the command line but she finds Ubuntu & Mint Easy to use and has no problem with it. She just using it for word processing, surfing the net, and facebook + facebook games.

2 of my friends, my younger brother and my wife likes to use Ubuntu and none of them knows what is going underneath, they like to use the GUI for everything and are happy about it.

Just added the poll to get the better of the results. Lets find out what we get in the results. :p

---

### Post by donkyhotay on 2010-08-09
> **sikander3786 said:**
> I don't think you need to hold one's finger and take him across. Instead I will tell one to go to "Software Center" and search for "GIMP". That's all. He is a newbie to Linux, Ubuntu, not new to computers and OS etc. He will himself figure out where is the button for "Install" and what the package is offering to him (as the description is always there).

It is easy to teach one to use "Software Center" than "apt-get". In software center there is a bit margin of error i.e, spelling. But in apt-get, you have to be dead accurate.

And then when he has to install something else, he will himself go to Software Center and try to do it himself unless some complications arise.

In the beginning I was also getting annoyed when everyone used to tell me to go to terminal and type "etc etc" and my friends, sitting besides me, starring and saying "He is gonna be mad very soon (due to lots of typing, editing files etc)." Then I found that there was a possibility to do almost everything via GUI in Ubuntu and I adopted it.

I agree, CLI has got the learning curve, it is far more stable, accurate and powerful but not for the beginners. A newbie doesn't even know that his password is not going to show up as ***** in terminal when he asks for root privileges and there are many newbies asking about it in the forums and web. Then you have to tell him to just hit enter after typing his password and he "learns".

There are many people arguing in favor of GUI and many against it. Yet one has to think that this is 2010, there is 3D, desktop effects and appealing graphics going on the computer. Linux is also for beginners and home users, not only for geeks and server environments and that will be accomplished only when there is not much typing involved. Everything should be just a few clicks away.

Depends on your newbie, someone using windows/osX for awhile moving to linux might manage with that though hopefully they've read the forums, new users guides, etc. which explains all this stuff already and they don't need help. If you've got such a novice that you have to specify left click each and every time you tell them to click something (which I have worked with before) then the CLI is the definite way to go. When we're talking about helping a newbie install software I assume we're past the "query: how do I install <program name>?", "reply: here is a link to <guide that explains how to do it>" which is fine because many newbies on that level would "RTFM" if they just knew where the manual was and need to be guided towads it. The guides are perfect for explaining how to use GUI functions since you can give screenshots to make it easier to follow. On the other hand you get people that can't understand the manual and/or don't care about anything on the computer besides getting <that one program> installed. At which point the CLI is the fastest and easiest way to resolve the issue. As I said previously, they don't need to know what the command means, they just need to copy and paste to get it working.

---

### Post by cariboo on 2010-08-09
If you do give a new user a cli solution to their problem, you should explain what the commands in the terminal do, just giving them something to copy and paste doesn't help them understand what they are doing.

---

### Post by donkyhotay on 2010-08-09
> **cariboo907 said:**
> If you do give a new user a cli solution to their problem, you should explain what the commands in the terminal do, just giving them something to copy and paste doesn't help them understand what they are doing.

I've found if people are interested they'll ask how the command works on their own. At which point you break apart the command for them, explain the different sections and educate them on how you did it. If they don't then there is no reason to force feed them more info then they care about.

---

### Post by bergfly on 2010-08-09
This really comes down to a case of what the issue is. If there is a brand new users, ready to abandon their existing OS and dive into Ubuntu, then the need to have them work in a clear GUI is paramount. If Ubuntu does not cater to this market, why all the focus on the shiny stuff? For most of these users, the best option by far to to hand hold through the GUI where possible, which is much more work from a support point  of view.

Occasionally, a new user will have a complex problem where the only real road to resolution is to use the command line, and in cases like  this it makes sense. However in some of these cases you need to ask, why would one expect the commandline, are we missing a bigger issue in the lack of GUI tools?
Ultimately the goals in helping a newbie are twofold. Firstly we would like to get their issue resolved, however the second and possibly more important goal is to have them adopt Ubuntu as their OS of choice. 
The number of users on this forum who sign-up, post once with a single newbie post, get a complex reply and are never heard from again is a concern. If some of these people were given simple click click check instructions, perhaps more of them could stay in the family. 

Good topic and one to think over...

---

### Post by sikander3786 on 2010-08-09
> **bergfly said:**
> 
The number of users on this forum who sign-up, post once with a single newbie post, get a complex reply and are never heard from again is a concern. If some of these people were given simple click click check instructions, perhaps more of them could stay in the family.

+1 for that.

But I believe it is almost impossible to guide them click by click. All the fellows are volunteers doing their job pretty well at the moment but there is always some room for improvement.

---

### Post by bug67 on 2010-08-09
For the most part I prefer a GUI.  However, I was amazed at the power of the CLI.  I love that about Linux.  Choices.  CLI does makes everything much quicker.  I wish I knew more than basically the copy and paste method I currently employ.  ;)

I love having the choices.  If I know what I want, I usually check Software Center and  Synaptic first.  If I'm on the net browsing for a solution and a command line is presented to me, I have no problems using that.

So, I voted for both.

---

### Post by quids on 2010-08-09
Theres a reason why personal computing caught on and we're not using DOS or Unix anymore - The masses preferred a GUI.
If Ubuntu is really going to be an alternative to Windows then we have to get rid of the geeky terminal response and reply with a GUI method.

Appreciate that my post count in the Ubuntu Forums is that of a newbie, but I prefer to help out in another forum that is dedicated to giving answers in the GUI format.

As a newbie I could have been scared away by long winded duff advise on CLI. But I stubbornly persisted on and have learnt a lot about the CLI and alternative methods provided by GUI programs. 
For a lot of common problems there is an easy enough GUI answer which happens to require a bit more typing to explain.

Of course its easier to type something like
cd ~/Ubuntu One
mkdir something

Than 
Open a file manager (Nautilus / Dolphin / Thunar / PCManFM)
Navigate to Home --> Ubuntu One
Create folder  "something"
 

It makes the Newbies life easier at the expense of ours having to go into more detail

---

### Post by slooksterpsv on 2010-08-09
To help newbies obtain information so we can help them troubleshoot the issue, I'm creating a python GUI application that will obtain the necessary information so they can either:

a) post the information outputted to the forum
b) post the file containing the information to the forum (in a tar.gz)

But that's just for troubleshooting. Other commands could be built into GUI's to obtain/perform what they need to do, someone would just have to make it.

Link to my thread regarding python gui app - still a WIP (work in progress): [http://ubuntuforums.org/showthread.php?t=1548660](http://ubuntuforums.org/showthread.php?t=1548660)

---

### Post by aysiu on 2010-08-09
> **quids said:**
> Theres a reason why personal computing caught on and we're not using DOS or Unix anymore - The masses preferred a GUI. I don't know how old you are, but I remember when personal computing caught on, and it was before GUIs were popular or usable. A lot of people were using MS-DOS computers and then Windows 3.1 (which was not a user-friendly GUI). Through the 80s and early 90s, most computer navigation, even in the GUI, was done through keyboard shortcuts (a lot of F keys and not a lot of mouse).

---

### Post by lisati on 2010-08-09
> **MasterNetra said:**
> There is this nifty thing called copy and paste. Create your reply for the GUI route, save it in a document and when you need it, open it and copy the contents and paste it onto forum or where ever.
Sometimes I wonder if some of the people I know would know what "copy and paste" is, and some of them have been using GUI-based systems for longer than I have! Some of these same people think that "making a presentation" is called "doing a PowerPoint." :D

As for GUI and CLI, I use what suits me at the time. Mind you, some of my experience working in IT many years ago ended up with me using text-based menu systems that were somewhere in between CLI and GUI, without the benefit of a mouse. Going CLI only was frowned upon, and going GUI wasn't an option.

---

### Post by quids on 2010-08-09
> **aysiu said:**
> I don't know how old you are, but I remember when personal computing caught on, and it was before GUIs were popular or usable. A lot of people were using MS-DOS computers and then Windows 3.1 (which was not a user-friendly GUI). Through the 80s and early 90s, most computer navigation, even in the GUI, was done through keyboard shortcuts (a lot of F keys and not a lot of mouse).


PCs still weren't exactly common in the 80s and early 90s. It'll be from the mid 80s I remember back to. 

Perhaps I was thinking more of the people who have come into the world of PCs in the last 10 years when hardware costs have significantly come down and they have only known one OS - Windows XP

---

### Post by Simian Man on 2010-08-09
If there was a moratorium on CLI-based instructions, it would not only hurt users who use something other than vanilla Gnome when they ask questions, but also prevent such users from *answering* questions.  Considering how many experienced users do use alternate setups that is a much bigger problem.

---

### Post by oldos2er on 2010-08-09
I give both GUI and CLI instructions as answers to problems raised on this forum. I think CLI predominates, although I haven't actually counted, just because of its ease of use to implement and to explain. You only need to tell someone once about **man foo** or **apropos foo**; and 99% of people asking for help alreay know how to copy and paste. Any GUI explanations of mine are only for Gnome because of my ignorance of KDE, XFCE, et al.

I think it's important to at least make newcomers aware of the power of CLI; whether they choose to use it or not is ultimately up to them.

"These forums exist because Ubuntu is not pre-installed."

Mine was! Dell XPS 410, acquired in 2007.

---

### Post by sikander3786 on 2010-08-10
> **aysiu said:**
> It actually depends. Sometimes it's more appropriate to offer GUI instructions. Other times, it's more appropriate to offer CLI instructions.

More details here:
[The GUI v. CLI Debate](http://www.psychocats.net/ubuntucat/the-gui-v-cli-debate/)

Well the link you provided was quite interesting. And I find these lines extremely expressing my own thoughts. :p:p

> 
Even though the apt-get command makes perfect sense to me, it is just cryptic gobbledygook to a new user, and it will not help her to install other software in the future unless I bother to explain how the command works; and, more importantly, even if she understands how apt-get works, she’ll still need to know the name of the package she wants to install in order to use the command most efficiently.
    
A lot of new Linux users (myself included, when I first started) have an irrational fear of the terminal, even if you tell them to copy and paste the command with a mouse (no typing necessary). Eventually, as they become more comfortable with the new environment that Gnome or KDE (or Xfce or whatever other user interface they’re exploring) has to offer, they are more likely to be amenable to learning terminal commands and even liking them.
   
Among Windows power users (the most likely group to migrate to an almost-unheard-of operating system that requires download, installation, and configuration from the user and not the OEM), there is already a reputation Linux distros have of being too terminal-dependent. It’s great to advertise to new users just how many things can be done by pointing and clicking, and that will make their transition to Linux that much easier.


---

### Post by sikander3786 on 2010-08-10
> **oldos2er said:**
> I give both GUI and CLI instructions as answers to problems raised on this forum. I think CLI predominates, although I haven't actually counted, just because of its ease of use to implement and to explain. You only need to tell someone once about **man foo** or **apropos foo**; and 99% of people asking for help alreay know how to copy and paste. Any GUI explanations of mine are only for Gnome because of my ignorance of KDE, XFCE, et al.

I think it's important to at least make newcomers aware of the power of CLI; whether they choose to use it or not is ultimately up to them.

"These forums exist because Ubuntu is not pre-installed."

Mine was! Dell XPS 410, acquired in 2007.

Different desktop environments are a hurdle in GUI support but what about this.

> 
I would say something similar to those who use Fluxbox or Enlightenment and want to primarily help those who use Gnome or KDE. If you aren’t familiar with the graphical environment the user you’re trying to help is using, don’t offer help in that instance. Save your help for when the CLI is appropriate. 


---

### Post by Austin25 on 2010-08-10
If you absolutely need a bunch of commands, a shell script should work.
The thing is, its easier to tell someone, "copy and paste this," than "click here, now here, now here, now here..."

---

### Post by Paqman on 2010-08-10
> **ronnielsen1 said:**
> One reason against that is not everyone is running gnome, some are running other window managers / de's  

Command line always works

That's why threads specify the DE being used. It's really not an issue.

If they're using a DE you aren't familiar with, step back and let someone who does know that DE show them how to use it. If they don't get the help they need, then maybe give them your CLI solution.

---

### Post by slackthumbz on 2010-08-10
No, no, no. The way to reply to newbies is with sneering contempt for their utter lack of 1337|\|355 and a resounding chorus of 'RTFM'. :twisted: At least, that's how it was when I started on *nix in the late 90s ;)

---

### Post by renkinjutsu on 2010-08-10
> **Paqman said:**
> Maybe, but they don't need to be shown how to immediately, especially for tasks where there is a perfectly good GUI.

Being at the bottom of a learning curve sucks, we tend to forget that from our smug position near the top. Stuff like this seems easy and obvious to us, but it's weird and confusing to newbs. We should be bending over backwards to make it as easy as possible for them. 

Unless someone specifically requests a command line tool (and they do) then they should be pointed at the GUI tool. They're far more likely to remember how to use the GUI in six weeks time than they are the command line method. Teaching the GUI teaches self-reliance and builds confidence. With confidence comes the ability to take on more advanced knowledge (such as CLI use). Diving in to the advanced subjects first just intimidates people and drives them away.

It's just basic teaching practice:
[LIST=1]
[*]Move from the known to the unknown
[*]Move from the simple to the complex
[/LIST]

Many people give the CLI method because it's simply less typing for them, and they want to score geek points by getting in the first answer. I think that's lazy and selfish. If you can't be bothered tailoring your advice to the correct level, then don't reply to newbs.


**I disagree.**
It's okay to hold a newbie's hand a little, but it is counter productive to carry him or her across the street or over a puddle for them. As you said, being at the bottom of the learning curve sucks. With your approach, the newbies will stay near the bottom for a much longer time; And when things actually go bad (X server doesn't work), what will you tell them to do? Get on another computer, download a LiveCD, burn it, boot it up, open up Gedit and check the contents of /etc/X11/xorg.conf?

Really, directing them only to GUI tools is a surefire way to get them in trouble later on. *"avoiding it because it CAN be avoided"*.. like taking diet pills to avoid exercising.

There are also some nice guys here that give command line fixes and also explain step by step what the command does. Also, your statement about GUI tools helping the user build confidence is true also for the CLI. I installed Ubuntu on my friend's computer because her XP installation stopped working. Sound/pulseaudio was on and off for her and it would always stop working a while after i fix it for her... One day, she phoned me and told me that she looked up how to fix pulseaudio and typed stuff into the command prompt. She said it made her feel very good about herself even though she was just following instructions from a site.

Also, (opinion) one is naturally able to understand GUI apps better after  being experienced with the CLI.

---

### Post by Paqman on 2010-08-10
> **renkinjutsu said:**
> **I disagree.**
With your approach, the newbies will stay near the bottom for a much longer time

Is that a problem? Why should people be made to learn skills they don't want or need? Do you HAVE to be good at the command line to have a successful Linux experience?

> 
And when things actually go bad (X server doesn't work), what will you tell them to do? Get on another computer, download a LiveCD, burn it, boot it up, open up Gedit and check the contents of /etc/X11/xorg.conf?

No, there are clearly cases when providing CLI support is the right way forward. It just shouldn't be the default. I've seen newbies asking in Absolute Beginners how to untar a file, and being given CLI instructions, which is nuts.

> 
There are also some nice guys here that give command line fixes and also explain step by step what the command does.


That's the ONLY way to give CLI instructions, IMO. Flinging a random chunk of unintelligible Bash at someone without explaining it teaches them nothing. Sure, some folks don't want to learn, they just want a fix, but it's still better to give them the chance to understand the fix.

Basically, the problem is that Linux is traditionally used on servers, so the most skillful users have always administrated their systems through the command line. There's no need to cling to that idea on desktop Linux.

---

### Post by malspa on 2010-08-10
Both are acceptable.  And it's probably best, if you have time, to show both approaches.

---

### Post by forrestcupp on 2010-08-10
If the poster wants to learn how to do things on their own, post GUI instructions.

If the poster just wants their problem fixed and feels like they won't need to know how to do it after the problem is fixed, post command line so they can copy and paste and be done with it.

---

### Post by johnson094 on 2010-08-30
I know I'm a couple of weeks late, but as a Newbie...never heard of Ubuntu until 4 days ago, maybe you would like to know what I think personally.  If I understand "GUI" it's kinda sorta like the DOS batch files that I used years ago in Windows.  I would wrie a series of DOS commands save them as a batch file and when I run the batch file it would perform a task.  For example, I may want to create a means of printing out all the files I had in a music file folder.  Create a batch file and one click on that file the printer starts spitting it out.  As for Cli, I guess that would be like opening up a batch file and seeing the dos commands.
 
What I'm saying is that you can give me the Gui but then please direct me to a link that helps see "how you did that"  As a newbie I need both the quick fixes to hold my interest and keep me moving in a positive direction without being killed by frustration, but at the same time, I do want to wean myself off the "do this" and experience "this is how and why you do this"
 
That's just my opion.
 
Thanks

---

### Post by aysiu on 2010-08-30
> **johnson094 said:**
> I know I'm a couple of weeks late, but as a Newbie...never heard of Ubuntu until 4 days ago, maybe you would like to know what I think personally.  If I understand "GUI" it's kinda sorta like the DOS batch files that I used years ago in Windows.  I would wrie a series of DOS commands save them as a batch file and when I run the batch file it would perform a task.  For example, I may want to create a means of printing out all the files I had in a music file folder.  Create a batch file and one click on that file the printer starts spitting it out.  As for Cli, I guess that would be like opening up a batch file and seeing the dos commands.
 
What I'm saying is that you can give me the Gui but then please direct me to a link that helps see "how you did that"  As a newbie I need both the quick fixes to hold my interest and keep me moving in a positive direction without being killed by frustration, but at the same time, I do want to wean myself off the "do this" and experience "this is how and why you do this"
 
That's just my opion.
 
Thanks
GUI means graphical user interface

CLI means command-line interface

GUI is what Windows and Mac offer when you first boot up... and actually what Ubuntu offers as well. It's the panels and icons and wallpaper and all that. It's point-and-click with the mouse. It's OK and Cancel dialogue boxes.

CLI means the cryptic terminal commands (a la MS-DOS). Batch files are CLI, not GUI.

---

### Post by Error: Unknown on 2010-08-30
I like the Cool Linux Interface. I learn more that way

---

### Post by johnson094 on 2010-08-30
I appreciate the explanation, as for the use of Gui vs Cli, I was thinking Gui was one step it'sdone..Cli I saw as how we got the Gui.  Just shows I think like a non tech person, I guess.  Still I would think most newbies want to get a boost to their confidence and then know how it happened.

---

### Post by cariboo on 2010-08-30
Unfortunately you a little of on your definition. GUI stands for **g**raphical **u**ser **i**nterface. What you are calling a gui, is actually called a script in linux speak. The CLI is the same as what you get when you type cmd in Windows, it is a **c**ommand **l**ine **i**nterface.

Most of the members that have been around for a while are more than happy to tell you what a command does. For example if you wanted to be able to access other partitions on your hard drive, they have to be mounted first. To do that from a command line, the command would be:

```
sudo mount /dev/sda5 /media/disk
```

sudo stands for super user do, the super user is the same as the Windows administrator user, mount is self explanitory, /dev/sda5 = the 5th partition on the first hard drive, /media/disk is the mountpoint of the partition, to access it you would navigate to the directory you mounted the partition on type:

```
cd /media/disk
```

cd stands for the same thing it does in DOS/Windows, change directory. if you wanted to se a list of the files in the directory you can use dir, which does the same in WIndows and Linux, or use:

```
ls -ls
``` 

ls means list directory and -ls means long and size. If you wanted to see all the files in the directory you would use:

```
ls -la
```

this time -la stands for long and all.

That's how we would like to see cli commands explained.

---

### Post by johnson094 on 2010-08-30
Oh yea, meant to say I appreciate your link to the tutorials..I bookmarked them and plan to start going through them right away.
 
Thans

---

### Post by Austin25 on 2010-08-30
Offer gui instructions if you want to solve a problem.
Offer cli commands if you want to help.

---

### Post by mamamia88 on 2010-08-30
As a semi newbie I prefer the cli for help.  It's a lot easier to paste commands into command line to fix problems

---

