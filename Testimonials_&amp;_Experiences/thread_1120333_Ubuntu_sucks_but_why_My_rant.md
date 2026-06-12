---
title: "Ubuntu sucks but why? /My rant/"
date: 2009-04-08
forum: Testimonials &amp; Experiences
---

### Post by KOTAPAKA on 2009-04-08
OK first of all I am  going to tell my view on Ubuntu linux which is subjective and is dependent on my views, abilities and requirements. I, personally hate when somebody comes and says something bad about the features of a distro and says that the distro is no good. As we know there are many distros and each and everyone should be different and should suit a particular group which will find it features useful and user save time to do them themselves.

This is a little bit like a review.

First [COLOR="Red"]for me[/COLOR] Ubuntu is loaded with too many programs or whatever it is loaded with. On my debian linux I have an old distribution with many many and again many settings and packages installed and I have just about 1000 packages. Ubuntu comes with that many out of the box :confused:  And the worst is that you cannot select what to install and what not during the installation process. Like for instance I might want to do a base install and build up. All major distributions offer this - for some (Arch) it is their philosophy. Anyway I think at least a selector for the groups of packages would have been nice (such as tasksel).

Then we boot into the actual thing itself. It eats too much RAM which is not a problem nowadays but you have no control - you've already filled your system with things you don't need and now go and try to uninstall them, good luck.

I run Debian unstable. I've never had a package let me down so far or if it does it is rare and I don't remember it because IT GETS FIXED THE NEXT DAY at the very least. Yes they are very fast fixing bugs. Anyway I've had a terrible compiz problem which just won't go away for a very long time now. Now you tell me what should I think of a system that is less stable than a system named unstable? And you know Debian unstable gets fixed fast. Ubuntu barely gets updates.

Conclusion of the above paragraph - Canonical is making its money by copying Debian's repositories and basically does almost no work on the packages like debugging. Some good users do that and some Debian developers working for Ubuntu as well. Well yes canonical did put a distribution together but that's it. It;s like bearing a baby and leaving it.

