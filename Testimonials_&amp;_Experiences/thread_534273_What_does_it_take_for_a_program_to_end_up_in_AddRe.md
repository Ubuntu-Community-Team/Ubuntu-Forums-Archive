---
title: "What does it take for a program to end up in Add/Remove?"
date: 2007-08-25
forum: Testimonials &amp; Experiences
---

### Post by keyboardashtray on 2007-08-25
I've been using Ubuntu for little more than a month I think. Everything is fine at the surface level, and for basic applications installation from Add/Remove is a breeze.

Linux already has the reputation of having a very limited selection of games, and the fact that when something "technically" works natively on Linux you still need a ton of work rigging it to work with your system just makes it seem like that limited pool of software is even smaller.

If something isn't in the repos, all I have to do is take a look at the instructions and realize I'm not even going to bother trying. Here is an excerpt from the instructions for installing Eternal Lands, just one of a dozen games I wanted to try but didn't even bother:
To play on Linux:
Download the zip file, and unzip it.
cd to the directory where you installed it.
chmod to 775 and execute el.x86.linux.bin
edit el.ini and change datadir to where you unzip everything
Also, the zip file has no base directory, so you should unzip it in a new directory you create. 

What the holy hell? Screw that. But then I'm bored, and I think I'm going to try anyway. But if I've learned anything from Ubuntu, it is to look for potential problems on the forums before I even try. And if the forums are any indication, there will be plenty. So I don't bother.

Why isn't there a definitive way of installing programs? With Windows, you extract, double click, pick a directory (and it's the SAME directory all the time, Program Files), and you're done. With Linux, it's different every time.

Right now, if a program has the blessed Linux label, I know it is still a far cry from being compatible with *my* system, and I'm in for a new adventure full of manual reading and forum searching before I'll be running it. 

And that also means I try less programs. I'm not even sure I want this game, but in Windows that wouldn't matter - I'd install it, try it, and if it sucked, uninstall.

Here I have to completely change my approach. Here I have to decide if I like a program *before* I try it. Because if installing is such a chore, I'm sure uninstalling is no picnic either.

Will installing non-repo software always be like this?

More important, though: What is the criteria for a program to end up in the repos, let alone in there and also installable via Add/Remove? I am very thankful to the people who port programs into the repos. To me, the biggest thing that could be done for Ubuntu is to just port a ton of programs into the repos so people like me couldn't say installing is a pain. 

I have no idea what the process is - is it difficult? Or underfunded? Or a low priority? Are there simply not enough volunteers? Why aren't there more programs there? When a programmer makes a Linux program, can he/she also whip up an Ubuntu port and toss it in the repos? Or is there a lot of red tape that prohibits independents/amateurs from making a port? Am I even using the terminology correctly?

Will we ever get to the point where, chances are, if it runs in Linux, it is in the Ubuntu repos? How popular would Ubuntu have to get for that to be the case?

---

### Post by eentonig on 2007-08-25
The answer the titel:

**_De default repo's:_**
All programs that the owners/'official' developpers of the distribution tested and are known to work with the distribution get packaged. If something goes wrong, they'll know where to start in troubleshooting, because it's a standard setup.

**_The extended repo's_**
(Universe/Multiverse and the like.) Volunteers can step in and do some testing and packaging of their own. If they do so, and can convince the community that 
- They will keep the soft up to date.
- It's stable and wont ruin your system.
Then the package can be included in those repo's.

> Commercial
Commercial vendors can work with Ubuntu/Canonical to package their apps which were precompiled to work for Ubuntu. This way, when you buy or install this closed software, you know it should work.


Up untill here. Installing and removing should be easy and well documented.

**_Adding third party repo's_**
John Doe can decide that he likes soft x that much, that he wants to provide a package for it to his distro. Maybe he doesn't know how to supply it to the guys who take of Universe, maybe the soft is stil to buggy, maybe he's just an ego tripper that wants the world to be gratefull to him that they're allowed to use his repo, whatever... He can package the soft and provide his own repo to the world that you can enable.

Software in here 'should' be easy to install/remove. But it depends on how well the owner implemented the packaging rules. Did he suply the correct dependencies or not.

**_Compiling_**
And then there's software that has not been compiled at all. Or better, there's source code. For this, people only provide you with a script that compiles the software and installs it on your system.
You need to manually make sure you have all dependencies. And if you want to uninstall, you'll need to read through the script to find out where things got written. This is usually created for a generic linux. So no real garantuees that it will work on your distro.

