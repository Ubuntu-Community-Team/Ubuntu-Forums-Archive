---
title: "Will be a Ubuntu Server Distro someday?"
date: 2005-05-16
forum: Server Platforms
---

### Post by ejms07 on 2005-05-16
I was wondering if someday will ba an Ubuntu Server Edition.  It will be a great help for our servers, right now we are runing Hoary in Firewall, Web, and Mail Servers, but we need to turn off many desktop services and install server tools and apps.

Anyway, keep the good work!..........Ubuntu Rocks!

---

### Post by dataw0lf on 2005-05-16
There already is one, during installation of Hoary you should get a choice between installing the 'normal' Ubuntu (ie, desktop) or server version.

---

### Post by Ric_ on 2005-05-16
Hmmm, whilst Ubuntu is by far the best desktop distro I have ever used, I'm still very sceptical on servers that run X11. The way I see it is the more software you run the greater the chance of being r00t3d  :roll:  . So for now I'll stick with Ubuntu desktop and a Debian base install with jsut the packages I want on the server.

However If the community comes up with Network server edition simular to SuSe's Enterprise job that does domain logins and maybe even open exchange I'm in. In fact i'll start thinking about that one if anyone else fancies getting involved???

(btw I definately do not recomend inferior rpm based systems  [-X  )

---

### Post by az on 2005-05-16
If you install with the server option, you do not get X.

You get a 350 meg system.

---

### Post by JonahRowley on 2005-05-16
There is an Ubuntu server distro, it's called "Debian."  OK, so it's not Ubuntu, but most of Ubuntu's efforts are wasted on servers, so I don't see any real good reason to use it over Debian.  The Debian stable tree is a little old, upgrade to Debian testing and everything will work fine, you'll get the 2.6 kernel, etc.

Maybe someone would want to change my mind?  Why would I want to use Ubuntu on a server?

---

### Post by Burgundavia on 2005-05-16
Ubuntu server does not have X installed, as above.
Ubuntu is newer than sarge, as it is a stablised sid.

Those are facts, choose as you will.

Corey

---

### Post by az on 2005-05-16
Sarge is frozen and is being pushed out the door.  Once Sarge is supported, there is no reason that I can think of to use Ubuntu as a server.  Perhaps Breezy will include some really cool server stuff?

---

### Post by Ric_ on 2005-05-17
Nice to know about the server install but I'm sticking with Sarge (now going frozen) I've run it on production servers in a LAMP enviroment for months ;) (I like taking risks) And no probs.

My only suggestion was some easy kind of domain controller/exchangeserver like SuSe does. I think linux as a whole will benifit from these kind of products, it would be nice to keep ubuntu in there.

I'm not talking internet facing here only debian will do for me there ;)

---

### Post by stilus on 2005-05-17
I just installed ubuntu hoary with "server" at the boot (installation) prompt, installed ssh and nmap. Result:
```
sudo du -hs / 
372M /

```
```

nmap localhost 

Starting nmap 3.75 ( http://www.insecure.org/nmap/ ) at 2005-05-17 21:35 CEST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
22/tcp open  ssh
25/tcp open  smtp

```

looks pretty clean to me :)

Although I must say I found a link somewhere on these forums to [sme server](http://contribs.org/modules/news/), which at first glance (haven't tried it) looked tempting.  to me it seems a great example of a way for an ubuntu server to go. I would love to have a clear and simple (well documented), not to mention integrated webmin/ console interface for all kinds of server activities!

Just my 2 cents :)

---

### Post by nocturn on 2005-05-18
[QUOTE=JonahRowley]The Debian stable tree is a little old, upgrade to Debian testing and everything will work fine, you'll get the 2.6 kernel, etc.

Maybe someone would want to change my mind?  Why would I want to use Ubuntu on a server?[/QUOTE]

Because Debian stable is ancient (Try building a mailhost with proper spam/virus filtering or a webserver to support mambo or newer Bugzilla).

