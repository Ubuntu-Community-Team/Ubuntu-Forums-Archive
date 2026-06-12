---
title: "Why doesn't Ubuntu come with build-essential?"
date: 2006-06-09
forum: The Cafe
---

### Post by az on 2006-06-09
There is a question from Matt Zimmerman as to whether build-essential (and linux-headers-386, too, I think) should be installed by default.  So what he is proposing is not only to continue to keep the packages present on the cd, but to have then already installed when you install your system.  Currently, if you need to compile something, you need to install those packages first.  

What do non-linux-veterans think about this?


[https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/thread.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/thread.html)

starter:[https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/018552.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-June/018552.html)

(It would not occupy more disk space since the packages are already shipped on the cd - they are just not installed)

---

### Post by fuscia on 2006-06-09
in ubuntu, sure. leave it out of the 'growyourownfood' distros.

---

### Post by givré on 2006-06-09
Why could it be a security risk?

---

### Post by matthew on 2006-06-09
I think anyone who needs it is likely to be adept enough at using Linux to find the documentation and install either the build-essential package themselves or the various components. I read the mailing list thread completely and I would lean toward the opinion that is it a bit of a security risk for novices to have it installed, either because they are likely to try doing things above their knowledge level and capablility (in which case we want them asking for help and we can show them how to install the package and compile whatever they need correctly) or because of the other risks mentioned there.

On the other hand, this is among the first things I install on my systems and I would love to have it by default...yet it remains to be seen whether that convenience is really necessary when (I would imagine) only a small percentage of users actually need the package. 

I also install nethack right away, and it would be wonderful to have that by default... :)

EDIT: I forgot to mention that build-essential is included on the installation CD, it just isn't installed by default, so internet access isn't required to install it.

---

### Post by matthew on 2006-06-09
[quote=givré]Why could it be a security risk?[/quote]There are examples of worms out in the wild that look for compromised machines and compile things on them...the lack of an installed compiler thwarts that vulnerability. Granted, that's an unlikely event, but security is about minimizing risk wherever possible. Again, it's not a great risk, even on a default Ubuntu installation, but it exists. Those who are likely to need a compiler installed are also more likely to know how to install and configure a firewall and do other security enhancements as well. Just my 2 cents.

---

### Post by purserj on 2006-06-09
[QUOTE=givré]Why could it be a security risk?[/QUOTE]

I'm guessing people are worried about self building trojans. This could be mitigated against by restricting access to the build-essentials tools to certain accounts.

---

### Post by az on 2006-06-09
I forgot to mention that you can enter multiple choices in the poll.

I also forgot to add the "what is build-essential and why do I need it" option.

Matt Zimmerman is the CTO (chief technical officer) for ubuntu.

---

### Post by wmcbrine on 2006-06-09
I actually had a rootkit (came in through an SSH hole) be thwarted once by the fact that it came with libc6-dynamically-linked binaries, while the system it was trying to invade was strictly libc5. :) There's a case to be made for the notion that the "dependency hell" created by having so many different distros with varying sets of libraries is really an unintentional security feature, with the presence of a compiler being a way around that. But personally, I think it's a pretty weak case.

Having a compiler come standard with the system is, historically, part of what makes Linux so Free.

Edit: Fuscia, what do you mean by "'growyourownfood' distros"?

---

### Post by mostwanted on 2006-06-09
The Ubuntu ISOs have limited space. There must be other apps than just the build tools which deserve that space.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=mostwanted]The Ubuntu ISOs have limited space. There must be other apps than just the build tools which deserve that space.[/QUOTE]

Exactly. I'm experienced, and if I need the dev tools I know how to install them. Don't worry about guys like me.

---

### Post by Virogenesis on 2006-06-09
No one complains about mac os x not being shipped with dev tools installed.
A new user is highly unlikely to use compilers so it shouldn't matter and experienced users can just installed them easy enough.

---

### Post by kabus on 2006-06-09
[QUOTE=mostwanted]The Ubuntu ISOs have limited space. There must be other apps than just the build tools which deserve that space.[/QUOTE]

The build tools are, and have always been, part of the ISO.

---

### Post by Jucato on 2006-06-09
The build-essential and it's packages is available on the text based installers if you add them as a repository. However, it's not available in the Desktop CD, and there's no way to install it from that CD, unless it was installed (by default) by the Ubiquity installer.

I'm quite torn on the issue and couldn't vote yet. On one hand, I want it to be there, not for myself (I rarely compile), but for others who who really want to compile things. (Newbies who think that compiling is the only/best way to install things are a different matter). 

But if the "security risks" are true, then it might not be a good thing to have it installed by default, especially if you rarely or don't use it. But then again, there would still be a security risk even if it wasn't installed by default, but was installed and kept later on, right?

Hmm.....

---

### Post by az on 2006-06-09
[QUOTE=Fenyx]The build-essential and it's packages is available on the text based installers if you add them as a repository. However, it's not available in the Desktop CD, and there's no way to install it from that CD, unless it was installed (by default) by the Ubiquity installer......[/QUOTE]

Yes it is on the Desktop cd.  You install and the use the small repo on the cd.  That small repo is not available to you from the live cd session, but once you boot into your new ubuntu system, if you re-isert the live cd, you will be asked if you want to add the packages there to your list.

That repo has build-essential, linux-headers, linux-wlan-ng, usb dsl drivers, etc....

[QUOTE=Fenyx]
But if the "security risks" are true, then it might not be a good thing to have it installed by default, especially if you rarely or don't use it. But then again, there would still be a security risk even if it wasn't installed by default, but was installed and kept later on, right?

Hmm.....[/QUOTE]

It would be less of a security risk.  The intruder would probably be at more risk of being detected when trying to install the compiler.

---

### Post by Christmas on 2006-06-09
I'd vote only "No" but there is no such option. I don't know why it could be a security risk or whatever, but who wants to compile things can install the package. It shouldn't be installed by default in my opinion, the software from the repositories (including universe and multiverse) is enough.

---

### Post by aysiu on 2006-06-09
I don't see how it's a security issue.