I'm sure there's more options. But this gives you an idea

---

### Post by keyboardashtray on 2007-08-25
Thank you - that gives me a very good idea on how it works. I still have a couple questions thouugh:

> **eentonig said:**
> 
**_The extended repo's_**
(Universe/Multiverse and the like.) Volunteers can step in and do some testing and packaging of their own. If they do so, and can convince the community that 
- They will keep the soft up to date.
- It's stable and wont ruin your system.
Then the package can be included in those repo's.


Is it a fairly difficult/time consuming process? Apart from making the program itself, if someone makes the decision to port it to Ubuntu's repos, is it a whole separate, monumental undertaking? Or is it fairly simple procedure (for a programmer) that they can do in a few minutes?

And as far as the convincing goes, that is what I meant by red tape before, is it a lengthy/difficult process to be approved?

I'm trying to understand why, when it seems like Ubuntu is such a popular Linux distribution, there are not more programs (I guess in this case games) in the repos. I would think when a programmer makes a program and wants to get it around they would look at the top five or ten Linux distros and make a port for them (assuming it isn't a difficult procedure). In time, will there ever be a situation where the majority of popular Linux programs are available through Ubuntu repos?

Also, a follow up question: Even if a program *does* make it into the repos, lets say an online game, is it pretty much guaranteed that there will always be a lengthy delay when that program is updated, before that update is made available to the repos? Because, for something like an online game, it is usually mandatory to be running the most recent version (which would mean someone is going to eventually have to install a version the hard way anyway). 

I ask this, because, for an example, Battle for Wesnoth is a game that the current version available is not the most recent one, and so a person can't play online (unless they find others who have an old version also). There also has been several updates to Rhythmbox, the default music player for Ubuntu, and even that isn't up to date. Is it safe to say that if someone wants up to date programs, the repos/updater is simply not an option (in other words, they better go back to windows?)

---

### Post by ticopelp on 2007-08-25
I agree that Linux is not an ideal gaming platform. If playing games is really important to you, it's best you either be prepared to do a little learning / tweaking, or stick with Windows if familiarity of installation is very important to you. 

Personally, I use Linux to get work done and be productive, and find my gaming amusements elsewhere, because Linux really is not a gaming platform. I did install Neverwinter Nights on my machine, and it only needed a little bit of tweaking to run beautifully. 

As for your last question, I think you're somewhat off the mark. Lots of third-party developers have their own repos available, and you can get the latest versions of software that way. I have the Compiz repos enabled, for example, and those update pretty much daily. There's also Subversion if you really want to be adventurous and try out nightly builds of software.

Ubuntu's release cycle is intended to bring the most stable builds of software available to users. Given that so many new users give up in the face of the slightest trouble, I think this is a sound approach. For a lot of users, including myself, something that works and is stable is far preferable to the latest version with lots of bugs. I had this problem on Windows all the time, to be honest -- the latest version of iTunes would break or destroy my music library or ratings, etc.

But, if that sort of thing is important to you, you can easily get the latest version of everything. You just have to be willing to learn and make a little extra effort.

---

### Post by keyboardashtray on 2007-08-25
> **ticopelp said:**
> 
As for your last question, I think you're somewhat off the mark. Lots of third-party developers have their own repos available, and you can get the latest versions of software that way. I have the Compiz repos enabled, for example, and those update pretty much daily. There's also Subversion if you really want to be adventurous and try out nightly builds of software.

Ubuntu's release cycle is intended to bring the most stable builds of software available to users. Given that so many new users give up in the face of the slightest trouble, I think this is a sound approach. For a lot of users, including myself, something that works and is stable is far preferable to the latest version with lots of bugs. I had this problem on Windows all the time, to be honest -- the latest version of iTunes would break or destroy my music library or ratings, etc.

But, if that sort of thing is important to you, you can easily get the latest version of everything. You just have to be willing to learn and make a little extra effort.

Well, I'm not a hard core gamer. I don't expect Ubuntu or Linux to be a fantastic gaming platform, either, I realize most cutting edge games are a very commercial thing. Which is why I'm looking at native Linux games. I primarily use Ubuntu for internet browsing/media - and I  intend to stick with it, because I'm into the ideals of GNU and FSF.

