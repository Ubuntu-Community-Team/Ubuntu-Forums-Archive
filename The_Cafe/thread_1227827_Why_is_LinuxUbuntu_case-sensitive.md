---
title: "Why is Linux/Ubuntu case-sensitive?"
date: 2009-07-31
forum: The Cafe
---

### Post by Jeinhor on 2009-07-31
I'm just curious why Ubuntu and Linux in general is case-sensitive? I can see a very good reason for having a case-insensitive file system though: less confusion!

---

### Post by dmizer on 2009-07-31
Actually, having a case sensitive file system creates less confusion. You're only confused with a case sensitive file system because you're used to a case non-sensitive file system.

---

### Post by wojox on 2009-07-31
Linux is written in C, which is case sensitive. It makes for faster sorting.

---

### Post by hellmet on 2009-07-31
Counter question : Why is Windows not case-sensitive?
Users of Linux/Unix really appreciate the value of case-sensitiveness. 
I myself feel very irritated by MS Windows treatment of file/network/user names (and more)

---

### Post by ssam on 2009-07-31
because its the simple way to do it. on computers letters are represented by numbers using an encoding like ascii or unicode. in ascii 'a' is 97 and 'A' is 65.

when you ask is 'Sam' the same string as 'sam', the computer sees three numbers, and check that numbers are all equal. does not need to know anything about the actual letters.

to do a case insensitive compare you need to convert both strings to lowercase, and then do the compare. so now you need a big table of equivalents. this is a fairly small task for the old ascii character set as it only has 128 characters, and you can convert to lower case by adding 32 to all the characters within a certain range.

Unicode which is now used modern operating systems has millions of characters from every language on earth (and some from elsewhere eg middle earth). some languages don't even have a concept of upper and lower case.

this does not make it impossible, but its a big task, and probably not worth the benefit in many places.

---

### Post by hetx on 2009-07-31
The computers like it this way, who are we to disagree!?

---

### Post by JohnFH on 2009-07-31
Linux/Ubuntu is case-sensitive because the file-system they use is case-senitive.  There's a great Wiki article comparing the different file-systems here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems").

Personally I much prefer case-sensitivity.  Gives me a lot more control over the naming of files.

---

### Post by Sporkman on 2009-07-31
More secure passwords, too.

---

### Post by stinger30au on 2009-07-31
just cos

---

### Post by JohnFH on 2009-07-31
> **Sporkman said:**
> More secure passwords, too.

Yep, cos Windows doesn't support that either.  Oh hang on ...

---

### Post by Sublime Porte on 2009-07-31
Unix has case sensitive file system to confuse non-initiates and filter them out from joining the ranks of elite users.

---

### Post by Jeinhor on 2009-07-31
> **dmizer said:**
> Actually, having a case sensitive file system creates less confusion. You're only confused with a case sensitive file system because you're used to a case non-sensitive file system.

I have actually used both Linux and Windows and know my way around both. However, I do admit I've spent more time on Windows.

If "newbie-John" creates a file called MyFile.txt, I am sure it would be less confusing for him to be able to access that file with /a/path/to/myfile.txt as well! For example, think of all the places where you specify configuration files, just a simple mistake with the casing there can make a lot go wrong.

I would say it's more natural with case-insensitivity.

> **wojox said:**
> Linux is written in C, which is case sensitive. It makes for faster sorting.

Does this really matter that much? Is Windows that much slower when it comes to sorting? It could be true, but I find it odd if that's the reason as it obviously works quite well on Windows.

> **ssam said:**
> because its the simple way to do it. on computers letters are represented by numbers using an encoding like ascii or unicode. in ascii 'a' is 97 and 'A' is 65.

when you ask is 'Sam' the same string as 'sam', the computer sees three numbers, and check that numbers are all equal. does not need to know anything about the actual letters.

to do a case insensitive compare you need to convert both strings to lowercase, and then do the compare. so now you need a big table of equivalents. this is a fairly small task for the old ascii character set as it only has 128 characters, and you can convert to lower case by adding 32 to all the characters within a certain range.

Unicode which is now used modern operating systems has millions of characters from every language on earth (and some from elsewhere eg middle earth). some languages don't even have a concept of upper and lower case.

this does not make it impossible, but its a big task, and probably not worth the benefit in many places.

Yeah, that might be it. Too much trouble for a relativly small gain. That I could understand. But maybe someone should step up and do the work soon, before it really gets impossible to do?

> **hellmet said:**
> Counter question : Why is Windows not case-sensitive?
Users of Linux/Unix really appreciate the value of case-sensitiveness. 
I myself feel very irritated by MS Windows treatment of file/network/user names (and more)

I can't see when I would actually benefit from having a case-sensitive file system. When do I actually need to create two different files named myfile/MyFile/Myfile etc? Why would I need two (or more) users with the name John?

> **hetx said:**
> The computers like it this way, who are we to disagree!?

True, we are merely small worms in the shadow of the mighty computers! Behold! ;)

> **JohnFH said:**
> Linux/Ubuntu is case-sensitive because the file-system they use is case-senitive.  There's a great Wiki article comparing the different file-systems here: [http://en.wikipedia.org/wiki/Comparison_of_file_systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems").

Personally I much prefer case-sensitivity.  Gives me a lot more control over the naming of files.

I understand it's because the file system is case-sensitive, but why is the file system case-sensitive? Could you give an example where you use it?

---

### Post by Jeinhor on 2009-07-31
> **Sublime Porte said:**
> Unix has case sensitive file system to confuse non-initiates and filter them out from joining the ranks of elite users.

I'm sure that attitude will make Linux and Ubuntu conquer the world! We really need to focus on what DEVELOPERS and advanced users wants, not what AVERAGE-JOE wants! :roll: ;)

---

### Post by Mornedhel on 2009-07-31
> **Jeinhor said:**
> I'm sure that attitude will make Linux and Ubuntu conquer the world! We really need to focus on what DEVELOPERS and advanced users wants, not what AVERAGE-JOE wants! :roll: ;)

Yeah, we do, actually. So that Linux can be a more attractive platform for third-party closed source developers, among other things. Which will attract more Average Joes once the mainstream apps are ported, if they ever are.

---

### Post by Keyper7 on 2009-07-31
Case-insensitivity only makes sense if you are associating file names with complete dictionary words or real-world names, which is not always the case. They can be acronyms, abbreviations or whatever the user wants them to be.

Why would I want the file "expo.txt", my review about a certain exposition, to be considered the same as file "expO.txt", the results of Experiment O? And that's not even considering they are in the same directory: it also affects searches.

Sure, I can circunvent this with "exp_o.txt" and a case-sensivity parameter in my search application, but the point is: in a world where file names can be everything, not just dictionary words or real-world names, case-sensivity by default is a more intuitive choice.

