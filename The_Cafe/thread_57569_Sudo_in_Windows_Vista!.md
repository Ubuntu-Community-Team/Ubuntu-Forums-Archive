---
title: "Sudo in Windows Vista!"
date: 2005-08-17
forum: The Cafe
---

### Post by Nequeo on 2005-08-17
Thought this was interesting...

[http://www.winsupersite.com/reviews/winvista_beta1_03.asp](http://www.winsupersite.com/reviews/winvista_beta1_03.asp)

> 
Behind the scenes, Windows Vista is running under a vastly reduced privilege level automatically. When the system requires an elevated privilege level, the dialog appears and you provide a password. This password is good only for the action you initiated. Everything else you do--even while the elevated action runs--happens with reduced privileges.


Sound familiar? :)

---

### Post by professor_chaos on 2005-08-17
Ha, figures. Everything else was hacked, why not sudo.

[I]Morpheus: Unfortunately, no one can be told what the Matrix is. You have to see it for yourself.

Morpheus: The Matrix is a system, Neo. That system is our enemy. But when you're inside, you look around, what do you see? Businessmen, teachers, lawyers, carpenters. The very minds of the people we are trying to save. But until we do, these people are still a part of that system and that makes them our enemy. You have to understand, most of these people are not ready to be unplugged. And many of them are so inert, so hopelessly dependent on the system, that they will fight to protect it. [/I]

---

### Post by sapo on 2005-08-17
I m sure that the first thing that most windows users are gonna do is DISABLE this feature cause they are gonna say that the password window is annoying...

And off course that it is gonna have a "disable" button, or maybe when you install windows its gonna ask if you want to enable it or not....

Windows XP has a admin password.. but i never used it.. always left it blank.. why do you think people are gonna use this stuff?

---

### Post by Nequeo on 2005-08-17
I don't. 

You are absolutely right, there will be an 'off' switch. And they probably will turn it off (though rumour is that it **will** be switched on by default). In fact, the article goes so far as to state that the sheer number of windows processes that cause that pop-up box to appear is alarming, and will annoy people.

I just find it amusing that this is reguarded in the MS world as 'innovation'.

---

### Post by drizek on 2005-08-17
the features can be turned off on first boot. you get a dialogue asking you if yo uwant to keep it or not, and the deafult action is no.

---

### Post by poofyhairguy on 2005-08-17
[QUOTE=Nequeo]Thought this was interesting...

[http://www.winsupersite.com/reviews/winvista_beta1_03.asp](http://www.winsupersite.com/reviews/winvista_beta1_03.asp)



Sound familiar? :)[/QUOTE]

Windows programs that need to run as an administrator won't all work with it I bet. Programs will have to be designed for it, and people will just run as an admin anyway.

---

### Post by jerome bettis on 2005-08-17
[IMG]http://common.ziffdavisinternet.com/util_get_image/10/0,1425,sz=1&i=102880,00.jpg[/IMG]

---

### Post by doclivingston on 2005-08-17
The problem is that quite a few windows applications, both free and commercial, won't run if they don't have administrator access. This is due to them doing things they are not supposed to, such as writing to their directory in "Program Files".

The end result is that to use those programs users are going to have to enter the password *every* time they run one of those apps, or just disable it. You can guess which is going to happen.

---

