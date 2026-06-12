---
title: "Is the ancient OpenOffice Linux-killing highlighting bug a wontfix?"
date: 2015-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by halfbeing on 2015-04-26
I am currently doing a test installation on an old hard disk with a view to reinstalling the ghastly Windows Vista on my laptop, which has been running Ubuntu for many years. The reason is that I need to create documents that are 100% compatible with MS Word, especially with regard to one particular feature, and the office software available for desktop Linux distributions, namely OpenOffice and its fork LibreOffice, isn't capable of doing this. (And before anyone tells me to install MS Office in Wine, I've tried and it doesn't work.)

The problem with OpenOffice (and LibreOffice) is with highlighting. Highlighting in OpenOffice becomes background in MS Office, meaning that someone who doesn't know what is going on (like one of my clients), can't remove it. There is no way that I can tell a client to follow an obscure workaround. Since highlighting is something that people are very likely to do when they share documents, this bug is undoubtedly a huge barrier to adoption of FOSS in collaborative office environments. This bug was first reported ages ago, 2003 or something like that if I remember right, but it has never been fixed, despite countless bug reports that have been filed over the years as the previous ones have been ignored. I believe the problem is with the ODT file format, which would need to be changed. You would think that if the aim of OpenOffice etc. is to be a 100% interoperable with MS Office, that changing the file format would be a price worth paying, but apparently not. Am I to assume that this problem will never be fixed and that I should say goodbye to Ubuntu forever? Or is there the possibility either that it will be fixed in OpenOffice or LibreOffice, or that a fork will be created for an MS Office compatible version?

---

### Post by neu5eeCh on 2015-04-26
I do get the impression that LibreOffice *Writer* gets a fraction of the attention that *Calc* gets. It's like all the engeering/code/math guys are obsessing over Calc. Who needs English majors?

I'm always reading about the next great upgrade to *Calc*. Woohoo!* Writer*? Meh.

The absolute drive me around the bend, kick the dog and shoot the mule bug is Libre Office's inability to vertically center text without absurd hoop-through-jumping. I can mess up LibreOffice/MSWord compatibility with one, (1), vertically centered period (.).

HOWEVER.

Why obsess over LibreOffice? If you want to continue using Linux, why not try WPS Office (which is actually better at cross-compatibility):

