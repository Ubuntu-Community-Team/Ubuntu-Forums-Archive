---
title: "a stupid question maybe : why not .lex as an extension?"
date: 2005-12-10
forum: The Cafe
---

### Post by newbie2 on 2005-12-10
why can't linux programs , like in window$ (.exe) have a universally **.lex** (linux execute) for all programs,games etc ?...it would be more easy for everybody coming from the window$ platform...:confused:

---

### Post by Iandefor on 2005-12-10
Because there's no need for it. An executable is known to be executable, and a special extension is unnecessary. A Windows user generally finds this out very quickly and there's no need to change the name of every executable to make it obvious for them. Oh, and, using Linux (Or any POSIX-Compliant operating system, for that matter), you would need to append the .lex to the end of a command do the simplest of operations, like copying. It would get ridiculous very, very quickly.

---

### Post by gord on 2005-12-10
also, don't newer versions of windows hide the .exe part anyway?

---

### Post by JimmyJazz on 2005-12-10
[QUOTE=newbie2]why can't linux programs , like in window$ (.exe) have a universally **.lex** (linux execute) for all programs,games etc ?...it would be more easy for everybody coming from the window$ platform...:confused:[/QUOTE]

ah you have much to learn about linux little one, you're in luck though because UBUNTU is a great distro for learning the ropes.

---

### Post by Iandefor on 2005-12-10
[quote=gord]also, don't newer versions of windows hide the .exe part anyway?[/quote] hiding the .exe extension is turned on by default in Windows, but it's quite easy to set it to display the extension.

---

### Post by aysiu on 2005-12-10
You don't have to agree with this, but you should read it:
[If you have ever wondered why Linux lacks something like an exe](http://ubuntuforums.org/showthread.php?t=54227)

---

### Post by PatrickMay16 on 2005-12-10
[QUOTE=newbie2]why can't linux programs , like in window$ (.exe) have a universally **.lex** (linux execute) for all programs,games etc ?...it would be more easy for everybody coming from the window$ platform...:confused:[/QUOTE]
Ah, my friend, you should check this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It will answer your question, and possibly others you may have.

---

### Post by Stormy Eyes on 2005-12-11
[QUOTE=newbie2]why can't linux programs , like in window$ (.exe) have a universally **.lex** (linux execute) for all programs,games etc ?...it would be more easy for everybody coming from the window$ platform...:confused:[/QUOTE]

This is unnecessary. If a file lives in a "bin/" directory, it's probably executable. A file extension on a file that lives in a directory like /usr/bin is like asking a person to enter their "PIN Number" instead of their PIN. Why introduce unnecessary redundancies?

---

### Post by JimmyJazz on 2005-12-11
also technically any file can be made excutable in linux you just have to set the permissions.

---

### Post by Kvark on 2005-12-11
ls.lex
cp.lex something /somewhere/
rm.lex something
sudo.lex apt-get.lex install some-package
...lol, it'd decorate the command line at least, thats for sure.

Personally I find it illogical to use the name of the file to tell which type the file is. Add a type property next to the name, permissions, owner, group and last edit date if needed. But putting the type in the name.., Why just type? Why not put permissions, owner, group and last edit date in the name too while we are at it then?

---

### Post by BWF89 on 2005-12-11
We allready have a univeral package format. It's .tar

.tar works on any *nix system. Linux, Unix, BSD, etc.

---

### Post by Malphas on 2005-12-11
[QUOTE=PatrickMay16]Ah, my friend, you should check this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It will answer your question, and possibly others you may have.[/QUOTE]
Terrible, terrible article, written by someone that can't even write valid (X)HTML.

---

### Post by aysiu on 2005-12-11
[QUOTE=Malphas]Terrible, terrible article, written by someone that can't even write valid (X)HTML.[/QUOTE] That's your critique?

---

### Post by prizrak on 2005-12-11
I don't think there is need for one executable extension. We have packages suck as .ded and .rpm and while I'm not sure if .debs can be installed on other distros .rpms work just fine through alien. The executables tend to be commands anyways I don't see much difference between typing in nautilus, nautilus.lex or nautilus.bin the only thing is that the first one has less to type (which is irrelevant with tab completion anyways).

---

### Post by Malphas on 2005-12-11
[QUOTE=aysiu]That's your critique?[/QUOTE]
Yep, I don't know where all these people get off, talking as though they have the authority to represent the entire FOSS community and have an absolute understanding of the motives and opinions of every developer.  From what I've noticed these usually aren't even particularly experienced Linux users either, they've generally only had a few years under their belt.  Phrases like "open source developers don't wan't to appease users, they're writing programs for themselves", "Linux doesn't care about gaining market share", etc. are just ridiculous and far too commonplace.  And when someone who actually knows what they're talking about takes a progressive stance (such as Steven Vaughan-Nichols on there being too many distributions), they're all over the place, thinking they know better.  The fact that this guy's (the author of the "Linux is not Windows" article) webpage is code-soup just adds to the hypocritical and pretentious nature of his comments.

Sorry for the rant...

---

### Post by jdong on 2005-12-11
Perhaps we need introduction to the **file** command?

```

jdong@shuttle:~$ file kingdoms.jpg
kingdoms.jpg: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJ"
jdong@shuttle:~$ mv kingdoms.jpg kingdoms.exe
jdong@shuttle:~$ file kingdoms.exe
kingdoms.exe: JPEG image data, JFIF standard 1.01, comment: "CREATOR: gd-jpeg v1.0 (using IJ"

```

Three-letter extensions are the dumbest idea ever. Each file has enough identifying data to determine what type they are -- extensions are just bogus.

---

### Post by Lovechild on 2005-12-11
if the execute bit is set, it's an executable - period.

what's so hard to understand about that, bash even nicely highlights the names for you on ls and tab completion makes your life easy.

besides who cares about executables and extensions in this the era of guis, I click the menu entry and voila.. I honestly rarely even use nautilus to browse my files.

---

### Post by aysiu on 2005-12-11
[QUOTE=Malphas]Yep, I don't know where all these people get off, talking as though they have the authority to represent the entire FOSS community and have an absolute understanding of the motives and opinions of every developer.  From what I've noticed these usually aren't even particularly experienced Linux users either, they've generally only had a few years under their belt.  Phrases like "open source developers don't wan't to appease users, they're writing programs for themselves", "Linux doesn't care about gaining market share", etc. are just ridiculous and far too commonplace.[/quote] I agree with you on this. In fact, I get really pissed when people say, "Linux doesn't need more users." It doesn't really matter what it *needs*, frankly. A lot of distros would benefit from more users using it, and each distro has its own goals. The goals of Gentoo are not the same goals of SuSE. The goals of Damn Small Linux are not the same goals of GoboLinux.  

> And when someone who actually knows what they're talking about takes a progressive stance (such as Steven Vaughan-Nichols on there being too many distributions), they're all over the place, thinking they know better.  I think the Linux is not Windows article leaves some room for improvement, but it does have some valid points in it (the motorcycle and car analogy is apropos) and takes into account a degree of moderation, even though its thesis is rather extreme. It even addresses the idea of Linspire being like Windows... I don't know if I agree 100% with the conclusion, but the author doesn't ignore the desktop distros.

> The fact that this guy's (the author of the "Linux is not Windows" article) webpage is code-soup just adds to the hypocritical and pretentious nature of his comments. I don't know. I mean, just because you've used Linux for a long time doesn't mean you know how to code HTML. After all, I can code HTML, but I don't really know that much about Linux--the two don't correlate that well with each other.

---

### Post by Malphas on 2005-12-11
[QUOTE=aysiu] I don't know. I mean, just because you've used Linux for a long time doesn't mean you know how to code HTML. After all, I can code HTML, but I don't really know that much about Linux--the two don't correlate that well with each other.[/QUOTE]
No that's not what I was suggesting, it was more of a sidenote than anything.  It wasn't just that the code was terrible, but he actually declared his pages as various doctypes and stuck the W3C logos on, yet didn't bother to actually write them to the correct spec, if he hadn't bothered with the doctype either then it would at least make some sense.  But what he's done would suggest he doesn't really understand W3C's standards or doesn't care but makes it want to seem like he does, which makes me hesitant to take anything he has to say on IT issues seriously or believe there's any credibility to his claims.  But like I said my main issue was with the content and his opinion that he had the right and ability to speak on behalf of every Linux distribution and developer out there - the bad (X)HTML was just the icing on the cake really.  Also, I should not that the page with the said article now does validate correctly (it didn't a few weeks ago) but the majority of the rest of his site doesn't.

