---
title: "Install Cinnamon and only cinnamon (or... how to create my own distro?)"
date: 2021-08-15
forum: Ubuntu, Linux and OS Chat
---

### Post by dietervansteenw on 2021-08-15
I've posted this question on [AskUbuntu]("https://askubuntu.com/questions/1357963/correct-way-to-install-with-only-cinnamon-and-sddm/1357966") but was sort of nicely told to go elsewhere. One useful reply was to  consider the Ubuntu Cinnamon Remix, but I'm not sure if I can expect the  same frequency of updates.

If the answer would be that I should look in to sort-of compiling my own distro then I'm willing to look in to that.

I'm trying to install a system to my new laptop where I have not too many unused packages installed. An unused DE seems like a lot of wasted space and possibly potential for issues.

What I'd like to accomplish is a system based on ubuntu so that I have (for instance) apt that I know and regular updates (as well as a wide community to search answers in when having issues), but with the Cinnamon DE and SDDM.

I want to avoid installing something like Xubuntu to have a lean system, installing cinnamon and then uninstalling xfce. This seems like a recipe for trouble and just not a correct way.

Should I install Ubuntu server and then manually install Cinnamon? Anything I should pay attention to?

If this

---

### Post by tea for one on 2021-08-15
Are you familiar with Linux Mint Cinnamon Edition?
[https://linuxmint.com/download.php](https://linuxmint.com/download.php)

---

### Post by ajgreeny on 2021-08-15
I do not know from where the Ubuntu-Cinnamon remix gets its packages for the cinnamon DE but I assume it is upstream updates that it uses and everything else would, I think, be from the same Ubuntu repos as every other Ubuntu based distro.

What makes you think that updates will be less frequent if you use the remix?

---

### Post by coffeecat on 2021-08-15
Welcome to the forum.

I don't think you were told to go elsewhere, rather that your question was off-topic for AskUbuntu. Similarly, it is off-topic for where you posted here - [Desktop Environments](https://ubuntuforums.org/forumdisplay.php?f=329) - which is in one of the Ubuntu and official Ubuntu flavours only sections. That being said, we pride ourselves on being a little less restrictive here :wink: and I've moved your question to ***Ubuntu, Linux & OS Chat***

If I was in your position and particularly wanted to use the Cinnamon desktop I would want to avoid the hassle and heartache of building my own system and go the easier route of installing either Ubuntu Cinnamon Remix or Linux Mint edition, both mentioned in your AskUbuntu link. But others may have other views and will be able to offer constructive ideas.

If you do install either of those two distros, please bear in mind that the first two main sections of this forum are reserved for Ubuntu and [the official flavours of Ubuntu]("https://ubuntu.com/download/flavours") only, and that does not include those two. We do have [sub-fora for various other distros]("https://ubuntuforums.org/forumdisplay.php?f=446"), but please note this part of the tagline for that section:

> Please be aware this is not the best place to receive tech support for these OSs/Distros and users should look for official support channels for those systems.

Good luck.

---

### Post by sudodus on 2021-08-15
> **dietervansteenw said:**
> Should I install Ubuntu server and then manually install Cinnamon? Anything I should pay attention to?


I think the advice in the previous answers are relevant and good. Here is my direct answer to your question: It should work well to install Ubuntu server and then manually install Cinnamon with [FONT=Courier New]**apt**[/FONT] (I checked and it is available from Ubuntu's repository [FONT=Courier New]**universe**[/FONT]).

---

### Post by dietervansteenw on 2021-08-15
Thank you all for your (constructive!) feedback.
Yes, the cinnamon remix is mentioned in the SE thread (as well as my initial post here), but I wasn't sure about updates. Likely because I still haven't managed to completely understand what a distro is exactly (But this is likely not the place to continue this question).

To me Ubuntu Server and then install cinnamon (answer from Sudodus confirming that is okay to do) seems the most logical way to stay as close to Ubuntu as possible.

---

### Post by dietervansteenw on 2021-08-15
> **coffeecat said:**
> Welcome to the forum.

I don't think you were told to go elsewhere, rather that your question was off-topic for AskUbuntu. Similarly, it is off-topic for where you posted here - [Desktop Environments]("https://ubuntuforums.org/forumdisplay.php?f=329") - which is in one of the Ubuntu and official Ubuntu flavours only sections. That being said, we pride ourselves on being a little less restrictive here :wink: and I've moved your question to ***Ubuntu, Linux & OS Chat***

I might not always be completely clear in translating my sentiments and questions into words- but I do try.
As far as I understand, being told that my question is off-topic somewhere amounts to politely asking me to go elsewhere. Which I understand if that is the policy. Anyhow, I am glad there are less restrictive places as well :P. Thanks for moving the question.

Still, I don't really think I understand (see also my last reply regarding not really understanding what defines a "distro".). 

* If I take Ubuntu Server and then install a DE myself, is this no longer considered Ubuntu?
* If I take Ubuntu and switch to LXDE (or any other), is that still considered Ubuntu?
* If I take Ubuntu and remove half the packages that come as part of the default DE, is that still Ubuntu?

Maybe I'm trying too hard to draw a hard line on the definition of what a distro is, that's possible as well.

---

### Post by guiverc on 2021-08-15
I'll give some thoughts.

- I don't see any real consequences with installing a Xubuntu and then adding another desktop like Cinnamon. Yes you'll have duplication of packages (*file manager as used by Xfce & another used by Cinnamon, text editor used by Xfce & another text edit used by ...*) however the amount of disk space those packages use is minimal on most disk sizes today; and yes you'll have more packages to update (ie. *more bandwidth used on upgrades*), but it's not that much extra.

- my own desktop is a Ubuntu (thus GNOME) install, on which I've added `xubuntu-desktop` (Xfce) & `lubuntu-desktop` (LXQt now but was LXDE initially) & another I've since removed. I call my box a **Ubuntu** one (even though I'm using Lubuntu/LXQt most of the time).  Adding other window managers, desktops etc doesn't change it from being a Ubuntu *in my opinion anyway*.

- removing packages doesn't generally change what you're using; but beware that *depends* rules can cause effects you didn't expect. eg. `firefox` maybe a requirement for a desktop package. I've recently dealt with a support question where because a user had installed a different browser (*brave*) they were stunned when their desktop was removed on removal of firefox. The *depends* rule mentioned  firefox, firefox-esr (*what Debian provides*) & two other browser as required, but made no mention of 'brave' so it's requirements (*depends*) were no longer present; thus desktop was removed.  You can use [https://packages.ubuntu.com/](https://packages.ubuntu.com/) or commands to view the package rules (*or read what will be removed when you enter the `apt remove` command, and don't answer "y" unless you're happy with what it says will occur*) 

- Adding LXDE to a Ubuntu base system to me would still mean you have a Ubuntu system. LXDE is a rather *strange* choice (GTK2 is *deprecated *now so it's mostly un-patched, and almost no GTK2 apps exist, but yeah there are some); it's no longer what it once was...

***Talking about distribution/distro***

- GNU/Linux (the term I prefer) is a load of projects, Linux refers to the kernel, on which you need the command line & base unix-like system (GNU), on which you put a desktop & other things.  Once this is put together it's called a *distribution*.

Ubuntu is a GNU/Linux distribution.

*Flavors* of Ubuntu ([https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)) just have the default desktop (GNOME for Ubuntu Desktop) switched out and replaced with another one.   The changing of that desktop may also mean other parts fo the *software* stack needs changing out too, eg. 

Ubuntu Desktop uses GNOME which uses GTK3 (toolkit/library).  GNOME apps all share the same toolkit/libraries as used by the GNOME desktop.

Lubuntu uses LXQt desktop which is Qt5 (toolkit/library); Kubuntu likewise uses Qt5 in it's KDE desktop, but KDE also needs KF5 as well.   With the change of toolkits/libraries, the desktop would be inefficient if using apps using GTK3 libs, so the Ubuntu Desktop apps get switched out as well. KDE desktop apps use Qt5 & KF5 (hey it's available & needed for KDE), where as LXQt apps use only Qt5.

XFCE, MATE & other apps share the same toolkits/libraries as GNOME (ie. GTK3), however they still use different libs thus swap out GNOME apps too for ones that are common with the desktop they're designed for (thus why Xfce has different apps to GNOME, different apps to MATE etc).

The LXDE you mentioned is GTK2 (ie.* uses different libraries to the more modern GTK3 apps of most GTK apps today*), so you'll need GTK2 libs for your desktop, plus GTK3 libs for apps when using them, meaning LXDE isn't *efficient* like it was long ago when apps were all GTK2  (*yes it's light & fast; but that's mostly lost if you use GTK3 or Qt5 apps generally; which is much of the time*)

Me - I'm using Lubuntu/LXQt as I already said; but I still use `hexchat` (one of the GTK2 programs) that wouldn't be as efficient as a Qt5 one as it requires GTK2 libs to be in memory; meaning I have multiple libs that do the same thing in RAM at the same time (Qt5 for the desktop, GTK2 for `hexchat`), ie. wasting RAM. It's not a problem on this box, I've enough RAM to do it, thus why I've not switched.

Distributions are built from packages to meet a specific *aim*, which maybe efficiency, looks, overall experience etc.  Some are very *lean* on resources, others value *appearance* over being lean etc; but every decision on what gets included in a *distro* is there for some reason.  Myself I find making a choice of desktop difficult - why my boxes have multiple installed (*which has it's costs too*)

---

### Post by QIII on 2021-08-15
Perhaps this will add some clarity for your questions in #7:

Ubuntu is an operating system distributed by a company named Canonical, LTD, which is based in the UK.  Ubuntu is not a company any more than Windows is.  The former is an OS produced by Canonical, the latter and OS produced by Microsoft.  Canonical recognizes several community-supported "flavors" as described in the flavors link above.  Note the taglines from our first two major forum divisions:  > Choose the most appropriate category for your questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, Ubuntu Studio, Mythbuntu, Ubuntu Mate, Ubuntu Budgie and Ubuntu Kylin.

Quick note:  Edubuntu and Mythbuntu are deprecated and we need to fix the tag line.  Oops.

There is a very detailed process each of those had to go through to be recognized as an official flavor (well, as an aside, Kubuntu actually used to be distributed by Canonical), part of which is that they had to be fully integrated without hiccup into the Ubuntu ecosystem.  Some previous flavors have dropped off the list because they were not maintained.  Canonical is particular about that.

Not everything that calls itself *buntu is recognized as an official flavor.  Some, in fact, are possibly liable for trademark infringement.

I think that may be the distinction that we often fail to explain when we talk about what "Ubuntu" is -- and I hope that implicitly makes that a bit clearer for you.

The upshot is that if you are using anything in that list, you are using what Canonical considers an official flavor of Ubuntu.  Notice from my profile information to the right that I use Kubuntu, and yet I am an Admin on the official Ubuntu Forums.  Kubuntu is a community-maintained flavor of Ubuntu with, among other things like specific apps and components of its stack, KDE as the DE.  Installing Ubuntu and then replacing GNOME with KDE does not make Kubuntu.  It's Ubuntu with the KDE DE.  The maintainers of Kubuntu also include some other software packages that are part and parcel of Kubuntu.  It is more than just replacing the DE.

If you install Ubuntu Server and add Cinnamon, what you will have is Ubuntu Server with the Cinnamon DE.  You won't have a distinctive flavor.  On the Ubuntu Forums, you questions belong in the two major divisions noted above.  There may not be a lot of people familiar with Cinnamon unless they use MINT, but you will still be asking in the right place.  If your question is specific to Cinnamon, we may move your post to Desktop Environments.  However, you will still be in the right place.

If you install MINT with the Cinnamon DE, your questions belong in the MINT sub-forum and we'll move it there if you don't put it there.  Although MINT is *based* on Ubuntu, it is a distinct distro.

I hope I've made that as clear as mud.  :)

---

### Post by monkeybrain20122 on 2021-08-15
> **dietervansteenw said:**
> 

* If I take Ubuntu Server and then install a DE myself, is this no longer considered Ubuntu?
* If I take Ubuntu and switch to LXDE (or any other), is that still considered Ubuntu?
* If I take Ubuntu and remove half the packages that come as part of the default DE, is that still Ubuntu?


What do you care if you just install on your own laptop (rather than distributing it when licensing issues come into play)? Functionally it is Ubuntu and you get the updates upstream so whatever you call it it is Ubuntu. 

As for not installing unneeded packages, there is a  "[minimal install]("https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option")" option in Ubuntu's installer but it includes the DE. Its "mini iso" is a different thing, it just means the installer downloads everything online during installation instead of baking them into the iso, so while the installation medium is small the resulting installation is normal size.

 in [Debian]("https://unix.stackexchange.com/questions/615448/how-to-install-a-minimal-debian") the installer allows you to install a subset of packages and choose a DE, and Arch only has the bare minimum after installation and you have to manually install a DE and most packages yourself after installation, you can practically choose any DE during (Debian) or after (Arch) installation, so if you are comfortable venturing out of Ubuntu land you can try either (Debian tends to be old, debian testing is more up to date, Arch is bleeding edge, debian is of course more familiar for those coming from Ubuntu), but neither is as convenient as Ubuntu and have as good out of the box hardware support.

---

### Post by guiverc on 2021-08-15
> **monkeybrain20122 said:**
> Debian tends to be old, debian testing is more up to date

Now maybe a good time to try Debian; Debian Bullseye is only ~27 hours from it's release so it's packages are somewhat similar in many areas  with my Ubuntu *impish*.

(Debian testing is now *bookworm* with no packages changed other than release name as of last night my local time; AEST)

---

### Post by dietervansteenw on 2021-08-16
All, thank you very much for some very informative and helpful replies. I'll still need time to either 
[LIST]
[*]fully grasp what makes a distro a distro
[*]or let go of the idea that I really want to understand and stop nitpicking
[/LIST]

As a result of the last reply from Guiverc, I found [this ]("https://linuxconfig.org/debian-vs-ubuntu")page which helps me a bit better understand what defines a distribution. Apparently it is also things such as the installer, policies, the people behind it, ... Not just the end result (the ISO).

---

### Post by dietervansteenw on 2021-08-16
> **tea for one said:**
> Are you familiar with Linux Mint Cinnamon Edition?
[https://linuxmint.com/download.php](https://linuxmint.com/download.php)

Yes, I had been made aware of that option. Although I think I am fairly okay-ish with using Linux, I still need to search how to do things (or fix things after I've tried said things). I've always used *buntu kind of distros (or Debian on one type of machines) so I figured it would be best to stay with that for now. I know Mint has a good name but felt that I shouldn't make things harder for myself at the moment and get better at what I'm working with first. Maybe that's a stupid idea...

Actually, I've been thinking of creating my own system based on Yocto for some embedded projects I'm working on. While that would be a lot of trial and error it would probably be rather helpful in understanding what makes a Linux system run and how thing fit together.

Maybe I'll just install Mint Cinnamon Edition on a separate machine or in a VM, which would help me understand what it means to run another distro (Mint instead of Ubuntu) and see what the differences are.

---

### Post by dietervansteenw on 2021-08-16
> **guiverc said:**
> I'll give some thoughts.
*Flavors* of Ubuntu ([https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)) just have the default desktop (GNOME for Ubuntu Desktop) switched out and replaced with another one.   The changing of that desktop may also mean other parts fo the *software* stack needs changing out too, eg. 

That I realized, hence my question "if I take a stock Ubuntu and decide to use something like Cinnamon instead of the stock DE, is it still considered Ubuntu". But once again, that question might just be me making things difficult and not be really relevant.

Apart from that, thanks for the very extensive reply!

---

