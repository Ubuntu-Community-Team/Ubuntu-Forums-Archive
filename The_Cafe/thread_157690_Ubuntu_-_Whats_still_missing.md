---
title: "Ubuntu - Whats still missing"
date: 2006-04-09
forum: The Cafe
---

### Post by KillerKiwi on 2006-04-09
An ex MS employee post : [http://keithcu.com/wordpress/?p=24](http://keithcu.com/wordpress/?p=24) basiclly summing up what he still thinks is missing:

[LIST]
[*]Multimedia often skips or doesn&#8217;t display properly in the browser 
Getting better - [http://www.gstreamer.net/](http://www.gstreamer.net/)
[*]Sleep and hibernate don&#8217;t work on my hardware yet 
Dosnt work for me ethier but more a driver issue I think
[*]Gnome will mount NTFS, but I can&#8217;t browse because of permission problems
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/) (If I have a ntfs parition then 99% I have windows..... )
[*]Enabling external monitors isn&#8217;t easy 
Why is there no UI tool?
[*]Remote printing requires manual textfile configuration
Needs a unified UI
[*]Installing non-free software or drivers requires lots of manual work (!!!!!)
[https://wiki.ubuntu.com/ThirdPartyPackages?highlight=%28third%29](https://wiki.ubuntu.com/ThirdPartyPackages?highlight=%28third%29)
[https://launchpad.net/distros/ubuntu/dapper/+source/gdebi](https://launchpad.net/distros/ubuntu/dapper/+source/gdebi)
[*]apt-get dist-upgrade hosed my machine
If this is supported there should be an upgrade to "Edgy Elephant" button
[/LIST]

One of my own
[LIST]
[*] Hi Res boot image
[/LIST]
Any one add to that list?

---

### Post by aamukahvi on 2006-04-09
**Multimedia often skips or doesn&#8217;t display properly in the browser (Gstreamer)**
Yeah, I agree, but I think it's getting there.

**Sleep and hibernate don&#8217;t work on my hardware yet (Driver Problemns)**
I don't really know because I've been unable to install a new BIOS on my computer that even enables those :p

**Gnome will mount NTFS, but I can&#8217;t browse because of permission problems**
I don't think it's a bug. It could be easily changed, but it's considered a security issue to allow unrestricted access to the NTFS partitions to any and all users.

**Enabling external monitors isn&#8217;t easy (!!!!!!!)**
Not a bug, but a missing feature. Configuring X is too much of a hassle. It should be graphical.

**Installing non-free software or drivers requires lots of manual work (!!!!!)**
Depends on the software. Some can be installed easily through apt. Others (w32codecs) can't be easily included because of legal issues. 

**Driver bugs ( as always )**
Blame the manufacturers.

**apt-get dist-upgrade hosed my machine**
Being a little more specific would help.

I really have nothing to add to that list. Of course, there are still major apps that are missing (mostly the Adobe/Macromedia stuff). As for multimedia support, it's all up to the codec manufacturers. If they released codecs with less restricted licences, they could be added to the repos.

---

### Post by shu on 2006-04-09
Well, holy truth, I'd say. The fact that NTFS is mounted but cannot be browsed is simply annoying. Sleep&Hibernate work from time to time. Setting up printing over network requires 3 different tools [gnome gui, browser and terminal] to have it done correctly. Enabling external monitor is easy, but setting it up is a nightmare. 

About bugs.. I can't complain. All bugs reported by me have been taken care of and fixed when possible. I had supplied developers with solutions though.

---

### Post by Ocxic on 2006-04-09
i wonder if he knows breezy is just the second realease of ubuntu.

---

### Post by joshrobinson on 2006-04-09
i never use sleep or hibernate.. never have.. never will

i like how he calls himself a newbie when it comes to linux, thats pretty funny
but he blames things that are different then windows "bugs" instead of taking time to learn the differences

the reading of ntfs drives is extremely easy to acomplish, but to him its a bug ](*,)

---

### Post by leech on 2006-04-09
[QUOTE=Ocxic]i wonder if he knows breezy is just the second realease of ubuntu.[/QUOTE]

Breezy is the third release of Ubuntu.  It is Warty, Hoary, Breezy, Dapper.  

Leech

---

### Post by BeatBoxRocker on 2006-04-09
He says is missing because is used to use Windows. I dont think anything more should be added to the list, but i agree with him in some points:

* Enabling external monitors isn’t easy - anything related to X is most of the times a headache ](*,) 
* Remote printing requires manual textfile configuration: yes, it could be easier for newbies.

Migrating from Windows to Linux isnt easy at all :), but once you are used to linux you arent going to change to windows. 

