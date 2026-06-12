---
title: "Fedora LXDE, Linux Mint LXDE or Lubuntu... is there a difference?"
date: 2014-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by tacosdebirri on 2014-03-27
I was wondering if there is a big difference between this three distros. (I'm talking about the current and the next release [the april release] of this distros) (For the Linux Mint, i should say that it would be a Linux Mint XFCE with a LXDE DE installed)
What are the differences?
Which one of them use less resources and have better performance?; why?
If i have a potato for a PC, which one i should use?

Thanks.

---

### Post by bapoumba on 2014-03-27
Moved to Ubuntu, Linux and OS Chat.

---

### Post by PondPuppy on 2014-03-27
My two cents, worth a bit less than two pennies nowadays -- Lubuntu and Mint can use Ubuntu software packages. They're both based on Ubuntu. As far as I know, Fedora uses a different package management system. It's developed by Red Hat, and is the open-source development platform for Red Hat Enterprise Linux. All are good solid distros, I believe.

---

### Post by tacosdebirri on 2014-03-27
But, is one of them better for old PC's? do i get more performance improvements if i use one instead the others? or all of them will have the same requirements, boosts and improvements because they all use LXDE? If this is the case, what should i use? should i try them all and see if i stay with one of them? any suggestion to start with?

---

### Post by lykwydchykyn on 2014-03-27
Usually the big differences between distros come down to:

- Quality of packaging (dependencies, compile options, default configuration, etc)
- Development and release cycle
- Community
- Specialty packages unique to the distro (usually config/management tools, e.g. Mint's software manager, Suse's YAST, etc).

On an average computer you're probably not going to appreciate a significant performance difference between any two distros with the same packages installed.

---

### Post by Ralph L on 2014-03-27
I have an old Compaq Presario 2100.  The only system I could get to run on it was Xubuntu.  I managed to get Nautilus to run on Xubuntu, which I needed to support Access Control Lists.  I use Ubuntu 12.04 on my other computers with Gnome Classic desktop.  So if you have trouble with an old computer give Xubuntu a try.

---

### Post by monkeybrain20122 on 2014-03-27
I dual boot Ubuntu and Fedora, I am not short of resources and both run fast (Unity for Ubuntu and gnome shell for Fedora, this is a very modest refurbished laptop that costs a little less than 300Cad) However, I would say graphic drivers and multimedia stuffs work significantly better in Ubuntu, both in terms of availability of packages and performance. I have done that on machines with different specs and this experience is quite consistent (Nvidia and intel cards, with intel I can get the latest mesa driver from Ubuntu through ppa, there is one in Fedora but it is a mess). 

I may be biased but so far I have encountered nothing that I can do in Fedora but not on Ubuntu, however there are things that I can do easily in Ubuntu but not in Fedora (e.g pipelight in Fedora seems to be consistently broken on two different machines, kazam works beautifully on Ubuntu but barely works on Fedora,--may have to do with gnome shell, and packages I compile easily in Ubuntu is a pain in Fedora due to the absence of certain libraries) I think that are things you can do with Fedora but not Ubuntu, like enterprise things which only support Redhat (e.g revolution R) but I have no need for them on my desktop.

Also if you try Fedora make sure you look up the options in Selinux. By default it blocks a lot of things for 'security' so many things either won't run or get flagged constantly. e.g I got security alert everytime I opened chrome in F19 and google talk just wouldn't run,--and froze up the browser to boot -- until I disabled selinux (though I think that was fixed in F20) 

In  terms of package management I would prefer apt-get to yum. Fedora's delta update is a much talked about achievement, it may be technically very nice but in practice I don't find any advantage. But there is nothing in the yum world that works like autoremove as far as I know. Fedora also doesn't have anything that works like synaptic (yumex is the closest but it is still vastly inferior in terms of searchability and flexibility. Yumex is not default though, Packagekit is, it should be removed immediately upon installation IMO)

Fedora is in general quite stable for delivering the bleeding edge.--as oppose to the mess that is Debian unstable,--, but when a bug hits it can hit you really hard. I have reinstalled Fedora 20  several times for various reasons. First akmod didn't build for the Nvidia driver, then somehow in an update (of systemd?) machine hanged on boot because it was looking for IPV6 connection(?!) while there wasn't any. Maybe I am just lucky, but I have never had to reinstall Ubuntu for something like that (except for the times I broke my system because of my own faults)

While I like to multi boot different Linux distros, when I set up Linux for not very experienced users I will never put Fedora on their machines. These are of course just my own two cents. I am sure others would disagree. :)

---

### Post by tacosdebirri on 2014-03-28
> **Ralph L said:**
> ... So if you have trouble with an old computer give Xubuntu a try.

I gave it a try before i moved to Lubuntu, it wasn't my taste.

> **monkeybrain20122 said:**
> 
... I have reinstalled Fedora 20 several times for various reasons... Maybe I am just lucky, but I have never had to reinstall Ubuntu for something like that (except for the times I broke my system because of my own faults)...


It seems that Fedora it's not my best option then (I have broke Ubuntu so many times that, to what you say, in the moment i put my hands on Fedora, i will break it.)


