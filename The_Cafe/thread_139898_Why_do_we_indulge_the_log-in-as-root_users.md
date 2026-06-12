---
title: "Why do we indulge the log-in-as-root users?"
date: 2006-03-05
forum: The Cafe
---

### Post by aysiu on 2006-03-05
I've seen it happen too many times on these boards. Why?

If someone says, "I want to run such-and-such a Windows program. Will that work in Wine?" the usual responses is "Have you tried looking for an equivalent native Linux program?"

However, when someone asks, "How do I log in as root?" I usually see three or four responses that actually tell someone how to log in as root before anyone (usually me) will actually say that you use *sudo*, *gksudo*, or *kdesu* instead.

I understand that if someone knows everything about *sudo* and wants to use root anyway, they're entitled to know how. But most of these people have no idea the advantages of sudo--they just want to stick with what they're comfortable with--just as the ex-Windows user who wants to run everything in Wine instead of looking for Windows alternatives, a lot of refugees from other Linux distros are so ingrained with the whole log-in-as-root phenomenon, that they won't even consider the sudo alternative.

Do me a favor, please? If you're going to straight away tell someone how to log in as root, at least tell them Synaptic Package Manager and just about every other program that asks for the "root" password won't be asking for the actual root password but still the sudo one?

Now you can all jump all over me.

---

### Post by navilon on 2006-03-05
I agree, I dont really see to many reasons why someone would need to login as root anyway if they have sudo (unless they were just lazy and didnt want to type 4 extra characters)

---

### Post by Bandit on 2006-03-05
I tell them to use sudo also unless there is some very technical reason that they must run as root so the software will compile and install correctly.

---

### Post by bvc on 2006-03-05
[QUOTE=aysiu]I've seen it happen too many times on these boards. Why?[/QUOTE]because it's their box to destroy if they want to and linux is about choice, or did ya forget that important part? I don't have a problem with someone making sure that the one asking how to login as root, knows of the possible consequences, and that they know of the alternatives. What bothers me are those that don't answer the question of 'how to login as root' and just say "don't run as root". Very childish.

---

### Post by aysiu on 2006-03-05
[QUOTE=bvc]because it's their box to destroy if they want to and linux is about choice, or did ya forget that important part? I don't have a problem with someone making sure that the one asking how to login as root, knows of the possible consequences, and that they know of the alternatives. What bothers me are those that don't answer the question of 'how to login as root' and just say "don't run as root". Very childish.[/QUOTE] I'm in total agreement with you *if they know the alternatives*. My whole point is that without even explaining what sudo is and that it is an alternative to the traditional root model, people will indulge right away requests of "How can I log in as root?"

By all means, if someone understands the sudo model and still wants to log in as root, the information should not be denied the user. Most of the time, though, I see no understanding of that.

---

### Post by Qrk on 2006-03-05
[QUOTE=bvc]because it's their box to destroy if they want to and linux is about choice, or did ya forget that important part? I don't have a problem with someone making sure that the one asking how to login as root, knows of the possible consequences, and that they know of the alternatives. What bothers me are those that don't answer the question of 'how to login as root' and just say "don't run as root". Very childish.[/QUOTE]

But if they have to ask how to log in as root... should they really log in as root? I have to agree with aysiu here.

---

