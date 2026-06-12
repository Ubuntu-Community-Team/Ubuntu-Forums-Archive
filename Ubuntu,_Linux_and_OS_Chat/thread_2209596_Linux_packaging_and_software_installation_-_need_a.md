---
title: "Linux packaging and software installation - need a rethink ?"
date: 2014-03-06
forum: Ubuntu, Linux and OS Chat
---

### Post by QdFPLGz on 2014-03-06
Guys, I know I may start a flame war here, but being a programmer/developer myself
and a daily user of desktop linux, I hope there is a constructive discussion on this topic.

I thought of starting this thread after I faced a problem with VLC media player in Xubuntu 13.10
The default version which I installed from the repositories is 2.0.8 TwoFlower.
When I tried playing videos, it gave a choppy/jerky playback.
On my previous Ubuntu 10.04 desktop, VLC GoldenEye (1.0.x -I think) used to play videos smoothly.
So I thought of downgrading to this old version of VLC, but could not find out how.
In windows you just download the older version, uninstall the new version and install the old one.
Same with MacOS.
But in linux, if you want to install older .deb, all the other dependant .debs of various libs must
exactly match the version which the old .deb requires. This will never happen if you have upgraded to
newer linux distro version. Every 'libpkg.deb' has a version - 'libpkg-2.1.5-x86.deb' for example.
So its pretty much impossible to downgrade a particular software to older version unless it is
totally independent and contained in its own deb(s).

That leads to the next question - why doesn't linux not distribute apps in their own self contained pkg ?
The answer would be because most of the required functionalities by the app are usually available
in some lib or another which is already available in the linux distro's repositories, so why bother ?
This works well only if the version in the distro's repositories matches the app's requirements.
What if it doesn't ? Then the user may very well go to hell !

How to solve this problem ? Several things need to be done:
[1] All linux distro's must agree on a providing a set of core system/app libraries which will guarantee
to implement a set of api's/functionalities.
[2] The core libs must not have version dependencies. By this I mean that older apps can use the newer lib
and newer apps can use the older libs (but may be with a reduced feature set).
So, for example if you are installing an app .deb, it must not look for a specific lib version like 'libmpeg-1.0.5',
but must just look for 'libmpeg'.
[3] Any feature/api which the app needs and is not present as part of the core libs, the app needs to include it
in its own deb package and during install this must be installed only to the app directory and not on a system wide level.
This is to prevent other apps from using each others libraries. This may lead to duplicate libs being present
in different app directories, but that is OK, since we are more concerned about the user's ease
of installing apps rather than disk space.
Also, we hope that the core libs cover MOST of the dependencies of the app.

If these 3 things are done, then linux apps can also be distributed in a clean self contained pkg without
worrying about dependencies and associated problems.

I feel this change should happen, although I doubt it will,
because in the linux world, usually the ease and flexibility of the programmer/developer
is given more thought than that of the end user. This is especially true in the case of desktop linux.

---

### Post by deadflowr on 2014-03-06
You've basically described the idea behind [click packages]("http://askubuntu.com/questions/337969/what-are-click-packages").

More and/or less.

---