Ubuntu can help here, it takes the newer software from testing but adds security tracking.

I would never choose testing for a real server, specially when it will be internet connected.

---

### Post by nocturn on 2005-05-18
[QUOTE=azz]Sarge is frozen and is being pushed out the door.  Once Sarge is supported, there is no reason that I can think of to use Ubuntu as a server.  Perhaps Breezy will include some really cool server stuff?[/QUOTE]

It depends.  If you think Sarge will support the functions you need from your server for the next 3-5 years, it will do fine.
If you think you may need something like PHP5 or  something like that before that time is over, Ubuntu will serve you better.

---

### Post by LordHunter317 on 2005-05-18
[QUOTE=nocturn]I would never choose testing for a real server, specially when it will be internet connected.[/QUOTE]I would absolutely love to hear your reasoning for this.

---

### Post by syndicate on 2005-05-18
[QUOTE=LordHunter317]I would absolutely love to hear your reasoning for this.[/QUOTE]

I doubt there is any.

---

### Post by Finchwizard on 2005-05-18
Just a quick question I was wondering, I currently have a Debian server, and all seems to be running well, but the main thing is I can't figure out all the different Image Libraries, and I can't get a few of the Gallery things to work, even though I have Imagemagik installed etc, and NetPBM and few others.

Is there a list of Image Libraries out there that are the most commonly used?

I've got the Ubuntu server installing on a machine now for testing, so if I have the same problem, I'd like to know which ones are the best to have on there, anyone know?

Cheers.

---

### Post by nocturn on 2005-05-19
[QUOTE=LordHunter317]I would absolutely love to hear your reasoning for this.[/QUOTE]

Security tracking.  Stable gets this, unstable/testing does not.

---

### Post by nocturn on 2005-05-19
[QUOTE=syndicate]I doubt there is any.[/QUOTE]

Unstable/testing is called that for a reason.  It gets feature updates which might lead to breakage and it is not security tracked.  So for a production server, I would not use it.

Both reasons apply also to Breezy for now.

---

### Post by LordHunter317 on 2005-05-19
[QUOTE=nocturn]Security tracking. Stable gets this, unstable/testing does not.[/QUOTE]Actually, sarge is reciving security updates right now in preperation for the release.

And unoffical Debian policy has been to note in the advisories when the fixed package enters unstable and testing as part of the security advisory.  So while they do not get official updates, you can still pretty readily track them and handle them as well.

>  It gets feature updates which might lead to breakageSo do all distributions.  Debian however, with the right tools installed, makes it extremely easy to tell if an particular upgrade will break a box or not.

That's ignoring the fact that sid tends to be of higher quality than many other distributions to begin with.

---

### Post by nocturn on 2005-05-20
[QUOTE=LordHunter317]Actually, sarge is reciving security updates right now in preperation for the release.
[/quote]

That is correct, and I would not hesitate to use it now.  However, the next testing/unstable tree will have the same issue once Sarge is out.

> 
And unoffical Debian policy has been to note in the advisories when the fixed package enters unstable and testing as part of the security advisory.  So while they do not get official updates, you can still pretty readily track them and handle them as well.


I know that testing/unstable receives most fixes (as does Breezy), but for production server systems, I like to have that for sure.  And I like to have fixes only, without upgrading to newer versions (unless minor).

> 
So do all distributions.  Debian however, with the right tools installed, makes it extremely easy to tell if an particular upgrade will break a box or not.


Yes, you can check it.  But for a production system I like the approach of applying security fixes immediately, bugfixes within a reasonable time and do upgrades to newer versions in bulk, taking the server offline for a couple of hours when needed.

---

### Post by LordHunter317 on 2005-05-20
[quote=nocturn] And I like to have fixes only, without upgrading to newer versions (unless minor).[/quote]This is pretty silly reasoning to me.  Most security issues cause a new release.  Which means in order for the version not to change, a fix must be backported.  Which the distribution must do.

