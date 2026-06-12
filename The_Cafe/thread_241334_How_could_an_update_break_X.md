---
title: "How could an update break X?"
date: 2006-08-22
forum: The Cafe
---

### Post by Carrots171 on 2006-08-22
[The latest updates for Ubuntu break X!]("http://www.ubuntuforums.org/showthread.php?t=241254"). This problem has been fixed (the fix may not have hit the repositories yet, check the thread above), but a whole lot of computers (including mine) have gotten screwed up. Luckily, instructions on how to fix it were posted on these forums! Good job guys! =D>

This problem does bring up many questions, however: How could a bug in the update that breaks the whole x-server (and for that matter breaks the computer) have gotten into the repositories? What exactly happened?

---

### Post by tseliot on 2006-08-22
A human mistake I guess. Did you ever make a mistake?

Well I did (many times) ;)

---

### Post by mrgnash on 2006-08-22
If there's a bug in the update for the xserver-xorg-core, then yeah, it can break X :-D

---

### Post by slimdog360 on 2006-08-22
Ive made a mistake once, I thought that I made a mistake but it turns out that I didn't so I made a mistake about that.

---

### Post by Rackerz on 2006-08-22
> **slimdog360 said:**
> Ive made a mistake once, I thought that I made a mistake but it turns out that I didn't so I made a mistake about that.

Lol, you learn from your mistakes ;).

---

### Post by win_zik on 2006-08-22
> **tseliot said:**
> A human mistake I guess. Did you ever make a mistake?

Well I did (many times) ;)

Oh many.
However, afaik I'm not a distribution that claims to offer a stable, enterprise ready linux distribution.

Breaking X in a stable release is something that simply must not happen.

---

### Post by %hMa@?b&lt;C on 2006-08-22
oh no! I just installed the update! How do i fix it, I have not rebooted yet though.

---

### Post by philipgm on 2006-08-22
Ubuntu has been installed by a lot of people who are not used to using the CLI and who will find fixing this problem very stressful, assuming that they have a spare system to look in these forums for the solution. The size of the installed base means that mistakes are much more difficult to tolerate in terms of the reputation of a distribution.

It seems to me that this could have cost Ubuntu some of its installed base and shows that there is some problem with the testing procedures. Since I can't believe that this software wasn't tested before going into the repos it seems to me that testing may have been limited to systems with the Intel bridge problem that the update says it fixes. The implication being that more testing needs to be done (obviously) but Ubuntu developers don't have unlimited access to hardware. Therefore, more people need to volunteer to test updates and I'd like to know how to do that!

---

### Post by %hMa@?b&lt;C on 2006-08-22
ok, i downgraded by going into synaptic and searching for 
"xserver-xorg-core" 
and then doing 
Package>Force version to dapper instead of dapper-updates. That should work

---

### Post by chaosgeisterchen on 2006-08-22
Humanity comes to its borders when it comes to the economical point of view. However.. Ubuntu cannot claim to be server capable if something like _that_ happens. I know that a professional server has no X. But just in case.. and imagine companies using ubuntu and updating the machines enterprisewide... 

oh my god.. it's horrible. 

Ubuntu can claim to be human, but this has nothing to do with it. Just an very annoying 'bugfix'

---

### Post by Suzan on 2006-08-22
I think, it has been tested, but not well enough!

It seems the problem don't appear on ANY system with any graphic-chip. 

So the Ubuntu-Team has to think of a better testing procedure. This will be tricky because of the many different graphic-chips. 

But I am agree... if a distro claims "ready for enterprise" such failures are very dissapointing.

I am shure, the Ubuntu-Team will discuss this.

---

### Post by missmoondog on 2006-08-22
do you know how frustrating this would be to a person without a second computer? I would be jumping right back to mandriva right now, if i didn't have a way of checking for the reason why 3 of my systems are now screwed. thank goodness for these forums and the rapid fixes (and multiple computers!!)

no wonder i actually made a contribution to the forums/ubuntu stuff. first time in my life i've ever done that too!!

now, to see if i can fix this mess. definitely needs better testing before releasing these things.

---

### Post by Yossarian on 2006-08-22
>  Posted by **jeffc313**
ok, i downgraded by going into synaptic and searching for
"xserver-xorg-core"
and then doing
Package>Force version to dapper instead of dapper-updates. That should work

Thanks for the tip, I just tried it.  For anyone trying this, you select "xserver-xorg-core" in Synaptic, and select from the menu bar Package => Force Version.  Change the item in the drop-down box to the version that ends in "(dapper)" and not "(dapper-updates)" and click "Force Version".

Breaking X with an update is decidely not cool.

---

### Post by chaosgeisterchen on 2006-08-22
This is true. As a linux newbie you will get very disappointed by all of the ubuntu project.

As you know.. newbies do not know how to handle command line. And finding out by yourself how to cope with this (first apt-cache policy xserver-xorg-core to get the older version and then installing it directly -> I did not know this option is existent) is not a issue for newbies...

---

### Post by slimdog360 on 2006-08-22
To be quite honest to me this feels like a big let down. Its just that for me the only time something has gone wrong is when it was my fault. This is the first slip up Ive seen the developers make. Quite a stupid one to, I mean dont they test these things properly before putting it up on the servers?
nuff said