At the same time, I find it frustrating that programs that run "natively" on Linux are such a chore to install. As an outsider my perhaps idealistic and admittedly demanding-sounding first impression is "geez, I'm already limiting myself to less than one percent of software that exists, you'd think at least that one percent would be relatively simple." 

And while effort is in the eye of the beholder, I guess all I can say is: I'm here, I installed Ubuntu, I got this far - I think it's safe to say I've already dabbled with tweaking more than the average Windows user is painted as doing.

I've heard the logic of less up-to-date traded for stability for the repos before, and on principle it makes sense, but on application I think it is taken too far. I'll come back to Rhythmbox again: Right now, they are up to 0.11.1, and for a while it has supported tag editing, one of those most frequently asked questions about it. Clearly, people wonder why they aren't able to edit tags with Ubuntu's default music player - we're still on version 0.10.0. I could understand why a third party program might take longer, but this is the flagship music player. One would think a more recent version would be available that wouldn't be a fundamental risk to system stability. If it takes so long to make something stable, one has to wonder if there is some underlying flaw in Ubuntu if it would be so risky to system stability to update the flagship media player.

And also on the subject of stability, if it is so important, isn't there something to be said for making a safer install (repo version) of a given program available as opposed to having it so far behind that it basically encourages someone to get the update the "back alley" way? I'll tell you what, having some novice like me fumbling around in the console typing sudo-this and chmod-that from the advice of a complete stranger, without a clue as to what they are doing, seems a whole lot riskier to system stability than having relative professionals make a more up-to-date version available on the repos.

So much of the purported stability comes from a perfect-world by-the-book use of Ubuntu that means only installing security and recommended updates, only enabling Ubuntu approved software sources, and certainly never dabbling with non-packaged third party programs. It's like there are two Ubuntus, the one everyone advertises as "Linux for Everyone" (where you follow the advice above and are perfectly content to stay that way) and the one that everyone saying that *actually* uses, which involves plenty of the stuff stereotypically Linux that scares that first group off - the stuff the fans claim isn't a problem.

---

### Post by ticopelp on 2007-08-26
> **keyboardashtray said:**
> 
At the same time, I find it frustrating that programs that run "natively" on Linux are such a chore to install. As an outsider my perhaps idealistic and admittedly demanding-sounding first impression is "geez, I'm already limiting myself to less than one percent of software that exists, you'd think at least that one percent would be relatively simple." 


Certainly the definition of what constitutes a "chore" depends on the person. Most software *is* really simple to install. sudo-apt get install whatever, or boot up Synaptic and click on a check box. Oh my, what a hardship. Even compiling from source isn't that difficult -- I do it all the time with the latest builds of Pidgin, and it amounts to typing out one line of code and walking away from my computer for a couple minutes! Dear lord, no! It's like pulling teeth! 

And I'm not a hardcore gamer either, or even a hardcore Linux user, for that matter. 

> **keyboardashtray said:**
> 
And while effort is in the eye of the beholder, I guess all I can say is: I'm here, I installed Ubuntu, I got this far - I think it's safe to say I've already dabbled with tweaking more than the average Windows user is painted as doing.


Very cool, and welcome to the community. 

> **keyboardashtray said:**
> 
I've heard the logic of less up-to-date traded for stability for the repos before, and on principle it makes sense, but on application I think it is taken too far. I'll come back to Rhythmbox again: Right now, they are up to 0.11.1, and for a while it has supported tag editing, one of those most frequently asked questions about it. Clearly, people wonder why they aren't able to edit tags with Ubuntu's default music player - we're still on version 0.10.0. I could understand why a third party program might take longer, but this is the flagship music player. One would think a more recent version would be available that wouldn't be a fundamental risk to system stability. If it takes so long to make something stable, one has to wonder if there is some underlying flaw in Ubuntu if it would be so risky to system stability to update the flagship media player.


Yeah, I often think the same thing about Microsoft -- if there isn't some fundamental flaw in Windows that motivates software developers -- not just third party developers, but MS themselves -- to release software so buggy and full of security holes that machines can get completely disabled just by plugging into the Internet (if you were around for the days of the Blaster virus). 

I'll be the first one to say that Linux media players are not quite up to Windows or Mac standards. I was a big fan of iTunes for a long time, and got very used to the interface and features, and I haven't quite found one that I'm happy with, although Songbird looks promising. But it was a worthy trade-off for me to get away from the DRM, bugs, and security holes I had to put up with. 

