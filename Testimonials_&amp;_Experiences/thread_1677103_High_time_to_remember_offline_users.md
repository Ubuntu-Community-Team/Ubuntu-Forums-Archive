---
title: "High time to remember offline users"
date: 2011-01-28
forum: Testimonials &amp; Experiences
---

### Post by EthioJOB on 2011-01-28
Recently I got me a newly assembled PC with a 500 GB hard disk, and one of the first things i did was to allocate a larger portion of it to Ubuntu; almost 300 GB (I'm still struck by the fast boot-time). Yes, I also installed Windows 7 too for dual-boot. Somehow, there is now an ugly reality I'm on the verge of facing that I can't do much with Ubuntu. How can I? There are lots of software that I need to make good use of it I can't get them for Ubuntu, all because I couldn't afford my own internet connection. With Windows, I can get software easily from someone. Sometimes I would have to download it from elsewhere after paying a little money, which is not much of a problem. But I can't even do that with Ubuntu, at least not without any hassle, with all the dependency issues, not knowing where to find codecs (I can't even listen to music with it!), you name it.

The way software is downloaded in Ubuntu is great; really convenient and easy, but requires one fundamental condition that one has an internet connection. Unfortunately, this is not an easily met criteria for a lot of us in developing countries. My ability to purchase a PC of my own is still a big deal for me (cost me a hefty part of my savings!). Going for a personal internet connection would be too much of a stretch on my limited finance. 

I'm not criticizing Canonical, for I believe the current means of availing software best recourse they could've taken to promote Ubuntu during its initial stages. At first, presumably most of the users were those that had internet connection which enabled Canonical to facilitate the 'Software Center' and/or 'Synaptic' way of downloading software, both which require internet connection. Now, however, Canonical must realize that with the global niche Ubuntu is achieving, developing countries are potential targets as much as nations in which Macs are common. I think it would do good if Canonical started focusing on achieving offline accessibility to Ubuntu applications for those that can't afford their own internet connections. What's the point of free software if it can't cater for and allow us disadvantaged people to participate in the open source community? The community would be a really 'limited' type.

Its time Canonical started looking into this issue. It could, for example, look into [keryxproject.org]("http://keryxproject.org") and help out there (I raise my hat for Chris, who started this project) or integrate it if possible, or it could create a more convenient way of downloading all the dependencies along with the main software in a single package (to be filtered out by some sort of script during installation), or any other way. Believe me when I say open source is the best alternative waiting out there for poorer countries. I believe that users in developed nations could also benefit if such a solution is implemented, at least partially.

The idea of adopting Windows as my main working OS is something I really, really dislike. But I have my limits.

---

### Post by Blutkoete on 2011-01-28
I agree that Keryx should be included if people pick it during install, I've a limited bandwith myself.

EDIT: Of course it's no use installing it on your computer, you'll need it on an USB stick; but the files for that should be there.

---

### Post by EthioJOB on 2011-01-29
Using Keryx can be a little confusing itself for some newbies; it could be more user-friendly (I'm not being critical, just pointing out room for improvement. I know the developer is very busy). Generally I feel that Keryx is somewhat sidelied from the major Ubuntu software. At least it could be promoted and supported by Canonical. The point is, there doesn't seem to be any or there's only little attempt to avail Ubuntu software for offline users or users with limited bandwidth, and this problem needs to be tackled.

---

### Post by mastablasta on 2011-01-29
i believe it is possible to download repositories on a couple of DVD's. or at least more important programmes.

Also starting out with Ubuntu Live DVD might be a better way to go than liveCD option for the "offliners".

then there are the .deb files. and i believe the tarrballed files also have it all in them. or am i wrong?

but all in all you are right. these linux systems are really web-o-centric. maybe because their origin is in servers. i also find it ridiculous that they didn't put a dial up agent (takes so little space) by default to ubuntu CD. plenty regions of the world don't have broadband fiber optics yet.

---

### Post by amsterdamharu on 2011-01-29
+1 on the DVD, I've tried to customise the live CD and found that 700MB is gone quite fast when you have gnome and some other software (Open Office for Mint).

The DVD is filled up with more packages, to put the whole repository on DVD is a bit crazy because programs are constantly updated and it'll be out of date while you compose it. And of course the size of the repository, I'd imagine it wouldn't fit on 5 or 6 DVD's.

When you are at a place that has Internet you can start with a live CD, install stuff and then copy all the files from /var/cache/apt/archives/ to a USB, then copy it from the USB to your computer. One problem still is that you have to run apt-get update on both machines to make sure you'll get the newest versions.

If you have a friend that has Ubuntu and a working Internet connection you could copy the /var/cache/apt/archives/ files to USB and onto your computer from his/her computer.

---

### Post by bjem85 on 2011-01-29
It could also me a matter of packaging of the DVDs, I tried Debian off a DVD (DVD #1 only) and it had virtually everything I wanted on the DVD to set it up to a level that I would set up Ubuntu to.  I've considered downloading one of the Ubuntu DVDs to avoid having to be on the internet all the time to install packages but the ones Canonical provide appear to be language packs only, at least according to their own documentation.

---

### Post by terry_gardener on 2011-01-29
EthioJOB

my idea is either try and get the repos on dvd or just the required software you need as stated above by other people.

another idea is if you know someone with internet access you could take a bootable cd or usb, boot into it and then open synaptic select the programs you want and then use the generate package download script. run the script and then just copy all the files to dvd or usb drive for use where you dont have internet connection, this also solves dependency issues.

---

### Post by oldfred on 2011-01-29
Take a look at aptoncd 
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Location of downloaded debs
/var/cache/apt/archives/

---

### Post by arunb on 2011-01-31
How can Windows 7 be useful for you if you do not have an internet connection?

I believe Windows 7 is as much dependent on the internet as Linux..

---

### Post by mastablasta on 2011-01-31
> **arunb said:**
> How can Windows 7 be useful for you if you do not have an internet connection?
 
I believe Windows 7 is as much dependent on the internet as Linux..
 
 
Programmes are packed in single .exe file with all libraries included. there is never a dependancy issue when you install windows because you get all libraries in the file and more. often they duplicate them which is one of the reasons windows porgrammes are bigger.
 
yeah you can easilly run windows and just have a DVD with porgrammes you need. windows programmes usually don't have so many updates (every week or 2 weeks).

---

### Post by EthioJOB on 2011-01-31
One upside to using Ubuntu is this forum. People would try to help. I appreciate your efforts.

Of course, I won't stop looking for ways to get the softwares offline, but let's take a moment to lie back and look at our posts, and how a fairly average (offline) computer user would think of the available installing methods.

> When you are at a place that has Internet you can start with a live CD, install stuff and then copy all the files from /var/cache/apt/archives/ to a USB, then copy it from the USB to your computer. One problem still is that you have to run apt-get update on both machines to make sure you'll get the newest versions.Well, I don't think getting permission to boot off a software that the owner of the internet cafe probably hasn't heard of is  as easy as you think. I've heard of very few internet cafes that use Ubuntu though, I could probably use that (of couse, that would depend on the connection, the version of Ubuntu, a probably a few others).

> If you have a friend that has Ubuntu and a working Internet connection you could copy the /var/cache/apt/archives/ files to USB and onto your computer from his/her computer.Wouldn't we all love to see Ubuntu being commonly used by people? Its hard enough to convince them to use something 'different'.

> It could also me a matter of packaging of the DVDs, I tried Debian off a DVD (DVD #1 only) and it had virtually everything I wanted on the DVD to set it up to a level that I would set up Ubuntu to. I've considered downloading one of the Ubuntu DVDs to avoid having to be on the internet all the time to install packages but the ones Canonical provide appear to be language packs only, at least according to their own documentation.Yes, that had me hesitating too for a while. If its got more than languages and software I could actually use, then its a viable option, but downloading something the size of a full DVD would be very inconvenient. (I use Shipit to get my Ubuntu CDs. I don't think I can afford such a large download at once.)

> another idea is if you know someone with internet access you could take a bootable cd or usb, boot into it and then open synaptic select the programs you want and then use the generate package download script. run the script and then just copy all the files to dvd or usb drive for use where you dont have internet connection, this also solves dependency issues.I could ask a couple of friends of mine to use their laptops with live USB in internet cafes for this. Perhaps this is the most practical method.

Once again, thank you all for your efforts to help. But my concern here is that the available offline software access is still pretty inconvenient. Its like saying 'Ubuntu is a great OS, but you'll need internet connection'. The '*but*' is one big catch, at least for some people. I'm only saying that I wish Canonical took time to facilitate a simple and available mechanism to download software without all the hassle. Windows could claim (though I hate saying this) an advantege in this regard. You go to any of the numerous websites out there, click on the download link of whatever software you want, and voila (though there are chances of mishap, its a working solution for now; at least mostly). Not so with linux distros. I'm just venting my concern. I know there are others who are affected the same way. As for me, I won't give up; at least I can come to this forum for help.

Cheers!! :p

---

### Post by cascade9 on 2011-01-31
> **bjem85 said:**
> It could also me a matter of packaging of the DVDs, I tried Debian off a DVD (DVD #1 only) and it had virtually everything I wanted on the DVD to set it up to a level that I would set up Ubuntu to.  I've considered downloading one of the Ubuntu DVDs to avoid having to be on the internet all the time to install packages but the ones Canonical provide appear to be language packs only, at least according to their own documentation.

For offline use, debian is so much better than ubuntu its not funny. You can get the whole repo if you want to d/l 5 DVDs. 

> **EthioJOB said:**
> Yes, that had me hesitating too for a while. If its got more than languages and software I could actually use, then its a viable option, but downloading something the size of a full DVD would be very inconvenient. (I use Shipit to get my Ubuntu CDs. I don't think I can afford such a large download at once.)

You shouldnt have to d/l them all at once, or even d/l them at all. There are lots of places that will sell you a debian DVD- 

[http://www.debian.org/CD/vendors/](http://www.debian.org/CD/vendors/)

When a new version of debian 'stable' appears there is normally a few linux magazines with at least 1 of the DVDs as a cover disc, and at least one which is a 'special version' with 2+ DVDs and all about that release. The bonus in that case is that you normally get whole magazine with articles, on that version at least some of which could be useful.

---

### Post by mastablasta on 2011-01-31
heh, no african countries in the list (have to admit i did a quick look). htough 5 DVDs for 10$ +shipping doesn't seem so much...
 
what i found interesting is that Mr. Shuttleworth organised vending maschines for Ubuntu CD in Africa (obviously ment for users with no Internet access). i wonder what those had pre-installed and how they worked out for people with no internet access. :-)
 
---
anyway i think .deb files do the trick.

---

### Post by EthioJOB on 2011-01-31
> **mastablasta said:**
> heh, no african countries in the list (have to admit i did a quick look). htough 5 DVDs for 10$ +shipping doesn't seem so much...
 
what i found interesting is that Mr. Shuttleworth organised vending maschines for Ubuntu CD in Africa (obviously ment for users with no Internet access). i wonder what those had pre-installed and how they worked out for people with no internet access. :-)
 
---
anyway i think .deb files do the trick.

That's interesting. Didn't hear of it. Its a good thing, though the Shipit service also works good. The CD is limited unless you're using it for basic functions (that's what I'm using). The 5 DVDs however seem to be a fair price (for a good amount of software without having to scourge the net). That would pull one to consider it. However, I think getting updates offline would be a challenge.

.deb files would've been cool, but the term 'dependency hell' is a very good one in describing the issues there. Its like picking beans spilled in a garden. Tried to install gimp and vlc from [packages.ubuntu.com]("http://packages.ubuntu.com") and downloading every dependent package listed there. Still managed to 'miss' some. So I'm back to square one.

Getting the OS is fairly easy. You either order through Shipit or gear up for a once-in-a-while hefty download from the Ubuntu website. The problem is finding applications to work with. They're not so easy to find.

---

### Post by cascade9 on 2011-01-31
> **mastablasta said:**
> heh, no african countries in the list (have to admit i did a quick look). htough 5 DVDs for 10$ +shipping doesn't seem so much...

You are right, no african countrie on that list. Pity. But a lot of them ship internationally, and with discs being very light, it should be cheap to ship them. 

> **EthioJOB said:**
> That's interesting. Didn't hear of it. Its a good thing, though the Shipit service also works good. The CD is limited unless you're using it for basic functions (that's what I'm using). The 5 DVDs however seem to be a fair price (for a good amount of software without having to scourge the net). That would pull one to consider it. However, I think getting updates offline would be a challenge.

That was for debian, not ubuntu. As far as I am aware, ubuntu has never had the option to d/l all the repos like debain does. 
Getting the updates offline with debian is pretty easy as well, they have 'update' DVDs- 

[http://cdimage.debian.org/debian-cd/5.0.8/amd64/iso-dvd/](http://cdimage.debian.org/debian-cd/5.0.8/amd64/iso-dvd/)

Of course, if you re totally offilne you would need to order a DVD with the updates, but at least its an option. 

> **EthioJOB said:**
> .deb files would've been cool, but the term 'dependency hell' is a very good one in describing the issues there. Its like picking beans spilled in a garden. Tried to install gimp and vlc from [packages.ubuntu.com]("http://packages.ubuntu.com") and downloading every dependent package listed there. Still managed to 'miss' some. So I'm back to square one. 

Thats exactly the problem, and thats why you need more of the repos than you get with a ubuntu DVD (which IIRC isnt much more than the standard CD + the alternate CD + all langauge packs)

---

### Post by EthioJOB on 2011-01-31
> **cascade9 said:**
> You are right, no african countrie on that list. Pity. But a lot of them ship internationally, and with discs being very light, it should be cheap to ship them. 



That was for debian, not ubuntu. As far as I am aware, ubuntu has never had the option to d/l all the repos like debain does. 


Oops! 

I've been thinking if being able to update synaptic offline and using generated download scripts is a viable option. I tried using this method but apparently I think I need to update the repo. What do you guys think?

---

### Post by mastablasta on 2011-01-31
on the other hand if system works are the updates realyl so necessary? i mean security updates are mostly focused to online security or am i wrong here? viruses (transfered by floppy or usb) are not really made for Ubuntu.

---

### Post by Blutkoete on 2011-02-02
Wouldn't it be technically possible to create a Internet page which allows you to pick e.g. Ubuntu, TexLive-full and Gimp and it is all automatically zipped, burned to a DVD and then sent to you via a normal postal service? Or something like "KeryxOnline" - you put your package lists on an USB stick, go to the Internet café, upload the list, choose "update all and install this and that" and the next day you get a download link to a zipped file that contains everything you need which you download again in the Internet café, put it on your stick and install it at home.

That might even be faster in some regions of the world (including the English countryside, German mountains or the here-live-dragons parts of Texas) where you have a constant but slow internet connection, as this article says ([http://news.bbc.co.uk/2/hi/8248056.stm](http://news.bbc.co.uk/2/hi/8248056.stm)).

---

### Post by Irihapeti on 2011-02-02
Before I lived at my current address, I had a consistent-but-slow connection, a.k.a. dialup.

After I'd clicked on "reload" in Synaptic, I'd generate a package download script (another Synaptic option). Then I'd run the thing overnight and "add downloaded packages" (which all have to be in the same directory) the next day.

The download script is only a series of lines: "wget -c packagename". It would be easy enough just to strip out the "wget -c" at the beginning of each line, and you have a list of URLs you can download anywhere you like.

If you have no connection at all, then you can't update the repository information, and that's a different problem altogether.

---

### Post by mastablasta on 2011-02-03
in some places even dial up is expencive or there is as you said no connection at all.
 
@Blutkoete - Ubuntu system made to order. i like it.

---

### Post by EthioJOB on 2011-02-03
> **Blutkoete said:**
> Wouldn't it be technically possible to create a Internet page which allows you to pick e.g. Ubuntu, TexLive-full and Gimp and it is all automatically zipped, burned to a DVD and then sent to you via a normal postal service? Or something like "KeryxOnline" - you put your package lists on an USB stick, go to the Internet café, upload the list, choose "update all and install this and that" and the next day you get a download link to a zipped file that contains everything you need which you download again in the Internet café, put it on your stick and install it at home.

That might even be faster in some regions of the world (including the English countryside, German mountains or the here-live-dragons parts of Texas) where you have a constant but slow internet connection, as this article says ([http://news.bbc.co.uk/2/hi/8248056.stm](http://news.bbc.co.uk/2/hi/8248056.stm)).

That' exactly what I'm talking about. Forget the postal service; I'm happy if I can find an online service that would automatically zip all your required files and present them to you in a link. 

I think if Canonical were to create something like this it would be one major advantage for it.

---

### Post by Elfy on 2011-02-03
> **EthioJOB said:**
> That' exactly what I'm talking about. Forget the postal service; I'm happy if I can find an online service that would automatically zip all your required files and present them to you in a link. 

I think if Canonical were to create something like this it would be one major advantage for it.

Then I suggest you post in brainstorm - more chance of getting a movement on that there than here. [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Though I will say that I've been seeing the same sentiment for 3 years. 

The only people who are likely to see this thread are other users - rarely will you see a developer.

As it stands this is just going in circles now - so thanks for your inputs :)

Closed

---