### Post by aysiu on 2006-03-05
Whenever possible, users should be directed to this page:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It explains the [advantages](https://wiki.ubuntu.com/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac) and [disadvantages ](https://wiki.ubuntu.com/RootSudo#head-a1a6136e349bca8bd739ef01ebe7a02c65007bd6) of both the root and sudo models.
It also explains [how to log in as root and how to make programs prompt you for your root password instead of your sudo password, should you wish that to happen instead of Ubuntu's defaults.](https://wiki.ubuntu.com/RootSudo#head-8352bb412ccfc81b89a48144986e8690c66e338c)

---

### Post by bvc on 2006-03-05
[QUOTE=Qrk]But if they have to ask how to log in as root... should they really log in as root?[/QUOTE]It's their computer isn't it? I agree it's a silly question that is easily answered with google, but so is 90% of questions but we answer those. If some has to ask how to install a theme, should they be allowed to install themes? That's silly...and yes, it's the same thing, in principle. Ask>receive>it's theirs to burn, not yours. Oh I know someone paranoid about security will say "but they could run apps that could be dangerous on the internet" but that's not near as dangerous as where most browse everyday ;) 

I'll admit I don't do any more than say how, but that's because everything but how has already been stated.

---

### Post by aysiu on 2006-03-05
Okay.

Can I mention what's an even bigger pet peeve, then? The half-answers.

People will say you can enable the root account this way, but then the user will still be prompted for her user password for Synaptic and other programs. If people are going to indulge the traditional root model, they should go the full mile.

And, again, the Wiki page explains everything, including how to enable root and fully use it.

---

### Post by jerome bettis on 2006-03-05
i use sudo without a password ... oh noes

i'm not typing that every 2 seconds .  nothing has happened and nothing will ever happen .. ever

in fact i'm gonna log in as root tommorow for fun, does that bother you?

---

### Post by aysiu on 2006-03-05
[QUOTE=jerome bettis]i use sudo without a password ... oh noes

i'm not typing that every 2 seconds .  nothing has happened and nothing will ever happen .. ever

in fact i'm gonna log in as root tommorow for fun, does that bother you?[/QUOTE] No. If you read my original post, you would understand that it doesn't bother me.

---

### Post by Jucato on 2006-03-05
EDIT: Removed paragraph.

As community members, don't we have a moral responsibility to each other? Isn't this community one of the things that make Ubuntu great? But if start with having that "It's your box to destroy" attitude and just give information here and there indiscriminately, what will happen to this community? I don't mind telling people how to do things the unconventional way as long as they know what the conventional (and presumably safer) way is first.

[QUOTE=jerome bettis]i use sudo without a password ... oh noes

i'm not typing that every 2 seconds .  nothing has happened and nothing will ever happen .. ever

in fact i'm gonna log in as root tommorow for fun, does that bother you?[/QUOTE]

Specifically this part:
[QUOTE=aysiu]I understand that if someone knows everything about sudo and wants to use root anyway, they're entitled to know how.[/QUOTE]

The fact that you know how to turn off the password for sudo means you know about sudo.

---

### Post by Jucato on 2006-03-05
EDIT: sorry for the double post. added it to my post above.

---

### Post by aysiu on 2006-03-05
Yes and no.

A computer is not a human life.

However, you do have a point--we should be helping people protect their computers. Nevertheless, if people *understand* the alternatives and what is safe and not safe, they are entitled to do whatever they want with their *own computers*.

My beef is just the automatic indulgence without even trying to educate people about the alternatives.

For me, the benefits of *sudo* aren't really security benefits (as there are both pros and cons to root and sudo models)--they're convenience benefits. It's easier for me to use ```
kdesu konqueror
``` than to log in as root. If people knew that, a lot of them wouldn't feel the need to log in as root. I'm just trying to promote alternatives that may, in fact, be easier.

It's like users who insist on using Nero in Linux. Nero in Linux may be fine, but have you tried K3B?

---

### Post by Kvark on 2006-03-05
I am auto logged in without a password when the computer boots. It's 100% safe cause I'm the only one in the family that knows how to do anything on a computer and maleware would run as my account anyway. But sudo still requires the password. The one and a half secounds it takes to type it in is a great opportunity to think twice before messing up and it prevents malicious programs from sudoing without asking me for the password. Sudo is the last thing that should be skipped.

I agree with aysiu. Tell them why they shouldn't before telling them how to.

---

### Post by kabus on 2006-03-05
> using bvc's logic, if a child asks how to use a gun, we should tell them, right? It's his/her life to destroy, anyway. I know it's a bit extreme, but that's how it really sounds.

People here aren't children and there's nothing inherently wrong with having the root account enabled.
If someone asks how to do that I'd just assume that he/she is aware of the pros and cons. If that's not the case, that's their problem.

(Just for the record I prefer sudo myself.)

---

### Post by GreyFox503 on 2006-03-05
Why do people answer by telling how to enable the root account?  Some may think that if they're asking about the root account, they already know what that is.

If a new user says "I don't have permission" or "it asked for a password" then we usually respond with sudo advice.

But generally, yes, sudo should be suggested first.  Unless the poster states or implies that they are already aware of sudo, that should be the first response.

---

### Post by Jucato on 2006-03-05
(NOTE: Edited) Not literally of course. (EDITED to prevent misinterpretation) But **most of** those asking about root passwords and stuff are still  new to ubuntu and/or linux.

We have to take everything into the context of the question. If we think that user knows about sudo already and wants, despite all the warnings, to enable the root account, then by all means tell them. Only when they don't even know that root is disabled by default in Ubuntu do we refer them to the RootSudo wiki.

---

### Post by darkmatter on 2006-03-05
Interesting discussion...

 Not meant to derail the tread... 

Though I *usually* run from my user account... it is not *much* safer than running as root, and the usuall arguements equating it to letting a child play with a gun is a common misconception (no offence)

Is the unix security model adopted by GNU/Linux *generally* safer than the non-unix model??? Yes...

Is it fool proof?? No... Like all current security models... it does have its flaws... it may be slightly more difficult to crack... but it can still be cracked. You can be rooted whether you run as root or not. (notice the use of 'crack' and not 'hack'... it irks me the way the two have become synonymous.... that many no longer know the difference between a cracker and a hacker)

My point being that... yes... though it is fine to promote the use of sudo in general...  we should not promote the use of such as the 'you are safe as long as you don't run as root' thing... because its a steaming pile of poo ;)

It is better to present it as it truely is: that the unix security model is better than that of other os's... and that itis true that not running as root offers enhanced security than running as root.... but don't feed them the false sense of security that it is pure rapture... the never-get-cracked Nirvana. 

End result: Give them the information needed to make an informed decision... and then let them do as they want (root or sudo/su)... instead of preaching the gods-sent gift of sudo and how it makes them impervious to harm.

Just my two cents. :)

EDIT: [quote=Fenyx]those asking about root passwords and stuff are still "children" when it comes to linux[/quote]

Why??? could you please explain the reasoning behing that statement???How does wanting to run as root make one a 'child'??? I've been using computers since the days of the monochrome tin can, and Windows is a foreign entity to me when I first used it... and in many ways still is (grew up a unix child)??? Does the fact that I actually run as root for days on end when it is convenient for me to do so make me one of these children??? Not likely... Granted... though there was a period of time when I did not have access to my *own* pc... I still have approx. 20 years of computing experience under my belt... most with the unices...

So by your own reasoning: When I came to Uby for the first time... I questioned as to why root was disabled... and therefore am a 'child' to the Linux world...

haha... funny.

---

### Post by Kernel Sanders on 2006-03-05
[QUOTE=aysiu]I've seen it happen too many times on these boards. Why?

If someone says, "I want to run such-and-such a Windows program. Will that work in Wine?" the usual responses is "Have you tried looking for an equivalent native Linux program?"

However, when someone asks, "How do I log in as root?" I usually see three or four responses that actually tell someone how to log in as root before anyone (usually me) will actually say that you use *sudo*, *gksudo*, or *kdesu* instead.

I understand that if someone knows everything about *sudo* and wants to use root anyway, they're entitled to know how. But most of these people have no idea the advantages of sudo--they just want to stick with what they're comfortable with--just as the ex-Windows user who wants to run everything in Wine instead of looking for Windows alternatives, a lot of refugees from other Linux distros are so ingrained with the whole log-in-as-root phenomenon, that they won't even consider the sudo alternative.

Do me a favor, please? If you're going to straight away tell someone how to log in as root, at least tell them Synaptic Package Manager and just about every other program that asks for the "root" password won't be asking for the actual root password but still the sudo one?

Now you can all jump all over me.[/QUOTE]


I dont mean to "jump all over you" but why do you care?

If someone wants to know how to do something, and you know, why not just be helpful and just tell them?

Preaching while trying to be informative really isnt that helpful.

John

---

### Post by Xian on 2006-03-05
[QUOTE=aysiu]My beef is just the automatic indulgence without even trying to educate people about the alternatives.[/QUOTE]

You are being right minded but I'm afraid you'll need a lot of aspirin.
If you know what I mean....

---

### Post by Xian on 2006-03-05
[QUOTE=*John*]I dont mean to "jump all over you" but why do you care?[/quote]

There is nothing wrong with caring about if members are using their systems effectively, securely, and with the facts that will let them make good decisions. Encouraging others to do the same is a responsible act that should be beneficial to the community.

[QUOTE=*John*]If someone wants to know how to do something, and you know, why not just be helpful and just tell them?[/quote]

If in the process of "helping" them you are also doing more harm than good, then what is the point of helping in the first place?

[QUOTE=*John*]Preaching while trying to be informative really isnt that helpful.[/QUOTE]

Some people need a little preaching. :)

---

### Post by Jucato on 2006-03-05
[QUOTE=darkmatter]Why??? could you please explain the reasoning behing that statement???How does wanting to run as root make one a 'child'??? [/QUOTE]

"child" = someone new to ubuntu or to linux, not someone immature (if that's what you are getting at.)
I'll edit my posts to avoid misunderstanding.

EDIT (just to add):
No one is saying that we force people to use or not to use sudo/root/whatever. Part of helping people make an "informed decision" is to present to them the alternatives. Consequently, one of those alternatives is something that Ubuntu has decided to make a standard in it's system (sudo rather than su). No one said anything about preaching. No one said anything about sudo being absolutely better than su. It just so happened that Ubuntu wanted to make sudo the norm.

It's just like telling people "Oh you want to do this as root? By the way, there's another way to do it using sudo. If you still want to do it as root, do this..."

---

### Post by fuscia on 2006-03-05
[QUOTE=Fenyx]As community members, don't we have a moral responsibility to each other?[/QUOTE]

that extends  only to mentioning something you feel the person you're helping is unaware of. as this is a support forum, the moral responsibility (if that's not too much of a term to use here) is to answer the questions of those seeking information. it would be immoral to impede another's freedom, no matter how well intended.

if someone is used to logging in as root, from using another distro, they may not want to learn about the beauties of 'sudo' while trying to solve another problem, at the same time. analogously, as a newb and non-techie, i am often provided with a solution to a problem and then am given additional info for scripting a permanent solution to the problem. solving the problem and making the solution permanent are two different processes, in my mind, and it's often too much for me to handle both. someone used to signing in as root, under another distro, may be too aggravated to both solve his/her/its problem *and* learn about 'sudo' at the same time.

freedom often means enabling others to do something stupid. (you're also free to tell them it's stupid.)

---

### Post by Stormy Eyes on 2006-03-05
[quote=aysiu]Re: Why do we indulge the log-in-as-root users?[/quote]

Because assault and battery is a felony?

---

### Post by nik on 2006-03-05
[QUOTE=fuscia]
freedom often means enabling others to do something stupid. (you're also free to tell them it's stupid.)[/QUOTE]
Yep.

There are different questions. If someone says "How can I enable the root account in Ubuntu?" I think it's perfectly fine just to tell them. But if someone asks "Help!!! I can't login as root!!!" then by all means tell them, but it might be a good idea to also tell them it's probably not nessesary...

There are other issues too. Many beginners have gotten a lot of problems because of well-meaning but bad advise (like changing file permissions). I wouldn't say anyone has a moral obligation to correct this, but it is a nice thing to do. after all, we all want people to be happy about their ubuntu experience.

As an aside, I almost asked the root account question when I first came here, but luckily I found a post where someone explained about sudo...

---

### Post by LordHunter317 on 2006-03-05
[QUOTE=aysiu]People will say you can enable the root account this way, but then the user will still be prompted for her user password for Synaptic and other programs. If people are going to indulge the traditional root model, they should go the full mile.[/quote]Why?  I retain root shell on my boxes because I run a limited sudo policy and it is far from perfect.

And people may only want root enabled for specific things.  Suggesting it's all or nothing is not only ignorant and arrogant, it's ludicrious.

[qoute=Fenyx]But figuratively speaking, most of those asking about root passwords and stuff are still "children" (new to ubuntu and/or linux) when it comes to linux.[/quote]It's still insulting to assume such things.

[quote=darkmatter]Though I *usually* run from my user account... it is not *much* safer than running as root, and the usuall arguements equating it to letting a child play with a gun is a common misconception (no offence)[/quote]What?  Root is dangerous. 

>  (notice the use of 'crack' and not 'hack'... it irks me the way the two have become synonymous.... that many no longer know the difference between a cracker and a hacker)It apparent you have no clue what difference is, though.

> It is better to present it as it truely is: that the unix security model is better than that of other os's...Seeing as it's the same model as all other general-purpose operating system you're just plain wrong.

---

### Post by darkmatter on 2006-03-05
Why don't you try responding to a level post with a level a replythat isn't an attempt at being condesending??? Read the guidlines.

---

### Post by LordHunter317 on 2006-03-05
[QUOTE=darkmatter]Why don't you try responding to a level post[/quote]Because there was nothing "level" about your post by any standard.  It was full of mistruths and garbage, frankly.  It's not reasoned discourse by any sense of the term, because as I said, you don't know what you're talking about.

Your delination between 'crack' and 'hack' cannot be determined from the attack.  Who launched the attack could have been a 'cracker' running someone else's canned tool, an invidiual person manually compromising a machine, or an actual security researcher, a 'hacker' in multiple literal senses, compromising a machine.

If you want a neutral word, you use exploit, or compromise. In fact, you use those anyway, because that's what happened.  Your machine was exploited, resulting in a compromise of it's security.  

As for the security model, all general-purpose operating systems use some variant of discresionary access control (DAC).  That means that a sufficently privileged user can bypass all security checks.  This is the model used by all BSDs, and OS X.  Windows NT, Linux, Irix, Solaris, OpenVMS and quite possibly a few others I'm forgetting / less familar with all use a form of DAC with capabilities.  In this case, named privileges are given to each action a user may wish to perform, beyond the filesystem.  Exactly what each privilge can do, how you acquire them and remove them varies, but the rule still applies: a user with all the privileges effectively bypasses all the checks.

And frankly, these things are so fundamental there's no reason to not be short about it.  It's tantamount to a professor walking into my EE class and not knowing Ohm's Law.

---

### Post by darkmatter on 2006-03-05
Yes DAC and all... but there are distinct differences in implementation... and root is only dangerous if you don't know what you are doing...

BTW... my post was quite general and not directed at any individuals I know of... only the general scare tactics used in how security is explained to a great deal of users (we've all seen it done... and it is sad that most users do noit get a decent explaination)

as for my post... observing... I just tend to be blunt in my choice of wording... and I don't mince meat with a 300 page essay post when I'm attempting to just get an opinion/point accross....

Now... I've been using computers for close to 20 years (mostly unices), and not just as a user... so maybe I prefer the 'pure' reference of hacker as it used to be... or maybe I just don't like being associated with the trash of the digital world *shug*

I'll ignore some of the remarks of your reply.... because I'm not going to respond to anyone who is not me or in my head when I post at *that* level.... All I'll say is I knoow a hell of a lot more than you think I know... but like I said... I'm not wasting my time and energy righting a 300 page essay on my views with all the necessary technical discussion... I've more important things to do with my life... like enjoy whats left of it

Regards

---

### Post by LordHunter317 on 2006-03-05
[QUOTE=darkmatter]Yes DAC and all... but there are distinct differences in implementation...[/quote]That, from a model perspective, matters little.  All of those OSes I mentioned are evaluated to the CAPP model in common criteria evaluations.  

They're that close.  The model is the same.  The implementation differences make some things eaiser, some things harder, but rarely make things out-and-out impossible.

The only obvious, common, and worthwhile exception I can note is the differences between NTFS and POSIX ACLs.

> and root is only dangerous if you don't know what you are doing...It's still dangerous even if you know what you're doing.  Running as root all the time is dangerous, period, for day-to-day use.  Unless your only work on a machine consists solely of administering it, the above holds.  Even with that constraint, it still may hold.

> BTW... my post was quite general and not directed at any individuals I know of...Which doesn't excuse it's gross incorrectness.

> only the general scare tactics used in how security is explained to a great deal of usersNone of which are being used here, nor were used here.

And if they had been, I would have pointed it out.  Paranoia helps no one.

> and I don't mince meat with a 300 page essay post when I'm attempting to just get an opinion/point accross....And then bash me for doing the same...

> Now... I've been using computers for close to 20 years (mostly unices), and not just as a user... so maybe I prefer the 'pure' reference of hacker as it used to be...That's not the issue.  Your issue is where you drew the line and how you drew it: both were simply incorrect.  Cracker has a very well-defined meaning, hacker does not.  But you drew the line on the wrong side: not all attacks are executed by crackers.

---

### Post by DigitalDuality on 2006-03-05
When i first started out with Linux, i HATED, hated hated hated sudo, su and any variation of.

I realized then (and do now) that it's for security purposes, but frankly i didn't care.  When i want to so much as put a single file in my wallpaper default folder, i can't utilize the gui without typing something in the command line.  It's annoying.  I still find it annoying.

That being said, i used my root account as my default account for about 2 months so i could explore linux and get used to it.  It's bad enough to you have to re-learn a ton of very basic things when making the switch, root access just makes it more frustrating and difficult.

Now, now i use a user account and use sudo.  But i just found making the switch and wanting to learn how to do a ton of things became a huge pain in the butt b/c of this.  I wanted full access and i wanted to explore.  I've learned a great bit in a short time and can get around just fine with a user account.  I've grown more accustomed to the command line, and it's no where near the annoyance now as it was then.  I dunno, i just think it's a pain to learn how to use linux as merely an end user, and you have that little restriction in your damned way all the time. For some people this may instill horrible security habits, but i dunno.. it didn't for me.  

I think people should be free to know, but also warned of the security risk it creates.  And let them decide.  Especially if its a home computer.

---

### Post by xequence on 2006-03-05
Running as root is just so much easier. I had to log out, log in as root, change something in the system files, then log back in as my normal self many times. And I tried to do sudo there but it didnt work... I dont remember why, maybe I got an error typing "sudo nautilus" or something.

If I am fine running as admin in windows I could run as root in linux ;)

(But I didnt run as root, everyone just told me not to so I didnt :O)

---

### Post by Jucato on 2006-03-05
I think there are really somethings that you can't do with sudo, that you would have to do as root. An example would be the HOWTO for the latest NVIDIA drivers.

OT: xequence, i thought that when starting a graphical app as root, you're supposed to use gksudo/kdesu? at least that's what the wiki says.

---

### Post by LordHunter317 on 2006-03-05
[QUOTE=DigitalDuality]f.When i want to so much as put a single file in my wallpaper default folder, i can't utilize the gui without typing something in the command line.  It's annoying.  I still find it annoying.[/quote]But why would you ever in your right mind want to put files there?

It's read-only for a reason.

---

### Post by aysiu on 2006-03-05
[QUOTE=Fenyx]I think there are really somethings that you can't do with sudo, that you would have to do as root. An example would be the HOWTO for the latest NVIDIA drivers.[/QUOTE] You're absolutely right. I don't know about NVIDIA drivers (I've never had to be root to install those), but, for example, if you want to follow [the Apt-Move Howto](https://wiki.ubuntu.com/AptMoveHowto), you **must** log in as root. *sudo* won't give you sufficient permission to do some of the later steps.

For the vast majority of tasks users want to accomplish, *sudo*, *kdesu konqueror*, and *gksudo nautilus* are not only sufficient but faster and easier.

---

### Post by aysiu on 2006-03-05
[QUOTE=DigitalDuality]When i want to so much as put a single file in my wallpaper default folder, i can't utilize the gui without typing something in the command line.  It's annoying.  I still find it annoying.[/QUOTE] So create a launcher of keyboard shortcut for the command ```
gksudo nautilus
``` Problem solved.

---

### Post by prizrak on 2006-03-05
xequence, you could just setup a shortcut that would run terminal in root mode anything started from there will run as root. As opposed to logging in and out.

DigitalDuality, I have not found a single reason to run as root all the time to explore and play around with Linux.

---

### Post by PatrickMay16 on 2006-03-05
I think that if someone wants to know something, they should be allowed to know. Of course, you should also let them know that it's safer to use sudo and such, but let them know how to do what they're asking to do, too.

---

### Post by bvc on 2006-03-05
[QUOTE=LordHunter317]
It's still dangerous even if you know what you're doing.  Running as root all the time is dangerous, period, for day-to-day use.  Unless your only work on a machine consists solely of administering it, the above holds.  Even with that constraint, it still may hold.[/QUOTE]That is your opinion and many others, but in 6 years I've debated the issue, that's all it's ever been...personal opinion. Never any facts as to why. Reasons have been given but they're always tied to the lies that benefit the security industry, which is big business and big money. If people knew the truth a lot of people would be out of a job. People that do not know any better don't help the situation. Hey, linux benefits from it as well. Oh security! security! Yet, I ran a single installation of win98se for 3 years w/o antivirus or a firewall and not one virus and no spam. It's all it how you secure your sys, what you use it for, where you go and if you're mouse click happy on everything that flashes. Security is highly overrated for the wise. For the rest, they have to play the game.

---

### Post by jerome bettis on 2006-03-05
[quote=Kvark]it prevents malicious programs from sudoing without asking me for the password. Sudo is the last thing that should be skipped.[/quote]

you're right, but practically speaking i am not aware of any malicious programs that exist, let alone could get on my computer and even execute.

i want to see a link about someone using root that had a program come in and F everything up.  i don't think you'll find any that aren't from 1988.  maybe i'm way off, but i really feel no threat whatsoever.  keep ports closed and use strong passwords and nothing can possibly happen.

when i run a server i keep it secured, but when it's not running i really don't even think about security.  i've had a few script kiddies from korea try to guess my name and password but that's all that ever happens anywhere.

nix by design is fundamentally way more secure than windows, i see no need to worry really.

---

### Post by LordHunter317 on 2006-03-05
[QUOTE=bvc]That is your opinion and many others, but in 6 years I've debated the issue, that's all it's ever been...personal opinion. Never any facts as to why.[/quote]Ok, run unpatched Firefox in Breezy as root.  If you hit one of the known exploits out there, they just didn't get your user account.  They got root.  **Your whole box.  *Everything*.**

This is why root is dangerous: compromise of the root account is compromise of the entire box.  You lose everything.  

Given proper auditing and tracking of the breakin, a breakin of an unprivileged account is substantially better, in terms of system security.  It may still be bad for the user, if personal information is stolen, but it does limit what they can do the box.

Most importantly, it greately limits their ability to cover their tracks and do things like install rootkits.

> Reasons have been given but they're always tied to the lies that benefit the security industry,No, they're not.  They're simple fact.  It's a logical consequence of the model.

> If people knew the truth a lot of people would be out of a job.And that truth is?  I see you in a tinfoil hat on a soapbox saying, "He lies," but not furthering:[list][*]The actual **factual** errors in my argument[*]How I'm tied to the security industry in any way[*]An awarness of even the basic security concepts we're discussing.[/list]

IOW, I don't think you have the foggiest idea what you're talking about.

> Yet, I ran a single installation of win98se for 3 years w/o antivirus or a firewall and not one virus and no spam.Non-sequitur, inductive fallacy.

Good for you.  Windows 98 isn't the least bit relevant here.  It never was, it never will be.  What you've managed to do isn't relevant either.

>  Security is highly overrated for the wise.No, it really isn't.  That's like saying, "Brushing your teeth is overrated for those who've never had cavities." 

An ounce of preventation and all that.  Yes, being a savvy computer user will lower your risk.  But when an exploit is discovered in FF, you can't do anything about it until the patch is released, beyond stop using FF.  And while you can do your best to avoid certain types of attacks, you're always going to be attacked in certain situations (e.g., email worms).

[quote=jerome bettis]
you're right, but practically speaking i am not aware of any malicious programs that exist, let alone could get on my computer and even execute.[/quote]Firefox is a security seive.  Local execution vulnerabilites exist for Firefox for UNIX and have known in the wild exploits.

So's Thunderbird, likely (I'm honsetly shocked that it hasn't had more holes found in it, or published.  Probably because it's not a darling child yet).

Off hand, software shipped in Ubuntu with known poor security track records:[list][*]PHPBB[*]PHP-Nuke[*]Firefox[*]ISC DHCP (mainly server)[*]Apache[/list]I could likely think of more if I went through secunia.org, but you get the point.

The very fact there's a security group ought to cue you off to the fact that there is indeed, insecure code shipped by Ubuntu (like all distros) and that indeed, malicious code exists to exploit that software.

People wouldn't go through the effort of paching this stuff if it weren't a real concern.

> i want to see a link about someone using root that had a program come in and F everything up.There are several in the security forum **of this very site.**  Why?  Because several system daemons run as root, and if they're compromised, it's ballgame.  Your rank ignorance doesn't change reality.

> maybe i'm way off, but i really feel no threat whatsoever. You're not only way off, you're not even in the right universe.

> keep ports closed and use strong passwords and nothing can possibly happen.That's a good start, if we're talking about one machine.  But security is rarely about one machine, outside of a home user's desktop.  And when we're talking about lots of machines, it gets far more complicated.

> i've had a few script kiddies from korea try to guess my name and password but that's all that ever happens anywhere.I guess Apache slammer didn't happen then?

> 
nix by design is fundamentally way more secure than windows, i see no need to worry really.**No, it isn't.  How many times to I have to continually repeat this?**

---

### Post by drizek on 2006-03-05
Wish Granted!

(Todays Dapper)

---

### Post by jerome bettis on 2006-03-05
[quote=LordHunter317]You're not only way off, you're not even in the right universe.[/quote] 
right.

whatever, at least i have friends and an ego that is under control. ;)

---

### Post by LordHunter317 on 2006-03-05
:rolleyes:  Whatever.  Seriously though, 30 *seconds* at secunia.org would show you just how wrong you were.  Again, this is on the level of an EE not knowing what Ohm's Law is.  This is fundamental stuff.

It'd be one thing to say, "I have no clue about this stuff, are these threats real."  It's another to say, "but practically speaking i am not aware of any malicious programs that exist, let alone could get on my computer and even execute." seeing as these sorts of things have made national news, been covered on CNN, we have a security team that releases this stuff, etc.

---

### Post by jerome bettis on 2006-03-05
like i've told you before, i have a lot of respect for your knowledge.  but i have 0 respect for the arrogant, omniscient way in which you try present it on here.

seriously read what you wrote, i find it rediculous that you would spend that much time typing something so insignificant, quoting every sentence like that.  you really come off like some home-schooled kid who has no social skills.  

you should turn the computer off and go try to get a girlfriend.

---

### Post by KiwiNZ on 2006-03-05
OK enough already

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=jerome bettis]like i've told you before, i have a lot of respect for your knowledge.  but i have 0 respect for the arrogant, omniscient way in which you try present it on here.[/quote]Well, like I said, **this is fundamental**.

> seriously read what you wrote, i find it rediculous that you would spend that much time typing something so insignificant,I'm sorry you consider correcting mistruths insignificant.  If that's the case, why do you even reply?  Your reasoning makes no sense.

> you should turn the computer off and go try to get a girlfriend.:rolleyes: So, it's OK to call me an arrogant *** and attack me? 

The hypocrisy here is absolutely incredible and out-and-out overwhelming, troll.  You have the *gall* to accuse me of having no social skills and then insult me?  Come off your white horse of superiority, it already fell in the mud.

---

### Post by pbransford on 2006-03-06
Meh, I don't really see a difference between using sudo or using root. You can hose your system just as easily either way, and differing from the expected (root) can cause issues with buggy software.

If a cracker can grab the root password somehow they can just as easily grab yours and use sudo themselves. So from a security standpoint it makes no difference. Doesn't matter that the root account exists or not, if you use a REAL password it won't matter if they have a username to begin with.

(BTW, real password being 8 chars alpha, numeric, symbols, and mixed case. Breaking that password on a normal computer would take a millenia)

---

### Post by bvc on 2006-03-06
> **LordHunter317]Ok, run unpatched Firefox in Breezy as root.  If you hit one of the known exploits out there, they just didn't get your user account.  They got root.  **Your whole box.  *Everything*.**

This is why root is dangerous: compromise of the root account is compromise of the entire box.  You lose everything.  

Given proper auditing and tracking of the breakin, a breakin of an unprivileged account is substantially better, in terms of system security.  It may still be bad for the user, if personal information is stolen, but it does limit what they can do the box.

Most importantly, it greately limits their ability to cover their tracks and do things like install rootkits.

No, they're not.  They're simple fact.  It's a logical consequence of the model.

And that truth is?  I see you in a tinfoil hat on a soapbox saying, "He lies," but not furthering:[list][*]The actual **factual** errors in my argument[*]How I'm tied to the security industry in any way[*]An awarness of even the basic security concepts we're discussing.[/list]

IOW, I don't think you have the foggiest idea what you're talking about.

Non-sequitur, inductive fallacy.

Good for you.  Windows 98 isn't the least bit relevant here.  It never was, it never will be.  What you've managed to do isn't relevant either.

No, it really isn't.  That's like saying, "Brushing your teeth is overrated for those who've never had cavities." 

An ounce of preventation and all that.  Yes, being a savvy computer user will lower your risk.  But when an exploit is discovered in FF, you can't do anything about it until the patch is released, beyond stop using FF.  And while you can do your best to avoid certain types of attacks, you're always going to be attacked in certain situations (e.g., email worms).[/QUOTE]Please keep in mind I am only referring to a single home desktop. It would be absurd to take my view in any other situation. I've run as root for all 6 years I've used linux. Come and get me :-k ...I have backups  said:**
> i want to see a link about someone using root that had a program come in and F everything up.  i don't think you'll find any that aren't from 1988.
...there's a lot of people sitting around waiting on a linux/root/vulnerable app running combo isn't there? :rolleyes:

Most that wanna run as root don't play around and aren't afraid of risk, or breaking things. That's our business. As a result, we do what other fail at. Running bug ridden distros stable, building linux from scratch, hacking patches and running 8 distros at once to debugging and improve them. We have fun with the challenges others cringe at. We don't expect anyone else to do it, nor do we encourage it, but we sure take offence to anyone telling us we don't have the right and despise freesoftware apps being made to not run as root so we have to edit the code to get them to work for us. Is this Linux? or Windows?

---

### Post by aysiu on 2006-03-06
[QUOTE=pbransford]
If a cracker can grab the root password somehow they can just as easily grab yours and use sudo themselves. So from a security standpoint it makes no difference. Doesn't matter that the root account exists or not, if you use a REAL password it won't matter if they have a username to begin with.[/QUOTE] Actually it would: > Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Would you rather guess a username and a password or just a password? Especially if you know the username root *has* root privileges. Any user doesn't necessarily have sudo privileges.

I like how to Wiki lays out both pros and cons.

> **The benefits of leaving root disabled by default include the following:**

    *

      The installer has to ask fewer questions
    *

      Users don't have to remember an extra password, which they are likely to forget
    *

      It avoids the "I can do anything" interactive login by default -you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing.
    *

      Sudo adds a log entry of the command(s) run (In /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing.
    *

      Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are.
    *

      Allows easy transfer for admin rights, in a short term or long term period, by adding and removing users from groups, while not compromising the root account.
    *

      sudo can be setup with a much more fine-grained security policy
[b]
Although for desktops the benefits of using sudo are great, there are possible issues which need to be noted:[/b]

    *

      Redirecting the output of commands run with sudo can catch new users out. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents.
    *

      In a lot of office environments the ONLY local user on a system is root. All other users are imported using NSS techniques such as nss-ldap. To setup a workstation, or fix it, in the case of a network failure where nss-ldap is broken, root is required. This tends to leave the system unusable unless cracked. An extra local user, or an enabled root password is needed here.

---

### Post by bvc on 2006-03-06
[QUOTE=pbransford]Meh, I don't really see a difference between using sudo or using root. You can hose your system just as easily either way, and differing from the expected (root) can cause issues with buggy software.

If a cracker can grab the root password somehow they can just as easily grab yours and use sudo themselves. So from a security standpoint it makes no difference. Doesn't matter that the root account exists or not, if you use a REAL password it won't matter if they have a username to begin with.

(BTW, real password being 8 chars alpha, numeric, symbols, and mixed case. Breaking that password on a normal computer would take a millenia)[/QUOTE]There is a difference. There are thngs you can't do with sudo that you can do as root. or so I've heard. I do agree with were you're going though. On non-sudo distros, everyone says....just su as root. Well, now you're root...so why bother? Then you get the complacent argument. Neither side can win. It's one of those neverending linux topics that always pop up and both sides are right. It's depends on the user what they wanna be.

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=pbransford](BTW, real password being 8 chars alpha, numeric, symbols, and mixed case. Breaking that password on a normal computer would take a millenia)[/QUOTE]No, length has nothing to do with it, really, beyond a minimal point.

On Windows, if I recover the SAM database, I can crack all passwords under 14 characters consisting of any common char (all letters, numbers, basic symbols in PC104) effectively instantly (order of minutes).  Rainbow table attacks solely have length as their weakness, and it's much higher than is practical for most people to remember.

Linux is protected via hashed passwords, which is an effective deterrent for now (and the near future).  The table for a hashed MD5 password is simply to large to be currently practical to generate.

As for brute force or dictionary attacks?  Making a password complex enough will make it pretty much impossible to break, regardless of length.  

That's not to say your suggestions are poor, but your conclusion isn't quite right.

Yes people should use complex passwords (numbers and symbols) and they should be of reasonable length.  But the idea that a password with a symbol, a number, and over 8 chars can't be trivally cracked isn't true anymore.

That being said, you still have to recover the hash in the first place, which isn't a trivial task, FWIW.

[quote=bvc]Come and get me  ...I have backups  ...so no worries. Be back up and running in an hour.[/quote]Backups won't protect you if I steal e.g., bank account information or a credit card number.

> am not saying the exploits aren't there. Just they don't concern me.Well, they should. This is just arrogance on your part.

> What % of linux users do you think run as root?Anyone running a server that listens public has a potential root compromise, as some part of that server almost certainly runs as root at somepoint.  The ones that don't are few and far between.  Off hand on my fileserver, I can think of PostgreSQL, and the Ventrillo server.  That's it.  Samba doesn't.  Apache doesn't.  VSFTPD doesn't.  SSHD doesn't.  

> Most that wanna run as root don't play around and aren't afraid of risk, or breaking things.No, it's almost universally been my experience they have no clue what the risk is.

> As a result, we do what other fail at. Running bug ridden distros stable, building linux from scratch, hacking patches and running 8 distros at once to debugging and improve them.Non-sequitur, slippery slope and just utter WTF.  How any of those follow is so utterly beyond me I don't even know what to say.  This is why stream-of-conciousness writing is bad, ok?


> We don't expect anyone else to do it, nor do we encourage it, but we sure take offence to anyone telling us we don't have the rightNo one said you did.

>  and despise freesoftware apps being made to not run as root so we have to edit the code to get them to work for us.I can't think of any that *refuse* to run as root.  Not a single one.

[quote=ayisu]Would you rather guess a username and a password or just a password?[/quote]Guessing a username with reasonably high accuracy (relatively) is easy.  Guessing a password isn't.  Guessing either is so hard anyway it doesn't matter.

Password space for an 8-character password, letters and numbers is 62^8.  That's assuming you know the space size (you don't) how long it is (you don't) and the username.  And that's a totally unsolvable problem.

Adding complexity doesn't necessarily increase your security at this point.  I could reduce the problem space even further and you'd still never get in, except as dumb luck.

---

### Post by Iandefor on 2006-03-06
[quote=LordHunter317]:rolleyes:  Whatever.  Seriously though, 30 *seconds* at secunia.org would show you just how wrong you were.  Again, this is on the level of an EE not knowing what Ohm's Law is.  This is fundamental stuff.

It'd be one thing to say, "I have no clue about this stuff, are these threats real."  It's another to say, "but practically speaking i am not aware of any malicious programs that exist, let alone could get on my computer and even execute." seeing as these sorts of things have made national news, been covered on CNN, we have a security team that releases this stuff, etc.[/quote] secunia.org is certainly an interesting site. Thank you for sharing it.

This is utterly off-topic, but I've heard you mention Firefox's insecurity before. What browser do you use, then, or do you just keep up with the security updates for Firefox?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=bvc]There is a difference. There are thngs you can't do with sudo that you can do as root.[/quote]That's not true in the least. 

>  I do agree with were you're going though. On non-sudo distros, everyone says....just su as root.I don't, and my only remaining Linux box in my posession ATM is running Debian, not Ubuntu.

Major corporations with multiple sysadmins per box don't either.  Sharing admistrator passwords is bad, and generally avoided.  sudo provides a solution to that.

> Well, now you're root...so why bother?Auditing, for starters.

> It's one of those neverending linux topics that always pop up and both sides are right.No.  While the answer isn't clear cut because the importance of some things is subjective (like auditing) the technical benefits of one solution over the other are crystal clear and quite objective.  It's how important those benefits are that's subjective.  To even remotely suggest this is a totally subjective thing borders on lunacy, or too much political correctness.

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=Iandefor]This is utterly off-topic, but I've heard you mention Firefox's insecurity before. What browser do you use, then, or do you just keep up with the security updates for Firefox?[/QUOTE]I use it, and often wonder if I should just give up on the Internet.  None of the current crop of major browsers (IE 6, FF, Opera) are written with security in mind.  IE7 looks to be better on that side of the road, but not substantially better (i.e., unlike IISv6 which was written with security as a primary goal, IE7 is not being given similar treatment).  

I just do my best to keep up and be savvy.  The fact I only really browse a small handful of very high-profile sites helps immensely, I suppose.  Not everyone has that luxury.

---

### Post by aysiu on 2006-03-06
[QUOTE=LordHunter317][quote=bvc]There is a difference. There are thngs you can't do with sudo that you can do as root.[/quote]That's not true in the least.[/quote] Actually, it is true. I tried doing this

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

using *sudo* instead of root and I couldn't do certain parts of it. It said I didn't have permission. When I did it as root (as the instructions ask you to do), I did have that permission.

If I'm remembering correctly, it was this set of commands that was tripping me up as *sudo*: ```
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/breezy/main/binary-i386/Packages.gz
apt-ftparchive packages pool/restricted/ \
  | gzip -9c > dists/breezy/restricted/binary-i386/Packages.gz
``` Any explanation why?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=aysiu]Actually, it is true.[/quote]No, it isn't.  One example doesn't prove the point.  In fact, as long as you can invoke a shell, you can do anything you'd do on a root shell with sudo (think about why).

Somethings would be awfully ugly to do that way, but it can be done.

> If I'm remembering correctly, it was this set of commands that was tripping me up as *sudo*: ```
apt-ftparchive packages pool/main/ \
  | gzip -9c > dists/breezy/main/binary-i386/Packages.gz
apt-ftparchive packages pool/restricted/ \
  | gzip -9c > dists/breezy/restricted/binary-i386/Packages.gz
``` Any explanation why?Yeah, you probably did this:```
sudo apt-ftparchive packages pool/main | gzip -9c > dists/breezy/main/binary-i386/Packages.gz
```Which doesn't run the gzip command as root.  Your two alternatives are:```
sudo apt-ftparchive packages pool/main | sudo gzip -9c > dists/breezy/main/binary-i386/Packages.gz"
```Or:```
sudo sh -c "apt-ftparchive packages pool/main | sudo gzip -9c > dists/breezy/main/binary-i386/Packages.gz"
```

---

### Post by aysiu on 2006-03-06
Thanks for the explanation. Maybe that's where I messed up--just doing *sudo* on the first command?

Just a random aside: I've really grown to like *sudo*. It was a big turnoff at first coming from Mepis where I was used to doing *su*. What I like most about it is actually giving instructions to people--I can just say "type *sudo apt-get update*." I don't have to say "make sure you're logged in as root or type *su* to log in as root and then type *apt-get update*."

---

### Post by LordHunter317 on 2006-03-06
Likely.  It's a common mistake to forget that the '|' is a shell operator, and runs a second command.  IOW, given:```
sudo a | b
```The shell executes:```
sudo a
``` and takes the output of that execution and pipes it to:```
b
```which is obviously running as yourself, for any arbitrary a and b.

It's pretty common, especially if you're unaware of how the shell parses a line (which isn't immediately obvious).  I'm aware of it and still make that mistake on occasion... :)

---

### Post by aysiu on 2006-03-06
Well, you learn something new every day... or at least *I* do. Thanks again for explaining.

---

### Post by bvc on 2006-03-06
[QUOTE=LordHunter317]
Backups won't protect you if I steal e.g., bank account information or a credit card number.

Well, they should. This is just arrogance on your part.

Anyone running a server that listens public has a potential root compromise, as some part of that server almost certainly runs as root at somepoint.  The ones that don't are few and far between.  Off hand on my fileserver, I can think of PostgreSQL, and the Ventrillo server.  That's it.  Samba doesn't.  Apache doesn't.  VSFTPD doesn't.  SSHD doesn't.  

No, it's almost universally been my experience they have no clue what the risk is.

I can't think of any that *refuse* to run as root.  Not a single one.[/QUOTE]Sorry, I don't purchase or bank on the internet ;) 

It's not arrogance, just a tiny risk, if any I am willing to take.

There ya go with that server stuff again. I don't do that anymore. Single home desktop, remember? Try to stay ontopic please. I shouldn't have to repeat myself. How is it that you can read all that security stuff, and remember it, but can't remember I said single home desktop? Makes me wonder how open minded you are on the topic at hand.

You're right...I'm clueless :mrgreen: 

gdesklets and gtkgnutella to start, though I don't use either. Just thought I'd check them out for grins.

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=bvc]There ya go with that server stuff again. I don't do that anymore. Single home desktop, remember? Try to stay ontopic please[/quote]I am ontopic.  You asked what % of Linux users aren't running somethign as root.  The answer is a very small number.

Limiting the discussion to single home desktops is an artifical, poor constraint.  

> How is it that you can read all that security stuff, and remember it, but can't remember I said single home desktop?You extended the discussion further.  More importantly, talking about single home desktops isn't interesting.   It's an artifically small case in today's world.

More importantly, even on a single home desktop, some of that software would be run anyway.  My laptop runs all sorts of server stuff so I can do development regardless of Internet connection.  That includes things such as Apache, Samba, etc.

So even if did artifically constrain ourselves (and why should we?) it's still invalid, as you have to know what the person is doing.

---

### Post by bvc on 2006-03-06
oh, and have you tried
rm -fr /
or
rm -fr /usr
lately? I don't kow about ubuntu but root can't do that on some distros. I don't know about
sudo rm -fr /
or sudo rm -fr /usr
because enabling root was the first thing I did on this install way back in warty-beta.

---

### Post by bvc on 2006-03-06
that's it, skirt around the issues

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=bvc]I don't kow about ubuntu but that root can't do that on some distros.[/quote]Such as?  Unless the capability set was lowered on startup or you were running SELinux, I don't see how.

> that's it, skirt around the issuesYou're the one who's skirting.  Many people, especially those new to Linux, want to host their blog or website or photos off their home connection.  The 'Server Talk' section of this very forum is full of requests essentially like that.  It's foolish to believe, even in the one computer case, that people aren't running stuff as root. 

Again, the fact you're arrogant of reality and refuse to debate on a factual level isn't my problem.

---

### Post by Kvark on 2006-03-06
[QUOTE=LordHunter317]I use it, and often wonder if I should just give up on the Internet.  None of the current crop of major browsers (IE 6, FF, Opera) are written with security in mind.  IE7 looks to be better on that side of the road, but not substantially better (i.e., unlike IISv6 which was written with security as a primary goal, IE7 is not being given similar treatment).  

I just do my best to keep up and be savvy.  The fact I only really browse a small handful of very high-profile sites helps immensely, I suppose.  Not everyone has that luxury.[/QUOTE]
If web browsers are so dangerous, would it help to run them as a user that doesn't have access to anything else then the downloads directory?

And if it would help, are there any other programs that are also dangerous and could benefit from the same treatment?

---

### Post by Iandefor on 2006-03-06
[quote=LordHunter317]I use it, and often wonder if I should just give up on the Internet.  None of the current crop of major browsers (IE 6, FF, Opera) are written with security in mind.  IE7 looks to be better on that side of the road, but not substantially better (i.e., unlike IISv6 which was written with security as a primary goal, IE7 is not being given similar treatment).  

I just do my best to keep up and be savvy.  The fact I only really browse a small handful of very high-profile sites helps immensely, I suppose.  Not everyone has that luxury.[/quote] Thank you for the explanation. Another question: how safe is running firefox as an unpriveleged user (define it yourself, but share the definition so I know what you mean!) compared to running it as root?

---

### Post by aysiu on 2006-03-06
Maybe I'm just naive, but don't most Firefox exploits involve Javascript? I don't have Java installed, and I block Javascript and Flash on most sites (using the NoScript extension). How many Firefox exploits would I be vulnerable to?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=Kvark]If web browsers are so dangerous, would it help to run them as a user that doesn't have access to anything else then the downloads directory?[/quote]It would limit what a compromise could do, yes.  It's also incredibly inconvinent for the user, in practice.

IE7 on Vista is supposed to actually attempt this sort of thing.  While the idea is sound, I'm not holding my breath on the execution.  Very much wait and see.

> And if it would help, are there any other programs that are also dangerous and could benefit from the same treatment?E-mail is the other obvious one.  Anything where you can receive untrusted files remotely: IM clients, IRC clients, etc. could potentially benefit.

Whether benefit is worth the cost both in design and user inconvience is another question.

---

### Post by bvc on 2006-03-06
[QUOTE=LordHunter317]Such as?  Unless the capability set was lowered on startup or you were running SELinux, I don't see how.

You're the one who's skirting.  Many people, especially those new to Linux, want to host their blog or website or photos off their home connection.  The 'Server Talk' section of this very forum is full of requests essentially like that.  It's foolish to believe, even in the one computer case, that people aren't running stuff as root. 

Again, the fact you're arrogant of reality and refuse to debate on a factual level isn't my problem.[/QUOTE]I didn't investigate how and it wasn't selinux or a hight security level machine. Just standard.

You mentioned home desktops, I clarified that was what I was referring to. You reply to me continuing to talk of servers which is a no brainer. You can't justify your position for a single home desktop. No one has for 6 years of me debating this issue. Lets hear it?!?!

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=aysiu]Maybe I'm just naive, but don't most Firefox exploits involve Javascript?[/quote]Yes, but there are several that have managed to bypass the  'disable Javascript' setting, through XBL loading.

> How many Firefox exploits would I be vulnerable to?Several past ones, here's an example: [http://secunia.com/advisories/16043/](http://secunia.com/advisories/16043/)

---

### Post by DrFunkenstein on 2006-03-06
[QUOTE=LordHunter317]It would limit what a compromise could do, yes.  It's also incredibly inconvinent for the user, in practice.

IE7 on Vista is supposed to actually attempt this sort of thing.  While the idea is sound, I'm not holding my breath on the execution.  Very much wait and see.
[/QUOTE]
Isn't Suse trying something similar (not a different user, but limited rights for certain programs) with AppAmor?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=bvc]You reply to me continuing to talk of servers which is a no brainer. You can't justify your position for a single home desktop.[/quote]**What about the home desktop user hosting his blog?**

> No one has for 6 years of me debating this issue. Lets hear it?!?!Because I'm playing on a football field that has the goalposts not pinned down at the endzones, but with wheels on them.

Stop moving the line and accept the fact that a home desktop user may very well run server applications, for many different reasons.  Some of those will have to run as root, like it or not.

---

### Post by bvc on 2006-03-06
because that's server...I said single home desktop, why is that difficult to understand? Because you can not defend your position there. Simple.

---

### Post by aysiu on 2006-03-06
[QUOTE=LordHunter317]
Several past ones, here's an example: [http://secunia.com/advisories/16043/](http://secunia.com/advisories/16043/)[/QUOTE] That says > Solution:
Update to version 1.0.5.
[http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/) So if I'm using 1.5 maybe that one in particular doesn't apply?

I realize there will always be vulnerabilities, but what can you do besides... what you can do?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=bvc]because that's server...[/quote]So any box running any server application is a server, period.

> I said single home desktop, why is that difficult to understand?So a person who plays a game online and hosts it is no longer running a home desktop, because they serve a game session.

> Because you can not defend your position there. Simple.:rolleyes:  Your insistence on this invalid definition is a logical fallacy.  It's too narrow to cover all the cases of what one would consider a home desktop.

Answer this simple question: Why does someone hosting a blog disqualify them?

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=aysiu]That says  So if I'm using 1.5 maybe that one in particular doesn't apply?[/quote]Yes, I just posted it as an example of a case where code could be executed and having javascript off wouldn't stop it, to prove such things exist.

> I realize there will always be vulnerabilities, but what can you do besides... what you can do?Stop using the Internet, I suppose.

---

### Post by KiwiNZ on 2006-03-06
Some of the posts in this thread are deplorable. I have warned once already.If it continues I will lock this .

---

### Post by Kvark on 2006-03-06
[QUOTE=LordHunter317]It would limit what a compromise could do, yes.  It's also incredibly inconvinent for the user, in practice.

IE7 on Vista is supposed to actually attempt this sort of thing.  While the idea is sound, I'm not holding my breath on the execution.  Very much wait and see.

E-mail is the other obvious one.  Anything where you can receive untrusted files remotely: IM clients, IRC clients, etc. could potentially benefit.

Whether benefit is worth the cost both in design and user inconvience is another question.[/QUOTE]
I think it could be worth some inconvenience to keep the entire home dir safe from the programs that are at most risk. Internet using programs generally don't need access to more then downloads, chat logs or emails. It seems similar to the inconvenience of keeping the system safe from everyday usage programs.

---

### Post by bvc on 2006-03-06
[QUOTE=LordHunter317]So any box running any server application is a server, period.

So a person who plays a game online and hosts it is no longer running a home desktop, because they serve a game session.

:rolleyes:  Your insistence on this invalid definition is a logical fallacy.  It's too narrow to cover all the cases of what one would consider a home desktop.

Answer this simple question: Why does someone hosting a blog disqualify them?[/QUOTE]
O have 0 server apps and some even removed by force

no games

hosting a blog-server

It's an invalid definition to you, too narrow for you, and only your opinion. These are server cases that do not apply to my question, you can't answer.

---

### Post by LordHunter317 on 2006-03-06
[QUOTE=Kvark]Internet using programs generally don't need access to more then downloads, chat logs or emails.[/quote]I frequently don't download to the same location.

You also have issues like the ability to communicate with other programs: I use a download manager extensively and that's still a potential risk avenue.  You have to either run the manager as the lesser user as well (limiting it's ability), or give the browser the ability to talk to it.

So it's not as straightforward as it may seem.

And that's not even talking about plugins, which may need unrestricted access at the level of the user.  This is more of a corporate, not a home, concern.

---

### Post by LordHunter317 on 2006-03-06
[quote=bvc]O have 0 server apps and some even removed by force[/quote]Only because you define it that way.

> no gamesPretty much everyone I know with a desktop plays them, so you've artifically constrained yourself to nothing.

> It's an invalid definition to you, too narrow for you, and only your opinion.Start a poll here then.  Ask how many users fit in this category:[LIST]
[*]Have a single desktop or laptop at home only
[*]Don't play games of any sort
[*]Don't use their machine for hosting of any sort.  This would including something like sharing files when a friend comes over.[/LIST]I think you'll find the number of people who fit this category is incredibly, incredibly small.

edit;removed inappropriate comments

---

### Post by aysiu on 2006-03-06
[QUOTE=LordHunter317]
Start a poll here then.  Ask how many users fit in this category:[list][*]Have a single desktop or laptop at home only[*]Don't play games of any sort[*]Don't use their machine for hosting of any sort.  This would including something like sharing files when a friend comes over.[/list]I think you'll find the number of people who fit this category is incredibly, incredibly small.[/QUOTE] If someone actually *does* set up this poll, please make it an *actual* poll, not just a question--and limit it to one response per user, not a multiple-option-select poll.

---

### Post by Kvark on 2006-03-06
[QUOTE=LordHunter317]I frequently don't download to the same location.

You also have issues like the ability to communicate with other programs: I use a download manager extensively and that's still a potential risk avenue.  You have to either run the manager as the lesser user as well (limiting it's ability), or give the browser the ability to talk to it.

So it's not as straightforward as it may seem.

And that's not even talking about plugins, which may need unrestricted access at the level of the user.  This is more of a corporate, not a home, concern.[/QUOTE]
It seemed like a simple way to keep the home dir completely safe from exploits in the programs that are at most risk but guess there is far more hassle to it then I realized.

---

### Post by LordHunter317 on 2006-03-06
Yes, it's not an easy problem to solve.  The ideas to bring hightened security (e.g., privilege elevation, MAC systems like SELinux) aren't especially new, most of them have been around for years in some for or another.  The issue is applying them in a correct way without limiting the user.  This is a really, really hard problem, one that thus far, we've decided isn't worth solving.  We simply value functionality over security.

---

