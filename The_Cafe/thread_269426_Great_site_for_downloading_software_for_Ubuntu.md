---
title: "Great site for downloading software for Ubuntu"
date: 2006-10-01
forum: The Cafe
---

### Post by saracen on 2006-10-01
It's like a download.com for Ubuntu!  Did u guys know about this?  I tried searching around the forums but didn't find another thread on it so I figured I'd post it here:

[http://www.getdeb.net/](http://www.getdeb.net/)

I'm sure there'll be more sites like this popping up and now that it's so easy to install software just by double-clicking on a .deb, we should really start to rethink the whole virus / security situation.  One thought I had was to allow users to install software in their home directories [without requiring admin rights]("http://ubuntuforums.org/showthread.php?t=264408").  This would enable them to run software in a sandbox that cannot damage the rest of the system.  The worst it could do is delete files from or corrupt their home directory, which is obviously potentially terrible but it at least wouldn't spread to the rest of the system.  It would still be able to spread over the network so a way to also see which programs are accessing the network and when would be useful too.

---

### Post by Bloodfen Razormaw on 2006-10-01
Why the hell would you want to go to a web site, manually download a deb, and install it, when you could just have it automatically installed from a signed deb retrieved from a trusted, secure repository?  Managing software from a single program is far easier than having to hunt it down in a web browser, download it, hunt it down in a file browser, and starting an installer.

---

### Post by maniacmusician on 2006-10-01
not every piece of software is available for ubuntu. I'm assuming that these guys find the software that isn't and make debs of it. havnt looked at the site yet, but that would be the smart thing to do. Or if its really like download.com, it'll be providing reviews and stuff of programs, which could be useful.

edit: it has some common software, and some not so common software.

things i didnt find in the repos: 
SDLJump, Goby, PCMan file manager, Incollector, TunaPie, Geany, GNOME Sudoku, AbsVolume, Agave, Exaile.

granted, they're not ALL useful, but it's nice to have a source for debs that aren't in the repos.

---

### Post by 13east on 2006-10-01
...but it is still good to have another option for programs that you can't find in the repository

thx saracen

---

### Post by mips on 2006-10-01
Why ? You've got the main, universe & multiverse + other non-free repos to install software from via a single click in Synaptic/Adept...

---

### Post by Bloodfen Razormaw on 2006-10-01
Installing software that isn't from a trusted repository is a sure way to:
a) hose your system, since the packager was incompetent
b) put more work on you, since upgrading won't be automatic
c) introduces virii and other security threats into the equation.  The whole reason Windows has a virus problem is people running all sorts of untrusted programs.

Fortunately, we can at least fix b, since apt is specifically made to accept specific repositories.  If these people want to package more software they should just make their own repository for you to add to your lists.

And if you are that upset about Ubuntu's lack of software, just install Debian and you will get the largest repository in existence without the potential compatibility problems between Ubuntu and Debian.

---

### Post by gnomeuser on 2006-10-01
This sounds like one of the biggest security risks imaginable.. Installing things off of random websites, it just seems like asking for it.

Honestly doesn't anyone stop to think about these kinds of things? This is the very root of many of the security problems with Windows and the way to solve it is to have a filter on installable software (in our case let's call it Universe). There is exactly zero trust in that system and if anything in that repo has network access all it needs is a tiny security hole and your box is deadmeat.

Bringing the Windows world one step closer to Linux and not in the good way.. I'm scared.

---

### Post by saracen on 2006-10-01
> **mips said:**
> Why ? You've got the main, universe & multiverse + other non-free repos to install software from via a single click in Synaptic/Adept...

Why?  Because if you're running Dapper you're stuck with the versions of software that were available before feature freeze on Dapper.  The level of testing and authentication that goes into making a package for the official repos prevents the latest and greatest software from being available right away and it is also against the policy to have newer versions of software that have feature updates.  A perfect example of this is firefox.  Dapper will be officially stuck with firefox 1.5 and security fixes will be backported, but it will not update to firefox 2.0  when it is released.  If you want the latest software, you need to go elsewhere.  This is one new option and I personally think it's great.

