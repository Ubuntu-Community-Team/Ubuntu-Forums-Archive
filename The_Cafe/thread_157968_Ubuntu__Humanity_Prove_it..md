---
title: "Ubuntu ? Humanity? Prove it."
date: 2006-04-10
forum: The Cafe
---

### Post by zugu on 2006-04-10
Why do the documentation, the wiki, the forum users, the IRC users almost ALL assume the standard Ubuntu newbie has internet access?

Why aren't there guides for offline upgrades? I thought Ubuntu was made for everyone, not for everyone with internet access.

Of course, there's the Automatix CD, but many people suggest not using it, because it's not safe. There are some DVD images of the universe and multiverse repos. But this is the time-consuming way.

There are people that have no money to have an internet connection, there are people who just thought about giving Linux/Ubuntu a try on the oldest machine in the attic (with no internet acces). Why won't you make it easier for these people?

Instead of dealing with so many people daily, asking "how to install files with no internet connection",  consider just adding some lines in the documentation; it would make wonders, you know.

Too bad these things happen, because Ubuntu is a great piece of software.

---

### Post by jrib on 2006-04-10
I'm not seeing how it can be done.  How can you get upgrades without access to the internet?  Even to burn cd images, you would need to download them from somewhere.  You do get free upgrades through shipit every 6 months I suppose.  But do you have any ideas for other ways to upgrade?

---

### Post by zugu on 2006-04-10
[QUOTE=_jason]I'm not seeing how it can be done.  How can you get upgrades without access to the internet?  Even to burn cd images, you would need to download them from somewhere.  You do get free upgrades through shipit every 6 months I suppose.  But do you have any ideas for other ways to upgrade?[/QUOTE]
Of course, updates can be found on the internet. One could get the updates on a machine with internet access, burn them on a CD (or other media) and then use the CD on the connection-less Ubuntu machine.

But just take a look at the documentation here (this is just an example)

