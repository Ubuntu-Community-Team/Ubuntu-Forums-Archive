---
title: "Things absolute beginners should NOT do:"
date: 2008-03-07
forum: The Cafe
---

### Post by Oldsoldier2003 on 2008-03-07
Things absolute beginners should NOT do:
This list is not all inclusive and is aimed at helping beginners. So of the advice here can be completely ignored by intermediate and advanced users. But hey if you are one of those you don't NEED the advice!
[LIST]
[*]**never use automatix**. Regardless of what you may have heard, automatix is a bad idea. The program has a high likelihood of trashing your system to the point that the only fix is a reinstall

[*]**never run scripts or commands you don't understand**. Although the people here on the forum are very helpful, you should never ever run a command you don't understand. When in doubt use man <command> or google the term. If you still don't understand post here and someone can help clarify it to you. example:** NEVER run sudo rm -rf / **

[*]**never install software from unknown or untrusted sources**. At first stick to the default Ubuntu repositories. If you need something specific that isn't available, be careful of where you get it. remember that not everything you find out there is stable on all operating system versions and some is just plainly malicious.
[**]corollary:never use source code from untrusted sources. 

[*]**never run makefs on a partition you need**. makefs will reformat that partition, destroying the exiting data. Never do it without first being absolutely sure you want to wipe the data and create a new blank partition.

[*]**don't enable root**. if you need to enable the root account, then you are not an absolute beginner. The forums do not support doing this for a bunch of reasons... read the sticky and you'll see why.

[*]**don't move your /home directory to a ntfs partition**. it breaks logins. Noted here because although moving /home to another drive or partition isn't exactly a beginner task, many people will consider it.

[*]**don't change your repositories to a newer version of Ubuntu**. this isn't the proper way to upgrade your installation, and could overwrite critical packages, placing your OS in a unstable state. 

[*]**don't pm the mods for a tech issue**. if you do that, you lessen the number of people that will see your issue, thus lessening your chance for a quick and helpful resolution. (besides it's just pretentious)

[*]**don't be afraid to ask questions**. If you are here, then you've found the best resource for friendly advice given by people that have "been there". Take a few moments to think through the issue and post it as clearly and concisely as you can. If you include all the pertinent info, the chances of resolving your problem are a lot higher.
[/LIST]

---

### Post by zeller on 2008-03-07
Good to know. Thanks for the wonderful post!

---

### Post by Vadi on 2008-03-07
That's really helpful, but I don't think absolute beginners will be able to understand the jargon used there.

---

### Post by Dr Small on 2008-03-07
Also:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
[http://kmandla.wordpress.com/2008/03/06/common-newb-mistakes-and-how-to-avoid-them/](http://kmandla.wordpress.com/2008/03/06/common-newb-mistakes-and-how-to-avoid-them/)

---

### Post by Ripfox on 2008-03-07
I liked Automatix...it worked good and never trashed my system once.

You just have to be smart enough to use it directly AFTER a fresh install.

---

### Post by Duck2006 on 2008-03-07
> never run scripts or commands you don't understand. 

How do you know if you don't give it a go?

This is just like running the DD commands, witch are not for beginners but if you don't try how do you learn?

---

### Post by Oldsoldier2003 on 2008-03-07
> **Duck2006 said:**
> How do you know if you don't give it a go?

This is just like running the DD commands, witch are not for beginners but if you don't try how do you learn?
*grins*
explain that to the windows user that just wiped out his entire digital life because he decided to dual boot to Ubuntu and did something to "learn linux"  I'm all ofr giving it a go, but you have to rememebr that not everyone that posts here is as adventurous, and many may not understand the ramifications of their actions, or have a clue on how to recover their data form a backup (if they even have backups).

---

### Post by Ripfox on 2008-03-07
> **Duck2006 said:**
> How do you know if you don't give it a go?

This is just like running the DD commands, witch are not for beginners but if you don't try how do you learn?

For some reason certain people like to tell other people what they "should do"

Personally I think learning by experience is the best teacher available. Yea, I trashed my system a few times to say the least. But thats the way it goes. I see why telling people not to use certain commands blindly is beneficial, but imho you should just make sure you back up your important files and jump right in, it's the best way to learn.

---

### Post by fuscia on 2008-03-07
**never** take one person's strongly voiced cautions seriously.

---

### Post by SomeGuyDude on 2008-03-07
I found Automatix convenient, actually. Never broke anything. My only beef with it is that they still have the old version of Swiftweasel packed.

---

### Post by jrusso2 on 2008-03-07
Don't try to upgrade glibc

---

### Post by herbster on 2008-03-07
**Don't** go outside without a helmet.

---

### Post by beercz on 2008-03-07
Forget to backup

---

### Post by amyst on 2008-03-07
Question 1: 
"don't pm the mods for a tech issue" 

What is "pm the mods" ?

Question 2: 
Say, I want to ask for help for printing to  a network printer, would the topic / title

"Printing to the network printers only print the first 2 pages"  

be enough or do I need to add something else to it?

---

### Post by Iehova on 2008-03-07
> **amyst8 said:**
> Question 1: 
"don't pm the mods for a tech issue" 

What is "pm the mods" ?

Sending a Private Message to the Forum Moderators. :)