Saludos.

---

### Post by aamukahvi on 2006-04-09
Oh yeah, more on that part about installing non-free programs being hard... I guess it's up to the manufacturers of said non-free programs to decide how they want their users to install. If they provided compliant .deb packages (or if Ubuntu devs were allowed to make and redistribute them), it would be extremely easy.

---

### Post by shu on 2006-04-09
I don't understand why some of you attack this guy. What he wrote is very objective. He pointed out those nasty little bugs that ruin whole image of Ubuntu and/or linux in general. 

There are some things that people are allowed to take for granted. And that's not because they came from windows. I've been using linux exclusively (except for games) for a 9 years and find those things annoying.

---

### Post by gunksta on 2006-04-09
[quote=shu]I don't understand why some of you attack this guy. What he wrote is very objective. He pointed out those nasty little bugs that ruin whole image of Ubuntu and/or linux in general. 

There are some things that people are allowed to take for granted. And that's not because they came from windows. I've been using linux exclusively (except for games) for a 9 years and find those things annoying.[/quote] 


Well, unless someone has edited their comment, I don't think anyone has really attacked him at all.  In fact, several people have agreed that X needs to be easier to set up.....because it should be easier to set up.  The M$ guy is 100% right about that.  And, the hibernate stuff borks on my laptop too.  Wish it didn't.  I also really wish ATI could pull themselves together and write a decent driver so I could use the full capability of my laptop.  

But, some of these things aren't really Linux's responsibility/problem.  Linus nor Ubuntu nor anyone else can help ATI write a good driver as long as the driver is kept proprietary.  My next laptop is going to have an Nvidia card in it.  Their driver is proprietary too but at least they view their linux customers as warranting a decent driver.

Some of the other bugs are differences in how the systems work.  I doubt 3rd party software will ever be as easy to install on Linux as it is on Windows.   I see how that's a "bug" to a Windows user, but I see it as a different software paradigm.  But, having centralized software management means it is much easier to update "3rd party" stuff like flash or Real Player when there are security holes found in that software, it gets updated too.  That just can't happen in the Windows software management paradigm.  Note: I resisted the temptation to say Windows software mismanagement.....well, OK, I guess I did say it.

So what I'm trying to get aroud to saying is:

1)  I love Linux
2)  I hate ATI
3) This conversation has been incredibly open and respectful of the bugs put forth by this guy.  Compared to some conversations I've had on some mailing lists this is downright genteel.

--andy

---

### Post by klahjn on 2006-04-09
Reverse the tables a little:      
I tried Windows XP the other day and this is what i found missing:
Antivirus Software - For some reason I can't keep those bugs off my system
Spyware Remover - For some reason I get too many popups
Customized Blue Screen Of Death - I see a blue screen all the time, can i at least change it to purple or something?  Maybe it will lighten the mood.
Desktop Choice - Where is the option to use Gnome?  I can't find it anywhere
Graphic Design Program - Where is Gimp?  It doesn't install from the beginning?
Office Suite - You mean to tell me I have to install OpenOffice??
Xgl - Where is my 3d spinning Cube & Wobbling windows?
Games - You mean i only get 5 games to start?  Where is Konquest?  What about AisleRot Solitare w/ dozens of game options?  What about Atlantik?  etc...
Package Manager -  Where is the Synaptic on this?  I can't install programs from  Windows Update?
Money -  Where is the money i should have used to pay my bills?  I think someone robbed me....my wallet is empty.....

I am an ex-windows user.  I use linux now, and will for probably as long as i am able to.  This is just an example of how you can turn something "good" into something "bad".  I believe that windows,linux,unix,mac,bsd,solaris,etc each have thier own place.  I also believe linux has a place in my home, my heart, and my computer.  d;]   Just a thought.