---

### Post by bonzodog on 2006-08-22
People fail to remember that X breakage does not equal a 'broken computer'. 

I think it would be hoped that most users can use the system entirely from the command line, including web browsing with something like links2.  It would also help if people made themselves familiar with aptitude and apt-get, and dpkg.

---

### Post by greggh on 2006-08-22
> **slimdog360 said:**
> I mean dont they test these things properly before putting it up on the servers?
nuff said

Apparently not. If they tested on even a few different machines this would not have happened. This is just wreckless carelessness. It's making me rethink my choice of distros. :confused:

---

### Post by raffytaffy on 2006-08-22
fix -
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo /etc/init.d/gdm restart

---

### Post by wedderburn on 2006-08-22
this wasn't a problem for thanks to a few years of using debian/ubuntu  (just rolled back xserver-xorg-core with aptitude but for a new user this would be horrible)

back when i was a new user this is the kind of thing that would make me reinstall

i wonder if it would be praticle  for a graphic fall back/safe mode for when this kind of thing happens just so non power users aren't left in the dark

---

### Post by Carrots171 on 2006-08-22
> **wedderburn said:**
> i wonder if it would be praticle  for a graphic fall back/safe mode for when this kind of thing happens just so non power users aren't left in the dark

There's actually a specification for this on Launchpad, and I think it's a very important one - both for things like this (although this was an anomaly) but for 1st-time installation when things often go wrong. You can find it here: 

[https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover]("https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover")

---

### Post by ubuntu_demon on 2006-08-22
PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by greggh on 2006-08-22
> **ubuntu_demon said:**
> PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

I think most of us have looked at that thread. But tseliot has said over and over that its pointless to bitch and moan in that thread, that it's just for support and not complaining. So we came here to bitch and moan a little. :wink:

---