### Post by newbie2 on 2005-08-17
[http://www.ehomeupgrade.com/entry/1182/what_windows_vista](http://www.ehomeupgrade.com/entry/1182/what_windows_vista)

---

### Post by Takis on 2005-08-17
[QUOTE=jerome bettis][IMG]http://common.ziffdavisinternet.com/util_get_image/10/0,1425,sz=1&i=102880,00.jpg[/IMG][/QUOTE]
I don't usually say this but
[CENTER][SIZE=7]OMFG[/SIZE][/CENTER]
Microsoft ought to be SHOT. Then hung, drawn and quartered. Then burnt and its ashes spread to the corners of the Earth. I can't express just how much this has really aggravated me.

---

### Post by Brunellus on 2005-08-17
[QUOTE=Takis]I don't usually say this but
[CENTER][SIZE=7]OMFG[/SIZE][/CENTER]
Microsoft ought to be SHOT. Then hung, drawn and quartered. Then burnt and its ashes spread to the corners of the Earth. I can't express just how much this has really aggravated me.[/QUOTE]
 they're providing the 'windows experience' to their users.

give 'em what they want.

---

### Post by Nequeo on 2005-08-17
I guess Mr Flibble really *is* cross!

The sad thing is, I believe Microsoft has the weight and leverage needed to force 'sudo' or least-privaledged-user, or whatever they call it, on people. Really, they are huge. If they made it non-intuitive to turn off... and they kinda implied, (while tapping a crowbar against their thighs), that developers ought to pay attention to this kind of thing... Well, perhaps things might change for the better a little. 

But that box! *shudder*

Working as an IT consultant, it has become perfectly clear to me that your average computer user *does not look at the screen*. 

Seriously. We had one client who managed to run Microsoft Word 50 times without activating it, and then call us in a panick when it stopped working. That means they clicked 'cancel' 50 times without once stopping to read that box that was popping up on their screen. This is not unusual behaviour. 

Anyway. It's Not My Problem anymore. Sorry for the rant :)

---

### Post by Tiede on 2005-08-17
here is something else intersting...Microsoft is catching on on Unix-like linking.
>  From [ the Part 2 ](http://www.winsupersite.com/reviews/winvista_beta1_02.asp) Virtual Folders don't actually contain anything per se. They're not "real" folders. You can't save a document to the All Documents Virtual Folder, but you can save a document to the Documents folder. Once you've saved that file, however, it will appear in both locations 

---

### Post by Solomon on 2005-08-17
Let's all face the fact. Windows Vista will be a piece of crap just like every other Microsoft product has been. An example of this is on the IE blog. IE7 will support webstandards but will not adhere to them all. They just "dont have time" to make IE support ALL webstandards which I find to be absolutely hilarious. Too many bathroom breaks if you ask me.

This new Sudo like approach... It makes me laugh. Its still part of Windows thus making it useless.

---

### Post by darkmatter on 2005-08-17
[QUOTE=jerome bettis][IMG]http://common.ziffdavisinternet.com/util_get_image/10/0,1425,sz=1&i=102880,00.jpg[/IMG][/QUOTE]

Ha! Talk about defeating the purpose of security.

More of Microsoft's "Don't read, Just click" policy.

---

### Post by Kerberos on 2005-08-17
Looks to me that Microsoft is just trying to fix the 'everyone is root' situation.  This is beta software, not final so any absolute judgements on it are meritless anyway as thats the whole point of a beta isn't it?

Also out of interest does anyone have a better solution that doesn't break backwards compatibility with just about everything?

---

### Post by endy on 2005-08-18
Seems like MS are in a tricky situation, they allowed developers to assume root privilage and now they see the security benifit of changing that. However imagine how many businesses WONT upgrade to vista if they have to re write all their custom apps...

MS should start from the ground up I think, but then why bother they should just use a linux or BSD base and work from there... chances of this happening? :P

I tried to run XP in a limited account and it's almost impossible to get much functionality from it on a day to day basis, not to mention games didn't work :(

---

### Post by WildTangent on 2005-08-18
so, windows will have its own pseudo sudo[SIZE=2]©[/SIZE]....

LOL im sorry, i had to...

[SIZE=1]the term "pseudo sudo" © Justin Hayes 2005[/SIZE]

-Wild

---

### Post by Brunellus on 2005-08-18
[QUOTE=Kerberos]Looks to me that Microsoft is just trying to fix the 'everyone is root' situation.  This is beta software, not final so any absolute judgements on it are meritless anyway as thats the whole point of a beta isn't it?

Also out of interest does anyone have a better solution that doesn't break backwards compatibility with just about everything?[/QUOTE]
 nope.  

And there's the rub:  windows has had this problem from its very inception.  *nix systems were never built this way, and thus never had this problem.

It's just two different ways to run a computer.  Each has its consequences.

---

### Post by weasel fierce on 2005-08-18
Well, its a step in the right direction.

Im rather dubious that this will work, without massive compatibility issues, but its better than what they have done so far

---

### Post by doclivingston on 2005-08-18
[QUOTE=endy]Seems like MS are in a tricky situation, they allowed developers to assume root privilage and now they see the security benifit of changing that.[/QUOTE]

It's not so much that they let developers assume root privileges, it's that with 95/98/ME there was nothing but root privileges.

---

### Post by GreyFox503 on 2005-08-18
I always wondered what the purpose of the 'Administrator' account was on a Windows machine.  I've never had to log into it once for any reason, except out of curiosity.  Have any of you ever had to use it?

---

### Post by WildTangent on 2005-08-18
[QUOTE=GreyFox503]I always wondered what the purpose of the 'Administrator' account was on a Windows machine.  I've never had to log into it once for any reason, except out of curiosity.  Have any of you ever had to use it?[/QUOTE]
nope. i can do anything the administrator account can do from the comfort of my own account :P oh wait...i do recall one time when i used it. this was before i had my own computer, my parents grounded me from the computer, and put passwords on all the accounts. but the administrator account doesnt show in the user control panel, and it didnt have a password by default. a simple double tap of ctrl+alt+del at the welcome screen, with no one else logged in gives you the classic login prompt, so i logged into admin to catch up on my emails :P

-Wild

---

### Post by drizek on 2005-08-18
[QUOTE=GreyFox503]I always wondered what the purpose of the 'Administrator' account was on a Windows machine.  I've never had to log into it once for any reason, except out of curiosity.  Have any of you ever had to use it?[/QUOTE]
 AFAIK, its for when you **** up your normal account and you need admin privelages to make a new one.

also used in safe mode.

---

### Post by nrayever on 2005-08-18
nice try for M$ for trying to copy sudo function. but as was told in this thread: must winbugs users don't even read what's about the warning window. the common winbugs user just clicks on ok, and they don 't even know what they r really doing. sure must of "us" as an old M$ users did that. do u think that know is really going to change now with vista????

M$ is giving u more possibilities to f&%# up your pc, but with "pseudo sudo" privileges. so know ur really going to blow up your pc!! as a dummy "super-user!!!" NICE!!! :grin:  :grin:  :grin:

> "pseudo-sudo" was copyrighted by WildTangent, And maybe later will be patented by WildTangent....... only if M$ haven't try it first!!!  :grin:  :grin:  :grin: 

---

### Post by WildTangent on 2005-08-18
[QUOTE=nrayever]M$ is giving u more possibilities to f&%# up your pc, but with _**"pseudo sudo"**_ privileges. so know ur really going to blow up your pc!! as a dummy "super-user!!!" NICE!!! :grin:  :grin:  :grin:[/QUOTE]
 you must not have read the fine print, ive copyrighted that term ;)

-Wild

---

### Post by Takis on 2005-08-18
[QUOTE=GreyFox503]I always wondered what the purpose of the 'Administrator' account was on a Windows machine.  I've never had to log into it once for any reason, except out of curiosity.  Have any of you ever had to use it?[/QUOTE]
Just one of those built in things. If it really annoys you, just go in and delete it- oh, wait, it's Windows. You can't do what you want to do because Microsoft Knows Best.

Silly Takis.

---

### Post by endy on 2005-08-18
I'm surprised so many people find running XP on a limited non admin account works so well. I gave up on XP after I couldn't play Doom3 without logging in as admin :(

Root access just to *play a game*? Not my idea of a good OS.

---

### Post by WildTangent on 2005-08-18
[QUOTE=endy]I'm surprised so many people find running XP on a limited non admin account works so well. I gave up on XP after I couldn't play Doom3 without logging in as admin :(

Root access just to *play a game*? Not my idea of a good OS.[/QUOTE]
i think you misunderstand. as far as i can see, there have not been any positive comments about the limited account. for myself personally, all my accounts on my various windows computers are admin accounts. not the super-user accounts you normally create when you make a new account and set it to admin. may be dangerous...but im very diligent when it comes to security, and i havent had a virus in over a year. then, i do run windows server 2003 on my main box, and use its highly customizeable user permissions...so i suppose that helps alot

-Wild

---

### Post by Takis on 2005-08-18
[QUOTE=endy]I'm surprised so many people find running XP on a limited non admin account works so well.[/QUOTE]
WildTangent's right, I think we're all talking about the built-in administrative account 'Administrator' (like how there's a built-in 'Guest' account), as opposed to an account 'bob' which has administrative rights.

Back on topic:
[SIZE=6]What on earth is the point of a new security feature if the very first option you're given is to turn the thing off?[/SIZE]
ARGH Windows has really gone and done exceptionally stupid. Why don't they open up all ports while they're at it?  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by GreyFox503 on 2005-08-18
[QUOTE=Takis]Just one of those built in things. If it really annoys you, just go in and delete it- oh, wait, it's Windows. You can't do what you want to do because _Microsoft Knows Best_.[/QUOTE]

I felt a shiver when I read that.... kinda disturbing.

I forgot to add that I don't have Windows installed now, so it doesn't bother me anymore.  :-P

---

### Post by darkmatter on 2005-08-18
[QUOTE=Takis]Why don't they open up all ports while they're at it?  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

Because most the ports are already open by default? :-P

---

### Post by endy on 2005-08-18
RE: WildTangent & Takis

Ok, I see what you mean now but my point still stands - you have to run an admin level account to get work done. If that were the same in linux I guess it would be like running everything with sudo infront.

Sorry to go on and on but this is my main gripe about windows, the rest I think I can almost deal with :)

---

### Post by benplaut on 2005-08-19
[QUOTE=Takis]all ports while they're at it?  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

what's the point? they're already open!

<<edit>>

woops... redundant

---

### Post by nrayever on 2005-08-19
[QUOTE=WildTangent]you must not have read the fine print, ive copyrighted that term ;)

-Wild[/QUOTE]

ok i have make some changes to my reply, i hope u like it!!!  :grin:  :grin:

---

### Post by nrayever on 2005-08-19
[QUOTE=darkmatter]Because most the ports are already open by default? :-P[/QUOTE]

nice answer!!, sad fo must winbugs users, but true!! linux rocks!!

---

### Post by poofyhairguy on 2005-08-19
[QUOTE=endy]

Sorry to go on and on but this is my main gripe about windows, the rest I think I can almost deal with :)[/QUOTE]

I agree. If this works it would be great. But I really don't believe this can be done without breaking a  lot of old apps. And if only new apps can use it, whats the point?

---

