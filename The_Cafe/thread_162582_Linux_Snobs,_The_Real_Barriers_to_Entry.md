---
title: "Linux Snobs, The Real Barriers to Entry"
date: 2006-04-19
forum: The Cafe
---

### Post by Zodiac on 2006-04-19
[That's why I've been sayin'!!!]("http://www.reallylinux.com/docs/snobsoped.shtml")

Seriously, I would never have tried (and now, used for as long as I have) Ubuntu if the community wasn't as great as it is... still... there is *always* room for improvement.

---

### Post by Sushi on 2006-04-19
Try the Mac-community one day :rolleyes:....

---

### Post by prizrak on 2006-04-19
Pfft neither of you are good enough for my Linux! ;)

---

### Post by Stormy Eyes on 2006-04-19
There are snobs and bigots in every user community. I'm willing to bet that there are plenty in the Windows community, and I know damned well there are quite a few in the Mac, BSD, and Linux camps.

I got my fair share of "RTFM n00b!" comments as a beginner. I didn't let the assholes stop me.

---

### Post by towsonu2003 on 2006-04-19
[QUOTE=Zodiac]
Seriously, I would never have tried (and now, used for as long as I have) Ubuntu if the community wasn't as great as it is[/QUOTE]
I second that.

---

### Post by Zodiac on 2006-04-19
[QUOTE=Stormy Eyes]There are snobs and bigots in every user community. I'm willing to bet that there are plenty in the Windows community, and I know damned well there are quite a few in the Mac, BSD, and Linux camps.

I got my fair share of "RTFM n00b!" comments as a beginner. I didn't let the assholes stop me.[/QUOTE]

I hear that... I change my IRC nick as many times as I have to dammit!!!

;)

---

### Post by Sheinar on 2006-04-19
The ones who "bash Windows, bash him and bash everything he said" and say things like "you ignoramous! Go back to your Windows." are likely to be the same idiots who say "Micro$oft", "Microshaft" and "Winblows". And most "pros" aren't that damn stupid. The ones who act like that are usually the type who just want to fit in, and think their e-penis grows if they mock new users.

---

### Post by OffHand on 2006-04-19
I couldn't care less about some geeks trying to diss me  :mrgreen:

---

### Post by asimon on 2006-04-19
I highly doubt that there is any correlation between the unfriendliness of people and the operating system they use.

---

### Post by aysiu on 2006-04-19
I've been on Mepis Lovers, Linux Questions, Linux Forums, Kubuntu Forums, and Ubuntu Forums.

No one has ever told me to RTFM.

I'm not saying I've never seen anyone tell someone *else* to RTFM, but no one's ever said it to me.

I don't think people *should* say RTFM, but I do believe they don't say it haphazardly. It's usually targeted at someone who isn't demonstrating that she has tried to read any kind of documentation or search for an answer (even if she did).

I think it's important for people asking questions to spell out for others not only what the problem is but also what they've tried and what they've searched for and read.

While I've seen my fair share of new users who are too lazy to find anything themselves, I've also seen some pretty crappy documentation. I mean, when people say, "Look at the *man* page for blahblahblah," do they realize that most of those *man* pages are gobbledygook to non-programmers?

I usually can't make any sense out of *man* pages, and I try--I really do.

Take, for example, *adduser*. After reading this, I have no idea what an actual *adduser* command would look like: ```
adduser(8) - Linux man page
NAME 
useradd - Create a new user or update default new user information
SYNOPSIS 

useradd [-c comment] [-d home_dir]
    [-e expire_date] [-f inactive_time] [-g initial_group] [-G group[,...]] [-m [-k skeleton_dir] | -M] [-n] [-o] [-p passwd] [-r] [-s shell] [-u uid] login 
useradd -D [-g default_group] [-b default_home]
    [-e default_expire_date] [-f default_inactive] [-s default_shell]

DESCRIPTION 
Creating New Users 
When invoked without the -D option, the useradd command creates a new user account using the values specified on the command line and the default values from the system. The new user account will be entered into the system files as needed, the home directory will be created, and initial files copied, depending on the command line options. The version provided with Red Hat Linux will create a group for each user added to the system, unless the -n option is given. The options which apply to the useradd command are:

-c comment
    The new user's password file comment field. 
-d home_dir
    The new user will be created using home_dir as the value for the user's login directory. The default is to append the login name to default_home and use that as the login directory name. 
-e expire_date
    The date on which the user account will be disabled. The date is specified in the format YYYY-MM-DD. 
-f inactive_days
    The number of days after a password expires until the account is permanently disabled. A value of 0 disables the account as soon as the password has expired, and a value of -1 disables the feature. The default value is -1. 
-g initial_group
    The group name or number of the user's initial login group. The group name must exist. A group number must refer to an already existing group. The default group number is 1 or whatever is specified in /etc/default/useradd. 
-G group,[...]
    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the -g option. The default is for the user to belong only to the initial group. 
-m
    The user's home directory will be created if it does not exist. The files contained in skeleton_dir will be copied to the home directory if the -k option is used, otherwise the files contained in /etc/skel will be used instead. Any directories contained in skeleton_dir or /etc/skel will be created in the user's home directory as well. The -k option is only valid in conjunction with the -m option. The default is to not create the directory and to not copy any files. 
-M
    The user home directory will not be created, even if the system wide settings from /etc/login.defs is to create home dirs. 
-n
    A group having the same name as the user being added to the system will be created by default. This option will turn off this Red Hat Linux specific behavior. 
-o
    Allow create user with duplicate (non-unique) UID. 
-p passwd
    The encrypted password, as returned by crypt(3). The default is to disable the account. 
-r
    This flag is used to create a system account. That is, a user with a UID lower than the value of UID_MIN defined in /etc/login.defs and whose password does not expire. Note that useradd will not create a home directory for such an user, regardless of the default setting in /etc/login.defs. You have to specify -m option if you want a home directory for a system account to be created. This is an option added by Red Hat. 
-s shell
    The name of the user's login shell. The default is to leave this field blank, which causes the system to select the default login shell. 
-u uid
    The numerical value of the user's ID. This value must be unique, unless the -o option is used. The value must be non-negative. The default is to use the smallest ID value greater than 99 and greater than every other user. Values between 0 and 99 are typically reserved for system accounts.

Changing the default values 
When invoked with the -D option, useradd will either display the current default values, or update the default values from the command line. The valid options are

-b default_home
    The initial path prefix for a new user's home directory. The user's name will be affixed to the end of default_home to create the new directory name if the -d option is not used when creating a new account. 
-e default_expire_date
    The date on which the user account is disabled. 
-f default_inactive
    The number of days after a password has expired before the account will be disabled. 
-g default_group
    The group name or ID for a new user's initial group. The named group must exist, and a numerical group ID must have an existing entry . 
-s default_shell
    The name of the new user's login shell. The named program will be used for all future new user accounts.

If no options are specified, useradd displays the current default values.
NOTES 
The system administrator is responsible for placing the default user files in the /etc/skel directory. This version of useradd was modified by Red Hat to suit Red Hat user/group conventions.
CAVEATS 
You may not add a user to an NIS group. This must be performed on the NIS server.
FILES 
/etc/passwd - user account information /etc/shadow - secure user account information /etc/group - group information /etc/gshadow - secure group information /etc/default/useradd - default information /etc/login.defs - system-wide settings /etc/skel - directory containing default files
SEE ALSO 
chfn(1), chsh(1), passwd(1), crypt(3), groupadd(8), groupdel(8), groupmod(8), userdel(8), usermod(8)
AUTHOR 
Julianne Frances Haugh (jockgrrl@ix.netcom.com)
die.net
```