Another thing is that Ubuntu is making things differently from other distributions. Generally, as unwritten laws, things such as the GRUB menu should have a standard layout amongst distros. Install Ubuntu then install some other distro and then GRUB and you will see that you need to edit the menu.lst. Well OK but I get confused - on one side Ubuntu tries to make it as simple as possible for new users (that's why I guess you get so much software installed and installation is optionless so that it will not be confusing for new users, which by the way makes the distro unsuitable for advanced users) but on the other hand if a new user tries another distro you deprive him of his Ubuntu box. And really shouldn't Ubuntu try to make a distro that people who try and become advanced users and who also strive for maximum performance with Ubuntu won't just use ir while they are newbies and then move on. That's what happened to me and to a lot of people I know. At the beginning it is very good and then you try another distro and you return to Ubuntu and you see the big difference and then don't even want to think Ubuntu.

Performance is fine but bugs are a lot. No development as far as I can see. I get nothing updated and I check every day and I've enabled all of the repositories.

Wireless has to be manually made to connect automatically to a specified network (User friendly? No, definitely no compared with the other stuff). The user friendliness of Ubuntu is messed - things that other distros make manually are automated in Ubuntu and here you come across something that is a standard across Linux (automatic connection) and it has to be manually done in Ubuntu.



Here we come to the root user. It's one of the characteristics of Linux. Root user. It's a must. You have it in Ubuntu but they don't give you the password. You can look it up using sudo in /etc but you have to decrypt it. Great that is efficient.

A little about sudo. It is just stupid. Or at least provide an option for users to have a super user during install. Here is why sudo is stupid: Tell me what is the difference between these 2 equations:

x = 2 - 3 - 4 - 8 - 22 - 21 + 23 + 5 - 6
x = 2 + (-3) + (-4) +(-8) + (-22) + (-21) + (+23) + (+5) + (-6)

the difference is the work done in writing. To do several commands with super user privileges you can do:

```
su
passwd:
aptitude update
aptitude safe-upgrade
.
.
.
```

Here is with sudo:

```
sudo aptitude update 
passwd:
sudo aptitude safe-upgrade
sudo .
sudo .
sudo .

```

It gets frustrating when you have a large number of commands. Maybe there is way to skip repeating but a linux user knows su and su must be there and it is but the root is missing.


To wrap up I will say that I was a big ubuntu user then moved to Debian and just the difference is humongous (in quality Deb>>Ubu).

Again Ubuntu is much less stable that Debian unstable. it might be a good choice for a newbie but I think such a big linux distro should make it suitable for a wider range.


I know there are a lot of advanced users using Ubuntu and I want to give you as an example what the Ubuntu system has done to you (at least I think). Some time ago there was the HDD spindown load cycle problem. A lot of you wrote scripts and stuff and did make it go away. I didn't know how to write scripts but I had a look at hdparm and looked at the config then at 90-hdparm in the acpi etc. I just changed the already writen script and it went away like so. I didn't used any of your scripts and you guys had more and still do have more knowledge about programming/scripting than me. 

Again I consider this to be my point of view which is subjective and according to my requirements. It doesn't mean anything when talking about another person unless you have similar aims and want a distro not just fo newbiew.

---

### Post by Stupendoussteve on 2009-04-08
Well written, although there are a few things that are incorrect or easily rectified.

The alternate install CD includes tasksel. I do agree that the graphical installer should have an advanced mode as well, where you can choose packages you would like. Still, it is not that hard to open up Synaptic and trim it down. If you feel you are an advanced user or limited by the graphical installer, you should be using the alternate cd.

Ubuntu gets updates quite often, from what I have seen. Have you posted a bug report for your issues? Is the bug sitting there and not being looked at? I find this hard to believe.

If you're having problems with Universe packages, remember that they are not maintained by Canonical. The [Components page]("http://www.ubuntu.com/community/ubuntustory/components") even says quite blatently "no guarantee of security fixes and support." I have not seen many problems with Canonical supported software, or universe for that matter.

Most every distribution requires you to rewrite menu.lst if you are multibooting, it is an advanced process that is not easily automated. Ubuntu does not use a "nonstandard" menu.lst, in fact the part of the file that is actually used (not commented out with #) is relatively small. You say installing another distro deprives the user from their Ubuntu box? It sounds as if you have installed grub through that distro and it did not include Ubuntu in *its* menu.lst, which is no fault of Ubuntu.

I get updates all the time, the fact that on a fresh Ubuntu install I see so many updates is proof that there is ongoing development. If you see bugs you should be reporting them, or tracking the progress of the existing reports.

My wireless connects automatically and has done so since I first entered my WPA key at the first login, and does so on previous releases as well.

The root account is disabled by default. You can access it without decrypting the non-existent hash from /etc/shadow, just by running sudo su (becoming root in the process) and then passwd to set a root password. Then su works as normal.

If running multiple commands with sudo bugs you, why aren't you running:

sudo su
aptitude update 
aptitude safe-upgrade

I used to be quite anti-Ubuntu. I saw it as a distribution for newbies, until I put it on my netbook and actually used it for a while. It is certainly easy on newbies, but in no way limits those who are more familiar or advanced users.

---

### Post by Black_Wolf_92 on 2009-04-08
I have to agree on the package installation there. The ubuntu installer does install a lot of packages I didn't need, however, as the above poster said, you can trim it down manually, but it seems like a bit of backwards work, on what SHOULD be an option for installation. After a bit of work though, (took about an hour for me) I had ubuntu running ONLY the applications I needed.

Your argument is well written however, and I don't think you are wrongly placed in any way, all are valid complaints. There is no reason not to switch to another distro, more suitable to your requirements, this is the main strength of open source =)

---

### Post by wolfen69 on 2009-04-08
i didn't bother reading the whole thing, so i can't really comment too much, but as i always say, use what works for *you* and be happy.  :)

---

### Post by Black_Wolf_92 on 2009-04-08
> **wolfen69 said:**
> i didn't bother reading the whole thing, so i can't really comment too much, but as i always say, use what works for *you* and be happy.  :)

lol excellent summary of nearly every distro argument.

---

### Post by 3rdalbum on 2009-04-08
Some people would say that Debian comes with too few packages by default.

