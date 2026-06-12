---
title: "getdeb.net = safe?"
date: 2008-02-19
forum: The Cafe
---

### Post by conphara on 2008-02-19
Hey everyone.

I have a friend whom I have helped getting Ubuntu installed on his pc and laptop. He likes it so far. I have a quite a lot of conversations about how to maintain, update etc. One of his questions was about new software. I showed him the getdeb.net site with all the updated software for Ubuntu.

Since I told him that installing from the Ubuntu repositories is very safe (free of bad code; read virus, malware etc).
What about the getdeb.net packages related to the above, how safe is it?

I most say that since I first found out about the site, I haven't stopped checking it out at least a couple of times every week to look for new software, and installing like i'm posest.
Regarding "safe" sites, what about source/deb packages from gnomefiles, sourceforge and so on?

---

### Post by LaRoza on 2008-02-19
> **conphara said:**
> 
I most say that since I first found out about the site, I haven't stopped checking it out at least a couple of times every week to look for new software, and installing like i'm posest.
Regarding "safe" sites, what about source/deb packages from gnomefiles, sourceforge and so on?

Those sites are safe. Remember, it is open source, so malware has no place to hide unless you code it in Perl.

---

### Post by htor on 2008-02-19
It's spyware site. I recommend to use only the official repositories.

---

### Post by p_quarles on 2008-02-19
> **htor said:**
> It's spyware site. I recommend to use only the official repositories.
Please post evidence in support of that claim. Making accusations like that is libel.

---

### Post by Kernel Sanders on 2008-02-19
> **htor said:**
> It's spyware site. I recommend to use only the official repositories.

:rolleyes:

---

### Post by htor on 2008-02-19
Installing .debs from 3rd parties (not officially from Ubuntu) always runs a risk. When installing a .deb, you give the installer root privileges, it has full access to install and remove anything on your computer. It needs root access to install and satisfy dependences, but if used maliciously it could install key loggers, spyware, viruses or simply delete your system files.

PROOF:
If getdeb isn't spyware site so why it contains packages** that already exist** in the official repository ?

---

### Post by conphara on 2008-02-19
Would a virus scanner like say, Clam (installed from the repositories), pick up on a key logger (to get the root password) and if an app would open a certain port (since Ubuntu has all ports closed by default) in order to attack a pc from the "outside"?

---

### Post by p_quarles on 2008-02-19
> **htor said:**
> PROOF:
If getdeb isn't spyware site so why it contains packages** that already exist** in the official repository ?
Actually, proof would be something more like an instance in which a package obtained from Getdeb was found to relay personal information to the person doing the package. 

They only package open source software there. While it's technically possible for someone to sneak in a malicious package, there is absolutely no record of this having ever happened.

---

### Post by LaRoza on 2008-02-19
That site probably has more recent versions of the software. I am not on Gutsy now, so I can't check the versions.

---

### Post by SunnyRabbiera on 2008-02-19
right, and there packages on getdeb seem to be more current most of the time.
I never had an issue with getdeb.

---

### Post by p_quarles on 2008-02-19
> **LaRoza said:**
> That site probably has more recent versions of the software.
Usually, yes. 