### Post by slougi on 2006-08-22
The actual bug ticket is here: [https://launchpad.net/bugs/57153](https://launchpad.net/bugs/57153)
As you can see in [Comment 15](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153/comments/15) by the dev, the update was actually tested on some number of machines. Maybe for updates to really critical parts of the system in stable releases some kind of a more rigorous testing procedure should be adopted.

---

### Post by greggh on 2006-08-22
> **slougi said:**
> The actual bug ticket is here: [https://launchpad.net/bugs/57153](https://launchpad.net/bugs/57153)
As you can see in [Comment 15](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153/comments/15) by the dev, the update was actually tested on some number of machines.

Franky, I find that very hard to believe. I would like him to give the specs of the machines used for testing. If you test on a few machines all with the same basic architecture, that hardly counts as "different".

---

### Post by ubuntu_demon on 2006-08-22
> **Carrots171 said:**
> There's actually a specification for this on Launchpad, and I think it's a very important one - both for things like this (although this was an anomaly) but for 1st-time installation when things often go wrong. You can find it here: 

[https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover]("https://features.launchpad.net/distros/ubuntu/+spec/xserver-failover")
I blogged about this here (which is also going to the planet) :

[http://ubuntudemon.wordpress.com/2006/08/22/xserverfailover/](http://ubuntudemon.wordpress.com/2006/08/22/xserverfailover/)

---

### Post by slougi on 2006-08-22
> **greggh said:**
> Franky, I find that very hard to believe. I would like him to give the specs of the machines used for testing. If you test on a few machines all with the same basic architecture, that hardly counts as "different".
True, which is why I said more testing is needed. What's more, testing by more than one developer. Preferrably some way for volunteers to test as well.

---

### Post by mrgnash on 2006-08-22
> **bonzodog said:**
> People fail to remember that X breakage does not equal a 'broken computer'. 

I think it would be hoped that most users can use the system entirely from the command line, including web browsing with something like links2.  It would also help if people made themselves familiar with aptitude and apt-get, and dpkg.

An excellent point. I accessed the fix from good ole Lynx myself :P

---

### Post by slougi on 2006-08-22
It might not mean an actually broken computer. However, is it not Ubuntus goal to be usable by everyone? Dropping someone to the command line is not a good way of achieving that.

Even for people who know what to do, it is a severe annoyance, to say the least.

---

### Post by wmcbrine on 2006-08-22
As an old-time Linux user, I should've known how to do this on the command line, but I didn't. (Old-time Linux user, but I never used a Debian-based distro before Ubuntu, where I jumped right into Synaptic.) So, I started an X server on my Windows laptop, pointed DISPLAY to there, and downgraded via Synaptic.

Was everyone affected by this using an AGP card? And, was anyone using an AGP card *not* affected?

"X -scanpci" told the story for me... with the broken version, my card fails to appear in the list. It's at 1:0:0 (everything else is 0:n:n), and it shows up fine via lspci, scanpci, or the old X server. It's a Matrox G400 BTW, but I'm not sure it matters.

Re: the ChangeLog, it's misleading... the changes shown were actually for the *old* version. This is some kind of bug in Software Update, I think -- often it shows no changes at all. Anyway, the changes for the broken version (10.3, not 10) are:

xorg-server (1:1.0.2-0ubuntu10.3) dapper-updates; urgency=low

  * Added 992_linux_bios_bug_6751.dpatch (Closes Malone #36461)

 -- Rodrigo Parra Novo <rodarvus@ubuntu.com>  Fri, 11 Aug 2006 14:00:07
-0300

xorg-server (1:1.0.2-0ubuntu10.2) dapper-updates; urgency=low

  * Added 004_xf86dri_byte_swapped_clients.dpatch (Closes Malone #27459)
  * Added 005_pci_domain.dpatch (Closes Malone #54880)

 -- Rodrigo Parra Novo <rodarvus@ubuntu.com>  Thu, 10 Aug 2006 16:31:53
-0300

xorg-server (1:1.0.2-0ubuntu10.1) dapper-updates; urgency=low

  * Do actually ship xdmx-tools instead of an empty package.

  * Apply setuid fix:
    - Add patch 003_fix_setuid_handling.dpatch.

 -- Fabio M. Di Nitto <fabbione@ubuntu.com>  Mon, 10 Jul 2006 12:26:29
+0200

I assumed that 005_pci_domain.dpatch was the problem, and that seems to be confirmed by comments in Launchpad.

---

### Post by evilghost on 2006-08-22
> **tseliot said:**
> A human mistake I guess. Did you ever make a mistake?

Well I did (many times) ;)

Mistakes happen. I make mistakes, however, the problem is that an entire GUI for a distribution can be brought to it's knees by the mistake of a single person.  There **should** be procedures and checks/balances in place to prevent this from happening.

No one is shaking their fists at someone who made a mistake but I am shaking my fists that this was allowed to happen because proper Q&A procedures are either non-existant or were not followed.

Testing on a "handful" of machines isn't adequate testing for a distribution that sprawls thousands of machines.

The obvious questions are:

1) Who pushed the update into the repos.
2) How many systems were tested.
3) How the fsck could a borked update be pushed into the repos.
4) Why was the borked package never removed from the repos.

If a single person controls the destiny of what is pushed into the repos **that is a major issue**.  If others approved this update without testing **that is a major issue**.

What prevents something nefarious being pushed into the repos?

---

### Post by Orunitia on 2006-08-22
It's happened before at least once from what I remember. They really need to be more careful.

---

### Post by aysiu on 2006-08-22
Like others, I'm sorely disappointed. The plain-text password slip-up was forgivable in a sense, because it wasn't exploited much (or at all), and the end-user couldn't really tell the difference.

Basically, this X breakage forces the end-user to search for help online (these forums, IRC, the mailing list), and unless that end-user is dual-booting, has a live CD, or knows how to install and use Lynx from the command-line... that user's pretty much screwed.

---

### Post by Sam on 2006-08-22
> **aysiu said:**
> Basically, this X breakage forces the end-user to search for help online (these forums, IRC, the mailing list), and unless that end-user is dual-booting, has a live CD, or knows how to install and use Lynx from the command-line... that user's pretty much screwed.

I really agree, it could have a LOT of users who got a negative impression of Ubuntu. I hope they thought "it may happen" like I did...

---

### Post by Erik Trybom on 2006-08-22
I wonder how many users will never recover their systems from this? 

Let's say Mary set up Ubuntu with some help from her friend Mike. All he taught her was how to surf the web, install new programs from Synaptic and keeping her system up-to-date with the update manager. She likes Ubuntu well enough, but Mike set up a Windows partition in dual-boot, just in case. Then this happens.

Unless she calls Mike and he fixes it for her, chances are she'll never boot into Ubuntu again. We cannot expect everyone to have the hardware, the software or the knowledge to rescue a broken X server, and that's why it's so important to prevent it from happening.

---

### Post by Onyros on 2006-08-22
> **Erik Trybom said:**
> I wonder how many users will never recover their systems from this? 

Let's say Mary set up Ubuntu with some help from her friend Mike. All he taught her was how to surf the web, install new programs from Synaptic and keeping her system up-to-date with the update manager. She likes Ubuntu well enough, but Mike set up a Windows partition in dual-boot, just in case. Then this happens.

Unless she calls Mike and he fixes it for her, chances are she'll never boot into Ubuntu again. We cannot expect everyone to have the hardware, the software or the knowledge to rescue a broken X server, and that's why it's so important to prevent it from happening.I couldn't agree more, really.

At least this may work as very serious heads up for Ubuntu devs, from now on. It WAS serious. It's in the fine line between using Ubuntu again (IF they manage to repair X, that is) and ditching it altogether for quite a few people.

The amount of publicity this unfortunate event may garner (I imagine Distrowatch, for instance) may actually hurt Ubuntu more than we may think at first.

Oh my, Shuttleworth must be pissed, right now.

P.S.: Btw, I'm one "Mike", just like in that hypothetical scenario you presented there, mate. But I happen to have a whole lot of "Maries" right here. I have already started receiving calls and people are telling me that that OS I told them was much safer and usable than XP had broken on them. ;)

---

### Post by DoctorMO on 2006-08-22
One solution which could mitigate this problem somewhat is having a menu item in boot which says something like 'My computer is broken, Help Me!' which would load a seperate linux kernel (or the original one from 6.06.0) and load up X windows ect how ever much it can and would load a browser with news, problems and links to the forums with some good recovery information, open IRC to freenode #ubuntu-helpme would be usefull too.

Not having a link between 'Oh shit' and 'It works' is a big problem for non technical users.

As for testing, they should have packages pushed out to technical users first, so me and various other users that know how to recover the system and look on the forums can test drive new updates. this would give developers a little more buffer between updates for public and broken systems.

personaly I havn't encountered any problems in any of the systems I manage either as Ubuntu or Kubuntu, but perhaps they havn't got all their updates yet.

---

### Post by bailout on 2006-08-22
I am just imagining the the gloating from the linux community if MS released an update that caused similar problems :D Thankfully I dual boot and could use my nice reliable XP install to look for a solution ;)