[http://help.ubuntu.com/starterguide/C/ch03.html#codecs](http://help.ubuntu.com/starterguide/C/ch03.html#codecs)

I think there should be a link somewhere labeled "Offline Updates" or "If your machine can't access the internet, read this". Also, every package on packages.ubuntu.com should be labeled as "existent/non-existent in the default installation/server installation".

Somewhere, in the wiki I think, it is stated that there are other methods to install packages, but "apt-get" is everywhere.

So if I'm online, I can get every update I need, easy and fast. If I'm permanently offline, the update process becomes a hell, not just because I need to move files from one machine to another, but because I need to find out by myself what to do, there's no documentation for this.

---

### Post by NeghVar on 2006-04-10
I'd have to agree with jason here. Its a great idea but how would we do it? To even know about Ubuntu you have to have acess to an internet connection. Even if you have to go to a friends or a net caffe you still need a net connection somewhere. A new version is released every 6 months, and it would be great to implement your idea if you gave someway of doing it.

What would you have them do, most of the things aren't created by them, they didn't write openoffice or firefox, should they send out a new image of the repositories everymonth to everyone? that idea doesn't make a whole lot of sense. You can't scale down the idea and say well just updates of want I have/want, but how do they know what you have.

Simply put it can't be feesably done, its possible I suppose but resource intensive, the Linux for human beings refers to the fact that they will never charge for updates or for the full install. Take a look at Starcraft (first example that came to mind) Battlenet is freee right, check out the back of your case, net fees are your responsibility, they offer the service but its your responsibility to get to that service. It may sound mean but as I said, it can't be reasonably done otherwise.

---

### Post by zugu on 2006-04-10
NeghVar, did you read my post before your post?

---

### Post by jrib on 2006-04-10
[QUOTE=zugu]Of course, updates can be found on the internet. One could get the updates on a machine with internet access, burn them on a CD (or other media) and then use the CD on the connection-less Ubuntu machine.

But just take a look at the documentation here (this is just an example)

[http://help.ubuntu.com/starterguide/C/ch03.html#codecs](http://help.ubuntu.com/starterguide/C/ch03.html#codecs)

I think there should be a link somewhere labeled "Offline Updates" or "If your machine can't access the internet, read this". Also, every package on packages.ubuntu.com should be labeled as "existent/non-existent in the default installation/server installation".

Somewhere, in the wiki I think, it is stated that there are other methods to install packages, but "apt-get" is everywhere.

So if I'm online, I can get every update I need, easy and fast. If I'm permanently offline, the update process becomes a hell, not just because I need to move files from one machine to another, but because I need to find out by myself what to do, there's no documentation for this.[/QUOTE]

Can we make the assumption that a person has another machine with internet access but for some reason it does not work in ubuntu?  For that, if the machine is debian based, I guess it is not difficult.  If it is something like windows then it becomes difficult because you have to go and ensure that you have all of the dependencies yourself.

When I first saw this thread: [http://ubuntuforums.org/showthread.php?t=149303](http://ubuntuforums.org/showthread.php?t=149303) , I thought that this would be a way for people to use windows and have a python script download all of the debs for whatever packages they needed.  I have not worked on it much, since I don't really feel like booting into windows to test things.  So far the only work has gone on in my head.  But I encourage you to join in and help with that.

And if we can't make the assumption that a user has internet access on another machine (even if it is a friends), do you think it is reasonable to say that upgrading every 6 months through shipit is acceptable?

---

### Post by NeghVar on 2006-04-10
> NeghVar, did you read my post before your post?

You posted your second one while I was typing. As for the first one I'm asking you, with no connection HOW do you upgrade, you have to have someway of getting the updates. Your asking for a wiki on a redundant idea. Your premise is:

> There are people that have no money to have an internet connection, there are people who just thought about giving Linux/Ubuntu a try on the oldest machine in the attic (with no internet acces).

Ok fine, if thats your premise for wanting an offline guide to updating, but your version of offline means NO internet connection at all. How would you get the program in the first place, if you can think of a way then join in and help write a wiki or how-to on it. Im sure people would help you if you could show someway to make it happen.

The best possible way I can think of would be to go to a net connection, download updates to the harddrive, make sure you have all of the dependancies, burn it all to a cd/dvd, go to your ubuntu box, use synaptic and tell it to look on the cd for the repository then do it that way. Ive seen a guide arround, ill take a look for it and see if I can find anything.

---

### Post by xyz on 2006-04-10
Not updating for a few months would not enable anyone from "getting into" Ubuntu (GNU/Linux at large).
-buy a Linux magazine at the store may list where you could (post) mail to ask for Live/Install CD to be sent to you 

-no money at all? There may be a town/school librairy in your town where you may find what you're looking for (HOWTO's,postal (Ubuntu) address,students who may be using Linux...)

-suggestion to our great (already immensely helpful!) Ubuntu Community to issue a short (very short=not too much work) written Howto along with the Live/Install Cd's so that internetless folks can familiarize themselves with the fantastic product we are lucky enough to be able to download.


I just dug up the enveloppe in which came my Ubuntu CD's:

It says on it:

> If undeliverable, please return to
CC International
SPI UK 077
4002 Basel
Switzerland
I guess writing them a short letter should get Ubuntu Cd's into your mailbox.
...just ideas!Good luck.
where there's a will, there's a way...some folks say!You can order 1,5,10...Cd's for the same o price,postage included in the 0.

---

### Post by meborc on 2006-04-10
i don't want to be a party-pooper, BUT - ubuntu may not be the distribution for you... it is clear that ubuntu is for users with internet access... there are other distributions which do not rely on internet connection as much as ubuntu...

you can try the basic (mother) debian... it has about 13 (or whatever number) cd's for installation so that you have all the packages you need on cd's...

do not say that ubuntu is not all about humanity... you can not possibly say that... it depends on you weather this distro suits your needs or not... ubuntu is on 1 cd so you get the basic platform where to DOWNLOAD via apt new programs as you need them... try some rpm based distros where there are alse add-on cd's available... it is too much trouble to maintain ubuntu without internet... i know... i have tried...

---

### Post by az on 2006-04-10
1.  Ubuntu works perfectly fine without an internet connection.  It ships with a complete, although streamlined, suite of software, more so than windows, actually.  It cannot be all things for everybody out-of-the-box.  That is impractical.  Would you prefer than you download all 15 cds that it would take to include all the packages from all the repositories?

2.  It would be cool if there was an online ressource where you could click on a package and download it along with all its' dependencies.  This may happen at some point - it is up to the community.

3.  The documentation generally does not reflect the non-networked user's needs since you would need to download stuff to install extra packages.

---

### Post by Buffalo Soldier on 2006-04-10
sorry, wrong post.

---

### Post by GeorgeAD on 2006-04-10
I'm a complete beginner who's just posted a question on exactly this topic, so I hope you don't mind me saying something (and maybe asking a couple of questions - my post is three pages back already!) 

Basically I agree with zugu. My problem is that my (win?)modem doesn't seem to work with Ubuntu and I have no broadband connection; that must be very common. I can of course download stuff to windows (dual boot system) and then put it on cd, and I have access to university computers. So getting files off the internet and onto a cd is very easy - but having Ubuntu itself on the internet is very hard. 

Re. the documentation, I only installed Ubuntu a couple of days ago, and pretty soon got to more or less the page linked to in zugu's second post. It wasn't obvious to me that an internet connection was essential, a note saying so would definitely have been nice. 

Also, being used to Windows and downloading a zip file to install, I assumed that even if the package wasn't on the install cd, it could simply be downloaded on another computer and burned onto a cd which could then be used like a repository in synaptic. Now I get the impression that's not the case, or at least not at all straightforward. Is that right? 

> "The best possible way I can think of would be to go to a net connection, download updates to the harddrive, make sure you have all of the dependancies, burn it all to a cd/dvd, go to your ubuntu box, use synaptic and tell it to look on the cd for the repository then do it that way. Ive seen a guide arround, ill take a look for it and see if I can find anything."

That guide would be very useful!

cheers, 
George

---

### Post by bonzodog on 2006-04-10
One of the original factors in the design of linux was the fact that it was for the internet. You can use Linux with no net connection, but updating is difficult at best, and linux is very much Net-centric, no matter which distro you use. It has often been said (not here I think), that Linux was designed by the net for the net. I have found myself in the past without a net connection in linux, and all you can do really is either officework, (comes on install CD!), or play some basic games. To get the most out of any distro, IMO, you need a net connection, and preferably a broadband one at that. I used linux though on a 56k modem for a number of years, but I never powered the machine up without connecting it to the net.

---

### Post by K.Mandla on 2006-04-10
Personally, I think zugu's got a good idea. I've been stuck trying to use Ubuntu on machines that had no internet connection, and it would have been nice to get updated packages that I could download, burn to CD and install. 

I know exactly zero about the way the updates and packages are posted, but couldn't a regular update "cluster" be made for downloading, specifically for folks who can't get a continuous connection? 

If you had a 256Mb USB drive, for example, and could download a self-installing cluster of updates every couple of weeks, it could keep off-line Ubuntunuts and 56Kers from suffering. You could go to your local library, download the cluster, copy it to your USB key, take it home, copy it off, double click (now that the gDebi tool looks like a reality), and you're up to date.

Perhaps it's already been suggested, or it's just not a possibility. Anyway, just an idea.

---

### Post by towsonu2003 on 2006-04-10
[QUOTE=azz]
2.  It would be cool if there was an online ressource where you could click on a package and download it along with all its' dependencies.  This may happen at some point - it is up to the community.[/QUOTE]
This is a very good idea. I only wish we had a proper way of filing this as a feature request in Malone... Wiki's "IdeaPool" is stupid at best (sorry for the rant)... 

Having dial up at home (ubuntu) but broadband at elsewhere (MS), I understand the OP's concern, and would love such a service (possibly to be built on packages.ubuntu.com)

---

### Post by NetMatrix on 2006-04-10
Wait... I know... let's send everyone CD's with updates who ask for them so when they finally get the CD in the mail the updates are outdated.  DUH!!  This is not even a viable issue.  If you don't have an internet connection (at all) you don't have to get updates (most of the time) because a lot of them will be in regards to security (over the internet) double DUH!!

---

### Post by aysiu on 2006-04-10
Anyone who wants to help, please help:

[https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD](https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD)

Anyone who needs an add-on CD, you can try this one for now:

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

---

### Post by Iandefor on 2006-04-10
> There are some DVD images of the universe and multiverse repos. But this is the time-consuming way. Is it more time-consuming than downloading and installing software from universe and multiverse across a nonexistent connection :)?

What if somebody offered repositories on disc- ie, you send somebody a quarter and they'll send you a CD with a certain section of universe or multiverse?

Good point in your post, but, as a tip, it's always best to err on the side of friendlieness :-D. I was mildly offended by the tone of the original post when I first read it.

@aysiu: the second link claims it's a "blender add-on" CD, not an Ubuntu add-on CD. Which is it?

---

### Post by xenmax on 2006-04-10
> 2. It would be cool if there was an online ressource where you could click on a package and download it along with all its' dependencies. This may happen at some point - it is up to the community.
Just thinking aloud here.. If synaptic can dump to a file about all packages installed  on a machine which is say inaccessible to internet, then user takes this file to another computer which has internect access where you can access a sort of an online version of Synaptic which resolve all dependencies so that it recognizes all required packages to be downloaded, and if user wishes to, download them to a sort of installer file, which can be taken back to original computer and running Synaptic on that file should install all packages in installer and since dependencies are already taken care of, everything should be fine... perhaps this idea is already floating around - i dont know - but just an idea i wanted to share.

---

### Post by aysiu on 2006-04-10
[QUOTE=Iandefor]
@aysiu: the second link claims it's a "blender add-on" CD, not an Ubuntu add-on CD. Which is it?[/QUOTE] I'll double-check with Tikal, but I believe it's a Ubuntu add-on CD.

She was probably thinking *Breezy* but typing *Blender.*

---

### Post by John.Michael.Kane on 2006-04-10
@Iandefor you would have to find someone willing to maintain up to date repo's on dvd for every version of ubuntu that an enduser chooses. we must take into account that there was still warty user when 5.10 was released who did not move to the next upgrade. the same may hold true for dapper. so one would have to maintain a dvd of the repos for say 5.10-dapper. this is including all codecs aswell, and a willingness to mail said dvds. plus you have to factor in are these users going to pay what ever fee's are charged for the media dvd's arent cheap, and sending 12+ cd's can also be costly.

just my thoughts..

---

### Post by prizrak on 2006-04-10
There is no need for updates on a non-networked machines. All official updates (with the exception of backports) are security updates, non-networked machines don't need security updates. As far as old machines go Ubuntu is crappy for that, it's a pretty heavy distro even with XFCE. DSL or Puppy would be the way to go on those. 
Ubuntu is not a universal solution for everyone, some of it's features are better than others and it's lacking where some other OS's might excel, that is normal.

---

### Post by K.Mandla on 2006-04-10
[QUOTE=prizrak]non-networked machines don't need security updates.[/QUOTE]
Except, perhaps, for that one glitch that left the installation password written in plain text in a file embedded down in a directory on a clean Breezy machine. ... ;)