Doing a little investigation, it seems that Mint is more stable than Ubuntu, though ubuntu have better tools and many other stuff... Which one i should go for then, Lubuntu or Linux Mint LXDE? (I don't talk anymore 'bout performance because it seems that there is no difference between this two about it.)

---

### Post by fantab on 2014-03-28
[Enlightenment]("https://www.enlightenment.org/") is another light DE and you can try it with [BodhiLinux]("http://www.bodhilinux.com/"), which is again based on Ubuntu LTS versions.

---

### Post by Rob Sayer on 2014-03-28
As mentioned, fedora, mint & ubuntu with LXDE would perform similarly.

Need to know the specs in more detail.  There are a number of new members here who want to install ubuntu on an old machine with 64-128 *mega*bytes of RAM.  None of the above full distros will work very well on that.  They're looking at a modern but more primitively featured distro.

I don't have nearly as much experience as some of the above posters but I've used all 3 distros mentioned on my netbook.  Only actually ubuntu with LXDE but there are real differences between them irrespective of the DE.

I agree that Fedora isn't something I'd recommend to newbies.  The software repositories stink compared to ubuntu/debian ones.  It comes with no codecs at all.  There isn't any package manager like Synaptic.  The terminal package manager is powerful but at least in fedora 19 it was broken.  And their support forum is full of pompous asses who act like it's your fault because you didn't read the bugzilla report first.

I could accept that from Gentoo linux.  Not fedora.  Never again.  I consider it RHEL beta.

I wouldn't recommend Mint to new users either.  There's nothing wrong with the distro or desktops I've seen per se but the tech support on their forums is just *awful*.  It's as bad as ubuntu's is good.

Linux works a hell of a lot better than windows but it generally requires more configuring.  Novices don't know how to do this so they need tech support.  No one else comes close to here or askubuntu.

If the computer will run it, I consider ubuntu the only one for real linux newbies.

---

### Post by slooksterpsv on 2014-03-28
Fedora & Codecs? Yeah it does. You just have to install gstreamer plugins to get the codecs to work, usually yum'ing VLC does a bit of this for you.

Mint has stepped away from a lot of what Ubuntu has/does, and they're more based off of Debian than Ubuntu.
Fedora while great, is more suited towards novice/advanced people - though I do admit I like their kernel implementation better, but I always have issues (no matter what version) with the installation (why I don't know - the past 4 versions I've tried to install always fail on different computers too even as a DVD!)

If it's an older machine, definiately Lubuntu poss. elementaryOS
Newer but not as fast (e.g. has HDMI) - Xubuntu or elementaryOS
New - Ubuntu, Ubuntu Gnome, or Kubuntu

---

### Post by slooksterpsv on 2014-03-28
Fedora & Codecs? Yeah it does. You just have to install gstreamer plugins to get the codecs to work, usually yum'ing VLC does a bit of this for you.

Mint has stepped away from a lot of what Ubuntu has/does, and they're more based off of Debian than Ubuntu.
Fedora while great, is more suited towards novice/advanced people - though I do admit I like their kernel implementation better, but I always have issues (no matter what version) with the installation (why I don't know - the past 4 versions I've tried to install always fail on different computers too even as a DVD!)

If it's an older machine, definiately Lubuntu poss. elementaryOS
Newer but not as fast (but has HDMI) - Xubuntu or elementaryOS
New - Ubuntu, Ubuntu Gnome, or Kubuntu

---

### Post by monkeybrain20122 on 2014-03-28
> **slooksterpsv said:**
> Fedora & Codecs? Yeah it does. You just have to install gstreamer plugins to get the codecs to work, usually yum'ing VLC does a bit of this for you.


You have to add the rpmfusion repo first, or you can yum til the second coming and you won't find any non free codecs or vlc. :) So Rob Sayer is correct that Fedora doesn't come with non free codecs, it doesn't even come with vlc or mplayer.

---

### Post by monkeybrain20122 on 2014-03-28
Oh and another thing about Fedora is that since it changes so quickly online tutorials quickly become obsolete. This can be very frustrating if you need to trouble shoot something and nothing you find on google works. For example, I booted into a black screen and the method to get into level3 to fix it doesn't work any more even though if you google you get always the same tutorials and forum posts which work only up to Fedora 19. It turns out you need a different way to boot into level3 because of systemd.

---

### Post by Navneet_Kumar on 2014-03-28
Yup,Fedora is very dynamic.mint and ubntu are the most popular and efficient linux OS.Hope u would stay with the ubuntu community for a long time....:D

---

### Post by monkeybrain20122 on 2014-03-28
> **Rob Sayer said:**
>    And their support forum is full of pompous asses who act like it's your fault because you didn't read the bugzilla report first.
.

Wait til you go to Debian's forum especially if you use Ubuntu. :)
In terms of support I think Ubuntu has the best forum and Arch the best documentation (the Archwiki is awesome)

---

