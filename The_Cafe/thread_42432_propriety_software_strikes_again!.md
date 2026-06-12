---
title: "propriety software strikes again!"
date: 2005-06-17
forum: The Cafe
---

### Post by DirtDawg on 2005-06-17
Having a windows machine means doing a lot of research before downloadfing or installing even seemingly harmless software. At least, that's how I feel about it.
My girlfriend, however, does not understand (or doesn't care) the kind of vigilance required to keep a Windows machine from getting 'sick'. So when she downloaded and installed the NAPSTER "free" trial when I was out of the house a few weeks ago, I was slightly upset and wary. She told me to relax.
First, Napster poo'ed all kinds of spyware on our machine. I read the "terms" you agree to and it states that they keep track of your music library (the all-seeing eye). Of course, they don't actually expect you to *read* these terms. 
Next, we found out once you download their tracks, they're encrypted to prevent you from doing anything except playing them through Windows media player. No burning them to CD and no putting them on your Mp3 player (unless, of course, it's a Naptster "approved" brand).
Now the final insult:
I decided today to uninstall the rotton piece of trash and, suprise suprise, it won't uninstall! Napster, of course, doesn't provide an uninstall exe (why on EARTH would anyone ever want to rid themselves of this precious gem?). When I try using the windows built-in uninstall program, I get a message complaing that I need to uninstall the old version of Napster before I can install the new version(!!!!). Of course, nowhere on the napster website is there anything about this "bug" or even uninstalling. Aye yi yi.  ](*,) 
Many of my friends who have not made the switch to open-source don't understand why I always check for open-source equivalents to proprietary software BEFORE I download *anything*. Well I present the above as 'exhibit A' (or maybe 'B', 'C', or 'Z').

---

### Post by trash on 2005-06-17
I've only had my first x86 for bout a month now and have windows running, just to get to know it a bit(YIKES!).
My trial Xchat just ended so i went looking for another IRC, ended up installing a few of them but the WORST was Neo Napster, it installed so much CRAP that Zonealarm popped up about 6-8 times asking to grant permission to various programes like bargains.exe and the like, and of course the Uninstall(lucky there was one at all i guess) only uninstalled Neo Napster not the other crap it installed.

I guess I will just stay away from anything and everything Napster related. I will now start reading the Terms agreements LOL.

Kind of off topic but will the repositories main, universe and multiverse stay spyware free? Are there ANY restrictions in place at the moment to prevent spyware making it into the repositories? Just curious.

---

### Post by N'Jal on 2005-06-17
It amazing what

```

del C:\Program Files\Napster\*

```
does :P

Sometimes its the only solution

---

### Post by trash on 2005-06-17
^:)^

thanks!

---

### Post by aysiu on 2005-06-17
[QUOTE=trash]I've only had my first x86 for bout a month now and have windows running, just to get to know it a bit(YIKES!).
My trial Xchat just ended so i went looking for another IRC, ended up installing a few of them but the WORST was Neo Napster, it installed so much CRAP that Zonealarm popped up about 6-8 times asking to grant permission to various programes like bargains.exe and the like, and of course the Uninstall(lucky there was one at all i guess) only uninstalled Neo Napster not the other crap it installed.

I guess I will just stay away from anything and everything Napster related. I will now start reading the Terms agreements LOL.

Kind of off topic but will the repositories main, universe and multiverse stay spyware free? Are there ANY restrictions in place at the moment to prevent spyware making it into the repositories? Just curious.[/QUOTE]

Most likely, stuff in Debian and/or Ubuntu repositories will be spyware free. First of all, spyware people tend to target Windows over other OSes. Secondly, open source software usually has a little bit of idealism attached to it, even if, in some way, it makes a profit--they're less prone to sneaky tactics and hidden software bundled with installers. Lastly, it may be *theoretically* possible to make spyware for Linux, but I haven't heard of this ever happening. Adware is just not possible, as adware typically uses Internet Explorer, which is built in to Windows (you cannot turn off or uninstall IE--it is *always* running, whether you have it open or not).

---

### Post by DirtDawg on 2005-06-17
[QUOTE=N'Jal]It amazing what

```

del C:\Program Files\Napster\*

```
does :P

Sometimes its the only solution[/QUOTE]

yup. Man I hate that because I know Napster dropped some presents elsewhere on the computer. IN my research, I've found several websites pointing to some files it dumps in the registry. I don't like messing with the registry. 
Mostly I just needed to have a freak-out/vent session.  :) 