---

### Post by aysiu on 2006-08-22
Yeah, if there are any anti-Linux Windows users out there who want to troll, now is the time. I've got nothing to defend this with--it was a major whoops, and it's unforgivable.

---

### Post by evilghost on 2006-08-22
> **bailout said:**
> I am just imagining the the gloating from the linux community if MS released an update that caused similar problems :D Thankfully I dual boot and could use my nice reliable XP install to look for a solution ;)

MS06-042 is pretty darned close:

1)  Random crashes affecting both XP Sp1 and XP Sp2, [http://news.zdnet.com/2100-1009_22-6106039.html](http://news.zdnet.com/2100-1009_22-6106039.html)

2) Updated patch promised 8/22/2006 but then delayed, no updated stable patch released.

3) Introduction of a new security vulnerability actively being exploited, [http://www.securityfocus.com/news/11408/1](http://www.securityfocus.com/news/11408/1)

As pathetic as this Xorg SNAFU was at least we had resolution in ~2 hours (with work-around being posted to the forums after ~30 minutes).

---

### Post by DoctorMO on 2006-08-22
unfortuantly no automatic resolutions, someone couldn't come back to their computer and discover it fixed.

perhaps we could have a cron job/on boot script which installs 'OMG Whoops' patches (and nothing more!)

---

### Post by zxee on 2006-08-23
It's obvious that this shouldn't have happened. It also reminds me of the movie Sound of Thunder-I'm a sci-fi & Bradbury fan. In that movie one of the characters says "We can't have any mistakes" to which the person listening says (summarizing) "It's completely unavoidable". In fact mistakes will always happen when you least want them too. 
The response time in getting a fix up was good but that seems to have come from the community first-rather than the devs. 
I wonder what's up with ubuntu's development community. Has there been a big turn over lately; the lost of key personel; does anyone know? (i'm thinking also of dapper's delayed yet still buggy release)
Crisis and problems are an opportunity to examine how to best deal with these things-since it's doubtful we will totally eliminate them. I'm not minimizing the problem just wanting there to be a positive response to it. I think that it's up to the ubuntu developers or the organization to provide some answers and the steps they intend to take to reduce the possiblity of a reoccurence plus their plans for corrective action.

---

### Post by grte on 2006-08-23
> **aysiu said:**
> Yeah, if there are any anti-Linux Windows users out there who want to troll, now is the time. I've got nothing to defend this with--it was a major whoops, and it's **unforgivable.**

Isn't that a little extreme?  It's not like the Ubunu devs ran over your dog.

---

### Post by The Noble on 2006-08-23
This truly is a tragic time for Ubuntu, very bad that something like this has happened. Luckily, I am using Edgy, so I wasn't affected. I feel bad for everyone, and I am shamed that this bug would have affected my friend if the Dapper install had worked a week ago. We must move ahead though, Edgy is starting to shape up well without too many problems.

Whomever pointed out that something must be going on in the Ubuntu Dev world must be right. Knot 2 for Edgy seems a little late, Dapper was delayed and had a semi-lackluster release, and X breaking must point to some stress they are going through. We Should be supportive of them now, no matter what, as it looks like they are going through a difficult time.

Good job, and good luck devs!

---

### Post by slimdog360 on 2006-08-23
> **wedderburn said:**
> this wasn't a problem for thanks to a few years of using debian/ubuntu  (just rolled back xserver-xorg-core with aptitude but for a new user this would be horrible)

Could someone tell me how to roll back a package via aptitude.

---

### Post by chaosgeisterchen on 2006-08-23
> **The Noble said:**
> This truly is a tragic time for Ubuntu, very bad that something like this has happened. Luckily, I am using Edgy, so I wasn't affected. I feel bad for everyone, and I am shamed that this bug would have affected my friend if the Dapper install had worked a week ago. We must move ahead though, Edgy is starting to shape up well without too many problems.

Whomever pointed out that something must be going on in the Ubuntu Dev world must be right. Knot 2 for Edgy seems a little late, Dapper was delayed and had a semi-lackluster release, and X breaking must point to some stress they are going through. We Should be supportive of them now, no matter what, as it looks like they are going through a difficult time.

Good job, and good luck devs!

oh my.. they have to cope with LOTS of pressure I assume...

---

### Post by Perfect Storm on 2006-08-23
I agree that it's unfortunate a thing like this happen. But what really dissapoint me is not the human error the devs made but the response I have seen on this board. Everything from cursing/threatening to change distro or back to windows. It's understandable to get frustrated for a newbie which can't the basic commands to fix the problem yet. But some comments I find (excuse my frence) redicules. Every distro have some glitches, unfortunate that ubuntu have become so big that every move/happening it takes becomes a digg.com story.

On the positive side, some people might have learned some new commands. ;)