---

### Post by aysiu on 2005-12-11
Point taken.

That said, I guess I just don't feel as strongly against that article as you do. I don't agree with it 100%, but I do believe it makes some good points, when taken with a grain of salt.

---

### Post by prizrak on 2005-12-11
[QUOTE=aysiu]Point taken.

That said, I guess I just don't feel as strongly against that article as you do. I don't agree with it 100%, but I do believe it makes some good points, when taken with a grain of salt.[/QUOTE]
Well everything has to be taken with a grain of salt no one is truely objective that's normal. I also agree with some of the article, I payed more attention to his analogies actually than anything else. 
One thing I don't agree with (independent of the article) is how many people think everyone should use Linux. I personally don't know it it would be a good idea to give Linux to your typical virus ridden Windows user since at the very least Windows will not let you delete shared files and in Linux and idiot with a root password can delete the entire kernel w/o even so much as a log out from X.

---

### Post by aysiu on 2005-12-11
[QUOTE=prizrak]
One thing I don't agree with (independent of the article) is how many people think everyone should use Linux.[/QUOTE] Same here. I believe people should use whatever OS works for them. If Windows is it, it's it. If OS X is it, it's it. If some Linux distro is it, it's it.

The reason some Linux users get some overzealous in evangelizing, though, is that most people don't even realize Linux is a desktop option, and it may, in fact, be the best OS for them.

---

### Post by Stormy Eyes on 2005-12-11
[QUOTE=Lovechild]besides who cares about executables and extensions in this the era of guis, I click the menu entry and voila.. I honestly rarely even use nautilus to browse my files.[/QUOTE]

You'd have to care if you decided that stock GNOME wasn't good enough for you. If you ever have to hack a FVWM config, you'd see the soft black underbelly of Linux right quick.

---

### Post by prizrak on 2005-12-11
[QUOTE=Stormy Eyes]You'd have to care if you decided that stock GNOME wasn't good enough for you. If you ever have to hack a FVWM config, you'd see the soft black underbelly of Linux right quick.[/QUOTE]
There is nothing soft about Linux!!!! Linux is a hard ass OS!!!!! Linux is gangsta! ;) 
Sorry I'm from Brooklyn I can't help it :)

---

### Post by erikpiper on 2005-12-11
My take on .lex-
Why? I came from windows, and didnt miss it at all.

---