Before Ubuntu came along, all the major desktop distributions would preinstall two web browsers, three text editors, two IRC clients, up to four media players and a handful of odd games. That made much less sense than Ubuntu's "ship one program for each task".

---

### Post by Stupendoussteve on 2009-04-08
> **3rdalbum said:**
> Some people would say that Debian comes with too few packages by default.

Before Ubuntu came along, all the major desktop distributions would preinstall two web browsers, three text editors, two IRC clients, up to four media players and a handful of odd games. That made much less sense than Ubuntu's "ship one program for each task".

And it was certainly annoying! One of the main reasons I moved into Debian and then Gentoo in the first place.

---

### Post by BrendanMark on 2009-04-08
Horses for courses. I, too, found sudo annoying until I found the way around it in the man-pages and the *Practical Guide to Ubuntu Linux*, but other distros (openSUSE for instance) allow root access fairly easily.

But it seems about the right size to me, and isn't much bother to trim IMHO. I use Ubuntu as my stable, GUI Linux and openSUSE as my test Linux distro, with a copy of XP for Exploder and Word. Suits me fine.

---

### Post by arashiko28 on 2009-04-09
I guess the idea of not giving the root access at once it's - to me - because since Ubuntu is like the door for new users in Linux who are way too noob and like to explore it all at once. I was one of those, I'm the kind that learns by pressing the button and seeing what it does, and thankfully among all the stupidity I did on the first few weeks while learning, none of them took my system stability away because none of the changes were made on the main files. So I'm pro sudo :p
Now, as the other fellows said, you can always install with the alternate CD or even better, get the Kernel and compile your own OS, it should be exiting to do so. I once planned to do it so that it would fulfill my needs as medicine student. But I'm not that advanced nor think ever will be to that level.
Good luck;)

---

### Post by exploder on 2009-04-09
I can see the point being made about updates. There is still not a decent, working version of Brasero in any of the repos for Hardy. You either have to compile Brasero yourself of go to GetDeb to have Brasero working right in Hardy.

The number of default packages seems fine to me, a lot of things are broken down to sets of small packages,Gftp comes to mind. There are 4 packages needed to install Gftp in Ubuntu, in PCLinuxOS it is a single package install, so this type of thing might account for the larger number of packages.

Using sudo is fine in almost any instance, the root account is not that difficult to enable if it is absolutely needed. The idea with sudo is to discourage people from using the root account like a user account. 

My only real rant revolves around the regressions and bugs left unfixed. Come on. how many releases does it take to have system sounds working? When release notes mention popular graphics cards not working properly where is the logic in running newer versions of xserverorg? Problems need to be addressed before moving on to the next release otherwise the system becomes a house of cards.

Edit: I would not go so far as to say Ubuntu sucks. There are areas where improvement is needed.

---

### Post by stchman on 2009-04-09
The OP I guess is unaware of the root terminal.  You can bring up a terminal an type:

```
sudo -s
```

After entering password you no longer have to type sudo.  Lack of knowledge.

To me Ubuntu is written for the masses.  It has a good mix of preinstalled applications for the average user.  You can install Ubuntu and be productive right away.

If the OP prefers Debian then by all means use it.

---

### Post by Tamlynmac on 2009-04-09
> Black_Wolf_92
lol excellent summary of nearly every distro argument. 	

In my opinion it's the perfect answer. If all one can do is rant and complain, then it just makes sense to find an alternative solution. Complaining never solves problems and unless one gets involved in the solution, complaining is only a venting process.

If one really wants solutions, then I would suggest they become active in the community in an effort to help find solutions for all. Or they simply remain another voice in the darkness. A voice that logically should seek an alternative option which supports the level of comfort they have become accustom to.

IMHO the last thing Ubuntu needs is individuals who only wish to complain and not get involved. The opportunities for involvement are many and one doesn't need to be a dev. to participate. I've never understood the logic of complaining about development here instead of directing it to the devs.? The devs. don't live here and true feedback (positive or negative) should be presented to those that could potentially have a direct impact on the issues. Ranting on the forum regarding development is not a solution, only a place that provides a platform to express one's frustrations and seek others who share their frustration.

Ranting is simple. Finding solutions - not so much. Perhaps, those that feel the need to rant regarding development - might consider becoming part of the solution - instead of remaining part of the problem. Focusing their energies on being involved in solutions, rather then complaining about those that are.