I think we all just need to realize we're human. Others are human. 

To new users--old users are not your lackeys, and they aren't obligated to help you. They're volunteers and fellow users, who are kind enough to take some of their precious time to help you out. So it's only fair that you make the effort to find your own answers and explain your situation fully so that others can help you.

To old users--new users don't understand everything you do. That documentation or those commands may make perfect sense to you, but a new user may not even know where the terminal is. For months, when I first started with Ubuntu, I would read people saying, "Oh, just use *visudo*" or "You can install that with Synaptic." Few people take the time to actually explain what the syntax is for "using" visudo or how to install things with Synaptic (or even where Synaptic is).

We just need to meet each other half way.

---

### Post by Zodiac on 2006-04-19
With Linux, you are wrong.

I will not use a distro with a snotty community because I am going to need them when I have beefs with my system.

Windows and OSX don't even have to HAVE communities for all I care.

---

### Post by Sushi on 2006-04-19
[QUOTE=Zodiac]Windows and OSX don't even have to HAVE communities for all I care.[/QUOTE]

Well, they do. I have been to the macrumors.com-forums, and trust me, you haven't missed a thing. I have also been in some Finnish Mac-related forums. And if you thought that Linux-users hate Windows, you should see the Mac-heads! Not only do they hate Windows, they hate everything non-Mac. Linux? Crap. Windows? Crap. FreeBSD is tolerable, since OS X uses some FreeBSD-tools, other BSD's are crap. SGI? Totally crap, software and hardware. Solaris? crap. And the list goes on.

dare I mention what happened when I mentioned that I would be interested in running Linux on my Mac Mini? "Why on EARTH would you want to run Linux on it?!?!?!". Duh, because I'm a Linux-user, and I prefer Linux over OS X. But that possibility was simply 100% impossible to them. To them, there is simply NO WAY that someone could prefer ANYTHING over OS X. And yes, I was flamed, and I was called stupid.

One of the reasons I stopped using the Mac entirely was simply because I didn't want to associate myself with those people. So yes, the article does have a point, but Linux-community is not the worst example of this behavior.

---

### Post by John.Michael.Kane on 2006-04-19
I don't think it's so much the Linux-community being snobs to new users/ect as it is each user you incounter who answers your questions on forums may have a diffrent way of dealing with questions/responces then some others just cause you may not like the way it is said or how the user is being giving help does not make them snobs. I have never seen anyone here tell a newuser to RTFM they may tell the user to search the forum before they post however that kind of responce is not always met with understanding it is better then hearing rtfm. UbuntuForums to me is very welcoming of all questions/polls ect from any kind of user.



Just my thoughts..

---

### Post by not28 on 2006-04-19
I'm a Mac/Windows/Linux user. I'm better than all of you!!! Muahahahaa!

/me gets killed by angry mob

---

### Post by not28 on 2006-04-19
There are snobs in every community. Ever play an online RPG like Everquest of WoW? Ask them to explain some common vernacular and you get roasted.

---

### Post by John.Michael.Kane on 2006-04-19
not28 no ones going to flame you. mac/windows/linux suit your needs, and this is fine. I think the issues that are being talked about come into play when some users post linux is not ready for this or that or windows and mac does this why can't linux ect thats when some of the issues crop up, however this is just guess.

---

### Post by Stormy Eyes on 2006-04-19
[QUOTE=not28]There are snobs in every community. Ever play an online RPG like Everquest of WoW? Ask them to explain some common vernacular and you get roasted.[/QUOTE]

I used to play NWN (*Neverwinter Nights*) online. When I encountered terminology that I didn't understand, I googled before I started bothering other people.

---

### Post by IYY on 2006-04-19
I happen to like TFM.

---

### Post by AlphaMack on 2006-04-19
[QUOTE=IYY]I happen to like TFM.[/QUOTE]

Unless it's full of TBAs.

With that said, I am a OS X/Linux user.  After being in both communities, I must say that the snobbery and zealotry runs more rampant in the Mac camps.

I was once told by a Maccie, "I hope you enjoy your Linux while the rest of us use a REAL operating system."  I've also been given the following comments along the lines of...

"Hope you have fun compiling everything..."
"Enjoy dependency hell..."
"Don't let the door hit you on the way out..."

None of the crap they come up with has ever applied to my experiences with Linux, especially Ubuntu.  I only had one dependency issue and it was a simple hunt.  For the most part, the apps on my machines play nicely.

