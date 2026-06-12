---
title: "What do you want in Kubuntu?"
date: 2007-07-13
forum: The Cafe
---

### Post by bread eyes on 2007-07-13
I'm probably not going to have anything to do for a while so I might make a distro. So I need to know what isn't easy (for most:)) to do in Kubuntu. What should be added? What should be removed? suggest away.

what isn't super easy:
[LIST=1]
[*] Kernel management/building
[/LIST]

What should be added:
[LIST=1]
[*] Smart Package Manager
[*] Peazip
[*] D3lphin
[*] KDE4
[*] add/remove-software-before-install-program (to be made?)
[/LIST]

What should be removed:
[LIST=1]
[*] Adept
[*] APT
[*] ark
[*] Konqueror
[/LIST]

---

### Post by misfitpierce on 2007-07-13
Firefox is in kubuntu I believe....Believe it has firefox and konqueror

---

### Post by bread eyes on 2007-07-13
> **misfitpierce said:**
> Firefox is in kubuntu I believe....Believe it has firefox and konqueror

okay

---

### Post by Quillz on 2007-07-13
Why should Konqueror be removed?

---

### Post by bread eyes on 2007-07-13
> **Quillz said:**
> Why should Konqueror be removed?

Most people seem to only use it as a file browser and complain about it being a file and web browser (kind of strange really). This solves the problem.

---

### Post by FuturePilot on 2007-07-13
+1 for removing Adept and Konqueror

---

### Post by user1397 on 2007-07-13
I believe dolphin is the new file manager for gutsy...just thought you should know!

---

### Post by Jucato on 2007-07-13
1. KDE4

Depends on what you mean by "super easy". KDE 4 is still in alpha, and the KDE 4 packages released by Kubuntu are meant for testing and development. Of course, there might be problems along the road, but that's the usual disclaimer that comes with alpha software.

2. Kernel management/building

I can't understand how this affects Kubuntu. The same packaging and building tools available to Ubuntu are also available to Kubuntu, specially command line tools.

3. Smart Package Manager and Peazip

I'm not sure about the Status of Smart PM using APT as backend. Anyway, I think it's possible to file a wishlist with the MOTU guys (the ones packaging software for Universe and Multiverse).

4. Dolphin

There already is, version 0.8.2 if I remember. Actually it's not worth trying Dolphin on KDE 3.5.x right now, since that version is so different, old, and broken compared to the real Dolphin on KDE 4. Best to either wait for the real Dolphin, or build KDE 4 from wherever is most convenient for you.

5. Adept

Good luck with that. Unless you can offer an actively maintained, KDE-compatible, GUI package manager, I'm afraid we'll all be stuck with Adept.

6. APT

Are you serious? APT and dpkg form the packaging backbone of any Debian-based system.

7. ark

Unfortunately, what other feasible alternatives are there?

8. Konqueror

No can do. First, it is *the* file manager of KDE. You can't remove it without putting in something else. And no, Dolphin is *not* an option on KDE 3.5.x. Second, Kubuntu is committed to using KDE as much as possible, hence Firefox is not installed by default (And we are moving towards KOffice by default in KOffice 2). Oh, and those distributions that ship with Firefox? They still use Konqueror as the default web browser. Firefox is just installed. :)

Anyway, you're free to do what you want with Kubuntu. But we're talking about defaults here. If you hate Konqueror as a web browser, install and use Firefox. But it's the file manager, and can't be removed without a replacement. If you don't like Adept, use KPackage, or Smart PM (if it works well with APT now). Same with Ark. But unless there are better, actively maintained, KDE apps there to replace these things, I doubt it would be changed anytime soon.

> I believe dolphin is the new file manager for gutsy...just thought you should know!
Err.. no. 
Dolphin will be the default file manager for KDE 4. KDE 4 won't be the default in Kubuntu until Kubuntu 8.10. for Kubuntu 7.10 (Gutsy) and 8.04 (another LTS release), KDE 4 packages will be released separately, in a separate repository.

