---
title: "A very specific &quot;Which distro is best&quot; question"
date: 2009-03-28
forum: The Cafe
---

### Post by Mulenmar on 2009-03-28
The computer: an eMachines T3990. CPU: 2.8GHz CeleronD, 256MB RAM

The target user: My mother, who is not knowledgeable in Linux, but only needs internet and word processing for online college classes.

I've tried a minimal custom Ubuntu installation, but it just doesn't have the zip AND functionality I want on this PC.

I will be the one providing tech support and doing all the updating stuff, I just want it to be fast and stable, with new programs, and not thrash the hard drive when running a word processor, Firefox or Opera, and maybe a music player all at once.  And I can't wait hours and hours for stuff to custom-compile, unless I can download everything at once and compile later, so Gentoo is out.

So, here's the question:  should I pick Arch, Debian Lenny, or perhaps DreamLinux?

---

### Post by Mulenmar on 2009-03-28
For Tux's sake, **bump**! :lolflag:

---

### Post by wolfen69 on 2009-03-28
i would give dreamlinux a try if you want an OS that is pretty much ready to go. i've gotten dream to work on a pc with 128mb ram. another one to consider is antix mepis (based on debian). it is made to work on older machines, but is very up to date with all codecs and such.

i just went to a computer fair today and saw sticks of ram for $5. there really is no excuse anymore for not having enough ram.

---

### Post by binbash on 2009-03-28
Arch and lenny is ok.Dreamlinux just sucks.with that ram you may want to install xubuntu.Also consider puppy and mepis

You can download everything at gentoo then compile it offline.

---

### Post by Changturkey on 2009-03-28
Puppy? Mepis?

---

### Post by cybergalvez on 2009-03-28
well from what I see the machine has limited memory and video.  So I guess I would aks you what you mean by "doesn't have the zip AND functionality I want on this PC"  I would suspect that its just gnome using up to many recourses that this machine simply does not have.  Have you tried Xubuntu its much leaner then the regular gnome based one because of XFCE. 

When you tested ubuntu did you actully install it or run the live disk? the live disk is great but slow comparied to a real install

You might also want to take a look at [http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989](http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989)

they mention a few distros that are optimised for small machines

---

### Post by Skripka on 2009-03-28
No matter WHAT you do.  A machine with only 256mb of RAM is going to page like MAD running anything like Firefox or OOO....unless you;re running something like Puppy.  I wouldn't bother with Xubuntu if you want "zip"...sure you can go ahead and try it-but I'd wager it wouldn't be that much quicker than a minimal Ubuntu install.

---

### Post by Mulenmar on 2009-03-28
I've been exploring using tiny little WMs like JWM and FVWM-Crystal, and ultra-light apps, for the past several weeks, and although they're half the answer, Ubuntu is just NOT the OS for this computer.

More memory is not a possibility at this point, we're a little short on money at the moment.

XFCE is ok, but I wanted even leaner -- not to mention something I can figure out how to change the menu on! I chose Linux for freedom and I can't change the XFCE menu.

I know Firefox and OOO are fat, I'm going to use Swiftfox, Midori, and Abiword but have those bigger versions available for max compatibility.

@ binbash:  Why does DreamLinux suck?
            And how can I download all the packages and compile   
            offline at a later time in Gentoo? I found the Portage snap
            shot, and the stage3 tarball, but everythihng else is 
            .ebuild files (telling where to download from?)

---

### Post by Mulenmar on 2009-03-28
> **cybergalvez said:**
> well from what I see the machine has limited memory and video.  So I guess I would aks you what you mean by "doesn't have the zip AND functionality I want on this PC"  I would suspect that its just gnome using up to many recourses that this machine simply does not have.  Have you tried Xubuntu its much leaner then the regular gnome based one because of XFCE. 

When you tested ubuntu did you actully install it or run the live disk? the live disk is great but slow comparied to a real install