However, like I said, the door now opens for malicious software to be introduced since these are unsigned debs that are pre-packaged by someone in the community.  The solution is not to restrict users, but to be more intelligent about how we can protect their computers from potential threats.  Users will always be on the lookout and will always want to try the latest and greatest.

---

### Post by lamego on 2006-10-01
> a) hose your system, since the packager was incompetent
Are you assuming I am incompetent ? Are the Ubuntu maintaners incompetent because they broke some hundreds systems they are paid to support ? No, They failed on quality assurance, yes. I and the other people for GetDeb may also fail.

> b) put more work on you, since upgrading won't be automatic
You mean automatic as as you can't get the newest version that you may need ?

> c) introduces virii and other security threats into the equation. The whole reason Windows has a virus problem is people running all sorts of untrusted programs.
Once again you are assuming the people behind GetDeb are not trusthfull while the hundreds of programmers/maintaners are.

Please give me a break.

If you don't feel the need for GetDeb just don't make assumptions or theories about people you don't know nothing about.

Thanks

---

### Post by lamego on 2006-10-01
> This sounds like one of the biggest security risks imaginable.. Installing things off of random websites, it just seems like asking for it.

1) You are not installing from random sites, you are installing from a single site

2) I get the sources from the same random sites the debian/ubuntu maintaners do, I don't care much aboute quality and system integration as they do, the risk you have is the same of compiling something from the source (unless you usually check the source for malware before compiling/trying, which I guess you don't).

What's next ? Installing from source is a security risk ?

---

### Post by OffHand on 2006-10-01
Using your computer is a serious security risk  :cool:

---

### Post by saracen on 2006-10-01
lamego, the point is that we have to trust you and we don't know you.  I didn't know you were the maintainer till you started posting on this thread.  I feel a bit better that you're an active member of the forums, but still, it involves a strong level of trust since installing software requires admin priveleges and potentially you could be inserting anything into the binary debs that we download.

Like I said, you are not the first and you will not be the last person to start offering pre-packaged software for Ubuntu.  Many people already do and even as you said, compiling and installing from source without checking the source also introduces the same types of threats.  Except with the source you can actually check it, even though again as you said, no one really does.

But we do trust the Ubuntu repo maintainers to have done the necessary examination and authentication of the software in the repos.  What options do u have to make your packages be more secure?  I guess having your own key and signing would be one way for us to at least know that the software did in fact come from you.  And if you develop a solid reputation, which it looks like you will, then this will be a strong level of security.

In the end it all boils down to trust.  In any case, hats off to you for starting the site.  I've already downloaded a couple of things and they're working swimmingly so far.

---

### Post by Bloodfen Razormaw on 2006-10-01
> **lamego said:**
> What's next ? Installing from source is a security risk ?
Did you compare the checksum of the source tarball against the known valid checksum to ensure it has not been tampered with?  Are you familiar with the source?  If you answered yes to either of these, then you are not securely installing software.

Edit:
> If you don't feel the need for GetDeb just don't make assumptions or theories about people you don't know nothing about.
Exactly what I am doing: not assuming you are trustworthy just because you say so.  I don't know who you are or why you duplicate work.  You can't expect people to trust you by default.  The security world prefers whitelisting.  It is on you to prove that your software undergoes the same QA and has trustworthy people.

---

### Post by gnomeuser on 2006-10-01
> **lamego said:**
> 1) You are not installing from random sites, you are installing from a single site

2) I get the sources from the same random sites the debian/ubuntu maintaners do, I don't care much aboute quality and system integration as they do, the risk you have is the same of compiling something from the source (unless you usually check the source for malware before compiling/trying, which I guess you don't).

What's next ? Installing from source is a security risk ?

Give me a reason to trust you... just one.

The openness of code is protection in itself, if everything is open and your name is on the package what reason do you have to do anything mean? 
Especially since every experiement run like this it has taken a matter of hours to detect and fix the problem and punish the responsible person. I remember this being tested by a KDE developer about 2 years ago..

I don't trust random binaries from the web, sorry - when getting into Universe there's a contract to be signed, your reputation is on the line and everyone will know that either your key was compromised or that you are a bad guy if something happens. With your site all I have is your word, I don't trust that further than I can throw it.