The funny part?  I have to compile apps under Fink and Darwin Ports!  Go figure.

I can tell you this:  Maccies are scared of the command line and depend on snake oil products to "fix" their systems (e.g. scripts, shareware, ad nauseam).  They'll flame you if you even dare mention a hint of the command line as a fix.  I use CLIX a lot whenever I need to tweak some things since a database of commands comes in handy without having to manually enter them into the terminal window.

I've never been told to RTFM on the Linux side, but sometimes I'll end up talking to myself on these forums when I eventually find the solution to my issues on my own.

---

### Post by aysiu on 2006-04-19
[QUOTE=alphasubzero949]
With that said, I am a OS X/Linux user.  After being in both communities, I must say that the snobbery and zealotry runs more rampant in the Mac camps.

I was once told by a Maccie, "I hope you enjoy your Linux while the rest of us use a REAL operating system."  I've also been given the following comments along the lines of...

"Hope you have fun compiling everything..."
"Enjoy dependency hell..."
"Don't let the door hit you on the way out..."[/quote] I've seen this same attitude on the [http://www.xvsxp.com/forums](http://www.xvsxp.com/forums)

The Linux users there are reasonable, and the Mac users tend to be ignorant of anything Linux, but very aggressive about it.

> 
I can tell you this:  Maccies are scared of the command line and depend on snake oil products to "fix" their systems (e.g. scripts, shareware, ad nauseam).  They'll flame you if you even dare mention a hint of the command line as a fix. While there may be a lot of "Maccies" like that, I think there's also a significant portion of the Mac OS X-using population that actually loves the command-line and embraces it.

---

### Post by nalmeth on 2006-04-19
Hmm, the author is worried that there are user's with extreme view's and policies about their operating system, and are scaring people away with their attitudes?
This is an "issue" that has to be "addressed"?
I wonder how far linux would have developed were it not for the extremist's who refused to put up with proprietary software, and who had the determination to go up against some tough odds. Are Richard Stallman or Eric Raymond considered snobs? If so, then I don't think we have enough!
And this article points out the helpful and courteous people as an afterthought. 
Seriously, the amount of times I have seen people go out of their way to walk somebody through the toughest problems, for day's and day's.
You run into all kinds of different people in forums, you should expect to see some ranging levels of opinion and behavior.

---

### Post by Sheinar on 2006-04-19
[QUOTE=nalmeth]Eric Raymond[/QUOTE]
Not a snob, just an idiot.

---

### Post by nalmeth on 2006-04-19
Haha
An idiot, yes, but he gets a lot of attention.

---

### Post by awakatanka on 2006-04-19
Hate it when people are bitching because someone has a different opinion then someone else. I can understand that someone can get frustrated if they see a post that is answered x times before, but to answer wit a bad attitude doesn't solve anything also, better don't answer at all then. Search function doesn't work that great also. 

If someone get frustrated because of a n00b question just stay out of the thread our post something like " this is answered before in a other topic" if you realy want to post something.

---

### Post by Gijith on 2006-04-19
When I first came over from Windows, I was expecting everyone Linux person I encountered to be a total Revenge of the Nerds type a-hole. But, with a few glaring exceptions, everyone here is very nice and very accomodating to those of us who are scared of computers.

---

### Post by aysiu on 2006-04-19
[QUOTE=awakatanka]
If someone get frustrated because of a n00b question just stay out of the thread our post something like " this is answered before in a other topic" if you realy want to post something.[/QUOTE] ... and then link to that topic or a search that would pop up all the threads relating to that topic.

---

### Post by joflow on 2006-04-19
This forum doesn't have that problem in regards to linux noobs who need help.  However, there are some elitist here who will tell you to just use windows if you don't regard gnu/linux as the perfect operating system.  Most of us come from windows backgrounds...we know what windows has to offer and apparently we're showing some interest in wanting to see linux improve.  The great thing about linux is that our input might actually be taken into consideration by developers.  We know windows isn't perfect either but theres little we can do about that since the decisions are made behind closed doors.  So its not like you're making a useful suggestion by telling us to use windows.

There are some real a-holes on IRC though (not in the ubuntu channels).  I once asked rasterman (the guy behind e17) if there were any plans to add improved integration with gnome and he went on this tangent ("you obviously no idea how blah blah blah works")..geez it was just a suggestion.  I think most linux developers aren't that rude however.

---

### Post by aysiu on 2006-04-19
[QUOTE=joflow]However, there are some elitist here who will tell you to just use windows if you don't regard gnu/linux as the perfect operating system.[/QUOTE] It really depends.

Some people are able to appreciate Linux for what it is **and** offer helpful suggestions to the developers to improve it.

Others just can't adjust to a different way of doing things and want Linux to behave exactly like Windows.

For the former, it would be rude to recommend a return to Windows. For the latter, it's the most appropriate advice there is.

---

### Post by nalmeth on 2006-04-19
[quote=joflow]This forum doesn't have that problem in regards to linux noobs who need help.  However, there are some elitist here who will tell you to just use windows if you don't regard gnu/linux as the perfect operating system.  Most of us come from windows backgrounds...we know what windows has to offer and apparently we're showing some interest in wanting to see linux improve.  The great thing about linux is that our input might actually be taken into consideration by developers.  We know windows isn't perfect either but theres little we can do about that since the decisions are made behind closed doors.  So its not like you're making a useful suggestion by telling us to use windows.

There are some real a-holes on IRC though (not in the ubuntu channels).  I once asked rasterman (the guy behind e17) if there were any plans to add improved integration with gnome and he went on this tangent ("you obviously no idea how blah blah blah works")..geez it was just a suggestion.  I think most linux developers aren't that rude however.[/quote]

