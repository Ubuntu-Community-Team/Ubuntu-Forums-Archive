---
title: "Canonical Commercial Repository isn't working (Edgy)"
date: 2006-10-28
forum: Repositories &amp; Backports
---

### Post by Aranel on 2006-10-28
Edit: Figured out why - see third post.

Hi there. I'd like to be able to use the Opera browser and RealPlayer, but I'm having some trouble. I've added Canonical's commercial repository for Edgy, and... it's just not working. It claims to, but it doesn't.

This is my sources.list:

> # 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I believe that's done correctly. This is what "sudo aptitude update" returns:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [189B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 5B in 1s (3B/s)  
Reading package lists... Done

As you can see, no errors. But when I enter "sudo aptitude install opera realplay":

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for opera
Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Using "sudo apt-get update" or reloading from Synaptic didn't help either. Applications > Add/Remove... also doesn't recognize them - even though it *did* list Adobe Reader, Flash Player, and JRE before I'd even added the Multiverse repository. Something is obviously not right here, and I'm stumped as to what it is. Any ideas? I mean, I know I can install Opera directly from its website (or deb.opera.com) and convert RealPlayer's RPM with Alien, but I'd like to be able to do it through Apt... :-k

---

### Post by Aranel on 2006-10-28
What the...? I just replaced "edgy-commercial" in my sources.list file with "dapper-commercial" to see what would happen, and it... um... worked. I went to the repository with a Web browser, and I couldn't see any discernible difference between Dapper and Edgy - they're both there, anyway - so what gives? Should I just wait and try Edgy's native repository again in a week or so? :neutral:

---

### Post by Aranel on 2006-10-28
Uhh... right. Take a look at this:

[http://archive.canonical.com/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/dists/dapper-commercial/main/binary-i386/Packages.gz)

And compare it to this:

[http://archive.canonical.com/dists/edgy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/dists/edgy-commercial/main/binary-i386/Packages.gz)

Notice a difference?

The Packages.gz for Edgy - presumably, what Apt reads to list the packages - is BLANK. *That's* why it doesn't work. Any clue when this will be fixed? #-o

---

### Post by Pinoy915 on 2006-10-29
I want to know what's a good recommended source list for Edgy. I had everything working fine in Dapper but I have Edgy now and it's making me want to go back.

---

### Post by markba on 2006-10-30
I filed a bug, reporting that repo edgy-commercial does not work and dapper-commercial does:
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/69396](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/69396)

---

### Post by Colonel Kilkenny on 2006-11-01
I hijack this thread, sorry.
I wonder if Canonical will update it's version of Opera?
If they are not going to keep up with current versions the whole repository will lost it's meaning. 
Opera 9.02 and 9.01 has been released a long time ago and 9.10 is on it's way.

Either throw the whole repository out of the picture or keep up with apps on that repo. This current situation sucks.

---

### Post by JimTDI on 2006-11-01
> **Colonel Kilkenny said:**
> I hijack this thread, sorry.
I wonder if Canonical will update it's version of Opera?
If they are not going to keep up with current versions the whole repository will lost it's meaning. 
Opera 9.02 and 9.01 has been released a long time ago and 9.10 is on it's way.

Either throw the whole repository out of the picture or keep up with apps on that repo. This current situation sucks.


Not to continue the hijack, but I couldn't agree more!  Trying to get Opera into Ubuntu, especially Edgy was challenging to say the least, and it's 9.0x - I went back to Dapper just to be able to get the package,  I know I probably didn't need to, but I'm a newb, and that was easiest for me, since I couldn't get the repositories in Edgy to find it - and I didn't want to bastardize my Edgy by installing unsupported packages.

I know, others got it to work by installing the .deb file of Opera 9.02 from Opera's site, and I tried that in Edgy, but the errors scared me (even though it seemd to work OK).

Need my Opera for my browsin; and email dontcha know...  :-D

---

### Post by markba on 2006-11-06
> **JimTDI said:**
> ... others got it to work by installing the .deb file of Opera 9.02 from Opera's site
Opera has it's own repo, [http://deb.opera.com/](http://deb.opera.com/). I haven't tried it though because I keep changing the way I install Opera:
(Dapper, only Opera-static works)
- .deb from Opera-site (which means no automatic upgrading)
- repo from Opera [http://deb.opera.com/;](http://deb.opera.com/;) later on a gpg-key was required, this wasn't the case initially!
- standard Ubuntu-repo (universe or multiverse, I don't remember)
(Edgy) 
- commercial repo (though the edgy repo is empty, but dapper-commercial works: [https://launchpad.net/distros/ubuntu/+bug/69396](https://launchpad.net/distros/ubuntu/+bug/69396))
- as noted from another poster, the commercial repo only contains 9.00 while the actual version is 9.03
- on the plus side, opera package works without dependency problems, on Dapper only opera-static worked for me 

They have been messing around with Opera a little bit too much, due to this instability costing too much energy each time they change the way Opera can or must be installed. For my self, I think I will settle with the Opera-repo.

---

### Post by atonaldenim on 2006-12-21
I was having similar problems in Edgy getting Realplayer 10 from the Canonical repository. I found that you could open [http://archive.canonical.com](http://archive.canonical.com) in a web browser, and from there I downloaded the appropriate .deb ```
[URL="http://archive.canonical.com/pool/main/r/realplay/realplay_10.0.8-0ubuntu1_i386.deb"]
http://archive.canonical.com/pool/main/r/realplay/realplay_10.0.8-0ubuntu1_i386.deb[/URL]
```
and installed it with dpkg
```
sudo dpkg -i realplay_10.0.8-0ubuntu1_i386.deb
```
worked great!

---

### Post by pinguinus on 2007-01-06
Any replies or information from Canonical about this bug? 

Or is it so that their commercial repo is meant only for LTS (long term support) releases of Ubuntu (= Dapper), and not for the more edgy releases in betweeb those LTS releases?? However, there is not that much commercial software included that maintaining a proper commercial repo also for edgy should be a problem?

Or maybe this problem has already been solved? Sorry, haven't tested the repo recently. :???:

---

### Post by PriceChild on 2007-01-06
you may wanna read this blog post that appeared on planet: [http://robitaille.wordpress.com/2007/01/06/the-canonical-commercial-repository-6-months-later/](http://robitaille.wordpress.com/2007/01/06/the-canonical-commercial-repository-6-months-later/)

---

### Post by pinguinus on 2007-01-06
Thanks for posting the information, PriceChild.[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=43712")

---