PS- some of this was meant for humor.....so lighten up and laugh a little.  I also want to state that i believe the original poster does have some valid points, but i think also to point out that linux is constantly evolving, so the features you request in linux usually come into play ALOT faster than if you request them from windows.

---

### Post by puelocesar on 2006-04-09
I agree with him in some points, but the majority of them are manufacturers fault.

Something it's strange is what he said about external printer.

I configured the servers printer in my ubuntu dapper workstation very easily, only with gnome printers dialog and the printer address on network

---

### Post by j_baer on 2006-04-09
[QUOTE=KillerKiwi]An ex MS employee post : [http://keithcu.com/wordpress/?p=24](http://keithcu.com/wordpress/?p=24) basiclly summing up what he still thinks is missing:

[LIST]
[*]Multimedia often skips or doesn’t display properly in the browser (Gstreamer)
[*]Sleep and hibernate don’t work on my hardware yet (Driver Problemns)
[*]Gnome will mount NTFS, but I can’t browse because of permission problems
[*]Enabling external monitors isn’t easy (!!!!!!!)
[*]Remote printing requires manual textfile configuration
[*]Installing non-free software or drivers requires lots of manual work (!!!!!)
[*]Driver bugs ( as always )
[*]apt-get dist-upgrade hosed my machine
[/LIST]

Any one add to that list?[/QUOTE]

Good points but trying to get it right for every conceivable environment is probably not going to happen. I believe Microsoft would say hardware is cheap, upgrade if you want to run the lastest and greatest. Dell can hardly wait for Vista to be release.

Multi media has been a challenge of which only half is technical. On my computer MPlayer offers the best solution although Totem-Gstreamer is very close. Music players development under Linux is just crazy. Look at the choices ... Rhythmbox, Banshee, amaroK, xmms; new ones like "Listen"; and ones under development like Songbird.

I don't know about the non-free software part as I used what is provided and I am not constrained by the choices that I have. Probably not a fair comparision as I can remember being challanged by software installs under Windows and attempting to get a driver to work. 

I haven't had the problem with remote printing so I don't know what the issue is.

All in all delaying the release of Dapper to tidy up loose ends my well prove to be a stroke genius. The bugs will be fixed, it will only take a little time.

Cheers ...

---

### Post by Anthem on 2006-04-10
Good list of bugs.  I might have to follow his blog, he's a good writer.

---

### Post by EPOX123 on 2006-04-10
A good Flash editor would be nice ..... cant use linux for flash stuff.....

---

### Post by adam.tropics on 2006-04-10
I agree with klahjn and would go further to say, that in the world of MS we are talking about a paid, sometimes heavily paid for product. As such its development is largely closed, and there is not nearly enough 'community' involvement in windows; average users generally just get what they are given. 

We have a different agenda within Linux. As we find these 'missing' things, we are able to see them evolve, and perhaps help them do so. We don't have to wait until the next big (often expensive) release. We can choose at what development stage we start to use much of the software available to us, we can provide feedback, which genuinely taken notice of, and have a real effect on the product we end up using. At the end of the day, if something is missing in Ubuntu, then we the community should, and can do something to change that. And we don't need to wait four years to see the benefits either.

This really isn't a race to the finish. How Ubuntu progresses is pretty much up to us. If many MS users don't see the benefits in it then fair enough. In time, they may change their opininion. But for now, as a community in general (not specific to this post) we need to stop slating MS and concentrate that energy on aiding Ubuntu. More constructive by a long way.

Just an opinion.

Adam

ps that said, where ATI are concerned..........!!!!!!

---

### Post by gamma on 2006-04-10
I read his article today, pretty fair review. Yes there are issues, but things are getting better. The desktop is constantly getting new features that are going to lead to a better user experience. Ubuntu for one is making Linux easy and simple and Dapper is going to be an excellent release.

---

### Post by xrado on 2006-04-10
sleep and hibernate works on my laptop :) 

but printing is missing a lot of features compares to MS

..anyway i use linux all the time and its geting better and better :cool:

---

### Post by Jingo on 2006-04-10
[QUOTE=puelocesar]I agree with him in some points, but the majority of them are manufacturers fault.
[/QUOTE]

Whether it's the manufacturers fault or some open source problem doesn't matter... the problem persist. Drivers need to be stable whoever makes them. I figure most driver I need are stable.

