---
title: "why is it so hard to install things in ubuntu?"
date: 2007-08-19
forum: The Cafe
---

### Post by shorty28898 on 2007-08-19
i am a windows guy, just switched over.  I wanted to download compiz fusion, but it nver seems to work.  Why cant downloads be like windows, where you download it, then click install and your done?

---

### Post by aysiu on 2007-08-19
> **shorty28898 said:**
> i am a windows guy, just switched over.  I wanted to download compiz fusion, but it nver seems to work.  Why cant downloads be like windows, where you download it, then click install and your done?
Because there's a superior software installation method called package management.

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by goumples on 2007-08-19
Use the snaptic package manager.  Installing things on Ubuntu is not "hard" just not the same as Windows.  It'll take some time to adjust to the way Linux does things.. as it takes time to learn any new OS.

---

### Post by Spike-X on 2007-08-19
You mean where you download it, click install, enter your cracked registration code that you got using a trojan-laden keygen from a crack site that's just put a ton of spyware on your computer, tell the installer where to install the program, restart the computer, then you're done?

Compiz Fusion is still in development, which is why it's not available in the repos (click install, and you're done!) yet. My understanding is that it will come packaged in the next Ubuntu release, due out in October.

---

### Post by aysiu on 2007-08-19
Ah, good point, Spike-X. I guess I was jumping the gun a bit there.

I would highly recommend *against* installing alpha or beta software if you're starting out. Stick with what's tested and true.

