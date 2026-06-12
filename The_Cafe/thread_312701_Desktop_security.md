---
title: "Desktop security"
date: 2006-12-04
forum: The Cafe
---

### Post by Daveski on 2006-12-04
Following on loosely from issues raised by zetetic, I am interested in debate about modern 'desktop' security issues.

I assume that we would all be happy to see Linux in general (and Ubuntu specifically) become widely adopted. I think that the best way is going to be catching the next generation of computer users by getting open software and OS's in schools etc. However, many newcomers are going to have some experience of Windows, and as such are going to bring some of their previous experience, knowledge and concerns over. Any modern Windows user will (should) have had some security precautions drummed into them - "you must run a firewall and a virus scanner if you connect to the internet" etc.
When considering switching to using Ubuntu they are told that this simply isn't a problem with Linux and so can disregard most security issues they have become familiar with. I think this can cause many to feel a little insecure with an OS they are not experienced in fixing and so keep that Windows partition handy at all times in case their new Ubuntu system screws up.

We should talk about ways to reassure new users about security especially as in a desktop environment it is the user themselves who are the system administrators - and although might understand some security issues, most are not experts.

---

### Post by ciscosurfer on 2006-12-04
I think it's about educating new converts and empowering them to make informed decisions.

It's about providing new users with documents and places on the web that describe in detail the differences between operating systems: the advantages, the disadvantages, the pluses, the minues.

People by nature are reticent to make changes in their lives.  And so in terms of switching to a new operating system, making sure they understand the differences is crucial and should put them on the right track.

--Great beginning Daveski, I applaud your effort in trying to frame up a subject and request others to join in and express their thoughts on the issue :-).

---

### Post by aysiu on 2006-12-04
[quote=Daveski]We should talk about ways to reassure new users about security especially as in a desktop environment it is the user themselves who are the system administrators - and although might understand some security issues, most are not experts.[/quote] That's why I wrote this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by ciscosurfer on 2006-12-04
> **aysiu said:**
> That's why I wrote this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)I very much like that link and refer to it sometimes for reassurance (believe it or not!) :KS

---

### Post by max.diems on 2006-12-04
aysiu, can we just have a list of what you've already stated so people don't start threads about it and have you reply "That's in my tutorial/guide/essay/whatever (link)"?

---

### Post by aysiu on 2006-12-04
> **max.diems said:**
> aysiu, can we just have a list of what you've already stated so people don't start threads about it and have you reply "That's in my tutorial/guide/essay/whatever (link)"?
I'm not sure I know what you're asking.

Anything on [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) is something I've created (sometimes with the gracious help of other forum members).

The sidebar has a list of the tutorials/explanations available.

---

### Post by ice60 on 2006-12-04
i just want to point out zetetic doesn't know what he's talking about. he is confusing an application firewall such as SSM, Process Guard, Prevx etc with a firewall :rolleyes: although i think that gives him too much credit because i think he also mentions security suites. why would a linux firewall want to be a security suite :confused: 