In some cases, telling the person to go back to Windows may be the right way after all.
People that have special hardware designed only for windows.
The hardcore guys are working their asses off to get everything to just run, and I can see why they might get frustrated, when some guy tells him he has to make this work better with that, and make it work in this way, on that device.
I just might flip out too. Especially if I'm working in my spare time only to give away all my work for free.
I think as long as we can get by with each other's emotional states, things will get worked out.
Rasterman is probably working hard just to iron out the major bugs which cause segfaults in E17. You must admit it seems a little premature to 'suggest' that it be better integrated with gnome, when it is not even near beta stage yet.
Will his reaction make you stop using E17?

---

### Post by malavar on 2006-04-19
All the linux guys i ever met were very nice(in real life), including college professors , which are sometimes bigots. i read that article on digg.com , it was funny, some irc channels and forums do have  a bunch of pricks who are on a mission to prove how cool/smart they are though.

---

### Post by Christmas on 2006-04-19
[QUOTE=not28]There are snobs in every community. Ever play an online RPG like Everquest of WoW? Ask them to explain some common vernacular and you get roasted.[/QUOTE]

Yes, you're right. I saw the same way of treating in any kind of online game. Looks like it's not something related only to Linux or Mac world, but something that's in the human nature.

---

### Post by John.Michael.Kane on 2006-04-19
One must also take into account those who try to cause issues with their post on forums.

---

### Post by BarfBag on 2006-04-19
Mac snobs are the worst kind.  Say ONE thing that criticizes Mac OS X, and your automatically flamed and considered a Linux fan boy.  They worship their computers too.  It's really hilarious.

---

### Post by htinn on 2006-04-19
Nice article.

> Second, I want to make sure you know my conviction that most of the people I encounter in the Open Source world, and among Linux engineers and project members specifically, are some of the smartest and nicest people I've met. Notice the coupling: smart AND nice. Being smart doesn't make you automatically nice and vice versa. In my case I had met many who were both.

Yay us. :)

> As described by Jason, the engineer began to mock Windows users, declared that Jason was "obviously ignorant and inexperienced" and continued by giving his personal opinions on various topics from religion to political philosophy.

Note to self: Avoid arguments with engineers.

---

### Post by briancurtin on 2006-04-19
[QUOTE=Zodiac]I hear that... I change my IRC nick as many times as I have to dammit!!!

;)[/QUOTE]
you shouldnt even have to do that. i use my real name and i dont give a shit what anyone says about anything. i am who i am, i know what i know, and im not hiding.

---

### Post by Sushi on 2006-04-20
[QUOTE=BarfBag]Mac snobs are the worst kind.  Say ONE thing that criticizes Mac OS X, and your automatically flamed and considered a Linux fan boy.  They worship their computers too.  It's really hilarious.[/QUOTE]

Heh, I remember when one guy in forums.macrumors.com said how XP is utter crap and how it crashes all the time (it doesn't). I then casually commented that "I run XP on my corporate workstation and it has now been running for three weeks straight". He then started telling me how I'm not using the system properly (for example, multitasking. And I AM multitasking) or how I'm an exception to the rule. I then mentioned that I do run several big apps at the same time and there are LOTS of people at my workplace who don't have problems with XP crashing. His reply?

"What are you, some ultimate Micro$oft fanboy? Do you worship the ground Gates and Ballmer stands on? Why are you exactly on these forums anyway?". And EVERY TIME anyone says ANYTHING good about Windows, that particular guy (*cough*Photorun*cough*) comes running along and start his "why are you on these forum anyway?"-tirade. You should really see him talk about Microsoft and Windows. His comments just ooze pure hatred for anything related to Windows. I have never seen anything like that in the Linux-community, even though we have out share of MS-hatred.

As it happens, I hate Microsoft and their business-practices. I dislike XP, I have been using Linux since 1998-1999, and I use Windows at home maybe once a month, if that. Yeah, some "fanboy".

---

### Post by Zodiac on 2006-04-20
[QUOTE=BarfBag]Mac snobs are the worst kind.  Say ONE thing that criticizes Mac OS X, and your automatically flamed and considered a Linux fan boy.  They worship their computers too.  It's really hilarious.[/QUOTE]

Linux snobs are the worst kind.  Say ONE thing that criticizes Linux, and your automatically flamed and considered a Microsoft/Apple fan boy.  They worship their computers too.  It's really hilarious.

See where I'm going with this???

---

### Post by prizrak on 2006-04-20
[QUOTE=Zodiac]Linux snobs are the worst kind.  Say ONE thing that criticizes Linux, and your automatically flamed and considered a Microsoft/Apple fan boy.  They worship their computers too.  It's really hilarious.

See where I'm going with this???[/QUOTE]
* Snobs are just the worst kind in general :)

---

