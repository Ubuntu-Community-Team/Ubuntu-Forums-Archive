---
title: "What freedom You have on Ubuntu? +Firefox"
date: 2010-01-23
forum: The Cafe
---

### Post by markinf on 2010-01-23
When Firefox 3.6 got out I was looking at this forum about how many users whant to try to use it. What freedom is this where YOU CAN'T **EASILY**, that is they can't update via the software or don't find a .deb, provide a way to install/update a software? You can't use version XYZ of GIMP? Users are in the hands of the developers which is worst than using a prop system.

Think about that.
 
PS: I don't use mainly ubuntu, right know arch / win7
PS2: And both I can update/upgrade WHENEVER I WANT AND EASILY. They don't restrict my freedom.

---

### Post by HoboElectus on 2010-01-23
True, but 3.6 isn't that great.

---

### Post by Ewingo401 on 2010-01-23
This reeks of a troll post, but I'll bite.  You have the freedom to choose.  Ubuntu doesn't try to hide the fact that it's a distro that runs on a six month release cycle.  You get a set of packages that remain essentially the same for 6 months barring major bug fixes or security updates.  If this doesn't work for you there are other distros that might cater to your needs...Arch, sidux, etc.  If Ubuntu doesn't meet your needs you have the CHOICE to use another distro.

---

### Post by Techsnap on 2010-01-23
When he is stating the FACT that it is harder to install on Linux than Windows then how is he a troll. I've used Linux long enough that installing Firefox is not hard but compared to Windows it is a more complicated process and it's as simple as that.

---

### Post by RabbitWho on 2010-01-23
You can do it easily on Arch? Surely the fact that you spent like a month of your life setting it  up far more than makes up for the amount of time it takes someone to figure out how to get 3.6 working for them, if they are so inclined, 3.5.7 does me fine, in fact I  had to check which version I was using just there. 

[img]http://imgs.xkcd.com/comics/perspective.png[/img]

---

### Post by markinf on 2010-01-23
> **RabbitWho said:**
> You can do it easily on Arch? Surely the fact that you spent like a month of your life setting it  up far more than makes up for the amount of time it takes someone to figure out how to get 3.6 working for them, if they are so inclined, 3.5.7 does me fine, in fact I  had to check which version I was using just there. 

[img]http://imgs.xkcd.com/comics/perspective.png[/img]

Good luck on staying on someone version/decision. :~

By the way from what I know the only distros that respect the freedom of choose is arch/crux/gentoo/slack.
The others one are prison of choose.

---

### Post by sliketymo on 2010-01-23
> **markinf said:**
> When Firefox 3.6 got out I was looking at this forum about how many users whant to try to use it. What freedom is this where YOU CAN'T **EASILY**, that is they can't update via the software or don't find a .deb, provide a way to install/update a software? You can't use version XYZ of GIMP? Users are in the hands of the developers which is worst than using a prop system.

Think about that.
 
PS: I don't use mainly ubuntu, right know arch / win7
PS2: And both I can update/upgrade WHENEVER I WANT AND EASILY. They don't restrict my freedom.

Mozilla PPA.,update,install.

---

### Post by HoboElectus on 2010-01-23
> **sliketymo said:**
> Mozilla PPA.,update,install.

Get ugly non-aliased font rendering, purge, and remove Mozilla PPA.

---

### Post by Xbehave on 2010-01-23
> **Techsnap said:**
> When he is stating the FACT that it is harder to install on Linux than Windows then how is he a troll. I've used Linux long enough that installing Firefox is not hard but compared to Windows it is a more complicated process and it's as simple as that.
It's almost the same.
1) go to mozilla website
2) download firefox
3-linux) unpack tar
3-windows) run exe
4) link /usr/bin/firefox to the firefox exe

Or you can do it the easy way by adding ppa:ubuntu-mozilla-daily/ppa (granted this gives you daily 3.6 builds not just official releases)