I agree with this ex-MS guy, that **first problem** we need to find the bugs and priotize them. It might be very helpful if people could vote on bugs, but other scenarios might get better results. Anyway we need to find out which bugs really matter for the overall user.

**Second problem**: whos responsible. I don't care who solves bugs, as long as they get solved. I would say, those who ship the distro are responsible to the end-user. And I think Ubuntu/Canonical does a very good job!

---

### Post by KillerKiwi on 2006-04-10
> Enabling external monitors isn’t easy 
[http://sax.berlios.de/](http://sax.berlios.de/) <- need this in Ubuntu !

---

### Post by nocturn on 2006-04-10
[QUOTE=shu]I don't understand why some of you attack this guy. What he wrote is very objective. He pointed out those nasty little bugs that ruin whole image of Ubuntu and/or linux in general. 

There are some things that people are allowed to take for granted. And that's not because they came from windows. I've been using linux exclusively (except for games) for a 9 years and find those things annoying.[/QUOTE]

I didn't see anyone attack the poster (or author), but some people disagree as do I.

Some issues like the sleep/hibernate are mainly caused by manufacturers distributing machines that do not confirm to the ACPI 2.0 spec, even when they claim to do so.   A lot of these problems are caused by the use of the MS compiler for the DSDT tables, which results in a broken implementation.

Blaming the lack of packages for non-free, third party programs on Linux or Ubuntu is crazy.  That's like blaming MS for not providing a setup for Gaim/Vi/Tomcat/...

He makes a good point about the lack of GUI tools to configure X though.

---

### Post by nocturn on 2006-04-10
[QUOTE=Jingo]Whether it's the manufacturers fault or some open source problem doesn't matter... the problem persist. Drivers need to be stable whoever makes them. I figure most driver I need are stable.[/quote]

Good point, but how are we going to force for example ATI to write good drivers?  
But the up side is that there are options you can buy that have good Linux support.  For graphics, Nvidia is one, for CD/DVD burners, plextor is one.

What we as users need to do is reward the companies that support the OS we choose, be it by opening up specs (preferred) or by writing good drivers.  That is why I always buy Nvidia cards and steer clear of ATI.

---

### Post by adam.tropics on 2006-04-10
> What we as users need to do is reward the companies that support the OS we choose, be it by opening up specs (preferred) or by writing good drivers. That is why I always buy Nvidia cards and steer clear of ATI.

Dead right. Unfortunatly, I kind of expected this trip into Linux to be as successful as my 1998 (redhat) expedition, and so didn't really expect to still be here. !!! My own fault, lack of research I suppose!

---

### Post by Don_DiZzLe on 2006-04-10
Is it possible to resize an existing dapper ext3 partition with the install cd?

---

### Post by patrickfromspain on 2006-04-10
FAT32 and NTFS... I a regular user should have read access on both by default. About write permissions for fat32, personally I think it would be good, but I understand that many people think it isn't. 
Also I think a graphical tool to change fstab would be very good.. something to change permissions, read/write options and such things, to make it easy. For a newbie, it's not funny to first having to search how you do that, then opening gedit and manually write it.

About the external monitor thing... there should also be a graphical tool, to make it much easier.

Setting up a tv card is also a bit of pain for a newbie: algo searching in the forums or googling around, then searching which number your tv card is and then making the text file... not funny.

---

### Post by klahjn on 2006-04-10
[QUOTE=nocturn]He makes a good point about the lack of GUI tools to configure X though.[/QUOTE]

A gui tool to help configure X would be great.  Doesn't Suse have this?
A gui tool to configure fstab, would be great, but very difficult.  
A few more printing options would be great.  
I don't like the idea of skipping audio, but i don't have that problem.....?? Am I missing something?
These are all software implementations, and would be something that would make Ubuntu stand out.  These are all ideas from this thread.  I agree that linux is not only ready, but should be out there being installed on desktops.  I think that there are small, minor things holding back this initial push.  Some of it is "there are a few bugs", and some of it is just hesitating.  Could you imagine if Linux never released linux because he was afraid there might be a small bug?  there would be no linux.  If it were perfect, there wouldn't be another release, because perfect can't get any better.  Just a thought.

---

### Post by chill on 2006-04-10
When I want to upload a photo via Firefox. I click [Browse...] and I can select the file to be uploaded. The problem is that there is **only** the file-list view and **NO** thumbnalil view. Sad but true. Bit frustrating.

---

### Post by klahjn on 2006-04-10
[QUOTE=chill]When I want to upload a photo via Firefox. I click [Browse...] and I can select the file to be uploaded. The problem is that there is **only** the file-list view and **NO** thumbnalil view. Sad but true. Bit frustrating.[/QUOTE]

Yes, i notice this as well.  It brings up the gnome dialog box, and there is real estate on the upper left for an option like that, but it seems to be absent.  Definitely something to enhance user experience.  Hopefully by next bug release, or feature release of gnome that is included.  It has my vote as well.

---

### Post by Anthem on 2006-04-10
[QUOTE=gamma]I read his article today, pretty fair review. Yes there are issues, but things are getting better. The desktop is constantly getting new features that are going to lead to a better user experience. Ubuntu for one is making Linux easy and simple and Dapper is going to be an excellent release.[/QUOTE]
But the point of his article is that the desktop should be considered pretty much feature-complete, and everything lacking at this point isn't features, but polish.  It's bugs that are the killers right now, not features.

EDIT:  And I don't understand what the problem is with an X configuration tool.  Sax2 is GPL, and it works brilliantly.  Yeah, it's got SuSE colors (green and blue) right now, but so what?  It was originally a QT app, but the underlying code shouldn't matter.  Heck, even the command line options are better than dpkg-reconfigure.

EDIT 2:  Debian looked at porting it back in 2001, and the response was "dpkg-configure works just fine."

](*,)