My motto: Live and learn
so goes to members and to the devs :)

regards
A.I. Dude

---

### Post by darrenrxm on 2006-08-23
Glad I didn't upgrade to dapper.

---

### Post by truico on 2006-08-23
[COLOR="Red"]Ubuntu has been installed by a lot of people who are not used to using the CLI and who will find fixing this problem very stressful, assuming that they have a spare system to look in these forums for the solution. The size of the installed base means that mistakes are much more difficult to tolerate in terms of the reputation of a distribution.
[/COLOR]
I'm one of those and I've spent all afternoon yesterday and all of this morning to get anywhere. All the tips and ,sudo.' s so far have helped me in no way. My X-server cannot start. And looking at X-server to find the problem gives me a whole page of info that does not help me to fix anything... So the end of the story is that I will have to do a complete re-install from CD, which will erase all my documents, foto' s, addresses and so forth, because this upgrade did not give me the chance to back up... 
I love UBUNTU and wil continue to advise it to everyone, but things like this don't make me angry, they just make me cry with frustration.:(

---

### Post by Bloch on 2006-08-23
truico:

The fixed x-org is now in the repositories.

Your computer still boots to the commandline, doesn't it?

Enter:
sudo apt-get update

This updates the list of packages. Then enter
sudo apt-get upgrade

This downloads all the up-to-date packages

The reboot

---

### Post by Mr.Auer on 2006-08-23
Hehe my backup regime was flawless..I borked my Box 1 with the update (nowadays I ALWAYS patch first box 1 then box 2 in case there are problems), returned system from tarball, was back up in ten minutes without even finding out what went wrong ;) ..

Sent out alerts to other Ubuntu users I know on IRC but a few managed to bork theirs too..No prob, I told the non-technical one how to downgrade, and how to install Elinks in case a console browser is needed in the future :)

Accidents happen, and Im prepared, mostly since Ive seen bugs and accidents since my trusty Atari ST and Commodore 64..Worse bugs than this too ;) At least now I could fix it myself, even without knowing whats up. And a very fast response from devs and community..

---

### Post by twowheeler on 2006-08-23
> **darrenrxm said:**
> Glad I didn't upgrade to dapper.

Yeah me too.  I have an old K6-2 machine on which I install things to do my own testing before loading them up on the family P4.  I thought perhaps dapper would have settled into a stable state by now ... but it just happens that I chose this day to upgrade the test machine when the X server screw up occurred.  No big deal, but it is exhibit A of why I do this staging.

---

### Post by truico on 2006-08-23
Bloch, thanks. 
I tried your commands, but all I got was:
[COLOR="Blue"]Error [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) dapper Release. gpg
Temporary error with ' nl.archive.ubuntu.com'  (2x)
                     ' security.ubuntu.com' 
                     ' archive canonical.com'  etc
Getting some index files failed, either ignored or older versions used[/COLOR]

It looks as if the internet connection (adsl) is down as well.

Is there a way to re install the X-server-xorg-core from cd?;)

---

### Post by tseliot on 2006-08-23
> **truico said:**
> I'm one of those and I've spent all afternoon yesterday and all of this morning to get anywhere. All the tips and ,sudo.' s so far have helped me in no way. My X-server cannot start. And looking at X-server to find the problem gives me a whole page of info that does not help me to fix anything... So the end of the story is that I will have to do a complete re-install from CD, which will erase all my documents, foto' s, addresses and so forth, because this upgrade did not give me the chance to back up... 
I love UBUNTU and wil continue to advise it to everyone, but things like this don't make me angry, they just make me cry with frustration.:(
Only a suggestion: next time make a "/" (root) partition and a /home partition so that if you need to reinstall Ubuntu you only have to format the "/" partition and without deleting your data on /home

---

### Post by jibril on 2006-08-23
Hi guys, 
I must say that for me after updating and then upgrading, X did not work and I had to do 
$sudo dpkg-reconfigure xserver-xorg
$startx

and then it worked.

Hussain

p.s. I am glad that I knew enough NNTP to access usenet and get info about this bug

---

### Post by truico on 2006-08-23
> **tseliot said:**
> Only a suggestion: next time make a "/" (root) partition and a /home partition so that if you need to reinstall Ubuntu you only have to format the "/" partition and without deleting your data on /home

:p TSELIOT/Great Gatsby?), this is precisely what I'm going to do! Thanks.
And further:
yes, this is bad PR for Ubuntu 6.06 and great for the msnopolists, but remember: we may be still driving a T-Ford, or a Beetle for the time being, getting a flat does only stall our trip, it does not make us buy a Mercedes, does it now?:-\"

---

### Post by zxee on 2006-08-23
> **Artificial Intelligence said:**
> I agree that it's unfortunate a thing like this happen. But what really dissapoint me is not the human error the devs made but the response I have seen on this board. Everything from cursing/threatening to change distro or back to windows. It's understandable to get frustrated for a newbie which can't the basic commands to fix the problem yet. But some comments I find (excuse my frence) redicules. Every distro have some glitches, unfortunate that ubuntu have become so big that every move/happening it takes becomes a digg.com story.

