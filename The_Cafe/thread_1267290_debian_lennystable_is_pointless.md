---
title: "debian lenny/stable is pointless"
date: 2009-09-15
forum: The Cafe
---

### Post by sena_akada on 2009-09-15
all the software is so dated. vlc can't play 50% of what i try. whats the point?

---

### Post by RiceMonster on 2009-09-15
Yeah, what's the point of well tested, highly stable software? I don't get it.

I bet you think RHEL and CentOS are pointless too?

---

### Post by ChrT on 2009-09-15
> **sena_akada said:**
> all the software is so dated. vlc can't play 50% of what i try. whats the point?

The point of stable is...wait for it...to provide a **stable** platform where everything has been 100% verified to work as intended, and not have to bother with continuous upgrades from upstream - such as in server environments. If you want a more up-to-date debian, use testing. If you want a stable, more up-to-date distro, use Arch.

---

### Post by sena_akada on 2009-09-15
> **RiceMonster said:**
> Yeah, what's the point of well tested, highly stable software? I don't get it.

I bet you think RHEL and CentOS are pointless too?

whats the point of software thats functionally out of date?

---

### Post by khelben1979 on 2009-09-15
> **sena_akada said:**
> all the software is so dated. vlc can't play 50% of what i try. whats the point?

Just activate backports and you will have more updated software on a stable system. I have Open Office 3.1 installed over here, outdated software??

---

### Post by sena_akada on 2009-09-15
> **khelben1979 said:**
> Just activate backports and you will have more updated software on a stable system. I have Open Office 3.1 installed over here, outdated software??

mhm my mistake i guess

---

### Post by RiceMonster on 2009-09-15
> **sena_akada said:**
> whats the point of software thats functionally out of date?

It's more reliable. Not everyone wants the latest cool thing. In the business world, you'll also notice that they generally do not use the latest version of everything because it's more reliable and it works.

> **ChrT said:**
> If you want a more up-to-date debian, use testing. If you want a stable, more up-to-date distro, use Arch.

Arch is not a good example of a stable distro; don't tell people that. Before you say anything, Arch is my main distro.

---

### Post by Regenweald on 2009-09-15
> **sena_akada said:**
> all the software is so dated. vlc can't play 50% of what i try. whats the point?

The point is that the majority of those dated apps are desktop use related. Debian is a powerful SERVER environment primarily. No server admin wants iffy software on their box. You need to base your OS selection carefully on *your* needs. For latest and greatest; Sidux, Fedora, Arch and Ubuntu testing come to mind.

---

### Post by aesis05401 on 2009-09-15
Adding newer packages is easy, but why would you?  Deb stable does not compete with Ubuntu or other downstream distros - they complement each other.

If you want a malleable desktop experience use Ubuntu incrementals.  If you want a workstation or server experience use deb stable.  If you want a stable hybrid then run an Ubuntu LTS w/manually upgraded packages or roll your own deb environment. 

... or do something else entirely ;)

---

### Post by dragos240 on 2009-09-15
Why not compile your packages from source :)

---

### Post by khelben1979 on 2009-09-15
> **dragos240 said:**
> Why not compile your packages from source :)

It feels like good therapy just hearing the rassle of the harddrive when I do.

---

### Post by koenn on 2009-09-15
> **sena_akada said:**
>  functionally out of date?
do you mean that programs suddenly stop working when a new version of that program is released ?

---

### Post by PurposeOfReason on 2009-09-15
$10 says it's a codec problem and you need to enable non-free.

---

### Post by sena_akada on 2009-09-15
> **koenn said:**
> do you mean that programs suddenly stop working when a new version of that program is released ?

 new? the vlc version has ww2 flashbacks :/

---

### Post by koenn on 2009-09-15
> **sena_akada said:**
> new? the vlc version has ww2 flashbacks :/

that wasn't my question.

---

### Post by nmccrina on 2009-09-15
> **khelben1979 said:**
> It feels like good therapy just hearing the rassle of the harddrive when I do.

Also, watching all the strange output flying up the screen is fun.

---

### Post by red_Marvin on 2009-09-15
Debian stable is server oriented, vlc does to not have many reasons to be installed in such an environment.

---

### Post by koenn on 2009-09-15
> **red_Marvin said:**
> Debian stable is server oriented, vlc does to not have many reasons to be installed in such an environment.

more accurately, Debian stable is 'stability' oriented, which makes it a good choice for servers, but also for any other managed environment where upgrades are subject to change management procedures. That's also the reason Ubuntu offers LTS.

---

### Post by Skripka on 2009-09-15
> **koenn said:**
> more accurately, Debian stable is 'stability' oriented, which makes it a good choice for servers, but also for any other managed environment where upgrades are subject to change management procedures. That's also the reason Ubuntu offers LTS.

Just because software is OLD does not make it STABLE.

Debian Lenny has Qt4.4.3...I remember that even by the time Qt4.4.x made it into Ubuntu it had big issues.

Qt4.5.x is FAR more stable than 4.4.3 evar was.

