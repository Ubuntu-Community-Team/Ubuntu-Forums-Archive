---
title: "gimp 2.4 stable is out"
date: 2007-10-24
forum: Repositories &amp; Backports
---

### Post by Fabioamd87 on 2007-10-24
when we can see it in gutsy?

---

### Post by Sef on 2007-10-24
Doubtful it will in Gutsy.   Maybe a backport,  However, it will be in Hardy Heron, 8.04.

---

### Post by Fabioamd87 on 2007-10-24
i must wait another 6 mounths????
backport for me is ok

---

### Post by KhaaL on 2007-10-24
I just stumbled on the news of gimps new release as i was unwrapping a 3d model and needed a image editor (kubuntu dosen't come with one, grunt!).

Would be real nice if someone could throw out an unofficial deb!

---

### Post by Fabioamd87 on 2007-10-24
but is strange that there are too much different with the rc that are in ubuntu

---

### Post by Asraniel on 2007-10-24
> **KhaaL said:**
> I just stumbled on the news of gimps new release as i was unwrapping a 3d model and needed a image editor (kubuntu dosen't come with one, grunt!).

Would be real nice if someone could throw out an unofficial deb!

there is krita in kubuntu. it's also very good, but does not have the same goal as gimp has. They are similar, but different. I use both, depending on what i have to do

---

### Post by Fabioamd87 on 2007-10-24
i use ubuntu and usually i use out of the box apps....

anyway... gimp in ubuntu is only an RC can contain bug... is better to update to the stable...

is possible to make a request somewere?

---

### Post by melange on 2007-10-24
> **Fabioamd87 said:**
> i use ubuntu and usually i use out of the box apps....

anyway... gimp in ubuntu is only an RC can contain bug... is better to update to the stable...

is possible to make a request somewere?

which bugs are you talking about?

Anyway - it's *not* possible to make a request to anyone. Ubuntu only upgrades applications between new versions - so unless you find a very critical security flaw in the RC you have to wait for 8.04....or just install it manually.

---

### Post by Fabioamd87 on 2007-10-24
i hope in backport...

---

### Post by melange on 2007-10-25
> **Fabioamd87 said:**
> i hope in backport...

If you want to know how to install GIMP 2.4 on Gutsy I've written a short guide here: [http://www.bottiger.com/install_gimp_2_4_on_ubunutu_7_10](http://www.bottiger.com/install_gimp_2_4_on_ubunutu_7_10)

---

### Post by Fabioamd87 on 2007-10-25
im an ubuntu user not a gentoo user :D

i wont to install it by typhing

sudo apt-get update
sudo apt-get upgrade

---

### Post by JRd1st on 2007-10-25
> **melange said:**
> which bugs are you talking about?


The Filter Pack tool doesn't work correctly in the RC3 version.  Look at the difference between the Windows 2.4 Final version and the RC3 one in Ubuntu.

There are other things too, that were fixed since RC3.

---

### Post by MadMan2k on 2007-10-25
its in my PPA. but take care what else you install from there...

---

### Post by Fabioamd87 on 2007-10-25
> **MadMan2k said:**
> its in my PPA. but take care what else you install from there...

other are unstable?

---

### Post by melange on 2007-10-25
> **JRd1st said:**
> The Filter Pack tool doesn't work correctly in the RC3 version.  Look at the difference between the Windows 2.4 Final version and the RC3 one in Ubuntu.

There are other things too, that were fixed since RC3.

I can read the changelog. But my point is, those things are really minor things, and the RC are very stable.

If you are a really serious artist, and those small changes truly are important to you, I refuse to believe it can be a problem to spend an hour compiling the gimp from the source.

I see myself as a quite heavy user, but really - the biggest difference I feel is the new splash screen.

---

### Post by Fabioamd87 on 2007-10-25
gimp is not a critiic package, can't corrupt all the system... than can be backported...

---

### Post by JRd1st on 2007-10-26
> **melange said:**
> If you are a really serious artist, and those small changes truly are important to you, I refuse to believe it can be a problem to spend an hour compiling the gimp from the source.

Apparently, you were born knowing how to compile programs.

It's two weeks since I decided to reconfigure my system so I'd have a free drive to install Ubuntu on.  The reason I decided to take the plunge is because GIMP doesn't run all that well in Vista, for some reason (although it runs 100% better on a lesser machine with XP :confused: ).  I'm having to learn a whole new way of doing what would be the simplest tasks in Windows, which I don't mind because up to now it's been reasonable.  But, now I'm told that if I want the latest stable version of the program that decided me on trying a new OS, that I'll have to wait 6 months or compile it myself.  It's not like everyone that uses programs is a programmer, you know.  I mean, get real!

1. Maybe I don't know how to compile in Linux.  That CAN be a problem
2. Perhaps knowing what all the "dependencies" are, when the guy that DOES know how to compile the program doesn't know himself, IS a problem for me
3. Having to wait an hour to compile is no problem, but waiting an hour when you don't know if it's going well because you don't know what you did in the first place, may be a problem for some. 
4. Microsoft may have its' problems, but at least they don't expect people to go all over and search for object libraries, or whatever, before they can have the latest stable version of something.
5. If you're such a "heavy user" of GIMP, then why is this n00b, me, the one that reported the Filter Pack bug, only a few days ago.  It WASN'T a problem for me to go through the trouble of reporting to the GIMP community. (and they didn't tell me "screw you, fix it yourself") 

This thread is not a very good inducement for regular people to use Ubuntu, nor is it a good way to introduce someone to the Ubuntu "Community".  

Maybe I expect too much, but is it a good idea for users only to be able to install packages that are "pre-ordained" by some "higher power" for them? ](*,)  And THIS is the better way? :confused:

So guys, next time you feel the urge to get all elitist on a n00b, wake up and smell the Windows.  :-k

EDIT: sorry for the rant, but it's the way things look from "down here"

Anyway, I may try to do this sometime today, but the tutorial doesn't explain this step

> 5. then compile the gimp (this may take an hour or two): make  Just make?  No arguments?

Also, before I get into this, I'll try to fine the "for sure"  list of those dependencies.

---

### Post by CarpKing on 2007-10-26
I think "sudo apt-get build-dep gimp" should install all the packages needed to compile from source, though looking at it the list seems really long.  If you don't want to do that, I'm sure it won't be too long before a deb from somewhere becomes available (apparently MadMan2k already has one in his repository).  You might also keep an eye on getdeb.net.

---

### Post by JRd1st on 2007-10-26
> **CarpKing said:**
> I think "sudo apt-get build-dep gimp" should install all the packages needed to compile from source, though looking at it the list seems really long.  If you don't want to do that, I'm sure it won't be too long before a deb from somewhere becomes available (apparently MadMan2k already has one in his repository).  You might also keep an eye on getdeb.net.
Thank you! 

I think I'll try doing the compile because no matter how badly I mess up, I can use Acronis TI (run from Windows) to fully restore back to where I started.  But I want to learn this stuff, because, as nuts as it seems, it looks as if things will be this way in Ubuntu-land for a long time to come.  :?

EDIT:  I installed GIMP 2.4 stable from [MadMan2k]("http://ubuntuforums.org/showpost.php?p=3629938&postcount=13")'s PPA and it's just fine, so far.

For those even more n00bish in Ubuntu than I am, look at MadMan2k's post, but to add when you get to System >> Administration >> Software Sources you hit the **Third-Party Software** tab, then **Add** and insert the line from MadMan2k's site.  When you get the updates available icon, hit it then de-select the Mesa-utils (I didn't know what they were so . . .) related entries and update the GIMP related ones.

It seems to work just fine and **YES** the Filter-Pack fix makes a huge difference because now you can see what's going to be applied and not go blindly.  Also the stable release seem to run better overall, for some intangible reason.:razz:

Thanks to all that helped! :)

---

### Post by Fabioamd87 on 2007-10-26
what the essence of the backports? Gimp should be updated here.
if million of people make this request someting can change?

---

### Post by rfurman24 on 2007-10-26
Why would they include release clients and then not upgrade?  I would just as soon have the older stable versions.

---

### Post by nightfrost on 2007-10-28
I've been going through this thread now in annoying frustration. I just don't understand the reasons for not upgrading a package from RC to final! It's incredible, I mean the only upstream changes are *bug fixes*. I mean, there are no new features that might possibly cause breakage. Sheesh.

I understand that some very basic low level packages should never be upgraded in the same release, such as gcc, glib, perhaps not even mesa and so on. But gimp?? Come on!

I can't help wondering; doesn't ubuntu even include the latest bug fixes from gnome 2.20.1?

---

### Post by exploder on 2007-10-28
Enable the Gutsy Proposed repo to get Gnome 2.20.1.

---

### Post by 4KvRMU7Nnv on 2007-10-28
just compiled and installed on gutsy.  It was quite easy, took about an hour to make though.  Works perfectly.

---

### Post by linuxlizard on 2007-11-01
Just get it from here:

[http://www.getdeb.net/category.php?id=4](http://www.getdeb.net/category.php?id=4)

---

### Post by Fabioamd87 on 2007-11-01
getdeb is supported by canonical or ubuntu team?

---

### Post by linuxlizard on 2007-11-01
no but so what?- neither is compiling from source. Getdeb does an excellent job keeping software for ubuntu up to date. If you have problems, you can always use synaptic to remove getdeb packages.

---

### Post by Fabioamd87 on 2007-11-01
is possible to request a package for backporting?
i wont all out of the box

---

### Post by duruttye on 2007-11-01
What if want to install it on Ubuntu 7.04.
I already tried it on 7.10 but it broke my system completly, instead of characters, there were squares...
So, anyone has 7.04??

---

### Post by duruttye on 2007-11-01
Well, this is really annoying.

Tried to compile the 2.4 packages, but it always finds some errors. I'm stuck with the glib libraries, new ones, old ones.... and so  on.
Downloaded from getdeb, but no use, unmet dependencies... but those libraries are installed....

This is really stupid...
not beeing able to upgrade some aplications, like we're forced to upgrade the distribution, this sounds like some old windows trick...

---

### Post by linuxlizard on 2007-11-02
> This is really stupid...
not beeing able to upgrade some aplications, like we're forced to upgrade the distribution, this sounds like some old windows trick...

It's not ubuntu's fault. It's the nature of open source software. Each thing is developed independently- like your glib libraries are developed by one group of volunteers, gimp by another, and ubuntu by another. When gimp comes out with a new release, they use the latest dependencies (like the latest glib for example). And when ubuntu comes out with a new release, it uses the latest gimp and dependencies. It's a chain reaction. And it illustrates *exactly* why it's unreasonable to expect ubuntu to constantly update packages after a release. And it illustrates *exactly* why they have a new release with updated software twice a year, so at least your software isn't too far out of date- some distros release yearly. When you start updating packages willy nilly, things can break. And it isn't just a matter of the gimp being updated- that's probably an easy one this soon after a gutsy release- but it's a matter of thousands of packages, each a link in a chain. If something goes wrong you can have a chain reaction and a big mess. When ubuntu comes out with a new release, a lot of effort and time is spent getting all the packages to work together in harmony without crashing anything on the system. It's not simply a matter of grabbing the latest gimp, open office, gnome and slapping some artwork on it and calling it a new release. It's a matter of bug fixing and making all these packages work together. Yet so many of you guys seem to expect them to be able to keep all of it constantly updated to the minute and still all working harmoniously between releases. That's just not going to happen unless you use a distro like gentoo where everything is compiled from source. And even then bad things happen with dependencies on user's systems- you've got to know your stuff and have a lot of spare time bug fixing and for compiling and keeping things up to date to run a distro like that. Ubuntu make's it easy for you.

Did you try getdeb's  gutsy package for gimp on gutsy gibbon or only on feisty? If you tried it on gutsy it shouldn't have broken anything- should work just fine. You probably tried to compile it from source rather than use the package for gutsy. If the getdeb did cause problems in gutsy, you can simply remove it with synaptic and you can be back to where you started from. 

For that matter, what's the big deal? Apps are updated constantly with bug fixes, the gimp being no exception. Is there a new feature that really makes a difference to your work? Is the one that comes standard on gutsy crashing on you? Mine isn't and I've already used it several hours for some web work, and I haven't bothered installing the getdeb package yet... 99.9% of the userbase are fine waiting 5 1/2 months for the latest version at that time when the next ubuntu comes out. For those who aren't- getdeb does a good job keeping stuff up to date...

---

### Post by gimpguy2000 on 2007-11-07
> **linuxlizard said:**
> It's not ubuntu's fault. It's the nature of open source software. Each thing is developed independently- like your glib libraries are developed by one group of volunteers, gimp by another, and ubuntu by another. When gimp comes out with a new release, they use the latest dependencies (like the latest glib for example). And when ubuntu comes out with a new release, it uses the latest gimp and dependencies. It's a chain reaction. And it illustrates *exactly* why it's unreasonable to expect ubuntu to constantly update packages after a release. And it illustrates *exactly* why they have a new release with updated software twice a year, so at least your software isn't too far out of date- some distros release yearly. When you start updating packages willy nilly, things can break. And it isn't just a matter of the gimp being updated- that's probably an easy one this soon after a gutsy release- but it's a matter of thousands of packages, each a link in a chain. If something goes wrong you can have a chain reaction and a big mess. When ubuntu comes out with a new release, a lot of effort and time is spent getting all the packages to work together in harmony without crashing anything on the system. It's not simply a matter of grabbing the latest gimp, open office, gnome and slapping some artwork on it and calling it a new release. It's a matter of bug fixing and making all these packages work together. Yet so many of you guys seem to expect them to be able to keep all of it constantly updated to the minute and still all working harmoniously between releases. That's just not going to happen unless you use a distro like gentoo where everything is compiled from source. And even then bad things happen with dependencies on user's systems- you've got to know your stuff and have a lot of spare time bug fixing and for compiling and keeping things up to date to run a distro like that. Ubuntu make's it easy for you.

.


While quite true to some respect, if you want people to use something, then make it work. Better yet, make things work together. 

Isn't it the cry of open source over Windows that says be free, use Linux, etc....I'm sure you know the rest. However, when complaints are made, it's the same old story, don't blame this, don't blame that, if you don't like it, go back to Windows, go to another distro, etc.... which is an option of course, but to get people to WANT to use Linux and support an open source community, that old adage had BETTER change, else it's only going to fall behind. 

With the Ubuntu Boom especially,  and the dawn of so many user friendly  distros coming around, an actual chance to grab hand fulls of Windows users and get them into the Linux community has finally happened, then you get comments like yours which stem from the old country Linux style when it actually held true, and much of it still does but it's not a GOOD thing.  It is changing and they have to learn that it cannot be per individual only any more. 

I would think if ANY distro or package, such as Ubuntu and Gimp TRULY wanted users, they could communicate a bit, hell it's been done before between others and with good reason. Gimp is NOT an entity of it's own. Without an OS Gimp is pile of crap as is any other package\app.  SO , this tells me, it had better LEARN to get along with others.  This goes for ALL open source.  

It may be the harsh new reality but as the expanding Linux users and Linux flagging users saying .... "hey we are user friendly and free", they have to begin to realize what they are saying. Ubuntu and others are doing much better for User friendliness but still have to be able to back it up else they will lose more than gain.  

In my eyes, this is the true time for Linux to grow and finally kick Microsoft's blue , red, yellow, green, ***.  But if the thinking goes as you have stated, this will NEVER happen completely or close to. 

That said, I am not saying you said all these things, etc... nor do I totally disagree with some of your statements. What I am saying is, I don't think Linux can stay in it's own corners of the world anymore and needs to combine some efforts.

---

### Post by rsambuca on 2007-11-07
You guys all want Ubuntu to be something that it isn't.  The developers take a snapshot of Debian sid every six months, stabilize it as much as possible, add their own little touches, the latest gnome and then release it.  On to the next snapshot.

If you can't wait six months to upgrade to a new version of a program, then you have choices.  You can find a deb and install it manually, you can compile it from source, or you can move to a new distro.

Many of you who want the latest versions of programs immediately after release should be using a rolling-release distro.  Some of these are Debian Sid, Arch Linux, Gentoo, Foresight linux.  

Ubuntu is what it is, and does it very well.  Please stop crying about it. :)

---

### Post by gimpguy2000 on 2007-11-07
> **rsambuca said:**
> You guys all want Ubuntu to be something that it isn't.  The developers take a snapshot of Debian sid every six months, stabilize it as much as possible, add their own little touches, the latest gnome and then release it.  On to the next snapshot.

If you can't wait six months to upgrade to a new version of a program, then you have choices.  You can find a deb and install it manually, you can compile it from source, or you can move to a new distro.

Many of you who want the latest versions of programs immediately after release should be using a rolling-release distro.  Some of these are Debian Sid, Arch Linux, Gentoo, Foresight linux.  

Ubuntu is what it is, and does it very well.  Please stop crying about it. :)

Hmmm. Ok, there is a point that things are what they are. But when you say people are crying about it, isn't it these cries that software applications, OSs, and such take into consideration to make a better or more likable OS\app ?  Ok, there is a means to go about it without yelling and gnashing teeth, I can agree with that. 

I think the point some make and I tend to agree, is that something like the new Gimp 2.4 won't work with Feisty is a bit  odd. Ok, it works with Gutsy, fine and there is a choice to use 2.3 in Feisty. However, it sort of made me a bit upset as I can't install the latest Gutsy for a number of reasons and had to use the "W" word to even try the new Gimp which oddly enough works quite well in XP.  

Now, you have an open source application that will not work in a slightly older Ubuntu, yet it will work in an even older XP. This tells me, and not saying it's either fault, but that Linux distros\apps needs to start working a bit better amongst each other as I stated above. 

I think this can only benefit Linux in my opinion.

---

### Post by CarpKing on 2007-11-14
> **gimpguy2000 said:**
> Now, you have an open source application that will not work in a slightly older Ubuntu, yet it will work in an even older XP. This tells me, and not saying it's either fault, but that Linux distros\apps needs to start working a bit better amongst each other as I stated above. 

I think this can only benefit Linux in my opinion.

The reason it won't work in Feisty (well, it will, but only if you go through a lot of trouble) is that all the libraries and such are different versions.  Upgrading GIMP would mean upgrading all of these, and could result in parts of Gnome that you didn't upgrade not working because they want older versions.  In Windows all these dependencies are bundled together (which is why GIMP is such a large download).  This is how Windows programs tend to work as well.  This may seem like a good plan, but it results in a lot of redundancy.  Imagine having different copies of every Gnome and GTK library for each program in Gnome.  That would take up a lot of space and would be very inefficient.

---