On the positive side, some people might have learned some new commands. ;)

My motto: Live and learn
so goes to members and to the devs :)

regards
A.I. Dude

With all due respect to you, I couldn't disagree more.
Ubuntu is being promoted based on its ease of use and that it's a linux distro that non-geeks can use. Either Canonical actually means what it says regarding ubuntu or it doesn't and the way it makes releases, updates and bug fixes matters very much.

I've used Ubuntu since the hoary release on x386 and ppc. I am very supportive of the project and have made small monetary dontations to this project as I'm sure have others. I'm not merely a dis-interested critic, but a concerned user.

We can't pretend this didn't happen but that's sort of what I hear you saying. I don't think there won't be mistakes and problems-I don't think that at all. But in so far as this is suppose to be a different type of linux for less technically inclined users then some sort of reassurances or statements from Canonical are in order. 

Such statements should include whether or not they intend to honor the orginal direction they plotted when begining the ubuntu project. There have been several noticible problems recently. Perhaps it wouldn't hurt for Canonical or the Ubuntu project team to acknowledge that they are paying attention and/or taking corrective actions. Ignoring these issues or trying to sweep it all under the rug is a disservice to the stated mission of Ubuntu.

---

### Post by grte on 2006-08-23
> **zxee said:**
> Such statements should include whether or not they intend to honor the orginal direction they plotted when begining the ubuntu project. There have been several noticible problems recently. Perhaps it wouldn't hurt for Canonical or the Ubuntu project team to acknowledge that they are paying attention and/or taking corrective actions. Ignoring these issues or trying to sweep it all under the rug is a disservice to the stated mission of Ubuntu.

...Last I saw, it's been fixed, so what are you on about?

Seriously, this thread is so full of unnecessary drama it's unbelievable.  The ubuntu devs have not run over any pets, commited genocide, or launched a nuclear weapon.  They released an update that inconveienced users of an OS that, quite frankly, the vast majority of us have not spent a dollar on.

So yeah, some of the comments I'm seeing here are beyond ridiculous, especially since the problem was resolved so quickly.  Making a mistake is not some kind of moral failing.

---

### Post by gregb49 on 2006-08-24
First time I've had to use XP to fix LINUX. Now, let me tell you about the number of times I've had to use LINUX to fix XP ........ Ubuntu - great product - one glitch soon fixed, even by one not used to the command line. Thanks team for this great free software and the quick, easy to type, fix. Greg

---

### Post by kellogs on 2006-08-24
for me it wasn't a problem because it happens to be that im a ppc ubuntu user and this architecture seems to be not affected by the bug. I am sure next time this wont happen. we must understand everybody makes mistakes and its the first time I see a bug like this in ubuntu. people should know what a console browser is, and should know how to use it.

I think the bug reporting tools need to be refined(ie. better control from desktop/cli to send reports to launchpad), and the next time Im sure we wont see this happening again.

ubuntu has been an excellent distro to me, and this was an unfortunate little mistake, but nothing that could not be fixed in some hours thanks to the community.

there is always people who complain for whatever reason, be it ubuntu or not.   
For those I say, if you use linux, be prepared to learn. If you dont want to put a little effort from your part, linux is not for you, so dont blame ubuntu.

---

### Post by win_zik on 2006-08-24
> **kellogs said:**
>  we must understand everybody makes mistakes 
So?
> **kellogs said:**
> 
people should know what a console browser is, and should know how to use it. 
Should they? Why? Who says so?

> **kellogs said:**
> 
ubuntu has been an excellent distro to me, and this was an unfortunate little mistake, but nothing that could not be fixed in some hours thanks to the community.

It wasn't a little, it was a grave mistake. You know, killin X on a distribution that's supposed to be stable is a must not.

> **kellogs said:**
> 
there is always people who complain for whatever reason, be it ubuntu or not. 
Well, the people who complain made their reasons known. That you simply ignore what they wrote is an other story.

As for my reasons, I complain mainly about people like you who are not prepared to call a grave mistake a grave mistake thus preventing Ubuntu from learning from this mistake and improving.
> **kellogs said:**
> 
For those I say, if you use linux, be prepared to learn. If you dont want to put a little effort from your part, linux is not for you, so dont blame ubuntu.
Who else than ubuntu should I blame if something happens that shows that ubuntu's QA is not sufficient.

Also Ubuntu claims to be an enterprise ready OS, not some learning tool that reguires people to learn because it's unstable and buggy.

---

### Post by kellogs on 2006-08-24
> It wasn't a little, it was a grave mistake. You know, killin X on a distribution that's supposed to be stable is a must not.

If it is that grave to you, now that it's fixed you've got the freedom to leave to another OS. so you wont have those mistakes again, but other OSes do have mistakes too, and sometimes equally grave (osx 10.4 unbootable, winxp sp2 random crashes, anyone?) and those sometimes arent fixed in the relatively short time it was fixed in ubuntu.

> As for my reasons, I complain mainly about people like you who are not prepared to call a grave mistake a grave mistake thus preventing Ubuntu from learning from this mistake and improving.

I dont think its so grave, it would be if it did left the system unbootable, look at it this way, you have the system totally at your disposal, except X. you can do many things at this point. or boot from a livecd and try to fix the system from there.