Sorry this is the wrong way around, there's a reason we have Universe, rather than maintaining packages outside it, become a master of the universe and enjoy the benefits. The rest of us can enjoy the trust then and the ease of upgrading everytime you release a new version.

---

### Post by lamego on 2006-10-01
saracen,
open source is all about trust, you trust all the people that work the hundreds of programs of the hundreds of packages, ubuntu/debian repositories do give you a better security just because of their reputation, I don't believe they scan for security problems on software  they include on the repositories with much more detail than I do, unless they don't trust the software authors.

I do understand your point, and I do think people should understand that installing .deb packages from untrusted sources is a bad practice.
GetDeb is not a random site, it has a clear statement and hopefully will get some reputation (right how it has a few days of life).

GetDeb is not a miraculous upgrade for everybody, it is just another resource for people which has special needs (needs that can't be addressed with the official versions).

I found it much more dangerous to see people adding strange repositories to their list and breaking their systems (dependency problems) just because they need a specific program.

---

### Post by ComplexNumber on 2006-10-01
this has been available for rpm systems for years. i don't see what peoples problem is with this getdeb website. personally, i think i would far rather trust getdeb than the ubuntu repos (eg broken X, broken cups, firefox changes, etc).
[URL="http://autopackage.org/index.html"]
[/URL]

---

### Post by maniacmusician on 2006-10-01
I appreciate your effort to provide an easy way to get the latest packages. I see you have some pretty common software on there, and thats fine, as you introduce beta versions and new releases of those. But what I find really interesting is your effort to package and introduce programs that aren't in the repos. that would really be the most implementation of getdeb, and it's cool to see that you're already all over it. 

I wouldnt trust the security of my computer to just anyone, but I'm not a paranoid coot either. having seen you around the forums lamego, i can safely say that I do trust your site. perhaps you should try to get some official sponsorship? you've already got some people sold that your site is trustworthy (like me), but official sponsorship should help to ease the minds of other people.

---

### Post by ILIJA on 2006-10-01
that site is awesome!! thanx alot!

---

### Post by lamego on 2006-10-01
> Give me a reason to trust you... just one.
Because I am an opensource developer and supporter, why do you need a reason from me and not from all the other open source developers of all those binary packages that you have installed ?

> The openness of code is protection in itself, if everything is open and your name is on the package what reason do you have to do anything mean?
Especially since every experiement run like this it has taken a matter of hours to detect and fix the problem and punish the responsible person. I remember this beiGive me a reason to trust you... just one.
My name is open, its written at the bottom of the getdeb page, the source for each package is provided on the home page link.

> 
I don't trust random binaries from the web, sorry - when getting into Universe there's a contract to be signed, your reputation is on the line and everyone will know that either your key was compromised or that you are a bad guy if something happens. With your site all I have is your word, I don't trust that further than I can throw it.
Once again, my name is on the line.

> Sorry this is the wrong way around, there's a reason we have Universe, rather than maintaining packages outside it, become a master of the universe and enjoy the benefits. The rest of us can enjoy the trust then and the ease of upgrading everytime you release a new version.ng tested by a KDE developer about 2 years ago..

Sorry, but I got bored while reading how to become a MOTU, we do not all have the same philosofy or purpose in life, I found it would be more usefull to provide 0 day upgrades with "click and run". I do feel I did the proper thing from the positive feedback I am getting from a lot of people.

---

### Post by Jesterday on 2006-10-01
Man, I see a lot of paranoid people here, I download whatever whenever, and deal with the consequences when they happen. As a Newfoundlander, I trust everyone until they give me a reason to think differently. Sometimes, it can be a look, or a twitch or even the way they talk, but still until you try it or hear something bad about it, trust it. Someone out there is trying to provide a service. (And a good one at that)

If everyone thought this way, then great sites like ebay wouldn't exist (I think it is great because I live in a town of 10000 people in the middle of nowhere), I can't buy Hockey equipment here, so I order it from ebay, so if I can't get something from Synaptic I'll download it from GetDeb, I am not going to go without something because it isn't in the repos.

I wish people would just learn to trust until they are given a reason not to, it isn't like if you got a virus or your system crashed it would be the end of the world, just start over. With all you have learned from the Ubuntu Forums, it would only take a matter of hours to get completely back up and running as you are right now.

Anyway, enough of a trust rant from me!

Darren

P.S. Remember to back up your work!

---

### Post by Kayne on 2006-10-01
I for one think that this project is great and has potential, all more so if it focuses on popular apps (for example Banshee), which you can get there updated.
I'm for sure not the only one who doesn't want to sit on one version for 6 months of an particular application.

And please ignore the paranoid people here, who think that 99% of teh int@rn3t consists of virus , spyware and hax0rs.

---

### Post by 3rdalbum on 2006-10-02
Who here has Flash Player 7 or Skype on their Linux boxes?

These are packaged by people we don't know, with no source code available, yet practically everyone uses them. How do we know that they're not calling home with information about our systems?

If you don't trust the maintainer of [www.getdeb.net](www.getdeb.net), why trust a completely closed corporation?

There is a market for .debs of updated versions and things which aren't in repositories, and people in the RPM world install such things all the time. I also know for a fact that people here in the DEB world install Checkinstalled and properly packaged .debs that others have given them. What's the difference?

---

### Post by aysiu on 2006-10-02
Even closed source software has license agreements, which have to let you know if they contain spyware. They won't use the actual word *spyware*, of course, but if they "phone home" without letting you know, they're legally in deep shit.

[http://www.adobe.com/products/eulas/players/flash/](http://www.adobe.com/products/eulas/players/flash/)
[http://www.skype.com/company/legal/eula/](http://www.skype.com/company/legal/eula/)

---

### Post by Johnsie on 2006-10-02
One word.... FREEDOM

The package maintainers can't be expected to have every application on the planet. If someone wants to install a .deb off the web then that should be their choice since it's their computer.

Yes it maybe a little more risky, but I don't really think the Ubuntu maintainers should have the final say on what I can and cannot install.

If Ubuntu maintainers force a software selection on me then they would be no batter than microsoft.

I'm glad that there are other options for installing software because I would hate to lose my software freedom.

---

### Post by matthew on 2006-10-02
FYI, I took a look at the site and installed a couple of things from it (I could fix it if something goes screwy...). Anyway, everything seems legit to me. I didn't look through every piece of software, though, so if you are the paranoid type stick to what you know.

I also looked through Launchpad and other places and can't think of a single reason lamego would risk his reputation over something so silly. I think he just thought this was a way to give back based on something he was doing for personal use anyway. Of course, this is unsupported software, so if that makes you uneasy it's best to avoid it (you can always learn to compile your own).

My personal advice in this thread: give the guy a break, he's just trying to do something nice. If it doesn't suit you you certainly have lots of other options. The risks have been stated, let's move on.

---

### Post by Nonno Bassotto on 2006-10-02
I think that this site can be a great resource and I appreciate the work you're doing. For what concerns the security I agree that there is some issue, but I think it is better than downloading each piece of software not in the repos from a different site.

Just a question: wouldn't it better to set up a repository for it? Would this require much more work?

---

### Post by EdThaSlayer on 2006-10-02
> **saracen said:**
> It's like a download.com for Ubuntu!  Did u guys know about this?  I tried searching around the forums but didn't find another thread on it so I figured I'd post it here:

[http://www.getdeb.net/](http://www.getdeb.net/)

I'm sure there'll be more sites like this popping up and now that it's so easy to install software just by double-clicking on a .deb, we should really start to rethink the whole virus / security situation.  One thought I had was to allow users to install software in their home directories [without requiring admin rights]("http://ubuntuforums.org/showthread.php?t=264408").  This would enable them to run software in a sandbox that cannot damage the rest of the system.  The worst it could do is delete files from or corrupt their home directory, which is obviously potentially terrible but it at least wouldn't spread to the rest of the system.  It would still be able to spread over the network so a way to also see which programs are accessing the network and when would be useful too.


Nice!! now it will be easy to get several programs...but...i will have to just trust that this site is offering good .debs...


btw-Thanks!!!!Now i can finally look through software and go back to my pastime of installing...tons of applications ^_^.Whoever made this site is a genius!!*makes it easier to find software*

---

### Post by lamego on 2006-10-02
> Just a question: wouldn't it better to set up a repository for it? Would this require much more work?
I don't like the idea of a repository because they will just upgrade the entire system, once you have the application installed tou can't select what you want in or out of upgrades, that can be dangerous because on GetDeb you don't have the quality control of a Ubuntu/Debian maintainer.

At the current stage it is preferable to have manual upgrades, you will be sure you don't break your system with updates you may not need/want.

---

### Post by saracen on 2006-10-03
> **lamego said:**
> I don't like the idea of a repository because they will just upgrade the entire system, once you have the application installed tou can't select what you want in or out of upgrades, that can be dangerous because on GetDeb you don't have the quality control of a Ubuntu/Debian maintainer.

At the current stage it is preferable to have manual upgrades, you will be sure you don't break your system with updates you may not need/want.

Agreed.  On another note, it would be great if you had a mechanism for requests.  I have one right now: [IceWeasel]("http://www.gnu.org/software/gnuzilla/").  It's a GNU variant of firefox without the non-free binaries that firefox distributes with their browser.  Otherwise it looks and feels just the same and you can install all the extensions/themes from the firefox website like you normally do.

---

### Post by lamego on 2006-10-03
There will be user registration with a request mechanism and updates notification via email, for now I need to keep both the site development and packaging alive so it will take some time.

Do you have a direct link for an IceWease release ? I only found the cvs info, I would prefer to build from a release.

---

### Post by Kayne on 2006-10-03
I would add Banshee (with official plugins) to the list, since the 0.11 release is really a huge improvement. 
[http://www.banshee-project.org](http://www.banshee-project.org)

---

### Post by mips on 2006-10-03
[http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)
[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

Are two things I would like to see packaged for Ubuntu as they offer segmented downloading.

---

### Post by lamego on 2006-10-03
wxdfast was added:
[http://www.getdeb.net/app.php?name=wxdownload%20fast](http://www.getdeb.net/app.php?name=wxdownload%20fast)

I will build aria2 later, I have other packages to build right now :)

---

### Post by mips on 2006-10-03
Thanks !

If you are a Kubuntu user you need to install  libwxgtk2.6-0  for wxdfast.

---

### Post by lamego on 2006-10-03
Does Kubuntu comes with .deb associated with gdebi on whatever is the Kubuntu default browser ? (Konqueror?). If yes it will take care of installing wxgtk ;)

---

### Post by Nonno Bassotto on 2006-10-03
The following two have their own repositories, but if the idea is to get new software only from one trusted source, they could be packaged too.

[Listen]("http://listengnome.free.fr/")
[Picard]("http://musicbrainz.org/news/picard.html")

The problem is that they depend on some libraries, also available via the respective repos.This is why I thought it would be better to create a repository than giving single packages. I don't know how frequent is this situation.

---

### Post by weatherman on 2006-10-03
I have one more for you as well, afaik the blackbox planning system is not in the repos
you can get the source from here:
[http://www.cs.washington.edu/homes/kautz/satplan/blackbox/blackbox-download.html](http://www.cs.washington.edu/homes/kautz/satplan/blackbox/blackbox-download.html)

---

### Post by mips on 2006-10-05
> **lamego said:**
> Does Kubuntu comes with .deb associated with gdebi on whatever is the Kubuntu default browser ? (Konqueror?). If yes it will take care of installing wxgtk ;)


Konqueror is the default browser. When you select install package from Konquerer it starts fine then gives you a dependancy error. you have to manually install the lib then try again.

---

### Post by John.Michael.Kane on 2006-10-05
nedit could be a nice addtion for those who may need/want it. [http://www.nedit.org/](http://www.nedit.org/)

---

### Post by mips on 2006-10-05
> **SD-Plissken said:**
> nedit could be a nice addtion for those who may need/want it. [http://www.nedit.org/](http://www.nedit.org/)

It's in the repos. I tried installing it earleir today looking for a CygnusEd equivalent but it did not work though. It installed but wont run...

---

### Post by darkhatter on 2006-10-05
if you are this worried about software you should not be using a computer, nothing more at that. There are people that freak out if I log into root.

---