Whenever I use Windows and Mac OSX, I feel *very* unconfortable knowing that what I type is not necessarily what the system reads.

---

### Post by pmlxuser on 2009-07-31
well because you can then create vitually lots of files with similar sounding name

name, Name,nAme,naMe,namE,NAME,NAMe, etc. if it was not case senstixe you could only get 1 (damn)

---

### Post by superdan006 on 2009-07-31
> **Jeinhor said:**
> 
I understand it's because the file system is case-sensitive, but why is the file system case-sensitive? Could you give an example where you use it?

It's not the filesystem, it is UNIX. Historically, case-sensitivity has been the norm for not just naming files, but commands (ls isn't the same as LS) more importantly. 

I appreciate that. Take for instance the VI editor. Using the editor isn't limited if you can use different cases to do different commands (r can replace one character, R can replace until you exit that mode).

Hope that helps...

---

### Post by RiceMonster on 2009-07-31
To quote one of my teachers: "Why would you want to leave out 26 other possibilites?"

> **Jeinhor said:**
> I'm sure that attitude will make Linux and Ubuntu conquer the world! We really need to focus on what DEVELOPERS and advanced users wants, not what AVERAGE-JOE wants! :roll: ;)

Why should Linux "conquer the world" in the first place?

---

### Post by dmizer on 2009-07-31
> **Jeinhor said:**
> I have actually used both Linux and Windows and know my way around both. However, I do admit I've spent more time on Windows.

If "newbie-John" creates a file called MyFile.txt, I am sure it would be less confusing for him to be able to access that file with /a/path/to/myfile.txt as well! For example, think of all the places where you specify configuration files, just a simple mistake with the casing there can make a lot go wrong.

I would say it's more natural with case-insensitivity.
I guess we'll just have to disagree then. I think it's much much more natural because often times, the meaning of a word changes depending on case. For example:

Windows = a operating system
windows = (pl) an opening in the wall of a building, the side of a vehicle, etc., for the admission of air or light, or both, commonly fitted with a frame in which are set movable sashes containing panes of glass.

This is why I said that it creates less confusion and makes more sense to have a case sensitive file system. That is only one example, and it's in English. There are many many more examples in English as well as a host of other languages.

Actually, not much can go wrong if you make a mistake in case. A user may become frustrated because the file they are looking for doesn't appear to exist, but once the user understands that the system is case sensitive, it doesn't cause a problem anymore. Though I can see where it would be a problem for users who frequently switch between Linux and Windows.

The experience is identical to users who don't know that a password is case sensitive, and that's becoming more and more prevalent even in Windows.

---

### Post by [h2o] on 2009-07-31
> **Jeinhor said:**
> Does this really matter that much? Is Windows that much slower when it comes to sorting? It could be true, but I find it odd if that's the reason as it obviously works quite well on Windows.
Ubuntu sorts file with respect to case insensitivity as well.
If you name two files the same thing, but one uppercased they will end up next to each other if you run "ls" and in Nautilus as well.

---

### Post by aysiu on 2009-07-31
Eh.

I don't really care either way.

On a daily basis I use Windows XP, Mac OS X Leopard, and Ubuntu 9.04.

On a weekly or biweekly basis, I use the terminal in all three of them.

I've never been bothered by case-sensitivity or case-insensitivity. I just go with the flow.

---

### Post by decoherence on 2009-07-31
I believe the original reason for case sensitivity was that a case insensitive system was considered a waste of perfectly good distinct characters.

Don't ask me where I heard that... I think it was the UNIX System User's Guide, years ago. I could be dreaming, though...

Also, remember that these rules (whatever the reason for them) are historical and likely rooted in the fact that the systems of the time had very, very few resources (this, for instance, is why we have 'ls' and not 'list' -- that much i know!) So when we talk about sorting and such, it might not be a big deal now but it was then, and it's a difficult convention to break (OS X had to do some very ugly hacks in the early days. Not sure how they handle it now)

---

### Post by Jeinhor on 2009-08-01
> **pmlxuser said:**
> well because you can then create vitually lots of files with similar sounding name

name, Name,nAme,naMe,namE,NAME,NAMe, etc. if it was not case senstixe you could only get 1 (damn)

Yes, that's exactly what I imagine could be confusing.

> **superdan006 said:**
> It's not the filesystem, it is UNIX. Historically, case-sensitivity has been the norm for not just naming files, but commands (ls isn't the same as LS) more importantly. 

I appreciate that. Take for instance the VI editor. Using the editor isn't limited if you can use different cases to do different commands (r can replace one character, R can replace until you exit that mode).

Hope that helps...

I agree it might be useful in some places, but wouldn't it be better to enable it when needed? For example, in the VI editor? Would it be so terrible if the editor started if I wrote Vi/vI/VI as well?

> **RiceMonster said:**
> To quote one of my teachers: "Why would you want to leave out 26 other possibilites?"

Why should Linux "conquer the world" in the first place?

I can answer that: "To keep the system intuitive and simple for end-users". The problem isn't exactly we're running out of unique file names...

Because the Ubuntu/open source concept is a good thing!

> **dmizer said:**
> I guess we'll just have to disagree then. I think it's much much more natural because often times, the meaning of a word changes depending on case. For example:

Windows = a operating system
windows = (pl) an opening in the wall of a building, the side of a vehicle, etc., for the admission of air or light, or both, commonly fitted with a frame in which are set movable sashes containing panes of glass.

This is why I said that it creates less confusion and makes more sense to have a case sensitive file system. That is only one example, and it's in English. There are many many more examples in English as well as a host of other languages.

Actually, not much can go wrong if you make a mistake in case. A user may become frustrated because the file they are looking for doesn't appear to exist, but once the user understands that the system is case sensitive, it doesn't cause a problem anymore. Though I can see where it would be a problem for users who frequently switch between Linux and Windows.

The experience is identical to users who don't know that a password is case sensitive, and that's becoming more and more prevalent even in Windows.

Well, that kind of makes sense. But me being able to tell Windows apart from windows in a file name seems to me a trivial gain for a lot of pain. This is the best argument I've heard for a case-sensitive file system though, but I think it should be up for discussion if it's heavy enough...

> **decoherence said:**
> I believe the original reason for case sensitivity was that a case insensitive system was considered a waste of perfectly good distinct characters.

Don't ask me where I heard that... I think it was the UNIX System User's Guide, years ago. I could be dreaming, though...

Also, remember that these rules (whatever the reason for them) are historical and likely rooted in the fact that the systems of the time had very, very few resources (this, for instance, is why we have 'ls' and not 'list' -- that much i know!) So when we talk about sorting and such, it might not be a big deal now but it was then, and it's a difficult convention to break (OS X had to do some very ugly hacks in the early days. Not sure how they handle it now)

Yea, I can understand that. But perhaps it's time for a change? We're not living in the 80's anymore...