I'd much rather have the new upstream version with the patch wherever possible, as it's the version that's been blessed by the people writing the code.

> Yes, you can check it.Not "can", but "should always".  Even for security fixes.  High-availability sites run everything through test staging first, and with good cause.

---

### Post by mendicant on 2005-05-20
[QUOTE=LordHunter317]
I'd much rather have the new upstream version with the patch wherever possible, as it's the version that's been blessed by the people writing the code.
[/QUOTE]

But if the new version changes functionality, it could potentially be a pain for admins or users, who have to figure out what has changed and how to use it.  Some new releases change default behavior as well, which can also be unwanted (by users, or by distributors who want to see the old default behavior).  The only times I've seen this, I've been warned about it, but I can see how some admins might not want to see it, period.

---

### Post by nocturn on 2005-05-23
[QUOTE=LordHunter317]This is pretty silly reasoning to me.  Most security issues cause a new release.  Which means in order for the version not to change, a fix must be backported.  Which the distribution must do.

I'd much rather have the new upstream version with the patch wherever possible, as it's the version that's been blessed by the people writing the code.
[/quote]

If the new version has bugfixes only, your reasoning applies (like FireFox 1.03 -> 1.04).
Sometimes on a production server, you are running an older version of a program though (like Cyrus 2.0 instead of 2.1, making the upgrade something like 2.0.1 -> 2.1.2). 
The new version introduces new features, some of which are incompatible with the old one and require conversion of files etc (this specific Cyrus problem occured for me on Gentoo).

> 
Not "can", but "should always".  Even for security fixes.  High-availability sites run everything through test staging first, and with good cause.

I would love to do that, but my organisation provides neither the time nor the infrastructure to do this, as is the case in many smaller organisations.  The same goes at home, I had money for one server, not two and I don't have the time to test out each patch before applying.

I made it a habbit of always checking the content of patches to make sure what I'm installing.
If it is a security/bugfix only, they get installed.  Although I do maintain a rollback scenario (backups, old packages, ...).
Debian Stable or Ubuntu are quite helpfull in this situation while unstable and Gentoo are not.

---

### Post by LordHunter317 on 2005-05-23
[QUOTE=nocturn]Sometimes on a production server, you are running an older version of a program though (like Cyrus 2.0 instead of 2.1, making the upgrade something like 2.0.1 -> 2.1.2).[/quote]The number of times I've had unstable make an upstream shift like this and burn me has been zero.  It's rare they make a major change in the version of a package like that.

And even if you do, staying at the release you're on isn't terribly hard.  

> The new version introduces new features, some of which are incompatible with the old one and require conversion of files etc (this specific Cyrus problem occured for me on Gentoo).Debian usually provides migration solutions.  Least all the packages I've used I've had to do a migration with.

> Debian Stable or Ubuntu are quite helpfull in this situation while unstable and Gentoo are not.Seeing as the tools stable provides to track versions are the **exact same** as the ones unstable provides, you're wrong.

The only advantage stable has over unstable is security updates.  Which is important, I'll admit.  But there's a whole host of situations where you can deal with the fact that security updates generally enter unstable at the same time (and always in the same time frame) and run a more up-to-date system, as long as you know what tools to use and how to use them.

---

### Post by nocturn on 2005-05-24
[QUOTE=LordHunter317]
The only advantage stable has over unstable is security updates.  Which is important, I'll admit.  But there's a whole host of situations where you can deal with the fact that security updates generally enter unstable at the same time (and always in the same time frame) and run a more up-to-date system, as long as you know what tools to use and how to use them.[/QUOTE]

That's what I'm talking about.  For a production system, I only want those.
I can get them in unstable by tracking vuln. on the net and manually applying what I need.  But the point remains that stable handles this better (aptitude update && aptitude upgrade pulls in security and well tested bugfixes only).

