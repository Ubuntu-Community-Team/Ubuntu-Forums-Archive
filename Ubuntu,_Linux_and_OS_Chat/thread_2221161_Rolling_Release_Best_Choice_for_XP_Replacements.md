---
title: "Rolling Release Best Choice for XP Replacements"
date: 2014-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by SurfaceUnits on 2014-04-30
If you are doing XP replacements, are you using a rolling release distro, a LTS, or are you planning to keep everyone updated manually?

---

### Post by sammiev on 2014-04-30
> **SurfaceUnits said:**
> If you are doing XP replacements, are you using a rolling release distro, a LTS, or are you planning to keep everyone updated manually?

I prefer the Ubuntu Development Version, but I like breakage. Not been so the last few versions.

---

### Post by robin7 on 2014-05-01
If it was for a Linux novice, I'd go with a LTS version.  My favorite rolling-release distro is PCLinuxOS.  I have their Xfce spin on another computer.  Heavier than Xubuntu (my main default distro, the one I always "run home to") but PCLOS' combination of apt-get with RPM packaging is pretty cool.  The all-or-nothing update approach was scary at first but I think it's a safe, reliable rolling-release OS.  I even donated to that project even though I'm a Xubuntu user most of the time.

---

### Post by ian-weisser on 2014-05-01
I find it hard to imagine that most decade-long XP users want to suddenly roll on the bleeding edge of Ubuntu's development.

---

### Post by Warren Hill on 2014-05-01
PAE could be an issue for really old hardware I'm pretty sure if you are staying with a *buntu Linux you only have the option of Xubuntu 12.04 as that was the last release to support non PAE processors.

And as of 12.10 non PAE processors are not supported at all

I believe that you can get a non PAE install of [Bodhi Linux]("http://www.bodhilinux.com/downloads_desktop.php") however not sure what other distros will work but I haven't tried them all.

---

### Post by mörgæs on 2014-05-01
The PAE problem is blown out of proportions. One boot option, problem solved.
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by 3rdalbum on 2014-05-01
> **ian-weisser said:**
> I find it hard to imagine that most decade-long XP users want to suddenly roll on the bleeding edge of Ubuntu's development.

+1000.

---

### Post by LastDino on 2014-05-01
Stay away from anything that says ''testing'', ''development'' etc.

While smaller releases/lighter releases are killer and could teach you lot stay away from OB and such. 

If it is a really must, go with Lubuntu LTS or it is better to stick with Xubuntu LTS. You can give a shot at Fedora or Mint too. I personally liked Xubu and Fedora XFCE. PClinuxOS might be a good choice to go for if you've decent machine, but be warned, it does come with lot of per-installed packages and you might never even use them. It is better to chose something which will require you least uninstalling/installing after you install the OS. I suggest going through packages of those OS I mentioned coming with just to check if what you need is there and if not what it is that you need to get it. Also, if you're using  graphic card and it requires 3rd party drivers, make sure it has Linux release as well.

---

### Post by lykwydchykyn on 2014-05-02
> **ian-weisser said:**
> I find it hard to imagine that most decade-long XP users want to suddenly roll on the bleeding edge of Ubuntu's development.

Rolling release doesn't necessarily mean "bleeding edge"; it just means that you keep current with regular updates rather than big version upgrades.  For example, SolydXK is a rolling release, but it's based on Debian testing (with additional vetting) so the packages are definitely not bleeding edge.

Basically, think "service packs" rather than "new versions".

That kind of a system could be pretty compelling for users who want to install once and keep it going indefinitely.

---

### Post by 3rdalbum on 2014-05-03
> **lykwydchykyn said:**
> Rolling release doesn't necessarily mean "bleeding edge"; it just means that you keep current with regular updates rather than big version upgrades.  For example, SolydXK is a rolling release, but it's based on Debian testing (with additional vetting) so the packages are definitely not bleeding edge.

Basically, think "service packs" rather than "new versions".

That kind of a system could be pretty compelling for users who want to install once and keep it going indefinitely.

But there will be UI changes. Things will break and things will unbreak. For somebody used to XP, the pace of OS changes will be a shock. People coming from XP probably want to learn a system once and then not have it change for five years or longer.

---