You might also want to take a look at [http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989](http://www.informationweek.com/news/software/linux/showArticle.jhtml?articleID=203100989)

they mention a few distros that are optimised for small machines

I'll check out the link, thanks.

I've been using Ubuntu for a year -- I know about GNOME, KDE, XFCE, and the WMs.  I HATE the live disk, I use DSL for that type stuff.

Xubuntu has far too much GNOME in it, used like 200 MB (RAM+swap) without any additional programs started.  Didn't bother optimizing that, just whacked away and started over with a custom-install.

Like I said, my mother will be using this, but the tech stuff is up to me. 

The options are Debian, Arch, and Dreamlinux.  Please suggest only the pros and cons of each.

---

### Post by ddrichardson on 2009-03-28
If you don't care for Gnome, then as someone else mentioned, use Arch.

The base system has no GUI and if you install XFCE (pacman -S xfce4)then it will only pull XFCE dependencies. I also find that wicd instead of network manager is a good way around a no-Gnome XFCE.

---

### Post by K.Mandla on 2009-03-28
I would pick whichever distro you feel comfortable managing, add a clean XFCE installation and put the software you want on top. The machine is fast enough, and there's enough memory there to work with.

---

### Post by Mulenmar on 2009-03-28
@ K. Mandla: I feel comfortable with Debian, but this is an opportunity to branch out. 

As long as my mom doesn't have to fiddle with the innards, I guess the distro is totally 
up to my skills...

Well, I guess since I have a limited time on the net connection here, I'm just going to attempt an Arch installation.  I've got Debian CDs, I can always install Debian later.  I'm marking this as solved, for now.

May the Penguin be with you.

---

### Post by swoll1980 on 2009-03-28
> **binbash said:**
> Arch and lenny is ok.Dreamlinux just sucks.with that ram you may want to install xubuntu.Also consider puppy and mepis

You can download everything at gentoo then compile it offline.

Really? You think Arch would be a good choice for Grandma?

---

### Post by Skripka on 2009-03-28
Since you are going to Arch, be CERTAIN you read and understand the Arch Beginner's Wiki (see Arch linky in my sig).  If you follow it to the letter-and understand it-you'll be up and running quick...skip steps or don't read, and you're setting yourself up for frustration.

---

### Post by cwsnyder on 2009-03-28
You may also want to look at a net-install of Debian Lenny with LXDE.  Debian can be installed as a minimal system better than Ubuntu, and the Lenny build (which I have been using off and on for 6 months) can be very similar in operation to Ubuntu.  Drawbacks:  No Firefox at all, it is called Iceweasel and has all of the trademarks of Firefox filed off.  Proprietary programs, such as Adobe Flash, commercial DVD playing, and MP3 music files are not enabled by default, and you have to follow the tutorials fairly closely to get them installed.  Debian is serious about not having any non-free, non-libre, or closed source software in their main repositories.

There is a tiny off-shoot of MEPIS, Tiny-ME, which is a minimal system, but which has more support for multi-media.  This may work better for you.  BTW MEPIS is based on Debian, now.

Puppy works well on small systems, but you have to remember to save your system state before shutting down.

DSL is also based on a Debian system with an earlier kernel for a smaller total size, but it has some quirks.

I personally like Slitaz, but it helps if you can puzzle out at least a little French for the installation.  Very minimal distribution.

---

### Post by Mulenmar on 2009-03-28
> **Skripka said:**
> Since you are going to Arch, be CERTAIN you read and understand the Arch Beginner's Wiki (see Arch linky in my sig).  If you follow it to the letter-and understand it-you'll be up and running quick...skip steps or don't read, and you're setting yourself up for frustration.

Thanks.  I think I started to try Arch before, and I decided to explore Ubuntu a bit further is all.  I've done some Gentoo, so how hard can Arch be? (ominous .ogg music plays).

BTW...what happened to the "Mark thread as SOLVED" tool?

---

### Post by K.Mandla on 2009-03-28
> **Mulenmar said:**
> @ K. Mandla: I feel comfortable with Debian, but this is an opportunity to branch out. 
Branching is good, but if you just want fast and stable together, with something you're familiar with, I'd stick with Debian and XFCE. They're quite nice together. And you get the benefit of easy administration (since you're comfortable with it) and a lighter environment.