> **aysiu said:**
> Eh.

I don't really care either way.

On a daily basis I use Windows XP, Mac OS X Leopard, and Ubuntu 9.04.

On a weekly or biweekly basis, I use the terminal in all three of them.

I've never been bothered by case-sensitivity or case-insensitivity. I just go with the flow.

Perhaps you haven't, as you're probably a advanced user compared to average-Joes - and those average users are important for Ubuntu to attract!

---

### Post by stuart.reinke on 2009-08-01
It's been stated several times that the case sensivity is because of the file system.

 Question, if you access a NTFS or FAT32 file system with Linux is it still case sensitive or does it apply only to Linux file systems.

Hope I didn't just ask an incredibally dumb question. :D

---

### Post by blueturtl on 2009-08-01
> It's been stated several times that the case sensivity is because of the file system.

Question, if you access a NTFS or FAT32 file system with Linux is it still case sensitive or does it apply only to Linux file systems.

Hope I didn't just ask an incredibally dumb question. :D

At least in the case of FAT32, you need to mount the file system with the proper codepage and chacter set. Otherwise the system will be case sensitive and while it may work for Linux, Windows will surely freak out.

> I can answer that: "To keep the system intuitive and simple for end-users". The problem isn't exactly we're running out of unique file names...

Have you considered the fact that operating system design also enforces  computing habits? 
If you learn to use a regular account instead of a root account, it is better in the long run even though constantly running as root is very convenient.

If your operating system or applications indicate you can issue them commands or file names that are "close enough" won't that cause terrible trouble later?

It is the nature of the computer to be precise. You can try to disguise the case-sensitive and very exact nature of a computer, but it is only a mask, and people who give their computers inaccurate instructions are the ones that get into trouble.

Ever heard of the expression: "Computers make very fast, very accurate mistakes"?

I would consider having to unlearn case-insensitive names hard, but not learning to use case-sensitive names. Also learning case-sensitivity from the beginning is much more rewarding in the long run.

I say we shouldn't treat newcomers as if they are stupid. Case-sensitivity isn't a very complex thing to understand, all that we need to really do is make sure that new users know that their systems are this way!

---

### Post by CaseSensative on 2009-08-01
linux and Linux can be read two different ways by your computer.

---

### Post by lisati on 2009-08-01
We should be thankful that we have a choice. On the first programming course I attended, I had no choice and had to use uppercase - possibly due in part to compatibility with something called "punched cards".

---

### Post by dmizer on 2009-08-01
> **Jeinhor said:**
> But me being able to tell Windows apart from windows in a file name seems to me a trivial gain for a lot of pain. This is the best argument I've heard for a case-sensitive file system though, but I think it should be up for discussion if it's heavy enough...

Well, I didn't say it wasn't trivial. You just indicated that you thought it was more natural to have a non case sensitive file system, so I was only trying to explain why I thought it was more natural (linguistically speaking) to have a case sensitive file system. Obviously there are good arguments both ways, not the least of which is interoperability between platforms.

---

### Post by zacktu on 2009-08-01
Linux is case sensitive because it's showing its UNIX roots.

Windows is case-insensitive because it's showing its DOS roots.

---

### Post by The Cog on 2009-08-01
Out of curiosity, which of these three files do you think should be allowed to exist together in the same directory of the filesystem?

1: A&#915;&#948;&#950;&#951;&#924;&#957;&#963;&#933;&#969;
2: &#913;&#915;&#948;&#950;&#951;&#924;&#957;&#963;&#933;&#969;
3: &#945;&#947;&#916;&#918;&#919;&#956;&#925;&#931;&#965;&#937;

Linux allows all three:
>  ls -l
total 12
-rw-r--r-- 1 steve steve 208 2009-08-01 15:55 A&#915;&#948;&#950;&#951;&#924;&#957;&#963;&#933;&#969;
-rw-r--r-- 1 steve steve 140 2009-08-01 15:55 &#913;&#915;&#948;&#950;&#951;&#924;&#957;&#963;&#933;&#969;
-rw-r--r-- 1 steve steve  73 2009-08-01 15:55 &#945;&#947;&#916;&#918;&#919;&#956;&#925;&#931;&#965;&#937;

I was able to copy them to a FAT filesystem too on a USB stick. Copying them to XP copied the first two, then complained that &#945;&#947;&#916;&#918;&#919;&#956;&#925;&#931;&#965;&#937; already existed.

---

### Post by aysiu on 2009-08-01
> **Jeinhor said:**
> Perhaps you haven't, as you're probably a advanced user compared to average-Joes - and those average users are important for Ubuntu to attract! Can you explain how case sensitivity would affect "average users"? They can name their files however they want to name their files.

---

### Post by Keyper7 on 2009-08-01
> **Jeinhor said:**
> I can answer that: "To keep the system intuitive and simple for end-users".

Except that this is completely subjective and depends on the user.

I, for example, consider case-insensivity to be less user-friendly. If I'm typing something, I want the system to read exactly what I'm typing.

There's no right or wrong in this matter. It's like the default colors or the default fonts: some people like it, some people don't.

---

### Post by SuperSonic4 on 2009-08-01
If average Joe cannot tell the difference between Name and name - even with tab completion - then average Joe can bugger off, Linux is better off without them

---

### Post by sydbat on 2009-08-01
> **hetx said:**
> **Our** computer **overlords** like it this way, who are we to disagree!?There...fixed it for you...:P

---

### Post by RD1 on 2009-08-01
Because Ubuntu/Linux has been to sensitivity training.

---

### Post by MaxIBoy on 2009-08-01
> **Jeinhor said:**
> I'm sure that attitude will make Linux and Ubuntu conquer the world! We really need to focus on what DEVELOPERS and advanced users wants, not what AVERAGE-JOE wants! :roll: ;)Yup.


Linux started out as one programmer "scratching an itch." He wanted a Unix-like environment at home so he could do his homework without going to the university computer lab, but he also didn't want to shell out gobs of money for a high-end Unix workstation. So he wrote Linux. Other people needed more features for their own personal use, and so they wrote modifications for Linux and submitted them. Oh, and by the way, millions of other people, by coincidence, found their work to be useful as well.


Open-source development works because the developers are motivated to create something which will be useful to *them*. And you know what? I trust the developers' judgment (or if I disagree I might program my own version!) Developers are smart people, they know exactly why they made the choices they did.


I would humbly submit that you should become well-versed in a given software before you start suggesting changes. After all, you wouldn't try to change the design of a car if you didn't at least know how to drive it and do basic maintenance. And no, I'm not suggesting that you need to know the inner workings of the code, although that helps too. But you need to know how to USE it and you need to know why each feature is useful or not-useful.