---

### Post by NetMatrix on 2006-04-10
Posted by K.Mandla
> Except, perhaps, for that one glitch that left the installation password written in plain text in a file embedded down in a directory on a clean Breezy machine.

Who's going to find it if the machine isn't networked?

---

### Post by K.Mandla on 2006-04-10
[QUOTE=NetMatrix]Who's going to find it if the machine isn't networked?[/QUOTE]
Perhaps someone else who signs on to the computer?

---

### Post by mstlyevil on 2006-04-10
Ubuntu is a great internet distro. Suse or mepis would probally be a better fit for someone that wants a free distro but has limited internet access.

---

### Post by aysiu on 2006-04-10
[QUOTE=K.Mandla]Except, perhaps, for that one glitch that left the installation password written in plain text in a file embedded down in a directory on a clean Breezy machine. ... ;)[/QUOTE] Anyone who has physical access to your machine and a little knowledge can do all sorts of damage. She doesn't need to know your password.

---

### Post by NetMatrix on 2006-04-10
Originally posted by aysiu
> Anyone who has physical access to your machine and a little knowledge can do all sorts of damage. She doesn't need to know your password.

My thoughts exactly.

---

### Post by htinn on 2006-04-10
Ubuntu is Linux for Humans (Humans who don't mind running Linux on their current desktop, that is)

---

### Post by Iandefor on 2006-04-10
[quote=SD-Plissken]@Iandefor you would have to find someone willing to maintain up to date repo's on dvd for every version of ubuntu that an enduser chooses. [/quote] Not up-to-date. Ubuntu's a stable distro- the version numbers in the repositories don't really change. You could download the repositories when it's first released and it would be the same by the next release (This is ignoring updates)

> 
we must take into account that there was still warty user when 5.10 was released who did not move to the next upgrade. the same may hold true for dapper. so one would have to maintain a dvd of the repos for say 5.10-dapper. Costs for keeping a couple DVD iso's from previous releases would be minimal. Again, maintainance is minimal for a stable distribution like Ubuntu.

> 
this is including all codecs aswell, What do you mean by codecs?

>  and a willingness to mail said dvds. plus you have to factor in are these users going to pay what ever fee's are charged for the media dvd's arent cheap, and sending 12+ cd's can also be costly.
 [100 Single-Layer DVD+R]("http://www.newegg.com/Product/Product.asp?Item=N82E16817132367")'s cost about $39.99 on Newegg. Divide $39.99 by 100 to get the cost per disc- $.3999, or about $.40. Let's assume the cost of shipping a DVD is something like $3.00. Costs for acquiring and shipping a DVD with Universe on it, then, are about $3.40. Let's bump the charge up by $1.60 for profit, to make it a worthwhile venture for whomsoever might choose to do this, and you wind up with a copy of Universe available to somebody without an internet connection for about $5. I know that, prior to getting an internet connection for my home, I'dve happily paid $5 for a copy of Universe on a DVD.
And if you really need security updates, you could release an updates disc every couple of months.

> just my thoughts.. Good thoughts, at that.

---

### Post by YuHoo on 2006-04-10
[QUOTE=Iandefor]
And if you really need security updates, you could release an updates disc every couple of months.[/QUOTE]

Security isn't much of an issue if you can't get the updates through the internet in the first place. This idea that Ubuntu, as well as other linux distros, are so reliant on the internet while other operating systems are not is a fallacy. Every time I install Win2000 or WinXP, I have to download approximately 100+ mb of updates. I had to download about 15mb for Ubuntu. Modern operating systems assume that you have internet access, period. Whether this is right or wrong, it's nearly impossible to work around. The universe on DVD is a good idea though, I'd gladly pay even $50 to get all of it so I can tote it around since you've got yourself a hell of a lot of options with it. 

For documentation, show me an operating system that doesn't rely on the internet and I'll show you an operating system older that Win95. Microsoft's knowledge base, Apple's help line, the only thing they have that linux does not is a phone line. Even with an A+ certification number they still belittle you like you're a monkey smashing the keyboard. But when it comes down to it, if you pay less than $25 for a complete operating system and programs supported, you're really doing good.

In addition to that I'd recommend that there is a dvd full of stable releases of drivers. Nothing ground breaking, just fill it up with what works.

---

### Post by prizrak on 2006-04-10
There is a DVD of Ubuntu on the main site which includes alot of randomness (I think at least never really checked it out).

---

### Post by htinn on 2006-04-10
The DVD for Ubuntu has about the same amount of material as Fedora Core 5.

---

### Post by prizrak on 2006-04-10
[QUOTE=htinn]The DVD for Ubuntu has about the same amount of material as Fedora Core 5.[/QUOTE]
That tells me nothing :) 
I think the easiest and most obvious solution to this would be a DVD provided by Canonical that has all the extra stuff (probably more than one DVD).