### Post by Eggnog on 2014-05-03
Update packs on rolling release distros can break a system, especially huge update pack offerings.  The last time I checked, LMDE had some pretty large update packs, and there were quite a number of breakage complaints.  Maybe they've solved that issue by now.  SolydXK may be the least likely to break, given that the devs vet everything before release and, if I recall correctly, their update packs occur a little more often and are a bit smaller, but it will probably happen to someone.  And if that someone is coming from XP it will be a terrible experience.  I would still recommend an LTS to someone new to Linux or coming from XP specifically.  In the alternative, I would probably go with SolydX.

---

### Post by lykwydchykyn on 2014-05-03
> **3rdalbum said:**
> But there will be UI changes. Things will break and things will unbreak. For somebody used to XP, the pace of OS changes will be a shock. People coming from XP probably want to learn a system once and then not have it change for five years or longer.

I was mostly making the point that rolling != bleeding edge.  Given the technologies chosen, SolydXK's desktops (KDE and XFCE from Debian) aren't likely to change much over the next five years.

But honestly, assuming too much about what "XP users" will or won't want is a bikeshed argument.

---

### Post by SurfaceUnits on 2014-05-04
XP users want icons to click to launch the 3 or 4 programs they run

---

### Post by LastDino on 2014-05-04
> **SurfaceUnits said:**
> XP users want icons to click to launch the 3 or 4 programs they run

Largely false general statement. ;)

---

### Post by slooksterpsv on 2014-05-05
LMDE for beginners - Its Mint, it uses either MATE or Cinnamon (you can install something else if you'd like post-install). Breakage happened with sound for me on this as well.
Manjaro for Intermedia - Based on Arch is great, but breakage will happen - sound keeps breaking on me.
Arch for advanced - It's arch, it takes a bit to set it up, you really need to read the documentation or thoroughly work through it so you can setup your perfect system. Breakage is to be expected.

---

### Post by SurfaceUnits on 2014-05-05
> **Goten0007 said:**
> Largely false general statement. ;)

An exact specific statement.

---

### Post by monkeybrain20122 on 2014-05-05
I think many of you are making too many assumptions about "beginners". I was a beginner when I switched from XP to Ubuntu 10.04 a few years ago. I DIDN'T want a cheap XP knock off, I wanted my desktop to look beautiful and  different, that was achieved in gnome 2 with Compiz and the Cairo dock. I didn't want same old same old, I didn't want to replicate the "Windows experience", I was looking for something different and better. :)

I think distros that try to replicate Windows' appearence to soften the transition are making a mistakes because that sets up the false expectation for the OS to work like Windows while under the hood it is nothing like that. I would rather tell new users upfront that they are using a different OS and a willingness to learn somehing new is required.

---

### Post by LastDino on 2014-05-05
> **monkeybrain20122 said:**
> I think many of you are making too many assumptions about "beginners". I was a beginner when I switched from XP to Ubuntu 10.04 a few years ago. I DIDN'T want a cheap XP knock off, I wanted my desktop to look beautiful and  different, that was achieved in gnome 2 with Compiz and the Cairo dock. I didn't want same old same old, I didn't want to replicate the "Windows experience", I was looking for something different and better. :)

I think distros that try to replicate Windows' appearence to soften the transition are making a mistakes because that sets up the false expectation for the OS to work like Windows while under the hood it is nothing like that. I would rather tell new users upfront that they are using a different OS and a willingness to learn somehing new is required.

+1

Many people think that XP is used because it gives 3 or 4 icons which is all XP users ever want to use. 

 Lets do the background check: The fact of the matter is (in my gigantic country, at least) that when people go to buy a computer without prior knowledge of it they are *only* offered Windows. And unless it is big branded store smaller ones often sell cracked version of Windows with custom build machine in hide of the selling licenced version, all that only to charge more money or to save cost of the licenced version in their own pockets. XP costs lot less than Win7 ever since it came out, not a hard choice for poor or hard choice for greedy who are used to tweaking XP licence. Normal users never even notice the difference as we all know how much of a fail ''Microsoft genuine check'' is, it only proves to be hindrance to the people who actually pay for licence. Add to that hardware often lives out few OS releases and it is financially impossible for most people from 3rd world countries to spend $ 150+ on OS with each release and sometimes *risk the change* in already established base of working environment. That is human nature. 

