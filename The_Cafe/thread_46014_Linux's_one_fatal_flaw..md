---
title: "Linux's one fatal flaw."
date: 2005-07-02
forum: The Cafe
---

### Post by Arktis on 2005-07-02
I think this is the right section for this; I just wanted to point out something about linux in general that I think deserves some discussion. 

The one major problem which has come to my attention (because of ubuntu's main server being down) is that many linux distros (especially highly customized 'flavors' like ubuntu) rely heavily on a central repository. This means that if this centralized repository goes down, not only can you not install the distribution specific packages availible there, but you're going to go through hell when you try and install something from an outside source, because you will find that in many cases you will be unable to satisfy dependancies unless you want to start breaking your system away from it's current branch.

This means that in esscence, if the repository fails, your system is frozen right where it is... which can mean big headaches if you need to install something to get some work done.

Now I ask you : do you find this crippling problem on windows? Well, not really, unless you need a service pack or specific bugfix and maybe windows update goes down. All other dependancy problems have decentralized solutions.

Keep in mind, I've totally ditched windows in favor of linux. I'm not trying to bash ubuntu or linux, just pointing out an issue I think needs serious attention : [b]DECENTRALIZATION.
[/b]

---

### Post by Stormy Eyes on 2005-07-02
I don't see how this is a problem at all. Any distribution that gains any sort of popularity usually has its vital files mirrored on FTP/HTTP sites across the world. More distributions are starting to use BitTorrent to distribute installation media.

---

### Post by Kimm on 2005-07-02
Its not realy an issue in Linux, its acctually more of an issue to how people deside to distribute their software.

I windows most software that need outside libraries have the staticly linked to itselfe, this ofcourse makes it almost impossible to lack something for the program to run properly, in Linux most libraries are mostly aquired separately due to the fact that static linking isnt all to common.

If windows developers didnt work the way they did windows would be very much like any rpm based distro, it would be in "dependency h*ll" and an even worse one at that!

---

### Post by remin8 on 2005-07-02
I think that this is a non-issue because how easy it is to set up a new repository. All you really need is bandwidth and to send the word out on the forums.

---

### Post by Kvark on 2005-07-02
Easy to avoid any problems with this, have lots of mirrors spread out, if one goes down, then clients can connect to any of the others.

But the package manager needs to know how to automatically download from another mirror if the first one tried is down without bothering the user. Think this is the only problem part of it atm. The sources.list file should contain a list of secoundary options for each repo to try if the perfered one is down.

---

### Post by poofyhairguy on 2005-07-02
Three Things:

1. Comparing Windows and Linux in this regard is apples and oranges. Windows doesn't have the THOUSANDS of pieces of COMPLETELY FREE (as in not "if you install our spyware you get it for free" free). We need some way to manage it.

2. I actually like the central repository things. Its quite elegant when you use it a lot. Its probably blows for people on dial up, but its like a computer buffet for me.

3. Other people has complained about decentralization before. No one or nothing can do anything about it. The divides are too deep, the differences are too great now. I personally see it as a strength, but I can see where some people (people who get gridlocked by choice) dislike it. Things will continue to go this way...no matter what anyone does. Its the nature of OSS.

The way I see it....we are lucky we all use the same kernel!!!

I sorry you dislike it. For people that do, I always say "well those Apples and Dells are pretty centralized out of the box..aren't they? Sounds more like you sort of thing." Each to his own and everyone is happy.

---

### Post by davahmet on 2005-07-03
[QUOTE=poofyhairguy]
1. Comparing Windows and Linux in this regard is apples and oranges. Windows doesn't have the THOUSANDS of pieces of COMPLETELY FREE (as in not "if you install our spyware you get it for free" free). We need some way to manage it.
[/QUOTE]
Excellent point.  Anytime someone tries to compare Windows against a Linux distrobution, the first thing overlooked is that when you buy Windows, all you get is Windows.  That would be equivilant to getting only the Linux kernel, some of the device modules (not all because Windows doesn't work out of the box with all hardware), a stripped-down, minimal Gnome and a Web browser.  Now, with a Linux distro like Ubuntu, you get not only the OS and desktop, but an enormous buffet of applications as well as the complete source code and freedom to modify.

This last point is of critical importance, since it is the freedom to modify, copy or distribute that enables anyone to easily clone a package repository.  With this in mind, decentralization is already built into the distribution structure only as a necessity.  What may appear to be a weakness in Linux would actually be a weakness only if Linux were hindered by the same distribution model as Windows.
> 
I sorry you dislike it. For people that do, I always say "well those Apples and Dells are pretty centralized out of the box..aren't they? Sounds more like you sort of thing." Each to his own and everyone is happy.

Yep, and because of the open nature, no one will impair your efforts to improve the software or the distribution system.

---

### Post by Arktis on 2005-07-03
Eh, maybe it was a bad idea to bring up windows. And perhaps the title of this thread should be "ubuntu's oversight". But the point I'm trying to make here is that there ought to be mirrors for the ubuntu repositories. It's a huge oversight not to have this redundancy if only for the reasons I described. I realize that this is free software, but regardless, I won't consider any distro that doesn't have at least two repository mirrors to be a wholely viable choice.

Now... I love ubuntu. Obviously. It's my distro of choice. But this issue is a big one in my opinion. So that's why I bring it up. It's important, and I want to see it addressed. The first step is to bring about awareness of the problem. If enough people would agree, then I believe this would be an issue the developers AND the community will have on their mind.

> I don't see how this is a problem at all. Any distribution that gains any sort of popularity usually has its vital files mirrored on FTP/HTTP sites across the world. More distributions are starting to use BitTorrent to distribute installation media.
I sincerely hope you are right. But I don't see how bittorent would address getting individual packages to satisfy dependancies. That would be impractical in my opinion.

**Edit:**  Oh yeah, thanks for your responses and input.

---

### Post by doclivingston on 2005-07-03
[QUOTE=Arktis]But the point I'm trying to make here is that there ought to be mirrors for the ubuntu repositories. It's a huge oversight not to have this redundancy if only for the reasons I described. I realize that this is free software, but regardless, I won't consider any distro that doesn't have at least two repository mirrors to be a wholely viable choice.[/QUOTE]

Ubuntu does have mirrors of the repository: au.archive.ubuntu.com, us.archive.ubuntu.com, et cetera. I'm not exacty sure if the local one gets automagically chosen when you install, but they exist.

---

### Post by Arktis on 2005-07-03
Really? Excellent! So then how might I add them as alternatives in my sources.list?  Will I have to download their package listings every time I update my listings?  How will synaptec or apt-get choose which mirror to download from?

---

### Post by Sionide on 2005-07-03
If you ask me, the package repositories are Linux's major strength, not weakness or flaw. I've never seen them go offline anyway? And they'd be back within a day and you're only meant to check for updates once a day.

---

### Post by doclivingston on 2005-07-03
[https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) has a listing of the Ubuntu mirrors.

Replacing [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with whichever mirror you want to use in your sources.list should do the trick, I assume that things like au.archive.ubuntu.com work the same way.

---

### Post by Arktis on 2005-07-03
Thanks guys. I'll check those out when ubuntu's website comes back up. I case you didn't know, everything is currently down. Been down for about a day now. Unless for some odd reason it's just me that can no longer access it.  Hmm, maybe google has those pages cached.

---

### Post by UbuWu on 2005-07-03
[QUOTE=Arktis]Thanks guys. I'll check those out when ubuntu's website comes back up. I case you didn't know, everything is currently down. Been down for about a day now. Unless for some odd reason it's just me that can no longer access it.  Hmm, maybe google has those pages cached.[/QUOTE]

I think it is just you... I didn't notice any problems and haven't heard anyone here on the forums complaining... I know there was a problem with the US mirror last week though, which gave people from the US very slow download speeds.

---

### Post by Kvark on 2005-07-03
Most people here missunderstood the thread completely. Arktis thought that there is only one central download server for the repos. He said that when the repos are centralized to one single server, if that server goes down, nobody can install new software from them.

A discussion about linux in general being decentralized is off topic.



The obvious fix is as I said earlier to add all mirrors to everyones sources.list by default in breezy. Then when you download something, the package manager tries the first one, if that fails it tries the next one automatically, and so on.

Even better would be if the package manager split the download into a couple pieces and downloaded the pieces from different mirrors. As a download accellerator does.

---