If everyone listened to what the "average Joe" wants, there'd be no passwords on anything, no "are you sure" dialogs when you install stuff, no signed public keys on secure websites, and as a result there would be no security whatsoever on ANYTHING. If everyone listened to what the "average Joe" wants, we'd all be using the [Macbook Wheel](http://www.theonion.com/content/video/apple_introduces_revolutionary). And that would suck.

---

### Post by swoll1980 on 2009-08-01
Someone pointed this out I'm sure, but I'm not going to read the whole thread. Internet != internet That's case sensitivity is a good thing, and why I like it. Just in case it wasn't mentioned.

---

### Post by lswb on 2009-08-01
Linux has its roots in unix and unix was always a case sensitive OS. After all, they are different characters. Making it case insensitive would actually require additional code in the OS, so why bother?

OTOH, early versions of DOS were influenced by CP/M systems. These old 8 bit systems used a simpler, cheaper keyboard that only had uppercase letters, there was no lower case. A company named Seattle Computer Products devolped an early OS for the 8086/88 processor and called it QDOS; it copied many features from CP/M, including some of the internal APIs and system calls. (QDOS is alleged to be the acronym for Quick and Dirty Operating System)

When IBM contracted with Microsoft to supply an OS for the original IBM PC, MS purchased QDOS from SCP and used it as the basis of DOS. It was (likely) easier to add simple code to uppercase any string passed to parts of the OS based on the original QDOS, than to go through the entire QDOS code base and ensure it could handle lower case. (It was written in assembly, after all)

So there you have it, like so many details of modern technology, there was no grand design, no well-thought-out logic, just simple chance and history.

---

### Post by chris200x9 on 2009-08-01
because it's better that way...

---

### Post by lisati on 2009-08-01
> **MaxIBoy said:**
> Yup.


Linux started out as one programmer "scratching an itch." He wanted a Unix-like environment at home so he could do his homework without going to the university computer lab, but he also didn't want to shell out gobs of money for a high-end Unix workstation. So he wrote Linux. Other people needed more features for their own personal use, and so they wrote modifications for Linux and submitted them. Oh, and by the way, millions of other people, by coincidence, found their work to be useful as well.



Nicely said.

---

### Post by ad_267 on 2009-08-01
Average users aren't going to be accessing their files and issuing commands through the terminal, they're only going to use graphical file managers to point and click to get to their files. In that case, why does it matter?

For users who actually enter file paths and use the terminal I'd say it's less confusing having case-sensitive file systems and commands, and if not it's still pretty easy to get used to.

---

### Post by Darkhack on 2009-08-01
My programming professor once told a story of how he was responsible for transferring a website from a Windows server to a Linux server.  The move was simple enough, but he noticed about a third of the links were broken after the move and he struggled to figure out why until he finally noticed the case sensitivity.  The original developer was very inconsistent.  Sometimes the links would be to Page.html and others to page.html.  He had to go through and fix all of them.  So I suppose one could say that case sensitivity is a means of keeping the users consistent.  To me, it just makes more sense.  A capital and lowercase letter have the same sound but they are not the same character.  If I started a sentence with a lowercase letter in English class, I'd get counted off for it.

---

### Post by lisati on 2009-08-01
> **Darkhack said:**
>  A capital and lowercase letter have the same sound but they are not the same character.  If I started a sentence with a lowercase letter in English class, I'd get counted off for it.

Good point. Written language tends to be a bit more formal than spoken language, it's easy to forget that our computers tend to be a touch more literal than we humans. (We could easily get side-tracked at this point by discussions like [this one]("http://ubuntuforums.org/showthread.php?t=1050685").)

---

### Post by JordyD on 2009-08-01
> **Darkhack said:**
> If I started a sentence with a lowercase letter in English class, I'd get counted off for it.

And in CS class, you'd be erasing the wrong directory. :)

---

### Post by MasterNetra on 2009-08-01
> **Mornedhel said:**
> Yeah, we do, actually. So that Linux can be a more attractive platform for third-party closed source developers, among other things. Which will attract more Average Joes once the mainstream apps are ported, if they ever are.

Yet also remember the third-party closed source developers go where the people are. people = $ for them. No matter how easy it is to develop on a platform, companies aren't going to do it, if there isn't a large enough group of people using it.

---

### Post by Dullstar on 2009-08-01
I find case sensitivity useful.

The only problem I ever ran into was when I accidentally saved some files to "/host/dos/" instead of "/host/DOS/"

The fix?  Move the files, then delete the directory.  I keep most of what I use in DOSBox in that folder.

---

### Post by Dr Small on 2009-08-01
Case-insensitive is messy, confusing, inexact and unorganized, whereas case-sensitive is clean, clear, exact and organized.

---

### Post by saulgoode on 2009-08-01
Consider that when internationalization is taken into account, equating lowercase values and uppercase values can become problematic when doing comparisons. For example, in some languages a "single" lowercase letter may map to multiple letters when capitalized (e.g., ["ß"]("http://en.wikipedia.org/wiki/%C3%9F")), and vice versa. In order to properly consider two characters equivalent except for case, a set of rules for all supported languages would need to be referenced and the rule set specified as a property of the locale. 

The situation for case-insensitive comparisons, taking into account i18n, would become similar to that required for canonical equivalence testing of characters with diacritical marks -- should a letter with an umlaut be considered equivalent to that same base letter with a cedilla? Sometimes such comparisons are desirable, but to provide it as a general implementation might create problems for developers, and users, in different countries. 

So while case-insensitivity may seem straightforward for programmers in the United States (and some other Western countries), it is really a very specialized solution that is not readily applicable to the broader audience.

---

### Post by aysiu on 2009-08-01
Can someone opposed to case-sensitivity present a few cases in which a novice user would be tripped up? I don't really see what the big deal is.

---

### Post by swoll1980 on 2009-08-01
> **aysiu said:**
> Can someone opposed to case-sensitivity present a few cases in which a novice user would be tripped up? I don't really see what the big deal is.

Other than not being aware of the case-sensitivity, I can't think of anything. When I was new to Linux, I was trying to do cd ~/desktop, and I had to post this forum wondering why it wouldn't work. I think that was my first post here.

---

### Post by aysiu on 2009-08-01
Yeah, I guess if you're typing into the terminal and trying to *cd* to the Desktop, it could trip you up.

That's why I always advise new users who have to use the terminal to *paste* commands in instead of retyping the commands.

---

### Post by mdsmedia on 2009-08-02
> **blueturtl said:**
> At least in the case of FAT32, you need to mount the file system with the proper codepage and chacter set. Otherwise the system will be case sensitive and while it may work for Linux, Windows will surely freak out.



Have you considered the fact that operating system design also enforces  computing habits? 
If you learn to use a regular account instead of a root account, it is better in the long run even though constantly running as root is very convenient.

If your operating system or applications indicate you can issue them commands or file names that are "close enough" won't that cause terrible trouble later?

It is the nature of the computer to be precise. You can try to disguise the case-sensitive and very exact nature of a computer, but it is only a mask, and people who give their computers inaccurate instructions are the ones that get into trouble.

Ever heard of the expression: "Computers make very fast, very accurate mistakes"?

I would consider having to unlearn case-insensitive names hard, but not learning to use case-sensitive names. Also learning case-sensitivity from the beginning is much more rewarding in the long run.

I say we shouldn't treat newcomers as if they are stupid. Case-sensitivity isn't a very complex thing to understand, all that we need to really do is make sure that new users know that their systems are this way!
Very nicely put!

---

### Post by init1 on 2009-08-02
> **dmizer said:**
> Actually, having a case sensitive file system creates less confusion. You're only confused with a case sensitive file system because you're used to a case non-sensitive file system.
The only case non-sensitive file system I can think of is FAT (and even that has extensions for case sensitivity)

---

### Post by Viva on 2009-08-02
Case Sensitivity is presented a very useful feature in many linux/ubuntu promotional videos:)