**obvious troll is obvious**, because you are always free to install any software to ubuntu. Even if it is not in the repos by default, nobody is going to stop you installing software in (hell that's what /usr/local and /opt directories are for and /usr/local will override /usr by default)

---

### Post by Techsnap on 2010-01-23
Right lets see:

Windows:
1. Mozilla Site
2. Download
3. Run the exe

Linux (Ubuntu Specifically): 
1. Uninstall old Firefox on Ubuntu.
2. Mozilla Site
3. Download
4. su
5. tar -xvf [filename]tar.gz /usr/lib/firefox
6. ln -s /usr/lib/firefox/firefox /usr/bin/firefox
7. Create Launchers & Exit root.
8. If you have an older version of Ubuntu, track down dependencies. 

Yeah you're right it's easier.

---

### Post by markinf on 2010-01-23
> **HoboElectus said:**
> Get ugly non-aliased font rendering, purge, and remove Mozilla PPA.

Or have no support for x64.

---

### Post by RabbitWho on 2010-01-23
> **Techsnap said:**
> Right lets see:


Linux (Ubuntu Specifically): 
1. Uninstall old Firefox on Ubuntu.
2. Mozilla Site
3. Download
4. su
5. tar -xvf [filename]tar.gz /usr/lib/firefox
6. ln -s /usr/lib/firefox/firefox /usr/bin/firefox
7. Create Launchers & Exit root.
8. If you have an older version of Ubuntu, track down dependencies. 



Ah ha! Now I see the problem! you don't know what you're doing! :D

---

### Post by Techsnap on 2010-01-23
I've used Linux for 8 damn years, I do know what I'm doing. Please tell me what I didn't do right?

---

### Post by HoboElectus on 2010-01-23
> **Techsnap said:**
> I've used Linux for 8 damn users, I do know what I'm doing. Please tell me what I didn't do right?

8 users?

Multiple personality disorder?

---

### Post by Xbehave on 2010-01-23
> **Techsnap said:**
> 
Linux (Ubuntu Specifically): 
1. Uninstall old Firefox on Ubuntu.
2. Mozilla Site
3. Download
4. su
5. tar -xvf [filename]tar.gz /usr/lib/firefox
6. ln -s /usr/lib/firefox/firefox /usr/bin/firefox
7. Create Launchers & Exit root.
8. If you have an older version of Ubuntu, track down dependencies. 

Yeah you're right it's easier.
[LIST]
[*]ubuntu uses sudo not su (so drop 4)
[*]you can drop 1 (and if you do then you can drop 7,8 )
[*]If you do uninstall firefox then 8 is trivial as you can run apt-cache depends firefox-3.5 to get the dependencies (the min version on the dependencies is quite low, so i think you would have to be running an unsupported ubuntu version to have any issues)
[*]you only need to do 6 or 7, you don't need to do both.
[*]you shouldn't install unmaintained (by apt) software to /usr/lib [nobody will stop you though]
[*]you have to exit the installer in windows too
[/LIST]. so it's really as i said
1) Mozilla site
2) Download
3) sudo tar -xf [filename] /opt (or just tar -xf to install to home [bad idea but like i said nobody is gonig to stop you])
4) ln -s /opt/firefox/firefox /usr/bin/firefox OR create gui launchers to /opt/firefox/firefox

> **markinf said:**
> Or have no support for x64.
Windows has no x64 firefox, so your x86_64 would be installed in a similar way to x86_64 for linux (downloading the build and installing it yourself)

---

### Post by Techsnap on 2010-01-23
> ubuntu uses sudo not su (so drop 4)

Oh yeah I forgot about Ubuntus ridiculous reliance on sudo.

---

### Post by Xbehave on 2010-01-23
> **Techsnap said:**
> Oh yeah I forgot about Ubuntus ridiculous reliance on sudo.
It's not a reliance it's a design choice, you can remove it if you wish but don't let your lack of knowledge about ubuntu  stop you making stuff up about it.

---

### Post by RabbitWho on 2010-01-23
> **Techsnap said:**
> Oh yeah I forgot about Ubuntus ridiculous reliance on sudo.

You're (blatantly) not familiar with Ubuntu you mean.

Troll.

---

### Post by #11u-max on 2010-01-23
> **Techsnap said:**
> Oh yeah I forgot about Ubuntus ridiculous reliance on sudo.
and i forgot about windows rediculous usability ;)

:popcorn:

---

### Post by madnessjack on 2010-01-23
I wish people would stop pointlessly arguing. The fact is, Firefox is easy to install on Ubuntu, and you have the freedom to do it.

You just don't know how

---

### Post by Techsnap on 2010-01-23
Edit: Never mind.

---

### Post by aysiu on 2010-01-23
One of the things I tired of in Windows is constantly having to manually update each individual program (many of which requiring or at least recommending a reboot afterwards).

One of the things I love about Ubuntu is the fact that all the updates are centralized (using repositories), and every six months, everything gets a new version.

Ubuntu never makes false promises about being a rolling release distro. If you want that, you have the freedom to use one (Debian Unstable, PCLinuxOS, Arch).

I don't see what the problem is here.

Not to mention that if you're not using 64-bit, UbuntuZilla makes it extremely easy to always have the latest stable Mozilla Firefox as soon as it comes out.

---

### Post by HoboElectus on 2010-01-23
> **madnessjack said:**
> I wish people would stop pointlessly arguing. The fact is, Firefox is easy to install on Ubuntu, and you have the freedom to do it.

You just don't know how

Have you ever installed a new version of Firefox on Ubuntu?

---