[QUOTE=trash]Kind of off topic but will the repositories main, universe and multiverse stay spyware free? Are there ANY restrictions in place at the moment to prevent spyware making it into the repositories?[/QUOTE]

My mom caught me off guard when she asked me once "well how do you know you're not getting any viruses?" But I thought it through and realized that, being open-source, surely *someone* has looked through the code. I also figure if that someone found some malicious code they'd let the rest of us in on it. (right?)

---

### Post by az on 2005-06-17
[QUOTE=trash]
Kind of off topic but will the repositories main, universe and multiverse stay spyware free? Are there ANY restrictions in place at the moment to prevent spyware making it into the repositories? Just curious.[/QUOTE]


If you have access to the source code, you are pretty sure that the app is not spyware or malware.  That is one argument for running only free and open-source software on your machine.  

Precompiled binary modules (like the nvidia driver or the sl-modem driver) are possible candidates for malware, since no one has access to the source.  Firmware is debated, since it usually only can talk to the kernel and the hardware it handles, it is argued that it cannot do any harm.

Nonetheless, Debian makes great effrots to separate fre and non-free repositories.

Universe and certainly multiverse contain these binary-only pieces.

So, if you want to be completely sure, use only the stuff in main.

However, I would not be worried about what is in the ubuntu repositories.

---

### Post by az on 2005-06-17
[QUOTE=DirtDawg]


My mom caught me off guard when she asked me once "well how do you know you're not getting any viruses?" But I thought it through and realized that, being open-source, surely *someone* has looked through the code. I also figure if that someone found some malicious code they'd let the rest of us in on it. (right?)[/QUOTE]


People were put off when they learned that firefox had security patches.

That is what you are talking about.  In many ways, the more security patches you get, (that is, software updates) the more secure your system it.

And by the way the linux or unix is designed, the security flaws found are much less severe, in general than on a Microsoft system.

---

### Post by DirtDawg on 2005-06-17
[QUOTE=azz]People were put off when they learned that firefox had security patches.

That is what you are talking about.  In many ways, the more security patches you get, (that is, software updates) the more secure your system it.

And by the way the linux or unix is designed, the security flaws found are much less severe, in general than on a Microsoft system.[/QUOTE]

Right. That seems right. Also it seems like people in the community could write their own patches (I suppose that's more or less what happens) instead of waiting for mega-company-X to get their rear in gear to plug the dike. 

BTW, I think there should be a bumper sticker that says "I like azz".  :)

---

### Post by trash on 2005-06-17
[QUOTE=azz]However, I would not be worried about what is in the ubuntu repositories.[/QUOTE]

Nice to know!
Thanks for the info.


I am mostly asking because of another poster on this forum saying that with the rise in populary of linux in general, spyware and other traditional windows crap will inevitably become more popular for linux.... should/will it become policy to restrict such software from eventually making it into repositories? I guess i am speaking more of Ubuntu's universe and even multiverse.

---

### Post by az on 2005-06-17
[QUOTE=trash]Nice to know!
Thanks for the info.


I am mostly asking because of another poster on this forum saying that with the rise in populary of linux in general, spyware and other traditional windows crap will inevitably become more popular for linux.... should/will it become policy to restrict such software from eventually making it into repositories? I guess i am speaking more of Ubuntu's universe and even multiverse.[/QUOTE]

The policy is that for everything that is in debian that is not in ubuntu proper (supported by Canonical) to be in universe.  The MOTU (masters of the universe) team look after those packages.  Each of those packages are maintained in debian by a Debian package maintainer.  Debian has high standards.

Look up the debian policy manual for details about what is allowed and not allowed in a package.  It can get complicated.


BTW:  Thanks for the gratuitous flattery!

---

### Post by trash on 2005-06-17
[QUOTE=DirtDawg]

BTW, I think there should be a bumper sticker that says "I like azz".  :)[/QUOTE]


here here!

ok no more kissing azz  :-#

---

### Post by davahmet on 2005-06-17
[QUOTE=trash]


I am mostly asking because of another poster on this forum saying that with the rise in populary of linux in general, spyware and other traditional windows crap will inevitably become more popular for linux.... should/will it become policy to restrict such software from eventually making it into repositories? I guess i am speaking more of Ubuntu's universe and even multiverse.[/QUOTE]

I've heard the same arguement, but it has no merit, based on social reasons as well as technical.

On the technical side, it is much, much harder to write a spy-ware application for Linux because of the way that Linux controls permissions in memory and on the filesystem.  Also, without ActiveX or a simliar vector for malware, it becomes much more difficult to install sneaky stuff.