---

### Post by ratcheer on 2009-08-02
Linux is case sensitive in order to conform to the UNIX standard. So, you would have to go back to Bell Labs in the early 70's to find out why it is case sensitive. Or, maybe, read some of the very early UNIX books.

Tim

---

### Post by Neheb on 2009-08-02
after getting used to it and adopting a naming convention (all lowercase since I am lazy), I am all for case-sensitivity.

Only "problem" is with files that I didn't create myself, or old files from windows.

---

### Post by Jeinhor on 2009-08-21
> **aysiu said:**
> Can you explain how case sensitivity would affect "average users"? They can name their files however they want to name their files.

Yes, it's not about creating files. It's about finding files.

> **SuperSonic4 said:**
> If average Joe cannot tell the difference between Name and name - even with tab completion - then average Joe can bugger off, Linux is better off without them

Well, Microsoft didn't use that attitude, and look where they are now. Would be sad if Ubuntu would be as big, don't you think? ;)

> **MaxIBoy said:**
> 
Open-source development works because the developers are motivated to create something which will be useful to *them*. And you know what? I trust the developers' judgment (or if I disagree I might program my own version!) Developers are smart people, they know exactly why they made the choices they did.


Yes, that's open source in general. But from what I've understood Ubuntu should focus on end users, not on developers. We wouldn't need interfaces for anything if we just built the objects from the ground up.

> **MaxIBoy said:**
> 
I would humbly submit that you should become well-versed in a given software before you start suggesting changes. After all, you wouldn't try to change the design of a car if you didn't at least know how to drive it and do basic maintenance. And no, I'm not suggesting that you need to know the inner workings of the code, although that helps too. But you need to know how to USE it and you need to know why each feature is useful or not-useful.


It's not a suggested change, I would really only like to discuss and understand WHY Ubuntu is STILL case-sensitive (I know about the history...). And I know my way around Ubuntu, I have been using Linux/Ubuntu for both servers and clients for quite a while.

> **MaxIBoy said:**
> 
If everyone listened to what the "average Joe" wants, there'd be no passwords on anything, no "are you sure" dialogs when you install stuff, no signed public keys on secure websites, and as a result there would be no security whatsoever on ANYTHING. If everyone listened to what the "average Joe" wants, we'd all be using the [Macbook Wheel](http://www.theonion.com/content/video/apple_introduces_revolutionary). And that would suck.

Well, that's not true. Average Joe would certainly not want his system to be unsecure. And they would most certainly not want to get rid of all confirmation dialogs! I've never heard someone saying "Damn that Are you sure-dialog! It saved me from deleting my photos once again! Damn the trash can! Blast!" ;). I'm not really sure how you connected a case-insensitive file system with average Joe wanting a unsecure system?

> **ad_267 said:**
> Average users aren't going to be accessing their files and issuing commands through the terminal, they're only going to use graphical file managers to point and click to get to their files. In that case, why does it matter?

For users who actually enter file paths and use the terminal I'd say it's less confusing having case-sensitive file systems and commands, and if not it's still pretty easy to get used to.

You might be right here. If we hide the file systems case-sensitivity in the GUI we won't have these problems. But since Ubuntu is mostly made up of different configurations files, users will eventually end up editing one of those. They will eventuelly reach the file system. But maybe that's when they have to learn it's case-sensitive.

> **Darkhack said:**
> My programming professor once told a story of how he was responsible for transferring a website from a Windows server to a Linux server.  The move was simple enough, but he noticed about a third of the links were broken after the move and he struggled to figure out why until he finally noticed the case sensitivity.  The original developer was very inconsistent.  Sometimes the links would be to Page.html and others to page.html.  He had to go through and fix all of them.  So I suppose one could say that case sensitivity is a means of keeping the users consistent.  To me, it just makes more sense.  A capital and lowercase letter have the same sound but they are not the same character.  If I started a sentence with a lowercase letter in English class, I'd get counted off for it.

I like being able to call my source files like EditCustomer.aspx to get a better structure when coding, but I like my links to be all in lowercase. I think it looks better. See for example the Ubuntuforums: ubuntuforums.org/newreply.php?do.., if we had case sensitive links we would have ubuntuforums.org/NewReply.php?do...

Okay, different letters have different sounds. But that hardly matters when talking about files or folders. Text documents are still case-sensitive :)

> **Dr Small said:**
> Case-insensitive is messy, confusing, inexact and unorganized, whereas case-sensitive is clean, clear, exact and organized.

I would say the opposite.

> **saulgoode said:**
> Consider that when internationalization is taken into account, equating lowercase values and uppercase values can become problematic when doing comparisons. For example, in some languages a "single" lowercase letter may map to multiple letters when capitalized (e.g., ["ß"]("http://en.wikipedia.org/wiki/%C3%9F")), and vice versa. In order to properly consider two characters equivalent except for case, a set of rules for all supported languages would need to be referenced and the rule set specified as a property of the locale. 

The situation for case-insensitive comparisons, taking into account i18n, would become similar to that required for canonical equivalence testing of characters with diacritical marks -- should a letter with an umlaut be considered equivalent to that same base letter with a cedilla? Sometimes such comparisons are desirable, but to provide it as a general implementation might create problems for developers, and users, in different countries. 

So while case-insensitivity may seem straightforward for programmers in the United States (and some other Western countries), it is really a very specialized solution that is not readily applicable to the broader audience.

Good point.

---

### Post by aysiu on 2009-08-21
> **Jeinhor said:**
> Yes, it's not about creating files. It's about finding files. So the Nautilus search function is also case-sensitive? Let me test it out.

**Edit**: Nope. If you search for files, the search is case-insensitive. (See attached screenshots)

So I still don't get what the problem is for average users.

---