I suppose the LXDE-Debian version is an option too, as it comes with OOo by default, plus a few other things. I think I'd use XFCE though, personally. 

Good luck. ;)

---

### Post by Skripka on 2009-03-28
> **Mulenmar said:**
> Thanks.  I think I started to try Arch before, and I decided to explore Ubuntu a bit further is all.  I've done some Gentoo, so how hard can Arch be? (ominous .ogg music plays).

BTW...what happened to the "Mark thread as SOLVED" tool?

If you RTFM, and understand it-it is easy; not being in a hurry and taking my time--my first Arch build took a few hours.  Bear in mind I was being uber thorough and readin and rereading to make sure I didn't screw up.  My second Arch build took all of 20 minutes (minus package downloading)

---

### Post by Mulenmar on 2009-03-28
> **swoll1980 said:**
> Really? You think Arch would be a good choice for Grandma?

It's for my MOTHER, not my GRANDMOTHER.  If it were for my grandma, she'd probably be able to figure out LFS!!

The technical side of things is my department, Mom doesn't have to worry about it.

---

### Post by SuperSonic4 on 2009-03-28
Once Arch is set up it is very low maintenance. Just ```
sudo pacman -Syu
``` every few days to update the system

---

### Post by Mulenmar on 2009-03-28
> **K.Mandla said:**
> Branching is good, but if you just want fast and stable together, with something you're familiar with, I'd stick with Debian and XFCE. They're quite nice together. And you get the benefit of easy administration (since you're comfortable with it) and a lighter environment.

I suppose the LXDE-Debian version is an option too, as it comes with OOo by default, plus a few other things. I think I'd use XFCE though, personally. 

Good luck. ;)

LXDE-Debian...wait a minute, that's not a bad idea :P.  If I can't get the Arch running, that's what I'll go with.

---

### Post by cariboo on 2009-03-28
I would suggest AntiX. I am running it on an old Compaq  PII 350Mhz with 256Mb ram. I use Icewm which looks quite Windows like and  I use Opera instead of Firefox and for just surfing it is quite acceptable. Just imagine what it would be like on something as fast as your system :) AntiX is Debian based, so there is no steep learning curve.

Jim

---

### Post by gn2 on 2009-03-28
Come on, it's your mother, treat her to some more RAM and regular Gnome Ubuntu will run just fine on that machine.

---

### Post by Mulenmar on 2009-03-28
> **cariboo907 said:**
>  AntiX is Debian based, so there is no steep learning curve.

Jim

It's not about the learning curve, it's about the repos and low-memory usage.  Thanks though, I'll check AntiX out too, while Arch installs.:)

---

### Post by mamamia88 on 2009-03-28
> **gn2 said:**
> Come on, it's your mother, treat her to some more RAM and regular Gnome Ubuntu will run just fine on that machine.

you beat me too it add some more ram you should be good to go.

---

### Post by Mulenmar on 2009-03-28
> **mamamia88 said:**
> you beat me too it add some more ram you should be good to go.