---

### Post by bread eyes on 2007-07-13
> **ubuntuman001 said:**
> I believe dolphin is the new file manager for gutsy...just thought you should know!

I'm not sure what that has to do with this but okay.

---

### Post by bread eyes on 2007-07-13
> 1. KDE4

Depends on what you mean by "super easy". KDE 4 is still in alpha, and the KDE 4 packages released by Kubuntu are meant for testing and development. Of course, there might be problems along the road, but that's the usual disclaimer that comes with alpha software.

It's out of date.

> 2. Kernel management/building

I can't understand how this affects Kubuntu. The same packaging and building tools available to Ubuntu are also available to Kubuntu, specially command line tools.

I was think more along the lines of programing new stuff.

> 3. Smart Package Manager and Peazip

I'm not sure about the Status of Smart PM using APT as backend. Anyway, I think it's possible to file a wishlist with the MOTU guys (the ones packaging software for Universe and Multiverse).

It uses dpkg as a backend

> 4. Dolphin

There already is, version 0.8.2 if I remember. Actually it's not worth trying Dolphin on KDE 3.5.x right now, since that version is so different, old, and broken compared to the real Dolphin on KDE 4. Best to either wait for the real Dolphin, or build KDE 4 from wherever is most convenient for you.

I don't understand where the problem is.

> 5. Adept

Good luck with that. Unless you can offer an actively maintained, KDE-compatible, GUI package manager, I'm afraid we'll all be stuck with Adept.

Smart will be just fine for what I'm doing.

> 6. APT

Are you serious? APT and dpkg form the packaging backbone of any Debian-based system.

You don't *need* APT.

> 
7. ark

Unfortunately, what other feasible alternatives are there?


Peazip

> 8. Konqueror

No can do. First, it is *the* file manager of KDE. You can't remove it without putting in something else. And no, Dolphin is *not* an option on KDE 3.5.x. Second, Kubuntu is committed to using KDE as much as possible, hence Firefox is not installed by default (And we are moving towards KOffice by default in KOffice 2). Oh, and those distributions that ship with Firefox? They still use Konqueror as the default web browser. Firefox is just installed. :)

You don't *need* Konqueror.

> And no, Dolphin is *not* an option on KDE 3.5.x.

I'm pretty sure it is.

> Anyway, you're free to do what you want with Kubuntu. But we're talking about defaults here. If you hate Konqueror as a web browser, install and use Firefox. But it's the file manager, and can't be removed without a replacement. If you don't like Adept, use KPackage, or Smart PM (if it works well with APT now). Same with Ark. But unless there are better, actively maintained, KDE apps there to replace these things, I doubt it would be changed anytime soon.


I think you need to read what I said more closely.

---

### Post by user1397 on 2007-07-13
> **Jucato said:**
> 

Err.. no. 
Dolphin will be the default file manager for KDE 4. KDE 4 won't be the default in Kubuntu until Kubuntu 8.10. for Kubuntu 7.10 (Gutsy) and 8.04 (another LTS release), KDE 4 packages will be released separately, in a separate repository.Hmmm..I just thought so, because I recently upgraded to gutsy gibbon for testing purposes, and dolphin was installed by default, although konqueror is still there of course.

---

### Post by user1397 on 2007-07-13
> **bread eyes said:**
> I'm not sure what that has to do with this but okay.that's why I said "just thought you should know"

I thought maybe you would want kubuntu gutsy as a base of sorts for your new distro...

---

### Post by Jucato on 2007-07-13
It's your distro, so its your call. Just pointing out why things are the way they are on Kubuntu.

Not sure about Smart PM details, since I'm not so familiar with it. If you say that you can have a Debian-based distro without APT (op Aptitude), I'll give you the benefit of the doubt. :)