you can get the protection he's talking about though with a firewall - netfilter/iptables, IDS - tripwire/aide, application control - apparmor and rootkit hunter. there are these too -
[http://www.bastille-linux.org/](http://www.bastille-linux.org/)
[http://www.grsecurity.net/](http://www.grsecurity.net/)
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

there's something called libsafe in the repos which you can install too

here's some links -
[http://debianhelp.co.uk/security.htm](http://debianhelp.co.uk/security.htm)
[http://www.linux-sec.net/Harden/howto.gwif.html](http://www.linux-sec.net/Harden/howto.gwif.html)
[http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents)

@zetetic i just read what you said about JAP you obviously don't know java is cross-platform :rolleyes: maybe you've heard of TOR that runs on linux too lol it even uses three mixes :o

---

### Post by ciscosurfer on 2006-12-04
> **ice60 said:**
> i just want to point out zetetic doesn't know what he's talking about. he is confusing an application firewall such as SSM, Process Guard, Prevx etc with a firewall :rolleyes: although i think that gives him too much credit because i think he also mentions security suites. why would a linux firewall want to be a security suite :confused: 

you can get the protection he's talking about though with a firewall - netfilter/iptables, IDS - tripwire/aide, application control - apparmor and rootkit hunter. there are these too -
[http://www.bastille-linux.org/](http://www.bastille-linux.org/)
[http://www.grsecurity.net/](http://www.grsecurity.net/)
[http://www.nsa.gov/selinux/](http://www.nsa.gov/selinux/)

there's something called libsafe in the repos which you can install too

here's some links -
[http://debianhelp.co.uk/security.htm](http://debianhelp.co.uk/security.htm)
[http://www.linux-sec.net/Harden/howto.gwif.html](http://www.linux-sec.net/Harden/howto.gwif.html)
[http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents](http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html#contents)

@zetetic i just read what you said about JAP you obviously don't know java is cross-platform :rolleyes: maybe you've heard of TOR that runs on linux too lol it even uses three mixes :oI agree with you, but...easy, tiger...

---

### Post by Polygon on 2006-12-04
general rule of thumb: use your brain. By default ubuntu's ports are blocked and unless you are running a server you really have no reason to have a firewall.

as long as you dont run scripts or .debs from untrusted sources, you should be fine no matter what you do, this also applies to windows, although its a little bit harder with windows cause there are some programs that are trusted but still are complete crap (example: internet explorer and outlook express... hell outlook express caused a hacker to gain the source code to a major video game, half life 2.)

---

### Post by ice60 on 2006-12-04
> **ciscosurfer said:**
> I agree with you, but...easy, tiger...
hmm, i was just abit upset that thread was locked when i went back to it. i don't care if someone doesn't like linux, but talking nonsense is abit irritating. although maybe i have abit of a drunken haze going on and i've not read very carefully :-k either way i'm going to bed, i might have editted out what i said, but you went and quoted it :P

[quote=zetetic]all Linux firewalls are snake oil[/quote] =; maybe you should go and tell d-link, netgear etc about that. should routers run NIS instead :confused: :rolleyes:

ok, i'm really going to bed now.

---

### Post by Daveski on 2006-12-05
> **Polygon said:**
> general rule of thumb: use your brain. By default ubuntu's ports are blocked and unless you are running a server you really have no reason to have a firewall.


Absolutely, and there are some excellent sources of information pointed at already in this thread. However my worry is that the general feeling seems to be that Ubuntu is secure - new users should just accept that, or go and learn some more about why.

The Linux community is all about finding out information for yourself, and I love this, but I am wondering if there is another approach which might fit with the philosophy that Ubuntu is for everyone. Let's not forget that many users might be interested in finding information, but may not have the technical knowledge to find what they need, or to really understand what they find.

---

### Post by aysiu on 2006-12-05
[quote=Daveski]I am wondering if there is another approach[/quote] Well, we all wonder if there is another. Unfortunately, not a lot can be done until there's a concrete suggestion made.

---

### Post by ciscosurfer on 2006-12-05
> **Daveski said:**
> Absolutely, and there are some excellent sources of information pointed at already in this thread. However my worry is that the general feeling seems to be that Ubuntu is secure - new users should just accept that, or go and learn some more about why.

The Linux community is all about finding out information for yourself, and I love this, but I am wondering if there is another approach which might fit with the philosophy that Ubuntu is for everyone. Let's not forget that many users might be interested in finding information, but may not have the technical knowledge to find what they need, or to really understand what they find.I guess I see it a little differently.  While the Linux community, per se, might be about finding out information for yourself, the Ubuntu community as I see it, is about sharing and collaborating information together.  A user need only pop onto the Forums to begin a discussion, join in others, propose solutions, and find answers to problems and concerns.

Despite the Yelp Help that we have, perhaps a link on a users Desktop after a fresh install, leading them in the proper direction *in terms of help *is the way to go.  I already see the Forums as place of interest for new and experienced users.  When I first joined the Forums, I did so because I needed to find out some very detailed information about some rather (currently mundane) tasks.  I searched out, and I found.  Short of placing links in big, bold letters on every Ubuntu site that states where I should go for help, I'm not really sure what else we can do as a community.

---

### Post by Daveski on 2006-12-05
My experiences are very similar. I hunted for a specific problem here on the forum which has broken the ice with me and enabled me to discover an almost overwhelming knowledgebase.

I do not think that Ubuntu should be more like Windows, and I get seriously annoyed at the constant nannying of Windows and the popcorn like effect of the message bubbles on a fresh install of XP. I do not like the patronising startup 'tutorials' and wizards and other helpful avatars interrupting me, however I do see that this is the acceptable norm for many users coming from the world of Windows, and I do understand the need to guide new users. Perhaps a few well placed (i.e. easy for Windows users to stumble upon) hints or at least reassurances may help. For example (and this is not particularly well thought-out by me) a security section on the main menu or even a desktop icon or system tray equivalent which is easily recognisable as a security centre, which when investigated reassures the user that a firewall is not necessary - perhaps by showing a table of daemons that are listening to network ports. A virus section might show that constant virus scanning is not necessary but might explain that if you are sharing files with Windows users you may want to install a scanner to enable you to check for Windows viruses before emailing that attachment - perhaps a link to install Clam or at least mention some well known firewall front-ends and virus scanners that would be easy for new users to investigate and deal with. I have found that knowing the name of a well known application helps enormously with hunting for information or even looking through the repositories.

---

### Post by ciscosurfer on 2006-12-05
> **Daveski said:**
> My experiences are very similar. I hunted for a specific problem here on the forum which has broken the ice with me and enabled me to discover an almost overwhelming knowledgebase.

I do not think that Ubuntu should be more like Windows, and I get seriously annoyed at the constant nannying of Windows and the popcorn like effect of the message bubbles on a fresh install of XP. I do not like the patronising startup 'tutorials' and wizards and other helpful avatars interrupting me, however I do see that this is the acceptable norm for many users coming from the world of Windows, and I do understand the need to guide new users. Perhaps a few well placed (i.e. easy for Windows users to stumble upon) hints or at least reassurances may help. For example (and this is not particularly well thought-out by me) a security section on the main menu or even a desktop icon or system tray equivalent which is easily recognisable as a security centre, which when investigated reassures the user that a firewall is not necessary - perhaps by showing a table of daemons that are listening to network ports. A virus section might show that constant virus scanning is not necessary but might explain that if you are sharing files with Windows users you may want to install a scanner to enable you to check for Windows viruses before emailing that attachment - perhaps a link to install Clam or at least mention some well known firewall front-ends and virus scanners that would be easy for new users to investigate and deal with. I have found that knowing the name of a well known application helps enormously with hunting for information or even looking through the repositories.Great ideas!  I believe ***if*** the motivation of Ubuntu devs is at least partly to ease the transition for new users, then yes, I completely agree with you.  Heck, I'd like to see those options in a menu or the like for myself, and I'm an experienced user. :cool:

---

### Post by DoctorMO on 2006-12-05
If we could integrate the help system a bit more in the gui side of linux so that kde, gnome, xfc all used the same system for help. I mean for the command line you have man or info and it's consistant. your lost when a program doesn't have a man page.

now go to firefox help or go to openoffice help, now goto nautilus help. see what I mean.

It would also be helpful to have the help files updated independently of the application, because sometimes there is going to be a user who wants to help out a project by updating the help files.

---

### Post by Daveski on 2006-12-06
I'm pretty impressed with the supplied documentation and help for the default applications, although I do see your point about them not being consistent. Sadly I think this is one of the prices to be paid for components coming from lots of different places. I guess you could argue that Windows users using IE get more integrated and consistent help than Windows users using Firefox etc.

I think that the Documentation Team, UbuntuGuide.org and other similar projects are the only way we are going to get good quality and unified documentation - although these are not help files and not that well integrated with the GUI.

In my experience most users do not spend much time with the help systems of applications or with the OS itself, and prefer instead to simply ask someone else how to do XYZ. If someone would spend time searching help files or documentation, then they are just as likely to 'Google' it than to navigate through help files - and are probably likely to get better information. This ties neatly back to what ciscosurfer has already said about Ubuntu being community based and sharing and collaborating information.

---

### Post by ciscosurfer on 2006-12-06
> **Daveski said:**
> [..]In my experience most users do not spend much time with the help systems of applications or with the OS itself, and prefer instead to simply ask someone else how to do XYZ. If someone would spend time searching help files or documentation, then they are just as likely to 'Google' it than to navigate through help files - and are probably likely to get better information. This ties neatly back to what ciscosurfer has already said about Ubuntu being community based and sharing and collaborating information.I know I use car analogies a lot, but it fits here perfectly as well: People really don't want to know the underpinnings of their car, how it works, what happens when the pistons fire, which wire connects to another one to make the windshield wipers work, what the rack and pinions are....they just want to be able to drive their car and they want it to work.  They do have some choices though: automatic vs manual, color, year/model/make.  So too does the end-user have these options in comparison: windows vs linux vs mac (unix), big tall case vs laptop vs cube, something old vs something new.

The bottom line though is that they want it to work.  So I agree with Daveski in this regard--they'd rather be told how to do it than read up on the special details of how to get it to work.  Of course, to some, showing is doing and people can learn this way as well.  I do.  But I also like the nitty-gritty. :D

---

### Post by Daveski on 2006-12-06
I guess there are 2 main camps of users of computers: those who use it as a tool and just want it to work; and those who like to learn about *how* computers work and like to fiddle. Of course there is a spectrum of users in-between.

Ubuntu seems to be so successful because it caters for both extremes to some degree. I wonder if we can build on this perhaps by offering 'training wheels' catering for specific users. Seasoned users can turn all this off, Windows users could have specific tips, as could Mac and total computer newbies. There is my previous example about Firewalls and Antivirus, but also Windows users are a bit stumped by the notion of drives being mounted and dismounted - *why doesn't by CD drive eject when I push the Eject button?* Whereas Mac users are more likely to understand you should software eject, or dismount the media first.

---

### Post by ciscosurfer on 2006-12-06
> **Daveski said:**
> I guess there are 2 main camps of users of computers: those who use it as a tool and just want it to work; and those who like to learn about *how* computers work and like to fiddle. Of course there is a spectrum of users in-between.

Ubuntu seems to be so successful because it caters for both extremes to some degree. I wonder if we can build on this perhaps by offering 'training wheels' catering for specific users. Seasoned users can turn all this off, Windows users could have specific tips, as could Mac and total computer newbies. There is my previous example about Firewalls and Antivirus, but also Windows users are a bit stumped by the notion of drives being mounted and dismounted - *why doesn't by CD drive eject when I push the Eject button?* Whereas Mac users are more likely to understand you should software eject, or dismount the media first.I can push the Eject button and my drive opens just fine in Ubuntu. :-k

---

### Post by aysiu on 2006-12-06
> **ciscosurfer said:**
> I can push the Eject button and my drive opens just fine in Ubuntu. :-k
I believe this was fixed as of Dapper. In Breezy and Hoary, you couldn't eject by pressing the **Eject** button.

---

### Post by Daveski on 2006-12-07
Sure. I am trying to give examples of where a user with experience of another OS might get tripped up (or even a total newbie). I guess looking through peoples first posts on this forum would give a good idea of some of the common ones.

I would be interested in anyone's opinion on having a built-in tips system - sort of tools tips, something really simple which would help guide a user during those first few hours using Ubuntu. I think this would especially be useful as many people's first impressions will be with the Live version from CD. I don't like the idea of masses of information for people to wade through after completeing the CD boot or a successfull install, but just a little bit of reassurance that is context sensitive rather than the age old 'Did you know?' at startup. Obviously this would have to be simple to turn off as I know it would wear thin after a very short time. Perhaps individual tips could turn off after being displayed twice or something.

---

### Post by Daveski on 2008-02-05
If anyone stumbles on this thread with conserns like those raised in the original post, I thought I'd link to some excellent security related articles written by Forum members. Feel free to post others.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and 

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by raymac46 on 2008-02-05
I've installed at least 10 Linux systems (mostly Ubuntu and Xubuntu) on older PCs and given them away to folks who don't have one.
When I deliver the system I tell them:
(1) It's pretty safe. There aren't many viruses around for Linux and no spyware since you get your programs from the same place you get the operating system.
(2) Nobody can hack you if you don't give away your administrator or user password.
So far that has been enough to reassure them, simplistic though it may be.

---

