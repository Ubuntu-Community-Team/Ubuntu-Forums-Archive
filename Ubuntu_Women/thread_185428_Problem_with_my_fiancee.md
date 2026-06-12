---
title: "Problem with my fiancee"
date: 2006-05-31
forum: Ubuntu Women
---

### Post by NinjaZombie on 2006-05-31
Hello,

I have a problem with my fiancee... 3 years ago I introduced her to Linux, I used  Slackware at the time. She liked it alot, and meanwhile she became more proficient in linux than me. Now she uses Linux From Scratch and constantly recompiles everything. Every night she pulls new patches from LFS subversion repository and does ./configure; make; make install the entire night, so we don't get to spend any time together. What can I do to make her switch to Ubuntu? Are there any good Ubuntu advocacy documents available?
Thanks.

---

### Post by meng on 2006-05-31
No you're going to have to call the whole thing off. Walk away now before it's too late. It's that or arrange an intervention. Personally, I'd quit while you're ahead.

Alternatively, you could see this as an opportunity. While she's recompiling, you could be spending time with a mistress (or more than one!)

---

### Post by cjm5229 on 2006-05-31
[www.ubuntuforuns.org](www.ubuntuforuns.org)   Get her on these forums, especially the one for women, and she will talk herself into it.;)

---

### Post by hollywoodb on 2006-05-31
Well, from personal experience using Slackware, Gentoo, and even dabbling with LFS I finally started the search for a good distribution with good package management and polished precompiled packages.  Simple reason being that the time I spent building packages outnumbered the time I spent using them 20:1.

Way I figure it, I can handle the fact that not every package on my system is custom-tailored to my system or needs if the payoff is actually using the software versus keeping it up to date.  Let's just say my productivity has increased ;)

---

### Post by linuchsan on 2006-05-31
Let it be like that&#8230;because I think you will have plenty of time for each other while the pc is compiling ;-)

---

### Post by NinjaZombie on 2006-05-31
[QUOTE=hollywoodb]Well, from personal experience using Slackware, Gentoo, and even dabbling with LFS I finally started the search for a good distribution with good package management and polished precompiled packages.  Simple reason being that the time I spent building packages outnumbered the time I spent using them 20:1.
[/QUOTE]

That's what I was trying to tell her, that she could simply apt-get the package instead of compiling it, but she tells me that the precompiled programs are waaaay slower. That's not true, at least from my experience. She gave me a small 4GB partition on her 200 GB harddisk to install Ubuntu, and for example, firefox binary on my install starts alot faster than her custom compiled firefox. 
Ah, women...

---

### Post by elamericano on 2006-05-31
She probably wouldn't be happy with Ubuntu, since she'd run out of things to tinker with. Just get her to automate her recompiling and you'll have plenty of time.

On the other hand, if you must burst her bubble, do some benchmarking to show what performance you get from all that effort. As someone alluded to, in order for any improvement to be worth it, you'd have to use those programs long enough to save more processing time than you wasted recompiling everything.

---

### Post by linuchsan on 2006-05-31
Can't you give here an other challenge, like 3 years ago?

---

### Post by MetalMusicAddict on 2006-05-31
Ya know. Of all the "problems" to have. ;)

Right now I gotta worry about my kids possiably growing up in a Windows only world. :(

With your firefox have you added the **-turbo** switch when you launch it? [LIST]("http://www.mozilla.org/docs/command-line-args.html") of arguments. Some are outdated.

For Thunderbird I add the **-compose** and **-addressbook** to launchers in my menus. ;)

---

### Post by nursegirl on 2006-06-02
Use two separate computers and support her choice of distro. Linux is about the freedom to choose. It's awesome that she compiles from scratch...I'm way too lazy.

---

### Post by aysiu on 2006-06-02
Switch her to Gentoo instead and then after she type ```
emerge *blah*
``` you can spend time together.

---

### Post by haircut on 2006-06-03
Script kiddies :rolleyes:

---

### Post by DaveQB on 2006-06-03
Yeah, of all the problems, thats not a bad one ;-)

**MetalMusicAddict**,
Are those arguments for firefox/thunderbird ? The link you gave seems to be Mozilla and runing firefox -h doesn't show -turbo option.

---

### Post by MetalMusicAddict on 2006-06-03
The commands should work the same. Its weird it doesnt show the **-turbo** command. I get a noticable increase in speed. I think it just doesnt do a debugging. Not sure. The 3 I listed are the only ones I use.

---

### Post by Mirrorball on 2006-06-10
Tell her to move to Gentoo, it'll compile everything from source as well but it's way more practical than LFS. Or just be patient. She will get tired of compiling everything sooner or later.

---

### Post by jdusablon on 2006-06-10
<WHAP!>
I just slapped down my vote for this thread being the best one ever.

---

### Post by ihavenoname on 2006-06-12
Hahaha! sry I found this to be funny I know it really isn't but that is completly not what I would expect, I cannot even begin to understand what that might be like, I also cannot imageine what watching Xorg, GNOME, and KDE compile might do to your head! I tried Gentoo for 3 days and I got so sick of the compile outputs I deleted it and installed Arch Linux( which might also be a good alternative as it has all the optimaztions done for you, at least all the ones I would use).

 That's amazing though, that shes been able to get LFS together. I think you should truely be proud of her. You might try getting an extra computer and asking her to help you setup LFS on it as well, it might be a good project to  get together. Or maybe you can even make your own distro (although that might just cause a bigger problem). 

I'll be careful getting a girl intrested in Linux from now on

Girl: "What are Gentoo and LFS?"
Me: "No no no dear, we don't talk about those"
Girl: "why not"
Me: "shhhh we don't ask questions like that about the unspeakable distros, if it says "source based" stay faaaaaaaaaaar awaaaaaaaaaaaay"