In last decade or so, XP was also most used OS  in workplaces and people are naturally prone to use the same OS environment at their home to notch-up their own performance with computer at their work places. Keep in mind that we are talking about the normal users who usually find it difficult to cope up with sudden changes made. 

Then came there some people who are half knowledgeable or have some minor exposure to OS like  Red-hat  and or tried Linux 10 years ago and have established strong biased opinions that Linux = Programmers or server administrators things. While it is certainly not wrong it is certainly not true. But it is definite turn off to people who have no need to know computers that well and don't know the truth beyond the popular opinions. 

All in all, phenomenon of people getting stuck with XP can be related to lot of things, but primarily it comes down to ''that is what they were introduced to'', ''that is what they paid heavily and when you pay that much you expect it to be around for considerable time'' & ''that is what they saw everywhere and needed to know the best  and for that they needed to use it at home''

Now imagine how picture would've been if Linux was as GUI oriented as it is now when XP came out? What would've been the picture if people actually knew it was available choice when they were first introduced to PC? Or how it was no difficult in learning compared to other counterparts like MS and OS X? AND BEST THING, its free and quite easy to jump to next version! It would've been certainly different. 

Commercial software followed the masses as they wanted to make profit by targeting larger user base. They would've taken little different approach if things were different too.


With end of XP and emergence of Win8 (and 8.1) which is as difficult (if not more) to use effectively and learn as it is to shift from XP to Linux, and people finally coming to know benefits of Linux prior to making decisions regarding buying home PC's, things are changing. So, why would you want to drove those users back to things which look like XP? That only makes them think that Linux operate like Windows and that thinking while being true for simple matters it is dreadful in long run. How many times we see people getting turned off because they have no clue what dependencies are and find it tedious to find out when they suddenly need to install something (for a change in course of year or so) which is not easily available or explained? Probably they wont find it as difficult only if they knew what it was or at least came to know about it over period of time rather than just magical appearance of it as some gigantic task, don't you think?  :P 

I went on some serious rant and probably went off the topic in process (not that many will bother to read this black text block), but that is what I think after using XP for 7 years or so and finally completely shifting to Ubuntu. I've been using ubuntu for around 8-9 months and I'm glad to know it is not same as Windows XP or as impractical as Win8. 

/Just my $ 0.2.

---

### Post by SurfaceUnits on 2014-05-06
People who are switching to Linux because of the end of XP support are not looking for a new experience. They want something that will allow them to do what they did on 
X
P.

---

### Post by monkeybrain20122 on 2014-05-06
> **SurfaceUnits said:**
> People who are switching to Linux because of the end of XP support are not looking for a new experience. They want something that will allow them to do what they did on 
X
P.

Well then chances are such users won't stay, not after they have signed up for UF just to post yet another "Linux sux" thread with 0 bean under their names. :) I won't even bother with them.

---

