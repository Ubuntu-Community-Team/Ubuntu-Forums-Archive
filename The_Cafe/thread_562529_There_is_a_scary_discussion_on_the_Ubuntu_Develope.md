---
title: "There is a scary discussion on the Ubuntu Developers mail list."
date: 2007-09-28
forum: The Cafe
---

### Post by Kilz on 2007-09-28
I happened to be cleaning out my email box for the Ubuntu developers list. What I found may send shivers up your spine.

[http://www.opensubscriber.com/message/ubuntu-devel@lists.ubuntu.com/7673369.html](http://www.opensubscriber.com/message/ubuntu-devel@lists.ubuntu.com/7673369.html)

This is a discussion on how to make it difficult for users to install 3rd party applications under the guise that some may be malware. That the developers know more than users what is safe or wanted on a their computers. This sounds more like it came from Microsoft.
Am I reading this correctly?

---

### Post by ryanVickers on 2007-09-28
I never thought about it before, but yeah, any program could be a virus, and linux is secure, but if you click and give it the password to go ahead and install, there's not much it an do, is there! :p

But they can't just go and block all 3rd party software!  That's preposterous!  I mean, did they even think what that's doing!?!

If this is actually implemented, I'm gonna switch to redhat or something... :(

---

### Post by crjackson on 2007-09-28
WOW! If they want to stop this fast running freight train called ubuntu, this is how to stop it.  I know I'll find a different distro if this comes to pass.

I don't need system administration from the creator, I prefer to do that myself.  Doesn't sound like freedom anymore.

---

### Post by ryanVickers on 2007-09-28
Look at it this way - if it does happen, within a month, someone will have fixed it and a new branch of Ubuntu will form that doesn't have it, they will both march on, with the original dieing miserably, and then they will merge back together and everything will be OK again!  Kin of like compiz --> compiz and beryl, then compiz-fusion! :p

---

### Post by crjackson on 2007-09-28
Well, I really don't think it will happen but you never know.  The Official Ubuntu book sings praises against this sort of control.  I'll be pissed off if I boutht the damn book and it lied.:mad:

---

### Post by Cappy on 2007-09-29
It won't ever come to happen because it is a stupid idea. You can block people from running debs but then attackers would start telling people to run commands. If they blocked people from running commands then they would tell them to go to System-->Preferences-->Remote Desktop and enable it.

There just isn't a way to block someone from running a trojan or rootkit without making it so difficult they couldn't use the system in the first place. If someone wants to run a trojan they ARE going to run it. Making them jump through 10 passwords and a chmod to install it are going to do absolutely NOTHING but waste time.

Also .. debs are extremely user friendly. One click to install? Amazing! On Windows you have to do
> Next Next Next Surrender-Soul-to-EULA    Pick-Install-Directory     Next Next Yes-My-Internet-Is-Up Next Next No-I-Don't-Want-Ads-But-Thank-You Next Next Next Finish

---

### Post by mysticmatrix on 2007-09-29
> We cannot assume that our users are sufficiently knowledgeable and  
experienced to know what is and is not an acceptable risk to take

Ya we all are fool to ditch windows.

---

### Post by nss0000 on 2007-09-29
BigK:

Yep scary-as-all-heck. I could hear the "hobnails" of serious men discussing serious a subject. Servants of the community ... naturally, and like all men with unmoderated power not one (1) thought to increasing the power of the individual lusr.  

That is the true liberating effect of the personal computer ... giving more power to more people than any other tool in human history, save fire and cranberry scones.

---

### Post by the yawner on 2007-09-29
The letter has some valid points. If there's anything that can break through the most secure system, it's social engineering. So, how do you protect your users from themselves?

---

### Post by peitschie on 2007-09-29
Wow... I feel like I'm on slashdot.... umm rtfa?

Yes, the article is broaching the idea of restricting installation of software.  And is discussing how software can be "controlled" for the deliberate purpose of eliminating malware and other such baddies (a good goal).  It is important to note though, that the author of the so called "scary letter" realises these points.  To quote:
> 
> > Or to put it another way: the point of Ubuntu is to give users control  
> > over their own computers - that is, Freedom.  Our job includes  
> > defending that control against those who would risk it in the name of  
> > temporary convenience.  
>  
> Ian, I basically agree with your thoughts but I think we should be  
> *very* careful about creating a measure that could "protect the user  
> against him/herself" in the model, say Windows Vista does.  
 
I agree that this is something we should look out for.  But we're in a  
bit of a different position to M$.  Because Ubuntu is free software,  
if users (and their technically-minded friends and allies) do not like  
what we're doing, they can do things themselves their own way.  

I have had to clean up so many malware infested windows machines... I would dream of chains of trust to help my job!  This is something that needs to be examined, because not everyone is a power-n3rd who can distinguish between cool eye candy ("yay compiz repos!") and a keylogger hidden in a music player ("umm.. Amaroque2?").  If we don't discuss OS defense, we leave the door open to virus makers, malware creators and all other kinds of malicious people.

Stop being so dramatic and lets actually get positively involved in the discussion.  How do we protect ubuntu, and protect our unexperienced brethren from those who wish to harm them?

---

### Post by Cappy on 2007-09-29
You can't without taking away every method they could use to install new software. Ubuntu can't whitelist every 3rd party package that a user might want to install.

---

### Post by ryanVickers on 2007-09-29
Perhaps there can be 2 modes to set the OS into in the Administration menu.  You could change it yourself, or the admin could lock it down, but what it does is you get 2 modes - "normal", and "safe".  For most users, they would set it to normal (how Ubuntu is now), and for very "computer-'unknowledgeable'" users, they, or the admin, could switch it to "safe" for their account, and it would block EVERYTHING that didn't com from the repositories or the updates - and adding repositories would be blocked.

You could just not give them the root password, but sometimes you have to, and some settings and stuff the *user* should be allowed to change needs it...

Just an ideae :p

---

### Post by NullHead on 2007-09-29
> **ryanVickers said:**
> Perhaps there can be 2 modes to set the OS into in the Administration menu.  You could change it yourself, or the admin could lock it down, but what it does is you get 2 modes - "normal", and "safe".  For most users, they would set it to normal (how Ubuntu is now), and for very "computer-'unknowledgeable'" users, they, or the admin, could switch it to "safe" for their account, and it would block EVERYTHING that didn't com from the repositories or the updates - and adding repositories would be blocked.

You could just not give them the root password, but sometimes you have to, and some settings and stuff the *user* should be allowed to change needs it...

Just an ideae :p

I think thats a good idea. There would be a smart user system  a root account and a user account ... the user would need to ask for a time activated root pass that would be only good e.g an hour but it's only good for something like changing a setting.

If they block all 3rd party software they should also make an easy to use repo screening system. So a developer has made some software for Ubuntu he submits it to the Ubuntu screening team to check it for something that might harm a pc and if the software passes it would go into the Ubuntu repository 3rd party software only section. But it needs to easy so that people aren't scared away from using it or not writing software at all.

---

### Post by Kilz on 2007-09-29
What everyone seems to be missing is that any ideas they have here will never be seen by the Ubuntu developers. Who have a history of not listening to users and doing exactly what they want. Try posting to that mail list and you will see what I mean.
I also see that this is something that effects the whole Ubuntu community. I am going to ask that it be moved to another part of the forum.

---

### Post by RAV TUX on 2007-09-29
> **Kilz said:**
> I happened to be cleaning out my email box for the Ubuntu developers list. What I found may send shivers up your spine.

[http://www.opensubscriber.com/message/ubuntu-devel@lists.ubuntu.com/7673369.html](http://www.opensubscriber.com/message/ubuntu-devel@lists.ubuntu.com/7673369.html)

This is a discussion on how to make it difficult for users to install 3rd party applications under the guise that some may be malware. That the developers know more than users what is safe or wanted on a their computers. This sounds more like it came from Microsoft.
Am I reading this correctly?

> **peitschie said:**
> Wow... I feel like I'm on slashdot.... umm rtfa?

Yes, the article is broaching the idea of restricting installation of software.  And is discussing how software can be "controlled" for the deliberate purpose of eliminating malware and other such baddies (a good goal).  It is important to note though, that the author of the so called "scary letter" realises these points.  To quote:


I have had to clean up so many malware infested windows machines... I would dream of chains of trust to help my job!  This is something that needs to be examined, because not everyone is a power-n3rd who can distinguish between cool eye candy ("yay compiz repos!") and a keylogger hidden in a music player ("umm.. Amaroque2?").  If we don't discuss OS defense, we leave the door open to virus makers, malware creators and all other kinds of malicious people.

Stop being so dramatic and lets actually get positively involved in the discussion.  How do we protect ubuntu, and protect our unexperienced brethren from those who wish to harm them?

Interesting post, but honestly nothing to worry about. You could always just use Debian or simply build your own Ubuntu derivative both of which are very, very easy to do. ;)

---

### Post by FuturePilot on 2007-09-29
That whole idea is just ridiculous! Sounds like they want to go back to the Linux of 1995.
I really hope that doesn't happen.

---

### Post by Polygon on 2007-09-29
this sounds liek teh scare that the kernel developers were going to make it so no restricted modules could be in the kernel, and gave everyone like 6 months to adapt before they forcefully reject any restricted modules (or something along those lines)

these people arnt stupid, im confident they will make a good decision

---

### Post by MetalMusicAddict on 2007-09-29
> **Kilz said:**
> **What everyone seems to be missing is** that any ideas they have here will never be seen by the Ubuntu developers. Who have a history of not listening to users and doing exactly what they want. Try posting to that mail list and you will see what I mean.
I also see that this is something that effects the whole Ubuntu community. I am going to ask that it be moved to another part of the forum.

What everyone ***is*** missing is that there are no nefarious intentions here.

And this crap about Ubuntu developers "history of not listening to users" is pure and utter nonsense.

As someone who has had the privilege of moving from user to developer I can say in all honestly the users (which they are also and everyone forgets) are first on their minds. Go to a UDS. The are free for anyone to come and participate in and will show you how important we **all** are.

People ask for alot of impossible things that simply can't be done.

This was probably a mistake posting because alot of people on the board now a days rather hold on to and feed the crappy FUD and rumor but oh well. :(

Everyone wants to complain. If you don't like it actually get off your duff and **do** something about it or use another distro.

***MMA shakes head.

Kilz - This isnt aimed directly at you, more this general attitude that to me is all too common on these forums lately. ;)

---

### Post by aysiu on 2007-09-29
What's the big deal? I guess some people didn't read the whole thing: > [b]What is of course also necessary is an ability for power users to  
specify additional third-parties without any blessing from Ubuntu.[/b]  
However *this facility must not to be accessible to naive users*.  
 
In particular, it *must not be possible* for a third party to invoke  
such a UI via eg a website, incoming email, video file, or whatever.  
 
 
We can't stop third parties writing on their website  
 
  "Now go to   Settings / Advanced / Trusted Software Sources  
   and select   Add Absolute URL  
   and paste in   [http://malware.example.com/ubuntu/](http://malware.example.com/ubuntu/)  
   say `confirm' to the security warning and enter your pasword"  
 
or  
 
  "Select  Applications / Accessories / Terminal  
   In the window type  
     sudo apt-add-untrusted-repository --force-security-override [http://malware.example.com/ubuntu/](http://malware.example.com/ubuntu/)  
   and type in your password when prompted."  
 
but even a naive user can be expected to smell a rat there.  
 
On the other hand if the third party can say  
 
  "Your browser does not support Frobnication.  
   [Click here] to install it"  
 
the user will click and probably say yes to the confirmation question  
and enter their password when prompted.  So we have to prevent that.   If you're a power user (as most of the people who visit the Community Cafe often are), then you can do whatever you want. This is basically extending a Gnome way of thinking: think *for* the "naive users" and then create a back-end for power users to do other stuff they want to do.

---

### Post by RAV TUX on 2007-09-29
> **aysiu said:**
> What's the big deal? I guess some people didn't read the whole thing:  If you're a power user (as most of the people who visit the Community Cafe often are), then you can do whatever you want. This is basically extending a Gnome way of thinking: think *for* the "naive users" and then create a back-end for power users to do other stuff they want to do.

aysiu, I agree that this is no big deal.

Also Ubuntu users can always use XFCE, KDE, Fluxbox or E17 if they don't agree with GNOME decisions.

---

### Post by aysiu on 2007-09-29
By the way, while I don't agree that this is a scary discussion, I will say that the proposal is a bit misguided. There's only so much you can protect users from themselves without *educating* them. Any uneducated user who has an administrative password (either root or sudo) is a security risk. Social engineering evolves. Right now, there may seem to be an easy way to thwart attempts to hijack security, but the ultimate solution is educating users, not constricting them.

I was just talking about this with some co-workers yesterday at lunch regarding wire transfers to Nigeria, PayPal asking you to verify credit card information, etc. Those social engineering scams mainly have to do with personal/financial security and less to do with operating system security, but the principle remains the same--these 30-something and 40-something co-workers of mine (who are not necessarily tech-savvy) had to wise up to the ways of the world, and they lamented how they were not always as wise as they are now.

Just as you tell a child not to take candy from strangers, you also have to tell computer users of any age not to download software from just anywhere. Teach them to be discerning. Yes, it's true--a warning pop-up will almost always go unread--but it's not up to the developers to think for you what is "trusted" or "not trusted" software. It's up to users to educate each other, just the way we do about looking both ways before crossing the street or not touching the stove when it's hot. Imagine if stove/oven manufacturers had to prevent users from turning on the stove because people might just touch it and burn themselves. It's ridiculous!

---

### Post by RAV TUX on 2007-09-29
> **aysiu said:**
> By the way, while I don't agree that this is a scary discussion, I will say that the proposal is a bit misguided. There's only so much you can protect users from themselves without *educating* them. Any uneducated user who has an administrative password (either root or sudo) is a security risk. Social engineering evolves. Right now, there may seem to be an easy way to thwart attempts to hijack security, but the ultimate solution is educating users, not constricting them.

I was just talking about this with some co-workers yesterday at lunch regarding wire transfers to Nigeria, PayPal asking you to verify credit card information, etc. Those social engineering scams mainly have to do with personal/financial security and less to do with operating system security, but the principle remains the same--these 30-something and 40-something co-workers of mine (who are not necessarily tech-savvy) had to wise up to the ways of the world, and they lamented how they were not always as wise as they are now.

Just as you tell a child not to take candy from strangers, you also have to tell computer users of any age not to download software from just anywhere. Teach them to be discerning. Yes, it's true--a warning pop-up will almost always go unread--but it's not up to the developers to think for you what is "trusted" or "not trusted" software. It's up to users to educate each other, just the way we do about looking both ways before crossing the street or not touching the stove when it's hot. Imagine if stove/oven manufacturers had to prevent users from turning on the stove because people might just touch it and burn themselves. It's ridiculous!aysiu, I commend you for your clarity in thought but more so for your articulate way to express yourself in writing so eloquently. Thank You for your post.

---

### Post by Cappy on 2007-09-29
> However *this facility must not to be accessible to naive users*.

And then naive users won't be able to install any 3rd party software. And then they go back to Windows OR they will just learn how to do it "the new way"

This does not solve any problem.

---

### Post by Frak on 2007-09-29
I trust the devs, they are just making another KISS (Keep It Simple Stupid) technique. If they did do something nefarious, within a week they would not only be disbanded for various reasons, but multiple Forks would have already been made excluding that function.

But seriously, they could never get away with anything nefarious because the code is open.

Some users don't know what they are doing, and sometimes we need to take their hand. Not everybody wants to worry about things we do, hopefully we will reach the day when your screen is autoconfigured, all malware is eliminated automatically, with no notification, for free, all hardware works, and nobody needs an IQ over 140 to operate it.

Our goal is to create the easiest OS to use, on this Earth or anywhere, not to compete with Windows. If Windows just goes away, then that's just an added benefit ;)

---

### Post by ryanVickers on 2007-09-29
This is really quite stupid!  your right about going back to windows!  They will just be like "We were less locked-in to the "brandname" software with Micro$oft!" and they'll leave.

---

### Post by aysiu on 2007-09-29
> **Frak said:**
> 
Our goal is to create the easiest OS to use, on this Earth or anywhere, not to compete with Windows. If Windows just goes away, then that's just an added benefit ;) If you're talking about Linux, then you're right. If you're talking about Ubuntu, then you're wrong.

Bug #1 is *Microsoft has a majority market share*. It mentions Microsoft specifically, so Ubuntu is a direct competitor to Windows.

---

### Post by Frak on 2007-09-29
> **aysiu said:**
> If you're talking about Linux, then you're right. If you're talking about Ubuntu, then you're wrong.

Bug #1 is *Microsoft has a majority market share*. It mentions Microsoft specifically, so Ubuntu is a direct competitor to Windows.
OK, then.

[CENTER][COLOR="Red"][SIZE="5"]DOWN WITH WINDOWS[/SIZE][/COLOR] :twisted:[/CENTER]

:lolflag:

---

### Post by RAV TUX on 2007-09-29
> **aysiu said:**
> If you're talking about Linux, then you're right. If you're talking about Ubuntu, then you're wrong.

Bug #1 is *Microsoft has a majority market share*. It mentions Microsoft specifically, so Ubuntu is a direct competitor to Windows.

kind of like the once unknown cola that decided to go in direct competition with the major cola.

The once unknown cola: Pepsi
The only major cola: Coca Cola

Marketing genius that worked for Pepsi, lets hope it works for Ubuntu also. ;)

---

### Post by ryanVickers on 2007-09-29
You know what's interesting, there's usually 2 marketing techniques: 1 is simply stating what you have (used if your the top product, and everyone is clueless to the competitors), and the other technique is to compare the products and make it look like yours is better (used if your fighting your way to the top).  The interesting thing is, micro$oft has been using #2 lately, so, I think they've finally recognized linux as a big risk to they're share of the market (at least on servers)!!! :p

---

### Post by Dimitriid on 2007-09-29
The approach is flawed.

1) Assuming Ubuntu will have any real penetration to guarantee attempts against users is absurd: Surely this developer and anyone on his side thinks too much of himself if he thinks he can achieve 0.1% market penetration within the next decade or so. ( and thats me being nice to him since he made the ridiculous claim "**When** Ubuntu is as popular as Windows" )  So right off the bat, its appealing to users so dumb that their wreck windows installations with spyware is already appealing to users **that wont ever switch to Linux unless somebody successfully stops windows from being on virtually every single consumer PC preinstalled**. Much like copy protection and DRM what will these do? Keep smart users smart? Dumb users use Windows and OS X

2) Assuming that any security team anywhere will be able to keep up with all the software people want to install. Limiting people to just the repositories they approve ( or making the OS jump through many hoops in order to enable third party repositories ) will just create a bottleneck. **Do we really need more bottlenecks to development when they are already on only a fixed 6 month release cycle which pretty much limits the distro greatly?** ( I.E. K/ubuntu will be very late to officially support KDE 4.0 since it will come out in mid cycle, completely losing momentum )

While they are concerned with security, im concerned with their wishful thinking, overly active imagination and naiive optimism. Should this find its way to the distro I would probably find my way to another distro, a distro that can fit both a power desktop user and is accessible enough for less advanced users. If I wanted something as paranoid Id get a server oriented distro with little or no upgrades.

---

### Post by RAV TUX on 2007-09-29
> **RAV TUX said:**
> kind of like the once unknown cola that decided to go in direct competition with the major cola.

The once unknown cola: Pepsi
The only major cola: Coca Cola

Marketing genius that worked for Pepsi, lets hope it works for Ubuntu also. ;)I was just envisioning the taste test commercials between Coke & Pepsi.

Taste test commercials between: Windows & Ubuntu would be classic. Set up booths around the world with two computers one with Ubuntu, one with Windows and film it, publish it on YouTube, and have a grass roots homegrown ad campaign.

---

### Post by Frak on 2007-09-29
> **RAV TUX said:**
> I was just envisioning the taste test commercials between Coke & Pepsi.

Taste test commercials between: Windows & Ubuntu would be classic. Set up booths around the world with two computers one with Ubuntu, one with Windows and film it, publish it on YouTube, and have a grass roots homegrown ad campaign.
I may do just that. I have alot of old unused laptops that run Ubuntu fine, Windows not so much...

I'd give away a bunch of laptops by the end of the day after people have tried out both booths.

A test, with a reward. :)

---

### Post by fireworksshow on 2007-09-29
> **Dimitriid said:**
> The approach is flawed.

1) Assuming Ubuntu will have any real penetration to guarantee attempts against users is absurd: Surely this developer and anyone on his side thinks too much of himself if he thinks he can achieve 0.1% market penetration within the next decade or so. ( and thats me being nice to him since he made the ridiculous claim "**When** Ubuntu is as popular as Windows" )  So right off the bat, appealing to users so dumb that their wreck windows installations with spyware is already appealing to users **that wont ever switch to Linux unless somebody successfully stops windows from being on virtually every single consumer PC preinstalled**

2) Assuming that any security team anywhere will be able to keep up with all the software people want to install. Limiting people to just the repositories they approve ( or making the OS jump through many hoops in order to enable third party repositories ) will just create a bottleneck. **Do we really need more bottlenecks to development when they are already on only a fixed 6 month release cycle which pretty much limits the distro greatly?** ( I.E. K/ubuntu will be very late to officially support KDE 4.0 since it will come out in mid cycle, completely losing momentum )

While they are concerned with security, im concerned with their wishful thinking, overly active imagination and naiive optimism. Should this find its way to the distro I would probably find my way to another distro, a distro that can fit both a power desktop user and is accessible enough for less advanced users. If I wanted something as paranoid Id get a server oriented distro with little or no upgrades.

I agree with you're first point, but I personally think that KDE 4.0 coming out in mid cycle is perfect, it gives enaught time to the developers/betatesters to give kubuntu polish and work out the early bugs. I found out that recently the linux marked started to lose some major bugs in they're distro's because of hurrying new released software without proper testing.

---

### Post by RAV TUX on 2007-09-29
> **Frak said:**
> I may do just that. I have alot of old unused laptops that run Ubuntu fine, Windows not so much...

I'd give away a bunch of laptops by the end of the day after people have tried out both booths.

A test, with a reward. :)cool but lets not get this thread off track....

post about that here:
 **     Grass Roots homegrown ad campaign ThinkTank Thread for Ubuntu**

[B][http://ubuntuforums.org/showthread.php?t=563075](http://ubuntuforums.org/showthread.php?t=563075)

[/B]

---

### Post by Kilz on 2007-09-29
> **MetalMusicAddict said:**
> What everyone ***is*** missing is that there are no nefarious intentions here.

And this crap about Ubuntu developers "history of not listening to users" is pure and utter nonsense.

As someone who has had the privilege of moving from user to developer I can say in all honestly the users (which they are also and everyone forgets) are first on their minds. Go to a UDS. The are free for anyone to come and participate in and will show you how important we **all** are.

People ask for alot of impossible things that simply can't be done.

This was probably a mistake posting because alot of people on the board now a days rather hold on to and feed the crappy FUD and rumor but oh well. :(

Everyone wants to complain. If you don't like it actually get off your duff and **do** something about it or use another distro.

***MMA shakes head.

Kilz - This isnt aimed directly at you, more this general attitude that to me is all too common on these forums lately. ;)

My opinion is that the developers have secluded themselves. Try making a new account and joining the developer's list this is on. Also from personal experience. IMHO the developers believe they are above us mere users.
Thats what makes this post so scary. Its like it should have came from Microsoft.

---

### Post by Kilz on 2007-09-29
> **aysiu said:**
> By the way, while I don't agree that this is a scary discussion, I will say that the proposal is a bit misguided. There's only so much you can protect users from themselves without *educating* them. Any uneducated user who has an administrative password (either root or sudo) is a security risk. Social engineering evolves. Right now, there may seem to be an easy way to thwart attempts to hijack security, but the ultimate solution is educating users, not constricting them.

I was just talking about this with some co-workers yesterday at lunch regarding wire transfers to Nigeria, PayPal asking you to verify credit card information, etc. Those social engineering scams mainly have to do with personal/financial security and less to do with operating system security, but the principle remains the same--these 30-something and 40-something co-workers of mine (who are not necessarily tech-savvy) had to wise up to the ways of the world, and they lamented how they were not always as wise as they are now.

Just as you tell a child not to take candy from strangers, you also have to tell computer users of any age not to download software from just anywhere. Teach them to be discerning. Yes, it's true--a warning pop-up will almost always go unread--but it's not up to the developers to think for you what is "trusted" or "not trusted" software. It's up to users to educate each other, just the way we do about looking both ways before crossing the street or not touching the stove when it's hot. Imagine if stove/oven manufacturers had to prevent users from turning on the stove because people might just touch it and burn themselves. It's ridiculous!

This post I can agree with, IMHO anything that takes power away from users is a bad thing. Loosing things under the guise of security just leaves a bad taste in my mouth. If all it was  were a popup or some such , it would be ok, but the topic on the mail list seems to be going further down a bad path. You might want to read the replies.

---

### Post by p_quarles on 2007-09-29
> **Kilz said:**
> This post I can agree with, IMHO anything that takes power away from users is a bad thing. Loosing things under the guise of security just leaves a bad taste in my mouth. If all it was  were a popup or some such , it would be ok, but the topic on the mail list seems to be going further down a bad path. You might want to read the replies.
The measure that was described doesn't take any power away from the user. It simply forces the user to go through more steps to accomplish something that could compromise the computer. There are already many similar measures built in to the typical Linux distro. Some examples:

-A normal user does not have root privileges. 
-If you want to compile something in the absence of the necessary dependencies, you have to override the default behavior
-If you want to delete a directory without getting an earful, you have to type out "rm -Rf"
-To use apt-get to do something dumb, you have to use "--force-yes"

I agree with aysiu on this, that this isn't really a very sensible proposal. All the same, the concerns they have are legitimate, and as near as I can tell they are trying to add some newbie-proof security measures *without* compromising the functionality and power of the system as a whole.

---

### Post by Frak on 2007-09-29
A better idea would be to just do like many anti-virus and build up an immunity against the invaders. Then if something goes wrong, we can examine the ruble of the machine and find a solution. Mainly to blacklist the offender. Risk one to save many. Plus all we have to do is enact some recovery measures, Just In Case.

Thats why we have GPG keys folks. To filter known "good" people, from "bad" people.

---

### Post by Warren Watts on 2007-09-29
There are a ***lot*** of folks in the Linux community that feel that Ubuntu has *already* gone too far in regards to making Linux idiot proof.  

All I can say on the subject is that there are plenty of Linux flavors out there, and if as a Linux user you are unhappy with the direction your particular Linux flavor is going, it's not at all difficult to switch to another distro that better suits your needs and personal beliefs about the way you want your OS to treat you.

I personally have Ubuntu installed on the family PC because it is easy to use and user friendly, and use Archlinux  on my personal PC.

---

### Post by ryanVickers on 2007-09-29
Idiot-proof doesn't have to mean it's lacking features; why, just look at my split rar maker! :p - they *could* do this intelligently...

---

### Post by p_quarles on 2007-09-29
> **Warren Watts said:**
> There are a ***lot*** of folks in the Linux community that feel that Ubuntu has *already* gone too far in regards to making Linux idiot proof.  

All I can say on the subject is that there are plenty of Linux flavors out there, and if as a Linux user you are unhappy with the direction your particular Linux flavor is going, it's not at all difficult to switch to another distro that better suits your needs and personal beliefs about the way you want your OS to treat you.

I personally have Ubuntu installed on the family PC because it is easy to use and user friendly, and use Archlinux  on my personal PC.
Whenever I hear that charge, it almost always boils down to two (and possibly three) things:
1) Automatix. For some reason, people think it is somehow built-in to Ubuntu. It's not. And it's not idiot proof. 
2) Using "sudo" by default. This is just plain ignorance. The arguments for and against it belong in the "recurring discussions" sub-forum, so I'll leave at it this: many power users on other distros disable the root account and use sudo.

The optional third part is the inclusion of the restricted modules in the installation CD. To me, that's more a matter of convenience than idiot-proofing. 

Long-story short: I haven't seen a single good argument so far for the contention that Ubuntu sacrifices functionality for the sake of coddling the newcomers.

---

### Post by fwojciec on 2007-09-29
Nothing scary about this discussion, just realistic.  People who want Ubuntu to take over the world usually don't think about the inevitable consequences of this ambition - as popularity of an OS increases the average skill-level of the user base decreases.  That's just the way of things, and only so much can be achieved by trying to educate the users...  It's encouraging that the devs understand it and are being proactive about the dangers/problems that are bound to appear as Ubuntu continues to gain momentum and becomes more mainstream.

---

### Post by Kilz on 2007-09-29
I see more and more people posting on how they will be glad to just blindly follow along.
Methinks some used Windows to long and it has made them think its normal to lose freedom for the sake of security.

---

### Post by fwojciec on 2007-09-29
> **Kilz said:**
> I see more and more people posting on how they will be glad to just blindly follow along.
Methinks some used Windows to long and it has made them think its normal to lose freedom for the sake of security.

I don't think your characterization of people who disagree with your description of the discussion as "scary" is fair or, for that matter, friendly.  It also doesn't seem that you have actually tried to listen to the arguments they rise, much less to answer them with anything resembling a counter-argument.

---

### Post by p_quarles on 2007-09-29
> **Kilz said:**
> I see more and more people posting on how they will be glad to just blindly follow along.
Methinks some used Windows to long and it has made them think its normal to lose freedom for the sake of security.
Now see that's just flamebait. If you disagree with my position, you are more than free to say why, and I will listen. Don't call me a "blind follower" though.

---

### Post by lisati on 2007-09-29
> **Frak said:**
> A better idea would be to just do like many anti-virus and build up an immunity against the invaders. Then if something goes wrong, we can examine the ruble of the machine and find a solution. Mainly to blacklist the offender. Risk one to save many. Plus all we have to do is enact some recovery measures, Just In Case.

Thats why we have GPG keys folks. To filter known "good" people, from "bad" people.

Perhaps we can learn from the developers of anti-spam systems. The last time I checked, Pegasus Mail was able to use "whitelists" and "blacklists" in its message rules to allow and/or block messages from particular senders, and some of the anti-spam products I've checked out have used similar techniques, combined with a form of "quarantine" system that allows you to safely review material from an unknown source, and also combined with a means to learn to distinguish the good from the bad.

---

### Post by Frak on 2007-09-29
> **lisati said:**
> Perhaps we can learn from the developers of anti-spam systems. The last time I checked, Pegasus Mail was able to use "whitelists" and "blacklists" in its message rules to allow and/or block messages from particular senders, and some of the anti-spam products I've checked out have used similar techniques, combined with a form of "quarantine" system that allows you to safely review material from an unknown source, and also combined with a means to learn to distinguish the good from the bad.
Yeah, Just like that.

I have no idea why I said anti-virus, the only thing to compare to anti-virus is anti-virus :P

---

### Post by Kilz on 2007-09-30
> **fwojciec said:**
> I don't think your characterization of people who disagree with your description of the discussion as "scary" is fair or, for that matter, friendly.  It also doesn't seem that you have actually tried to listen to the arguments they rise, much less to answer them with anything resembling a counter-argument.
Maybe thats because I cant believe what I am reading. That any argument I would make is based on simple understanding that freedom is good and limits on that is bad. But maybe I have given to much credit to the fact that people using free software would know the free stands for freedom, not price. That its a personal computer and not a developers computer. The user is the one that should decide what should be allowed to be installed. 
> **p_quarles said:**
> Now see that's just flamebait. If you disagree with my position, you are more than free to say why, and I will listen. Don't call me a "blind follower" though.
I didnt point out who, but since you answered, you yourself must think of yourself as a blind follower. One of the main reasons I love Ubuntu and Linux is the freedom it gives. anything that limits that freedom is bad. Those that have blind faith in developers are letting themselves in for a letdown. Developers are human, they make mistakes.

---

### Post by Dimitriid on 2007-09-30
> **fireworksshow said:**
> I agree with you're first point, but I personally think that KDE 4.0 coming out in mid cycle is perfect, it gives enaught time to the developers/betatesters to give kubuntu polish and work out the early bugs. I found out that recently the linux marked started to lose some major bugs in they're distro's because of hurrying new released software without proper testing.

Other distros can extend their release cycles to include and support KDE 4.0 because they are not on a fixed release cycle. Now as it is right now, I also think is good they have more time to "polish" yes but, there is an equally strong argument about jumping out of the gate first and prepared ( botched/broken releases of course only harm themselves ).

But the point was not really that ( my prose is not that good, english being my second language ) but rather the fact that there are already both advantages but disadvantages to a fixed release cycle, adding more disadvantages and having less features to spend that much time on paranoid foolproof security however would add up to existing "shortcomings".

I honestly think that developers should appeal to just 3 basic groups of users
1) Completely hopeless. These people can crash a microwave and send dvd players to blue screen of dead. They need an appliance, not  a computer so their apps and OS should look like that. Media centers come to mind.

2) Proficient users: this users know enough to master a straight forward system like Ubuntu and have enough common sense not to trust whoever tell them "You are our 1 zillion visitor, you already won cash click here!". 

3) Power users and professionals. They might choose an intermediate level like Ubuntu if they are maybe lazy but they know they are capable of anywhere from going Slackware to building their own distro.

Now Ubuntu is fine appealing to group 2. Group 1 will never move out of windows. By trying to win over group 1, which will be a complete failure ( group 1 is easily bullied into windows ) they alienate group 2 by bogging down already croweded and pressing release cycles.

---

### Post by Dimitriid on 2007-09-30
> **ryanVickers said:**
> Idiot-proof doesn't have to mean it's lacking features

Thats more wishful thinking: To idiot proof something you have to inconvenience non-idiots. If non-idiots are not inconvenienced then idiots fill find a way to wreck things because of it. 

Realistically speaking there's just no way to have the cake and eat it like that.

---

### Post by Dimitriid on 2007-09-30
> **fwojciec said:**
> Nothing scary about this discussion, just realistic.  People who want Ubuntu to take over the world usually don't think about the inevitable consequences of this ambition - as popularity of an OS increases the average skill-level of the user base decreases..

Compared to total windows users, the popularity of Linux its NEXT TO NONE. Only dedicated people looking for alternatives find its way to Linux in general. Ubuntu developers with comments like that are just shooting for the impossible. 

Windows is NOT the main OS because of any features, any user friendliness, nothing that has anything to do with the OS itself. Its the dominant because it used economical brute force to shove it down the throats of nearly everybody. 

Honestly I just dont see this argument of some magical exodus of Windows users to Ubuntu happening within the next decade at the very least. There is no indication of it, in fact Microsoft has only increased and perfectioned their bully tactics and managed to force most people to Vista even with strong disapproval all around. They managed to force DRM into everybody, they are even threating the PC platform by attempting to turn it into a useless DRM happy appliance and nothing more. You really think a fugly brown Linux distro with Nelson Mandela and without painfully needed things like mp3 codecs not included by default will even threaten even 1% of Microsoft's market share?

The people who will come to Ubuntu will be ready to not be complete jackasses. If they were they'd probably run back to windows in 5 minutes after not finding "my computer" on this strange brown thing we use.

---

### Post by FyreBrand on 2007-09-30
> **p_quarles said:**
> The measure that was described doesn't take any power away from the user. It simply forces the user to go through more steps to accomplish something that could compromise the computer. There are already many similar measures built in to the typical Linux distro. Some examples:

-A normal user does not have root privileges. 
-If you want to compile something in the absence of the necessary dependencies, you have to override the default behavior
-If you want to delete a directory without getting an earful, you have to type out "rm -Rf"
-To use apt-get to do something dumb, you have to use "--force-yes"

I agree with aysiu on this, that this isn't really a very sensible proposal. All the same, the concerns they have are legitimate, and as near as I can tell they are trying to add some newbie-proof security measures *without* compromising the functionality and power of the system as a whole.
**From the article:**

All of us experts here know that this isn't a good way to proceed.  
But our users don't.  For these reasons, it is up to us to do better.

What might also be OK is selectively permitting the installation of  
software from third parties that we have the right kind of  
relationship with.

The list of approved third parties should be provided by Ubuntu and  
   programmatically enforced by the software

We should consider the position of users who have already approved  
   a particular third pary source which we have revoked -  
   specifically, we should consider what actions of ours would be in  
   the best interests of those users

**End of Article quote**

There is plenty more in that article discussing how the developers know better than the user what they should and shouldn't install and use.  It's way beyond misguided.  It's on the cutting edge of facist.  Remove the word Ubuntu and insert the phrase Microsoft Windows in that article.  If Microsoft published an article like this imagine the response.  I bet it would be very different.

> **Warren Watts said:**
> There are a ***lot*** of folks in the Linux community that feel that Ubuntu has *already* gone too far in regards to making Linux idiot proof.  

All I can say on the subject is that there are plenty of Linux flavors out there, and if as a Linux user you are unhappy with the direction your particular Linux flavor is going, it's not at all difficult to switch to another distro that better suits your needs and personal beliefs about the way you want your OS to treat you.

I personally have Ubuntu installed on the family PC because it is easy to use and user friendly, and use Archlinux  on my personal PC.This is pretty much what I think as well.

> **lisati said:**
> Perhaps we can learn from the developers of anti-spam systems. The last time I checked, Pegasus Mail was able to use "whitelists" and "blacklists" in its message rules to allow and/or block messages from particular senders, and some of the anti-spam products I've checked out have used similar techniques, combined with a form of "quarantine" system that allows you to safely review material from an unknown source, and also combined with a means to learn to distinguish the good from the bad.Maybe I don't want someone deciding what is appropriate software to install on my OS.  This isn't about malware even though it's framed in that charade.  This is about a small group of people putting their stamp of approval on on projects or not.  Is this free and I mean Free software, or is this moving in the direction small projects will have to earn the status to be included?  The overused "Slippery Slope" is put out often around here, but who would have thought it was the developers creating that.

This whole idea is utter rubbish and I'm not very happy about it one bit.

---

### Post by koenn on 2007-09-30
> **Kilz said:**
> . ... That its a personal computer and not a developers computer. The user is the one that should decide what should be allowed to be installed. 

When you think about it, in the case of malware, its the malware-maker that decides what gets installed on your computer, and the user has no idea what's going on. 



> **Kilz said:**
> .
I didnt point out who, but since you answered, you yourself must think of yourself as a blind follower. 
Sounds like a typical troll answer to me. 
[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102) :
[QUOTE=Matthew]]A troll is usually an expert in reusing the same words of its opponents and in turning it against them.[/QUOTE]

---

### Post by nowshining on 2007-09-30
I read nothing of that matter - all I read was to get rid of the pop up asking dialogs to enter the password - what it says is true, however no matter what no one is 100 percent safe on this earth - not even when they are alone with themselves.

---

### Post by koenn on 2007-09-30
> **FyreBrand said:**
> **From the article:**
All of us experts here know that this isn't a good way to proceed.  
But our users don't.  For these reasons, it is up to us to do better.

you should read that in context, it sounds a lot better then : 

> we have been inheriting the idea that it is acceptable to go to a website, find  you need to install some software to use it, and then install that  software provided by that website - and 
the idea that it is a sensible thing for a user to look for zero-cost software via a search engine  and then just install it.  
 
All of us experts here know that this isn't a good way to proceed.  
But our users don't.  For these reasons, it is up to us to do better.  

---

### Post by FyreBrand on 2007-09-30
> **koenn said:**
> you should read that in context, it sounds a lot better then :Ok Let's look at some more "in context".

[quote=Ian Jack$pn]What might also be OK is selectively permitting the installation of  
software from third parties that we have the right kind of  
relationship with.  We would have to think about what the criteria  
might be, but here is a starting point:  
 
* The third party would have to agree in a legally binding way to  
   uphold and not subvert the user's rights on their own computer;  
* The third party would have to commit to provide security updates,  
   where necessary, within a defined timeframe.  
* The list of approved third parties should be provided by Ubuntu and  
   programmatically enforced by the software;  
* We should be able (both contractually and technically) to  
   withdraw/revoke such a third party permission if they turn out  
   in our opinion not to take our users security and privacy  
   seriously;  
* We should think carefully about the user interface for enabling a  
   particular third party, which ought to be an explicit step;  
* We should consider the position of users who have already approved  
   a particular third pary source which we have revoked -  
   specifically, we should consider what actions of ours would be in  
   the best interests of those users.  
 
 
What is of course also necessary is an ability for power users to  
specify additional third-parties without any blessing from Ubuntu.  
However *this facility must not to be accessible to naive users*. [/quote]We can write the whole damn article out for all I care.  It doesn't sound any better "in context" to me at all.  This is written by someone who is **assuming** a lot (he uses the word several times in the article) and that he and the developers are better than ignorant users.

Maybe that's what the Ubuntu community wants, but not me.  Maybe a majority of the community feels it's okay to have decisions made for them about what's an acceptable application, but really it's not for me.  I can't see promoting this at work or in the educational community any longer.  I can only see warning potential users about this.

I have never read something so repugnant.  What's next?  Is there going to be a test to decide how ignorant and naive of a user you are?  Will we have a naive users help section and a "cool guy power user" section?  I don't think so.  I know I'm nothing here and won't be missed, but unless this thinking changes direction, I'm done.

PS: What happened to the Ubuntu I loved?

---

### Post by koenn on 2007-09-30
How about keeping this article in perspective :
1/ the author clearly states it's a personal opinion. So let's keep the generalisations about "the devs" out of it.

2/ the author is clearly floating an idea in porder to get feedback. It's on a publically accessible mailing list, out there for anyone to read.
[if they were facists, they'd know better than that]

3/ the author clearly states the assumptions his conclusion is based on.   If you don't agree, all you need to do is provide proof/indications that one or more of the assumptions are wrong, or demonstrate that the conclusion doesn't follow from the (assumed) premises. 

4/ the author identifies a problem and takes steps towards a sollution. He deserves credit for that. 

5/ the author is aware of the fact that he's dealing with a trade-off between security on one hand, user convenience (both the 'naive new user' and the 'power user who wants control') on the other hand. His proposal attempts to accommodat all these. That makes it a good effort.

---

### Post by koenn on 2007-09-30
> **FyreBrand said:**
>   This is written by someone who is **assuming** a lot (he uses the word several times in the article) and that he and the developers are better than ignorant users.

" ... that he and the developers **know** better than ..."
And he might be right. 


> **FyreBrand said:**
>   What's next?  Is there going to be a test to decide how ignorant and naive of a user you are?
There doesn't need to be, or it's already there. If your skill set doesn't go futher than "I can click a hyperlink and an OK button", and you're unaware of the risks of such behaviour,  you fall in the "naive" category. If you know better than that,  : 
> What is of course also necessary is an ability for power users to  
specify additional third-parties without any blessing from Ubuntu.  

All over ubuntu forums you'll find suggestions that cater towards novice users while leaving 'alternatives' to power users. Add/Remove versus Synaptic versys apt-get. " a less confusing file system hierarchy". Quiet or verbose boots. The --force 'I know what I'm doing" options with several commands (listed earlier in this thread) , the '1 application per task to reduce the confusion for novice users" approach of ubuntu as a distro, ... and on, and on and on. 


All in all, the only thing scary about this article is
> But the alternative is that in 5 years' time our users' systems will  
be malware-infested nightmares.  

---

### Post by Kimm on 2007-09-30
Your all exagerating (I think... I did not read the entire thread)

What this developer is essentially saying is that we should remove gdebi. And thats about it.

Also, if you continue to read the discussion on that website, you'll see that most, if not all others think that this is a bad idea.

---

### Post by bash on 2007-09-30
This is all nice and lovely. Great idea at heart. But oh well not very practical. Im sorry but Ubuntu reps are only updated every 6 months with new software (not program updates but new programs that weren't in the repo before). 

Now take the average user. He or she hears from their friends that program abc is out and they should really try it. This is a legit program. Not talking bout malware here. So well they go to the vendors page and lookie it even has a linux version. They download it but oops. No can do. Install forbidden or highly complicated to achieve. Result: They'll be annoid about Ubuntu and if this keeps happining a couple of times, they switch to something else. Most probably window or OS X.

So unless with this change not also come a new official ubuntu "new software" repo, this change will jut lead to users leaving Ubuntu. And with a new software repo I mean something that contains software that came out after an Ubuntu realese. Preferably  new software should be in this repo a maximum a week after it was released. Maybe something like an extended backpors repo might do the trick. Or integrate getdeb.net into an official ubuntu repo.

---

### Post by Kilz on 2007-09-30
> **koenn said:**
> Sounds like a typical troll answer to me. 
[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102) :

Trolls dont usually have 4000 posts on a forum, 99% of which are in support sections. Maybe thats why I find this whole idea scary, I have helped to make Ubuntu better. It feels like a knife in the back.

> **koenn said:**
> How about keeping this article in perspective :
1/ the author clearly states it's a personal opinion. So let's keep the generalisations about "the devs" out of it.

2/ the author is clearly floating an idea in porder to get feedback. It's on a publically accessible mailing list, out there for anyone to read.
[if they were facists, they'd know better than that]


The author puts it on a closed mailing list that only developers can reply to.

---

### Post by SonicSteve on 2007-09-30
Trolls or no trolls,
I think I get the gist of the what's happening with the devs. I've worked in IT for sometime now.
First though, I don't believe this will ever come to pass. Revoking user access is a classic knee jerk reaction to a security issue. IT managers face it every day. This is the philosophy of group policy management implemented in a Windows Domain environment and as a Pro IT manager I quite appreciate that the students at my school can't monkey with the systems. 

HOWEVER,,
The home user can't be limited in this kind of way. A home user can't be treated as though they are a computer virus. In learning ubuntu I crashed a few installs before I learned what to do and what not to do. That's how I learned, people need the freedom to make these kinds of mistakes. I trust that this DEV who started this "scary discussion" will be set straight. Surely sanity and clear heads will prevail.

---

### Post by koenn on 2007-09-30
> **Kilz said:**
> Trolls dont usually have 4000 posts on a forum, ...  true. 

> **Kilz said:**
> The author puts it on a closed mailing list that only developers can reply to. We all can **read** it, can't we ?

---

### Post by Dimitriid on 2007-09-30
reading it its meaningless if you cannot reply, it means you'll have to go along with whatever they decide without being able to voice opinions, or ( what they'll accomplish if they keep it up ) change distro.

And yes, to whoever it said so, having to change a distro IS a big deal. Just how many times we had an "IN" distro that grows huge and promises to raise the Linux out of complete obscurity? Way too many times and for one reason or another, most just end up fading back instead of getting anywhere. Ubuntu losing support from many users would mean it would lose momentum and it would be another huge setback for Linux awareness in general.

---

### Post by koenn on 2007-09-30
> **SonicSteve said:**
> HOWEVER,,
The home user can't be limited in this kind of way. A home user can't be treated as though they are a computer virus. In learning ubuntu I crashed a few installs before I learned what to do and what not to do. That's how I learned, people need the freedom to make these kinds of mistakes. I trust that this DEV who started this "scary discussion" will be set straight. Surely sanity and clear heads will prevail.
I trust that the dev in question had a genuine concern, is looking for sollutions, and bounces his ideas to fellow devs ... Ain't that how things are done in teams ?

While i not necessarilly agree with the proposed sollution (actually, a vague idea as to what direction a sollution might be found in), I do share the guys concern. When looking at posts on these forums, i too get visions of malware-infested and zombified ubuntu systems.

---

### Post by Dimitriid on 2007-09-30
I do not, I already stated this many times: linux as a whole is not popular enough to be this paranoid. Ubuntu on its own, much much less likely to be a target. You guys need to get realistic about where we stand. You don't need more proof but the article to know the devs themselves are not being realistic about the possibilities of targeted security threats. 

Developers cannot afford to be that naiive, neither should users. I just simply think there is no need for this, there is no need to fix things that are not broken, this is specially true if this will end up breaking other things in the process.

---

### Post by Tomosaur on 2007-09-30
Uhh, how about we just fork gDebi and and incorporate user-specified white-lists about where they wish to install software from? AdBlock is the model we need to look at here, not some stupid Trusted Computing malarkey. The most you can ever hope to do is warn people that what they're about to do is potentially dangerous - it's just that currently, Ubuntu doesn't do this very well at all. All we really get is a 'Enter your password' dialog, not some check that the .deb in question is from a whitelisted source (or even just included in a blacklist), a **warning** (not an outright ban on that .deb) that harm could come to your system if you continue, and then some 'inconveniencing' wait time - like Firefox's add extension dialog, before the 'Next' button is available to click. All of this should be turned on by the default Ubuntu installation, and able to be turned off if the user wants to.

We do not need Canonical / the Ubuntu devs babysitting us and censoring us from the big bad world, but I'm sure many would appreciate a more visible warning about potential harm.

---

### Post by Buffalo Soldier on 2007-09-30
For those who want this feature, there's Ubuntu. For those who don't, there's always the mothership Debian.

---

### Post by fwojciec on 2007-09-30
> **koenn said:**
> How about keeping this article in perspective :
1/ the author clearly states it's a personal opinion. So let's keep the generalisations about "the devs" out of it.

2/ the author is clearly floating an idea in porder to get feedback. It's on a publically accessible mailing list, out there for anyone to read.
[if they were facists, they'd know better than that]

3/ the author clearly states the assumptions his conclusion is based on.   If you don't agree, all you need to do is provide proof/indications that one or more of the assumptions are wrong, or demonstrate that the conclusion doesn't follow from the (assumed) premises. 

4/ the author identifies a problem and takes steps towards a sollution. He deserves credit for that. 

5/ the author is aware of the fact that he's dealing with a trade-off between security on one hand, user convenience (both the 'naive new user' and the 'power user who wants control') on the other hand. His proposal attempts to accommodat all these. That makes it a good effort.

Exactly.  I read it the same way you did, and I thought the discussion expressed a reasonable concern.  Some people here seem to be oversensitive or just not very realistic/practical at all.

---

### Post by fwojciec on 2007-09-30
> **Dimitriid said:**
> I do not, I already stated this many times: linux as a whole is not popular enough to be this paranoid. Ubuntu on its own, much much less likely to be a target. You guys need to get realistic about where we stand. You don't need more proof but the article to know the devs themselves are not being realistic about the possibilities of targeted security threats. 

Developers cannot afford to be that naiive, neither should users. I just simply think there is no need for this, there is no need to fix things that are not broken, this is specially true if this will end up breaking other things in the process.

Ubuntu (and Linux in general) has been gaining popularity *rapidly* in recent 2 years or so, and if the trend continues, and it is not unreasonable to assume that it will, security is going to become a much larger problem for Linux desktop users, and the most popular Linux distros like Ubuntu are likely to be targeted specifically.  You can afford to live in the moment and with a false sense of security - developers can't, or at least shouldn't IMO.

---

### Post by Frak on 2007-09-30
> **Buffalo Soldier said:**
> For those who want this feature, there's Ubuntu. For those who don't, there's always the mothership Debian.
Very true, just a little more time to get it done, but it still is the same thing underneath.

---

### Post by ryanVickers on 2007-09-30
Maybe they'll not do it if they realize so many people are ready to jump ship just like that if they do it!!!

---

### Post by Kilz on 2007-09-30
> **ryanVickers said:**
> Maybe they'll not do it if they realize so many people are ready to jump ship just like that if they do it!!!

The thing is, Im quite happy with Ubuntu as it is now. I have invested a lot of time learning how to make it just as I want it. I guess if I did go to another distro I would choose a debian based one. I just hope that they dont do this to the next long term release. That way it would give plenty of time to look into other options.

---

### Post by NullHead on 2007-09-30
> **Kilz said:**
> The thing is, Im quite happy with Ubuntu as it is now. I have invested a lot of time learning how to make it just as I want it. I guess if I did go to another distro I would choose a debian based one. I just hope that they dont do this to the next long term release. That way it would give plenty of time to look into other options.

I would go to Debian ... maybe Mepis ... Free BSD looks nice ... All in all it's very sad if Ubuntu turns into an empire like Microsoft.

---

### Post by the yawner on 2007-09-30
Hmm...

- The author of the letter is just one of the developers. His opinion does not represent the the dev's position. Thus, even though we do not have the privilege to voice out our concerns, I'm sure there will be always be at least one amongst their ranks that will.

Besides, the proposal was just at its beginnings. I don't think the correct flow to discuss it would include immediate inclusion of users. That in my opinion would be chaotic, and whatever valid points the proposal may have would likely be lost in the midst of repetitive opinions.

- While it's not exactly a threat right now due to the minor popularity of Ubuntu (and other distros) compared to the main competition- I share the author's belief that it will be a problem some time later in the future. Could be 5 years from now, or ten years, a century or so. It might not even be Ubuntu's problem (if another distro manages to supplant Ubuntu's lead and topples the other OS out there). Heck, even proponents from the *other side* use it as an argument and I've yet to find anything solid to counter that.

=====

On another note...  How about you guys? Some of you are frequent here in this community. What's stopping you from creating a community-supported list of third party software and its sources/repositories?

---

### Post by Kilz on 2007-10-01
> **the yawner said:**
> Besides, the proposal was just at its beginnings. I don't think the correct flow to discuss it would include immediate inclusion of users. That in my opinion would be chaotic, and whatever valid points the proposal may have would likely be lost in the midst of repetitive opinions.



Ya, those pesky users might just say something that stops this dead in its tracks. Why listen to them, or let them voice an opinion. :roll:

---

### Post by Frak on 2007-10-01
> **Kilz said:**
> Ya, those pesky users might just say something that stops this dead in its tracks. Why listen to them, or let them voice an opinion. :roll:
Yes, but they can talk the talk, but I doubt they could walk the walk.

---

### Post by Sayers on 2007-10-01
If this happens which it wont , I'd go to debian.

---

### Post by NJC on 2007-10-01
I read the article and the proposal doesn't frighten me. This seems a reasonable and worthwhile pursuit (from article):

> Or to put it another way: the point of Ubuntu is to give users control  
over their own computers - that is, Freedom.  Our job includes  
defending that control against those who would risk it in the name of  
temporary convenience.  


---

### Post by Ozor Mox on 2007-10-01
The paranoia on this thread is something else...

---

### Post by Kilz on 2007-10-01
> **NJC said:**
> I read the article and the proposal doesn't frighten me. This seems a reasonable and worthwhile pursuit (from article):

Kind of a strange way of putting freedom. The freedom to only install  software from sources that are approved. Sounds like something Microsoft would come up with.
Thats trading freedom for security. Each time I have seen this happen you loose freedom and never get security.
Lets see how it sounds when applied to something else. 
Lets improve breathing by limiting the sources of air.

---

### Post by p_quarles on 2007-10-01
Kilz: You're not listening to what anyone is saying. Stop with the "this is too much like Microsoft" and the "they're taking freedom away from users." It's silly.

1. The proposal (did you read the article?) would not take any freedom away. It would eliminate "click-through" installers from the default installation. I don't think this is a particularly good idea, but it doesn't stop you from a) Using appropriate and secure methods to install whatever you want, and b) Installing the click-through installers themselves.

2. The reason the devs don't allow everyone to sign up for their mailing list is that it would simply become flooded with spam, half-baked ideas, repetitious feature requests, etc., etc. It would become unusable. That's not "shutting you out," it's getting work done. 

I think I've spelled it out pretty clearly here. You can either continue to misrepresent the views of those of us who aren't "scared" by the article you linked to, or you can address my points intelligently. Your choice.

---

### Post by fwojciec on 2007-10-01
> **Kilz said:**
> Lets improve breathing by limiting the sources of air.

Well, this actually happens, in case you didn't know, and it's good that there are measures out there that try to limit air pollution.

---

### Post by Frak on 2007-10-01
> **Kilz said:**
> Kind of a strange way of putting freedom. The freedom to only install  software from sources that are approved. Sounds like something Microsoft would come up with.
Thats trading freedom for security. Each time I have seen this happen you loose freedom and never get security.
Lets see how it sounds when applied to something else. 
Lets improve breathing by limiting the sources of air.
"Those who would sacrifice essential liberties for a little temporary safety deserve neither liberty nor safety" - Benjamin Franklin

---

### Post by Kilz on 2007-10-01
> **p_quarles said:**
> Kilz: You're not listening to what anyone is saying. Stop with the "this is too much like Microsoft" and the "they're taking freedom away from users." It's silly.

1. The proposal (did you read the article?) would not take any freedom away. It would eliminate "click-through" installers from the default installation. I don't think this is a particularly good idea, but it doesn't stop you from a) Using appropriate and secure methods to install whatever you want, and b) Installing the click-through installers themselves.

2. The reason the devs don't allow everyone to sign up for their mailing list is that it would simply become flooded with spam, half-baked ideas, repetitious feature requests, etc., etc. It would become unusable. That's not "shutting you out," it's getting work done. 

I think I've spelled it out pretty clearly here. You can either continue to misrepresent the views of those of us who aren't "scared" by the article you linked to, or you can address my points intelligently. Your choice.

1. It isnt an article, its an email in an archive. Yes I read it.
Conclusion: Ubuntu systems should not provide a smooth `click through'  
route to the installation of untrustworthy software.  
 
"Untrustworthy software includes all software which we don't have some  
reason to trust.  This means:  
 
* No click-through installation of downloaded .debs  
* No click-through addition of arbitrary apt repositories or keys  
* No click-through installation of arbitrary browser plugins  
* No click-through addition of PPAs without further policy controls "

This says to me that they are going to limit easy install of downloaded debs and installation of apt repositories. That is limiting innstall sources, Why?

"Firstly, I would assert that we are largely responsible for the  
security of Ubuntu users' systems:  
 
We cannot assume that our users are sufficiently knowledgeable and  
experienced to know what is and is not an acceptable risk to take."

The developers know more than us dumb users on what should be easy to install. If I download a deb, I want to install it. It should be as easy as can be, since its my computer. I make the call as to what to install. Thats freedom.

2. I guess you dont know the history of that mail list. Its never had spam. It was open until last version.

I'm not misrepresenting anything. I think you may not have enough knowledge to know a mail list archive from a article, or the lists past history.

---

### Post by Kilz on 2007-10-01
> **fwojciec said:**
> Well, this actually happens, in case you didn't know, and it's good that there are measures out there that try to limit air pollution.

I was not talking about pollution and you know it. Thats just spin.

Try this , limit your air intake, Put a plastic bag tightly over your head and try to breath.

---

### Post by Frak on 2007-10-01
> **Kilz said:**
> I was not talking about pollution and you know it. Thats just spin.

Try this , limit your air intake, Put a plastic bag tightly over your head and try to breath.
Puts less Carbon-Dioxide into the air ;)

---

### Post by p_quarles on 2007-10-01
@Kils: There you go again, attacking people instead of offering even the faintest outline of an argument. Yes, I misspoke: it's an e-mail. 

Now, can you please be specific about which of the [four software freedoms]("http://www.gnu.org/philosophy/free-sw.html") [gnu.org] would be compromised in the event that this *proposal* were ever to be implemented in an official Ubuntu release? 

So far, you've said "dude, I wasn't talking about you, so I guess you must consider yourself a blind follower" and "dude, you think that's an article? You're dumb." This is flamebait, and if you do any more of it in this thread, you're getting reported. Now: please look at my argument and try to respond like a civilized interlocuter.

---

### Post by 23meg on 2007-10-01
[QUOTE=Kilz]2. I guess you dont know the history of that mail list.[/QUOTE]

And neither do you.

Last year when the signal to noise ratio went low, posts from non-developers started to be moderated. For non-moderated discussion, which is still followed (though less frequently, which was the whole point) and replied to by the developers, a separate list called ubuntu-devel-discuss was started. 

This means that your relevant replies that have some merit to whatever is posted ubuntu-devel can still go through to ubuntu-devel, or in the worst case, you can post to ubuntu-devel-discuss, which is still frequented by the developers. 

[QUOTE=Kilz] Its never had spam.[/QUOTE]

How about addressing the rest of what p_quarles is saying?

[QUOTE=p_quarles]spam, half-baked ideas, repetitious feature requests, etc., etc.[/QUOTE]

Did it become flooded with half-baked ideas and repetitious feature requests or not? Did it start to host arguments between non-developers, matters of personal opinion and even flame wars, that belong to the sounder or ubuntu-users mailing lists, or not? Did people post their technical support questions to ubuntu-devel with the hope of getting "the best possible help" "straight from the developers" or not?

[QUOTE=Kilz] Last year when someone asked questions it was closed.[/QUOTE]

Asked what kind of questions? Technical support? Whether feature foo will be included in the next release? May those have been considered as factors lowering the signal to noise ratio of the list and making it inefficient?
 
The purpose of the list is communication and discussion between the people who actually do the work. If people's ability to do the work is inhibited by so called noise, it's an acceptable solution to switch to moderated mode, and start a separate unmoderated mailing list. It's been done in many  other places. It has nothing to do with censoring people or not wanting to listen to people's opinions, but of course, for people who distort facts to make a storm in a teacup, it's perfect bait.

There's nothing keeping anyone from posting to ubuntu-devel-discuss or joining #ubuntu-devel on Freenode to get involved in development discussions.

---

### Post by multifaceted on 2007-10-01
My lack of developing knowledge impedes my ability to make a vaible rebuttal or even a reply...

I must say, if this is in fact a prospect on the horizon... I don't know what I'll do. Reasons like this are why I ditched Windows in the first place!

Yes, I still seldom use WinXP but, it is strictly for my Adobe and recording apps... the internet does not touch that install.

---

### Post by aysiu on 2007-10-01
> **Kilz said:**
> 
The developers know more than us dumb users on what should be easy to install. If I download a deb, I want to install it. It should be as easy as can be, since its my computer. I make the call as to what to install. Thats freedom. Actually, the original email to the mailing list made it clear that it would still allow you to override the clickthrough process so as not to limit power users (i.e., people like you, kilz; not "us dumb users").

I'll quote it for you, since you seem to pay attention to only parts of the email that would stir the most controversy and paranoia: > What is of course also necessary is an ability for power users to  
specify additional third-parties without any blessing from Ubuntu.  
However *this facility must not to be accessible to naive users*.

As I said before, this is a typical Gnome mentality: don't make it easy to deviate from the sensible defaults, but keep deviation as an available option for those who can be bothered. Just think about assigning keyboard shortcuts for commands that aren't already in System > Preferences > Keyboard Shortcuts. Sure, it can be done, but it can't be done easily unless you know exactly what you're doing (and aren't intimidated by *gconf-editor*).

And, as I said before, I don't agree with the proposal, but it is by no means "scary." It's just a backwards way of approaching the problem (frontwards would be educating users, not thinking for them).

---

### Post by Kilz on 2007-10-02
> **p_quarles said:**
> @Kils: There you go again, attacking people instead of offering even the faintest outline of an argument. Yes, I misspoke: it's an e-mail. 

Now, can you please be specific about which of the [four software freedoms]("http://www.gnu.org/philosophy/free-sw.html") [gnu.org] would be compromised in the event that this *proposal* were ever to be implemented in an official Ubuntu release? 

So far, you've said "dude, I wasn't talking about you, so I guess you must consider yourself a blind follower" and "dude, you think that's an article? You're dumb." This is flamebait, and if you do any more of it in this thread, you're getting reported. Now: please look at my argument and try to respond like a civilized interlocuter.

No one attacked anyone, if you feel you were attacked report it. You are adding things. Just because I dont sugar coat something doesnt make it flaimbait or an attack. 

As for what freedom. Thats easy it gets in the way of 

The freedom to redistribute copies so you can help your neighbor (freedom 2). 
if the user I give a deb to has a hard time installing it because someone made it harder than it was before.

---

### Post by Kilz on 2007-10-02
> **aysiu said:**
> Actually, the original email to the mailing list made it clear that it would still allow you to override the clickthrough process so as not to limit power users (i.e., people like you, kilz; not "us dumb users").

I'll quote it for you, since you seem to pay attention to only parts of the email that would stir the most controversy and paranoia: 

As I said before, this is a typical Gnome mentality: don't make it easy to deviate from the sensible defaults, but keep deviation as an available option for those who can be bothered. Just think about assigning keyboard shortcuts for commands that aren't already in System > Preferences > Keyboard Shortcuts. Sure, it can be done, but it can't be done easily unless you know exactly what you're doing (and aren't intimidated by *gconf-editor*).

And, as I said before, I don't agree with the proposal, but it is by no means "scary." It's just a backwards way of approaching the problem (frontwards would be educating users, not thinking for them).

Making it hard even for new users is wrong imho. Perhaps we agree on that. But I find the talk of limiting freedom for anyone scary. 
Imho if you are quiet and lets someone step on others freedoms it isnt long before you yourself loose them

---

### Post by Kilz on 2007-10-02
> **23meg said:**
> And neither do you.

Last year when the signal to noise ratio went low, posts from non-developers started to be moderated. For non-moderated discussion, which is still followed (though less frequently, which was the whole point) and replied to by the developers, a separate list called ubuntu-devel-discuss was started. 

This means that your relevant replies that have some merit to whatever is posted ubuntu-devel can still go through to ubuntu-devel, or in the worst case, you can post to ubuntu-devel-discuss, which is still frequented by the developers. 



How about addressing the rest of what p_quarles is saying?



Did it become flooded with half-baked ideas and repetitious feature requests or not? Did it start to host arguments between non-developers, matters of personal opinion and even flame wars, that belong to the sounder or ubuntu-users mailing lists, or not? Did people post their technical support questions to ubuntu-devel with the hope of getting "the best possible help" "straight from the developers" or not?



Asked what kind of questions? Technical support? Whether feature foo will be included in the next release? May those have been considered as factors lowering the signal to noise ratio of the list and making it inefficient?
 
The purpose of the list is communication and discussion between the people who actually do the work. If people's ability to do the work is inhibited by so called noise, it's an acceptable solution to switch to moderated mode, and start a separate unmoderated mailing list. It's been done in many  other places. It has nothing to do with censoring people or not wanting to listen to people's opinions, but of course, for people who distort facts to make a storm in a teacup, it's perfect bait.

There's nothing keeping anyone from posting to ubuntu-devel-discuss or joining #ubuntu-devel on Freenode to get involved in development discussions.

Nice attempt at revisionist history.

---

### Post by p_quarles on 2007-10-02
> **Kilz said:**
> No one attacked anyone, if you feel you were attacked report it. You are adding things. Just because I dont sugar coat something doesnt make it flaimbait or an attack. 
I don't "feel" attacked, and my feelings are not hurt. I was simply pointing out that you are behaving inappropriately, and I stand by that. Go back and read your posts.

> As for what freedom. Thats easy it gets in the way of 

The freedom to redistribute copies so you can help your neighbor (freedom 2). 
if the user I give a deb to has a hard time installing it because someone made it harder than it was before.
Nonsense. It's quite easy to run dpkg to install a .deb from the command line. By the same token, just because I have the freedom to drive a car does not mean that I should be allowed to do so without any kind of training or licensing. 

The issue here boils down to what I believe is a very poor understanding on your part of the meaning of "freedom." It's not the same as convenience, and it's never unconditional.

---

### Post by 23meg on 2007-10-02
> **Kilz said:**
> Nice attempt at revisionist history.

Nice attempt at a charismatic one liner due to lack of a counter argument.

---

### Post by eentonig on 2007-10-02
I really don't see the reason why this stirrs up so much emotions. Isn't this the way how all significant linux development has been done in the past?

1. Somebody recognizes a problem/solution and voice his concerns.
>> People have the opportunitie to discuss whether his concerns are legit or not.
2. Proposes a solution for discussion. Maybe already knowing that it is NOT the ideal solution, but to get discussion going
>> Other people discuss this solution, point out obvious flaws, propose alternate workarounds, solution, ....
3. A blueprint is written to get going on implementation
>> Again this is reviewed and commented on.
4. ....

There is no decission taken yet. Someone had a (genuine) concern and is trying to find a solution for it. Maybe his way of thinking is flawed, but then he will be pointed out to his flaws by the community. Sometimes, to come to a good solution, you have to start your thinking from a thing you know is bad, but by reviewing it's flaws, you end up with somethin usefull. But you never get their alone. You always listen to the pro's and contra's being raised by everyone involved. In this case devs, users, system admins, Canonical, ...
This is one of the reasons why Linux is amongst the safest OS existing. Because all security matters have been discussed extensively and been reviewed from different angles.

If you don't like debating/discussion, then linux isn't for you.

---

### Post by toupeiro on 2007-10-02
This one is a tough call, given the fact I can see the incentive in what they are wishing to accomplish..  However, One change in this direction stems another, and another, until you've made Ubuntu as debilitating as windows.  In the end, I think the developers are crossing the line if they would ultimately choose to inhibit functionality over fear in a free and Open source Operating System.  The last I checked, (which was a few days ago) the first time you fire up a terminal window in a fresh installation of ubuntu, you are presented with the ABSOLUTELY NO WARRANTY disclaimer,  Let me then, hold the responsibility of my actions and level of awareness.

 Awareness is the solution to this problem.  Making a solution tailored to the concept of "it just works" more difficult to use is not the right answer.  If I want fear as a technological driver over innovation, I'll go back to running Windows.

ok, I won't go that far, :) but more likely, another Linux distribution lacking the self-assigned moral obligation to protect me from myself.

---

### Post by the yawner on 2007-10-02
@Kilz
Curious. May I know your exact position on the matter if it's all right with you?
1. Do you agree about the problem the letter presented has merits?
2. If so, how do you think should they solve it?

And on another note. Do you think these same developers are not giving you enough freedom by providing you with a distro that comes in a live CD with pre-selected software?

---

### Post by conehead77 on 2007-10-02
> **Kilz said:**
> Making it hard even for new users is wrong imho. Perhaps we agree on that. But I find the talk of limiting freedom for anyone scary. 
Imho if you are quiet and lets someone step on others freedoms it isnt long before you yourself loose them

Following this logic, is sudo also too much a limitation for new users? Maybe its too hard for new users to edit a Textfile with sudo? lets just have everybody as root by default, cos thats where you get the most freedom.

This whole discussion is all about how Ubuntu should be by default, completely customizable for an advanced user.

I use Ubuntu for some months now and i only needed an external repository once, for making DVDs work.
If i had the choice, i would probably limit myself to official repositories only, on my main installation.

As for the initial statement, i dont see anything scary.

---

### Post by frodon on 2007-10-02
> **Kilz said:**
> Making it hard even for new users is wrong imho. Perhaps we agree on that. But I find the talk of limiting freedom for anyone scary. 
Imho if you are quiet and lets someone step on others freedoms it isnt long before you yourself loose themI think it is an interpretation of the email (a really negative one IMO), i have a totally different interpretation and not see anything limiting or/and damaging our freedom.
All of what i read sounds really positive to me.

I have to confess that i'm a bit surprised by this in your first post :
> **Kilz said:**
> IThat the developers know more than users what is safe Because the answer is obviously yes for me and i thank the devs to create systems which prevent me to do unsafe things if i'm not enough knowledgable to know exactly what i do and why i'm doing it.

---

### Post by Kilz on 2007-10-02
> **p_quarles said:**
> I don't "feel" attacked, and my feelings are not hurt. I was simply pointing out that you are behaving inappropriately, and I stand by that. Go back and read your posts.


Nonsense. It's quite easy to run dpkg to install a .deb from the command line. By the same token, just because I have the freedom to drive a car does not mean that I should be allowed to do so without any kind of training or licensing. 

The issue here boils down to what I believe is a very poor understanding on your part of the meaning of "freedom." It's not the same as convenience, and it's never unconditional.

I disagree, maybe if the easy install method never existed you can say that. But when its taken away, thats a different story.
It would be like , yes you have the freedom to drive a car. But the car makers are going to take the gas cap and mount it under a riveted steel panel. Maybe even remove the gas cap completely. Then they are going to install a special port that you can only buy fuel from one site, that is owned by the car makers.

> **the yawner said:**
> @Kilz
Curious. May I know your exact position on the matter if it's all right with you?
1. Do you agree about the problem the letter presented has merits?
2. If so, how do you think should they solve it?

And on another note. Do you think these same developers are not giving you enough freedom by providing you with a distro that comes in a live CD with pre-selected software?

1. I think its a problem other os's have (Windows) But they also have other problems that may be the root of the problem (everyone runs as an admin). I dont think its clear that Linux will ever have that problem.
2. I think education and information are the ways to solve it if it ever is a concern. Not removing parts that make it easier for users. After all Ubuntu is supposed to be easy for new users, should the developers take what is easy now and make it harder?

Another note, yes, I kind of like it, as a base install. But there are lots of things that need to be added, some of which are not in the Ubuntu repos.

> **frodon said:**
> I think it is an interpretation of the email (a really negative one IMO), i have a totally different interpretation and not see anything limiting or/and damaging our freedom.
All of what i read sounds really positive to me.

I have to confess that i'm a bit surprised by this in your first post :
Because the answer is obviously yes for me and i thank the devs to create systems which prevent me to do unsafe things if i'm not enough knowledgable to know exactly what i do and why i'm doing it.
I dont think I could have that much faith in a human. Lets also remember that the developers are suggesting limiting ALL outside installs, that includes good useful software. Application updates that may not be in the repos, beta software, extensions for Firefox. To me it sounds like lets through the baby out with the bathwater.

---

### Post by the yawner on 2007-10-02
> **Kilz said:**
> Then they are going to install a special port that you can only buy fuel from one site, that is owned by the car makers.
Uhm, do you mean to say that Ubuntu/Canonical will eventually find a way to milk some money out of this distro which will be in contradiction with their social contract. Pllease elaborate.

> 
1. I think its a problem other os's have (Windows) But they also have other problems that may be the root of the problem (everyone runs as an admin). I dont think its clear that Linux will ever have that problem.
Yes, at the coming months I don't think it would be a problem. As a user, I wouldn't worry about that myself. But if I was part of the development, I'd rather be prepared. Don't you think so?

Actually, I think it's not just Ubuntu's problem. It may also affect the other distros aiming to be user-friendly.

> 
2. I think education and information are the ways to solve it if it ever is a concern. Not removing parts that make it easier for users. After all Ubuntu is supposed to be easy for new users, should the developers take what is easy now and make it harder?
Now here's the tricky part. How do we convince people that they should learn the essentials of Ubuntu and Linux? That they should take the responsibility of keeping their systems away from bad programs. The most basic users want easy most of the time. So, how do you instill in them the importance of self-vigilance? Especially the stubborn ones, and the ones that are not so technical. Won't that affect their user experience as well? I mean, they have been told that the system is very secure, and now they're told it will be secure for as long as they, the users, make it so.

=====
> 
Another note, yes, I kind of like it, as a base install. But there are lots of things that need to be added, some of which are not in the Ubuntu repos.
Can I assume then that most of the decisions the devs have made are okay with you?

---

### Post by frodon on 2007-10-02
> **Kilz said:**
> I dont think I could have that much faith in a human. Lets also remember that the developers are suggesting limiting ALL outside installs, that includes good useful software ...This is where starts the paranoia .... 
Developers make sometimes, like anyone, some mistakes but i can affirm you that there are not such bad intend anywhere in the ubuntu community.

---

### Post by ssam on 2007-10-02
i am sorry if this has aready been posted.

the disucsion on the mailing list is about whether or not to add a system by which users can trigger apt to install a package by clicking a link on a website.

it is not a plan to make it more difficult for users to install 3rd party apps.

please read [https://wiki.ubuntu.com/AptFirefoxFileHandler](https://wiki.ubuntu.com/AptFirefoxFileHandler)

---

### Post by 23meg on 2007-10-02
[QUOTE=frodon]Developers make sometimes, like anyone, some mistakes but i can affirm you that there are not such bad intend anywhere in the ubuntu community.[/QUOTE]

And the worst thing about this thread is that it begins with such an assumption: that the Ubuntu developers have malicious intentions against users. This must sound ridiculous to anyone who's even barely acquainted with the people behind Ubuntu. From the first post:

[QUOTE=Kilz]This is a discussion on how to make it difficult for users to install 3rd party applications under the guise that some may be malware.[/QUOTE]

This sentence assumes that the main intention in the discussion is "How can we make it more difficult for users to install 3rd party applications?", and the fact that some of these applications may be malware is *used as an excuse* to make this happen. In other words, as this sentence tries to lead people to think, the intention of protecting people from common malware, which is the main point the OP argues against, is secondary to the more important goal: to make it difficult to install 3rd party applications.

---

### Post by wolfger on 2007-10-02
> **the yawner said:**
> The letter has some valid points. If there's anything that can break through the most secure system, it's social engineering. So, how do you protect your users from themselves?
You don't. It's not possible without destroying the system. You can *warn* your users, which is about as effective as they are smart and cautious, or you can take their freedom/power (one in the same, really) away and turn Ubuntu to crap, which is 100% effective: much like poking a person's eyes out is a 100% effective way of preventing them looking at x-rated pictures.

To those who point out (correctly, I'm sure) that the dev's are not thinking these thoughts out of malice or other dark motive, I have but one quote:

"Of all tyrannies, a tyranny exercised for the good of its victims may be the most oppressive. It may be better to live under robber barons than under omnipotent moral busybodies. The robber baron's cruelty may sometimes sleep, his cupidity may at some point be satiated; but those who torment us for our own good will torment us without end, for they do so with the approval of their own conscience."
-- C.S. Lewis

---

### Post by koenn on 2007-10-02
> **wolfger said:**
> 
"Of all tyrannies, a tyranny exercised for the good of its victims may be the most oppressive. It may be better to live under robber barons than under omnipotent moral busybodies. The robber baron's cruelty may sometimes sleep, his cupidity may at some point be satiated; but those who torment us for our own good will torment us without end, for they do so with the approval of their own conscience."
-- C.S. Lewis
That Lewis guy makes sense, but seriously, do you think we're discussing tyranny here ?

If your governement imposes speed limits to reduce traffic accidents and makes wearing seat belts in cars compulsory to reduce the risk of fatal injuries when youre driving, does that make them tyrants ? 

And if parents baby-proof their house, are they taking away the baby's freedom ?

---

### Post by p_quarles on 2007-10-02
> **wolfger said:**
> You don't. It's not possible without destroying the system. You can *warn* your users, which is about as effective as they are smart and cautious, or you can take their freedom/power (one in the same, really) away and turn Ubuntu to crap, which is 100% effective: much like poking a person's eyes out is a 100% effective way of preventing them looking at x-rated pictures.

To those who point out (correctly, I'm sure) that the dev's are not thinking these thoughts out of malice or other dark motive, I have but one quote:

"Of all tyrannies, a tyranny exercised for the good of its victims may be the most oppressive. It may be better to live under robber barons than under omnipotent moral busybodies. The robber baron's cruelty may sometimes sleep, his cupidity may at some point be satiated; but those who torment us for our own good will torment us without end, for they do so with the approval of their own conscience."
-- C.S. Lewis
As ssam just pointed out, the discussion was about implementing a *new *feature, and one of the developers was concerned that this new feature might make a tempting target for the black hats. 

Getting all self-righteous about "freedom" ( !=power, by the way) or "tyranny" in this case is just way off the mark. I'll reiterate two points:
1) Every distro of Linux already implements numerous features which make it more difficult for users to destroy their system or unwittingly allow it become compromised. We all benefit from these features, whether we realize it or not.
2) It's _open source software_. The only barrier to doing anything you want to it/with it is your own level of knowledge. No Ubuntu developer can "tyrannize" you by offering a feature which you don't like. You don't even have to be a very advanced user to put together your own customized installation of Ubuntu or whatever other distro you like. 

Anyone who can complain about the "tyranny" of Linux developers and still take themselves seriously needs to think really hard about what real tyranny looks like, and then compare the two.

---

### Post by wolfger on 2007-10-02
> **koenn said:**
> That Lewis guy makes sense, but seriously, do you think we're discussing tyranny here ?

If your governement imposes speed limits to reduce traffic accidents and makes wearing seat belts in cars compulsory to reduce the risk of fatal injuries when youre driving, does that make them tyrants ? 
Yes. :-)
Seriously, I hate seatbelt laws (people wanna be stupid, let 'em).
Speed limits are something else entirely. The government doesn't impose a speed limit on you to keep **you** safe, it does so to keep **me** safe! Nothing you can install on your computer makes me less safe, so go for it!

> And if parents baby-proof their house, are they taking away the baby's freedom ?
Yes, absolutely. But do you think babies should have freedom? If so, you're in the minority.

---

### Post by wolfger on 2007-10-02
> **p_quarles said:**
> "freedom" ( !=power, by the way)
You're absolutely wrong about that. I'd love to explain why, but that's getting way off topic. ;-)

> 2) It's _open source software_. The only barrier to doing anything you want to it/with it is your own level of knowledge. No Ubuntu developer can "tyrannize" you by offering a feature which you don't like.
Well, there you go. No dev can tyranize me, because I have power ;-)
The devs *can* tyranize Joe Desktop, though, because Joe Desktop doesn't know his CLI from his CIA. Speaking out against loss of freedom doesn't necessarily mean it's *my* freedom that's at stake.

> Anyone who can complain about the "tyranny" of Linux developers and still take themselves seriously needs to think really hard about what real tyranny looks like, and then compare the two.
Tyranny is a quality, not a quantity. :guitar:

---

### Post by p_quarles on 2007-10-02
> **wolfger said:**
> Tyranny is a quality, not a quantity.
Correct. And I was asking you to think about precisely the qualitative difference between tyranny and an open source software security policy.

---

### Post by 23meg on 2007-10-02
From the second post in the discussion:

[QUOTE=Ian Jackson]Our users' collective ability to escape our control is one thing that
keeps us honest.  Another of course is our own conscience but I hope
you'll agree that what I'm proposing here is very much that we should
exercise that conscience.[/QUOTE]

Tyrants aren't known for their willingness to hold open discussions about their policies, or be willing to let those whom they set out to tyrannize escape those policies upfront.

I think this simple fact needs more emphasis: nobody is setting out to lock anyone out of anything in the sense that Microsoft and Apple are locking their users out of certain software and services. People are simply discussing measures to prevent problems that are present today, which will presumably grow at least as fast as Ubuntu grows. 

[QUOTE=p_quarles]
2) It's open source software. The only barrier to doing anything you want to it/with it is your own level of knowledge. No Ubuntu developer can "tyrannize" you by offering a feature which you don't like. You don't even have to be a very advanced user to put together your own customized installation of Ubuntu or whatever other distro you like.[/QUOTE]

From the first post:

[QUOTE=Ian Jackson]What is of course also necessary is an ability for power users to
specify additional third-parties without any blessing from Ubuntu.
However *this facility must not to be accessible to naive users*.[/QUOTE]

The line of thinking here is that there should be a facility to enable the user to override the SAFTM (Scary Anti-Freedom Tyranny Mechanism) which is easily discoverable and usable by power users, but out of reach of inexperienced users. In other words, SAFTM's killswitch would be in the hands of the user, not the vendor, and the user wouldn't have to modify source code to get unrestricted functionality.

Microsoft, huh?

---

### Post by wolfger on 2007-10-02
> **23meg said:**
>  The line of thinking here is that there should be a facility to enable the user to override the SAFTM (Scary Anti-Freedom Tyranny Mechanism) which is easily discoverable and usable by power users, but out of reach of inexperienced users.
That sounds very reasonable to me, a power user... but how does that sound to inexperienced users, which by definition includes everybody who is new to Ubuntu Linux? I can see the forums filling up already with cries of "Ubuntu sucks because it won't let me do X", followed by somebody explaining how to do X, and at that point you've added zero security, and given some noob a bad first impression of the OS, while providing the rest of us a minor inconvenience. That's my take on the situation, at least. I'm gonna shut up and go away now, because I don't think there's anything else to say. Opinions stated. ;-)

---

### Post by 23meg on 2007-10-02
[QUOTE=wolfger]Nothing you can install on your computer makes me less safe, so go for it![/QUOTE]

Malicious software installed by a third party on your computer can send thousands of spam mail per day, without you even knowing about it. Part of the spam you're seeing in your inbox everyday is almost certainly coming from botnets made up by infested Windows machines being used to send spam, without their non-security-conscious owners even knowing about it. The fact that neither your OS vendor, nor you were unable to secure your computer would cost thousands of people valuable time and energy that they could have used for other things than filtering out spam. Come to think of it, it might actually inhibit some of their *freedoms*.

Just some food for thought.

---

### Post by aysiu on 2007-10-02
I give up. If people want to paranoid and scared about this, they can be paranoid and scared about it. *Think* your freedom is being taken away somehow. *Think* that Ubuntu is turning into Microsoft and Apple. Do whatever you want.

If you leave Ubuntu, hopefully you can find something you like better (another distro perhaps).

---

### Post by James85 on 2007-10-02
I have recently changed from Microsoft XP to Ubuntu, and I like to install .deb files from websites. Does this mean that Ubuntu will stop me choosing my programs. If so, I thought that Linux was about freedom of choice as well as being free ($). 

My friend told me that when Linux distros get taken over by corporations, that they start to become like Microsoft and start trying to control users. This is why he uses Debian, as it is still a community thing.

Is this the case with Ubuntu? Because although i'm new to the Linux scene, I get the Linux philosophy of freedom preached at me on every forum I join. It was the freedom for me to choose my own programs that made me change, as well as the price ;), and stability.

I like Ubuntu as it is easy to install and use, but I wouldn't like to have a Linux that controls what I can install.

---

### Post by 23meg on 2007-10-02
> **wolfger said:**
> That sounds very reasonable to me, a power user... but how does that sound to inexperienced users, which by definition includes everybody who is new to Ubuntu Linux? I can see the forums filling up already with cries of "Ubuntu sucks because it won't let me do X", followed by somebody explaining how to do X, and at that point you've added zero security, and given some noob a bad first impression of the OS, while providing the rest of us a minor inconvenience. 

Such a poor implementation of the idea at hand will never fly in Ubuntu. The Technical Board isn't that naive, and the community isn't that forgiving.

---

### Post by tehet on 2007-10-02
This thread is silly.


> **James85 said:**
> I like to install .deb files from websites.
That is generally a bad idea as these are untrusted by definition and may break your system, well intended or not.
> Does this mean that Ubuntu will stop me choosing my programs.
No. You can still install whatever benevolentware/malware/whatever by hand using the dpkg command.

---

### Post by James85 on 2007-10-02
Ok, thanks. I would prefer to have the choice, even if I do make a mistake and install something bad.

So your saying that Ubuntu has a lot of benevolentware/malware/whatever .deb files on the internet, and the developers just want to protect the users from them.

That's ok I suppose, I just didn't realise that Linux has viruses and trojans like Windows. Or is it just Ubuntu? because nobody has said about this for other distros.

PS: This thread isn't silly for me, I came to Linux for security as well as freedom. I see you've only got 2 beans, are you a new user as well?

---

### Post by p_quarles on 2007-10-02
> **James85 said:**
> Ok, thanks. I would prefer to have the choice, even if I do make a mistake and install something bad.

So your saying that Ubuntu has a lot of benevolentware/malware/whatever .deb files on the internet, and the developers just want to protect the users from them.

That's ok I suppose, I just didn't realise that Linux has viruses and trojans like Windows. Or is it just Ubuntu? because nobody has said about this for other distros.

PS: This thread isn't silly for me, I came to Linux for security as well as freedom. I see you've only got 2 beans, are you a new user as well?
Pretty much everything has already been said in this thread, so I'll just recommend that you go back and read through all of it.

This all stems from a developer discussion that was looking at what *may* be necessary in the future if and when Ubuntu gains a sizable share of the desktop market. There are no known viruses in the wild for Linux right now, and there are relatively few threats if you practice common sense safe surfing. 

The discussion, moreover, was about adding *new *features that would make it even easier than it currently is to install software, and how to implement this without greatly increasing the risk for users who don't spend a lot of time reading security bulletins.

That's my summary, but don't take my word for: read it yourself.

---

### Post by James85 on 2007-10-02
Ok, thanks. I did read it by the way. Glad to know we're safe ;)
So at the moment I should just get stuff from the Ubuntu repositories then? 

I was going to get a program called Automatrix for some stuff, but my cousin said it would break my system, and he hasn't got the time to keep fixing it lol!, so I left it.

Guess i've got some more reading to do. Plenty here on this forum though.

---