hahah, ok I'm sry I just had to do that. 

Relax NinjaZombie I think things will come around, it could be just a phase. 

BTW I noticed you said fiancee, thus I assume that you asked her to  marry you and she said yes, thus I belive congradualtions are in order (however late) thus, CONGRADULATIONS! I wish you too the very best!

Good Luck buddy!

---

### Post by devurandom on 2006-06-12
Well, I'm a (K)ubuntu user at work (that's why I'm here) but I use Gentoo at home, and I don't think I want to switch back to a binary-based distro on my desktop PC. 

That's not so much for performance reasons (only seldomly you notice real improvements), but for flexibility. The real plus of Gentoo are USE flags - imagine them as ./configure flags+patching  automated and on steroids. Simply put, you can choose to compile your packages with (or without) a lot of options when you install them (for example, all my KDE is compiled without arts, because I hate it :) ): the Portage package manager will download and apply the right patches and configuration options at compile time, et voilà. 

Another lovely thing is that Gentoo has stable and unstable branches, but they are not sliced in "releases": stable packages are released as soon as they are tested, and your system so is always as much updated as possible. You don't have to upgrade all your system between releases -the whole concept makes no sense in Gentoo. 

OTOH, Gentoo can make you angry when upgraded packages decide not to work anymore, or when you have to recompile all your system due to a binary-incompatible GCC upgrade... sigh.

I love Ubuntu, really, since it gives me a very well functional and good Linux desktop ready-to-go at work where I and other users can feel comfortable. Gentoo is another thing -not worse, not better: different aim, different feeling.

Sorry for doing promotion for the "competitors" :) ...

---

### Post by costoa on 2006-06-13
Ok, this is coming from a guy that's been married for 15 years: **Don't even try to make her switch.** The fact that she uses LFS seems to me that she knows what's she doing and wants it her way. That's cool and that's life. My wife (a MIT grad), while she uses an account on my laptop once in a great while, has a PowerBook and loves Mac OS X. Doubt she'll switch unless Mac goes (more) evil. Find a middle ground. For us it was Samba. =) 

BTW, cjm5229's advice is a great idea and has a good chance of success.

As for spending time together just hang out, chat and listen to some music while she hacks away and enjoy it. You only have **x** days ahead of you together, spend them well and don't worry about which distro she uses. Besides, people drift from distro to distro so unless she's really happy with her version of LFS she'll move on to something else.

Could be much worse; she could love using XP and constantly making PP slides. =)

---

### Post by Adrian_b on 2006-06-19
This HAS to be a hoax.
Seriously :/

---

### Post by ihavenoname on 2006-06-19
[QUOTE=Adrian_b]This HAS to be a hoax.
Seriously :/[/QUOTE]
huh?

---

### Post by SavantEdge on 2006-07-08
> **nursegirl said:**
> Use two separate computers and support her choice of distro. Linux is about the freedom to choose. It's awesome that she compiles from scratch...I'm way too lazy.

I don't think he feels his computer is being oppressed by her version of Linux.  I think he feels his relationship with her is being oppressed by her constant compiling.

---

### Post by nanophobic on 2006-07-21
Be very careful. She'll recompile you if she doesn't like your behavior.

---

### Post by Lord Illidan on 2006-07-21
Wierd.. I would have understood if you had been the one compiling and recompiling, and her using Ubuntu...but not the other way round!
Wacko!!

Wish I had a girl like that! Probably, given my luck, I'll get one who loves macs and windows.

---

### Post by nikkiana on 2006-07-24
I second whoever raised the sentiment of trying to get her to switch to Gentoo... She's probably be bored with Ubunutu. :)

---

### Post by saphil on 2006-07-24
Turn-about is fair play!  Who says the woman has to be "using the computer for something" besides playing.  I have one machine that I primarilly use to play with edgy.  If I had a few others, I would put up copies of gentoo, LFS, solaris 10, suse, bsd, and a couple of other alphas, just for fun.  I might have to make excuses like I am "testing" the others, but that would be like saying I had 12 flavors of ice cream in the freezer because I was testing how well they worked.

---

### Post by punkinside on 2006-07-25
you should be happy, my gf uses ubuntu but anything and everything that has to be done she comes to me. For g*d's sake sudo apt-get install *something* is not that hard! still she cant bring herself to do it.

She's vindictive too we had a really bad argument some time ago and she went and got a friend of hers to install fedora on her laptop [-X  but she never got wireless working so i had to install ubuntu again!!

hell hath no fury like a woman scorned indeed!

---

### Post by SavantEdge on 2006-07-26
You know...  Usually I hear people whining about having to administer Windows machines, not Linux.

---

### Post by Mr_J_ on 2006-08-25
I've never heard of such a thing done by a woman.
Are you sure you are the male in the relation?

You could try to be romantic...

A linux detox in going to be hard to make into a success.
You're going to have to get her to admit she has a problem and that she needs to stop to give you your man time.

You know...

You need to go out and look at birds and trees, and Programming books, and holding hands and Processors...

You need tp yell out something like "Gcc sucks!" or "I'm changing back to windows!" or "You should be using ms-dos!" or "I won't Grep anymore because of you!"... You get the idea.](*,)

---

### Post by FuriousLettuce on 2006-09-01
> **Mr_J_ said:**
> You need to yell out something like "Gcc sucks!" or "I'm changing back to windows!" or "You should be using ms-dos!" or "I won't Grep anymore because of you!"... You get the idea.](*,)

> **nanophobic said:**
> Be very careful. She'll recompile you if she doesn't like your behavior.

Nice :D

---

### Post by RoamenCota on 2006-09-03
dude, cyber with her.  =D.

---