If someone comes on these forums saying, > I'm trying to get my wireless working and need to compile this thing or > I want to install this obscure program but it says the make command is not found nobody replies > Well, we've deliberately left the build-essential package out just for you, because we know you're going to hurt yourself if you do install it. Don't compile packages from source until later, honey. That idea's ludicrous. Anyone who wants to compile from source is told > Yeah, you have to install the *build-essential* package ```
sudo aptitude update
sudo aptitude install build-essential
``` and sometimes get back the response > What if I don't have an internet connection?

---

### Post by John.Michael.Kane on 2006-06-09
Deleted...

---

### Post by az on 2006-06-09
[QUOTE=aysiu]I don't see how it's a security issue.

If someone comes on these forums saying,  or  nobody replies  That idea's ludicrous. Anyone who wants to compile from source is told  and sometimes get back the response[/QUOTE]

No.  The point is not that people can break their boxes by using the compiler.  It seems to be that an intruder can use the compiler to further propagate the vulnerability.

And no one is suggesting that build-essential be kept off the install cd.  They are suggesting to not only ship it but to install it by default.  Currently it is only shipped (present on the cd).

---

### Post by aysiu on 2006-06-09
I understand that, Azz, but when people say, "How do I install this .tar.gz?" I **never** hear forum members say, "Well, do you know that if you install the necessary program, intruders can use that compiler to further propagate themselves?"

People almost always respond, "Just install *build-essential*."

So why do they talk about it all of a sudden as if it's this big danger?

If you'll freely give someone a security risk when they ask (with no cautionary warning), why wouldn't you just give it to them to begin with?

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=azz]No.  The point is not that people can break their boxes by using the compiler.  It seems to be that an intruder can use the compiler to further propagate the vulnerability.[/QUOTE]

The solution, IMHO, is not to cripple the computer, but to beef up its security so that intruders can't get in to begin with.

---

### Post by Virogenesis on 2006-06-09
[QUOTE=aysiu]I don't see how it's a security issue.

If someone comes on these forums saying,  or  nobody replies  That idea's ludicrous. Anyone who wants to compile from source is told  and sometimes get back the response[/QUOTE]
Why do you think smoothwall doesn't include a compiler? Because it could be considered a security risk.
Mac os doesn't include a compiler as default do people complain?
The fact of the matter is IF you don't know how to install the compiler then you shouldn't be using it its as simple as that really.

---

### Post by Stormy Eyes on 2006-06-09
[QUOTE=Virogenesis]Why do you think smoothwall doesn't include a compiler? Because it could be considered a security risk.[/QUOTE]

Is that the reason the Smoothwall people give? I thought Smoothwall didn't include a compiler because it was a specialized distro that didn't need a compiler. Personally, I don't give a damn if the compiler is installed by default or not, but I think this "security risk" argument is bullshit.

---

### Post by aysiu on 2006-06-09
[QUOTE=Virogenesis]Why do you think smoothwall doesn't include a compiler? Because it could be considered a security risk.[/quote] What's smoothwall? > Mac os doesn't include a compiler as default do people complain? Mac OS doesn't include a compiler for two reasons:

1. Unlike Ubuntu, Mac has a lot of commercial binaries made for it. If Mac users want a program, they get a .dmg they can double-click. If Ubuntu users want obscure programs, they usually have to compile a .tar.gz from source.

2. Mac comes preinstalled with Mac-compatible hardware. Maybe if someone is trying to get a wireless device or dial-up modem working with Ubuntu, they might have to... compile something from scratch. If your Airport Extreme Wireless doesn't work with Mac OS X, something's wrong with your computer because it was designed to work with Mac OS X.

I just hope that the next time someone wants to ./configure make make install all the people in this thread who claim *build-essential* is a security risk tell that user, "Yeah, we could tell you the package that would help you install that, but it's a security risk. Don't install it until you're a more advanced user."

I'm just going to tell them, as I and others have always done, ```
sudo aptitude update && sudo aptitude install build-essential
``` and when they ask why it's not included, I'll tell them the truth: "I don't know why."

---

### Post by Virogenesis on 2006-06-09
[QUOTE=aysiu]What's smoothwall?  Mac OS doesn't include a compiler for two reasons:

1. Unlike Ubuntu, Mac has a lot of commercial binaries made for it. If Mac users want a program, they get a .dmg they can double-click. If Ubuntu users want obscure programs, they usually have to compile a .tar.gz from source.

2. Mac comes preinstalled with Mac-compatible hardware. Maybe if someone is trying to get a wireless device or dial-up modem working with Ubuntu, they might have to... compile something from scratch. If your Airport Extreme Wireless doesn't work with Mac OS X, something's wrong with your computer because it was designed to work with Mac OS X.

I just hope that the next time someone wants to ./configure make make install all the people in this thread who claim *build-essential* is a security risk tell that user, "Yeah, we could tell you the package that would help you install that, but it's a security risk. Don't install it until you're a more advanced user."

I'm just going to tell them, as I and others have always done, ```
sudo aptitude update && sudo aptitude install build-essential
``` and when they ask why it's not included, I'll tell them the truth, "I don't know why."[/QUOTE]

1. maybe I wish to install some obscure program maybe I wish to run the latest version of apache 

2. true but why not make it installer from a cd or dvd whats the problem with that.

aysiu why doesn't ubuntu come shipped with apache, mysql and ssh running they are useful to some.
Some might wish to run those without an internet connection.

Make it easier to install the build tools from the cd so its a win win solution.

Smoothwall 2 is a firewall designed around the linux kernel 2.4, its the firewall that was around before ipcop.
Its a cut down distro based upon security, it doesn't include wget, compilers or anything like that.
Its pretty tight security the gui is all perl scripts.

---

### Post by az on 2006-06-09
[QUOTE=Stormy Eyes] Personally, I don't give a damn if the compiler is installed by default or not, but I think this "security risk" argument is bullshit.[/QUOTE]
I'm not smart enough to say.  Read the threzad and see what people who are that smart are saying and make up your own mind.

Aysiu:  build-essential is already included.  Included and installed are two different things.

---

### Post by aysiu on 2006-06-09
[QUOTE=Virogenesis]1. maybe I wish to install some obscure program maybe I wish to run the latest version of apache [/quote] Only goes to support my argument--a lot of people need *build-essential*.

> 
2. true but why not make it installer from a cd or dvd whats the problem with that. Because it's annoying. Why not make *ubuntu-desktop* on the CD but not installed?

> 
aysiu why doesn't ubuntu come shipped with apache, mysql and ssh running they are useful to some.
Some might wish to run those without an internet connection. Because those are programs by themselves. *build-essential* is a helper program that helps you install other programs. You might as well leave out *dpkg* or Synaptic.

> 
Make it easier to install the build tools from the cd so its a win win solution. That could work, but someone has to make it happen. I think what would be a good compromise would be leaving it out, but when you try to compile from source, instead of saying "make: command not found," you get a pop-up that says, "make: command not found--do you want to install the *build-essential* package that will help you compile from source?"

Even that I think is lame, but it would be better than the way it is now. Can someone make a real case for it being a security risk? I happen to have a great deal of respect for Stormy Eyes' technical expertise, and if he thinks it's BS, I really would like to hear someone substantiate the security risk side of things.

---

### Post by John.Michael.Kane on 2006-06-09
Don't really mater if someone substantiate the security risk side of things. or not. seems you three are the end all know it all on this, and any other subject. bottom line unless it comes from you three it will be classed as BS anyway so why should someone substantiate the security risk side of things.


Just My Thoughts.

---

### Post by Virogenesis on 2006-06-09
[QUOTE=aysiu]Only goes to support my argument--a lot of people need *build-essential*.

 Because it's annoying. Why not make *ubuntu-desktop* on the CD but not installed?

 Because those are programs by themselves. *build-essential* is a helper program that helps you install other programs. You might as well leave out *dpkg* or Synaptic.

 That could work, but someone has to make it happen. I think what would be a good compromise would be leaving it out, but when you try to compile from source, instead of saying "make: command not found," you get a pop-up that says, "make: command not found--do you want to install the *build-essential* package that will help you compile from source?"

Even that I think is lame, but it would be better than the way it is now. Can someone make a real case for it being a security risk? I happen to have a great deal of respect for Stormy Eyes' technical expertise, and if he thinks it's BS, I really would like to hear someone substantiate the security risk side of things.[/QUOTE]
User breaks in, looks around decided to infect libjpeg with his own version compiles his own version, nice rootkit inside a lib file which no one would bother checking.

aysiu if you were an admin of a school would you want your students to be able to compile i know they cannot do make install but thats not the point.
Bottom line is let the user install it its not needed til its needed and until its needed no point in having it.

---

### Post by aysiu on 2006-06-09
Virogenesis, when a forum member wants to compile a program, what do you tell her?

A. I could give you the tool for this, but it's too dangerous.
B. Install *build-essential*

---

### Post by az on 2006-06-09
[QUOTE=aysiu]Virogenesis, when a forum member wants to compile a program, what do you tell her?

A. I could give you the tool for this, but it's too dangerous.
B. Install *build-essential*[/QUOTE]

A is ridiculous.

What is  being discussed, however, is whether the risk is significant enought to warrant the inconvenience to about 1 percent of users who will have to install it from the cd before they use it instead of it being preinstalled on every ubuntu box.

---

### Post by aysiu on 2006-06-09
Only 1% of users install *build-essential*?

The real question is--is it a security risk or not? If it is, people should install it, use it, and uninstall it. If not, then I don't see why everyone shouldn't have it available.

---

### Post by Virogenesis on 2006-06-09
[QUOTE=aysiu]Only 1% of users install *build-essential*?

The real question is--is it a security risk or not? If it is, people should install it, use it, and uninstall it. If not, then I don't see why everyone shouldn't have it available.[/QUOTE]
Yes & No but why should it be installed as default? 
So what a user can just compile what about in the future when we might not need to compile.
Leave it on the cd make a front end so when the cd is in the drive it loads up and gives you options to install other parts such as dev tools.

It will market itself better without a compiler. 
Why? 
Because you can clearly say that the support is blinding and use of compilers isn't needed so much. 
Ofcourse this is a load of crap but it sounds good and thats what counts.
Its a security risk as alot will compile crap from random places.

---

### Post by aysiu on 2006-06-09
And a lot will get encouraged to compile crap from random places, too.

I've spent a lot of time on these forums, and I can tell you not once have I ever seen a new user trying to compile something from source and another user saying, "You know, doing this might be a security risk. I don't know if you should install *build-essential*."

---

### Post by ranf on 2006-06-09
[QUOTE=SD-Plissken] bottom line unless it comes from you three it will be classed as BS anyway so why should someone substantiate the security risk side of things.
[/QUOTE]
Sorry? What does BS mean?

---

### Post by aysiu on 2006-06-09
[QUOTE=ranf]Sorry? What does BS mean?[/QUOTE]
It's short for b u ll s h it, an English word for "not true." Well, it's kind of an insulting way of saying something is not true.

[quote=SD-Plissken]Don't really mater if someone substantiate the security risk side of things. or not. seems you three are the end all know it all on this, and any other subject. bottom line unless it comes from you three it will be classed as BS anyway so why should someone substantiate the security risk side of things.[/quote] Who's "you three"? I hope you're not including me in that, as I don't really know what the security risks of *build-essential* are.

If those risks exist, I think we should make it a common practice to warn new users of those risks every time they try to compile something, and we should encourage them to uninstall the *build-essential* packages after compiling something from source.

But if those risks don't exist, we should just leave those mythical "risks" out of this discussion entirely.

I have yet to hear a convincing case, though, that those risks *do* exist.

Sounds like *build-essential* FUD to me... unless someone wants to explain exactly what the risk is.

---

### Post by John.Michael.Kane on 2006-06-09
ranf ask the three  who seem to know all things linux, and ignore those who they feel are not on their leavel.

Edit: you have your answer ranf.

---

### Post by LaserJock on 2006-06-09
I was just reminded by an awefully smart dev that *build-essential* has nothing really to do with users compiling programs. It is just a meta package that describes what the buildd (the scripts that build the .debs from source packages) are guaranteed to have so developers don't have to explictly depend on them. It depends on *dpkg-dev* (which you don't need to compile a program),  *gcc*, *g++* (only needed for C++ apps), *libc6-dev*, and *make*. So if you install *build-essential* you get some but certainly not all of the common build tools. What about autotools, X libraries, or even kernel headers? Surely those are used my in compiling apps by users than devscripts.

So my thought is that we should not be reccomending *build-essential* to people who want to compile a program but instead either need to explicitly list the packages or come up with some sort of ubuntu-builder meta package more appropriate to what users want.

just my $0.02

-LaserJock

---

### Post by thomashauk on 2006-06-09
Build-essential is not included for two reasons:

1)It encourages the use of the repos.
2)Promotes that ubuntu sees this method as not normally needed and hence is more user friendly.

---

### Post by Jucato on 2006-06-09
I have to agree with thomashauk on this. Ubuntu aims to be a distro more oriented towards regular destkop users (except the server version), where everything is supposed to just work (except for propriety/restricted stuff). As such, installing programs should be done easily through the repositories. 

I don't think build-essential et al should be installed by default for a number of reasons:
1. Like what thomashauk said, we should encourage the use of the repositories. This also has the side effect of dispelling fears that you have to always compile things in Linux. We're not Gentoo/Slackware. I've seen countless times where some users begin to ask questions about compiling stuff and/or why they can't compile, only to see that the exact same package and exact same version can actually be found in the repositories. Most of the time they just don't know it's available, or just don't search. I've also seen some posts where people come in here, asking how to compile, because they came in with the preconceived notion that compiling is the only way to install things. (And so they download loads of .tar.gz for that).
2. Newbies don't need to know how to use it. Well, not immediately, of course. Most of what they need can be found in the repositories. By the time they do really need it, they would know by then how to get it.
3. It can be installed from the Alternate Install CD, and if what azz said was true (I can't confirm it), from the Desktop CD as well.
4. Compiling versions of packages that are newer than the ones in the repositories might introduce some dependency problems in the future.

I'm not really sure regarding the security issues involved. I mean, if it's so much of a security issue, why would it be included (not installed) in the first place? And why would we encourage it's use, too? But the mere mention of a "security issue" is enough to make alarms go off, so unless someone could offer substantial evidence (previous incidents, reports, papers, etc), I really couldn't consider it as an issue.

---

### Post by fluffington on 2006-06-09
While I'd like build-essential to be installed by default, it's really not that big a deal when the package is right there. What annoys me more is that the live CD doesn't even have the build-essential or linux-headers-whatever packages on it. This makes it impossible for me to use the live CD, as I have to compile my own network driver (forcedeth doesn't like me, apparently), and I don't exactly have access to the repos before getting that working.

Edit: build-essential and linux-headers weren't on the live CD I originally downloaded, but the ISO has apparently been updated to include them between then and now, so you can ignore my complaint.

---

### Post by ranf on 2006-06-10
[QUOTE=aysiu]It's short for b u ll s h it, [/QUOTE]
K, I'm familiar with that.

Reminds me of this:
---
I WILL NOT USE ABBREV.

Bart Simpson on chalkboard in episode 2F33
---

---

### Post by Alpha_toxic on 2006-06-10
I say install it. No point in putting it in the CD if it is not installed...
Oh, and please remove the windows software from the CD, put there sth that we are actually going to use. This way it's just a waste... I'd suggest putting the extra kernels there (686, 686-smp, k7...), but I guess there will not be enough space for them.

---

### Post by az on 2006-06-10
[QUOTE=aysiu]
If those risks exist, I think we should make it a common practice to warn new users of those risks every time they try to compile something, and we should encourage them to uninstall the *build-essential* packages after compiling something from source.[/QUOTE]
Sounds like a good idea.  That should be mentioned on the devel maililng list discussion...


[QUOTE=aysiu]

But if those risks don't exist, we should just leave those mythical "risks" out of this discussion entirely.

I have yet to hear a convincing case, though, that those risks *do* exist.

Sounds like *build-essential* FUD to me... unless someone wants to explain exactly what the risk is.[/QUOTE]

It's all there on the mailing list thread.  Here are two quotes, see more for yourself.

Quote Matt Zimmerman:

Some arguments against this approach include:

 * Most users don't need a compiler

 * If they have already compromised a system, worms can use a compiler to
  help propagate themselves and launch attacks (and if one is installed by
  default, this is a more appealing technique for targeting Ubuntu systems)

 * We should solve the same problems in more elegant ways where possible


and


Quote:
 Anders Karlsson 	
<trudheim@gmail.com> to Lee, sounder, ubuntu-devel, Matt
	 More options	  Jun 8 (2 days ago)
On Thu, 2006-06-08 at 16:19 -0400, Lee Revell wrote:
[snip]
> If someone cracks a system don't you think they could just compile on
> their local machine and upload binaries?  I really don't understand the
> argument that having a compiler installed is a security issue.

Yes they can, and they may do even if gcc is available on the target
machine. But security practises are that you leave as few vectors open
as possible.

An example. You run httpd as the www-data user. There is a flaw in httpd
that allows buffer overflow that ultimately leads to shell as www-data
user. If gcc is available, the attacker can rapidly exploit the local
root vulnerability in the running kernel. If no c compiler (gcc), it
takes longer and is harder for the intruder to achieve his aim. Perhaps
long enough that the attackers actions are detected.

Convenience and security does not generally go hand in hand. Common
sense is not to install compilers unless you have to, as you give an
intruder tools and more vectors.

I fully agree with another poster, the Ubuntu Server install should
under no circumstances install a C compiler by default.

End Quote

---

### Post by aysiu on 2006-06-10
Well, are people really going to start telling folks it's a security risk, then, instead of just saying, "*sudo apt-get install build-essential*"?

I wish I'd known it was a security risk. I would then uninstall it right after using it to install VMPlayer.

---

### Post by Imexius on 2006-06-10
[QUOTE=mostwanted]The Ubuntu ISOs have limited space. There must be other apps than just the build tools which deserve that space.[/QUOTE]

Just make room for it then, take out some of the unnessasary things, or better yet, allow users to choose what they want to be installed like Slackware.

Build-essential should be installed by default. I know for a fact that many users point out this aspect as a fault to ubuntu.

---

### Post by patrick295767 on 2006-06-10
[QUOTE=fuscia]in ubuntu, sure. leave it out of the 'growyourownfood' distros.[/QUOTE]
  
I heavily support fuscia !!  Please leave us freedom to make our Linux Evolute by ourself.

How can people make use of their old pc with such attitudes then ? go to slackware, ... then ... :-(
  
Greetz

---

### Post by aysiu on 2006-06-10
So Imexius says many users see *build-essential*'s omission as a fault of Ubuntu.

Azz says only 1% of users need it.

Well, I've created [a poll](http://www.ubuntuforums.org/showthread.php?t=193862) to see just how useful it is.

---

### Post by Jucato on 2006-06-10
[QUOTE=aysiu]So Imexius says many users see *build-essential*'s omission as a fault of Ubuntu.[/QUOTE]
Not only our own users, but users of other distros see this as a downside to ubuntu as well.

> Azz says only 1% of users need it.
I'm sure that's not accurate.

> Well, I've created [a poll](http://www.ubuntuforums.org/showthread.php?t=193862) to see just how useful it is.
Leave it to aysiu to be able to think of a productive solution. :D

Just Voted. :D

---

### Post by GreyFox503 on 2006-06-11
I don't know much about security, but I can't help but mention this thought since I don't think I've seen it.

We're worried about including build-essential because a malicious program/intruder could run it, causing more harm, right?

If something/someone else has permission to be running the compiler on your machine in the first place, doesn't that mean security has been defeated at a much earlier stage somewhere else??

I'd be more worried about including the dangerous *rm* command.  It can delete your entire home directory.



At first I thought this debate was about whether to include build-essential on the CD.  But know that I know it's already on every Ubuntu CD, the question is, why not install it?  It's not called build-*essential* for nothing.

---

### Post by aysiu on 2006-06-11
[QUOTE=GreyFox503]
If something/someone else has permission to be running the compiler on your machine in the first place, doesn't that mean security has been defeated at a much earlier stage somewhere else??[/QUOTE] I'm with GreyFox on this.

Can someone who *does* know about security more than GreyFox and I do please explain why *build-essential* is a security concern?

A concrete hypothetical scenario would be much appreciated.

---

### Post by mstlyevil on 2006-06-11
Things are really getting heated here. Please tone it down a bit so we won't have to backyard this thread. This is a very informative thread and it would be a shame to have to backyard it because some cannot control themselves.

---

### Post by Azrael on 2006-06-11
> An example. You run httpd as the www-data user. There is a flaw in httpd
that allows buffer overflow that ultimately leads to shell as www-data
user. If gcc is available, the attacker can rapidly exploit the local
root vulnerability in the running kernel. If no c compiler (gcc), it
takes longer and is harder for the intruder to achieve his aim. Perhaps
long enough that the attackers actions are detected.
Ubuntu installs no network daemons by default, so surely you can install build-essential by default.

Besides, there are many ways to escalate user privileges. Remote buffer overflows are usually lethal anyway so I think it's silly to scapegoat gcc for this. The only propper solution is to strictly audit the source code of networking services. It's not rocket science.
> Convenience and security does not generally go hand in hand. Common
sense is not to install compilers unless you have to, as you give an
intruder tools and more vectors. Let's cancel the internet then. It's an intruder's paradise of tools and attack vectors.

The gains of installing build-essential by default far outweigh the need for mostly futile attempts at protecting rare cases of already compromised Ubuntu machines.

---

### Post by az on 2006-06-11
[QUOTE=aysiu]
A concrete hypothetical scenario would be much appreciated.[/QUOTE]
See my last post.  Two devs give two examples.  What more do you want?

Actually, if you want more, see the actual mailing list thread?  Lots of people think it's BS.  Lots don't.  The point is whether having it on the cd is convenient enough or should it be on the cd *and* installed by default.  

The debate is about whether the security risk is greater than the inconvenience.

---

### Post by aysiu on 2006-06-11
If the security risk is that great, people should be allowed to only temporarily install it, then.

After it's used, it should be uninstalled until manually reinstalled again.

And if it's not a security risk, include it. Geez. It's not 1% of users. I don't know where this percentage comes from.

> An example. You run httpd as the www-data user. Don't you think it's more likely that someone will *not* be running httpd as the www-data user but also need *build-essential* for something else?

---

### Post by Zdravko on 2006-06-12
Oh God, someone here said that most of the users don't use gcc... What are you talking? Why do I quit Windows and start Linux? To play games, maybe? No, there is only one reason for me - it is in its developing capabilities. I use g++ everyday in order to compile my programs and I start it at least 50-60 times at day. I don't know why it isn't installed by default. Instead I get games and hundreds of ugly screenshots. Please, do the humanity a favor - place a gcc package in the CD for default installation. I can't even imagine a PC without a C++ compiler - it would be useless!
The issues about security risk are BS.
People who don't need gcc (e.g. gamers) won't even notice it is installed.

---

### Post by Jucato on 2006-06-12
[QUOTE=mstlyevil]Things are really getting heated here. Please tone it down a bit so we won't have to backyard this thread. This is a very informative thread and it would be a shame to have to backyard it because some cannot control themselves.[/QUOTE]

Just trying to repeat mstlyevil's reminder.

---

### Post by maagimies on 2006-06-14
Yes it should be installed by default. Makes things much easier on the user. Newbie Linux users DO install stuff from source that they can't get from the repos because thats what's told to them: "./configure && make && make install"

About the security issues of it, I think that if a hacker even gets to the command line, the admin has already failed to secure that machine.

Even if you have to keep ssh open to the world, atleast use things like fail2ban and port knocking! And change passwords once in a while... And ofcourse keep all servers in a chroot.

---

### Post by professor_chaos on 2006-06-14
NO, build-essential should not be installed by default. 
I think one of the main goals of Ubuntu is to have a working desktop for the desktop user. It aims at being a polished distro... and only the "nessesary" packages for someone new to linux should be apart of the default install. It doesn't matter if it's 1% or 10% or 100% of users will eventually need/use compile tools. The fact is that I don't think a new-comer to linux needs build-essential, and including it as a part of the default install increases bloat. 

And if you do need it, the just "sudo apt-get install build-essential". How hard is that.

---

### Post by brentoboy on 2006-06-29
The Ubuntu-Devs email list has been kicking around the idea of adding a compiler to the default ubuntu installation.  thus making make, build, install available without having to apt-get build-essentials.

It ends up requiring about 20MB of space on the finished installation that isnt there today.  It doesnt take up any more space on the CD becuase it is shipped on there already, it just doesnt get installed unless you add it later.

There are basically two sides of the argument:
1) dont add it, because we need to keep the ubuntu attitude to be one of "just works" if there is no compiler, then we should include extensive hardware support, and have everything under the sun in the Universe repo so that people never need to install one in the first place.  In the perfect world, a non-developer shouldnt need one.

2) do add it, becuase if someone doenst need it, they wont know its there, and if they do, they will appreciate it for already being installed.  Some driver modules and other stuff that people need to get started on the first day need a compiler and why make life difficult for them.

Please comment.  I believe that if we get a strong vote requesting it, it might make edgy.  It has being heavily debated for the last 2 weeks.

---

### Post by YourDoom123 on 2006-06-29
u missed one major argument for 1... security. that's the one that keeps getting thrown around the list... 

anyway, i'm all for having it installed by default. it adds a lot of convenience to the lives of ppl who just want to add some hardware support, or install a package thts only available in a source format.

---

### Post by Senori on 2006-06-29
It's the very first thing I do when installing a new Ubuntu system.

---

### Post by brentoboy on 2006-06-29
Security was kicked around as a concern on the lists, but it was shot down as a valid reason because a compiler could be snuck in with malicious software and be used whether the system has the build environment setup or not.   Here is a quote on the subject from Matt Zimmerman (one of the senior Ubuntu  Developers)

> 
I can't really agree; I don't at all support the assertion that there is a
security concern here, and even if I did, restricting access wouldn't solve
the problem.

The usual argument that people make is that the availability of gcc makes it
easier for a worm to compile exploits, rootkits and so forth for the target
system.  This really isn't a sizeable barrier, though, and plenty of worms
are written which cause plenty of destruction without a compiler.  Some easy
ways to circumvent this "security" mechanism include:

- Including instructions in the worm for installing a compiler (I can easily
  think of a sequence of less than 10 shell commands which would get a
  compiler installed on a majority of Linux systems, regardless of which
  distribution is in use)

- It is possible (and indeed it has been done) to write exploits in a
  language for which an interpreter is likely to be available on the system
  already, such as Python.  We certainly shouldn't exclude Python because of
  this possibility, though!
  
- It's even possible (and indeed it has been done) to write a C compiler in
  Python, and to use that to compile an exploit.

- It is possible (and indeed it has been done) to ship a simple C compiler
  built for the target architecture.  It's pretty easy to build a simple
  program which will run on any 32-bit Intel Linux system, which is a huge
  majority

-- 
 - mdz


---

### Post by brentoboy on 2006-06-29
I realize that this is a duplicate poll, but the last one that was done had a few dev's on the dev-list who didnt feel like interpreting it for what it was... and it got dropped from discussion.  I figured if we had two seperate polls each with different wording--but similar results that would say a lot more than just the one.

---

### Post by henriquemaia on 2006-06-30
Well, the ones needing to use build-essential know how to install it. The ones not needing it don't care. Don't install it. Ubuntu is for all, but directed to those who don't need to install build-essential.

---

### Post by gn0me on 2006-06-30
[QUOTE=Senori]It's the very first thing I do when installing a new Ubuntu system.[/QUOTE]

Me too..

[QUOTE=henriquemaia]Well, the ones needing to use build-essential know how to install it. The ones not needing it don't care. Don't install it. Ubuntu is for all, but directed to those who don't need to install build-essential.[/QUOTE]

Although I agree with the first quote, the second one is what is the truth. If you think about it, this is meant for simplicity and easy installation and usage. 

If you want to install build-essential and compile something, do it. But if you're a new user and just switched to linux.. I'm 90% sure you won't need it, and if you do.. that's one extra step of installing it.

---

### Post by mlind on 2006-06-30
I think most of the users don't have any need for it. I don't need build stuff at all
on my another box. It's quite easy to install and I believe it's even included on the cd.

nope for me.

---

### Post by Kilz on 2006-06-30
Its on the cd but never gets installed? We are worrying about 20meg in an age of 200gig hard drives? Install it, I have read quite a few posts in the beginers section asking how to install this program that came as "tar.gz". One less thing to tell them to do. You also need it if you want to install drivers from the ATI web site.

---

### Post by .t. on 2006-06-30
You can test if it's on the Live CD by booting up the CD, opening the terminal and typing gcc. If it's not found, then it's not on the disk and won't be installed. The installation process basically involves copying the CD to the harddrive, and setting it up for your PC. If you've noticed, the CD takes up 696MiB of space on a 700MiB (standard size) disk. If it's not included, it's because it won't fit.

---

### Post by Norm 2782 on 2006-06-30
[QUOTE=gn0me]Me too..



Although I agree with the first quote, the second one is what is the truth. If you think about it, this is meant for simplicity and easy installation and usage. 

If you want to install build-essential and compile something, do it. But if you're a new user and just switched to linux.. I'm 90% sure you won't need it, and if you do.. that's one extra step of installing it.[/QUOTE]

I have to agree with gn0me here... Ubuntu is supposed to just work and provide a stable Linux desktop for people who maybe never heard of Linux before. If you want to start compiling right away after you first install, I think you'd better install Gentoo.
Besides, when compiling stuff you always need to fulfill dependicies anyway, so an extra click in Synaptic to get build-essentials and all that won't kill you.

---

### Post by ohgod on 2006-06-30
I vote for having build-essential installed by default.

"If you want to start compiling right away after you first install, I think you'd better install Gentoo."

I disagree.  I generally don't compile things that have packages available, but sometimes I'd much rather have the newest release (mplayer comes to mind).  True, installing build-essential is not hard to do, but what's the advantage of leaving it out of the default install?

"Ubuntu is supposed to just work and provide a stable Linux desktop"

Does adding a compiler reduce the stability of the system?

---

### Post by apoclypse on 2006-06-30
If you know how to compile a source package, you know how to apt-get install build-essentials. The thing i love about ubuntu is that it only install whats neccessary for a user environment and lets you add what you need later. An example, SLED (Suse Enterprise Linux whatever) is nice but it has FIVE cds, why? When I think about an enterprise os i'm thinking fast install and easy deployment, SLED is neither the installer is slooooow (has always been) and there are way to many steps and options in the way, and you have to reboot at least twice. The real pain in the *** is that all that could be avoided by only including base packages on 1 cd and letting the user add what they need later. Don't become suse please.

---

### Post by az on 2006-06-30
[QUOTE=brentoboy]
There are basically two sides of the argument:
1) dont add it, because we need to keep the ubuntu attitude to be one of "just works" if there is no compiler, then we should include extensive hardware support, and have everything under the sun in the Universe repo so that people never need to install one in the first place.  In the perfect world, a non-developer shouldnt need one.[/QUOTE]

Having kept up with the discussion, I don't really think that was the big reason to not include it.  The big reason to ship but not install by default is security.  Best security practices are to not install something which will not be used.

That argument has been kicked around a lot.  There have been excellent arguments supporting it and refuting it.  

A few people mentioned that stuff should just work and you should not need a compiler, but that is relevant to whether or not you ship the compiler or not - not whether it is *installed* by default.

[QUOTE=brentoboy]
2) do add it, becuase if someone doenst need it, they wont know its there, and if they do, they will appreciate it for already being installed.  Some driver modules and other stuff that people need to get started on the first day need a compiler and why make life difficult for them.
[/QUOTE]

Precisely, this problem targets linux veterans who are trying ubuntu for the first time.  Most people whose hardware does not work need far more guidance than locating the compiler.  

I blame the docteam.

But seriously....  what this boils down to is that there is excellent ubuntu documentation that describes the steps you need to do to compile your winmodem driver.  Only someone who is experienced with using another distro (which does install a compiler by default) will wonder why there is no compiler included.  But then again, these people should have less trouble figuring it ou anyway (since it is on the cd).

So, do you cater to those who pimp strict security-best-practices or those who are annoyed by the slight inconvenience?

---

### Post by wrtrdood on 2006-06-30
All good arguments but I see one group of users that have been overlooked.  These are those people that know just enough to be dangerous.  I've read a number of posts and answered enough simliar questions of my own to think that including this package can cause more trouble than it helps.  The typical reaction for the nearly-savvy Linux user -- especially those with experience in other distros -- is to download the tarball from somewhere else and build the software without *first checking the respositories* for compatible versions.  

Like many other here, build-essentials is one of the first additions to my systems.  I run E17 and often rebuild the kernel.  It's a *gotta have*.  But I have several years of experience using Linux and building software and know what I need to get it done.  For this type of new user we simply need better documentation explaining that development tools must be installed before they can accomplish anything.  What percentage of Ubuntu users are of this caliber?  Dunno.  But given that the distro is advertised as one for the "masses" it makes sense to keep the "gun rack" locked up until they learn more about the dangers.

---

### Post by az on 2006-06-30
I don't buy the attitude that build-essential is a "gun-rack."

The solution to what you describe is to improve the existing documentation and has nothing to do with build-essential.

---

### Post by YourDoom123 on 2006-06-30
[QUOTE=.t.]You can test if it's on the Live CD by booting up the CD, opening the terminal and typing gcc. If it's not found, then it's not on the disk and won't be installed. The installation process basically involves copying the CD to the harddrive, and setting it up for your PC. If you've noticed, the CD takes up 696MiB of space on a 700MiB (standard size) disk. If it's not included, it's because it won't fit.[/QUOTE]

build-essential IS on the desktop cd. its just not installed by default. if its on the cd, then is the extra 20mb it takes up really worth not installing it?

---

### Post by henriquemaia on 2006-06-30
This poll is a bit biased from the beginning, since most users watching and posting on this forum are build-essential users. More important than the poll itsefl is what reasonings each part has to deffend its position. As stated before, I don't see any good reason why to install it by default. 

If one knows how to use this package, one will know on how to install it (and this includes those reading howtos), so there is no problem. If one doesn't, no problem either.

---

### Post by YourDoom123 on 2006-06-30
but theres also no good reason not to install it. by autoinstalling it, you bring a tiny convenience to the users who do need it. and no inconvience to anyone. this is just one less step for someone to mess up on, and hose their system.

---

### Post by Lord Illidan on 2006-06-30
From experience, most of the users who are compiling ndiswrapper over here know that they need to compile, but they get confused when it doesn't work, thus we have to tell them to install build-essential.

I say install it by default. If it is already included, then what is stopping you?? It is more convenient for the majority, and for the ones who don't need it, it won't affect them negatively either.

---

### Post by ronb on 2006-06-30
I just tried to compile xvidcap. I got an error message that said that I did not have a C compiler.  According to synaptic it looks to me like I have gcc but not build-essential. When I read the description for build-essential, I don't see why I need it to compile xvidcap.

Do I have a compiler? Do I need build-essential for xvidcap? 

This isn't urgent, but I'm just wondering?

Thanks for any help.

---

### Post by Turgon on 2006-06-30
We shouln't have to compile in 2006 so I vote no. I havn't used it for a long time and it is not rally that hard to install later anyway if anyone should need it.

---

### Post by VRWarper on 2006-07-01
Including build-essentials is an absolutely horrible idea for something like ubuntu. The majority of the users will not compile stuff on their own. If they do get around to compiling, then apt-get install build-essentials is probably not a problem. The security issue is just silly. The space issue is indeed the biggest concern. Of course, if we move the distribution to DVD or even bluray/hddvd, then fine, stuff all you want. However, as long as we stick to a single cd, every megabyte counts. 20MB is already 3% of the total amount of space on an average 700MB disk.

---

### Post by drizek on 2006-07-01
[QUOTE=ronb]I just tried to compile xvidcap. I got an error message that said that I did not have a C compiler.  According to synaptic it looks to me like I have gcc but not build-essential. When I read the description for build-essential, I don't see why I need it to compile xvidcap.

Do I have a compiler? Do I need build-essential for xvidcap? 

This isn't urgent, but I'm just wondering?

Thanks for any help.[/QUOTE]

you need more than just a compiler. build-essential includes most of the programs youre going to need in order to compile something. you will also probably need some -dev packages for x.org. If you get errors compiling go back and look for x.org-dev(or similar) and that will probably fix it.

---

### Post by aysiu on 2006-07-01
I have yet to see any of these "security" advocates actually warn a user about the supposed security risks before saying > Oh, just install *build-essential* If it is a **real** security risk, people should be warned. If it isn't, then I don't see why it shouldn't be installed.

Yes, people who can compile from source can easily ```
sudo aptitude update
sudo aptitude install build-essential
``` but that argument's lame because those people also never have to do that on other Linux distros, so this just confuses them.

And an ordinary user can Add/Remove Programs to get OpenOffice or Rhythmbox. It's not that hard. So why are those included?

Just saying that something is easy to add on doesn't mean it should not be included.

---

### Post by aysiu on 2006-07-01
[QUOTE=VRWarper]The space issue is indeed the biggest concern. Of course, if we move the distribution to DVD or even bluray/hddvd, then fine, stuff all you want. However, as long as we stick to a single cd, every megabyte counts. 20MB is already 3% of the total amount of space on an average 700MB disk.[/QUOTE] Actually, it's not an issue at all, since *build-essential* is already taking up space on both the Desktop and Alternate CDs. It is already on the CD, but it's not installed.

---

### Post by drizek on 2006-07-01
I think we should get rid of firefox and OOo for windows from the livecd. That will shave off 100-200mb

---

### Post by K.Mandla on 2006-07-01
Add it. Those who want it will have it on hand, and those who don't want it probably won't even know it's there.

---

### Post by aysiu on 2006-07-01
[QUOTE=K.Mandla]Add it. Those who want it will have it on hand, and those who don't want it probably won't even know it's there.[/QUOTE]
Exactly how I feel.

If it's not a security issue, and it's already taking up the space, why not just install it? I never use *build-essential*, but I wouldn't mind if it were there.

Anyone for whom the installation is a space issue wouldn't be doing a regular installation, anyway--probably some kind of modified server install with x-window-system-core and some other custom packages.

---

### Post by .t. on 2006-07-01
I agree; the other day, the Desktop CD installed Ubiquity to my harddrive. I don't need to install once it's installed. If it installs the installer, why shouldn't it install the compiler?

---

### Post by drizek on 2006-07-01
[QUOTE=aysiu] I never use *build-essential*, but I wouldn't mind if it were there.[/QUOTE]

Its that attitude that made distros like mepis so bloated. From the start ubuntu tried to cater to the majority, and make it as easy as possible for the minority to install the things they need. Ubuntu should come with a web browser, an IM client, an image editing app, an office suite, a media player, a music player, a cd burner and little else.

---

### Post by aysiu on 2006-07-01
I'm not saying we need KWeather and the Aquarium applet and three text editors.

*build-essential* is needed by a lot of people--not just power users who like to use it for fun but also normal people who may need it to get the latest versions of software, who need to set up wireless or dial-up, or who need software outside the repositories.

Sad as it is ./configure make make install can be part of even a new user's experience.

At least *build-essential* doesn't run in the background. Run BUM and see just how much bloat Ubuntu already has. There were quite a few services I had to turn off to speed up my boot time.

---

### Post by jasongrieves on 2006-07-01
[QUOTE=aysiu]I'm not saying we need KWeather and the Aquarium applet and three text editors.

*build-essential* is needed by a lot of people--not just power users who like to use it for fun but also normal people who may need it to get the latest versions of software, who need to set up wireless or dial-up, or who need software outside the repositories.

Sad as it is ./configure make make install can be part of even a new user's experience.

At least *build-essential* doesn't run in the background. Run BUM and see just how much bloat Ubuntu already has. There were quite a few services I had to turn off to speed up my boot time.[/QUOTE]

I completely agree.  There is a big difference between having background services or multiple apps performing the same function.  Not having simple build tools on a Linux box is almost blasphemy.  I can't tell you how many users I have put on Ubuntu who go "ummm why the heck are building tools installed?  Isn't that half of what Linux is about?"

---

### Post by brentoboy on 2006-07-01
[QUOTE=drizek]From the start ubuntu tried to cater to the majority.[/QUOTE]

If that were true, they would install build-essential by default.  It seems from both of the threads on the topic, a huge majority are in favor.

---

### Post by aysiu on 2006-07-01
The largest minority of users here prefer Thunderbird to Evolution, but Evolution remains the default. Ubuntu does not cater to the majority.

**Edit**: Actually, [it's the majority](http://www.ubuntuforums.org/showthread.php?t=190461)--not the largest minority.

---

### Post by az on 2006-07-01
[QUOTE=brentoboy]If that were true, they would install build-essential by default.  It seems from both of the threads on the topic, a huge majority are in favor.[/QUOTE]
I would say that is biased.  People who don't need to use it nor care about it don't even know what it is and so would ignore these threads.

---

### Post by aysiu on 2006-07-01
[QUOTE=azz]I would say that is biased.  People who don't need to use it nor care about it don't even know what it is and so would ignore these threads.[/QUOTE]
And also wouldn't give two s its if *build-essential* were installed. So just install it and have everyone happy or ignorant.

---

### Post by az on 2006-07-01
[QUOTE=aysiu]And also wouldn't give two s its if *build-essential* were installed. So just install it and have everyone happy or ignorant.[/QUOTE]
I see your point.  The only thing that nags at me is the *possibility* of going against best security practices.

When you are dealing with a few million desktops, caution is good.  If only shipping but not installing a compiler makes Ubuntu that much less of an apealing target, then I agree with it.  If a vulnerability needs to do a few more steps in ubuntu before it can work, that's good.

Not to mention that there is only a finite number of people who are comfortable with other linuxes and who would expect the compiler to be there.  Ubuntu is the most popular distro - it's only a matter of time before everyone knows where the compiler is and installing build-essential becomes less of an annoyance.

The Ubuntu documentation is clear on installing build-essential.

At the rate Ubuntu is growing, I think the number of people who would benefit from this cautious aproach will outweight the annoyance to a relatively small number of people.

---

### Post by mlind on 2006-07-01
One possibility is to add "express" option to installer, where user could select
additional pacakges on to install. Then everybody would be happy.

---

### Post by aysiu on 2006-07-01
If this security threat is real, how about publicizing that?

It's only in discussions like these that the idea of *build-essential* being a security threat comes up. Nowhere else on these forums have I ever seen it even mentioned as in any way insecure.

Ideally, instead of ```
bash: make command not found
``` you'd get some kind of prompt to install *build-essential* with a note that it can be installed from both CDs or online repositories.

Barring that, it should just come installed.

---

### Post by drizek on 2006-07-02
OK i think mlind has come up with the best solution. 

Just add a little checkbox in the installer that allows you to install them off the cd, with a little note about any possible secuirty issues and what exactly build-essential is.

---

### Post by slavik on 2006-07-02
I would like to suggest a ubuntu-dev mwetapackage, that installs various IDEs and compilers and such ...

---

### Post by brentoboy on 2006-07-03
azz,
I think you might have convinced me here.

Ubuntu "just works" without a compiler.  Which means the official answer to getting any particular thing working doenst generally require a compiler.  Becuase of this, many things are easier in ubuntu than other distros.

if it is a potential security risk, simply becuase "best practices" make it such, even if exploitation is not obvious, at least we are a step ahead of other distros who install it by default.  If an exploit is circulated, ubuntu users who never installed it will be safe, and those who did install it should be a little more keen on finding and fixing security problems anyway.

the only people who miss it are veterans from other distro's, and they would often default to a compiler without even enabling universe to add their favorite window manager just because they dont read the directions in the first place.

I still plan on adding it to all my systems after a fresh install, but I no longer really feel like everyone should get it regardless.  And I would welcome the change, but maybe it wouldnt benefit the community as much as I believed it would.

---

### Post by brentoboy on 2006-07-03
[QUOTE=drizek]OK i think mlind has come up with the best solution. 

Just add a little checkbox in the installer that allows you to install them off the cd, with a little note about any possible secuirty issues and what exactly build-essential is.[/QUOTE]

this was shot down in the dev-mailing list already.  They dont want to present any questions to new users that dont need to be asked.  I could see the expert isntall offering an option, but I doubt it will becuase it is inherited from debian, which installs it by default, so adding that quiestion probably wont ever happen.

-b

---

### Post by aysiu on 2006-07-03
[QUOTE=brentoboy]this was shot down in the dev-mailing list already.  They dont want to present any questions to new users that dont need to be asked.  I could see the expert isntall offering an option, but I doubt it will becuase it is inherited from debian, which installs it by default, so adding that quiestion probably wont ever happen.

-b[/QUOTE]
How about my proposal, then? When you try to *make*, instead of ```
bash: make command not found
``` There should be something like ```
make requires *build-essential*--do you want to install that now? [y/n]
``` By the way, for those of you who consider it a security issue, [here's a perfect opportunity for you to explain the risk to a new user installing *build-essential*](http://www.ubuntuforums.org/showthread.php?t=208549).

---

### Post by brentoboy on 2006-07-03
that was also considered on the dev email list.  but to do it right, it would have to handle configure and other things as well.

I dont remember any particular complaints against it in the email list, it just kind of got dropped.  maybe azz remembers better.

this does address the "its a documentation issue" because then the documentation gets presented when it is needed.

---

### Post by aysiu on 2006-07-03
[QUOTE=brentoboy]that was also considered on the dev email list.  but to do it right, it would have to handle configure and other things as well.[/quote] I'd rather it be done 90% right than 0% right, if we can't do 100%.

Most of the time when *build-essential* is recommended, it's because someone tries to issue the ```
make
``` command and finds out the command is not found.

By the way, [here's yet another opportunity to explain the security risk that supposedly exists.](http://www.ubuntuforums.org/showthread.php?t=208326)

---

### Post by Kiddalee on 2006-07-03
Yes, this would be excellent.  I am currently trying to find that thing because my Winmodem drivers keep whining about it, and I haven't a clue where it is.  (If that's not what I'm looking for, it would be nice at least to have it easily on hand so I can eliminate it as a possible help for me.)

---

### Post by aysiu on 2006-07-03
[QUOTE=Kiddalee]Yes, this would be excellent.  I am currently trying to find that thing because my Winmodem drivers keep whining about it, and I haven't a clue where it is.  (If that's not what I'm looking for, it would be nice at least to have it easily on hand so I can eliminate it as a possible help for me.)[/QUOTE]
First of all, keep in mind that some people here consider it a security risk, for whatever reason.

Pop in your Ubuntu installer CD and paste these commands in the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by aysiu on 2006-07-06
Another great opportunity [right here](http://www.ubuntuforums.org/showthread.php?t=209949) for the "security risk" folks to let a user know about the risks.

---

### Post by aysiu on 2006-07-08
[Here](http://www.ubuntuforums.org/showpost.php?p=1229714&postcount=11)'s yet another opportunity to talk about the supposed security risks.

Apparently the "security risks" are important only in theoretical discussions about excluding packages from the default installation.

When it comes to people actually *apt-get*ting or *aptitude*ing the package, all of a sudden it's not a security risk...?

Hey, you security people, where are you when someone's *actually* installing *build-essential*?

**Edit**: Thanks to SD-Plissken for actually putting money where the mouth is.

---

### Post by Iandefor on 2006-07-08
From a security standpoint, it seems to me that it wouldn't be such a bad thing to include. It was mentioned that a piece of malware could easily use the packages in build-essential to compile malicious software. I wonder why it would bother to compile malicious software- precompiled binaries would be harder to detect, since compiling is a really noticeable process. Either way, the only way it would really be able to do any serious damage is if the user granted sudo priveleges... and at that point, it becomes the user's fault if they're not cautious enough to wonder why the hell a sudo box just popped up when they're not doing anything administrative.

From a perspective of bloat, Ubuntu's already plenty bloated. Look at all the services that get installed by default for maximum compatibility- laptop utilities, stuff to handle bluetooth, two different logging daemons, two different scheduling daemons. I hardly think a metapackage that installs software that the user has to specifically invoke would cause any problems.

From a perspective of marketing, worrying about what kind of impression including build-essential is going to leave is like worrying about the impression it leaves when you include arcane commands like awk, grep, lspci, and so on.

I don't particularly care if it gets installed by default or not. I already install a ton of stuff and remove a ton of stuff immediately after install, and one extra metapackage doesn't make much difference to me, but none of the arguments against it really hold water.

---

### Post by aysiu on 2006-07-08
> **Iandefor said:**
> 
From a perspective of marketing, worrying about what kind of impression including build-essential is going to leave is like worrying about the impression it leaves when you include arcane commands like awk, grep, lspci, and so on. Never mind the fact that to the novice who doesn't use *build-essential*, the package is practically non-existent. I see HP, CUPS, and all the Bluetooth stuff loading up when I boot. I don't see "loading *build-essential* tools."

If they were included by default, those who used it would be happy they didn't have to install it. Those who didn't use it wouldn't even notice it was there.

---

### Post by Iandefor on 2006-07-08
> **aysiu said:**
> Never mind the fact that to the novice who doesn't use *build-essential*, the package is practically non-existent. I see HP, CUPS, and all the Bluetooth stuff loading up when I boot. I don't see "loading *build-essential* tools."

If they were included by default, those who used it would be happy they didn't have to install it. Those who didn't use it wouldn't even notice it was there. My thoughts exactly.

---

### Post by mips on 2006-07-09
I personally don't mind either way. I install them by default after I do a fresh install as there always seems to a point at which you need them.

The fact that they are on the alternate install cd is good enough for me, if they can be added to all the iso's, space permitting, then that would be fine. At least this way you can get to them without a net connection.

---

### Post by aysiu on 2006-07-22
This is seriously ridiculous.

People talk about how much of a potential security risk *build-essential*, and yet when someone wants to ./configure make and all that, the first thing people say is ```
sudo apt-get build-essential
```

Still the "security" people are strangely silent.

Here's another one:
[http://www.ubuntuforums.org/showthread.php?t=220984](http://www.ubuntuforums.org/showthread.php?t=220984)

---

### Post by John.Michael.Kane on 2006-07-22
aysiu so at the veryleast when one tells someone howto: install **Build-essential** they should include a statment that installing is at ones own risk or remove build files when done?

---

### Post by aysiu on 2006-07-22
Well, frankly, I don't see it as being a significant security issue at all, so I don't think people should mention it.

But since certain forum members made such a big stink of it being a security risk, don't you think they'd want to hope on to those threads and say something about it?

---

### Post by Iandefor on 2006-07-22
> **aysiu said:**
> This is seriously ridiculous.

People talk about how much of a potential security risk *build-essential*, and yet when someone wants to ./configure make and all that, the first thing people say is ```
sudo apt-get build-essential
``` 
Still the "security" people are strangely silent.

Here's another one:
[http://www.ubuntuforums.org/showthread.php?t=220984](http://www.ubuntuforums.org/showthread.php?t=220984) I don't want to sound rude, aysiu, but why did you feel the need to revive this thread? Seems to me it had sort of become a non-issue.

---

### Post by aysiu on 2006-07-22
I just don't like people using an argument that they don't really believe in.

If people really believed *build-essential* was a security risk, they'd be telling that to new users.

Apparently, it was just a flimsy excuse for not including it in the default installation (for whatever other reason... I can't imagine what it is).

I'm just blowing off steam. Some people are great about talking about protecting users in theory, but when it comes to helping actual users... nothing.

You can lock the thread if you want. I've ranted. I'm done.

---

### Post by Iandefor on 2006-07-22
> **aysiu said:**
> I just don't like people using an argument that they don't really believe in.

If people really believed *build-essential* was a security risk, they'd be telling that to new users.

Apparently, it was just a flimsy excuse for not including it in the default installation (for whatever other reason... I can't imagine what it is).

I'm just blowing off steam. Some people are great about talking about protecting users in theory, but when it comes to helping actual users... nothing.

You can lock the thread if you want. I've ranted. I'm done. Well, it seems to me that if it's a topic people want to discuss further, it's hardly fair to close the thread if it isn't violating the forum policy, and, if no one cares, they won't respond and it'll sink back into the depths. I can also understand wanting to blow off steam, and I'll let pass a comment or two that seem a little "on the edge" of the forum policy. But I shan't be making a habit of it.

---

### Post by Mrmental on 2006-09-14
I'm kind of a Linux dilletante, but when I first learned to use linux, there was no Ubuntu, and I didn't know how to use apt. I had to learn to do everything on the command line, from tarballs. In retrospect, if I had found out about apt-get earlier, my life would have been a lot easier, but then I would never have learnt the core command line skills that I think everybody who uses linux should learn. It's not an elitist thing, I think, it's just one of those skills you need. Without make, how are people going to learn how to help themselves when, say, the repositories are down?
make, and by extension, build-essential are good things to have; because in using them, you learn about all sorts of useful things like dependencies, versions and libraries.
Sam B

---

### Post by ankursethi on 2006-11-17
I think build-essential should be included by default in Feisty. The compilers are quite an important part of any distro because there are several bits of s/w floating around which require compilation. I don't think I should need to apt-get something that basic. It's not very big and it can probably be squeezed into the CD.

What say?

---

### Post by s_h_a_d_o_w_s on 2006-11-17
I agree, I alwys end up installing it anywaze. They should have a list of programs youwant whenn your installing so you would'nt have to install evolution etc. and have build-essential.

---

### Post by christhemonkey on 2006-11-17
This has been discussed many a time before.

It is still included on the cd, so it is possible to install it from the cd, is that not good enough?

---

### Post by justin whitaker on 2006-11-17
> **christhemonkey said:**
> This has been discussed many a time before.

It is still included on the cd, so it is possible to install it from the cd, is that not good enough?

Using that rationale, why not just include the proprietary drivers, and not install them by default?

---

### Post by int on 2006-11-17
> **christhemonkey said:**
> This has been discussed many a time before.

It is still included on the cd, so it is possible to install it from the cd, is that not good enough?

no, it's better to be installed by default.

---

### Post by amiga_os on 2006-11-17
> **int said:**
> no, it's better to be installed by default.

+1... the only reason I can think of not installing it by default is that there is no room on the CD.  However if it's already included on the CD then why on earth isn't it installed by default?

It took me ages as a noob to figure out why I couldn't compile software I'd downloaded... the fact that it was on the CD was pointless 'cos this is the first I've heard about it, and I've always installed build-essential via the repos.

---

### Post by earobinson on 2006-11-17
Personally I don't think we should put anything but what is needed to give "an average" windows user (think your mother) a seamless out of the box experience. If your going to be using the build-essential's you are able to do a ```
sudo apt-get build-essential
```.

But thats just my 2 cents

---

### Post by christhemonkey on 2006-11-17
> Using that rationale, why not just include the proprietary drivers, and not install them by default?

As i recall, and correct me if im wrong, nvidia-glx was also included on the cd by default?

---

### Post by ankursethi on 2006-11-17
First time I'm hearing of build-essential being on the CD. Don't know about nvidia-glx, though.

---

### Post by Amaranth on 2006-11-17
Everything needed to build kernel modules is already installed as of edgy. What is in build-essential that you need that isn't installed by default?

---

### Post by doobit on 2006-11-17
build-essential can be a security risk, just like having any dev package in there. To maintain a higher level of security, it's better that it not be default for the sake of noobees who could be compromised by it.

---

### Post by Akoluth of Nandus on 2006-11-17
> **doobit said:**
> build-essential can be a security risk, just like having any dev package in there.

Why?

---

### Post by Amaranth on 2006-11-17
That argument is no longer valid, edgy already installs gcc.

---

### Post by leech on 2006-11-17
The only logic I can see in having the development tools on there by default (which this is the first I've heard they were on the CD anyhow, I mean honestly, gcc doesn't do much good if you don't also have any development libraries on there, though build-essential will let you compile a kernel in which case I can definitely see where that would be great to have on the CD, but not necessarily installed by default).

Here is my logic in this.

Let's say you are just an average monkey that works at Nasa installing software on a computer.  You pick up Ubuntu, put it in, go through the simple installation, and now you're happily monkeying around with the Gimp.

On the other hand, let's say you're installing Linux for a friend who just bought a brand new computer and can't stand Vista.  Oh, what's that?  The Network card doesn't work in Ubuntu out of the box, but does come with a Linux driver on the CD (I was shocked too, actually).  So if you don't have an extra network card floating around (fortunately I did), you could install the build-essentials and the kernel-headers and compile the driver.  

Very useful.

For the record, he didn't have Vista on there, I set up a dual-boot for him.  Told him he'd be safer browsing his porn in Linux :D

Leech

---

### Post by Amaranth on 2006-11-17
edgy (and feisty) already install everything needed to build kernel modules.

---

### Post by doobit on 2006-11-17
> **Akoluth of Nandus said:**
> Why?

Because it allows a hacker to modify your operating system. 
OK, it's a weak arguement, but it's the original reason for not including dev apps in a default distribution.

---

### Post by dpw2atox on 2006-11-17
i dont think it should even be included on the cd, it takes up a lot of space that could be otherwise better utilized. i mean honestly the only thing i compile is my nvidia drivers as they require the 9xxx drivers to work on my card and once ubuntu packages them i wont even compile that. typical home users dont need to compile so why waste the space?

---

### Post by o_fortuna on 2006-11-17
> Because it allows a hacker to modify your operating system.
OK, it's a weak arguement, but it's the original reason for not including dev apps in a default distribution.

? Hackers would still need root privaledges. If they have those, then they can install build-essential themselves, so including it by default is not changing anything. Having a compiler on your system is absolutely not a security risk.

That said, I don't think having build-essential is necessary for default desktop systems -- it's easier to just install .deb packages. And like Amaranth said (3 times), you can build kernel modules with the default install.

---

### Post by stoffe on 2006-11-17
I'm always installing them, but I don't think they should be there by default. However, it wouldn't be a bad thing if the system could detect when doing something common that requires them and tell me what I am missing, because that had me stumped a few times when I was beginning Ubuntu, coming from other distros. Just telling me the name of the package would be sufficient (much like the ideas about informing what packages are needed when a codec or unpacker etc is missing). It could help people that wants to build things but don't know about Debian/Ubuntus naming system.

---

### Post by hod139 on 2006-11-17
This has been asked many times, a thread with an identical title and poll already even exists: [http://ubuntuforums.org/showthread.php?t=206348](http://ubuntuforums.org/showthread.php?t=206348)
I refer you to that thread.

---

### Post by montgoej on 2006-11-17
I have to install build-essential every time I install Ubuntu, even for friends.  I compile a lot of my software, more than just the kernel, and build-essential is...well...essential, so I voted yes

---

### Post by ahaslam on 2006-11-17
> **earobinson said:**
> Personally I don't think we should put anything but what is needed to give "an average" windows user (think your mother) a seamless out of the box experience. If your going to be using the build-essential's you are able to do a ```
sudo apt-get build-essential
```.

But thats just my 2 cents

While I agree with what you're saying, at some stage most people want to install something that's not in the repo's. Including the build essential package just makes things that bit easier for noobs.

Either way I'm not all that bothered but I voted for it, purely out of convenience.

Tony.

---

### Post by aysiu on 2006-11-17
[quote=hod139]This has been asked many times, a thread with an identical title and poll already even exists: [http://ubuntuforums.org/showthread.php?t=206348](http://ubuntuforums.org/showthread.php?t=206348)
I refer you to that thread.[/quote] I've merged this with the other thread (with almost exactly the same name) to give some historical context to the discussion.

Personally, I'm in favor, but I know the developers have discussed this extensively and decided against it being in by default.

It is, however, available for installation off both the Desktop and Alternate CDs.

---

### Post by gcsoares on 2006-11-17
no way, every package you want you can google for "nameofthink ubuntu .deb", someone just compiled it and packaged...  

if you wanna be the guy who packaged, so won't be hard for you to past "sudo apt-get install build-essential" in you xterm...   

put this kind of package w/ ubuntu will just force 90% of the user to download a larger file and will never use this feature, while those who use can easily download the separeted package any time...

---

### Post by aysiu on 2006-11-18
You're already downloading *build-essential*, whether you install it or not. It's on both the Desktop and Alternate CDs.

---

### Post by msak007 on 2006-11-18
Personally I don't really have a strong opinion on either side of the argument and either option is OK. If it makes life easier for newbies, install it by default (although I'm surprised at how many people have to compile packages and don't use the repos). If it's such a big security risk, don't install it by default. While it is one of the first packages I always install, I usually have some other dev packages to install along with it because I'm installing the compiler for a specific reason or app so it's not too much of an inconvenience. I can see the argument for it if a majority of users install it, and some don't have Internet out of the box and need it to compile a new kernel or wireless driver.

IMHO a better option than including certain (seemingly) controversial packages by default would be to have 2 options for installing, just like the partitioner - simple or manual. The simple installer installs the default DE / desktop metapackage (the way it's done now), and the advanced / manual installer would let you pick and choose the packages you want off the CD (or possibly install packages from the repos if you are online at the time of the install). The users that really need and use build-essential would most likely be using the advanced installer anyway and can choose it for inclusion.

---

### Post by Canis familiaris on 2007-01-17
I think the build essential package is very essential for any user in Ubuntu. Thus I conduct a poll that how many users would like the build-essential package to be included in Ubuntu by default install.
Posting this thread, i hope that build-essential package is included by default in Feisty Fawn.
After all so many programs have to compiled from source!

---

### Post by stivani on 2007-01-17
I don't think it should be installed by default. Some people who don't know how to compile from source will not need it. Experienced users can easily download and install it.
The one-CD install with default package selection is in my opinion a good thing.

But it would be great to have an alternative for experienced users: I would like to see an advanced package selection option where you can select/deselect  packages (for example dev-packages). An install DVD like Fedora or OpenSUSE would be great :D .

---

### Post by Canis familiaris on 2007-01-17
It wont really harm new users on including the build-essential package. Not only geeks, but also newbies do require them. Some programs are in fact much easier to install by source than by apt-get, etc. (those beyond the standard repos, i mean). Source code apps can be used in any platform and of course build-essential includes programming tools/compilers of C,C++,Python,etc.

---

### Post by Canis familiaris on 2007-01-17
Another thing to be noted is the fact that Ubuntu is made for Human Beings and the most of the computers especially in Asia and Africa are devoid of a decent internet connection. Most of the linux programs distributed via CDs are in source and need to be compiled and then install.
How can those devoid of an internet connection can use these programs?
Linux is itself open-source and it's open-source model itself commands that basic programming tools like build-essential are included in Ubuntu by default.

---

### Post by frodon on 2007-01-17
If you have build-essential by default it will be easier for hackers to execute and compile malicious softwares on your box. So my answer is no for security reasons.
Besides it's not that painful to type "sudo apt-get install build-essential" in case that you need it ;)

---

### Post by Canis familiaris on 2007-01-17
It could be disabled by default and made easy enough to enable it.
If not installed by default, at least should be installed easily via CD  (atleast for those who do not have internet connection.)

---

### Post by Canis familiaris on 2007-01-17
> **frodon said:**
> If you have build-essential by default it will be easier for hackers to execute and compile malicious softwares on your box. So my answer is no for security reasons.
Besides it's not that painful to type "sudo apt-get install build-essential" in case that you need it ;)
Perhaps! but if it's by default disabled and there could a wizard in the Programming in Applications Menu/KMenu which will set up build-essential without downloading from net and also warning users about security. ;)

---

### Post by lotusleaf on 2007-01-17
No, for security reasons

---

### Post by Canis familiaris on 2007-01-17
Why can't the make-essential package programs be made such that they prompt for user password(not root password) before compiling files or scripts ?
It's surely is possible!!!

---

### Post by saulgoode on 2007-01-17
Of course they should be included. This would encourage users to contribute to Ubuntu by building packages that aren't in the repositories.

---

### Post by patwack on 2007-01-17
isn't build-essential already included on the cd but not installed by default? i thought it was but could be wrong

---

### Post by v8YKxgHe on 2007-01-17
I don't think it should be included by default, for security reasons. Another thing is if you need build-essentials to compile a program you are most likely going to need to download additional dev files anyway. Well if your not gonna know how to install build-essentials, how are you going to know what additional dev files to install? 

That didn't really make sense :-D - I can't explain it any other way lol.

---

### Post by ssam on 2007-01-17
> **patwack said:**
> isn't build-essential already included on the cd but not installed by default? i thought it was but could be wrong

i think that is right (atleast it used to be the case, unless things have changed with the live cd installer).

> No, for security reasons

is there anything you could do with it that you could not do with an interpreted language like bash, perl or python (which are all installed by default)?

---

### Post by Arisna on 2007-01-17
> **ssam said:**
> is there anything you could do with it that you could not do with an interpreted language like bash, perl or python (which are all installed by default)?

Or with a binary, for that matter?

---

### Post by lukew on 2007-01-17
I hat the fact that ubuntu comes with so much and actively remove things once insatlled. It drives me crazy about some of the stuff i do not need and can not insatll Obviously I install a lot more than it ships with but minimalistic is they way!!

---

### Post by zerhacke on 2007-01-17
To those worrying about security reasons - the same user can connect to a third party repository and have the same security issues.  If you're going to use security as the ballast in your arguments you have to apply it evenly to both sides, just like in algebra.  Sure, build-essential can introduce security concerns with a user who doesn't know what they're doing but trying it anyways, but the same user can get the same results faster by apt-get.

---

### Post by MrHorus on 2007-01-17
> **Anurag_panda said:**
> I think the build essential package is very essential for any user in Ubuntu.

It's also essential for any cracker who breaks into your machine to compile and install exploits and root kits.

The point why many distributions ship without a compiler by default is that if a user account is compromised then there usually is a limited amount of damage that can be done with what is installed but if a compiler is there then they can compile and execute pretty much anything they want.

---

### Post by MrHorus on 2007-01-17
> **zerhacke said:**
> To those worrying about security reasons - the same user can connect to a third party repository and have the same security issues.  If you're going to use security as the ballast in your arguments you have to apply it evenly to both sides, just like in algebra.  Sure, build-essential can introduce security concerns with a user who doesn't know what they're doing but trying it anyways, but the same user can get the same results faster by apt-get.

You need root privilages to install anything with apt-get and I turn off sudo and use different passwords for user accounts and root accounts.

---

### Post by rai4shu2 on 2007-01-17
I voted no because it is redundant. The build-essential package and its dependencies are included on the CDs, so they are not out of reach, and if for some weird reason this makes it impossible for you to use then you have no business using it in the first place.

---

### Post by Bloch on 2007-01-17
I voted no. This is what often happens: A new users hears about some interesting software and downloads "it" not really knowing if "it" means the debian package, a binary installer or the source. Often they get the source and find the instructions enclosed: "Type ./configure and then make then make install . . check you have the libxyz package etc"

I have gone down that road and I think I have successfully compiled about 1 in 5 times. The latest thing I tried to compile was gpaint. I am at ease on the command line, I know how to use apt-get and about dependancies and versions etc. Even so, getting stuff to compile is a dark art for me.

But in any case any (opensource) software which is really useful is available as a package. 

Compiling is no longer a necessary skill for a linux user.

---

### Post by qalimas on 2007-01-17
I say yes.  Definitely.

My reason is that when I put Kubuntu on my girlfriend's computer, I needed the most up to date version of ndiswrapper, which I had to compile from source.  I had it on my jump drive, luckily, but I couldn't compile it on her computer.  I had to go get my laptop, download the packages, install them, then compile ndiswrapper.

Would have saved me a trip home and back if it came with build-essential ;)  (I thought the newer Ubuntu's did, so I didn't think anything of it at the time...)

---

### Post by FLPCGuy on 2007-01-17
> **Anurag_panda said:**
> Another thing to be noted is the fact that Ubuntu is made for Human Beings and the most of the computers especially in Asia and Africa are devoid of a decent internet connection. Most of the linux programs distributed via CDs are in source and need to be compiled and then install.
How can those devoid of an internet connection can use these programs?
Linux is itself open-source and it's open-source model itself commands that basic programming tools like build-essential are included in Ubuntu by default.
I haven't seen any comment that directly addresses your point. Those who have a broadband connection think everything should be downloaded. They don't know what it is like to work entirely from CD or an unreliable dial-up.

My live CD didn't include build-essentials while it had lots of stuff I didn't need.  This could have prevented me from compiling winmodem or network drivers...connectivity essentials.  I agree, Ubuntu should provide the essential tools on the live CD, even if it means leaving out some more useful stuff that can be downloaded once you have connectivity.  I would consider keeping the big stuff and dropping the small stuff anyone can download.  If that doesn't work, then make a separate multiple CD distro with the best big packages on it as most others do, but keep the LiveCD.
The security issue is a valid one, these tools should be easy for a beginner to install, but not installed or activated by default, even for a basic user.

---

### Post by BWF89 on 2007-01-17
Even if including build-essential by default would make it slightly less secure it's still a good deal more secure than Windows. Building from source was THE way to install software for the majority of Unix/LInux's lifetime. It's only in the recent years that installing from repositories has picked up as much steam as it has.

---

### Post by riven0 on 2007-01-17
I voted yes, because I think it's essential. People with non-compatible wireless cards, (Broadcom!), are not going to know to fire up the LiveCD in order to install the ndiswrapper. It just makes it less of a headache for the people trying to help them if build-essential was already there and ready to use.

---

### Post by aysiu on 2007-01-17
I've merged this with the other default *build-essential* thread.

I've also included a screenshot of the poll that got lost during the merge.

By the way, the debate is really about whether *build-essential* should be **installed** by default, not **present** by default. It is already present and installable from both the Desktop CD and the Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
``` I voted it should definitely be installed by default. Most other distros do this and do not seem any more insecure than Ubuntu. We don't live in this fairyland where only experts have to compile stuff. A lot of new users who are afraid of the command line have to compile certain programs just to get their hardware working properly. To top off the frustration of having to learn how to ./configure make and make install (and deal with .tar.gz files), why add on ```
make: command not found
``` to make them even more frustrated?

At the very least, instead of saying ```
make: command not found
``` the terminal should say ```
Would you like to install *build-essential*, which may be a minor security threat, in order to have the *make* command available?
``` 

By the way, the only time I've ever heard anyone suggest that *build-essential* is any way a security threat is in this debate. Whenever a user asks for help with compiling from source, all the veterans jump in with > Make sure you have *build-essential* installed **Never** have I seen someone add > And be careful, because it's a security risk

---

### Post by Amaranth on 2007-01-17
Why are we **still** talking about this? Everything needed to compile kernel modules is included in the install as of edgy. That means gcc and friends + linux-headers.

---

### Post by aysiu on 2007-01-17
> **Amaranth said:**
> Why are we **still** talking about this? Everything needed to compile kernel modules is included in the install as of edgy. That means gcc and friends + linux-headers.
Because people (yes, even beginners) sometimes need to compile more than kernel modules.

1. If it is truly a security risk, have a big warning about the risk any time someone tries to install it.

2. It already takes up space on the disk, so space is obviously not an issue.

3. It's just frustrating to have yet another thing to install to get things to work, and it's usually not covered in README files because .tar.gzs assume you have the essentials installed already. They just ask you to ./configure make make install.

---

### Post by ssam on 2007-01-17
> **aysiu said:**
> At the very least, instead of saying ```
make: command not found
``` the terminal should say ```
Would you like to install *build-essential*, which may be a minor security threat, in order to have the *make* command available?
``` 


this should be fixed in fiesty
[https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic](https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic)

---

### Post by aysiu on 2007-01-17
> **ssam said:**
> this should be fixed in fiesty
[https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic](https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic)
Excellent!

---

### Post by Canis familiaris on 2007-01-17
> **aysiu said:**
> 
At the very least, instead of saying ```
make: command not found
``` the terminal should say ```
Would you like to install *build-essential*, which may be a minor security threat, in order to have the *make* command available?
``` 

By the way, the only time I've ever heard anyone suggest that *build-essential* is any way a security threat is in this debate. Whenever a user asks for help with compiling from source, all the veterans jump in with  **Never** have I seen someone add

Exactly, what I was saying, I mean, its packages should atleast be in APT cache and a message just the one above should be there instead of the 
```
make: command not found
```
Personally when I was a newbie but was an experienced programmer and I installed Ubuntu and was frustrated at this prompt. At that point I did 
```
sudo apt-get install make
```
which of course did not work! :mad: 
Then by forums only I realized that I wanted the build-essential package.
I did'nt undergo this much frustration even when I used RHL  8 which was in other terms except this a frustrating experience.

These arguments about security issues are lame. After all the build-essential package can be configured to prompt for user's password as I suggested in my previous posting.

I think this thread must be forwarded to the Feisty developers, to consider suggesting **aysiu**'s suggestion.

---

### Post by Canis familiaris on 2007-01-17
> **ssam said:**
> this should be fixed in fiesty
[https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic](https://blueprints.launchpad.net/ubuntu/+spec/command-not-found-magic)
Very good:-D

---

### Post by FernandoMilton on 2007-01-18
> **Stormy Eyes said:**
> Exactly. I'm experienced, and if I need the dev tools I know how to install them. Don't worry about guys like me.

Quoted for Truth. Ubuntu is "Linux for Human Beings", and "they" mostly don't like/need command line/compiling stuff.

---

### Post by FLPCGuy on 2007-01-18
> **aysiu said:**
> ... about whether *build-essential* should be **installed** by default, not **present** by default. It is already present and installable from both the Desktop CD and the Alternate CD: 
```