[http://lists.debian.org/debian-x/2001/10/msg00001.html](http://lists.debian.org/debian-x/2001/10/msg00001.html)

---

### Post by scrook on 2006-04-10
[QUOTE=joshrobinson]i never use sleep or hibernate.. never have.. never will

i like how he calls himself a newbie when it comes to linux, thats pretty funny
but he blames things that are different then windows "bugs" instead of taking time to learn the differences

the reading of ntfs drives is extremely easy to acomplish, but to him its a bug ](*,)[/QUOTE]

He does bring up a valid point as to why NTFS partitions are not at least readable by user accounts out of the box. I understand not making it writable (especially since as far as I know Linux NTFS support is still incomplete) but if user accounts can browse the root file system, /usr, and everything else on the Ubuntu install, what justification is there to not be able to read NTFS?

---

### Post by prizrak on 2006-04-10
I agree with some stuff and not other. The ATI thing is actually a very very big issue. I'm in a market for a new laptop and the only nVidia based ones are widescreens, which I hate with a passion too bulky/crappy battery life as they tend to be higher performance. The only other choices are integrated crap like Intel, which is supported well by Linux but cannot run XGL/Compiz. There is also the S3 graphics but they are not that popular so we can pretty much disregard them. ATI is really the only choice for moderate performance/battery life laptops and not having good drivers (well they swallow on Windows too) isn't helping. Now I know many will say there is no need for XGL/Compiz on a laptop but I'd like to at least play with it :(

---

### Post by egon spengler on 2006-04-10
[QUOTE=gunksta]Well, unless someone has edited their comment, I don't think anyone has really attacked him at all.  [/QUOTE]

Aaah but you cheated, you actually read people's posts before commenting on them, that gives you an unfair advantage over shu

---

### Post by greenwom on 2006-04-10
Well I'm a new-bee and have been able to overcome with a little pain;
* all the video / audio streaming with only a few minor hickups.  
* Getting a Nvidia video card and dual monitors working
* a Wacom table
* various multibutton mice
* mounted windows drives 

With the forums and the IRC I've had no problems.  

What's missing is a shockwave player.  I hate that, I've installed wine w/ firefox and the plugin but it's a bit slow and lacking.

Scripts and the automatrix have made it real easy to setup a fresh box and get all the multimedia working upfront.  I do hate the dependance on W32codecs and libdvdcss.  I wish these weren't issuses.

---

### Post by gunksta on 2006-04-11
[quote=egon spengler]Aaah but you cheated, you actually read people's posts before commenting on them, that gives you an unfair advantage over shu[/quote] 
Sorry.  :-#  I hate it when I do that.  :-)

---