On the social side of the arguement, the fact that the source code is viewable and auditted through use of MD5 signatures by Linux package managers means that it becomes very difficult to sneak extra stuff into packages.  Spyware and adware creators and distributors rely on the built-in obfuscation that comes with Windows to get away with what is essentially resource hijacking.  Without such obfuscation, distributors (such as Claria, Napster, etc.) gain little to no value by sneaking the extras into the package, and risk a lot with such an action.  The social stigma that comes from doing it is too expensive, especially when the open source community can and will easily strip away such crud.

So, to answer the Fudsters that claim Linux will be hit once it becomes popular, the answer is "no, Linux will be hit with the same problem when Linux closes the source, hence, never."

---

### Post by sonny on 2005-06-17
[QUOTE=davahmet]Also, without ActiveX or a simliar vector for malware, it becomes much more difficult to install sneaky stuff.[/QUOTE]
What is the "real" reason for windows to have ActiveX, I mean the technical reason, what does it do or manage??

---

### Post by poofyhairguy on 2005-06-17
[QUOTE=sonny]What is the "real" reason for windows to have ActiveX, I mean the technical reason, what does it do or manage??[/QUOTE]

What is does do. Install stuff on your computer. Problem is that MSes logic ("we can use it to install things people need but they don't know they do") gets warped once again.

---

### Post by sonny on 2005-06-17
[QUOTE=poofyhairguy]What is does do. Install stuff on your computer. Problem is that MSes logic ("we can use it to install things people need but they don't know they do") gets warped once again.[/QUOTE]
hahahahahahahahahaha... I see your point... :-P

---

### Post by davahmet on 2005-06-18
[QUOTE=sonny]What is the "real" reason for windows to have ActiveX, I mean the technical reason, what does it do or manage??[/QUOTE]

Actually, it's derived from Microsoft OLE technology, which was fairly harmless when confined to Office documents.  The idea of having cross-application scripting combined with Microsoft's vision of networking brought ActiveX into the picture, intended as a way to link IE with Office applications and the OS.  It could have been a good idea if we lived in the fantasy, candy land where all people are nice and nothing ever breaks.  However, since we have the real world and Microsoft pushed ActiveX into it, it has in retrospect been considered a monumentally bad idea.  Worse still has been Microsoft's insistance that ActiveX is a benefit to users.

---

### Post by SparkyDawg on 2005-06-18
I almost want the spread of Linux to stop and have our nice communities stay how they are. If more people continue to switch to Linux, viruses and spyware could be possible.

---

### Post by sonny on 2005-06-18
[QUOTE=davahmet]Actually, it's derived from Microsoft OLE technology, which was fairly harmless when confined to Office documents.  The idea of having cross-application scripting combined with Microsoft's vision of networking brought ActiveX into the picture, intended as a way to link IE with Office applications and the OS.  It could have been a good idea if we lived in the fantasy, candy land where all people are nice and nothing ever breaks.  However, since we have the real world and Microsoft pushed ActiveX into it, it has in retrospect been considered a monumentally bad idea.  Worse still has been Microsoft's insistance that ActiveX is a benefit to users.[/QUOTE]
So in essence it was a good thought but a bad thing to do....  :neutral: That guy really loves his software...

---

### Post by DirtDawg on 2005-06-18
[QUOTE=SparkyDawg]I almost want the spread of Linux to stop and have our nice communities stay how they are. If more people continue to switch to Linux, viruses and spyware could be possible.[/QUOTE]

At last, somone else knows how to spell "dawg" correctly!

---

### Post by davahmet on 2005-06-18
[QUOTE=SparkyDawg]I almost want the spread of Linux to stop and have our nice communities stay how they are. If more people continue to switch to Linux, viruses and spyware could be possible.[/QUOTE]

Yes and no, actually.  Viruses, trojans and spyware will still exist, even in a Linux-dominated environment, but creating and distributing them is much, much more difficult.  But with the openness that comes with Linux and FLOSS, sneakware no longer has the cover of code obfuscation to operate from.  Sneakware tends to lose its potency when exposed.

---

### Post by davahmet on 2005-06-18
With proprietary systems, the applications are protected and hidden while the user data is generally open for all to see.  With open source, the applications are open for all to see while the user data is by default protected.  

So...given a simple choice, how would you like your bank records stored?

---

### Post by Gir on 2005-06-18
I have a feeling that there would be a rather large community dedicated to obliterating spyware should they target linux.  Firefox does a pretty good job with pop-ups.  It has been awhile since i used IE, but afaik it don't offer the same.

That last statement of ignorance fills me with joy. 

Gir.

---