By the way, I edit ID3 tags with Rhythmbox all the time, and I'm using the version that shipped with Feisty. So I'm not sure what you're talking about there. 

> **keyboardashtray said:**
> 
And also on the subject of stability, if it is so important, isn't there something to be said for making a safer install (repo version) of a given program available as opposed to having it so far behind that it basically encourages someone to get the update the "back alley" way? I'll tell you what, having some novice like me fumbling around in the console typing sudo-this and chmod-that from the advice of a complete stranger, without a clue as to what they are doing, seems a whole lot riskier to system stability than having relative professionals make a more up-to-date version available on the repos.


LOL. I'm afraid I can't get behind that at all. There's one entity who takes responsibility for any damage or changes done to your system from you messing around with "sudo this and chmod that," and that is YOU. Stable, usable software "encourages" you to update the "back alley" way? I'm sorry, but that's BS. Give me a break and learn some responsibility, please. 

When I was first learning Linux, I borked my system a couple of times by fooling around where I knew I shouldn't be -- but that's how one learns, by experimenting. If you want your machine to be reliable and stable, use the software as shipped from Ubuntu -- they have a six-month release cycle, as compared to 7+ years for Microsoft's latest, so you won't have that long to wait to get an updated version. If you want to install newer or beta software, do a little research and learn how -- but when it comes to beta software, you take your chances, no matter what operating system you're using. 

> **keyboardashtray said:**
> 
So much of the purported stability comes from a perfect-world by-the-book use of Ubuntu that means only installing security and recommended updates, only enabling Ubuntu approved software sources, and certainly never dabbling with non-packaged third party programs. It's like there are two Ubuntus, the one everyone advertises as "Linux for Everyone" (where you follow the advice above and are perfectly content to stay that way) and the one that everyone saying that *actually* uses, which involves plenty of the stuff stereotypically Linux that scares that first group off - the stuff the fans claim isn't a problem.

Generally, it isn't a problem, once you educate yourself. Frankly, your point seems pretty self-contradictory to me. "Oh, sure, Ubuntu works fine out of the box, but if I try to get under the hood and screw around... well, that's too hard and I shouldn't have to learn how!" Well, you don't have to learn how. But if you want to get under the hood of Linux and use some of the more fun stuff, you have to learn how the OS works. There's no way around that, I'm afraid. And if you're too busy or unmotivated to learn those kind of things (which are, again, not very hard at all IMHO), then unless you're having massive hardware issues, you shouldn't have to.

I'm certainly not claiming Ubuntu is without problems -- I've used many versions of Windows, Mac and Linux OSes throughout the years, and I've had issues with all of them. I just don't think what you're talking about here is as big a shortcoming as you're making it out to be.

---

### Post by wolfen69 on 2007-08-26
ive never once had to compile an app myself. between synaptic/add-remove/www.getdeb.net i have never had a problem finding what i need. if you don't like the command line, wait until gutsy gibbon comes out. ive been  using it for 3 days and havnt had to use the command line once. and EVERYTHING is working. have fun.

---

### Post by Lord Illidan on 2007-08-26
Dude, installing Eternal Lands is a doddle. It doesn't take much to learn how to do it, and once you'll do it you'll take off.

---

### Post by keyboardashtray on 2007-08-29
> **ticopelp said:**
> Certainly the definition of what constitutes a "chore" depends on the person. Most software *is* really simple to install. sudo-apt get install whatever, or boot up Synaptic and click on a check box. Oh my, what a hardship. Even compiling from source isn't that difficult -- I do it all the time with the latest builds of Pidgin, and it amounts to typing out one line of code and walking away from my computer for a couple minutes! Dear lord, no! It's like pulling teeth! 

First, you start by describing the repositories (which is what my title and OP are about: I say that there should be more programs there, that those are easy to install). Then you say how easy the repos are and you include a sarcastic comment "Oh my, what a hardship.", essentially taking my argument about non-repo software and transferring it to repo software. (Because if this guy can't install from the repos, certainly any problems he's having with other software is from his own stupidity/ignorance.) [http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

Then you go to describe compiling from source and how "easy" it is (by way of another sarcastic comment "Dear lord, no! It's like pulling teeth!") What I take from this, is that In your opinion, anything including and short of compiling from source is so easy that everyone should know how to do it, and therefore any problems with ease of use for the end-user is due completely to the ignorance of that user - clearly, the software can never be at fault. 

Conversations about ease of use with the likes of you are useless, since you've already established that: 
a.) any discussions of such are simply an argument to be won regardless of finding actual truth
b.) clearly you are out of touch with the abilities and expectations of the average computer user