### Post by lisati on 2010-01-23
> **markinf said:**
> When Firefox 3.6 got out I was looking at this forum about how many users whant to try to use it. What freedom is this where YOU CAN'T **EASILY**, that is they can't update via the software or don't find a .deb, provide a way to install/update a software? You can't use version XYZ of GIMP? Users are in the hands of the developers which is worst than using a prop system.

Think about that.
 
PS: I don't use mainly ubuntu, right know arch / win7
PS2: And both I can update/upgrade WHENEVER I WANT AND EASILY. They don't restrict my freedom.

Perhaps the solution lies in getting involved. It might need to be much, but every little bit of help and supporty **can** make a difference.

---

### Post by cariboo on 2010-01-23
It's time for you users of other distributions to learn something new. Go to System--> Administration-->Software Sources, click the Other Software Tab, click the add button and type:

```
ppa:ubuntu-mozilla-daily/ppa 
```

Once you have updated the sources list, you can install firefox the normal Ubuntu way.

There are plenty of other posts with links to the same method here in the forums, so this shouldn't be such an ordeal as the users of other distributions are trying to make of it.

---

### Post by aysiu on 2010-01-23
> **cariboo907 said:**
> It's time for you users of other distributions to learn something new. Go to System--> Administration-->Software Sources, click the Other Software Tab, click the add button and type:

```
ppa:ubuntu-mozilla-daily/ppa 
``` Why *type* when you can *copy and paste*?

By the way, I'd recommend UbuntuZilla for non-64-bit systems. It uses only the stable Mozilla releases instead of the daily builds.

---

### Post by HoboElectus on 2010-01-23
> **aysiu said:**
> Why *type* when you can *copy and paste*?

Why not stick with what's stable and works?

---

### Post by aysiu on 2010-01-23
> **HoboElectus said:**
> Why not stick with what's stable and works?
You can do that as well. In fact, that's what I recommend for Ubuntu users. Stick with the regular repos and get security updates until the next Ubuntu release, which will feature the newest Firefox at that time.

My point, which you quoted out of context, is that if you **are** going to go for unstable daily builds of Firefox, it's easier to copy and paste a string of text than to retype it (also less room for user error).

---

### Post by madnessjack on 2010-01-23
> **HoboElectus said:**
> Have you ever installed a new version of Firefox on Ubuntu?

No, because I don't care for it! But I'm sure if I spent 10 minutes with my friend Google I could put in some effort figuring it out and learning. Heck, admins are even spelling it out for us in this very thread :D

---

### Post by squilookle on 2010-01-23
Neither Ubuntu, Arch or any other distro restrict you. I run Arch on my laptop now and am still usng firefox 3.5.7. 

I was using the most up to date version of Firefox on Ubuntu for a long time - I downloaded it from the Mozilla site and just extracted it to my home directory, and pointed the launchers on my desktop at the up to date binary. 

It was no harder or longer than installing Firefox on Windows - and I therefore had as much freedom as I had on Windows.

---

### Post by HoboElectus on 2010-01-23
> **madnessjack said:**
> No, because I don't care for it! But I'm sure if I spent 10 minutes with my friend Google I could figure it out. Heck, admins are even spelling it out for us in this very thread :D

They also aren't listing some of the problems.

---

### Post by markinf on 2010-01-23
> **aysiu said:**
> One of the things I tired of in Windows is constantly having to manually update each individual program (many of which requiring or at least recommending a reboot afterwards).

One of the things I love about Ubuntu is the fact that all the updates are centralized (using repositories), and every six months, everything gets a new version.

Ubuntu never makes false promises about being a rolling release distro. If you want that, you have the freedom to use one (Debian Unstable, PCLinuxOS, Arch).

I don't see what the problem is here.

Not to mention that if you're not using 64-bit, UbuntuZilla makes it extremely easy to always have the latest stable Mozilla Firefox as soon as it comes out.

Well the problem is that you can't easily install a updated version of a software like on windows or arch/gentoo/slack/crux. You are stuck there, unless someone build a ppa that works or generate some debs, you best bet is to compile and pray to not break the system.

> **cariboo907 said:**
> It's time for you users of other distributions to learn something new. Go to System--> Administration-->Software Sources, click the Other Software Tab, click the add button and type:

```
ppa:ubuntu-mozilla-daily/ppa 
```

Once you have updated the sources list, you can install firefox the normal Ubuntu way.

There are plenty of other posts with links to the same method here in the forums, so this shouldn't be such an ordeal as the users of other distributions are trying to make of it.

Are you serious? Do you think I'm retarded or something like it? LOL.
Mozilla PPA has major problems specially with fonts.
The question is that ubuntu philoshy view engages you onto a 6 month of no choice. You have their choice. Unless the software you use has a ppa that actually works, you are restricted to their choice. ON windows and arch/gentoo/slack/crux you can update on your terms and when you want.

---