---

### Post by unf on 2006-04-10
Humanity is killing all the fun. :D I must be psyco...:confused: [-(

---

### Post by htinn on 2006-04-10
Just one dual-layer DVD should be plenty (as long as you make one for each particular machine type).

---

### Post by benplaut on 2006-04-10
As has been mentioned a few times, ubuntu is not the ideal distro for a machine without internet.

Besides, you probably aren't going to be doing much with a non-networked machine. Office apps and tetris? What would you really need that isn't on the disk (other than mp3, i guess. Then again, what media server isn't networked!?)

---

### Post by fuscia on 2006-04-11
um...how did you start this thread?

---

### Post by duality on 2006-04-11
[QUOTE=zugu]Why do the documentation, the wiki, the forum users, the IRC users almost ALL assume the standard Ubuntu newbie has internet access?

Why aren't there guides for offline upgrades? I thought Ubuntu was made for everyone, not for everyone with internet access.

Of course, there's the Automatix CD, but many people suggest not using it, because it's not safe. There are some DVD images of the universe and multiverse repos. But this is the time-consuming way.

There are people that have no money to have an internet connection, there are people who just thought about giving Linux/Ubuntu a try on the oldest machine in the attic (with no internet acces). Why won't you make it easier for these people?

Instead of dealing with so many people daily, asking "how to install files with no internet connection",  consider just adding some lines in the documentation; it would make wonders, you know.

Too bad these things happen, because Ubuntu is a great piece of software.[/QUOTE]


Are you from Microsoft or something?  ](*,)

---

### Post by NeghVar on 2006-04-11
> Are you from Microsoft or something?

Most likely as I yet to see him return.

---

### Post by LaBOOdha on 2006-04-11
well I agreed with the original post in many respects.
Ubuntu docs wikis weem to be a little convoluted for a linux newbie. there ought to be a basic overview of linux then ubuntu and getting started instead of accidentaly finding out about automatix and driver issues.
I'm just glad I figured out how to get a dual boot going because I need to rely on the evil XP when I don't feel like hunting for a way to get a dvd to write to or play or some old camera or toy microscope. 
I couldn't even find a good hand holding guide to dual booting I just had to hope that partition magic wouldn't do anything too strange or the couple of linux flavors I tried. one nearly locked me out of booting back to XP.
and yes a simple "CD/DVD distro relies heavily on a working internet connection" written on the case might be nice. 
I was foolish enough to believe I could just quickly play with linux without having to invest in a lot of infohunting mazework time.  to do it for real I mean, Knoppix worked pretty well I have to admit-live from cd. I even got the wifi to work right away which I didn't in Ubuntu.
But Overall its pretty cool to have applications to play with without having to be tempted to borrow from the windows or mac underworld.

"first they came for the recreational software users, then for the dvdcopyists, then for the illicit mp3 people, ....etc etc
the way this country is going I'm afraid Ubuntu won't be used for humanity but for the surveillance info distribution the Military/Internet was orginally designed for. What an easy way to harass dissenters or environmenatalists but through their poverty and love of music. ...oh I'm sorry LiHippieNux that little 2gb postage stamp is a felony 'round heeruh.

well anyways its a nice name and thought, hopefully freedom will learn how to play dodge ball at last.

sorry for the rambling tendencies

and so it follows... where do I find Public Domain content for sale on dvd?! looked on ebay and all I saw was some newsreels and sucker books about selling it. where is the magic website with links?

---

### Post by aysiu on 2006-04-11
I, too, was frustrated with the availability of documentation for Ubuntu... until I found the Ubuntu Guide. Unfortunately, that wasn't really maintained after Hoary.

The Wiki is a mess organizationally, but once you find stuff there, the instructions tend to be good.

I wrote up a PDF guide I would have found helpful last May. Maybe you would have found it helpful to when you started:

[http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

When I revise it for Dapper, I'll be sure to mention something about the downsides of not having an internet connection.

---

### Post by Mustard on 2006-04-11
[QUOTE=aysiu]I, too, was frustrated with the availability of documentation for Ubuntu... until I found the Ubuntu Guide. Unfortunately, that wasn't really maintained after Hoary.
[/QUOTE]

The Breezy version of the Ubuntuguide lives on at this link...

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by nickle on 2006-04-11
I am surprised that many seem to think people cannot do much without internet. You can write books, documents, play games, design graphics, keep a calender, do your accounts, build databases,  perform vast amounts of scientific work, listen to music, play movies, copy cds, store photos, watch and record TV and many other thing I have never done or even thought of doing. Of course for all this you need a good OS and good software, but no internet. 
Ubuntu is clearly not designed for this -without broadband - and I have to agree, the humanity stuff does ring a little hollow when we think that broadband access will remain the domain for a small percentage of humanity and certainly a smaller percentage than those that who will have access to computers and want to do useful things with them...
The humanity stuff is one of those warm soft feel good marketing things. Nothing much more. 
Having said that, the Ubuntu community as represented on the forum has grown into something impressive. So while Ubuntu might not be "the real thing", it is managing to give some momentum to Linux and the OS movement, both of which have a reasonable claim to the "humanity" title...

---

### Post by prizrak on 2006-04-11
[QUOTE=nickle]I am surprised that many seem to think people cannot do much without internet. You can write books, documents, play games, design graphics, keep a calender, do your accounts, build databases,  perform vast amounts of scientific work, listen to music, play movies, copy cds, store photos, watch and record TV and many other thing I have never done or even thought of doing. Of course for all this you need a good OS and good software, but no internet. 
Ubuntu is clearly not designed for this -without broadband - and I have to agree, the humanity stuff does ring a little hollow when we think that broadband access will remain the domain for a small percentage of humanity and certainly a smaller percentage than those that who will have access to computers and want to do useful things with them...
The humanity stuff is one of those warm soft feel good marketing things. Nothing much more. 
Having said that, the Ubuntu community as represented on the forum has grown into something impressive. So while Ubuntu might not be "the real thing", it is managing to give some momentum to Linux and the OS movement, both of which have a reasonable claim to the "humanity" title...[/QUOTE]
Anyone with internet access tends to feel like that, I didn't use to have Inet till 97 and was just fine. I cannot use any of my machines now if they are not on the network I feel completely and utterly lost. The humanity thing is not that anyone and everyone can use it.  It is more along the lines of Ubuntu being free both in price and freedom, it comes with no proprietary stuff out of the box and is free for anyone to get as well as being covered by the GPL making it available to use it for anything you want. Humanity doesn't mean no net access is needed. Having said that, Ubuntu is quite loaded out of the box, the only thing would be codecs but those are easy enough to install w/o Synaptic (in fact that's how I did it). As mentioned before an offline box has no need for updates. Now if you are talking about lack of software available offline then the problem is that Ubuntu is not Windows or OS X you can't just go to your local $COMPUTERSTORE and get software for it. FOSS movement is very net centric as it is pretty much the only way to bring so many people from so many locations together in one big community.

---

### Post by zugu on 2006-04-12
Well, some people wanted me back, so here I am :D 

No, I am not "from Microsoft or something", I am just a plain Ubuntu user like many others. I am quite surprised to see that my original post has received so many replies. But I think I was quite misunderstood, and that may be because of my bad English. When I meant "updates", I actually meant "just any piece of software that can be found in the repos", not just security patches and updates. I also meant no harm to any user on this forum, and I want to assure everyone of my total respect. Sorry if my original statement seemed harsh, I wanted it to be constructive. And actually it might be constructive, given that there was interest in it.

All I wanted to say was that the wiki and the documentation could include some enhancements. 

There could be a page that could show the users what to do in order to install basic things, such as multimedia support, java, PDF support etc. 
There are also a LOT of good HOWTOs on these forums that could make it in the documentation, or at least in the wiki. 

In other words, show me what synaptic actually does when installing let's say, gstreamer0.8-mad, so that I can do it myself (or "here's a page that tells you what packages to download and in what order to install them so that you can get gstreamer0.8-mad up & running without frustration, and without having to mock install it so that you can see what dependencies are/are not installed on your system" or "here's gstreamer0.8-mad, here are it's dependencies; keep in mind that the one listed with yellow are already installed on the Ubuntu default installation, but if you made a custom install, you can always find them on the CD").

I'm not asking for "Firefox 1.5.0.1 + OpenOffice latest version + more"  DVDs delivered at my door, I'm just asking for a better user experience. The community can do this.

Cheers

---

### Post by Sushi on 2006-04-12
[QUOTE=zugu]Why do the documentation, the wiki, the forum users, the IRC users almost ALL assume the standard Ubuntu newbie has internet access?[/QUOTE]

related to this: Why does everyone here assume that the user has a computer? "Humanity"? I think NOT!

;)

---

### Post by prizrak on 2006-04-12
zugu,
There is another thread there about the same issue, dealing with an add-on CD. If you put it this way, it is a good idea to have an extra CD that can be downloaded with extras on it. Even better a DVD cuz it has more stuff (although an older no net machine might not have a DVD drive)

---