---

### Post by tjwoosta on 2009-09-15
> all the software is so dated. vlc can't play 50% of what i try. whats the point?

Theres no reason an older version of vlc would refuse to play certain media. Its not like they didn't have all the same media types when that version was released. If media is not playing for you its a simple codec issue, not a vlc version issue.

---

### Post by medic2000 on 2009-09-15
And also they make security fixes to packages in Debian Stable. Besides being stable security is very very important to a server oriented OS.

---

### Post by DjBones on 2009-09-15
The more likely reason that Debian stable can't play your media with VLC is that the codecs aren't in the free repositories, if you open the contrib and non-free repositories then you can install the gstreamer good/bad/ugly.

I use stable myself, but it is good to remember that it has a purpose, that it provides a platform where all the packages are at controlled versions and tested to work together well.  Debian is also a platform that is meant to be composed completely of free, non-proprietary software, and to many that is a sought after quality.  Stable shines with servers; testing is better for a desktop since its a rolling distro.  You could always upgrade to unstable if you would like the next version of ubuntu's packages before it comes out ;) ...

---

### Post by DjBones on 2009-09-15
> **PurposeOfReason said:**
> $10 says it's a codec problem and you need to enable non-free.

Beat me to it PurposeOfReaon haha.

---

### Post by Frak on 2009-09-15
Sounds like someone didn't enable non-free.

---

### Post by red_Marvin on 2009-09-16
> **koenn said:**
> more accurately, Debian stable is 'stability' oriented, which makes it a good choice for servers, but also for any other managed environment where upgrades are subject to change management procedures. That's also the reason Ubuntu offers LTS.

True, I stand corrected, my main point still works though: I.E. places where stability is a very big issue is not likely to allow their users to play random videos, so the presence or absence of codec X is not really an issue.

---

### Post by t0p on 2009-09-16
> **tjwoosta said:**
> If media is not playing for you its a simple codec issue, not a vlc version issue.

Indeed.  OP is picking on vlc (and poor old lenny) for no good reason.

---

### Post by bruno9779 on 2009-09-16
> **nmccrina said:**
> Also, watching all the strange output flying up the screen is fun.

It is good to hear these comments.
I love Ubuntu forums, but I think I have seen to often the advice "go for the .deb instead of compiling" when newer guys asked for help on compiling.

If you compile it yourself, chances are that it will work better.
Gentoo and other are based on this concept.

---

### Post by Hallvor on 2009-09-16
> **sena_akada said:**
> all the software is so dated. vlc can't play 50% of what i try. whats the point?