> I am not on Gutsy now, so I can't check the versions.
[Yes you can](http://packages.ubuntu.com/gutsy/). ;)

---

### Post by LaRoza on 2008-02-19
> **p_quarles said:**
> Usually, yes. 


[Yes you can](http://packages.ubuntu.com/gutsy/). ;)

I was browsing that page actually, it isn't easy to find stuff though. Find "cheese" or "deluge", I couldn't.

After going through that page, I gave up.

---

### Post by loell on 2008-02-19
there are no incidents yet, so it is safe to say that it is safe :)

---

### Post by p_quarles on 2008-02-19
> **LaRoza said:**
> I was browsing that page actually, it isn't easy to find stuff though. Find "cheese" or "deluge", I couldn't.

After going through that page, I gave up.
Those are both in third-party repos, if I recall correctly. The search will show anything available in Canonical's own repositories, though.

---

### Post by helliewm on 2008-02-19
Get deb is[COLOR="Black"] NOT [/COLOR] a spyware site.

I have never ever had any issues with get deb and use it alot for update software. Its a site I really admire they must put alot of work into it and really complements the repositories.

Helen

---

### Post by eilu on 2008-02-19
+1 for getdeb

Q: why does getdeb have the "same" packages as the repos if it isn't spyware?
short answer: why does wallmart/costco have the same products name-brand stores have if it isn't stolen? :lol:
real answer:  getdeb has **newer** packages, usually before they're in the official repos. It's their rationale:
> The current Ubuntu official packages update policy (described here) is limited to critical bug fixes, meaning after each release there will be no regular bug fixes or improvement updates. This a good practice for stability purposes specially if you are planning to do an enterprise level support but it also means that until the next release you will not be able to get the latest and greatest software versions for your system.
Experienced users and developers will be able to compile and install from the source but unskilled users which would like to try the latest versions will be complaining about how hard it is to compile software packages, specially those which depend on several development libraries.
This policy is also a limitation for the emerging applications which will not be available on the official repositories and consequently not getting the proper recognition, something that they can get by being easily available to the end users.

---

### Post by Lster on 2008-02-19
McAfee SiteAdvisor says:

[http://www.siteadvisor.com/sites/getdeb.net](http://www.siteadvisor.com/sites/getdeb.net)

---

### Post by mr.propre on 2008-02-19
I guess there is always a risk when you download something from a 3rd party website. But I won't call getdeb a spyware site.

Just be careful ;-)

---

### Post by ung/xunil on 2008-02-19
That McAfee siteadvisor is just really saying that the site is safe, it doen't refer to the packages you download from it. I really would even care what the McAfee says just because it is possible that it only refers to Windows malware and known virus.

About using a third party repository, I think some people make confusion and blindly thrust all sites that has "opensource" writen somewhere in the site. 


Official repositories (main and restricted)

The package maintainers don't upload compiled stuff: they upload the code and the modifications to the original software code to build a deb package. The software is compiled and the package is built in the canonical/ubuntu servers by an automated script (ubuntu-cdimage - a modified debian-cd program used to build it all, from code, passing by compilation and packaging and ending with repositories and the ISO files that are the various Ubuntu CD's - server, alternate, desktop, kubuntu, etc). You can test this by using "apt-get source" and build packages.


Universe/Multiverse repository

Although the universe/multiverse repositories are not maintained by Ubuntu official team, it is maintained upstream by Debian community and by the MOTU. The code used to make those packages are on the server as well and is available to all (opensource).


Third party repositories

The uploader uploads compiled software and built packages by himself. You must trust the maintainer (Do you know him? Is he the developer of the software?) and you cannot verify what code was used to compile the packages.


What's the difference?

In the official repositories, the packages built and compiled has to be the result of the code that was uploaded. There is no way to add/hide 3 lines of code without it being visible to all of the world (it doesn't mean that the all world is looking at that code, but eventually somebody will).


Conclusion: A third party repository is not another "universe" repository.

I really prefer to compile the software that isn't available on the repositories myself.

---

### Post by forrestcupp on 2008-02-19
> **ung/xunil said:**
> 
Conclusion: A third party repository is not another "universe" repository.

I really prefer to compile the software that isn't available on the repositories myself.
That doesn't make an ounce of difference if you don't read and understand *every line* of code you are compiling.  And just reading the comments and accepting that they are truthful isn't good enough.  You have to sift through the thousands of lines of code and make sure it is really doing what they say it is.  If you don't do that, it doesn't really make a difference whether you compile or install a deb.  I know I'm not going to bother with that.

If you only use the official repos, you are letting your fears really limit you.  Cinelerra is the only viable offering for professional video editing, but it will never be in the official repos.  And I'm not going to go through all that code.

---

### Post by loell on 2008-02-19
> **ung/xunil said:**
> That McAfee siteadvisor is just really saying that the site is safe, it doen't refer to the packages you download from it. I really would even care what the McAfee says just because it is possible that it only refers to Windows malware and known virus.

About using a third party repository, I think some people make confusion and blindly thrust all sites that has "opensource" writen somewhere in the site. 


Official repositories (main and restricted)

The package maintainers don't upload compiled stuff: they upload the code and the modifications to the original software code to build a deb package. The software is compiled and the package is built in the canonical/ubuntu servers by an automated script (ubuntu-cdimage - a modified debian-cd program used to build it all, from code, passing by compilation and packaging and ending with repositories and the ISO files that are the various Ubuntu CD's - server, alternate, desktop, kubuntu, etc). You can test this by using "apt-get source" and build packages.


Universe/Multiverse repository

Although the universe/multiverse repositories are not maintained by Ubuntu official team, it is maintained upstream by Debian community and by the MOTU. The code used to make those packages are on the server as well and is available to all (opensource).


Third party repositories

The uploader uploads compiled software and built packages by himself. You must trust the maintainer (Do you know him? Is he the developer of the software?) and you cannot verify what code was used to compile the packages.


What's the difference?