Yes you can run a secure unstable system, the same applies to things like Gentoo, but it takes a lot more testing and work, so you need the time and the infrastructure to do it which is a luxury many people don't have.

Ubuntu fills a lot of this gap.  It offers more up to date packages then stable does  and has security tracking.
If there was a way to upgrade from older releases (5.04 -> 6.04) without intermeddiate versions, it would be even better.

---

### Post by nocturn on 2005-05-24
[QUOTE=LordHunter317]
Debian usually provides migration solutions.  Least all the packages I've used I've had to do a migration with.
[/QUOTE]

That's a good thing, but it requires manual intervention anyway.  Which I do not want to do regulary on a server.

I want to install patches as soon as possible when they come out (takes 10 minutes), while doing such upgrades/migrations on scheduled maintenance when I have set the time aside.

---

### Post by LordHunter317 on 2005-05-24
[QUOTE=nocturn]Yes you can run a secure unstable system, the same applies to things like Gentoo, but it takes a lot more testing and work, so you need the time and the infrastructure to do it which is a luxury many people don't have.[/quote]The point is though, you're always supposed to have that infrastructure, so this is irrelevant.  It's technically a strawman.

I understand that a lot of places can't afford to have such infrastructure, but it doesn't change the fact you should.  And I also understand that if you don't have it, the slow of rate changes in stable is valuable.

As an aside, I think Debian should stop doing formal releases and just become a rolling distribution, and provided security updates for all "releases" (i.e., unstable, testing, whatever).

---

### Post by ejms07 on 2005-05-26
Thanks to you all guys.....you all Rock!

My question was answered in the first reply because I missed the server choice during installation startup.  Nevertheless I agree with most of you regarding debian and desktop issues, as I started to use the Ubuntu's server installation I'm not using any desktop at all.  I'm using all Ubuntu's repository sections to get the most updated packages and none of our servers gave me any conflicts or errors.

---

### Post by nocturn on 2005-05-27
[QUOTE=LordHunter317]The point is though, you're always supposed to have that infrastructure, so this is irrelevant.  It's technically a strawman.

I understand that a lot of places can't afford to have such infrastructure, but it doesn't change the fact you should.  And I also understand that if you don't have it, the slow of rate changes in stable is valuable.
[/quote]

It's a big plus if you have that option, but technically, the most important thing is to apply security patches as quickly as possible (without trashing the machine, so backups are your friend).

I worked in some pretty different enviroments (a major multinational, a rather small Unix consulting firm and now a medium sized public research facility).
None of these provided infrastructure to test patches...

Even if I had that option, I still prefer to only have to test out security patches on a regular basis and do feature upgrades on scheduled maintenance.

> 
As an aside, I think Debian should stop doing formal releases and just become a rolling distribution, and provided security updates for all "releases" (i.e., unstable, testing, whatever).

I personally would like to use Debian Stable for servers,  but only if they would provide a stable release yearly. 
Adding security tracking to testing would be nice for many people though.

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=nocturn]but technically, the most important thing is to apply security patches as quickly as possible[/quote]That's simply not true though.  Enterprise doesn't circumvent their testing and pre-production stages with security patches.

I'm sure sometimes they'd like to be able to, but they get tested like every other patch to production.  I don't buy that reasoning as valid nor that desire as valid (though I understand why would want it to be).

> None of these provided infrastructure to test patches...They're not truely enterprise (in the sense I mean) then.  I'm talking people like Amazon, where an outage of a webserver starts costing large dollar values quickly.

> Even if I had that option, I still prefer to only have to test out security patches on a regular basis and do feature upgrades on scheduled maintenance.When you're testing, everything becomes more or less the same.  

> I personally would like to use Debian Stable for servers,  but only if they would provide a stable release yearly. Why?   Just to be up-to-date?  As long as the software is secure and meeting your needs, you don't ever have to upgrade.

---