This post is not targeted at anyone in particular, it only represents my $0.02.

---

### Post by yosumi on 2009-04-10
Hey KOTABAKA. I agree with you. Ubuntu has too many packages by default. 

But for people who know very little about computer software like me, the extra packages installed would be idiot proof. I've no idea what packages are needed for printer, wireless, audio, video, different languages, etc. 

However, we SHOULD have to option of not installing some default applications like GIMP, bluetooth, games, passwords, tomboy notes, magnifier, and softphone which some of us will never use.

I'd love to use the alternate install method IF it accepts wireless connection by default. 

I've always been using Ubuntu but never tried Xubuntu. Maybe it'll trim down the bloat by a bit.

---

### Post by cariboo on 2009-04-10
@yosumi

If you are looking for a trimmed down distribution Xubuntu is not for you. It basically is just another desktop with the same underpinnings. Have a look at [Distrowatch]("http:///distrowatch.com/"), it may help you find a lighter distro.

Jim

---

### Post by cardinals_fan on 2009-04-10
I also despise sudo.

---

### Post by yosumi on 2009-04-10
> **cariboo907 said:**
> @yosumi

If you are looking for a trimmed down distribution Xubuntu is not for you. It basically is just another desktop with the same underpinnings. Have a look at [Distrowatch]("http:///distrowatch.com/"), it may help you find a lighter distro.

Jim

o I'm wrong but according to distrowatch, Ubuntu is number one so I'm still going for Xubuntu. ;) And Xubuntu has ext4 which is something new to me.

---

### Post by wolfen69 on 2009-04-10
> **cardinals_fan said:**
> I also despise sudo.

thank you for sharing those words of wisdom. :rolleyes:

---

### Post by solwic on 2009-04-10
> **wolfen69 said:**
> thank you for sharing those words of wisdom. :rolleyes:

+1.  :)

---

### Post by cardinals_fan on 2009-04-11
> **wolfen69 said:**
> thank you for sharing those words of wisdom. :rolleyes:
When it comes to personal experiences and opinions, there is no universal wisdom.  Since this is really the OPs thread about his/her experience, I didn't want to derail it, but some of the pros/cons of the default timeout in Ubuntu have been discussed [here]("http://ubuntuforums.org/showthread.php?t=925998").  With a timeout of 0, I don't have any real complaints about sudo.  It just doesn't seem necessary.

---

### Post by revelationman on 2009-04-12
You make some valid points I know the hard drive issue cost me  two drives in the last year on my laptop. I had to put Microsoft back on it was getting too expensive, I am not sure if the problem has been corrected. I currently run Ubuntu as my sole system on the desktop and it seems fine. 
I do not see the arguement that a distro has to be difficult to be good I believe in simplicity, and  Ubuntu has that. As for the sudo well it is just security and really a new user does not need to go into the terminal right away. I always recommend not going into the terminal right away until you learn the basics of it.

---

### Post by memories on 2009-04-13
You can use sudo -i instead of su. I have aliases for everything I use often. Even "su" is too much work. 

To install a package I do "aptinstall <package>" which is aliased to 
sudo apt-get install <package>

etc.


The fact that it comes with a lot of packages isn't a problem and it's not the reason too much RAM is being used. RAM is not used if the apps are only on disk. Yes it might have a lot of stuff open, but I like the functionality. Instead of stripping the OS and having it run fast on 1 gig of RAM, I enabled everything and went out and bought 8 gigs of RAM. I'm MUCH more productive when I have notifications, compiz and other things enabled. I used to use Flux and Slackware because all the other distros were too bloated - but I was wasting my time. 

I don't really care about too much apps.. terabyte HDs are cheap. I have 100-200 gigs of old videos/music I don't need laying around that are taking up much more space than random linux packages. Those are a problem.
But being that I have space to use, I don't bother deleting them. 

I hated Ubuntu for too long, because I also thought it was for newbs. But I'm _much_ more productive on it + gnome.

---

### Post by stchman on 2009-04-13
> **cardinals_fan said:**
> I also despise sudo.

You despise the thing that makes Ubuntu very secure?

---