> Question 2: 
Say, I want to ask for help for printing to  a network printer, would the topic / title

"Printing to the network printers only print the first 2 pages"  

be enough or do I need to add something else to it?

That should be fine...

---

### Post by SomeGuyDude on 2008-03-07
> **amyst8 said:**
> Question 1: 
"Printing to the network printers only print the first 2 pages"  

be enough or do I need to add something else to it?

That would be plenty. It's enough information for someone scanning to know if they're having a similar problem or if it's of a subject they can help with.

Far better than, say, "PRINTING HELP!!!"

---

### Post by darth_indy on 2008-03-07
> **SomeGuyDude said:**
> Far better than, say, "PRINTING HELP!!!"

Agreed! Or, worse, the topics that have the title "PLEASE HELP" or simply "HELP". The best way to get help is to explain the problem as well as possible in a short sentence. For example, the aforementioned "Printing to the network printers only print the first 2 pages" is excellent, or a description like "Problems with Dell [model #]wireless printer and Dell 1420n" to let people know your specific problem. This not only makes it easier for those that are knowledgable to find your problem and help you, but chances are that someone else will have the same problem, and will search the forums. If your title is good, it will help others a lot. I don't know how many times I've tried to fix a problem on the forums, and not find a fix until I waded through "PLZ HELP!1!" topics.

---

### Post by amyst on 2008-03-07
Thanks, you guys are awesome :)

---

### Post by glenboarder99 on 2008-03-10
Thanks for telling me.

---

### Post by perce on 2008-03-11
> **jrusso2 said:**
> Don't try to upgrade glibc

I did, many years ago :oops:

---

### Post by hhhhhx on 2008-03-11
automatix should be fine if you install it right after an installation, but if you do it later it apparently can cause dependency issues

---

### Post by steveneddy on 2008-03-11
I wish a list like this was the first thing that was on the Absolute Beginners section of these forums.

How many times in** one weekend** do we see the same question being posed by every noobie out there.

Someone teach them to search the forums and Google.

I hate to say it, b/c I'm not an RTFM guy myself most of the time, but please read the "Read Me" file or the help file at least once.

There you go. My .02

You are **very** welcome.

---

### Post by SomeGuyDude on 2008-03-11
I'm definitly not a RTFM or JFGI kind of fella, but there definitely is a list of things that people should spend about 5 minutes looking up before bringing to the table.

Hell, searching is usually faster than waiting for someone to respond, anyway. The greatest tool on this forum is to open a new topic, type your question in the title box, and then see what it spits back at you. I've answered SO many questions that way.

---

### Post by kevdog on 2008-03-11
Jfgi ??

---

### Post by chewearn on 2008-03-11
> **kevdog said:**
> Jfgi ??

Oh... the irony. [JFGI]("http://www.fuckinggoogleit.com/")

EDIT:
And yes, I did google it too. :redface::lolflag:

---

### Post by Trail on 2008-03-11
Concerning not enabling the root account... I got a question for that (and sorry, not gonna search the forums at this time :P).

What if there is an electricity blackout, your / is not unmounted cleanly, and fsck asks tries to remount read-only and asks for the root passwd for maintenance. What can you do if you DON'T have one set?

I got a friend for which I installed ubuntu recently, and I SMSed him the instructions to do so just in case.

---

### Post by Trail on 2008-03-14
bump

---

### Post by n3tfury on 2008-03-14
also, don't wipe your partition with Windows unless it's already hosed beyond belief.

---

### Post by vbt on 2008-03-14
> **SomeGuyDude said:**
> 
Hell, searching is usually faster than waiting for someone to respond, anyway. The greatest tool on this forum is to open a new topic, type your question in the title box, and then see what it spits back at you. I've answered SO many questions that way.

That's how I learned, by coming to this forum.  After a week of dual boot, buh bye Windows. I don't think I ever had a problem that was not already solved by someone here.   

:guitar:

Good list of don'ts.  I agree, it should be posted in the absolute beginner section.

---