### Post by aysiu on 2006-04-20
[QUOTE=Zodiac]Linux snobs are the worst kind.  Say ONE thing that criticizes Linux, and your automatically flamed and considered a Microsoft/Apple fan boy.[/QUOTE] [Here are about 400 posts that prove you wrong](http://www.ubuntuforums.org/showthread.php?t=57994). Sorry, but I haven't seen that to be the case at all.

I have, however, seen actual Windows fan-boys not recognizing anything worthwhile in Linux, thinking everything in Linux should be done the way Windows does it, and complaining about problems only on the forums instead of filing bug reports... and then being flamed and then thinking that anyone who criticizes Linux will be flamed.

No, it's not just anybody. Sorry.

---

### Post by prizrak on 2006-04-20
[QUOTE=aysiu][Here are about 400 posts that prove you wrong](http://www.ubuntuforums.org/showthread.php?t=57994). Sorry, but I haven't seen that to be the case at all.

I have, however, seen actual Windows fan-boys not recognizing anything worthwhile in Linux, thinking everything in Linux should be done the way Windows does it, and complaining about problems only on the forums instead of filing bug reports... and then being flamed and then thinking that anyone who criticizes Linux will be flamed.

No, it's not just anybody. Sorry.[/QUOTE]
To be fair, he didn't say ALL Linux users were like that, there are snobs though who will call you a fanboy if you even metnion some issue. Hell go to Gentoo forums, they are called ricers for a reason and look down on Ubuntu users. Hell even my friend who uses Gentoo sometimes does that to me and his a good friend :)

---

### Post by aysiu on 2006-04-20
[QUOTE=prizrak]To be fair, he didn't say ALL Linux users were like that, there are snobs though who will call you a fanboy if you even metnion some issue.[/QUOTE] Touche.

---

### Post by Zodiac on 2006-04-21
[QUOTE=aysiu]Touche.[/QUOTE]

Exactly... I definitely wasn't saying ALL Linux users were like that... 

SOME are, just like there are some Windows snobs, Apple snobs, etc. HOWEVER, I think the Linux snobs have more of an effect because people are so clueless when it comes to Linux... 

Like myself for example, I waited to try Linux until there was a distro that had a more helpful community. I would not have even tried to install it if I had gotten one "RTFM" when I had a question. I just don't have time to search man pages or something if an answer isn't clearly listed somewhere or forthcoming. 

If Ubuntu did not come about, I would never, EVER, have tried Linux. It has the community and the documentation that no other distro in existence can match. Hence, I believe it is better by a wide margin. 

So yea&#8230;

---

### Post by htinn on 2006-04-21
I've been using Linux in one form or another for a few years, and I'm not the least bit hesitant to admit that I am a Linux snob. So what? It's superior, and that's a fact. If you can't deal with that, then maybe you should see a therapist.

Having said that, I've run into some REAL Linux snobs who make even me want puke with their narrow-mindedness. It's all part of life, and you just have to deal with it cheerfully and move on or you won't get very far in any aspect of it. Here's some helpful pointers:

Don't complain to developers. Don't be surprised if you get badly flamed when you do, either. Don't then turn around and complain to us with some highly edited version of the account to show how "badly you were treated by some snob". I'm not going to buy it. Those type of complaints are from people who've had their ego bruised because THEY said something stupid and got caught in it.

Don't talk about vague concept ideas to developers. Chances are that they don't know jack about design. They understand code, but they suck at design or they suck at describing how to design.

In fact, just plain don't talk to developers. Lots of developers are great at developing and BAD at social skills. Do the math. :)

---

### Post by prizrak on 2006-04-21
> I've been using Linux in one form or another for a few years, and I'm not the least bit hesitant to admit that I am a Linux snob. So what? It's superior, and that's a fact. If you can't deal with that, then maybe you should see a therapist.
I would have to highly disagree with that. I'll give you one simple example, sound. Linux is still nowhere near the ease of use and quality when it comes to sound in even Windows I won't even mention OS X. (Video is also not that great but it might be a codec issue). However it is superior in other ways, just like with everything there are good things and there are bad things.

---

### Post by BoyOfDestiny on 2006-04-21
[QUOTE=prizrak]I would have to highly disagree with that. I'll give you one simple example, sound. Linux is still nowhere near the ease of use and quality when it comes to sound in even Windows I won't even mention OS X. (Video is also not that great but it might be a codec issue). However it is superior in other ways, just like with everything there are good things and there are bad things.[/QUOTE]

This depends on hardware. If you have a decent soundcard, Audigy2 ZS, sound rocks hard. Much easier to deal with my speaker volumes (side, center, rear, etc) in Ubuntu than windows. However, on my other machines I did have issues. Your mileage may vary, sweeping generalizations aside...

---

### Post by prizrak on 2006-04-21
[QUOTE=BoyOfDestiny]This depends on hardware. If you have a decent soundcard, Audigy2 ZS, sound rocks hard. Much easier to deal with my speaker volumes (side, center, rear, etc) in Ubuntu than windows. However, on my other machines I did have issues. Your mileage may vary, sweeping generalizations aside...[/QUOTE]
Not exactly what I was talking about actually. My sound hardware is recognized just fine and the quality is acceptable (it's a laptop I don't expect much from it). However there are issues, for instance there are like 3 different sound subsystems (that I can name off the top of my head installed by default), ALSA, OSS, ESD, and some programs use different ones. There is also the no multiple sound issue, while that is fixable it's not a default and for instance I still don't get multiple sounds with Flash, others reported issues with Skype. I know there probably issues with whoever created the software. 
My basic point in all of this is that Linux in general and Ubuntu in particular is hardly superior to any other modern OS on all fronts. It has issues other OS's don't have and it has features other OS's don't have. 
P.S. I love Ubuntu and I'm planning on sticking with it.

---

### Post by BoyOfDestiny on 2006-04-21
[QUOTE=prizrak]Not exactly what I was talking about actually. My sound hardware is recognized just fine and the quality is acceptable (it's a laptop I don't expect much from it). However there are issues, for instance there are like 3 different sound subsystems (that I can name off the top of my head installed by default), ALSA, OSS, ESD, and some programs use different ones. There is also the no multiple sound issue, while that is fixable it's not a default and for instance I still don't get multiple sounds with Flash, others reported issues with Skype. I know there probably issues with whoever created the software. 
My basic point in all of this is that Linux in general and Ubuntu in particular is hardly superior to any other modern OS on all fronts. It has issues other OS's don't have and it has features other OS's don't have. 
P.S. I love Ubuntu and I'm planning on sticking with it.[/QUOTE]

I hear ya, but as for the no multiple sound issues etc. no problems on this card out of the box. I'm not sure if ESD interfered with software using OSS, since I disabled that the moment I installed Ubuntu.
 On other machines with Ubuntu, yep had to do tweaking and often ESD caused problems. :) 

Hopefully if everything just goes ALSA (which seems to be the best way to go IMHO), a lot of these problems will go away. ALSA with dmix on dapper finally fixed multiple sounds on my laptop (with an .asoundrc :) ) I had just been "putting up" with it since I love Ubuntu too.

---

### Post by prizrak on 2006-04-21
Glad to see that Dapper is fixing one of the most annoying issues EVER :) I must say I am AMAZED at the development and improvement speed of Ubuntu, I got in on the ground floor (Hoary was it?) and LOVED it from the beginning, was finally able to switch the lappy to it exclusively. Now with Breezy I didn't even need Windows till I decided to play with Media Center (kinda a pain with Myth, tho considering issues I had with MCE would prolly be the same). It seems that Dapper will surpas Vista when it's released and Vista won't even be remotely ready by that time :)