If you want a reliable production machine, Lenny is actually a very good choice. Yes, the software is dated, but it works. Heck, the place where I work even use IE6 as a web browser. Everything is much more dated than the software in Lenny. For a production machine stability is almost everything, and I`ll choose stability over bleeding edge any day.

---

### Post by lloyd_b on 2009-09-16
> **bruno9779 said:**
> It is good to hear these comments.
I love Ubuntu forums, but I think I have seen to often the advice "go for the .deb instead of compiling" when newer guys asked for help on compiling.

If you compile it yourself, chances are that it will work better.
Gentoo and other are based on this concept.

I've given that advice more than a few times.  Out of self-defense :)

Too often, somebody opening up a "how do I compile ..." thread is not really interested in learning about how to compile stuff - they just want the latest/greatest version of a given program.  If a .deb is available to fill their needs, then pointing them to it is the best way to get them what they want with a minimum of headaches.

Gentoo is a "tinkerers" distro - it's intended for people who have or want to acquire the knowledge of how to build stuff on their system.  Ubuntu is a "users" distro - most of the people using it don't care how to build stuff - they just want it to work.

There are quite a few tinkerers using Ubuntu (for instance, I compile a custom kernel for each of my machines).  But I for one am NOT going to try and force-feed the knowledge of how to do so on newbies who neither need nor want that knowledge.

Lloyd B.

---

### Post by HappyFeet on 2009-09-16
> **PurposeOfReason said:**
> $10 says it's a codec problem and you need to enable non-free.

I agree. I used lenny for a little while before jaunty came out, and had no problems playing anything. (I'm a media junkie) It took a little more work to set up than ubuntu, but it *can* be done.

"debian lenny/stable is pointless" simply says you don't know much about linux.

---

### Post by koenn on 2009-09-16
> **Skripka said:**
> Just because software is OLD does not make it STABLE.

Debian Lenny has Qt4.4.3...I remember that even by the time Qt4.4.x made it into Ubuntu it had big issues.

Qt4.5.x is FAR more stable than 4.4.3 ever was.
where did I say that software needs to be old to be stable ?

Also, you apparently don't understand what 'stable' means in 'Debian stable release'. It's explained on the debian website. You'll also find info there about how stable, testing and unstable interrelate.
hint: 'stable' is an adjective to 'release'.

Once you begin to understand what "Debian Stable Release" is about, you could read the wikipedia aricle on "change management (in systems engineering)" to have an idea as to why a stable release can be desirable.

---

### Post by ~sHyLoCk~ on 2009-09-17
EDIT: Oops I quoted the wrong guy. My bad. :P But yes, debian stable has nothing to do with vlc not playing files, that's just ridiculous.

---

### Post by tjwoosta on 2009-09-17
post revoked :)

---

### Post by sena_akada on 2009-09-17
also [s]firefox[/s] iceweasel is at 3.0.6 in lenny. do they apply the security updates from the newer [s]iceweasel[/s] firefox releases?

---

### Post by aesis05401 on 2009-09-17
> **sena_akada said:**
> also [s]firefox[/s] iceweasel is at 3.0.6 in lenny. do they apply the security updates from the newer [s]iceweasel[/s] firefox releases?

[http://wiki.debian.org/Backports]("http://wiki.debian.org/Backports").  

Running a proper deb stable system is not for everyone.  If you are interested in learning more about it the deb wiki is a good place to start.  I would also strongly recommend you join the debian-security-announce mailing list.  Stable and secure are general descriptions - it is up to the admin to deliver the promise of the deb system to the end-user.  In the Ubuntu world Canonical is taking on a lot of the responsibility that falls on the admin's shoulder's in deb trees.  Anyhow, I hope this thread has answered some of your questions.

---

### Post by tjwoosta on 2009-09-17
Another good advantage of using debian stable is that its much lighter weight. I have lenny xfce installed on my parents computer that has only 256mb ram and it runs flawlessly and only uses about 64mb ram at idle compared to xubuntu which was using all 256mb plus about 30mb of swap at idle.

---

### Post by RedSquirrel on 2009-09-17
> **sena_akada said:**
> also [s]firefox[/s] iceweasel is at 3.0.6 in lenny. do they apply the security updates from the newer [s]iceweasel[/s] firefox releases?

From what I've seen, Debian provides security updates for the *dependencies* of iceweasel while leaving the version at 3.0.6. Some of these updates may occur in a less than timely fashion, however.

---

### Post by RedSquirrel on 2009-09-17
> **tjwoosta said:**
> Another good advantage of using debian stable is that its much lighter weight. I have lenny xfce installed on my parents computer that has only 256mb ram and it runs flawlessly and only uses about 64mb ram at idle compared to xubuntu which was using all 256mb plus about 30mb of swap at idle.

You could achieve a similar result by installing an Ubuntu command-line system and adding the **xfce4** metapackage plus a few other goodies. Xubuntu is not as light as it used to be.

---

### Post by Hallvor on 2009-09-17
> **sena_akada said:**
> also [s]firefox[/s] iceweasel is at 3.0.6 in lenny. do they apply the security updates from the newer [s]iceweasel[/s] firefox releases?

Yes. Security fixes are backported. You can also enable the backports repository and run a newer version, but it is not necessary for security.

---

### Post by MikeTheC on 2009-09-17
@OP: Then you're not paying attention to what the whole point of having linux distros is.

---

### Post by beercz on 2009-09-17
> **sena_akada said:**
> whats the point of software thats functionally out of date?
What do you mean "funtionally out of date?" - to me it means you are using the wrong software for the wrong job.

Debian is fantastic as a server operating system - which is precisely what I use debian for, and have been for a number of years - and it has never been "functionally out of date" - it has worked flawlessly as a server operating system for years.

Right tools for the right job I suppose.

---

### Post by sena_akada on 2009-09-18
> **beercz said:**
> What do you mean "funtionally out of date?" - to me it means you are using the wrong software for the wrong job.

Debian is fantastic as a server operating system - which is precisely what I use debian for, and have been for a number of years - and it has never been "functionally out of date" - it has worked flawlessly as a server operating system for years.

Right tools for the right job I suppose.

ummmm, apart from the fact that its called debian - the universal operating system, not debian - the universal server operating system ](*,)

---

### Post by beercz on 2009-09-18
> **sena_akada said:**
> ummmm, apart from the fact that its called debian - the universal operating system, not debian - the universal server operating system ](*,)
There's nothing to stop anyone using debian on the desktop.

---

### Post by public_void on 2009-09-18
I'm still using Debian Etch, despite Lenny having been out for a while. Its as solid as a rock and I get the security updates. Might update to squeeze when it's released.

---

### Post by moster on 2009-09-18
This somehow remind me of Vista and XP suggestion. Oh, XP had bugs too. But point is, they were known :D

---

### Post by Ginsly on 2009-09-18
> **sena_akada said:**
> ummmm, apart from the fact that its called debian - the universal operating system, not debian - the universal server operating system ](*,)

Umm, so why don't you just run Testing/Squeeze instead then if you want newer software? Lot's of people do... If it's just for a home desktop it's stable enough, and not that hard to look after.

Looking at the Debian Packages lists, and the version of VLC in the Squeeze repo is newer than the one in the Jaunty repo. So too is Xfce, Gnome, KDE, XMMS2, Banshee, Ryhythmbox...

---