> Who else than ubuntu should I blame if something happens that shows that ubuntu's QA is not sufficient.

Also Ubuntu claims to be an enterprise ready OS, not some learning tool that reguires people to learn because it's unstable and buggy.

Again, I think we should not complaint. A system that was given to me for 0$, and that is made with the effort of many people, and that is free... 

the least I could do would be report bugs, make patches/code to help,etc.

if you want enterprise support I think there is a paid service. If you want a perfect stable system and complain then there are some other oses out there than you can complain and pay for.

---

### Post by win_zik on 2006-08-24
> **kellogs said:**
> If it is that grave to you, now that it's fixed you've got the freedom to leave to another OS. 

Ah the old "if you don't like it here go someplace else" defense to someone being critical.
I already had this freedom to leave beforehand, but as I said, I like Ubuntu and no, I certainly won't leave. This is not about leaving or bashing ubuntu but about improving it.


> **kellogs said:**
> 
I dont think its so grave, it would be if it did left the system unbootable, look at it this way, you have the system totally at your disposal, except X. you can do many things at this point. or boot from a livecd and try to fix the system from there.

Sigh and what about the many many users who don't know what to do then? To them the system was unusable and probably unfixable.
Look at all the peopel who borked their system trying to fix this mess, read the stories of all those people who had to support friends and family who ran into this mess.

**remove due to personal attack* -- Artificial Intelligence*

the least I could do would be report bugs, make patches/code to help,etc.

> **kellogs said:**
> 
if you want enterprise support I think there is a paid service. If you want a perfect stable system and complain then there are some other oses out there than you can complain and pay for.
Oh Jebus, this is not about me having the right to get a stable, enterprise ready distro for free, this is about Ubuntu claiming to be a stable, enterprise ready distro and not delivering.

---

### Post by zxee on 2006-08-24
...Last I saw, it's been fixed, so what are you on about?

Seriously, this thread is so full of unnecessary drama it's unbelievable. The ubuntu devs have not run over any pets, commited genocide, or launched a nuclear weapon. They released an update that inconveienced users of an OS that, quite frankly, the vast majority of us have not spent a dollar on.

So yeah, some of the comments I'm seeing here are beyond ridiculous, especially since the problem was resolved so quickly. Making a mistake is not some kind of moral failing.

And in fact I never claimed any of that. You are the one getting dramatic.
I'm just stating what I see happening. Perhaps the next time you comment you want to read what you're commenting about.

---

### Post by grte on 2006-08-24
> **zxee said:**
> ...Last I saw, it's been fixed, so what are you on about?

Seriously, this thread is so full of unnecessary drama it's unbelievable. The ubuntu devs have not run over any pets, commited genocide, or launched a nuclear weapon. They released an update that inconveienced users of an OS that, quite frankly, the vast majority of us have not spent a dollar on.

So yeah, some of the comments I'm seeing here are beyond ridiculous, especially since the problem was resolved so quickly. Making a mistake is not some kind of moral failing.

And in fact I never claimed any of that. You are the one getting dramatic.
I'm just stating what I see happening. Perhaps the next time you comment you want to read what you're commenting about.

I'm commenting on the unearned sense of entitlement displayed not only in your post, but many others in this thread.  Hence why I specified "thread,: and not "you."

As to what you claimed:

> Such statements should include whether or not they intend to honor the orginal direction they plotted when begining the ubuntu project. There have been several noticible problems recently. **Perhaps it wouldn't hurt for Canonical or the Ubuntu project team to acknowledge that they are paying attention and/or taking corrective actions. Ignoring these issues or trying to sweep it all under the rug is a disservice to the stated mission of Ubuntu.***[emphasis mine]*

Did you not see the bright green notice addressing all of this right at the very top of the first page of the forum?  The one that was posted before you posted this?  That's what I mean when I ask what you're on about.

---

### Post by kigina on 2006-08-24
heh
im glad i was too lazy to update

---

### Post by Zelut on 2006-08-25
I am STILL affected by the updated even after using the later release of xserver-xorg, installing xserver-xorg-core & doing numerous dpkg-reconfigure xserver-xorg .  I've had to revert to using a Vesa driver instead of the usual ati/fglrx.

If anyone has any other tips on fixing this problem I'd really appreciate it.

---

### Post by zxee on 2006-08-25
> **grte said:**
> I'm commenting on the unearned sense of entitlement displayed not only in your post, but many others in this thread.  Hence why I specified "thread,: and not "you."

As to what you claimed:



Did you not see the bright green notice addressing all of this right at the very top of the first page of the forum?  The one that was posted before you posted this?  That's what I mean when I ask what you're on about.
Maybe that's an effective strategy attacking those who bring up problems in hopes that will make the problem go away. And your tone is very defensive. I've seen this behavior many times. e.g bashing critics and hoping that would take attention away from the issues. 
Actually when I posted my reponse to A.I. there was just a notice about the upgrade problem not the more complete notice now there.
Which BTW was not fixed in a couple of hours-The "fix" was a downgrade AFAIK provided by one of the forum staff. There were people in the help forums last night saying they couldn't use their ubuntu install, and the defective update stayed on the servers for two days. I think those that use this system have the right to question what's going on just as you have the right to obscure their efforts with ranting about it. 
I think the forum posts are a good thing, but they do nothing for people whose system is without an xserver particularly if they don't know commandline or don't have a dual boot or other computer to use. It's also within the realm of possibility that people were upgrading their systems in the two days the flawed xserver update was on the servers without coming to the ubuntu site. Of course the people who have no other computer to use can't come here and upset you.
Go ahead and rant away about this post too-for all I care.