Therefore I find it pointless to detail the rest of your fallacies: I believe you are trolling me and am updating my ignore list to reflect it.

---

### Post by keyboardashtray on 2007-08-29
> **wolfen69 said:**
> ive never once had to compile an app myself. between synaptic/add-remove/www.getdeb.net i have never had a problem finding what i need. if you don't like the command line, wait until gutsy gibbon comes out. ive been  using it for 3 days and havnt had to use the command line once. and EVERYTHING is working. have fun.

I'm excited to see Gutsy then :)

---

### Post by stinger30au on 2007-08-29
> **keyboardashtray said:**
> I'm excited to see Gutsy then :)

i cant wait for Gutsy, it certainly sounds great

---

### Post by keyboardashtray on 2007-08-29
> **Lord Illidan said:**
> Dude, installing Eternal Lands is a doddle. It doesn't take much to learn how to do it, and once you'll do it you'll take off.

A doddle? Flushing a transmission is a doddle compared to rebuilding one, but it is still a pain in the *** and if you mess up you can still do some damage. 

I *did* install Eternal Lands after my post, and let me tell you, it was as much of a headache as I thought it would be.

I had to download it 4 times, and while 2 of those times can be attributed to a bad download, the myriad of information available as well as the amount and variety of problems made it so I had no clue as to whether it was simply that, a bad download, or if I had done something wrong, as I had plenty of opportunities to screw it all up.

Without giving a link to every single post on installing it, I can tell you that there are at least a half a dozen variations on installation, which only makes it that much harder. Ranging from just put it on your desktop and right click and select make executable, to several different values for chmod (775, 777, -x) to getting some lib0blahblahlblah from the repos *then* trying any combination of the former. 

One poster said to type sudo -R chmod in a command, well, luckily I knew that meant repeat command for every file, but the potential for the casual user who takes these commands as casually as they are presented could have really messed crap up. I changed all of the download anyway, just out of desperation. Of course, it *did* mess everything up, and then I had to download it again. 

Finally I stumbled on some info that said if I ran the file it would mean I'd also need to change some .ini file hidden in my home directory, apart from the one in the el folder that I knew I'd already have to change. If I would've attempted this in usr/local/games or wherever the others recommended, would there have been some master .ini file? Where would that have been? 

Not to mention the whole "tampering with the guts" feel that *all* of this has to the new user.

Suffice it to say that whatever I did that got it to work I don't remember, but it was not what the site told me, nor was it directly from a post. It was some hassle filled hybrid of all of it.

Please, don't come here telling me it's a doddle, because we all know the base comparison is to Windows (for all its faults, yada yada) where I download the file, unzip it, run the .exe, and pick a directory.

And in the end, by the way, didn't like the game, which left a particularly sour note after all the struggle - therefore reinforcing my reluctance to try other non-repo software.

---

### Post by ticopelp on 2007-08-29
> **keyboardashtray said:**
> Therefore I find it pointless to detail the rest of your fallacies: I believe you are trolling me and am updating my ignore list to reflect it.

Well, I'm sorry you feel that way. I wasn't attempting to troll you, just disagreeing, and none of it was meant as a personal attack. Sorry if my arguments don't meet your rigorous standards of logic -- I'm not a machine, after all. Best of luck to you.

Just as an aside -- likely a useless one, since you put me on your ignore list over this trifle -- I never claimed the software "could never be at fault." I stated quite the opposite several times. In fact, you seem to have either accidentally or deliberately misconstrued what I said several times. I simply said most software in the repos is easy to install -- I didn't say anything about all Linux software being in the repos, which it clearly isn't. 

As for compiling from source, I maintain that it isn't that hard under most circumstances -- I certainly think it would be good for Ubuntu and Linux in general if end users didn't have to compile from source, though, and Ubuntu is slowly moving towards that point, as said above regarding Gutsy. I know I certainly prefer just using apt-get to downloading and compiling source code. All I was saying is that it isn't the brutal hardship some make it out to be -- just a bit of typing or cutting and pasting. I'm not a Unix engineer or a programmer, and I managed to figure it out.

---

### Post by Alex Fernandez on 2007-08-31
I dont see whats so hard about:
./configure
make
sudo checkinstall make install

---