---

### Post by BoyOfDestiny on 2006-04-21
[QUOTE=prizrak]Glad to see that Dapper is fixing one of the most annoying issues EVER :) I must say I am AMAZED at the development and improvement speed of Ubuntu, I got in on the ground floor (Hoary was it?) and LOVED it from the beginning, was finally able to switch the lappy to it exclusively. Now with Breezy I didn't even need Windows till I decided to play with Media Center (kinda a pain with Myth, tho considering issues I had with MCE would prolly be the same). It seems that Dapper will surpas Vista when it's released and Vista won't even be remotely ready by that time :)[/QUOTE]

Just in case it doesn't work out of the box for when you switch to dapper...

[http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)
"6. The complex approach (defining dmix parameters)"
Did the trick for my laptop's intel ich6. Just paste that into a .asoundrc in your home. I can load up dosbox, zsnes, totem, audacious, and get a nice cacophany... ;)

Well I guess I got this thread offtopic now... Um. Don't let snobs get you down :)

---

### Post by prizrak on 2006-04-21
[QUOTE=BoyOfDestiny]Just in case it doesn't work out of the box for when you switch to dapper...

[http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)
"6. The complex approach (defining dmix parameters)"
Did the trick for my laptop's intel ich6. Just paste that into a .asoundrc in your home. I can load up dosbox, zsnes, totem, audacious, and get a nice cacophany... ;)

Well I guess I got this thread offtopic now... Um. Don't let snobs get you down :)[/QUOTE]
Lol thanks I won't be going Dapper till it hits stable tho ;) And yeah them snobs are teh suck ;)

---

### Post by enopepsoo on 2006-04-26
When I migrated to Ubuntu last summer, I found that the people in #ubuntu were very kind and helpful regardless of what issue I was having.  I haven't had much experience with the forums yet, but people seem very nice here too.
I think Ubuntu has a community of a lot of former "sftu+rtfm n00b" recipients who stuck it out and now want to be a real help.  I want to be a real help, and I know that most of the people here (who are on average far more knowlegable than I) are the same.
This is not a problem with our distro like it is with others.

---

### Post by Resurrection on 2006-04-26
Its amazing that its "Whats in a Name"

Ubuntu.  I think the name started the community towards friendly treatment, not the community being friendly and giving it the name as a result.  Course, I've been here for about 2 seconds, so what do I know....:p 

But think about it:  If you had name this distro:  LEODUYFIN

L inux E xperts O nly, D on't U se Y ou F ***in I diot N oob


Think you would have a nice community then?

---

### Post by AlphaMack on 2006-04-26
I went barking up the wrong tree elsewhere and already got the n00b Linux user treatment. :roll:

There's a reason why I stuck with Ubuntu.  I've saved two PCs whose users have no freaking clue about Linux so as long as they can do their light computing tasks without fighting the system (Windows).

On my own machine?  I can get by, but I'm not an omniscient über-geek who uses an advanced distro to compensate for my e-nuts.

I'm now just starting to experience the nuts and bolts of Linux after a "just works" network install went south upon installing Mac-on-Linux + dnsmasq, ipmasq, and dhcpd.  Now it's clashing with Firestarter and my connectivity is hijacked in the process until I physically start the Firestarter program upon logging in.  I've been tearing my hair out over this for over two days now with no solution in sight.  I'm afraid of completely removing Firestarter and leaving no way for me to get online.

I know exactly what will happen if this were another distro and I had the same problem:  OMGroflRTFMuN00b13!!!111oneeleven  Or my thread will just be ignored and sink into the abyss of old threads.


I also just found out the hard way that Linux snobs don't tend to like Ubuntu users very much (we're n00bs in their eyes).

---

### Post by joflow on 2006-04-26
[QUOTE=nalmeth]In some cases, telling the person to go back to Windows may be the right way after all.
People that have special hardware designed only for windows.
The hardcore guys are working their asses off to get everything to just run, and I can see why they might get frustrated, when some guy tells him he has to make this work better with that, and make it work in this way, on that device.
I just might flip out too. Especially if I'm working in my spare time only to give away all my work for free.
I think as long as we can get by with each other's emotional states, things will get worked out.
Rasterman is probably working hard just to iron out the major bugs which cause segfaults in E17. You must admit it seems a little premature to 'suggest' that it be better integrated with gnome, when it is not even near beta stage yet.
Will his reaction make you stop using E17?[/QUOTE]

I wasn't asking for gnome integration right away...I was just wondering if there were any plans for it in the future.  From his response, he seemed anti-gnome.

And yes, I don't use E17 anymore.  I use XGL/Compiz/Gnome which I find to more usable and prettier

---

### Post by prizrak on 2006-04-26
[QUOTE=alphasubzero949]I went barking up the wrong tree elsewhere and already got the n00b Linux user treatment. :roll:

There's a reason why I stuck with Ubuntu.  I've saved two PCs whose users have no freaking clue about Linux so as long as they can do their light computing tasks without fighting the system (Windows).

On my own machine?  I can get by, but I'm not an omniscient über-geek who uses an advanced distro to compensate for my e-nuts.

I'm now just starting to experience the nuts and bolts of Linux after a "just works" network install went south upon installing Mac-on-Linux + dnsmasq, ipmasq, and dhcpd.  Now it's clashing with Firestarter and my connectivity is hijacked in the process until I physically start the Firestarter program upon logging in.  I've been tearing my hair out over this for over two days now with no solution in sight.  I'm afraid of completely removing Firestarter and leaving no way for me to get online.

I know exactly what will happen if this were another distro and I had the same problem:  OMGroflRTFMuN00b13!!!111oneeleven  Or my thread will just be ignored and sink into the abyss of old threads.