---

### Post by zxee on 2006-08-25
> **kuyaedz said:**
> I am STILL affected by the updated even after using the later release of xserver-xorg, installing xserver-xorg-core & doing numerous dpkg-reconfigure xserver-xorg .  I've had to revert to using a Vesa driver instead of the usual ati/fglrx.

If anyone has any other tips on fixing this problem I'd really appreciate it.

It's probably better for you if you start a thread in the help forums specifying what exactly you're experiancing now.
You could also check this thread: [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)
Let me know if I can be of any other help.

---

### Post by ubuntu_demon on 2006-08-25
Tollef Fog Heen, a member of Ubuntu&#8217;s  X SWAT team blogs about X broken in Dapper :
[http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html](http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html)

My blog posts about this subject :

xserver breakage follow-up
[http://ubuntudemon.wordpress.com/2006/08/25/xserver-breakage-follow-up/](http://ubuntudemon.wordpress.com/2006/08/25/xserver-breakage-follow-up/)

XserverFailover
[http://ubuntudemon.wordpress.com/2006/08/22/xserverfailover/](http://ubuntudemon.wordpress.com/2006/08/22/xserverfailover/)

Latest Dapper xserver-xorg upgrade might break the xserver
[http://ubuntudemon.wordpress.com/2006/08/22/latest-dapper-xserver-xorg-upgrade-might-break-the-xserver/](http://ubuntudemon.wordpress.com/2006/08/22/latest-dapper-xserver-xorg-upgrade-might-break-the-xserver/)

---

### Post by zxee on 2006-08-25
Thanks, ubuntu_demon great links and I appreciate the openess very much.

---

### Post by danh on 2006-08-25
Back to the original question: does anyone know what happened? How could the faulty package slip by QA?

---

### Post by philipgm on 2006-08-25
Just like condoms, QA is not a 100% exercise. Unlike condoms it doesn't say that on the package.

If you have ever worked in QA you'll know that it is a statistical not an absolute process.

---

### Post by danh on 2006-08-26
My question was "what happened?", not "does shit ever happen?".

---

### Post by KiwiNZ on 2006-08-26
> **danh said:**
> My question was "what happened?", not "does shit ever happen?".

[http://www.ubuntu.com/UpgradeIssue](http://www.ubuntu.com/UpgradeIssue)

---

### Post by danh on 2006-08-26
So no one knows what happened yet (the above link basically only says "We have launched an investigation")?

That's really scary.

---

### Post by ubuntu_demon on 2006-08-26
> **danh said:**
> So no one knows what happened yet (the above link basically only says "We have launched an investigation")?

That's really scary.
Tollef Fog Heen, a member of Ubuntu&#8217;s X SWAT team blogs about X broken in Dapper :
[http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html](http://err.no/personal/blog/tech/Ubuntu/2006-08-24-11-36_broken_X_in_Ubuntu.html)

The points and views in that blog post are not any kind of official communication from Canonical or Ubuntu.

I suspect they want to have finished the investigation and the plans on how to prevent them in the future before they do an official announcement.

---

### Post by ubuntu_demon on 2006-08-26
> **zxee said:**
> Thanks, ubuntu_demon great links and I appreciate the openess very much.
You are welcome :)

---

### Post by kinematic on 2006-08-26
i don't know what some of you are bitching about.
conanical gives you a great os for free with a shitload of apps in the repo's and as soon a some makes 1 mistake(and we all make mistakes...that's part of being human)you start to rant and bitch and moan.
well...i'm not going to do that.
i recovered from the borked x-server 10mins after installing the update and is still think ubuntu is one of the best distro's out there today so i say big kudo's to the devs.

---

### Post by Ziox on 2006-08-26
"Experience is the name we give for our mistakes"

---

### Post by zalmoxes on 2006-09-14
its quite a pity... i have always wondered why linux is recognised by so little people. now i know. ubuntu's reputaion is generally increasing at a constant rate; but every time something like this happens, the reputation plunges... what a ridiculously serious crash i was just lucky i had another com that was not yet updated and. if this had happened one week later, i would be stranded with this single laptop and no information on how to fix it. it hasnt deterred me from continuing to use ubuntu but thats not the case for most people. i still think UBUNTU is the best linux distro and it is the ambassador of linux to the rest of the world.

---

### Post by EdThaSlayer on 2006-09-14
Hey! We are all humans!
Everybody makes a mistake!
But you should be glad that they corrected their mistake pretty quickly!

---

### Post by evilghost on 2006-09-14
The issue has not been if/why people make mistakes but rather why the proper mechanisms were not in place to prevent such mistakes from negatively impacting and disabling a multitude of Ubuntu users.  If one person is able to cripple the entire Ubuntu community of users **that** is the issue.

---