[http://www.wps.com/linux/](http://www.wps.com/linux/)

Or Softmaker Office:

[http://www.softmaker.com/english/](http://www.softmaker.com/english/)

Which is *as good at* cross-compatibility and will soon be releasing a fresh and updated version -- to be much better at cross-compatibility.

---

### Post by vasa1 on 2015-04-26
> **halfbeing said:**
> ... You would think that if the aim of OpenOffice etc. is to be a 100% interoperable with MS Office, ...
That would assist a monopoly survive. Maybe MS Office might find it easier to be "intraoperable" with its own previous versions and "interoperable" with an open source standard.

---

### Post by ian-weisser on 2015-04-26
> **halfbeing said:**
> You would think that if the aim of OpenOffice etc. is to be a 100% interoperable with MS Office, that changing the file format would be a price worth paying, but apparently not.
False assumption: You assume that the .docx format can be sensibly interpreted. It cannot. It's a deliberately opaque and obfuscated format.
If you wish to help the Document Foundation figure out how Word encodes/decodes highlighting in a .docx format, their (mostly volunteer) developers will be eternally grateful.

---

### Post by d-cosner on 2015-04-26
Rather than changing out an OS that you are happy with why not install Vista in Virtualbox and install MS Office in it? WPS Office is said to be more compatible with MS Office but I have never tested it myself. Just trying to think of some options that could help you with this.

Edit: I am not sure if Vista is even supported, at the very least you should check that out before going that route.

---

### Post by halfbeing on 2015-04-27
VTPoet:

Thanks for the pointer to WPS Office. It looks interesting, but I'm wary because the Linux version is still in alpha and there is a long list of recently fixed serious on the community page, suggesting that there are more serious bugs still to be fixed. I can't take the risk of sending a client a corrupt document.

vasa1:

Yes it would be great if I could order the entire world to use the file format I choose, but I can't. I have to give the client what they expect, and they expect Word documents. If I don't give them what they want, I won't get any work. You are not going to break a monopoly if you don't offer people an alternative way of doing what they need to do. In any case the whole history of Star Office and its successors has been about being like MS Office. If that hadn't been the case then they would have been designed quite differently.

d-cosner:

My laptop doesn't support virtualisation, so virtual machines are out of the question until I can afford to replace it.

---

### Post by philhughes on 2015-04-27
It is not a bug, but a difference in behaviour. But anyway, it looks like v5 will enable better compatibility:

[http://zolnaitamas.blogspot.co.uk/2015/03/word-compatible-text-highlighting-in.html](http://zolnaitamas.blogspot.co.uk/2015/03/word-compatible-text-highlighting-in.html)

---

### Post by halfbeing on 2015-04-27
Thanks for the link. That's not a bad workaround. But it depends on being able to do without MS Word shading. Does anyone ever use that in the real world? If they don't then this will be a viable solution.

---

### Post by vtpoet2 on 2015-04-27
> **halfbeing said:**
> VTPoet:

Thanks for the pointer to WPS Office. It looks interesting, but I'm wary because the Linux version is still in alpha and there is a long list of recently fixed serious on the community page, suggesting that there are more serious bugs still to be fixed. I can't take the risk of sending a client a corrupt document.

Fair enough. Sounds like you should return to Windows. That's frustrating but I would probably avoid blaming Ubuntu/Libre Office. MS wants you to use Word on Windows and fine [grouse, sigh, p & moan] Apple. They do *not* want third party compatibility with suites like LibreOffice and _deliberately_ obfuscate their format. In a perfect world (or various municipalities in Germany) you would simply switch everyone to LibreOffice and screw Word. Short of that, if you want to use Word, and it's mission critical, then say hello to your new best(?) friend -- Windows 8/10. 

I dual boot once a year -- to use Turbotax. And occasionally itunes for my ipod.

---

### Post by kurt18947 on 2015-04-27
Halfbeing, your situation is not unusual. Have you explored the online variants of MS office?

[https://office.live.com/start/default.aspx](https://office.live.com/start/default.aspx)

I've not looked at them and presume they don't have all the functions of the full-fat (literally!) Office. Do they support the functions you need? Supposedly the newest MS Office versions render and save .odt files accurately. I'll believe that just as soon as I see it.

---

### Post by The Cog on 2015-04-27
Recent versions of office claim to be able to support the Open DOcument standard. A quick test shows that it can at least open .odt and .ods files.

---

### Post by kurt18947 on 2015-04-27
> **The Cog said:**
> Recent versions of office claim to be able to support the Open DOcument standard. A quick test shows that it can at least open .odt and .ods files.

My experience with opening .odt files on MS office is extremely limited as well. I rented time on a machine at a FedExOffice (formerly Kinkos) location. It had Office 2010 installed. I tried opening a simple .odt file with indents and bullets. First I was told the file was corrupt. I said "okay, open it anyway". The solid bullets were not filled and the spacing was messed up. I didn't try more.

---

### Post by sybille on 2015-04-27
> **halfbeing said:**
> (And before anyone tells me to install MS Office in Wine, I've tried and it doesn't work.)

I run MS Office in Wine and have done so for years with no difficulty. I need it for compatibility with certain clients, too.

I'd recommend checking out Crossover Linux, the commercial version of Wine.  It's not free, it does include support. Also, there is a trial version. You should be able to get at least MS Word 2010 SP 1 running with it.
[https://www.codeweavers.com/compatibility/crossover/microsoft-office-2010-service-pack-1](https://www.codeweavers.com/compatibility/crossover/microsoft-office-2010-service-pack-1)
[https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install](https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install)

---

### Post by kurt18947 on 2015-04-27
> **sybille said:**
> I run MS Office in Wine and have done so for years with no difficulty. I need it for compatibility with certain clients, too.

I'd recommend checking out Crossover Linux, the commercial version of Wine.  It's not free, it does include support. Also, there is a trial version. You should be able to get at least MS Word 2010 SP 1 running with it.
[https://www.codeweavers.com/compatibility/crossover/microsoft-office-2010-service-pack-1](https://www.codeweavers.com/compatibility/crossover/microsoft-office-2010-service-pack-1)
[https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install](https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install)

PlayOnLinux gets pretty good reviews as well. No experience because LibreOffice has done everything I've needed.

---