I also just found out the hard way that Linux snobs don't tend to like Ubuntu users very much (we're n00bs in their eyes).[/QUOTE]
Before you shutdown your computer, turn off all programs cept for firestarter, then pick "save current setup" on the shutdown menu and shutdown/restart/log out w/e you need. Next time firestarter will start up with Gnome :)

---

### Post by unrandomsam on 2006-04-30
I think it important to learn something about unix before starting to use it. You nothing blindly following howtos. If a new years asks my what to recommend I suggest using FreeBSD for a few months. Then turn to ubuntu in a few months after you understand some of the principles of how to unix effectively. (The FreeBSD handbook is very very well written). Also  
learning how to use vi is a good skill to have. (I read UNIX in a nutshell maybe 8 years ago and it probably still is a good introduction). 

I think RTFM is a reasonable response when the solution is documented in a totally obvious way and the user just through laziness hasn't read any of it.

---

### Post by DigitalDuality on 2006-04-30
I recently moved to Fedora.. and you know what?

I hate their forums.  The Suse forums are just as bad and don't get me started on Debian guys.

If most communities surrounding other distros were as friendly as this place is... Linux would be taking off.

I'll admit the zealotry can be a bit much.  But we also have to realize there's different types of "fanboyism".

The enthusiast, who notice's MS flaws... isn't so bad.. as long as he'll give MS or Mac credit where credit is due i find.

The FOSS fanboy.. well, they could be like a Demcrat..or like a PETA member.  It really depends.  There's a range with the philosophy in how extreme one takes it.

Then you have the "blame microsoft first" crowd who are annoying as hell and only hate them b/c they're so huge.  They follow windows users around and nag the hell out of them..online and in real life.  If you are this person, let me be the first to tell you.  You are annoying and obnoxious and you need to shut your trap.

what i'd really like to see is Novell or RedHat start getting some of their well executed ads (you can find them on their websites.. Novell has like a hundred, redhat has 3) on television.

---

### Post by polo_step on 2006-04-30
[QUOTE=Sheinar]The ones who "bash Windows, bash him and bash everything he said" and say things like "you ignoramous! Go back to your Windows." [/QUOTE]
[FONT="Courier New"]Note that the original blog writer couldn't even *spell* "ignoramus."  :rolleyes: 

That said, I've long felt that the worst thing about Linux was the Linux Cult.  As I've written before, "OS advocacy is best understood as a psychiatric symptom."  Linux creeps are doing no one any good and should seek treatment.  I'm not talking about the people who are doing the good work in programming and development, or even those who take the trouble to learn, critique and debug the distros.  I mean the cranks, missionaries, zealots, snobs, cheerleaders and other head cases who don't understand that Linux is merely an OS and will never be anything more.  They give Linux a very bad name among normal humans.  There are far too many of these people and the rest of us let them get away with far too much.  They should get professional help and scrupulously avoid computers for at least two years. ;) 

I was reading an interesting article the other day about barriers to corporate conversion to Linux and one of the worst problems was "excessive advocacy." This was described as the reluctance to try Linux experimentally because of bad experiences with Linux creeps disrupting the process, being religious about the OS and losing perspective (which they usually don't have to start with).   Their outrageous behavior (some examples were given) cause decision-makers to be reluctant to even mention Linux.  I do not believe this is at all exaggerated, based on my own experience.  

"Advocacy" is for neurotic fanboys who don't have the skills to contribute anything meaningful to the OS's development.

If Linux ever becomes truly market-ready, it will be unstoppable.  In the meantime, the cultists are just scaring off a whole **lot** of people.
[/FONT]

---

### Post by htinn on 2006-04-30
Heh. If Linux ever becomes "market-ready" I will stop using it.

If your ego is so huge that a few "fanboys" can scare you off, you don't deserve the benefit of a friendly, helpful community.

---

### Post by BoyOfDestiny on 2006-04-30
> **polo_step][FONT="Courier New"]Note that the original blog writer couldn't even *spell* "ignoramus."  :rolleyes: 

That said, I've long felt that the worst thing about Linux was the Linux Cult.  As I've written before, "OS advocacy is best understood as a psychiatric symptom."  Linux creeps are doing no one any good and should seek treatment.  I'm not talking about the people who are doing the good work in programming and development, or even those who take the trouble to learn, critique and debug the distros.  I mean the cranks, missionaries, zealots, snobs, cheerleaders and other head cases who don't understand that Linux is merely an OS and will never be anything more.  They give Linux a very bad name among normal humans.  There are far too many of these people and the rest of us let them get away with far too much.  They should get professional help and scrupulously avoid computers for at least two years.  said:**
> 

Linux isn't an OS, it's a kernel. Works with gnu tools etc. Together these form an OS. :P

Free software is a movement, and I think it's valuable.