If you want to hurt yourself, though, try this tutorial:
[*Updated* Compiz Fusion Guide on Ubuntu 7.04](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by eentonig on 2007-08-19
It's so hard, because in Windows you wouldn't even have to opportunity to install alpha-release software.

At least in Linux you can if you are willing to take the risk.

---

### Post by kellemes on 2007-08-19
> **shorty28898 said:**
> i am a windows guy, just switched over.  I wanted to download compiz fusion, but it nver seems to work.  Why cant downloads be like windows, where you download it, then click install and your done?

Well, *buntu, PCLOS and some other distro's are working on this kind of point-click installation of packages but don't seem to be able to offer the point-click-comfort like Windows...yet.
And looking at the amount of HELPME!!-threads about installing Compiz and related projects I don't see this coming anytime soon.

---

### Post by PrimoTurbo on 2007-08-19
The long answer is that linux is so fragmented that software developers need to provide a huge number of variations of formats in order to appease everyone. rpm, deb, dependencies, etc..

Package management is not the best solutions, many of the packages are out of date and they don't allow you to test beta or alpha releases.

Everyone who posted so far has tried to justify why it's more difficult to install instead of providing an actual answer.

---

### Post by Spr0k3t on 2007-08-19
Considering Compiz-Fusion just released a Development Preview release (0.5.2) on the 13th, the stability and ease of use is not going to be amazing.

[http://smspillaz.wordpress.com/2007/08/13/compiz-fusion-our-first-release-052/](http://smspillaz.wordpress.com/2007/08/13/compiz-fusion-our-first-release-052/)

If you are just wanting to play with the cube and other effects, give Beryl a shot (it's in the repos).

System/Administration/Synaptic Package Manager, search for 'beryl'

When you see and understand how the package management system works, you will start to wonder why you even used the Microsoft way of installing/removing software.

---

### Post by sstusick on 2007-08-19
I like how the installation of packages process works in Ubuntu. Why make it like Windows? Ubuntu is a completely different OS, how you install programs **should** be different from Windows.

---

### Post by 3rdalbum on 2007-08-19
> **shorty28898 said:**
> I wanted to download compiz fusion, but it nver seems to work. 

That software is in heavy development phase, and not designed for end-users at the moment. If you don't know what you're doing it can break your system. If you do know what you're doing, it can crash anyway. Wait until Compiz Fusion reaches version 0.6.0, or try installing Beryl 0.2.0 instead.

> Why cant downloads be like windows, where you download it, then click install and your done?

If you have a Windows-compatible system (i386 processor) then there are binary packages available on Linux, which do the same sort of thing as the binary installers on Windows. Except more efficiently, of course.

Compiz Fusion is in development. Because of its open-source nature, you can grab it today and build it (well, there's a Debian package for it too) and try it out. However, there are extra steps you must take because those steps have not yet been included inside the Compiz program itself.

It's like if you managed to get a development version of Internet Explorer 7.5, a proprietary piece of software. You would need to use Microsoft's build system to compile the source code, because they wouldn't have placed a binary installer around it yet. Why not? Because it's not designed for newbies, it's designed for developers. Same thing applies with Compiz Fusion.

If you want things to be easy to install, stick to Ubuntu's repositories, or if you must, use .deb packages of STABLE RELEASES.

---

### Post by tehkain on 2007-08-19
> **shorty28898 said:**
> i am a windows guy, just switched over.  I wanted to download compiz fusion, but it nver seems to work.  Why cant downloads be like windows, where you download it, then click install and your done?

It is really easy. Just ad the repos or download the debs from a repo like trenvino and open the deb files and click install.

How is that harder? Now not working is a different story. This is beta software and not the standard repos. Gutsy will have compiz fusion on install :)

So I ask, How is our method harder then windows? if its in the repos you click a button in 'add and remove'. If its a deb you double click it and push install. If it is in a non standard repo you add the repo in synaptic(2 clicks) then install it. I cannot use window or OSX since I cannot stand dependency management on those systems without a package manager.

Honestly windows app installation is horrible and only easier because people are like sheep.


Also imagine installing a powerful 3d window manager on windows... then dealing with all the configs on that system. It would surely cause deaths due to brain damage world wide.

---

### Post by Perfect Storm on 2007-08-19
Disagree, PrimoTurbo.

In my opinion it's good to have alot of variants, linux is about choices (one of among others).

> Package management is not the best solutions, many of the packages are out of date and they don't allow you to test beta or alpha releases.

Package manager is the best solution. These packages have been tested and are more secure than anything else (except source codes, but it require you can figure out how to read codes). You have one central place to get your stuff without hunting down 1000 of other places.

> Everyone who posted so far has tried to justify why it's more difficult to install instead of providing an actual answer.

Wrong again. See statement above.

---

### Post by EdThaSlayer on 2007-08-19
I love the way you install in Ubuntu, well, if you want to install everything manually you can try going to  [http://packages.ubuntu.com](http://packages.ubuntu.com) and download some debs. Although that would take longer than choosing your program and clicking on "apply".

---

### Post by thisllub on 2007-08-19
> **Artificial Intelligence said:**
> Disagree, PrimoTurbo.

In my opinion it's good to have alot of variants, linux is about choices (one of among others).



Package manager is the best solution. These packages have been tested and are more secure than anything else (except source codes, but it require you can figure out how to read codes). You have one central place to get your stuff without hunting down 1000 of other places.



Wrong again. See statement above.

I don't understand how anyone who has used both Windows and an apt based Linux could find Windows superior.

One word that settles the debate
Registry.

---

### Post by PrimoTurbo on 2007-08-19
Again everyone here is not entirely right.

Windows is superior in software installation if you deny that then you are delusional.

On windows if you want stability, you download non-beta, non-alpha versions of known and trusted software. The user makes a choice on what he/she wants.

While I think package managers and the apt-get method is great, it still has tons of short comings.

[LIST]
[*]Old and outdated packages.
[*]Occasionally missing packages that appear like they exist
[*]Missing information and help files, I had some serious problem for the lack of documentation on Quake2 files in the repo
[*]Lack of informative information about packages, you still have to find out from other sources what package you need to get media playback to work.
[*]Problems with removing packages, some times ubuntu-desktop is removed or something else which causes the whole system to break.
[*]Lack of information on where the file is installed you, you cannot even control where you want things to be installed. What if you have limited space and want to install something on a different drive?..Windows can easily do it, package managers  don't.
[/LIST]

Windows software rarley has any odd dependencies compared to Linux. Finding, Downloading and Installing software is as easy as opening a file and following instructions.

Blaming other aspects of Windows for file installation in order to justify Windows inferiority is insane. 

Viruses? use a virus scanner, only idiots download Kazaa-Ultimate-XXX Addition. There are many trusted websites that provide spyware and virus free software.

---

### Post by aysiu on 2007-08-19
I'm sorry--are you asking for help, or just trolling?

No one here is *insane* or *delusional*. People are expressing their opinions on software based on their experiences. Name-calling is not appropriate here.

If you want help, ask for it. If you feel like insulting other users, you will find yourself quickly banned from these forums.

---

### Post by hooyoung on 2007-08-19
i like ubuntu,because it's not window$.[-X

---

### Post by kellemes on 2007-08-19
Lately there are some initiatives going on to make installation of packages easier..
Lot of info here..
[http://www.linux-foundation.org/en/Packaging]("http://www.linux-foundation.org/en/Packaging")

---

### Post by kellemes on 2007-08-19
> **hooyoung said:**
> i like ubuntu,because it's not window$.[-X

Great reason. :confused:

---

### Post by popch on 2007-08-19
> **PrimoTurbo said:**
> Windows is superior in software installation if you deny that then you are delusional.

Thank you, I still prefer my delusions over yours. I have so far  encountered many more software programs in Windows than in Linux which did not install properly, did not run when installed, did not uninstall, did not work after upgrading or updating, crashed the system or damaged other installed software. Some of that software was quite expensive, too.

If you think that the one way to do something which you happen to know of must be the best and only way to do that, you should stay with Windows, and with the version of Windows you are currently using.

---

### Post by eentonig on 2007-08-19
> **PrimoTurbo said:**
> ...

On windows if you want stability, you download non-beta, non-alpha versions of known and trusted software. The user makes a choice on what he/she wants.

While I think package managers and the apt-get method is great, it still has tons of short comings.

[LIST]
[*]Old and outdated packages.


Aren't you contradicting yourself? If you want stability, use the 'official' and tested versions.
If you want bleeding edge, you introduce beta software and risk breakage. That's the same in windows.


> **PrimoTurbo said:**
> 
[*]Occasionally missing packages that appear like they exist
[*]Missing information and help files, I had some serious problem for the lack of documentation on Quake2 files in the repo
[*]Lack of informative information about packages, you still have to find out from other sources what package you need to get media playback to work.

Can you give examples of these from the official Ubuntu repo's? Not third party repo's you added afterwards.

> **PrimoTurbo said:**
> 
[*]Problems with removing packages, some times ubuntu-desktop is removed or something else which causes the whole system to break.

Before any remove, you get an information which other packages will be influenced. If you took the time to read system feedback, this shouldn't happen. At least, I never had a problem with it.

> **PrimoTurbo said:**
> 
[*]Lack of information on where the file is installed you, you cannot even control where you want things to be installed. What if you have limited space and want to install something on a different drive?..Windows can easily do it, package managers  don't.
[/LIST]

Because the way Linux works, packages share common libraries. which helps in keeping filesizes down. Also, configuration is kept in a structured fashion. 

Yes, this poses some limitations. In the advance of allowing easy automation, small footprint for common programs, etc...
If you do some study on the linux filesystem, you will quickly know where you can expect to find your installed programs and related files.

> **PrimoTurbo said:**
> 
Windows software rarley has any odd dependencies compared to Linux. Finding, Downloading and Installing software is as easy as opening a file and following instructions.


In windows, almost every program comes with it's own libraries.   - Making programs ten times as big as in linux to achieve the same result.
- Forcing developpers to continuously reinvent the wheel in order to achieve the same functionality.


> **PrimoTurbo said:**
> 
Blaming other aspects of Windows for file installation in order to justify Windows inferiority is insane. 


Correct. I too see no need to bash windows on other points when talking about software installation.

> **PrimoTurbo said:**
> 
Viruses? use a virus scanner, only idiots download Kazaa-Ultimate-XXX Addition. There are many trusted websites that provide spyware and virus free software.


- Why would I need to waste cpu and memory on a program (virusscanner)? I used them in windows, and they really slowed down my system. To the point where I decided to run without them and just make sure I could easily reinstall my OS when I got infected.

---

### Post by Perfect Storm on 2007-08-19
> **PrimoTurbo said:**
> ...

You, sire - don't really grasp how Gnu/Linux works and the philosophy behind it, or Ubuntu for that matter. And the insulting only hurt your creditability.

---

### Post by kellemes on 2007-08-19
> **Artificial Intelligence said:**
> You, sire - don't really grasp how Gnu/Linux works and the philosophy behind it, or Ubuntu for that matter.

Don't tell me it's philosophy that made GNU/Linux package-management as it is today.. Well, except for "the freedom of choice" leeding to a gazillion of pm-systems.
GNU/Linux is for a long time desperately trying to get to some sort of standard (without success as so often) in package-installation for no reason at all?

---

### Post by Spr0k3t on 2007-08-19
> **PrimoTurbo said:**
> Windows is superior in software installation if you deny that then you are delusional.

This line quoted above is pure flame-bait.  I vote to lock, jail, or remove.  Basing opinions as fact doesn't get much credibility.

> **PrimoTurbo said:**
> Windows software rarley has any odd dependencies compared to Linux. Finding, Downloading and Installing software is as easy as opening a file and following instructions.  Blaming other aspects of Windows for file installation in order to justify Windows inferiority is insane.

I'm not even going to go there.  There have been several situations where I've helped people reinstall the OS simply because one software refused to work with another software.  A good case in point is if you look at AutoCAD and Flash9.  Oh and let's throw BusinessObject, Crystal Reports, SAP G, MS Project 2007, and Visio 2003 on to the same computer without having to hand tweak almost every package install... it's impossible.  Still, the windows method of installing software is superior, we can't forget that.

:lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by bwtranch on 2007-08-19
Hi folks,

Just wanted to point out that this thread was posted by "shorty" and they have not replied. I recommend this thread be closed.

---

### Post by Perfect Storm on 2007-08-19
> **kellemes said:**
> Don't tell me it's philosophy that made GNU/Linux package-management as it is today.. Well, except for "the freedom of choice" leeding to a gazillion of pm-systems.


Again, you think it's a bad to have diffrent packages, where I see it's one of the strong side. You will never ever _ever_ see a standardize of packages on Linux. It also require that every single Distro out there standardize which will defeat one of the purpose of choices. Which again will never happen.


> GNU/Linux is for a long time desperately trying to get to some sort of standard (without success as so often) in package-installation for no reason at all?[/quote]

By who? Not with the folks I talk to.

---

### Post by kellemes on 2007-08-19
> **Artificial Intelligence said:**
> Again, you think it's a bad to have diffrent packages, where I see it's one of the strong side. You will never ever _ever_ see a standardize of packages on Linux. It also require that every single Distro out there standardize which will defeat one of the purpose of choices. Which again will never happen.





I think the diversity is great, I love Pacman myself, it's my primary reason for choosing Arch, I personally don't need standards myself.
But the poster of this thread was asking about usability, and browsing the forums these days I see a lot of folks having big problems un/installing packages.

[http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")

---

### Post by bwtranch on 2007-08-19
Re: #28 Yeah, I do too. I was just saying that the OP is not around and maybe you guys should take this disscussion somewhere else and close this thread.

Edit: Re: #30 Otay, just seemed like it was getting a little out of hand.

---

### Post by Sef on 2007-08-19
> Hi folks,

Just wanted to point out that this thread was posted by "shorty" and they have not replied. I recommend this thread be closed.

Since shorty only 3 hours ago, I will keep it open for a day or two to see if they reply.

---

### Post by kellemes on 2007-08-19
> **bwtranch said:**
> just seemed like it was getting a little out of hand.

Would be a pitty if one bad-mouth-dude could kill the hole thread.. Better kill the post.

---

### Post by bwtranch on 2007-08-19
OK, one more post on this one and I'm outta here. If you read this, there is not much substance. A whole lot of bickering, but not much useful information. I'm gonna go find a thread where I can actually HELP someone and stop watching a Jerry Springer show. Bye. See ya in the funny papers :)

---

### Post by wolfger on 2007-08-19
Thanks, bwtranch. That was the best post of the thread.:lolflag:

---

### Post by moshuptrail on 2007-08-19
When a discussion devolves into what is "better" you just get opinions, and don't learn much.  If the discussion could be turned to what are the differences (facts) and the advantages/disadvantages of each we just might learn something.

There is a sort of parallel question that goes with the OP's question: How easy is it to write a new program and then distribute it for Linux systems in general, or Ubuntu specifically?  And how does that compare with Windows?

There are many Linux distros for developers to worry about.
There are only a few Windows "distros"  CE XP etc.
Does that make binary distribution easier?  (I would think so, but...)

Just about anyone (including some that we would rather not) seems to be able to post a .exe on the internet for Windows.  Is the same true for Linux?  (that's a serious question, not rhetorical)  Suppose I created a binary for at least one Linux distro, say, Ubuntu. How easy would it be for me to then share it with the world, without distributing source?  (for whatever reason, be it ease of install, or code I want to keep proprietary)

Can just anyone create a repo and post the address so I can add it to my package manager and then install stuff from it?   Or are repos controlled or restricted in some way?

There is one program in particular that I have watched evolve, gscan2pdf.  I use it a lot.  At first there was no repo.  Eventually the guy figured out how to create one.  I have it in my list now, but package manager still flags it as "not validated" or something like that.  I like the way it keeps me up-to-date with the latest version.  I don't get that with Windows programs unless the developer has built it in.

---

### Post by salsafyren on 2007-08-19
Check out zeroinstall.

A common install system for ALL distros.

Someone should seriously run with this method since it would help people who need new software but won't upgrade the whole distro.

Also, klik2 will be able to do that, however a bit differently.

---

### Post by Dimitriid on 2007-08-19
Its "harder" cause its more stable. Chances you will break your system beyond repair ( other than formatting it ) on windows, even with "supported" software is fairly high.

But even if some stupid software you download for Linux decides "what the hell im gonna delete 34 lines at random from xorg.conf" you'd still be able to log in on text mode, use something like links2, find a solution, rewrite the file and go right back to your desktop.

Try that with the Windows registry and their "tools" :guitar:

---

### Post by PrimoTurbo on 2007-08-19
I want to apologize I didn't mean to flame anyone specific I was using the terms as a figure of speech.

---

### Post by blithen on 2007-08-19
> **hooyoung said:**
> i like ubuntu,because it's not window$.[-X

Amen! Linux is NOT windows, so I have no idea how it can be superior. It has it's advantages, but you can actually see what you are installing. It's a lot safer choosing out of a list of what you want.

---