In the official repositories, the packages built and compiled has to be the result of the code that was uploaded. There is no way to add/hide 3 lines of code without it being visible to all of the world (it doesn't mean that the all world is looking at that code, but eventually somebody will).


Conclusion: A third party repository is not another "universe" repository.

I really prefer to compile the software that isn't available on the repositories myself.




don't spread FUD, and don't be too paranoid.

nobody said to put the same level of trust for getdeb.net like the same given for the official repositories. 

of course getdeb.net is not another "universe" repository it never intends  and neither pretends to be one.

---

### Post by DrMega on 2008-02-19
> **htor said:**
> PROOF:
If getdeb isn't spyware site so why it contains packages** that already exist** in the official repository ?

The fact that the same .deb file is available from more than one place (ie the Gutsy repo plus somewhere else) doesn't prove anything other than that it is available.

I can buy Windows from my local PC World store, or I can buy it somewhere else. Does that mean that one copy is spyware and one isn't?

---

### Post by zerhacke on 2008-02-19
> **Lster said:**
> McAfee SiteAdvisor says:

[http://www.siteadvisor.com/sites/getdeb.net](http://www.siteadvisor.com/sites/getdeb.net)

This is misleading as McAfee is going to scan for Windows malware.  You could write a real Linux threat and pass it under McAfee's nose and it will never find a problem.

That said, yes, GetDeb is safe.

---

### Post by htor on 2008-02-19
When Mr. Mark  Shuttleworth will Say (after he hires some security experts) "I trust getdeb.net" I will believe to you.

---

### Post by LaRoza on 2008-02-19
> **htor said:**
> When Mr. Mark  Shuttleworth will Say (after he hires some security experts) "I trust getdeb.net" I will believe to you.

I trust getdeb.net.

[http://ubuntuforums.org/showthread.php?t=700714](http://ubuntuforums.org/showthread.php?t=700714)

---

### Post by loell on 2008-02-19
> **htor said:**
> When Mr. Mark  Shuttleworth will Say (after he hires some security experts) "I trust getdeb.net" I will believe to you.

sure thing,  but to say that getdeb.net is a spyware without backing it up with static proof, is plain old hearsay.  

until you can explain in technical terms why getdeb.net is a spyware then I  or rather We ,.. will believe you.

---

### Post by roaldz on 2008-02-19
> **htor said:**
> When Mr. Mark  Shuttleworth will Say (after he hires some security experts) "I trust getdeb.net" I will believe to you.

I think you are spreading lies. I won´t believe you if you say you don´t, unless Mike Shuttleworth´s security experts tell me you don´t.

I mean, c´mon..

---

### Post by tehet on 2008-02-19
> **p_quarles said:**
> Please post evidence in support of that claim. Making accusations like that is libel.
Rather prove the opposite. Such sites are 3rd party and as such untrusted by definition. It may be open sauce, but mallware *can* hide in binaries, which is what getdeb offers.

Whether or not the folks of getdeb et al can be trusted is one thing. Who says their packages won't break my next dist-upgrade?

If you're on your own using Automatix the same should apply for this kind of stuff.

---

### Post by qazwsx on 2008-02-19
I have had troubles once with getdeb I didn't had zenity installed and because of that it locked my package management. I fixed it later with apt and dpkg commands but it really wasn't easy.
It is allways risky  when you decide to go towards third party packages.
Still using getdeb :)

---

### Post by blithen on 2008-02-19
> **htor said:**
> It's spyware site. I recommend to use only the official repositories.

Bad troll is bad.

---

### Post by aimran on 2008-02-19
You guys dont put on your troll-retardant suits do you?

---

### Post by Tristam Green on 2008-02-19
Spent too much money on the troll-feed at the zoo :popcorn:

Bottom-line:  getdeb = safe (no question mark)

---

### Post by Luggy on 2008-02-19
I'm getting a 503 when checking out the 'get involved' section of getdeb.net so I can't check this out for myself, but are the .debs that are submitted screened at all?

I mean, it would be nothing to  include our friendly neighbrohood 'sudo rm -rf / ' in an install script. Granted if you did do something like that you would be caught really quickly and only a handfull of users would suffer, but still if the packages are not screened it could happen. 

Sorry if it sounds like FUD but there is always a risk whenever you run sudo and you don't know exactly what it is you are installing or doing. That's why every other member of this forum has a warning about 'sudo rm -rf' in the sig.

---

### Post by LaRoza on 2008-02-19
> **Luggy said:**
> I'm getting a 503 when checking out the 'get involved' section of getdeb.net so I can't check this out for myself, but are the .debs that are submitted screened at all?

I mean, it would be nothing to  include our friendly neighbrohood 'sudo rm -rf / ' in an install script. Granted if you did do something like that you would be caught really quickly and only a handfull of users would suffer, but still if the packages are not screened it could happen. 

Sorry if it sounds like FUD but there is always a risk whenever you run sudo and you don't know exactly what it is you are installing or doing. That's why every other member of this forum has a warning about 'sudo rm -rf' in the sig.

There is a packaging team that does it. It is not random uploads.

---

### Post by forrestcupp on 2008-02-19
> **LaRoza said:**
> I trust getdeb.net.

[http://ubuntuforums.org/showthread.php?t=700714](http://ubuntuforums.org/showthread.php?t=700714)

:lolflag:  Mark?  You have time to be a forum moderator?

---

### Post by LaRoza on 2008-02-19
> **forrestcupp said:**
> Mark?  You have time to be a forum moderator?

No, I paid someone to be me. 

The plea to Mark's opinion on the matter was too opurtune not to bring up that thread.

---

### Post by BobSongs on 2008-02-19
[FONT=Verdana]Wow. Interesting thread.

I use GetDeb's software without any harm to my system. But I've got to admit I find how some of us think to be rather surprising.

GetDeb's been around for a while. If something fishy was happening don't you think we would have heard wind of it by now? Some bozos on this forum suggest **sudo rm -rf **as a solution to a new user's woes. And now half the forum members warn us about it in their sigs. In the same vein GetDeb's "bad reputation" would have found its way on as many forum members' signatures by now.

I realize that the Internet is a dangerous place these days. There's a thriving industry out there that focuses on wrecking people's machines. That being said, I still think the general rule is innocent until **proven** guilty. Especially with the easy access to Google. I'm sure a search would result in a lot of hits about GetDeb and bad software if such were indeed the case.
[/FONT]

---

### Post by cprofitt on 2008-02-19
From my understanding getdeb is not limited to Ubuntu or Debian, but any Debian based distro... if that is the case that could explain the packages that are on the site being in some distros repositories (they might be newer versions too).

---

### Post by ung/xunil on 2008-02-19
> **loell said:**
> don't spread FUD, and don't be too paranoid.

It's not FUD. It's principles. The opposite of my opinion is ingenuity, not "responsible and confident".  And I sincerely don't like the blind level of thrust that some people put in third party repositories. And I don't like people starting to say that "yes, you can thrust it" without explaining the difference between a package compiled by an unknown member of some site in the internet and a official repository. If this continues to pass that way, next year noobs will be installing software thrusting it just because somebody just say them that "you can thrust it because I do". Lets not be throlls here and lets help people to use safely their opensource software.

You should only add 100% secure repositories or compile and install your own software. If you don't do it, when you type your sudo password to install a third party package, your accepting the risk, just as installing some .exe file you downloaded from the Inernet on your Windows. Paranoid? Ask the millions of windows users that have to remove malware and virus from their Windows. The last 25 years of computer history and the way that virus and others have made their way in Windows is an example of what to avoid for Ubuntu/Linux.

I'm not telling that getdeb is malware, please don't misunderstand me! If getdebs was something like 'backports' repositories, and/or someone could check the code from where  the packages were built, just like the regular repos and 'opensource' software (not compiled),  then I would thrust getdebs. 

I didn't say that getdebs is 'universe'. I just tried to make it clear it isn't.

Of course that I don't check every line of code of the opensource I install here. I verify sometimes the options used to build a package, rebuild some from source when needed, some times I download a newer version of the software from their website and use it. Like me, many more people do it too. Like I said on my previous post, eventually somebody will find untrusted code with the time (if that software is massively used, this should be quick). That's the thust you can get from opensource.

I think that having the code in front of you, you are much more safer than blindly installing some binary from somewhere. 

Once again, it's a matter of principles. I have the right to have my opinion and I'm just expressing it. You only have a safe Ubuntu box while you know what you are installing and from where you get it.

I thrust Ubuntu/Debian/Linux for some reason: all it's code is available to whoever wants/needs to verify, change it, etc and it is "controled" by reputed maintainers. I don't thrust getdeb that way.

To end this long post, I just want to say that if you didn't like Windows because of it's software quality and problems, blindly installing .deb packages that you find on the internet will not make Ubuntu/Linux better, only worst because you can't check what you installed. Even a antivirus or rootkit scan will not find anything on those .deb packages simply because a "rm -rf *" or a selfmade keylogger (this are examples) inserted in the binary would not be revealed on any security tool (apparmor or other tools would only find any problem if it was configured too check if the program can access the internet or write in some file/directory.)

---

### Post by forrestcupp on 2008-02-19
@ung/xunil  
I'm not trying to be a jerk; I just want to help you.  The word is 'trust'. 'Thrust' means something else.  I know there are a lot of users here that have English as a second language.

And there is nothing wrong with being cautious.  Some people are just more cautious than others.

---

### Post by ung/xunil on 2008-02-19
Thanks for correcting me. Yes, English is not my first language (it's my third). 

I blame it on the spell check: it can't tell the difference.:mrgreen:

---

### Post by icechen1 on 2008-02-19
> **htor said:**
> Installing .debs from 3rd parties (not officially from Ubuntu) always runs a risk. When installing a .deb, you give the installer root privileges, it has full access to install and remove anything on your computer. It needs root access to install and satisfy dependences, but if used maliciously it could install key loggers, spyware, viruses or simply delete your system files.

PROOF:
If getdeb isn't spyware site so why it contains packages** that already exist** in the official repository ?

Ubuntu forbids upgrading a package once it is in a release.getdeb is designed to get the latest package of that program without compiling.

---

### Post by SomeGuyDude on 2008-02-19
Getdeb is my saviour. And yes, it's safe.

---

### Post by forrestcupp on 2008-02-19
> **icechen1 said:**
> Ubuntu forbids upgrading a package once it is in a release.getdeb is designed to get the latest package of that program without compiling.

You can get a lot of the same things by enabling the gutsy-proposed and gutsy-backports updates.

---

### Post by heathenos on 2008-02-19
i check getdeb all the time.   yes, it is safe.:wink:

---

### Post by JordanII on 2008-02-19
> **LaRoza said:**
> I was browsing that page actually, it isn't easy to find stuff though. Find "cheese" or "deluge", I couldn't.

After going through that page, I gave up.

Ctrl+F is your friend, friend. ;)

---

### Post by LaRoza on 2008-02-19
> **JordanII said:**
> Ctrl+F is your friend, friend. ;)

It depends on the browser sometimes, but I did use the "Find in Page" feature of my browser (though a more convenient method) and those apps weren't on it.

---

### Post by bruce89 on 2008-02-19
> **icechen1 said:**
> Ubuntu forbids upgrading a package once it is in a release.getdeb is designed to get the latest package of that program without compiling.

Not quite. Ubuntu takes the Debian style view that new packages are unstable, and should not be used.

> **LaRoza said:**
> It depends on the browser sometimes, but I did use the "Find in Page" feature of my browser (though a more convenient method) and those apps weren't on it.

'/' was it?

---

### Post by gsmanners on 2008-02-20
I'm not too worried about the packages, but it does worry me a little that [http://wiki.getdeb.net/](http://wiki.getdeb.net/) gives you a 503.

Who exactly is the packaging team? I think if we could answer that definitively, it would put to rest any reasonable fear of that site.

---

### Post by Polygon on 2008-02-20
doesnt getdeb accept packages from its users, and then it checks them to make sure they are safe before putting them on the site?

---

### Post by Mr.Auer on 2008-02-20
I use Getdeb.net quite a lot as well, and found this thread when googling "getdeb.net malware" :)

I guess theres always more risk of compromise when using unofficial software sources. Still Id consider Getdeb better than downloading free Windows software from anywhere... And Im pretty sure that if there ever will be a problem with some package on Getdeb, someone will notice it and tell us all about it pretty soon. There are so many technical minded, skilled and paranoid Linux users out there that im sure theyd notice a backdoor or trojan eventually. Many are running all kinds of monitoring and packet sniffing programs.

Im not so skilled, but I do go through my system logs now and then. Folder /var/log is your friend :) Most important ones being auth.log and syslog. I also run fail2ban, which monitors login attempts (ssh, ftp, apache etc) and bans ips if they fail at login a given number of times. Fail2ban also logs. You can also have Conky draw the last lines of logs on your desktop ("tail /var/log/auth.log" or something).

Now and then I also run a basic system check with chkrootkit and rkhunter, both are in repos. They check for known rootkits, sniffers and trojans, and check some system files for alterations and search for hidden files. They catch only known stuff, but they can catch stuff an unwary hacker has left unhidden.

All this is mostly paranoia, but I think its good to know at least the basic logs of your machine, even if Linux is pretty secure. And its always good to be wary of installing programs from the net.
That said, Ive used Linux for 4 years and ive never had any security problems, nor have I heard of anyone having any.

Only thing Ive seen is hackers trying to login to ssh when I have it open to internet (for logging in remotely). I once noticed someone trying usernames and passwords in my native language only, thousands of em. Thats when I installed fail2ban, and that took care of it. Its important to have a strong password thou! Now I have also limited ssh logins to only those ips I will be logging in from, and use a key to verify also.

---