### Post by Tar_Ni on 2014-05-06
> **slooksterpsv said:**
> LMDE for beginners - Its Mint, it uses either MATE or Cinnamon (you can install something else if you'd like post-install). Breakage happened with sound for me on this as well.
Manjaro for Intermedia - Based on Arch is great, but breakage will happen - sound keeps breaking on me.
Arch for advanced - It's arch, it takes a bit to set it up, you really need to read the documentation or thoroughly work through it so you can setup your perfect system. Breakage is to be expected.

Mint is a great distro for beginners but I would recommend Linux Mint XFCE 32bit for a user that wants to replace XP with it. It's lightweight and you've got a software center to install apps and all that can be installed on Ubuntu so Mint XFCE can use. It's an advantage since that gives access to thousand of apps. Adobe flash, Java and media codecs are shipped out-of-the-box.  Beginners will find it much more easier to get what they want, trouble-free. I see no obvious reason to go for LMDE.

My first choice would be Xubuntu or Lubuntu. It's user friendly, a large community ready to help and lots of documents for tweaking purpose can be found online. 3 years of support each for 14.04. All the advantage of Ubuntu on a minimalistic desktop. It's the best for a beginner on low-end hardware.

---

### Post by slooksterpsv on 2014-05-06
Ahh I was meaning if he was looking for a rolling release candidate. I do recommend for those with little to no experience sticking with an LTS release. I must have thought he was asking what was best for a rolling release for those switching from XP. Xubuntu is what i use =D

---

### Post by SurfaceUnits on 2014-05-06
> **monkeybrain20122 said:**
> Well then chances are such users won't stay, not after they have signed up for UF just to post yet another "Linux sux" thread with 0 bean under their names. :) I won't even bother with them.

You have to weed out the weaklings before you begin. Some people I will never change over to Linux because I don't need the drama.

---

### Post by LastDino on 2014-05-06
> **SurfaceUnits said:**
> You have to weed out the weaklings before you begin. Some people I will never change over to Linux because I don't need the drama.

Exactly, but don't you think it could be done better with letting them know exactly what they are getting into rather than making falls impression of something similar to what they were using or are used to?  ;)

---

### Post by SurfaceUnits on 2014-05-06
I don't have that problem

---

### Post by sammiev on 2014-05-06
> **LastDino said:**
> Exactly, but don't you think it could be done better with letting them know exactly what they are getting into rather than making falls impression of something similar to what they were using or are used to?  ;)

Some people have no problems at all. Others do likely due to hardware issues more than any thing else.

---

### Post by robin7 on 2014-05-07
I think it's useful to ask an XP user a lot of questions to help them choose the right distro:

**1. What do you want to use your computer for?**
    Maybe just e-mail and Facebook and the occasional word processing stuff.  Or maybe they are
    into gaming, etc

**2. Are you &#8220;technically challenged&#8221; and just want to keep it simple, or would you like to explore your &#8220;inner geek?&#8221;**
    Maybe they like the idea of learning Linux!  Maybe they're just plain scared like I was.

**3.  How old is your computer and what Operating System did it ship to you with (example: Windows XP or Vista, OSX, etc)? How big is the HDD and how much RAM?**
     Choose a lightweight OS for the older, modest machine.

**4. Do you like &#8220;eye candy&#8221; and pretty special effects on your desktop, or do you prefer a faster, basic desktop with fewer bells and whistles?**
    Even on modest hardware it's possible to have an amazing desktop with active desklets and stuff. Enlightenment is awesome (check out Bodhi Linux).  Even my Xubuntu (on a 10-year-old Dell with 512 RAM) runs nicely with desklets (calender, clock, CPU and RAM monitors)
[IMG]http://myphotos.mypclinuxos.com/images/Artim/xubufebruary.png[/IMG]


**5. Please list your favorite and most-used computer applications (programs).** 
    If I am customizing it for them, I try to categorize Linux applications under headings such as Web Browsing, E-Mail, Music Editing, CD-burning, Office/Word Processing, Photo Editing, etc. A newbie wouldn't know that Thunar is the file manager, so I change it's name on the menu to "File Manager," for example.

**6. Would you like the latest &#8220;bleeding edge&#8221; stuff or do you prefer older, proven, rock-stable programs?**
    "Bleeding edge" is higher risk.  As a general rule I would install only an LTS version for a beginner.  I probably wouldn't even install 14.04 until it was several months old.  But some beginners just have to have the latest and greatest, but they deserve to know there is a higher chance of breakage.


**7. What&#8217;s your favorite color? **
    I customize my installs for Linux novices.  I'll choose theming and wallpaper to match their tastes when possible just for the wow factor. 

**8. How will you connect to the Internet (if applicable)? Dial-up, wifi, Cable**
    This matters a great deal!  Nothing is more frustrating than getting a "brand new" OS that won't do the first thing most people expect.  TEST it first on whatever THEY will use to connect.  Make sure wifi is detected, dialup software installed if needed (except proprietary stuff - only Juno that I know of has really old proprietary software that will run on a debian-based OS).

Of all the rolling-release distros I have personal experience with, I find PCLinuxOS among the "safest," despite the all-or-nothing approach used to keep it updated.  But for a newcomer to Linux I would probably insist on an LTS version of one of the 'buntu flavors.

---

### Post by lhowaf on 2014-05-08
I've been doing a fair number of transitions from XP. About 10% of those are to Linux. Interestingly, all of the Linux convertees were senior citizens. All of the distros used were Ubuntu-based. None of the distros were Ubuntu.
Because of the challenges faced by seniors (diminished visual acuity, unsteady hands, etc), Unity is a non-starter. It is just too difficult for them to try to hit the sweet spots for scroll bars and other UI elements.
They also want a clear paradigm - a desktop. Trying to decipher the appropriate actions in Unity is difficult when there is no strong, unifying paradigm.
It is a shame that the UI designers are so insensitive to the needs of physically-challenged users.
Oh, and I've been using the most stable releases I can find.

---

### Post by LastDino on 2014-05-08
> **lhowaf said:**
> I've been doing a fair number of transitions from XP. About 10% of those are to Linux. Interestingly, all of the Linux convertees were senior citizens. All of the distros used were Ubuntu-based. None of the distros were Ubuntu.
Because of the challenges faced by seniors (diminished visual acuity, unsteady hands, etc), Unity is a non-starter. It is just too difficult for them to try to hit the sweet spots for scroll bars and other UI elements.
They also want a clear paradigm - a desktop. Trying to decipher the appropriate actions in Unity is difficult when there is no strong, unifying paradigm.
It is a shame that the UI designers are so insensitive to the needs of physically-challenged users.
Oh, and I've been using the most stable releases I can find.

Out of curiosity, which are those distros? In both senior citizen case and yours?

---

### Post by robin7 on 2014-05-09
> **lhowaf said:**
> I've been doing a fair number of transitions from XP. About 10% of those are to Linux. Interestingly, all of the Linux convertees were senior citizens. 

My "conversions" are about evenly split between kids who "inherit" their parents' or older siblings' XP box, and seniors who just want to keep in touch with their far-flung families who don't write letters, but have plenty of time to post on social media and blogs and such (guilty as charged). For both groups I think [Xubuntu]("http://xubuntu.org") is ideal. A Xubuntu derivative called [Linux Lite]("https://www.linuxliteos.com/") does what I do, sort of: Change the names of menu items to reflect their function. Firefox is re-labeled, "Web Browser," Thunderbird is re-named "E-Mail," Abiword is "Write a Letter," etc. New folks looking for a file manager can't be blamed for not knowing that it's called Thunar or Dolphin or PCManFM, so I just re-name it in the menu.

> **lhowaf said:**
> All of the distros used were Ubuntu-based. None of the distros were Ubuntu.
Because of the challenges faced by seniors (diminished visual acuity, unsteady hands, etc), Unity is a non-starter. 

I don't know about that, but I only know that Unity is too resource-hungry for use on most of those old XP machines. While I like Lubuntu for that hardware I find it less customizable than Xubuntu and not noticeably faster anyway.  But I'm thinking that LXQt is going to be amazing, so I'm keeping my eye on it while I use Xubuntu in the meantime.

> **lhowaf said:**
> Oh, and I've been using the most stable releases I can find.

Absolutely agreed.  I'm still installing 12.04 for most folks even though the next LTS is out. 14.04 needs to be about a year old or more before I'll even think about installing it for newcomers to Linux.

---

### Post by monkeybrain20122 on 2014-05-09
> **robin7 said:**
> 

Absolutely agreed.  I'm still installing 12.04 for most folks even though the next LTS is out. 14.04 needs to be about a year old or more before I'll even think about installing it for newcomers to Linux.

Well that is way too conservative IMO. If your clients come to me they get new stuffs. :) Not cutting edge but even for ex XP users I would not inflict > 2 year old software on them. In Linux world that is very out of date.They deserve to be more up to date (provided the hardware works of course) 

I don't find LTS to be more stable or usable, the only advantage is that the person who supports it (you ;)) only have to install once and forget about it. I would prefer that too when I install for others, but that is only for my convenience, nothing to do with stability or usability for the users I install Ubuntu for. For such cases I would consider LMDE, Debian testing takes too long to set up and I find Manjaro to be a bit too unstable for new users in my testing (but then it may be because I install stuffs from AUR)

P.S. Unity is not that resource hungry, if machine has a little more than 2G of ram it shouldn't have a problem, usually the issue is not resources, but old graphic cards.

---

### Post by SurfaceUnits on 2014-05-09
[http://www.datamation.com/open-source/50-open-source-replacements-for-windows-xp-1.html](http://www.datamation.com/open-source/50-open-source-replacements-for-windows-xp-1.html)

---

### Post by lhowaf on 2014-05-09
Mostly the most recent Mint or Zorin the computer will support but I remember installing LinuxLikeXP on somebody's slightly decrepit PC. Most of my business is repair of Windows PCs so most of my own run one of the modern flavors of Windows. For the Linux workstation boxes, though, it has been all Zorin of late. I, too, prefer a desktop paradigm.

---