Like I said, cash isn't something we've got a ton of at the moment, and what we've got is probably going to go to the broadband connection it's taken me three years to convince her to get. I'd love to get more memory, but it's just not an option right now. :( Maybe later.

---

### Post by gn2 on 2009-03-28
Mulenmar, where are you located and what type of RAM is required?

---

### Post by Mulenmar on 2009-03-28
> **gn2 said:**
> Mulenmar, where are you located and what type of RAM is required?

My location isn't something I want on the public forum (and thus Google, and thus everywhere), PM me please.

---

### Post by ddrichardson on 2009-03-28
> **SuperSonic4 said:**
> Once Arch is set up it is very low maintenance. Just ```
sudo pacman -Syu
``` every few days to update the systemI'd be careful with that. I've been running Arch for quite some time, if you update automatically without checking to see what updates there are then there is a very good chance you won't boot.

Its a great system and I really like pacman but you need to check before an upgrade especially if there are kernel updates.

---

### Post by gnomeuser on 2009-03-28
You may want to look at moblin, it is damn zippy

---

### Post by gn2 on 2009-03-28
> **Mulenmar said:**
> My location isn't something I want on the public forum (and thus Google, and thus everywhere), PM me please.

Quite right too.
I've responded to your PM.

---

### Post by huzzam on 2009-03-28
> **Skripka said:**
> No matter WHAT you do.  A machine with only 256mb of RAM is going to page like MAD running anything like Firefox or OOO....unless you;re running something like Puppy.  I wouldn't bother with Xubuntu if you want "zip"...sure you can go ahead and try it-but I'd wager it wouldn't be that much quicker than a minimal Ubuntu install.

Xubuntu installs Abiword, not OpenOffice, and I find that makes a huge difference right there. Also XFCE's relative lightness compared to Gnome really does seem to help.

I installed Xubuntu on my girlfriend's Thinkpad T30 (2gHz p4, 256mb ram, thanks to the damn T30 memory slot problem), and it works surprisingly well & runs reasonably fast, even though she never ever closes anything; usually I find six to ten firefox windows with her yahoo mail open. And it's plenty simple enough for her to use (and the dangerous bits are hidden behind my admin password).

Yes the machine pages all those dormant firefox processes out, but that's fine. That's what paging's for!

I recommend xubuntu highly for a low memory machine.

---

### Post by chris200x9 on 2009-03-28
> **ddrichardson said:**
> I'd be careful with that. I've been running Arch for quite some time, if you update automatically without checking to see what updates there are then there is a very good chance you won't boot.

Its a great system and I really like pacman but you need to check before an upgrade especially if there are kernel updates.

:confused::confused::confused: I've been running arch for about a year on two machines one i686 and one x86-64 and I've never had that happen, the worst that has happened is my pidgin got a little bit crashy once.

edit: did you specificaly enable testing?

---

### Post by ddrichardson on 2009-03-29
> **chris200x9 said:**
> :confused::confused::confused: I've been running arch for about a year on two machines one i686 and one x86-64 and I've never had that happen, the worst that has happened is my pidgin got a little bit crashy once.

edit: did you specificaly enable testing?
Nope. Its on an Acer Aspire One and there have been a couple of kernel updates that have prevented it booting. There was also the recent XFCE update that completely broke all the graphics after the package removed one of the library paths. The version of DHCP on the install image didn't work either - it wouldn't accept DHCP offers.
  
Then there is also the issue of AUR packages, which can be very easily broken on upgrading another package. I've been using the custom LCD filters in libxft/cairo and every time there's been a kernel upgrade these have needed remaking and on one occasion a wait until a newer version of libxft was available.

I like Arch, like I said and actually prefer AUR and pacman to their counterparts but the point is that when recommending to a new user it's worth mentioning that unlike many distros, it really shouldn't be automatically upgraded without [checking]("http://wiki.archlinux.org/index.php/Package_Management_FAQs#Q:_An_update_to_package_XYZ_broke_my_system.21") what the upgrades are. Personally, I only install security updates or updates that offer me new features that I can use.

---

### Post by snowpine on 2009-03-29
IMHO, you don't want a rolling release like Arch for someone like your mother. Pick something like Debian Lenny that will stable and consistent for years with minimal updates. I think LXDE Lenny is probably the best suggestion in this thread. :)

---

### Post by Rotaj on 2009-03-29
Since you said you feel comfortable with Debian, I would suggest [sidux]("http://www.sidux.com") XFCE or KDE-lite. Once setup, there is very little to worry about.

The KDE lite version should only use about 100mb ram.

---

### Post by EV500B on 2009-03-29
If you feel right with debian:
.Download Debian XFCE cd, install it minimally and using **aptitude** install whatever you want, like xfce and all the applications you want. (60Mb RAM)
(IMHO, the desktop is faster and more stable than when making the full installation)
.Install Debian minimally, icewm+icebuntu. (40Mb RAM)
(That one looks fairly pretty after a good customization.)

[COLOR=SlateGray]Make yourself a favor and disable all unnecessary services to have the maximum free resources possible[/COLOR].

Xubuntu and all Ubuntu derivative aren't recommended at all for slow pc,[SIZE=1] [I]believe me! or try to.



[/I][/SIZE]

---

### Post by jimi_hendrix on 2009-03-29
i would go with arch or something like puppy or DSL

---

### Post by doorknob60 on 2009-03-29
Arch (or Lenny if you want) +Lxde or Xfce, using Opera as a browser and Abiword (OOo would run, but might be a little sluggish) for word processor. Exaile is a good full featured music player, but it's fairly light.

---

### Post by mips on 2009-03-29
> **gn2 said:**
> Mulenmar, where are you located and **what type of RAM is required**?


333MHz DDR Non-ECC CL2.5 DIMM

Machine has two sockets and can take a maximum of 2GB

[http://www.ec.kingston.com/ecom/configurator_new/modelsinfo.asp?id=1&SysID=24449&mfr=eMachines&model=eMachines+T3990&search_type=&root=us&LinkBack=http%3A%2F%2Fwww.kingston.com&Sys=24449-eMachines-eMachines+T3990&distributor=0&submit1=Search](http://www.ec.kingston.com/ecom/configurator_new/modelsinfo.asp?id=1&SysID=24449&mfr=eMachines&model=eMachines+T3990&search_type=&root=us&LinkBack=http%3A%2F%2Fwww.kingston.com&Sys=24449-eMachines-eMachines+T3990&distributor=0&submit1=Search)

---

### Post by ddrichardson on 2009-03-29
> **doorknob60 said:**
> Arch (or Lenny if you want) +Lxde or Xfce, using Opera as a browser and Abiword (OOo would run, but might be a little sluggish) for word processor. Exaile is a good full featured music player, but it's fairly light.
Abiword pulls a lot of Gnome dependancies (somewhere in this thread someone said his was an issue).

---

### Post by Chemical Imbalance on 2009-03-29
EDITED upon correction:

Xubuntu:

[www.xubuntu.com](www.xubuntu.com)

For Xubuntu, you'd probably be better off installing vanilla xfce on Ubuntu than using the distro Xubuntu.  I also recommend fluxbox window manager on vanilla Ubuntu with gnome-dependencies removed.

---

### Post by snowpine on 2009-03-29
> **Chemical Imbalance said:**
> Fluxbuntu or Xubuntu:

[www.fluxbuntu.org](www.fluxbuntu.org)



Terrible idea. Fluxbuntu reaches its "end of life" on April 18, after which the OP's mom will get all sorts of errors next time she tries to update the system or install a new application.

[http://ubuntuforums.org/showthread.php?t=1104965](http://ubuntuforums.org/showthread.php?t=1104965)

---

### Post by Chemical Imbalance on 2009-03-29
> **snowpine said:**
> Terrible idea. Fluxbuntu reaches its "end of life" on April 18, after which the OP's mom will get all sorts of errors next time she tries to update the system or install a new application.

[http://ubuntuforums.org/showthread.php?t=1104965](http://ubuntuforums.org/showthread.php?t=1104965)

[bad day rant]

What?  There is a Jaunty update for Fluxbuntu.  Look at the page more carefully before you call someone's idea terrible. It will be updated soon apparently.
If not, then just install fluxbox onto vanilla ubuntu.  That's not hard to figure out.

[/bad day rant]

EDIT: it seems fluxbuntu has only included a mockup of Jaunty, and it may be a while before they update it, so you probable shouldn't go with  it.  Thanks to snowpine

---

### Post by snowpine on 2009-03-29
> **Chemical Imbalance said:**
> What?  There is a Jaunty update for Fluxbuntu.  Look at the page more carefully before you call someone's idea terrible. It will be updated soon apparently.
If not, then just install fluxbox onto vanilla ubuntu.  That's not hard to figure out.

I am very familiar with the Fluxbuntu project and stand by my recommendation. Gutsy Gibbon 7.10 is the most recent release currently available, and the OP is looking for a recommendation now, not at some hypothetical future date. :)

Check out the official Fluxbuntu forums at community.fluxbuntu.org if you are curious about the status of the project.

My recommendation continues to be Debian Lenny with LXDE (or something else light, like Xfce).

---

### Post by Chemical Imbalance on 2009-03-30
> **snowpine said:**
> I am very familiar with the Fluxbuntu project and stand by my recommendation. Gutsy Gibbon 7.10 is the most recent release currently available, and the OP is looking for a recommendation now, not at some hypothetical future date. :)

Check out the official Fluxbuntu forums at community.fluxbuntu.org if you are curious about the status of the project.

My recommendation continues to be Debian Lenny with LXDE (or something else light, like Xfce).

I'll edit my post above to not include Fluxbuntu.  I didn't realize they weren't continuing support and the Jaunty Experimental on the home page just seems to contradict this.  I'm assuming this is just a mockup of Jaunty?  Sorry for my snapping--bad day then.

---

### Post by Mehall on 2009-03-30
> **Skripka said:**
> No matter WHAT you do.  A machine with only 256mb of RAM is going to page like MAD running anything like Firefox or OOO....unless you;re running something like Puppy.  I wouldn't bother with Xubuntu if you want "zip"...sure you can go ahead and try it-but I'd wager it wouldn't be that much quicker than a minimal Ubuntu install.

Duno if anyone argued this, but I have a Crunchbang Linux box with 256MB RAM (getting it upgraded soon) and I can run Firefox without too much paging. it's not exactly blazing fast like most anything else in Crunchbang is, but it's okay.

---

### Post by Mulenmar on 2009-05-22
Hello again), Ubuntu community! ):P