### Post by monkeybrain20122 on 2014-03-28
Speaking of Arch, it is definitely not for beginners, but OP may want to check out Manjaro Linux, it is an Arch based distro, very newbie friendly and very fast and light (with a light desktop like xfce) Since it is Arch based I think it would work well with older machines. The Arch way of installing and managing software (Pacman, yaourt, AUR etc) may take a bit to get used to, but very well documented and Manjaro forum is very newbie friendly
[http://manjaro.org/](http://manjaro.org/) 

Manjaro is a rolling release like Arch which means there is no need to upgrade OS/reinstall after x months, the trade off is that it can be a bit unstable. To remedy that Manjaro holds back on Arch updates so you don't get the bleeding edge as in Arch but the system would be more stable.

Edited:server down for maintenance atm but download button works.

---

### Post by slooksterpsv on 2014-03-28
Odd I don't remember anything about rpmfusion, but then again it's been so long ago since I actually got Fedora to work. Thanks for the info. =D

---

### Post by PondPuppy on 2014-03-28
Of the three distros mentioned in the OP, Lubuntu is probably closest to Ubuntu while keeping it light. I use it on one old machine. 

Manjaro was mentioned -- I like it, and the XFCE version is pretty snappy. So is Salix, based on Slackware and also XFCE. So there you have it: Lubuntu of the Debian Dynasty, Manjaro of the Arch Archistocracy, Fedora of the Red Hat Regency, and Salix of the Slackware Sovereignty. ;)

---

### Post by orb9220 on 2014-03-28
Yep Lubuntu or xfce for older or less performing systems.

Personally moved away from ubuntu based distros moved from Mint 15 KDE to SolydXK that has a great debian based Xfce version.
The nice thing I like about Debian based is a rolling release so no more Clean installs every 6 months or borked dist-upgrades.

Been on the KDE version of SolydXK and it even comes in pretty light at 287mb to desktop and that is with all the bells & whistles.
And Xfce is even lighter. Been doing updates based on Testing branch since Aug 2013 with zero issues and zero need to do a complete reinstall.

[Linux Action Show just did a review on it]("http://youtu.be/ScfVvpyAXpc?t=38m") giving it thumbs up.

And also there is a Ubuntu Xfce version? available?
Good Luck sure you find something that fits your needs.

---

### Post by tacosdebirri on 2014-03-29
Well, i have seen all of your suggestions, and one of them have got my attention: Budhi linux.

It uses the same resources as Lubuntu, BUT, you can customize it even more (Yuss!) No more differences though (Not that catch my attention anyway)

I have also had done a little research in Manjaro and Salix: For Manjaro, there seems there is an LXDE version of it (YES!... that's one of the best DE i know, okay!?) though it's a little bit hard to find the requirements of that distro (Maybe they are the same as all of the other Distros that use LXDE?)
And Salix... there is not a lof of information on the Internet about that distro (Maybe it's my fault because i'm not searching with the correct words?), though, for what i found, it seems it's not the lightest distro. 

Fedora... nope. As stated before, that distro seems to be very problematic, and as stated before by me, i have broken Ubuntu so many times that i would end breaking Fedora in no time.

And last but not the worst, Linux Mint: It's still an option, but with Budhi being one of the lightest and more customizable distros from all of the ones that have been named, it doesn't put Mint in a very good position.

At this point:
Budhi linux>Lubuntu>Linux Mint>Salix and Manjaro (Need more information about them)>Fedora

Thanks for the answers btw.

---

### Post by buzzingrobot on 2014-03-31
> **tacosdebirri said:**
> 

Fedora... nope. As stated before, that distro seems to be very...


At this point:
Budhi linux>Lubuntu>Linux Mint>Salix and Manjaro (Need more information about them)>Fedora

.

Fedora's primary purpose is considerably different than Ubuntu and its derivatives. Before it is anything else, Fedora is a platform to develop and explore new tech for potential inclusion in RHEL. It is fast moving with frequent releases and updates. Ubuntu targets mainstream consumers with a particular focus on new Linux users. Fedora does not.

Both Fedora and Red Hat are adamant about FOSS. Red Hat is also a U.S. corporation, unlike Canonical, and exposed to potential legal issues regarding certain multimedia tools.  For both these reasons, Fedora ships with only open source code.  

For my use, Fedora and Ubuntu are equivalent. I would not, though, suggest Fedora to someone who just wants an attractive out-of-the-box desktop and is not interested in learning what's under the hood.

---

### Post by Allavona on 2014-03-31
While Fedora is all about FOSS it does not necessarily mean that you can't put the things on that are needed to make it 'work.' It really is a simple matter to add the RPMFusion repo to Fedora 20. You need not even use the terminal to install anything, you can use Yum Extender, sort of a Software Center, to install all you need.
There is also Korora Linux. Based on Fedora, it basically is Fedora, but with bells and whistles.

But as with all distros, it comes down to personal taste and preferences.

---

### Post by xxx6 on 2014-04-12
> **tacosdebirri said:**
> Salix and Manjaro 

Those r  **_NOT_** for you! yet...

:p

---

### Post by rare HERO on 2014-11-10
Lubuntu is okay. I use it and I like it.

---