### Post by red_Marvin on 2009-08-21
Adding a console example to that:
```
[leo@troposphere ~]$ touch Foo
[leo@troposphere ~]$ touch foo
[leo@troposphere ~]$ find . -name foo
./foo
[leo@troposphere ~]$ find . -name Foo
./Foo
[leo@troposphere ~]$ find . -iname foo
./foo
./Foo
```

I don't see why linux should assume that we don't know the difference between lower and upper case letters.
If that is the case, whAT About ALL otheR plAces wheRe caSE is Used? Ors pacingf ort hatm atter?

---

### Post by aysiu on 2009-08-21
The mythical average user wouldn't be using the terminal anyway, but thanks for showing us how to do a case-insensitive search.

I'm still not convinced of any real-life situations in which a non-power-user would have a damaged user experience from a case-sensitive filesystem.

---

### Post by lisati on 2009-08-21
> **aysiu said:**
> The mythical average user wouldn't be using the terminal anyway, <snip>

Taking the idea a bit further: the mythical average user does know the difference between lower case and upper case, but out of a combination of laziness, ignorance and habit, doesn't give much thought to what they type.

---

### Post by red_Marvin on 2009-08-21
Aysiu: I were merely trying to puncture a potential argument of "once the user wants to leave gui..." or something like that.
The last sentence was somewhat sarcastic (really!), since I find the whole concept of "case being confusing" very odd.

---

### Post by Musky Melon on 2009-08-21
Case-sensitivity certainly makes verbal communication really long. In example: "It's filename dot t-x-t where the first four letters are uppercase and the remaining letters are lower case" rather than "It's filename dot t-x-t". It also adds additional workload on the user's part when he's trying to search for a file and doesn't know the case or is presented with two mysterious files that have the same name differed by case. And of course it also increases the likelihood of errors. The benefits of a case-sensitive system are really marginal. And of course in a case-insensitive system you can still name your files 'The Doors' or 'the doors' depending upon context*--some of you act like having a case-insensitive system would prevent you from properly naming your documents.

*However not in the same directory. It is worth mentioning that putting unrelated documents in the same directory is bad practice.

---

### Post by red_Marvin on 2009-08-21
> **Musky Melon said:**
> Case-sensitivity certainly makes verbal communication really long. In example: "It's filename dot t-x-t where the first four letters are uppercase and the remaining letters are lower case" rather than "It's filename dot t-x-t".
Most terminal commands also sounds somewhat awkward when read aloud, and in this case, simply looking in the filemanager or issuing an 'ls' beforehand isn't that difficult.
> It also adds additional workload on the user's part when he's trying to search for a file and doesn't know the case or is presented with two mysterious files that have the same name differed by case.
I've yet to see a case where this isn't the user's fault, or rather, I've yet to see this happen at all. AFAIK None of the default files in a linux system has these kinds of ambiguous names.

---

### Post by K-bear on 2009-08-21
The Windows filesystem *is* case sensitive. It's not like it's all lower/upper case.  You can create a file called TeSt.TxT if you really want to and the capitalisation will be as specified.

What Windows does is introduces an extra layer of sanity checking to the FS that Linux, and traditional Unix lacks.  It's the user-friendly mindset vs the developer mindset, really, where the user-friendly mindset limits choices to pre-emptively stop problems, while the developer mindset assumes you know better in the first place (thus doesn't feel the need to stop you).

For example you can create a legal file called * on Linux.  Windows won't let you.  Obviously the only real reason for creating a file called * is if you were being a dick (think someone trying to delete it by typing 'rm *').  The Unix approach is 'only an idiot would do that, so why stop them?'.

Same goes for case sensitive names - Windows stops you having 2 files called Test.txt and test.txt - and rightfully so.  In most programming languages you can have two variables of a different case, but same name, but no semi decent programmer would ever dream of ever taking advantage of this 'feature'.  Again, only an idiot would think having two identically named, but differently cased, files is a good thing.  The assumption is people know this and know not to do it making blocking it redundant.

Case sensitive autocomplete on Linux does bug me though.  I got into the habit of never typing more than two letters then hitting tab to navigate in a hurry, and it's just plain annoying that it is case sensitive.  The correct way of doing it would be to tab-show the correctly cased matches, then move on to the incorrectly cased ones rather than just failing.  The reason this is a bad thing is that tab autocomplete is technically a search, and searches should not be case sensitive - it should be useful rather than pedantic.

People may argue that the OS should not stop you from doing something stupid* (and probably take a few cheap shots at Windows in the process) but consider this.  In C, If I want to write a 32 bit int into a 16 bit memory slot, it'll let me, destroying whatever happens to be unfortunate enough to be 16 bits after the target memory address.  Again nobody in their right mind would do this deliberately so most high(er)** level languages simply don't let you do it - at the expense of speed and memory usage.

Ultimately I feel safe in saying that the way Windows handles things is the correct way, by pre-emptively stopping users doing something they have no good reason to do in the first place, and by pattern matching intelligently, rather than pedantically.

[I]* Where is your GOTO command now?
** Personally I'd consider C a 'middle level language'.[/I]

---

### Post by K-bear on 2009-08-21
> **decoherence said:**
> Also, remember that these rules (whatever the reason for them) are historical and likely rooted in the fact that the systems of the time had very, very few resources (this, for instance, is why we have 'ls' and not 'list' -- that much i know!) So when we talk about sorting and such, it might not be a big deal now but it was then, and it's a difficult convention to break (OS X had to do some very ugly hacks in the early days. Not sure how they handle it now)

If I remember correctly it was simply due to the keyboard on the ASR-33 TTY being un utter POS leading to a desire to have to type as little as humanly possible.  It's also the reason behind bin/ etc/ opt/ usr/ etc.  

I have to say the Windows filesystem is so much more sane - Windows/ Users/ and Program Files/.  It seems stupid to have a filesystem that is so spectacularly arcane* and confusing simply because a keyboard made in the 70's happened to suck.

*P.S. If the name of something is not illustrative of what it is without a cheat sheet then the words 'logical', 'usable' and 'intuitive' should not be used.*

---

### Post by red_Marvin on 2009-08-21
Maybe it's because I'm closer to the dev mindset, (in philosphy even if my skills are very moderat) but I wouldn't call a approach that assumes the user is an idiot very friendly. It's more of a sandbox vs. full access or something, but that would perhaps only be arguing labels ...and then I'd probably need the goto.

---

### Post by K-bear on 2009-08-21
> **red_Marvin said:**
> Maybe it's because I'm closer to the dev mindset, (in philosphy even if my skills are very moderat) but I wouldn't call a approach that assumes the user is an idiot very friendly. It's more of a sandbox vs. full access or something, but that would perhaps only be arguing labels ...and then I'd probably need the goto.