I just wanted to post, for posterity's sake, the final configuration I ended up placing on Mom's 2-something GHz, 256MB RAM computer --- and she absolutely loves it, btw! :D

Debian Lenny + Openbox + wbar + OpenOffice 3 + Swiftfox + Adobe Flash (yuck utterly closed-source, but she needs the "just works" aspect), and Nitrogen to set the wallpaper. Oh, and a Conky showing CPU, RAM, and swap usage in nice colors. :)

Memory usage, if I recall correctly, runs at about 158MB out of the 256MB -- no custom kernel as of yet -- with Swiftfox open and two tabs.

So, this setup should run well for other computers with the same amount of memory, I didn't put in anything too processor intensive but I have yet to test a similar setup with any older hardware. I plan on building a duplicate of my grandfather's PC to try an convince him to try Linux, so that'll be a good test. I'll edit this post and add a link to a new topic in the Testimonials section.

---

### Post by XubuRoxMySox on 2009-05-22
For my low-resource machine I use [Crunchbang]("http://crunchbanglinux.org") (Ubuntu-based, very minimal) and installed [LXDE]("http://lxde.org") (much more lightweight than even XFCE). It runs fast and sweet and looks kinda like WinXP.

LXDE will play nice with Crunchbang as long as you let PCMan (LXDE's built-in file manager) manage the desktop.

In PCMan, applications are found in */usr/shared/applications* and appear as icons. Just drag the ones you want to use to the desktop.

You can add way-kewl Grandma-friendly wallpapers to /*usr/shared/lxde/wallpapers* (you have to be root to add files there, but PCMan makes that easy too). Give your gramma a nice pretty desktop with lightweight, speedy Crunchbang.

-Robin

---

### Post by JSC77 on 2009-05-22
I dual boot Debian Lenny and Arch on my machine. I like to tinker, so I prefer to play with arch most of the time, but debian lenny is definitely much more stable. Since they are both very customizable and as lightweight as you want them to be, I would go for lenny with lxde or xfce. If you pick lxde then combine it with thunar since there's no trash can in pcmanfm (dangerous when you accidently delete a file).

---