### Post by ElSlunko on 2010-01-23
You're stating one issue and applying it to something unrelated. Ubuntu's update cycle has **nothing** to do with freedoms. You might as well blame ubuntu for 9/11 because it doesn't have native photoshop.

---

### Post by ElSlunko on 2010-01-23
Manual installs are easy by the way. And boatloads safer.

---

### Post by Xbehave on 2010-01-23
> **HoboElectus said:**
> They also aren't listing some of the problems.
Such as? Doing exactly what was described in this thread (twice), is how i used firefox for years (it even lets you keep the same firefox accross distros if you have a separate /opt), I never had any problems.

ppa:ubuntu-mozilla-daily/ppa

or running

```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```

are even easier and have the benefit of using apt for updates.

---

### Post by lovinglinux on 2010-01-23
Not again please.....

Hopefully threads like this won't show up in the near future.

Firefox update policy has changed and we will get major-minor updates from official repositories.  Read these please:

[http://ubuntuforums.org/showpost.php?p=8706725&postcount=343](http://ubuntuforums.org/showpost.php?p=8706725&postcount=343)
[http://ubuntuforums.org/showpost.php?p=8707213&postcount=347](http://ubuntuforums.org/showpost.php?p=8707213&postcount=347)
[http://ubuntuforums.org/showpost.php?p=8708092&postcount=43](http://ubuntuforums.org/showpost.php?p=8708092&postcount=43)

If you install Firefox 3.6 from the PPA you will notice that...

[LIST]
[*]Firefox does not require xulrunner anymore.
[*]You can't install firefox-3.6 side-by-side with firefox-3.5. Instead, it updates the old default version to 3.6.
[/LIST]

---

### Post by aysiu on 2010-01-23
> **markinf said:**
> Well the problem is that you can't easily install a updated version of a software like on windows or arch/gentoo/slack/crux. You are stuck there, unless someone build a ppa that works or generate some debs, you best bet is to compile and pray to not break the system. I don't see that as a problem. I don't mind having automatic security updates and then getting newer versions of software in six months.

As I said before, this is what Ubuntu is *supposed* to be like by design. It isn't a problem.

If **you** consider a problem, then you **should** use Arch, PCLinuxOS, Debian Unstable, or some other rolling release distro. Ubuntu is not a rolling release distro, and it isn't meant to be one.

By the way, you can ignore this if you want to, but you do not have to compile anything to get the Mozilla build of Firefox installed on Ubuntu. You can paste three commands into the terminal to get the [UbuntuZilla](http://ubuntuzilla.sourceforge.net) repositories enabled. Once those are enabled, you'll get regular updates to the Firefox stable builds every time they come out. (I've provided [GUI instructions, too, for adding the UbuntuZilla repositories](http://www.psychocats.net/ubuntu/ubuntuzilla), though they're not as simple as copying and pasting commands.)

What you're basically arguing is that a motorcycle's "problem" is that it has only two wheels. Well, a motorcycle is *supposed* to have two wheels. If you want four wheels, get a car. Ubuntu is *supposed* to get new software every six months. If you want a rolling release distro, use a rolling release distro, not Ubuntu.

---

### Post by SuperSonic4 on 2010-01-23
> **cariboo907 said:**
> It's time for you users of other distributions to learn something new. Go to System--> Administration-->Software Sources, click the Other Software Tab, click the add button and type:

```
ppa:ubuntu-mozilla-daily/ppa 
```

Once you have updated the sources list, you can install firefox the normal Ubuntu way.

There are plenty of other posts with links to the same method here in the forums, so this shouldn't be such an ordeal as the users of other distributions are trying to make of it.

A daily version as the name implies - much different from a *stable* version of Firefox. For a distro that defines itself as outdated by using discrete release cycles may not be what be what many users would want

Installing firefox on arch is simpler than on ubuntu ```
su -c 'pacman -S firefox'
``` or ```
sudo pacman -S firefox
```. Maintaining Arch is not as difficult as fixed-released distros imply

@:Techsnap. Don't forget unofficial rule 1: If you mention faults with ubuntu you're a troll. Also how does Slackware compare to Arch in package management and releases?

---

### Post by HoboElectus on 2010-01-23
> **Xbehave said:**
> Such as?

Non-aliased fonts
Plugin incompatibilities
Crashes a lot
Flash grey boxing

Those are the main problems, but there are sometimes others as well.

---

### Post by k64 on 2010-01-23
I agree with the OP that users are at the hands of developers. If you don't know C++, you're screwed. That's really the mentality with Linux.

That said, it really pays to have a UI designer.

Edit: However, it also really pays to have a stable repository. That way, you can really know what to expect.

---

### Post by Zoot7 on 2010-01-23
Download the tarball from the mozilla site, extract it to somewhere (/opt IMO is the best), then
```
chown -R $USER:$USER /opt/firefox
```
Then create a Launcher on the desktop and point it to /opt/firefox/firefox.

Then, you can check for updates the same way you do in Windows (Help -> Check for Updates).
I nearly always do this myself because in most distros I find the firefox from the site that's free of dependencies is always a lot faster.
 
Anyway, it's not hard *per se*, but it's certainly a lot more convoluted and it's hardly the actions one would have to take in a so called "User Friendly" OS.

---

### Post by mikewhatever on 2010-01-23
> **markinf said:**
> When Firefox 3.6 got out I was looking at this forum about how many users whant to try to use it. What freedom is this where YOU CAN'T **EASILY**, that is they can't update via the software or don't find a .deb, provide a way to install/update a software? You can't use version XYZ of GIMP? Users are in the hands of the developers which is worst than using a prop system.

Think about that.
 
PS: I don't use mainly ubuntu, right know arch / win7
PS2: And both I can update/upgrade WHENEVER I WANT AND EASILY. They don't restrict my freedom.

It was easy for me, but regardless, who said 'freedom' equals 'easy for everyone'? Even in real life, it's actually easier to be a slave, follow a known set of rules, never need to decide, etc.
So to summarize, wrong logic --> wrong conclusion.

---

### Post by aysiu on 2010-01-23
> **SuperSonic4 said:**
> 
@:Techsnap. Don't forget unofficial rule 1: If you mention faults with ubuntu you're a troll. I mentioned a couple of Ubuntu faults just the other day, and no one called me a troll:
[http://ubuntuforums.org/showthread.php?p=8707017#post8707017](http://ubuntuforums.org/showthread.php?p=8707017#post8707017)

Maybe it's more about criticizing Ubuntu for a fault that isn't really a fault. Legitimate criticism, good. Illegitimate criticism, trolling.

Your baseless assertion makes about as much logical sense as "I'm rubber, and you're glue, whatever you say bounces off me and sticks to you." It also makes *any* criticism of Ubuntu (valid or invalid) excusable by saying "Well, if you have a problem with it, you just can't take criticism."

The truth is that saying Ubuntu limits your freedom by having a six-month release cycle is ridiculous. Saying Ubuntu is faulty for having hardware support regressions (wireless card works in version X of Ubuntu and then doesn't work in version X+1 of Ubuntu) is a valid criticism.

Here are some of the other faults I've found in Ubuntu. Let's see how many people call me a troll:
[My top ten favorite Ubuntu Brainstorm usability ideas](http://www.psychocats.net/ubuntucat/brainstormtopten/)
[The Top 5 Gnome/Ubuntu Usability Bugs I&#8217;d Love to See Fixed](http://www.psychocats.net/ubuntucat/the-top-5-gnomeubuntu-usability-bugs-id-love-to-see-fixed-2/)

---

### Post by Xbehave on 2010-01-23
> **markinf said:**
> Well the problem is that you can't easily install a updated version of a software like on windows or arch/gentoo/slack/crux. You are stuck there, unless someone build a ppa that works or generate some debs, you best bet is to compile and pray to not break the system.
You can, we've given 3 different ways to do this, so you're either trolling or to stupid to installing a tar **or** using the daily ppa **or** run a single command ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```
My money is on that you're trolling

> Are you serious?
yes
> Do you think I'm retarded or something like it?
No comment
> Mozilla PPA has major problems specially with fonts.
It has problems? or you're to busy trolling to figure out how to get fonts working on your install?
> The question is that ubuntu philoshy view engages you onto a 6 month of no choice. You have their choice. Unless the software you use has a ppa that actually works, you are restricted to their choice. 
by my count you have 4 choices
1) Stick with ubuntu version 
2) Find a ppa/repo (there are at least 2 listed in this thread)
3) Install binary tar and update yourself
4) Compile from source

> ON windows and arch/gentoo/slack/crux you can update on your terms and when you want.
Only if you want an unsecured machine, otherwise you have to constantly update to get secure versions.

---

### Post by HoboElectus on 2010-01-23
> **Xbehave said:**
> [QUOTE=markinf;8712738]Well the problem is that you can't easily install a updated version of a software like on windows or arch/gentoo/slack/crux. You are stuck there, unless someone build a ppa that works or generate some debs, you best bet is to compile and pray to not break the system.[/quote[
You can, we've given 3 different ways to do this, so your either trolling or to stupid to installing a tar **or** using the daily ppa **or** run a single command ```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
```My money is on that you**_'re_** trolling


yes

No comment

It has problems? or you_**'re**_ to_**o**_ busy trolling to figure out how to get fonts working on your install?
 
by my count you have 4 choices
1) Stick with ubuntu version 
2) Find a ppa/repo (there are at least 2 listed in this thread)
3) Install binary tar and update yourself
4) Compile from source


Only if you want an unsecured machine, otherwise you have to constantly update to get secure versions.

:popcorn:

---

### Post by aysiu on 2010-01-23
> **k64 said:**
> I agree with the OP that users are at the hands of developers. If you don't know C++, you're screwed. That's really the mentality with Linux. I don't know C++ or any programming language. Somehow I manage just fine.

More details here:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

---

### Post by AllRadioisDead on 2010-01-23
> **k64 said:**
> I agree with the OP that users are at the hands of developers. If you don't know C++, you're screwed. That's really the mentality with Linux.

That said, it really pays to have a UI designer.

Edit: However, it also really pays to have a stable repository. That way, you can really know what to expect.
What are you smoking?

---

### Post by ElSlunko on 2010-01-23
I don't know programming either! Just move the dang folder into opt! You don't even need to compile anything... That's how you install stuff on OSX. I just wish you could drag and drop the folder into /opt and it would prompt you for a password. That and only that alone would make things as easy as popular OS's.

---

### Post by Xbehave on 2010-01-23
> **k64 said:**
> I agree with the OP that users are at the hands of developers. If you don't know C++, you're screwed. That's really the mentality with Linux.
1) much of ubuntu uses python
2) most libraries have python/java/ruby binding
3) You can customise most of Linux by modifying the shell scripts
4) the kernel, GTK (and I believe most of gnome gnome) are written in C, not C++

---

### Post by chewearn on 2010-01-23
> **k64 said:**
> I agree with the OP that users are at the hands of developers. If you don't know C++, you're screwed. That's really the mentality with Linux.

Mmm... if you are not a programmer, you are always... always in the hands of developers.

Or did I missed something important, like how software actually grew from trees? ;)

---

### Post by mikewhatever on 2010-01-23
> **Techsnap said:**
> Right lets see:

Windows:
1. Mozilla Site
2. Download
3. Run the exe

Linux (Ubuntu Specifically): 
1. Uninstall old Firefox on Ubuntu.
2. Mozilla Site
3. Download
4. su
5. tar -xvf [filename]tar.gz /usr/lib/firefox
6. ln -s /usr/lib/firefox/firefox /usr/bin/firefox
7. Create Launchers & Exit root.
8. If you have an older version of Ubuntu, track down dependencies. 

Yeah you're right it's easier.

Man, you are funny and your confidence is appalling. Just by running the exe, I get a prompt asking if I want to run it, nothing else.

---

### Post by lovinglinux on 2010-01-23
> **HoboElectus said:**
> Non-aliased fonts

I don't have any font problems whatsoever. Although some users are suffrering with this problem, the majority is not.

> **HoboElectus said:**
> Plugin incompatibilities

I guess you are talking about extensions, because plugins compatibility as far as have notice is only a problem with 64bit, but that's another story.

If you really are talking about extensions, then you don't understand how it works. Extensions depend on third-party authors to be updated. Nevertheless, you can override compatibility with [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003?src=external-fxfirstrun) and help the developers by reporting which works and which doesn't.

BTW, I have 53 extensions installed. Most are already compatible and most of the remaining still works with compatibility check disabled.

> **HoboElectus said:**
> Crashes a lot

Not here. In fact, I haven't had any crashes yet. Perhaps you have a corrupted profile, bad hardware or are simply accessing pages with bad content.

> **HoboElectus said:**
> Flash grey boxing

Have you removed all flash plugins except the one from adobe? Are you using the correct plugin for your system (32 or 64bit)?

---

### Post by mikewhatever on 2010-01-23
> **ihermit said:**
> What are you smoking?

:lolflag:

You need to learn assembler to make a folder in Linux.:lol:

---

### Post by HoboElectus on 2010-01-23
> **lovinglinux said:**
> I don't have any font problems whatsoever. Although some users are suffrering with this problem, the majority is not.



I guess you are talking about extensions, because plugins compatibility as far as have notice is only a problem with 64bit, but that's another story.

If you really are talking about extensions, then you don't understand how it works. Extensions depend on third-party authors to be updated. Nevertheless, you can override compatibility with [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003?src=external-fxfirstrun") and help the developers by reporting which works and which doesn't.

BTW, I have 53 extensions installed. Most are already compatible and most of the remaining still works with compatibility check disabled.



Not here. In fact, I haven't had any crashes yet. Perhaps you have a corrupted profile, bad hardware or are simply accessing pages with bad content.



Have you removed all flash plugins except the one from adobe? Are you using the correct plugin for your system (32 or 64bit)?

I have tried updating Firefox on about 7 different PCs. They all have these kinds of problems.

---

### Post by SuperSonic4 on 2010-01-23
> **aysiu said:**
> I mentioned a couple of Ubuntu faults just the other day, and no one called me a troll:
[http://ubuntuforums.org/showthread.php?p=8707017#post8707017](http://ubuntuforums.org/showthread.php?p=8707017#post8707017)

Not in that post you didn't. Wait, you mentioned focussing which is a DE fault as you freely admit rather than an ubuntu problem.

> Maybe it's more about criticizing Ubuntu for a fault that isn't really a fault. Legitimate criticism, good. Illegitimate criticism, trolling.

For it's target audience, ubuntu does have an astonishing reliance on sudo. Don't get me wrong, sudo is an excellent idea but having the root account active makes certain tasks easier especially fixing sudo.

> 
Your baseless assertion makes about as much logical sense as "I'm rubber, and you're glue, whatever you say bounces off me and sticks to you." It also makes *any* criticism of Ubuntu (valid or invalid) excusable by saying "Well, if you have a problem with it, you just can't take criticism."

I never meant that, while my original statement was largely hyperbole it does remain true that should an OP raise a negative point about ubuntu (and they are not staff) they are branded trolls. I know staff cannot patrol 24/7 but acquiescence is akin to condoning it on more than a few occasions.

> The truth is that saying Ubuntu limits your freedom by having a six-month release cycle is ridiculous. Saying Ubuntu is faulty for having hardware support regressions (wireless card works in version X of Ubuntu and then doesn't work in version X+1 of Ubuntu) is a valid criticism.

Didn't say that. I said that due to having six-month release cycles it's possible to be using out of date software for six months. Sure you can add a PPA or you can compile from source - the latter rendering apt useless.

> Here are some of the other faults I've found in Ubuntu. Let's see how many people call me a troll:
[My top ten favorite Ubuntu Brainstorm usability ideas](http://www.psychocats.net/ubuntucat/brainstormtopten/)
[The Top 5 Gnome/Ubuntu Usability Bugs I’d Love to See Fixed](http://www.psychocats.net/ubuntucat/the-top-5-gnomeubuntu-usability-bugs-id-love-to-see-fixed-2/)

Like people are going to call staff trolls :rolleyes:

---

### Post by Warpnow on 2010-01-23
With greater freedom, and greater options, **always** comes greater complexity. It is impossible to have it any other way. When you increase an option, you increase a query. Ubuntu has ALOT more options than windows...hell you can compile Firefox from source on a day to day basis for the most up to date code, which you can't do in windows, but with greater options, comes difficulty.

Freedom has nothing to do with ease. In fact, things are almost always easier when you have few freedoms. This is universally true if you take things ceteris paribus.

---

### Post by azagaros on 2010-01-23
Its funny reading through this thread.  reeking of Trolls a good way to put it but I gave up on IE and Mozilla over a year ago and went to Chrome on both platforms and never looked back.

---

### Post by Xbehave on 2010-01-23
> **SuperSonic4 said:**
> I never meant that, while my original statement was largely hyperbole it does remain true that should an OP raise a negative point about ubuntu (and they are not staff) they are branded trolls. I know staff cannot patrol 24/7 but acquiescence is akin to condoning it on more than a few occasions.
OP is a troll though, his claim that ubuntu is limiting your freedom is ridiculous and even after people have explained how it's not true, he keeps insisting that it is.

> Didn't say that. I said that due to having six-month release cycles it's possible to be using out of date software for six months.
It depends how you define out of date, [55% of arch is out of data]("http://oswatershed.org/") (and arch is the most up to date linux distro)

> Sure you can add a PPA or you can compile from source - the latter rendering apt useless.
If you use checkinstall, the package is installed using dpkg so it can still be removed using apt (and I think you can also verify it using debsums), but yes you do make apt fairly useless.

---

### Post by lykwydchykyn on 2010-01-23
Suprised nobody moved this in recurring discussions yet.  This software installation thing comes up all the time.

What people always seem to miss is that Mozilla took time and effort to write an installer for Windows, but for Linux just chucked a static binary in a tarball.

They could have at least made an "install.sh" script that copied the binaries to /opt and put a link in /usr/local/bin (like GoogleEarth).  Or They could have offered static debs and rpms (like OpenOffice.org).  Or they could have done any number of other things to make installation point-and-click a-la Windows.  But they didn't.

Yet, somehow, this is Ubuntu's fault.

As for it not being in the repos -- look at the threads going on right now:

user1:  Firefox 3.6 is out!  Whenzit gonna be in the repos???
user2:  Probably not 'til Lucid, though there might be a backport in a week or two.
user1:  What???? It's out for Windows NOW!!!!! BAWWWWWWWWWWW!!!!
user2:  Well you can get it through method1 method2 or method3.
user1:  OK! DOING THAT NOW!11

user1: ZOMG!! JAVA BROKE!! FONTS BORKSED!! FLASH BROSKEDERD!w1@#  UBNUTTU BAWWWWWWWWWWWWWWWWWWWW!!!!!!!!!

Gee, I wonder why it's not in the repos NOW NOW NOW.

---

### Post by NCLI on 2010-01-23
> **SuperSonic4 said:**
> A daily version as the name implies - much different from a *stable* version of Firefox. For a distro that defines itself as outdated by using discrete release cycles may not be what be what many users would want

Installing firefox on arch is simpler than on ubuntu ```
su -c 'pacman -S firefox'
``` or ```
sudo pacman -S firefox
```. Maintaining Arch is not as difficult as fixed-released distros imply

@:Techsnap. Don't forget unofficial rule 1: If you mention faults with ubuntu you're a troll. Also how does Slackware compare to Arch in package management and releases?

How is that easier than the way you do it in Ubuntu?
```
sudo apt-get install firefox
```

Besides, as lovinglinux has mentioned in every single Firefox 3.6-related thread so far, this "problem" will soon be "solved," since Mozilla is going to change its release policy, and as a result of that, Canonical will backport new releases of Firefox from now on.

Lastly, what reasons would any ordinary user have to need the newest Firefox release? Most people will just stick with what works, and if you, as an advanced user, want the latest version, you can.

---

### Post by Xbehave on 2010-01-23
> **NCLI said:**
> How is that easier than the way you do it in Ubuntu?
```
sudo apt-get install firefox
```
Arch will update to new firefox branches(e.g 3.0->3.5), so sometimes you'll find that your extensions no longer work.

---

### Post by Starlight on 2010-01-23
> **aysiu said:**
> Why *type* when you can *copy and paste*?

By the way, I'd recommend UbuntuZilla for non-64-bit systems. It uses only the stable Mozilla releases instead of the daily builds.

This is actually quite strange... there's a stable repository for 32 bit, daily builds repository for 64 bit, but no stable repository for 64 bit. o_O Is that because there's no stable 64 bit version?

---

### Post by lovinglinux on 2010-01-23
> **Starlight said:**
> This is actually quite strange... there's a stable repository for 32 bit, daily builds repository for 64 bit, but no stable repository for 64 bit. o_O Is that because there's no stable 64 bit version?

Looks stable to me :)

I also don't understand why Mozilla doesn't release a 64bit build.

---

### Post by Xbehave on 2010-01-23
> **Starlight said:**
> This is actually quite strange... there's a stable repository for 32 bit, daily builds repository for 64 bit, but no stable repository for 64 bit. o_O Is that because there's no stable 64 bit version?
Yup, I don't get why they don't just package the 64bit daily builds that correspond to actual releases.

---

### Post by Chronon on 2010-01-23
> **Techsnap said:**
> When he is stating the FACT that it is harder to install on Linux than Windows then how is he a troll. I've used Linux long enough that installing Firefox is not hard but compared to Windows it is a more complicated process and it's as simple as that.

Falsely linking freedom with ease-of-use makes it appear like a troll.

---

### Post by ElSlunko on 2010-01-23
> **chronon said:**
> falsely linking freedom with ease-of-use makes it appear like a troll.

this.

---

### Post by Pogeymanz on 2010-01-23
> **Xbehave said:**
> [LIST]
[*]ubuntu uses sudo not su (so drop 4)
[*]you can drop 1 (and if you do then you can drop 7,8 )
[*]If you do uninstall firefox then 8 is trivial as you can run apt-cache depends firefox-3.5 to get the dependencies (the min version on the dependencies is quite low, so i think you would have to be running an unsupported ubuntu version to have any issues)
[*]you only need to do 6 or 7, you don't need to do both.
[*]you shouldn't install unmaintained (by apt) software to /usr/lib [nobody will stop you though]
[*]you have to exit the installer in windows too
[/LIST]. so it's really as i said
1) Mozilla site
2) Download
3) sudo tar -xf [filename] /opt (or just tar -xf to install to home [bad idea but like i said nobody is gonig to stop you])
4) ln -s /opt/firefox/firefox /usr/bin/firefox OR create gui launchers to /opt/firefox/firefox


Windows has no x64 firefox, so your x86_64 would be installed in a similar way to x86_64 for linux (downloading the build and installing it yourself)

What are you guys talking about? Doesn't Mozilla still release .deb files?
1) Mozilla Site
2) Download
3) Double Click

Just like on Windows. So Ubuntu has more options for installing FF than Windows does, including the same way that Windows doesn't it. Doesn't that make it strictly better?

EDIT: Huh, I guess they don't have a .deb. I could have SWORN that I've installed FF from a .deb.

EDIT2: And shut up about freedom. I have the freedom to install whatever I want in Ubuntu or Windows and that does not mean that they are equal when it comes to freedom.

---

### Post by koenn on 2010-01-23
> **Chronon said:**
> Falsely linking freedom with ease-of-use makes it appear like a troll.

exactly.

---

### Post by lovinglinux on 2010-01-23
Boring. Who has the record of being a thread killer? Post here and let it die... :)

---