There's an ongoing discussion about providing Dolphin as the default in Gusty, using the 3rd party D3lphin. However, nothing's final. IMHO, Dolphin 0.8.2 and lower (the only versions available for KDE 3.x) is not polished enough to be used as a default file manager. (Of course, if you're OK with it, no problems there).

Again, good luck with your project. :guitar:

---

### Post by bread eyes on 2007-07-13
> **ubuntuman001 said:**
> that's why I said "just thought you should know"

I thought maybe you would want kubuntu gutsy as a base of sorts for your new distro...

I probably will later.

---

### Post by deepclutch on 2007-07-13
Gnome?I'm sorry but cant stop asking!

---

### Post by sparks0548 on 2007-07-13
How about during the installation offering a advanced or typical installation selection screen.  Allowing those users to select the packages they want to install from the KDE selection list instead of installing everything and cluttering the K menu.  My perspective I would like to have th option at install/build time to choose what I want to install rather than getting inundated with applications that I probably won't touch.

Best of luck with your development.

---

### Post by EdThaSlayer on 2007-07-13
If possible I would like KDE4(even though it isn't easy, it is the #1 objective) since I heard that a lot of things are fixed then(bloat is gone).

---

### Post by Kingsley on 2007-07-13
Kubuntu would be much sweeter if the software in K-menu had a better layout. I'm talking about sub-menus in each menu. For example, Multimedia should be divided into sound and video. PCLinuxOS accurately features what I mean.

---

### Post by Hobbsee on 2007-07-13
I'd suggest you get involved in the current kubuntu, rather than making a subdistro, from that...

---

### Post by awakatanka on 2007-07-13
Dolphin hasn't have embedded viewers, hasn't have tree view, hasn't have tab view, and hasn't have a lot of options konqueror has. **yet**

It looks you try to make a Knome. :lolflag:

---

### Post by SlayerMan on 2007-07-13
I want kubuntu to have the following:

1. The same automatic codec search / restricted drivers manager / X screen setup (available in Gutsy) that the GNOME-variant of Ubuntu has
2. More development on the package management side, i.e. boost Adept development or replace it with something better (e.g. a statically linked Synaptic)
3. A speedier KDE desktop. Look at openSuSE, KDE is whoppingly fast there

---

### Post by LuisAugusto on 2007-07-13
Kubuntu needs:

-A new icon theme (Everaldos crystal icons or Oxygen will be nice)
-A new theme
-A package manager (Adept Sucks)
-Make KDE a little faster
-I want my KDE apps to start whit the first click :P
-A nice update-manager (again, Adept Sucks)
-Easy codecs and restricted drivers manager (I don't need them, but a lot of people do)
-KDE 4 (there's going to be an alternative CD, I think that's stupid, almost every KDE user will go whit KDE 4, and GNOME interested users won't go for KDE 3), or at least make it available in default repositories.
-A nice Add/remove (well, you know), for newbies.
-This is for both, Ubuntu and Kubuntu, (K)Network-manager doesn't work whit WEP so I'm stuck whit wlassistant.
-Dolphin; Is it true that Dolphin (or D3lphin) will be the Default file manager? Sweet (it's soooo fast).  
-So, if dolphin/d3lphin is the file manager, make the Kubuntu profile better for web browsing tasks.
-Did I mention that Adept sucks?

See you later.

---

### Post by Jucato on 2007-07-13
> **awakatanka said:**
> Dolphin hasn't have embedded viewers, hasn't have tree view, hasn't have tab view, and hasn't have a lot of options konqueror has. **yet**

It already has a tree view. It has an embedded konsole. It has some other panels that Konqueror doesn't have.

But it will not have embedded viewers, tabs, and "a lot of options konqueror has". Dolphin is not Konqueror. :)

...

Oh, and hi Hobbsee!

LuisAugusto:
> - A new icon theme
KDE 4
> - I want my KDE apps to start whit the first click :P
Huh?
> - A nice Add/remove (well, you know), for newbies.
Already there. Adept Installer. It's practically the same interface as the Add/Remove Programs in Ubuntu
> -Did I mention that Adept sucks?
So Adept has its problems (I somewhat agree). Again, I wonder if anyone has really offered an alternative. The criteria are: actively maintained, uses APT or Aptitude as backend, KDE-based (or PyKDE if you want) (of course it shouldn't suck as much). I can't really seen any feasible alternative for now (other than KPackage).
> -KDE 4 (there's going to be an alternative CD, I think that's stupid, almost every KDE user will go whit KDE 4, and GNOME interested users won't go for KDE 3), or at least make it available in default repositories.
Most likely it will be in the repositories, either kubuntu.org or ubuntu.com.
Why we won't be having KDE 4 by default on Gutsy: Gutsy is scheduled to be released on October. So is KDE 4.0. But
1. There's no guarantee that KDE 4.0 will be released on October. Gutsy will.
2. Even if KDE 4.0 were to be released on October, it would still be close to impossible to have it included in the release in time. We have things that we call "freeze", where you stop adding new features in order to maintain stability before releasing. 
3. KDE 4.0 will be great. But it's expected to have some very rough edges. (This is the same reason we can't put it in the next LTS release, which should be 8.04)

Given those factors, we actually have very little choice but to *not* ship Gutsy with KDE 4.0 by default.

---

### Post by LuisAugusto on 2007-07-13
> **Jucato said:**
> Huh?

Some times in Kubuntu applications don't launch.

> **Jucato said:**
> Already there. Adept Installer. It's practically the same interface as the Add/Remove Programs in Ubuntu

I said a nice add/remove, I know there's one, but it doesn't show applications added of non-official repositories, Ubuntu Add/remove does.

> **Jucato said:**
> So Adept has its problems (I somewhat agree). Again, I wonder if anyone has really offered an alternative. The criteria are: actively maintained, uses APT or Aptitude as backend, KDE-based (or PyKDE if you want) (of course it shouldn't suck as much). I can't really seen any feasible alternative for now (other than KPackage).

Most Adepts problems come from it's ridiculously interface:

-Empty Screen saying: "Welcome to Adept Update Manager"... 
-Expand tree on Adept to see Package Description" 
-Ridiculous amount of filters
-And one or two simple features; force version for example. 
-Well, you got my point

> **Jucato said:**
> 
1. There's no guarantee that KDE 4.0 will be released on October. Gutsy will.
Delay Kubuntu one month isn't that hard 
> **Jucato said:**
> 2. Even if KDE 4.0 were to be released on October, it would still be close to impossible to have it included in the release in time. We have things that we call "freeze", where you stop adding new features in order to maintain stability before releasing. 
I know about freezing, but KDE 4 has "freezing" too, so last month of KDE 4.0 development will be bug fixing, you could start KDE 4 implementation on BETA releases and continue whit RC.
> **Jucato said:**
> 3. KDE 4.0 will be great. But it's expected to have some very rough edges. (This is the same reason we can't put it in the next LTS release, which should be 8.04)
This is true, but I don't think it will be that bad. (and about LTS, 90% of Kubuntu users don't care, but well, I got the point)

When Kubuntu KDE 4 Alternative CD: Non maintained; Non Official; Non recommend for end-users get the 80% of Kubuntu downloads don't come crying :lolflag:

---

### Post by Jucato on 2007-07-13
> **LuisAugusto said:**
> Some times in Kubuntu applications don't launch.
The only time this happens to me is with Firefox launched through Katapult (a behavior I can reproduce on Gentoo). All other apps, launched through the menu or katapult, start fine.

> I said a nice add/remove, I know there's one, but it doesn't show applications added of non-official repositories, Ubuntu Add/remove does.

I will have to check once I get back to my Kubuntu. If it is indeed a bug, have you tried filing a report?

> -Empty Screen saying: "Welcome to Adept Update Manager"... 
Going to disappear in Gutsy, afaik.

> -Expand tree on Adept to see Package Description"
You only need to do this to see the long description. The short description is available at first glance.

> -Ridiculous amount of filters
-And one or two simple features; force version for example. 
-Well, you got my point


I never said Adept didn't have problems. I did say that there isn't any other feasible alternative. The good news is that Adept is actively maintained and can change. We just need people willing to do something (other than state the obvious :P).

> Delay Kubuntu one month isn't that hard
It is, considering it's not just Kubuntu, but Ubuntu and Xubuntu and Edubuntu as well. Although we want it to, the world doesn't revolve around KDE unfortunately. :(

> I know about freezing, but KDE 4 has "freezing" too, so last month of KDE 4.0 development will be bug fixing, you could start KDE 4 implementation on BETA releases and continue whit RC.
*Our* freeze means that the version that will be included is stable enough. Taking into consideration Kubuntu's and KDE's schedules, Kubuntu's Feature Freeze will be 4 days before KDE's beta tagging. It just won't be possible given that scenario. We also have to take into account that Alpha 2 was delayed. We are not certain how much more delays there will be.

[https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)
[http://techbase.kde.org/Schedules/KDE4/4.0_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.0_Release_Schedule)

> When Kubuntu KDE 4 Alternative CD: Non maintained; Non Official; Non recommend for end-users get the 80% of Kubuntu downloads don't come crying :lolflag:

It will be official. Kubuntu.org repositories are official **Kubuntu** packages. Who do you think makes those packages anyway? :)

---

### Post by LuisAugusto on 2007-07-13
> **Jucato said:**
> The only time this happens to me is with Firefox launched through Katapult (a behavior I can reproduce on Gentoo). All other apps, launched through the menu or katapult, start fine.

It happens to me sometimes (but, of course no like in dapper!).

> **Jucato said:**
> I will have to check once I get back to my Kubuntu. If it is indeed a bug, have you tried filing a report?

No, I thought it was on purpose, lol. 


> **Jucato said:**
> Going to disappear in Gutsy, afaik.

Thanks god.


> **Jucato said:**
> You only need to do this to see the long description. The short description is available at first glance.

The short description is often, well, too short.

> **Jucato said:**
> I never said Adept didn't have problems. I did say that there isn't any other feasible alternative. The good news is that Adept is actively maintained and can change. We just need people willing to do something (other than state the obvious :P).

As soon as I start learning code at a decent level (one more year) you can bet I'll help

> **Jucato said:**
> It is, considering it's not just Kubuntu, but Ubuntu and Xubuntu and Edubuntu as well. Although we want it to, the world doesn't revolve around KDE unfortunately. :(

I don't see any problem there, Ubuntu, Xubuntu, Edubuntu dosen't have to be delay. Just the KDE version, but well, you probably know better the situation than my self.

> **Jucato said:**
> *Our* freeze means that the version that will be included is stable enough. Taking into consideration Kubuntu's and KDE's schedules, Kubuntu's Feature Freeze will be 4 days before KDE's beta tagging. It just won't be possible given that scenario. We also have to take into account that Alpha 2 was delayed. We are not certain how much more delays there will be.

Alpha 2 wasn't delayed, was it? They made the announcement late, but it was on svn on time (anyway, the delayed couldn't be more than a week)

> **Jucato said:**
> It will be official. Kubuntu.org repositories are official **Kubuntu** packages. Who do you think makes those packages anyway? :)

As far I remember, I read that Kubuntu KDE 4 wouldn't be official, and that KDE 4 repositories weren't be by default, and that won't be hosted in kubuntu servers, maybe I misunderstood it, 
Treviño package them I guess :P (kidding of course).

I understand your points, it's just I think is making double work, most people will be using KDE 4 version, and it won't be polish, you'd probably will just put the KDE 4.0 RC 2 in the CD and done! (I hope am wrong), not because you're lazy, no, because you already have a lot of work (as far as I know, there aren't much Kubuntu contributors) so I think is better to invest the effort for what will be most use.

---

### Post by Jucato on 2007-07-13
> **LuisAugusto said:**
> The short description is often, well, too short.
Blame Debian.

> I don't see any problem there, Ubuntu, Xubuntu, Edubuntu dosen't have to be delay.
The problem there is that these four are to be released simultaneously. You'll have to take it up with the higher-ups if you have issues with it. :)

> Alpha 2 wasn't delayed, was it?

It was. Originally, there was no Alpha 2, and Beta 1 was supposed to be tagged June 25. Instead, Alpha 2 was put up and Beta 1 is delayed by a month. Of course, the Alpha 2 release announcement came later than the actual tagging itself.

> As far I remember, I read that Kubuntu KDE 4 wouldn't be official
They are official, as far as Kubuntu is concerned.

> and that KDE 4 repositories weren't be by default
Of course not. Otherwise, if they were there by default, then we'd have KDE 4 by default.

> and that won't be hosted in kubuntu servers, maybe I misunderstood it.
Where else would they be put up? Official Kubuntu packages, made by Kubuntu packagers/developers, will always be hosted in either kubuntu.org or ubuntu.com.

> Treviño package them I guess :P (kidding of course).
You should be. :P

> I understand your points, it's just I think is making double work
Aren't you glad you're not the one doing the double work? :D

> most people will be using KDE 4 version, and it won't be polish, you'd probably will just put the KDE 4.0 RC 2 in the CD and done! (I hope am wrong), not because you're lazy, no, because you already have a lot of work (as far as I know, there aren't much Kubuntu contributors) so I think is better to invest the effort for what will be most use.

Nope. A lot will still be using stable versions, as needed. Some will wait and see. And (presuming we will have KDE 4 CD images) what will be the point in releasing separate images/packages if we're just going to put an RC?

Final thoughts: There's a lot more to releasing a distro than just putting in the latest and greatest. There's a lot of factors to consider. Of course, the developers want you to be able to experience KDE 4 as soon as it is ready, that's why we have to make compromises. At this point in time, considering all the factors, it has been decided that it will not be beneficial to ship Kubuntu 7.10 with KDE 4 by default. If that should change before the release, then good. If not, you have been informed. :)

---

### Post by LuisAugusto on 2007-07-13
> **Jucato said:**
> 
It was. Originally, there was no Alpha 2, and Beta 1 was supposed to be tagged June 25. Instead, Alpha 2 was put up and Beta 1 is delayed by a month. Of course, the Alpha 2 release announcement came later than the actual tagging itself.
Nothing was delayed, Beta 1 became Alpha 2, one more alpha, one less beta, no schedules changes. And it was like one and a half week between the update on svn and the announcement on dot.


> **Jucato said:**
> Of course not. Otherwise, if they were there by default, then we'd have KDE 4 by default.

Huh? You can have both KDE 3 and 4.0 on the repositories.


> **Jucato said:**
> pe. A lot will still be using stable versions, as needed. Some will wait and see. And (presuming we will have KDE 4 CD images) what will be the point in releasing separate images/packages if we're just going to put an RC?
Between RC 2 and Final Release there's just one week.

See you later.

---

### Post by bread eyes on 2007-07-13
> **Hobbsee said:**
> I'd suggest you get involved in the current kubuntu, rather than making a subdistro, from that...

There wouldn't be a point, it's going to end up very different from kubuntu anyway. At the moment I'm just trying to fix some stuff that people don't like in the default. BTW, would someone compile KDE4 for me? My computer isn't very fast.

---

### Post by bread eyes on 2007-07-13
> **ubuntuman001 said:**
> that's why I said "just thought you should know"

I thought maybe you would want kubuntu gutsy as a base of sorts for your new distro...

Actually now that I think about it, it's probably not going to be interesting till awhile after gutsy so I guess I might as well base it on it now.

Edit: Actually, nvm, I'll just piggy-back stepan2's distro.

---

### Post by Arathorn on 2007-07-13
> **Jucato said:**
> 3. KDE 4.0 will be great. But it's expected to have some very rough edges. (This is the same reason we can't put it in the next LTS release, which should be 8.04)
Has Gutsy + 1 been confirmed as LTS? Because last time I heard (which was quite some time ago already) it wasn't going to be. LTS or not, it's too early to judge how KDE 4 looks when Gutsy + 1 is due. Besides, despite Dapper being a LTS release, it's the (K)ubuntu that gave me most trouble of all.
@bread eyes: I doubt people want to see yet another (Ubuntu derivative) distro.

---

### Post by bread eyes on 2007-07-13
> **Arathorn said:**
> @bread eyes: I doubt people want to see yet another (Ubuntu derivative) distro.

It's going yet another distro but its (eventually) not going to be an insignificant Ubuntu clone with different defaults, this is just the short term.

---

### Post by Jucato on 2007-07-13
> **LuisAugusto said:**
> Nothing was delayed, Beta 1 became Alpha 2, one more alpha, one less beta, no schedules changes.
If you want to see it that way. But consider this. The original plan was to tag a beta quality KDE 4 on that day. Instead, an alpha quality release was tagged. In the end, releasing the first beta was delayed.

> Huh? You can have both KDE 3 and 4.0 on the repositories.
Not if there are going to be clashes with naming. The only reason why KDE 3 and KDE 4 can exist now on the same system and repository is because KDE 4 is packaged to have different names, to install in a different location from KDE 3. Once KDE 4 goes stable, KDE 4 will/should be installed in the default system locations. It will still depend on the distribution how to implement it in the end. 

> Between RC 2 and Final Release there's just one week.
So? They still have to test, package, test, re-package, etc. to make sure that everything will be working fine, lest they start to be called lazy by simply dumping an RC into a CD. Not to mention that, if KDE sticks to its release schedule faithfully, this will all happen during a time where everybody's busy working on Gutsy. 

[QUOTE=Arathorn]Has Gutsy + 1 been confirmed as LTS? Because last time I heard (which was quite some time ago already) it wasn't going to be. LTS or not, it's too early to judge how KDE 4 looks when Gutsy + 1 is due.[/QUOTE]

Confirmed through interviews with some developers, notably Jonathan Riddell. It just can't be officially announced yet until after Gutsy has been released. They are also not keen on putting KDE 4, whether it be 4.0 or 4.1 on an LTS just yet.

I should stop replying... I'm supposed to be on "vacation"... :(

---

### Post by bread eyes on 2007-07-13
> **Jucato said:**
> I should stop replying... I'm supposed to be on "vacation"... :(

I've always found that to be a funny problem.:)

---

### Post by Hobbsee on 2007-07-14
> **bread eyes said:**
> There wouldn't be a point, it's going to end up very different from kubuntu anyway. At the moment I'm just trying to fix some stuff that people don't like in the default. BTW, would someone compile KDE4 for me? My computer isn't very fast.

As you wish.  I hope you have the time to maintain it indefinetly.  Patches welcome, at least.

And no, i dont think most people will offer you their computer power

---

### Post by MeteoriK on 2007-10-24
What's all this talk about getting rid of konqueror?  It's a great web browser, and KHTML has long had a cleaner code base than gecko.  It's fast, it's got great keyboard controls, it looks tidier than firefox, and it's way smaller than firefox.  It's been my main browser for about 5 years now.

I'm not about to start a "konqueror versus firefox" flame war, but firefox has always been an option for those who want it, meanwhile konqueror is /the/ KDE browser and integrates far better with other kde apps (embedding, for instance).

---