[http://www.gnu.org/](http://www.gnu.org/)

The main point is to prevent the community from being used as a doormat and benefiting society as a whole. This may not mean much to some people. However, look around, computers are everywhere and in almost everything (embedded). Just for the sake of reliability and interoperability, this [free software] seems the best route to take (IMHO.)

Also, I don't know what "market ready" means. If it means hosting a good chunk of the internet. It's there. It's in corporate offices, in server rooms, in watches, in phones, in portable devices, etc. For some it's on the desktop. There are several hundreds of distros to choose from (see distrowatch.com). Linux doesn't have to be "one thing", and due to its license, someone can always fork it or modify it as they please.

With that said, why not post a link to the article (or where it was published), sources are good.

The real barrier to Linux (desktop?) adoption I'd say varies. If some people turn you off that's fine. You'll encounter fanboys with windows and mac. I don't think that's the main reason for someone to not switch... 
Unless they are snobs themselves... "Oh dear, look at what kind of folks use Linux, let's use Windows instead"

---

### Post by blastus on 2006-05-01
> If most communities surrounding other distros were as friendly as this place is... Linux would be taking off.

I'm not sure these forums are much different than any others. Take the Security Issues and Programming Talk subforums for example. Many people don't post in those subforums anymore because of the eternal trolls that monitor them. There are those who argue over everything to the point of death and think they are doing the community a great favor. They only post to argue with someone just for the sake of arguing and exhibit complete disrespect for anyone that has a different opinion or viewpoint from theirs. 

It is more important to convey a message with respect to another member than it is to be right, but unfortunately there are those on these forums that don't give a damn about respecting other members. I truely wish there was something different about these forums than other communities (i.e the friendliness factor) but from my experience there isn't. They're all the same.

---

### Post by prizrak on 2006-05-02
[QUOTE=blastus]I'm not sure these forums are much different than any others. Take the Security Issues and Programming Talk subforums for example. Many people don't post in those subforums anymore because of the eternal trolls that monitor them. There are those who argue over everything to the point of death and think they are doing the community a great favor. They only post to argue with someone just for the sake of arguing and exhibit complete disrespect for anyone that has a different opinion or viewpoint from theirs. 

It is more important to convey a message with respect to another member than it is to be right, but unfortunately there are those on these forums that don't give a damn about respecting other members. I truely wish there was something different about these forums than other communities (i.e the friendliness factor) but from my experience there isn't. They're all the same.[/QUOTE]
Well you are talking about a highly specialized and very technical forum section. Professionals are prone to being hard headed and that's normal. Look at Linus Torvalds and how he expresses his opinions, he sounds like a real ******* on the mailing lists. But general tech support areas are alot friendlier on this forum than they are on others. You don't get many RTFM's or Google it bitch! here, other Linux distros, forget about it. Hell even in my anime forum (a fairly small and "local" one) any newbies who ask about something that has been answered already get a dose of "use the mofing search dumbass".

---

### Post by stansaraczewski on 2006-05-09
I've had many good experiences on these Ubuntu forums - the people are nice and helpful.

As far as hostility goes, you should see what newbies are like on the MVSHELP forum. (I'm an old mainframer). 

These people demand help immediately, or asap !

---

### Post by TeeAhr1 on 2006-05-09
[QUOTE=polo_step]"Advocacy" is for neurotic fanboys who don't have the skills to contribute anything meaningful to the OS's development.[/QUOTE]
[QUOTE=Destiny]Free software is a movement, and I think it's valuable.[/QUOTE]
I agree with Destiny, and am trying hard not to be offended by polo_step.  I am an advocate.  Of Linux, sure, but first and last, of free software, both because it is technologically superior and because it is a social good.

Yes, GNU/Linux is just an operating system.  But Free Software is a living, breathing, constantly evolving confirmation of the politics and philosophy I've tried to live by all my life.  Not only can We The People do it, we can do it *better*.

---

### Post by Clay85 on 2006-05-09
I find the same thing with competing MMOs. I can't stand WoW; it is phischer price's 'My First MMO' when compared to the graphical beast that is EQ2. But WoW addicts will defend their graphics to the death. (WoW graphics are comparable to EQ1 + lots of purple/pink/green armor/hair/weapons. It's just unrealistic.)

Sorry, I was digressing... See? I hate WoW. I can't help it. Mac users hate everyone else. They just can't help it. (I find mac users to be an odd sort anyway!) But I find myself using mac for some of my art because I just can't do it in another OS. (I use a friend's computer, of course. I wouldn't be caught dead with OS X. ) 

Also, in MMOs, everyone is a complete tetragrammaton because they simply can be. (I was referring to 'four letter word', there. Not God.) I think these 'flamers' are everywhere and anyone. It's easy to make fun of people, lose your temper, et c. on the internet.

Think of an OS as a country. The country is really proud to be that country. (Americans are proud to be American!) I think of MMOs as countries, too. They're just being defensive.

Well I've rambled on long enough. Trying to get my posts up so people won't think I'm a newb! Oh wait... that's impossible. :(

So far I have really enjoyed the Ubuntu community. Very helpful, and I'm very grateful for that.

---

### Post by RavenOfOdin on 2006-05-09
For a long time, Linux has been restricted to techies and IT professionals - which will always remain a large part of its user base, even after it becomes marketable to the other segment of the population. Its understandable that issues of this nature would come about, but I personally am not going to compound the problem. We don't need any more SNL "Computer Guys" being drawn up to illustrate a few idiots that can't treat a new user as someone who simply doesn't know any better and should be handled with kid gloves.

I know we have some of those "idiots" on this forum, but I will not name names.

Just as a job requirement for a Linux professional or tech assistant in any area  is knowledge, there is also one very big one which is . . . *drumroll please* . . .*Dealing with ignorance.*  And no, I don't mean ignorance in the multiculturalist context of the word.  I mean simply not knowing what you're doing with a particular issue.  If you don't know how to do this, if you don't know how to field questions from "John and Jane Q. Public" or from the guy in Management that is trying to get his Windows / Mac / Solaris / etc. to play well with your system, chances are you won't get very far in a work environment - or at least be restricted to a cubicle where you have little or no contact with people.  

Given that above, I can see why the abovesaid idiots can turn an entire organization or business off of Linux and its associated software.

If you wouldn't want a person working for you, would you want him fixing so much as broken package dependencies on your box?

Okay, I'm done rambling now, insert questions etc. where appropriate.
Sorry. :D

---

### Post by mrgumby on 2006-05-09
I dunno...
I like MAC users.
They taste like chicken ;)

:mrgreen:

---

### Post by Clay85 on 2006-05-09
[QUOTE=mrgumby]I dunno...
I like MAC users.
They taste like chicken ;)

:mrgreen:[/QUOTE]

HAHAHA! A few people I know are MAC users. I've never tried eating them. That may solve several problems at the same time... (my hunger and my need to get rid of bad friends.)  :)

---

### Post by fuscia on 2006-05-09
i've never been given a hard time anywhere and i've asked some pretty stupid questions. there are definitely people who are ready to get snippy about things, but in most cases, i think you have to push the right (wrong?) button to get that kind of treatment. the usual scenario: a vet offers his/her highly biased and strongly worded opinion along with whatever help is being given. the recipient sees it as a personal afront, rather than just fee for the service, and the battle is up and running.

---