### Post by grahammechanical on 2014-03-06
> [COLOR=#000000]All linux distro's must agree on a providing a set of core system/app libraries which will guarantee[/COLOR]
[COLOR=#000000]to implement a set of api's/functionalities.[/COLOR]

First they need to agree as to which folders to put libraries in. There are differences of opinion, or so I have heard.

Your problem is that no one organisation controls the Free and Open Source Software ecosystem. And FOSS would be worse off if one monolithic corporation did control everything in FOSS. It was to get away from being forced to develop software according to the instructions of an overriding organisation that the philosophy of FOSS was worked out.

Regards.

---

### Post by ian-weisser on 2014-03-06
> **QdFPLGz said:**
> 
That leads to the next question - why doesn't linux not distribute apps in their own self contained pkg ?


It's a question that pops up every few months.

It's very possible to distribute apps in their own self-contained package, and deadflowr has pointed out that the new click packages include this funcionality. The tradeoff is that you (the developer) assume all support responsibility for the entire software stack that you install. If one of your dependencies uses a deprecated Unity API method, it's your problem instead of the community's problem.

This is different from the free Ubuntu Repositories and Software Center applications. On these, the community provides support, the Ubuntu Security Team provides security updates, and a mix of upstreams, volunteers, and paid engineers provide bugfixes and updates. The current release-snapshot method that binds users to a single version of software per release is a way to enhance overall release quality and reduce the community testing burden. The community simply lacks the paid and volunteer resources to test every possible combination of packages.

It's not about telling the user to go to hell. It's about telling highly-skilled specialty users that we lack the resources to test and maintain their unusual use case.

---

### Post by lykwydchykyn on 2014-03-06
Sounds to me like the whole problem is that downgrading is hard.  Probably this just needs to be fixed in the package management tools.

Throwing dynamic linking out the window and proposing to unify package management across all distros is a bit of an extreme solution to the problem.

---

### Post by QdFPLGz on 2014-03-06
> **deadflowr said:**
> You've basically described the idea behind [click packages]("http://askubuntu.com/questions/337969/what-are-click-packages").


Thanks for the link. I did not know about this. So does a click package include all the libs the app needs ?

> **grahammechanical said:**
> First they need to agree as to which folders to put libraries in. There are differences of opinion, or so I have heard.

Your problem is that no one organisation controls the Free and Open Source Software ecosystem. And FOSS would be worse off if one monolithic corporation did control everything in FOSS. 

Yeah, getting the various distro's to agree is difficult, but what about if initially Ubuntu takes the lead and says that we're going to support 'x' number
of core libs which are guaranteed to provide 'y' set of features and that they will be present in '/usr/lib' ?
Besides I'm not proposing that some monolithic org take control :), just that there has to be some sort of agreement to make life
of the end user in desktop linux easier.

> **ian-weisser said:**
>  The tradeoff is that you (the developer) assume all support responsibility for the entire software stack that you install. 

Exactly, that is the tradeoff that the dev has to agree for, to make the end-user life easier. 

> **ian-weisser said:**
> 
It's not about telling the user to go to hell. It's about telling highly-skilled specialty users that we lack the resources to test and maintain their unusual use case.
This is not an unusual test case, its a common use case. The user must have flexibility to install whichever ver. of software he desires without problems.
And it is not the use case of a 'highly skilled specialty user', any ordinary user may run into problems with a new ver. of software, what
will he do then ?

> **lykwydchykyn said:**
> Sounds to me like the whole problem is that downgrading is hard.  Probably this just needs to be fixed in the package management tools.

Throwing dynamic linking out the window and proposing to unify package management across all distros is a bit of an extreme solution to the problem.

This would be very difficult to fix using package mgmt. That is the whole point, current package mgmt relies heavily on versions being matched.
And I did not say that dynamic linking should be discarded, that would be bad.
The app can still dynamically link to the core libs provided by the OS as well as to its own libs in its directory.
Also, I did not propose to unify package mgmt across distros, just that all distros need to provide a set of core libs.
In fact what I'm driving at is to do away with package mgmt to install apps (gasp !)

---

### Post by lykwydchykyn on 2014-03-07
> **QdFPLGz said:**
> 
Yeah, getting the various distro's to agree is difficult, but what about if initially Ubuntu takes the lead and says that we're going to support 'x' number
of core libs which are guaranteed to provide 'y' set of features and that they will be present in '/usr/lib' ?
Besides I'm not proposing that some monolithic org take control :), just that there has to be some sort of agreement to make life
of the end user in desktop linux easier.


Ubuntu doesn't exactly excel at leading and or building consensus with the wider FOSS community (*cough*Mir*cough*).  In any case, there have been attempts to specify core libraries, you might want to look up the Linux Standards Base (LSB).  It's probably not as expansive as you're looking for, but it's something.

> 
This would be very difficult to fix using package mgmt. That is the whole point, current package mgmt relies heavily on versions being matched.


Package management has some flexibility here; at least in APT a package can specify a minimum version, or a list of possible candidates that can fill a particular dependency.  You can't get around the fact that software often requires libraries at a certain version to run.  If my application uses features only found in libfizzbuzz3.10 or higher, there's not much a distro can do about that but provide the library and make it a dependency.

> 
And I did not say that dynamic linking should be discarded, that would be bad.
The app can still dynamically link to the core libs provided by the OS as well as to its own libs in its directory.
Also, I did not propose to unify package mgmt across distros, just that all distros need to provide a set of core libs.
In fact what I'm driving at is to do away with package mgmt to install apps (gasp !)

I don't know and don't care to check if Gobolinux is still around, but they were doing something like this.  Check it out, maybe.

---

### Post by QdFPLGz on 2014-03-07
> **lykwydchykyn said:**
> 
If my application uses features only found in libfizzbuzz3.10 or higher, there's not much a distro can do about that but provide the library and make it a dependency.

If libfizzbuzz is part of the core libs that the OS provides then certainly the app may not run properly or run with a reduced feature set.
In any case some sort of warning should be displayed to the user while installing or running the app. This is OK, because even in windows
some apps require a specific ver. of OS. 
If libfizzbuzz is not part of the core libs then the OS should not take care of it, but the app must provide it in its own package.

But the main thing is that if the older ver. of the app used to run on libfizzbuzz2.10 then it must be allowed to install and
run with libfizzbuzz3.10. Backward compatibility should be a must.

---

### Post by mastablasta on 2014-03-07
a couple of things...

First this beta linux seems an interesting concept (excerpt from Distrowatch) :> 
GoboLinux is a modular Linux distribution - it organizes the programs in a new, logical way. Instead of having parts of a program thrown at /usr/bin, other parts at /etc and yet more parts thrown at /usr/share/something/or/another, each program gets its own directory tree, keeping them all neatly separated and allowing the user to see everything that's installed in the system and which files belong to which programs in a simple and obvious way

Next PC-BSD has PBI packages that will do that.

Finnaly support issue - i dissagree. i mean community does provide patches etc. but mostly developers themselves do it anyway. furthermore i use plenty of FOSS in windows and they are more or less same stuff we have here only packaged for windows. yet somehow they manage to have the old versions readilyl available that can be installed at will. e.g. old versions wesnoths available: [http://sourceforge.net/projects/wesnoth/files/?source=directory](http://sourceforge.net/projects/wesnoth/files/?source=directory)

furthermore i don't think anyone would be mad at developer not supporting 10 years old version of software. if all needed libraries are there and they still work in new system then software works. if there is some incompatibility you need to use newer version.

it is similar in windows. i can still install run programs written in the 90's that have absolutelly no maintenance. heck at work we are runnnig a DOS app in windows. it's monocromatic graphics and all... a simple database applicaiton with varios data etc. anyway point is it still works. even in 2014. judging by files application was made in 1992. i dare you to try and run an application from first linux desktop version. :-)  even some from 9.04 do not work well anymore.

one of the things businesses like about windows is it's support for really old stuff. there is no need to for some massive changes. software is mostly backward supported.

---

### Post by 3rdalbum on 2014-03-07
If your idea was so brilliant, it would already be widespread on Linux. It's not widespread and it's not a brilliant idea. What you are suggesting is the Windows XP model. That worked so fabulously for security for the last twelve years. Not.

Perhaps you should think more about the interplay between (2) and (3) in your original post. And perhaps think about it in light of the recent GnuTLS security flaw.

The last thing anybody needs is to be running software from 4 years ago with - potentially - 4-year-old libraries.

Package management has an elastic-band effect where it encourages the use of recent software versions, and then when it's no longer possible to run new software on the old OS it encourages upgrading to the newer OS. Keeps everyone using supported software that actually gets security fixes.

Being able to run an ancient binary of VLC is not a desirable feature. As it is, you can downgrade a few minor versions which is all you should need. You'll need to compile it yourself though.

Given a choice between package management and Windows-style binary installers with everything built in, cross-platform developers overwhelmingly choose the package management method on Linux. They COULD do it your way, and they are even familiar with your way... but your way is not the best way available on Linux.

---

### Post by QdFPLGz on 2014-03-07
> **3rdalbum said:**
> If your idea was so brilliant, it would already be widespread on Linux. It's not widespread and it's not a brilliant idea.  Of course its NOT a brilliant idea. Its a common enough idea to make the user's life easier. Who ever said its a brilliant idea ?   > **3rdalbum said:**
> What you are suggesting is the Windows XP model. That worked so fabulously for security for the last twelve years. Not.  The last thing anybody needs is to be running software from 4 years ago with - potentially - 4-year-old libraries.  An old app need not run with 4 year old libs. If the app is using a core lib, then the newer core lib in the OS would have implemented the same api's  but would have the required security fixes. But the way the api's are called would remain same so that the old app can still run on the newer lib with  all the security fixes. Of course for the libs that the app itself provides your point is valid and it would be the developers responsibility to provide the security fixes.  > **3rdalbum said:**
>  Being able to run an ancient binary of VLC is not a desirable feature. As it is, you can downgrade a few minor versions which is all you should need. You'll need to compile it yourself though.  Who are we to decide that is not a desirable feature ? For many users it IS a desirable feature. Isn't this what open source should be about ? Not just the developers but the user's freedom should also be considered. Telling an average joe user that he is free to COMPILE an ancient ver. of the software and use it is as good as saying that backward compatibility is NOT there in linux.  > **3rdalbum said:**
> .... Windows-style binary installers with everything built in  I did not say the we should go for windows style binary installers with everything built in. What I said was most of the functionalities would be met by the core libs provided by the OS. Only the rest of the functionalites would need to be provided by the apps own libraries.

---

### Post by mastablasta on 2014-03-08
when i was studying back in the *fin de siecle* i was very short for some cash. well i still am but for another reason...
At home we had a brand new P2 400Mhz with plenty ram and all but it was used by other family memebers. anyway i took this old 486 i had with Win95 on it. i could do anythign i needed to do on it except for listening to mp3. for some reason newer winamp just couldn't decode without stuttering. i then somehow found this really old version beta 0.8 or something. the menu and playlist looks really simple and all. and it was the only version that would run mp3 on that old maschine providing i didn't use any other program at the same time. so i just used that old version. it didn't look preety but at least i could listen to my favourite music while studying. this would have probably been impossible to do on linux. winamp at the time was already quite developed, it had themes and all. 

not long ago i installed Kubuntu on old mashcine. the mashcine is descent, but the GPU is 128 MB (ATI radeon 9200). it can't run the latest supertuxkart, just because the GPU doesn't have enough ram to load the textures. i could use the old version. in this case i am not sure if i could compile it (or if there are old binaries available). or in some way load lower res textures. eventhough in this case i am not sure if runinig old version is good at all since i remmeber it wasn't really so good back then as it is now.

---

### Post by ian-weisser on 2014-03-09
> **QdFPLGz said:**
> This is not an unusual test case, its a common use case. The user must have flexibility to install whichever ver. of software he desires without problems.
And it is not the use case of a 'highly skilled specialty user', any ordinary user may run into problems with a new ver. of software, what
will he do then ?

It may be common for you, a high-skill user. It's not common for the vast majority of users. Been here many years. Seen lots of ordinary user problems. Your problem is common only among high-skill users, seen it before.

More fundamentally, you seem to be describing a bug. "Version X works better than Version Y" seems to describe a regression of some kind.
Generally, we prefer that bugs get identified and fixed rather than restructure the entire packaging system and (unrealistically) expecting every past version of every lib and application to function with the current releases of Ubuntu.

Alternately, if older Version X is superior due to a design decision, then feel free to fork it and package it. Like MATE and other projects forked older versions.

---

### Post by QdFPLGz on 2014-03-09
Yes, you are right, technically it is a bug in the newer version.
But do you really expect an end user to report and file a bug and wait for it to be fixed in some future version ?
He would certainly prefer a quicker solution, and the most natural thing he would want to do is to try an older version.
Why does no one seem to acknowledge that there is a problem here? Why is everyone so adamant on insisting that the packaging system is great
and we need not touch it ? If this particular problem can indeed be fixed using the existing packaging system, thats great (though I think it would not be easy).
Otherwise we must be open to other solutions rather than saying - "the existing packaging scheme in linux is a wonderful thing, we cannot/ will not change it, 
if you have a problem with it then yours is a very rare problem ". Or "If you don't like it, go fork it..." yeah right, wonderful way to welcome newbies to linux what ?

---

### Post by CharlesA on 2014-03-09
Why not just do this?
[http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get](http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get)

I've had to backport stuff from sid to wheezy but I don't think that's everyone's cup of tea.

---

### Post by zeke2135 on 2014-03-09
I can see the argument that some users might want to run older software on newer releases of the operating system, but my frustration w/ linux packaging (meaning ubuntu packaging, which is what I'm familiar with), is the inverse. Namely, the lack of backwards compatibility of applications with previous releases of the operating system.

Shotwell, a program for managing photos, is a good example. I assume this is judged to be a mainstream application, as it is installed by default in ubuntu. I certainly use it often at home. I like shotwell, and I've used it for some time, but it doesn't have every feature I'd like, nor is it bug free. It seems to improve with each new release, so I would like to try newer releases. The release that is installed with 12.04 LTS is 0.12.x, and I believe the current release is 0.15.x, which is installed with 13.10. 

The problem is that as far as I can tell, the only way to try a newer release of a single application like shotwell is to upgrade the entire operating system. There is a ppa, with packages created ca. 11/20/2013, but nothing for 12.04 LTS. So in other words, ~19 months into the 5 year "long term support", one can no longer upgrade this application (and many others I'm sure). 

Now, I don't know if I need the "latest and greatest" version of this application, but the reality is that I have no way of even finding out,  short of upgrading the entire operating system. This is the thing that really boggled my mind when I first started using linux. 

I'm aware that applications like shotwell aren't developed by the people who distribute ubuntu. I don't know what sort of effort it takes to create "back-ports" for previous ubuntu releases, but I assume it's not trivial, or else they would be more common than they seem to be. I don't know if it's feasible for Canonical to assist small developers in creating back-ports of their default applications or to change the packaging system to make it easier to maintain backwards compatibility (I would guess not), but honestly the concept of long term support for the operating system is pretty meaningless if it also means that one is doomed to be using application software that never improves or advances for 5 years.

---

### Post by QdFPLGz on 2014-03-10
The very fact that an app has to be back 'ported'  to make it work on just the previous version of the **same OS , same hw, same arch** is fundamentally wrong.
And like you said, sometimes the only way to try out newer versions of the software is to upgrade the entire OS ! - a deal breaker for many users.
People will say "ubuntu upgrade is easy, it works seamlessly.."
NOT ! if you have a slow internet or if you have installed proprietary drivers.
And no sane user would want to upgrade the OS just for the sake of trying out a newer version of an app.

---

### Post by CharlesA on 2014-03-10
> **QdFPLGz said:**
> The very fact that an app has to be back 'ported'  to make it work on just the previous version of the **same OS , same hw, same arch** is fundamentally wrong.
And like you said, sometimes the only way to try out newer versions of the software is to upgrade the entire OS ! - a deal breaker for many users.
People will say "ubuntu upgrade is easy, it works seamlessly.."
NOT ! if you have a slow internet or if you have installed proprietary drivers.
And no sane user would want to upgrade the OS just for the sake of trying out a newer version of an app.

No, I only need to deal with backporting because I am dealing with Debian not with Ubuntu and Debian does not have PPAs like Ubuntu does. If someone already had a newer package that will work on your version of Ubuntu, all you need to do is add their PPA and install the package.

I only need to backport something from Debian Sid because I want to run a newer version of the program that is not in the repos for wheezy (stable) and I don't want to deal with compiling it from scratch. I backported smartmontools because the version in the Wheezy repos did not detect the drives on my RAID card with smartd. If I was running Ubuntu, I could either A) Use a newer release or B) Find a PPA for smartmontools.

I don't know about you, but I've got a box that I upgraded from 10.04 to 12.04 with no problems. Granted I wasn't using the propriety drivers, but those drivers have gotten better as Ubuntu has matured.

If you want to run an OS that has the latest and greatest, I would recommend Arch or Debian Jesse (testing) or Sid (unstable).

---

### Post by mastablasta on 2014-03-10
heh 12.04 this weekend just got soem updates and sound stopped working just like at my maschine at home. only this oen has completelly different sound chip. rebooting, restarting ... nothign helped. "dummy output" just like it happened to me at home. eventhoughg card is recognised it is not selected. really strange (will have to open another topic on this issue but i need to collect more data on hardware etc..). anyway in windows it would be a trivial matter to remove the updated driver and reinstall the older working one. not so much in linux. especially since probably a kernel upgrade caused this.

---

### Post by 23dornot23d on 2014-03-10
Every new release of Ubuntu I have to go into the development arena ..........

Just to check the 3d programs I like using will still work ..... 



K3dsurf another example of 3d software that is really good - you will not find it running in 14.04

some old ones too 16 bit editing 32 bit even in **Cinepaint**

Luckily Gimp is getting there now .......

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=32+bit+even+in+Cinepaint&ie=utf-8&oe=utf-8&q=32+bit+gimp+cinepaint](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=32+bit+even+in+Cinepaint&ie=utf-8&oe=utf-8&q=32+bit+gimp+cinepaint)

 ..... that was lost a long time back now

**Gnofract4d** ....... another ....... [http://gnofract4d.sourceforge.net/](http://gnofract4d.sourceforge.net/)

**K3dsurf** ......  [http://k3dsurf.sourceforge.net/](http://k3dsurf.sourceforge.net/)

Interesting subject ....... and it is something that is annoying when you do like using something
only to find that it no longer works anymore ........... in the latest release.

Is the program out of date though or unused , maybe they become unused because they just
get removed from the repos without so much as a murmur ....... ( what is the solution )
run them in Windows - because they will still work ok there ?

**Wings3d** for example ........... how do you get this running properly now in 14.04

How is the package manager set up to install this ?

---

### Post by lykwydchykyn on 2014-03-10
> **QdFPLGz said:**
> 
Why does no one seem to acknowledge that there is a problem here? Why is everyone so adamant on insisting that the packaging system is great
and we need not touch it ? 

What kind of response are you expecting?  You're not talking to the people who would make this happen.

OK.  Your idea is fine.  It would solve some problems.  It would create others.  Maybe the net result would be better, maybe not.  

In any case, it's not likely to happen without a herculean effort between a massive number of FOSS communities.

If you do decide to approach actual distro devs with this idea, expect it to be held to a critical examination far more strenuous than you've got going here.  You'd be asking people to accept many constraints, take on a lot of extra work, and throw out a lot of things that work perfectly fine 90% of the time for a few dubious benefits; they aren't going to do that uncritically.

---

### Post by ian-weisser on 2014-03-10
> **QdFPLGz said:**
> The very fact that an app has to be back 'ported'  to make it work on just the previous version of the **same OS , same hw, same arch** is fundamentally wrong.

It's not Ubuntu's fault, nor this community's fault, if a newer version of the application introduces a bug. Talk to that development team.

Backporting is merely the process of recompiling and retesting a newer version for the same OS, same hw, same arch. Indeed the process of community backporting is a *feature* so that everyone can benefit from a single user's testing work.

I don't see how the package manager is relevant to that discussion.

---

### Post by QdFPLGz on 2014-03-11
> **lykwydchykyn said:**
> What kind of response are you expecting?
Atleast some one acknowledging that there *do exist* some problems with the current packaging system.
The first step in solving a problem is to admit there is one.
No one is willing to even admit there is a problem with the way apps are currently distributed and installed in linux.
But I think slowly with the advent of Ubuntu for mobiles, the 'One click packages' will become more widespread
and hopefully desktop linux will also migrate towards such a model.
I might have lost this battle but the war might yet be won :)...
Time will tell....

---

### Post by CharlesA on 2014-03-11
Considering the developers do not post here, I doubt you will get the acknowledgment you seek here.

Try the dlevel mailing list.

[http://www.ubuntu.com/support/community/mailing-lists](http://www.ubuntu.com/support/community/mailing-lists)

---

### Post by lykwydchykyn on 2014-03-11
> **QdFPLGz said:**
> Atleast some one acknowledging that there *do exist* some problems with the current packaging system.
The first step in solving a problem is to admit there is one.
No one is willing to even admit there is a problem with the way apps are currently distributed and installed in linux.


I don't think anyone's denying there are problems with the way PM works.  It's just that the problems aren't compelling enough for anyone to want to champion such a massive change.  Not being able to install any arbitrary old version of a program, or install a 20-year old piece of software, is an irritation or annoyance.  It doesn't warrant imposing massive limitations and requirements on the developer community.  OK, that's my opinion, and you feel differently.   In either case, it's moot, because I can't do a thing about how distros package software.

---

### Post by mastablasta on 2014-03-11
well it's just a debate about Ubutnu, Linux and OS (i don't understand this thread to be a manifesto or some schedule, request or task) between some people with interest in the OS.  

to continue - the question to me is would the effort really be so massive? as i understand PBI packages the PC-BSD already has this option. would implementing similar thing in linux really require massive efforts? or could some things be ported over from BSD? the systems are relatively similar (though different) and ports betwen them are made in certain cases. they also borow from eachother or implement same things. both are open and free though licences are different.

---

### Post by 23dornot23d on 2014-03-11
If the applications have bugs ......... they should not run in the latest version surely 

So if Ktoon had a bug - it should not run
So if K3dsurf had a bug - it should not run on the latest version
So if Gnofract4d had a bug - it too should not run in 14.04 on the latest kernel released today

The only one I really need is Wings3d .... ( on 32 bit and its still giving me screen flickering problems - anyone have
any idea why Erlang and Wings3d are in conflict on 14.04 ......... )

And why cannot a package manager install a working version of Wings3d - is it out of date - is it buggy - is it not required ?

or were some Erlang programs added for Saucy that caused some problems ..... Erlang removes Wings3d by default now
so what is wrong with Wings 3d that the package managers do not like ? [COLOR=#ff0000]anyone know[/COLOR]

and to answer one comment - do you want 4 year old applications running - [COLOR=#ff0000]well Yes[/COLOR] - if they work and if they
are what the User is used to and would still like to use.

But not at the cost of over working the Developers ... the way is clearly forward ...... no backtracking to solve
problems they cannot solve .........

Applications .... are they really at fault ........... 

I just did a short video on things that are not included now - they run on my system 32 bit too ....... but will they
run on yours and how well does the package manager resolve the dependencies ....... or is that not its task ?

[http://youtu.be/UniZnxZn4so](http://youtu.be/UniZnxZn4so)

Not that I would disagree - if there are clear and easy instructions to follow to get an older packages working
that will do for me .... some people post some really good instructions ..... but the package manager is not bad
really ..... the list is only short for what it cannot install with one click.

---

### Post by lykwydchykyn on 2014-03-11
> **mastablasta said:**
> 
to continue - the question to me is would the effort really be so massive? 

Implementing yet-another-packaging-system would not be the hard part.  Re-read the original post.  The first point starts "All distros should agree".  You can stop right there and have a massive enough effort, but the remaining points involve requiring all libraries to be backwards compatible and all applications to degrade gracefully when compiled against older versions.  That's the massive effort I'm talking about.

---

### Post by mastablasta on 2014-03-12
> **lykwydchykyn said:**
> Implementing yet-another-packaging-system would not be the hard part. Re-read the original post. The first point starts "All distros should agree". You can stop right there and have a massive enough effort, but the remaining points involve requiring all libraries to be backwards compatible and all applications to degrade gracefully when compiled against older versions. That's the massive effort I'm talking about.

yes ok well all distributon would be a bit hard to achieve since they each use different kinds of package management.

libraries could come with packages and if they are the ones software works with then software would use them. or it could use new one ifthey work better. 

As i udnerstand libraries come along with windows programs because developers do not know if users already have them installed or not. and if they do have them installed they again do not know which version.

another thing i've noticed (talking about stable, and current system) is that there are many packages currently in the repository that do not work when installed. if you check the comments on some they have bad ratings as well as "not working" in the comment. surely those packages should have been removed (or updated). it is quite strange to me that packages like that are still in repositories of an LTS while some other (working ones) need extra repository (e.g. like some of those found on playdeb or only in PPAs).

---

### Post by lykwydchykyn on 2014-03-12
> **mastablasta said:**
> 
another thing i've noticed (talking about stable, and current system) is that there are many packages currently in the repository that do not work when installed. if you check the comments on some they have bad ratings as well as "not working" in the comment. surely those packages should have been removed (or updated). it is quite strange to me that packages like that are still in repositories of an LTS while some other (working ones) need extra repository (e.g. like some of those found on playdeb or only in PPAs).

This has more to do with the way the Ubuntu repos are pulled in from Debian.  As I understand it (and I could be fuzzy on some details here), basically the entire Debian repositories are brought in at the beginning of every release cycle.  Stuff that Canonical "officially" supports goes into main, everything else goes into Universe.  Some things in Universe have active maintainers that apply patches and so forth, but a lot of it is just pretty much default debian packaging recompiled for Ubuntu, with nobody actually tracking bugs or testing them within Ubuntu.

PPAs provide people a means of circumventing the Debian route for packages.  So if you have a package that has been languishing for some reason in Debian, and Ubuntu doesn't particularly care about it, it might be broken in the repos; but someone can upload a working version to a PPA without a lot of overhead.

---

### Post by CharlesA on 2014-03-12
Pretty much what lykwydchykyn said, unless something has changed because Ubuntu basically takes a "snapshot" of the Debian testing repos and porting things over at the start of the development cycle.

Sere here for an explanation of what each repository is for: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jussi-konttinen on 2014-03-14
It's easy, just install files in right folders : 
```
locate firefox
```:popcorn:

---