**sudo apt-cdrom add**
sudo aptitude update
sudo aptitude install build-essential
```...At the very least, instead of saying ```
make: command not found
``` the terminal should say ```
Would you like to install *build-essential*, which may be a minor security threat, in order to have the *make* command available?
```....

I missed adding the CDROM as a source.  That would be a worthwhile addition to your great documentation.. [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)  

I saw it somewhere else but didn't understand enough to add it to my sources. 
[I don't see why it isn't included by default in the image etc/apt/sources.list.]   In my case it added:

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

Just having instructions a reasonable person could follow to install the compiler and use it are vital to the success of Linux.  

I really like the improved response to the unknown make command too!  That's coding for Human Beings.

---

### Post by demonhunter on 2007-01-29
I think that it shouldn't be there because every user should choose what to install or not. If you need build-essential, you can get it, but I think that you must have the freedom to choose.

:KS

---

### Post by cowlip on 2007-01-29
> **aysiu said:**
> Because people (yes, even beginners) sometimes need to compile more than kernel modules.

1. If it is truly a security risk, have a big warning about the risk any time someone tries to install it.

2. It already takes up space on the disk, so space is obviously not an issue.

3. It's just frustrating to have yet another thing to install to get things to work, and it's usually not covered in README files because .tar.gzs assume you have the essentials installed already. They just ask you to ./configure make make install.

I agree.  Until Debian gets to 75% of Linux marketshare, not all programs or kernel modules will have .debs :)  Installing should be as easy as possible, no?

I remember being very frustrated at not being able to ./configure/make/make install because of the missing "build-essential", as a Ubuntu newbie.

---

### Post by givré on 2007-01-29
If command-not-found goes default (what i hope), people wouldn't have to care about that.
[https://wiki.ubuntu.com/CommandNotFoundMagic](https://wiki.ubuntu.com/CommandNotFoundMagic)

---

### Post by cowlip on 2007-01-29
> **givré said:**
> If command-not-found goes default (what i hope), people wouldn't have to care about that.
[https://wiki.ubuntu.com/CommandNotFoundMagic](https://wiki.ubuntu.com/CommandNotFoundMagic)

true :)

---

### Post by akiratheoni on 2007-12-09
Alright so I know that build-essential is only a simple sudo apt-get install away, but I'm just curious as to seeing why the Ubuntu developers decided to leave an essential part of command line goodness out (pun intended). Anyone know why?

---

### Post by John.Michael.Kane on 2007-12-09
This may help answer your question.
[Build Essentials by default!]("http://ubuntuforums.org/showthread.php?t=206348&highlight=build-essential+included")

---

### Post by igknighted on 2007-12-09
I've often wondered this... many people need the compilers to install drivers for things like wireless... to get online in the first place.  Even if this is only 1% of users, I think this is significant and should be addressed.

---

### Post by GSF1200S on 2007-12-09
I think it should be, but then they have their reasons, too.

For instance, back in the days before the restricted drivers manager, I had to compile madwifi drivers from source, but I couldnt do that without build-essential. At the time I didnt realize I could pull it from the CD if I commented the sources.list, so I ended up having to d/l it on windows, make a copy from the windows partition (didnt have ntfs3g by default then), and then install it. I imagine this could still be the case for broadcom cards, etc. 

If you know your way around a little, all you need is the CD- but at first it would have been nice to at least had a command informing me of a way to install it...

just IMHO though...

---

### Post by bobbocanfly on 2007-12-09
If its on the CD it doesnt really make much sense not to install it. A lot of people use it and if its not going to take up any extra CD space it really should be installed by default. I know a lot of people run sudo apt-get install build-essential on their new Ubuntu system.

---

### Post by Fixman on 2008-01-01
I know its on the CD, but, seeing many questions happenned here for it, why is that build-essential, a package that weights some KBs, not included by default in Ubuntu?

---

### Post by hyper_ch on 2008-01-01
Because Ubuntu is a binary distribution on which the need for self-compliation isn't that big  ;)

---

### Post by Dr Small on 2008-01-01
I don't know. That's a good question.

---

### Post by John.Michael.Kane on 2008-01-01
This may help answer your question.
[Build Essentials by default!]("http://ubuntuforums.org/showthread.php?t=206348&highlight=build-essential+included")

---

### Post by por100pre1 on 2008-01-01
I think hyper_ch is right. Unless getting in the business of compiling from source, there's no much need for build-essential. It is already in the disk if it is ever needed.

---

### Post by Fixman on 2008-03-26
> **por100pre1 said:**
> I think hyper_ch is right. Unless getting in the business of compiling from source, there's no much need for build-essential. It is already in the disk if it is ever needed.

Yes, but there are many linux programs that MUST be compiled from source, and seriously, before I knewed ubuntuforums I had not a clue of what to do.

---

### Post by Oldsoldier2003 on 2008-03-26
> **por100pre1 said:**
> I think hyper_ch is right. Unless getting in the business of compiling from source, there's no much need for build-essential. It is already in the disk if it is ever needed.

Ubuntu is hailed as Linux for Humans. Humans don't compile, they click add....

But yes I ersonally think build-essential should be installed by default, but then again I'm a Computer Geek, not the typical Ubuntu Human :)

---

### Post by p_quarles on 2008-03-26
> **Fixman said:**
> Yes, but there are many linux programs that MUST be compiled from source, and seriously, before I knewed ubuntuforums I had not a clue of what to do.
Ultimately this is a question for the developers rather than for the forums. In my own opinion, it is far easier for new users to install build-essential than it is to figure out how to deal with all the issues inherent in building from source. There is a reason that compiling one's own binaries is not recommended for new users. The potential for security issues is one. 
                                     
In any case, Ubuntu is hardly unique in regard to this policy. Debian does not include build tools by default, nor (IIRC) does SuSE. Distros that rely on them -- such as Gentoo or Slackware -- are a different story.

---

### Post by cmnorton on 2008-03-26
Actually, everyone's post here makes sense from their vantage point, so here goes. Does it exist already, and if not could it, that the installation could be steered in a similar fashion that Fedora/Red Hat have already taken? That is the Ubuntu installation would install the way it does now by default, but upon some keystroke allow those of us who want build-essential, unix2dos, gcc, and so on to be installed with everything else.

In that way, Ubuntu would install for those people who are never going to build from the command line. For those of us who chose Ubuntu because of its support and essentially set it up as a development workstation with server components, it would be nice to install what we want at the installation, not after.

---

### Post by Oldsoldier2003 on 2008-03-26
> **p_quarles said:**
> Ultimately this is a question for the developers rather than for the forums. In my own opinion, it is far easier for new users to install build-essential than it is to figure out how to deal with all the issues inherent in building from source. There is a reason that compiling one's own binaries is not recommended for new users. The potential for security issues is one. 
                                     
In any case, Ubuntu is hardly unique in regard to this policy. Debian does not include build tools by default, nor (IIRC) does SuSE. Distros that rely on them -- such as Gentoo or Slackware -- are a different story.

You have a valid point your average new Linux user isn't likely to run slack or Gentoo as a first distro, unless they are really stubborn and pretty technically savvy. Well at least not run it and become a Linux convert immediately.

---

### Post by aysiu on 2008-03-26
I've merged a bunch of these threads together, and this poll (see attached) got lost in the process.

I've re-read this entire thread, and almost two years later, I still stand by everything I said before (sometimes I do change my mind, but not in this case), and I still have yet to see someone (without my prompting) in a support thread say, "You would need to install *build-essential*, but it is a security risk to have it installed, so please uninstall it after you're done compiling.

By the way, there's a Ubuntu Brainstorm idea about this:
[http://brainstorm.ubuntu.com/idea/4522/](http://brainstorm.ubuntu.com/idea/4522/)

---

### Post by LaRoza on 2008-03-26
It is the first thing I install, but it is on the CD, so it really isn't a problem.

I would like it installed by default, but that is just for convenience.

---

### Post by heartburnkid on 2008-03-26
Personally, I think build-essential should be left out by default, if only to encourage Linux developers to distribute software as .deb files in addition to source.  Myself, I don't mind compiling, as I've had a solid education in software development, but many people do see it as a big, scary thing, and that will keep them from giving Ubuntu a try.

Ubuntu is the most popular desktop Linux distro right now, so they could really set a trend here by encouraging developers to distribute software in a way that is easy for users to install.  That's the goal, right?  "Linux for human beings"?  It seems to me that encouraging compiling from source as a distribution method would be a step backwards.

---

### Post by aysiu on 2008-03-26
> **heartburnkid said:**
> Personally, I think build-essential should be left out by default, if only to encourage Linux developers to distribute software as .deb files in addition to source.  Myself, I don't mind compiling, as I've had a solid education in software development, but many people do see it as a big, scary thing, and that will keep them from giving Ubuntu a try.

Ubuntu is the most popular desktop Linux distro right now, so they could really set a trend here by encouraging developers to distribute software in a way that is easy for users to install. That sounds good in theory, but Ubuntu has been around for three and a half years, and I can't think of a single project that has felt pressured to create .deb files because of Ubuntu's lack of *build-essential* by default.

---

### Post by Trail on 2008-03-27
> **az said:**
> Matt Zimmerman is the CTO (chief technical officer) for ubuntu.

Offtopic, but is he related to the Zimmerman from PGP? (Philip wasn't it?)

As for build-essential, I don't care myself really. But I custom-compile the latest gcc usually.

---

### Post by z0mbie on 2008-03-27
One of things I like about Ubuntu installation is it's very stripped down and slim. 
Adding build essentials will make Ubuntu more bloated and like the other distros. 
Those of us who need it can install it & know how to. 
Lets not throw ideas around for the sake of ideas.

---

### Post by aysiu on 2008-03-27
Many people actually use *build-essential* and have no idea what package to install to get compiling from source working. It's not "throw[ing] ideas around for the sake of ideas." It's actually a good idea. If you disagree with it, provide reasons.

If you want to get out some bloat, you could always get rid of Bluetooth support. Not everyone has Bluetooth devices, and that can always (as *build-essential* has to be now) installed manually.

---

### Post by forrestcupp on 2008-03-27
I think it was more necessary to have build-essentials installed by default in 2006 when the thread was started than it is now.  Now, things have progressed to the point that everything is much easier and automated.  Also, Ubuntu's popularity has grown to the point that there isn't much out there that doesn't have either it's own repository or at least a deb available.

The main things now that you need to compile are the bleeding edge versions of software.  Common users don't need that, and people who do need that are knowledgeable enough to install build-essentials.

I don't know how many people I've seen in the forums asking how to compile a tar.bz they downloaded and they didn't even know they could just install the same thing from the repos.  People like that have no business compiling things they don't really need to.

I think now we are better off leaving it out.  2006 may have been a different story, though.

---

### Post by hyper_ch on 2008-03-27
As ubuntu is a binary distribution and relays on apt there should be little need for build-essential, hence there's no need to include that by default.

---

### Post by bruce89 on 2008-03-27
I don't know if anyone's noticed, but build-essential (and obviously its dependancies) is on the wee APT repository on all CDs (even Desktop ones). This means you can install it without having access to a mirror.

---

### Post by Captain Giraffe on 2008-03-27
Yes I vote for nethack by default :-)
build stuff gets tossed in by those who needs it.

---

### Post by kevdog on 2008-03-28
Build-essentials is ...Essential.   I have no idea why packages are included on the CD but are not installed.  Include and install them all, or simply don't include them.  Reminds me of Windows installation disks.  I think a lot of people use the build-essential package.  I know many many users that compile ndiswrapper from scratch.  I often tell people to go ahead and install the header and build-essential packages and never warn them off any possible security risk -- if there is one?  Now if there was just a simple way to remove the CD-ROM for the /etc/apt/sources.list that would be great -- a CL statement rather than editing the file manually.

---

### Post by aysiu on 2008-03-28
> **kevdog said:**
> I often tell people to go ahead and install the header and build-essential packages and never warn them off any possible security risk -- if there is one? That's what's bugged me throughout this whole conversation.

It either is a security risk... or it isn't. Some of the anti-install-build-essential-by-default people talked a big game about what a security risk it is, but I didn't see them ever telling people in support threads not to install it when it's needed or to install it only temporarily and then remove it straight afterwards.

We need a consistent message here.

If it's a security risk, the risk should be mentioned everywhere that someone says > Just *sudo apt-get install build-essential* and then anyone advised to install it should be told immediately to remove it after they're done using it.

And if it's not a security risk, well, people should admit it, and it should be installed by default. It doesn't use system resources. It just takes up space. You think it's not bloat to have laptop hotkey support, HP printer and Bluetooth services running for people who are running desktops, don't have HP printers, and don't have Bluetooth devices? Those are services using system resources.

So you anti-build-essential people need to make up your minds. Either go on a crusade warning people against installing it, as it is a security risk, or finally admit here and now that it isn't a security risk and all that talk about it being a security risk before was just bunk.

---

### Post by p_quarles on 2008-03-28
> **aysiu said:**
> So you anti-build-essential people need to make up your minds. Either go on a crusade warning people against installing it, as it is a security risk, or finally admit here and now that it isn't a security risk and all that talk about it being a security risk before was just bunk.
The build tools themselves are not a security risk at all, so if anyone is saying that, they're wrong. The security risk comes in the form of compiling a program without being subscribed to its mailing list, or without regularly checking the project page. This is particularly problematic when the application in question is responsible for any kind of networking function.

It's not the fact of compiling a program that is the risk, it is the fact that this practice is poorly integrated into the Debian security model.

---

### Post by quill3033 on 2008-03-28
I think the reason most people *on this forum* want the Build-essential (which seems to be a program for developing ubuntu??? and possibly other programs???) is that most are probably really good at computers and programming etc. 

for a non-expert like myself I would rather it were not on by default as it would be useless to me and could potentially leave my computer open to virus/intrusion whatever. 

I think that it is good for Ubuntu to also be as open to non experts as possible - at least that is how I understand the philosophy.

---

### Post by drascus on 2008-03-28
well I think that most software packages that people want are in the repos or available through Getdeb as .deb packages. If someone finds they really need build essential they are only a small click or few keystrokes away from getting it. It would really just be one more thing that they would have to try and fit into the live CD and you are not really going to be compiling with a live CD anyway.
> I think the reason most people *on this forum* want the Build-essential (which seems to be a program for developing ubuntu??? and possibly other programs???) is that most are probably really good at computers and programming etc.
for a non-expert like myself I would rather it were not on by default as it would be useless to me and could potentially leave my computer open to virus/intrusion whatever.
I think that it is good for Ubuntu to also be as open to non experts as possible - at least that is how I understand the philosophy.
__________________
Thanks

I don't think Build Essential is really that much of a security risk an attack would still need to force super user powers in order to use it. Also it is not necessarily unfriendly to the non-technical user as unless you need to use it you wouldn't even really know it was there so it wouldn't freak you out. Also even for people who don't program it could be very useful say if you want the latest version of a Software package that hasn't made its way into the repos yet. You could easily download source type a few commands and have the latest program in no time. This doesn't require programming knowledge and I think its worth any Gnu/linux users while to learn a few basic commands in Terminal and compiling is definitely considered a basic skill.

---

### Post by bruce89 on 2008-03-28
> **drascus said:**
> well I think that most software packages that people want are in the repos or available through Getdeb as .deb packages. If someone finds they really need build essential they are only a small click or few keystrokes away from getting it. It would really just be one more thing that they would have to try and fit into the live CD and you are not really going to be compiling with a live CD anyway.

For any real program, you need a lot more than just a C and C++ compiler.

---