Speaking as a dev I heartily appreciate it when software stops me from doing something stupid.  Everyone believes they will attain a point of understanding and control when they don't need the safety net (See C's bounds checking) but this is the pot of gold at the end of the rainbow - people will always do stupid things.  Even the most knowlegable pro may accidentally press enter at the wrong time while using rm and kill the whole filesystem.  The question is should the OS know that rm -rf / is only ever deliberate 0.01% of the time and stop you, or should it just do it anyway.

What if the filesystem started overwriting old files if you copied a file to it that there was no space for?  What if they removed all the delete confirmation dialogues?  What if the 'save and close' option was removed (you know to save before close, so why ask)? I think any case of stopping the 99.99% of people doing something daft at the expense of the 0.01% who wouldn't do it anyway as they (should) know better is a good thing.  

When I get in a car I like to wear a seatbelt, even if it does stop me climbing into the back while driving.

---

### Post by red_Marvin on 2009-08-21
I agree, but it were you who called it the 'developer mindset', however I do of course too want (and need) some level of protection from shooting myself in the foot. I guess the hard part is to agree on what level to start/stop. - I personally think that case sensitivity is not difficult at all, so I don't mind it. I guess I would not stop using linux if it changed to case insensitivity, it's more that I think that the long term benefits from changing (if any at all) do not upweigh the short term detriments linked to the transitional period.

---

### Post by Dullstar on 2009-08-21
I kinda like having a sensitive file system, actually, because that way I can make a file with the same name with different casings if I want to.  Besides, I like how the file system used by Linux uses / instead of \.  I prefer accessing directories with the correct casing than pressing \ just because it's more convenient.  \ is just placed weired for file system use.

Also, I wanted to make a game, so I try putting the music in a directory with the beta character...  Windoze didn't like it.

---

### Post by Musky Melon on 2009-08-22
> **red_Marvin said:**
> Most terminal commands also sounds somewhat awkward when read aloud, and in this case, simply looking in the filemanager or issuing an 'ls' beforehand isn't that difficult.


You're assuming the person you're talking to is at their computer. Sometimes you have to tell people about multiple files. Now you have to tell them about the cases of each file provided that some retard decided to put multiple files with the same name but different case.

> **red_Marvin said:**
> 
I've yet to see a case where this isn't the user's fault, or rather, I've yet to see this happen at all. AFAIK None of the default files in a linux system has these kinds of ambiguous names.

I have. Happened a lot on UNIX file servers where people would do multiple saves of the same file only they typed it wrong. Joe Blow in account doesn't care about preserving cases. Now we've got people out of sync viewing different versions of what is supposed to be the same file. Then there is also the issue of some software and some portable devices changing the case on you so when you copy it back to the directory you get a new file rather than overwriting an existing one.

There are plenty of reasons to not like case-sensitivity and virtually no benefits to having it. Putting multiple files in the same directory with the same name only cased differently is bad practice so why let people do it anyway?

---

### Post by JordyD on 2009-08-22
> **Musky Melon said:**
> You're assuming the person you're talking to is at their computer. Sometimes you have to tell people about multiple files. Now you have to tell them about the cases of each file provided that some retard decided to put multiple files with the same name but different case.
Paper.

> **Musky Melon said:**
> Putting multiple files in the same directory with the same name only cased differently is bad practice so why let people do it anyway?

Why stop them?

This is like tabs vs spaces. The argument will never end because there are good and bad things about everything. Bash (so I hear) will be getting case-insensitive tab completion soon, so scratch the auto-completion problem.

When an OS restricts what you're allowed to do because it thinks that there is no possible reason that you would want to do that, then it gets annoying. Recently I've been using a Mac. It doesn't let me make files starting with a "." from the Finder. I'm sure they reasoned that people didn't want their files disappearing when they created them. Well, I'm one of those people that *wants* that to happen. The Mac won't even let me delete the 'Documents' folder in my home directory. Now I can't symlink my Documents folder to my remote Samba share. Guess how I got around that. Yes, I named the folder "documents" instead of "Documents".

Now tell me again that there are hardly any benefits to giving users more power versus restricting it.

---

### Post by Musky Melon on 2009-08-22
> **JordyD said:**
> 
Why stop them?

This is like tabs vs spaces. The argument will never end because there are good and bad things about everything. Bash (so I hear) will be getting case-insensitive tab completion soon, so scratch the auto-completion problem.

When an OS restricts what you're allowed to do because it thinks that there is no possible reason that you would want to do that, then it gets annoying. Recently I've been using a Mac. It doesn't let me make files starting with a "." from the Finder. I'm sure they reasoned that people didn't want their files disappearing when they created them. Well, I'm one of those people that *wants* that to happen. The Mac won't even let me delete the 'Documents' folder in my home directory. Now I can't symlink my Documents folder to my remote Samba share. Guess how I got around that. Yes, I named the folder "documents" instead of "Documents".

Now tell me again that there are hardly any benefits to giving users more power versus restricting it.

You know that you actually can make a .directory in OS X using mkdir in terminal just not in Finder? You could also create a symbolic link for Documents in the terminal after moving the folder (to which it lets you). There are many other ways to accomplish your goal. Looks like they gave you a route to get what you want while simultaneously protecting lesser users. I stand by my claim, there is virtually no benefit to having a case-sensitive system.

---

### Post by red_Marvin on 2009-08-22
> **Musky Melon said:**
> [...]Now you have to tell them about the cases of each file provided that some retard decided to put multiple files with the same name but different case.

I have. Happened a lot on UNIX file servers where people would do multiple saves of the same file only they typed it wrong. Joe Blow in account doesn't care about preserving cases. Now we've got people out of sync viewing different versions of what is supposed to be the same file.[...]
I just don't think that this is should be the assumed general user, I mean I wouldn't let a person use my car if he/she do not know where the brakes are. Misspellings will happen anyway, there could be extra letters (foo.txt dfoo.txt fo.txt) should files with names close to other already existing files be allowed?
Note that I've more than once misspelled things myself, accidentally named files ' - since I've managed to hit :w'<CR> instead of :w<CR> in vim. (The ' and <CR> key is right next to each other on a Swedish keyboard)

---

### Post by K-bear on 2009-08-22
[IMG]http://imgs.xkcd.com/comics/rtfm.png[/IMG]

Seems appropriate.

---

### Post by Musky Melon on 2009-08-22
> **red_Marvin said:**
> 
I just don't think that this is should be the assumed general user, I mean I wouldn't let a person use my car if he/she do not know where the brakes are.


Your analogy isn't even close to what we're talking about. Not caring to preserve case or having programs/file-systems that change case is not the same as not being able to safely operate a car which puts people's lives in danger. Furthermore, you can't just revoke people's network privileges at your work because somebody doesn't care to preserve case.

> **red_Marvin said:**
> 
Misspellings will happen anyway, there could be extra letters (foo.txt dfoo.txt fo.txt) should files with names close to other already existing files be allowed?


This is a different issue. There is no way to predict a spelling error it would be impossible it fully implement. Furthermore the file-system would be broken if you couldn't store files with different names. Again, this is a completely different issue than case-sensitivity.

---

### Post by RabbitWho on 2009-08-22
Our "Digital Media" teacher in college told us all to always save our files as lower case and without spaces (even though of course the college had windows computers and none of us had heard of anything else). when we asked him why he said it was good discipline and it built character.

---

### Post by red_Marvin on 2009-08-22
Musky melon: the car analogy is seldom fully correct, maybe I missed this time. My point is simply that most systems require certain base knowledge.
Sure, case sensitivity might be inconvenient in certain cases, but for me personally, I do not think it is a problem really.
However on locking out users, perhaps I couldn't but I would not see it as a problem with the _system_ either, but with the users.

I think we have fundamentally different views here, or at least thinking differently on how far the computer should go in order to ease the use.
I have more or less expressed my points as well as I can, and it seems I am not able to convince you, while I fail to see any issue [at all] with a case sensitive file system, so I doubt you will convince me either.
I actually think it is less confusing if anything, if two files are described by different strings, they are different files. And with that I'll jump off.

---

### Post by Mister LinOx on 2009-08-22
As all above have said. Although I like it, I would prefer, at least, having the option to make usernames with caps in them. I fancy MisterLinOx over misterlinox.

---

### Post by JordyD on 2009-08-22
> **Musky Melon said:**
> You know that you actually can make a .directory in OS X using mkdir in terminal just not in Finder? You could also create a symbolic link for Documents in the terminal after moving the folder (to which it lets you). There are many other ways to accomplish your goal. Looks like they gave you a route to get what you want while simultaneously protecting lesser users. I stand by my claim, there is virtually no benefit to having a case-sensitive system.

These are both things I considered, and never did because it might screw up the system. If you're an application that expects things to be a certain way, because you *know* that it's not allowed to be any other way, would it mess you up if I changed things on you?

There are many other ways, all carrying with them the problems that all 'workarounds' do.

Any design that facilitates the need of workarounds because they're restricting the power of the user is a bad design.

---

### Post by Musky Melon on 2009-08-22
> **JordyD said:**
> These are both things I considered, and never did because it might screw up the system. If you're an application that expects things to be a certain way, because you *know* that it's not allowed to be any other way, would it mess you up if I changed things on you?

There are many other ways, all carrying with them the problems that all 'workarounds' do.

Any design that facilitates the need of workarounds because they're restricting the power of the user is a bad design.

It doesn't mess anything up. It's just Finder trying to be protective towards lesser users (who in all probability aren't going to redirect Documents to other drives) but there is still a method to accomplish your goal and the method requires a deliberate act from the user. As such these aren't really "workarounds".

Anyway, back to the case-sensitivity. I just view it as a nicety. Given that there really isn't a good reason to have two files of the same exact name being case-insensitive means I don't have to remember the casing convention and I avoid the issue of programs or imported files from other systems changing the case and thus creating a new file. It just makes the whole thing less annoying. In short it makes things easier which is inline with the ultimate purpose of using a computer.

---

### Post by 3rdalbum on 2009-08-23
Isn't it because Unix was case-sensitive, and Linux is designed to be as close to Unix as possible?

---

### Post by Dr. C on 2009-08-23
The real question should be why is Windows not case sensitive? Non case sensitive OSs arose form backwards compatibility with Teletypes and Punch Cards which originated in the 1900's and 1890's respectively. 

When Unix arose in the 1960's it was a modern operating system in its day and was case sensitive. GNU / Linux as a much more modern Unix clone is also case sensitive. By the way one can make recent versions of Windows case sensitive by a registry change and this is necessary to run applications like Apache for example.  

As for helping users it makes much more sense to have computers behave as common languages where A and a are different characters than to accommodate technologies that are over 100 years old.

---

### Post by K-bear on 2009-08-24
> **FineE said:**
> The real question should be why is Windows not case sensitive? Non case sensitive OSs arose form backwards compatibility with Teletypes and Punch Cards which originated in the 1900's and 1890's respectively. 

When Unix arose in the 1960's it was a modern operating system in its day and was case sensitive. GNU / Linux as a much more modern Unix clone is also case sensitive. By the way one can make recent versions of Windows case sensitive by a registry change and this is necessary to run applications like Apache for example.  

As for helping users it makes much more sense to have computers behave as common languages where A and a are different characters than to accommodate technologies that are over 100 years old.

Windows is case sensitive, only file compares are not which you'd realise had you bothered to read the thread.  The whole 'Windows is based on 100 year old tech lolzorz' angle you've come up with is just mindless fanboyism that only serves to damage Linux' reputation among the knowledgeable.

There are pros and cons to each approach but acting like it's because Windows still uses the equivalent of punch cards is intellectually dishonest.

---

### Post by RiceMonster on 2009-08-24
> **K-bear said:**
> Windows is case sensitive, only file compares are not which you'd realise had you bothered to read the thread.  The whole 'Windows is based on 100 year old tech lolzorz' angle you've come up with is just mindless fanboyism that only serves to damage Linux' reputation among the knowledgeable.

There are pros and cons to each approach but acting like it's because Windows still uses the equivalent of punch cards is intellectually dishonest.

Ummm... he/she said that was the reason why OSes were originally case sensitive, and thus it doesn't make sense anymore, not "lol windows uses punch cards lol". It was a valid point towards case-sensitivity, not really mindless Windows bashing. As you can see, he/she said it's possible to make Windows case sensitive.

---

### Post by ssam on 2009-08-24
If you want case insensitive bash completion run
```

echo "set completion-ignore-case on" >>~/.inputrc

```
note: the above command is case sensitive :-)

there are a whole bunch of other issues with filenames on unix [http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html](http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html) though i am not sure if they are really big enough issues to worry about.

---

### Post by sjatkins on 2013-04-01
> **Jeinhor said:**
> I'm just curious why Ubuntu and Linux in general is case-sensitive? I can see a very good reason for having a case-insensitive file system though: less confusion!

Why in the world wouldn't it be case-sensitive? Filenames are strings.  Case-sensitivity is built in expected feature of strings in most settings.  So why make an exception for file names?  

I hate it that in OS X for instance SCS tools by default think there has been a change to files simply because OS X is by default case-insensitive.  What an absolutely dumb idea.  If I wanted myCoolFile and MyCoolFile to be the same thing then I would have given them the same name.  

This is a throwback to when filesystems (and OSes) were less capable.  It is not a freaking feature regardless of the fanboys for systems that still support this broken behavior.  And if software out there depends on case-insensitivity then that software is broken and in need of repair.

---

### Post by QIII on 2013-04-01
This is a very, very old thread.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

Thanks,


QIII

---

### Post by sisco311 on 2013-04-01
oLD tHREAD cLOSED.

---

