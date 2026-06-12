---
title: "Epiphany/Web 3.8 Available for Ubuntu Gnome?"
date: 2013-03-26
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2013-03-26
Is Epiphany/Web 3.8 available to those of us who have updated an Ubuntu Gnome daily install to Gnome 3.7.92 from the Gnome3 and Gnome3-staging PPA's?

I know the source is available, but a package is obviously preferable.

Thanks.

---

### Post by Flywaver on 2013-03-27
Same here...just upgraded to gnome 3.8 with the gnome3 staging PPA and checked this PPA and the regular gnome3 team PPA and can't find web 3.8 :(

---

### Post by RavisPohan on 2013-03-29
I'd be keen to see a package for Web 3.8 as well. I seem to remember it also being a bit of a late-comer in the past, though.

---

### Post by Stinger on 2013-03-29
Although Firefox is now the default browser, Epiphany/Web 3.8 is a **'need to have'** for a Gnome enthusiast as myself and used to be part of the Ubuntu Gnome Remix, like PackageKit used to be part of the Ubuntu Gnome Remix.
Just because Ubuntu Gnome now uses different default software it doesn't mean that I don't want to use Web and PackageKit with the new Gnome 3.8

So, to the Ubuntu GNOME team: " Please let us have the possibility to choose" , don't 'cripple' the complete Gnome 3.8 experience

---

### Post by jbicha on 2013-03-29
> **Stinger said:**
> So, to the Ubuntu GNOME team: " Please let us have the possibility to choose" , don't 'cripple' the complete Gnome 3.8 experience

Uh, I haven't personally packaged the new WebKit and Epiphany yet because WebKit takes a long time (and a lot of hard drive space) to build and the cost/benefit ratio wasn't worth it to me when there were a lot of other things that needed to be done. I'd love to see the new versions too and now that Debian has packaged them it's easier for Ubuntu to get them too.

I think many people got involved in open source because they saw something that wasn't being done and stepped up to get it done. The Ubuntu GNOME team could use help with packaging, identifying bug fixes, and more.

---

### Post by Stinger on 2013-03-30
@jbicha
"Houston we have a problem" ;)

**Gnome 3.8 is not official** and only available in the Gnome3 ppa, so therefore, as I understand it, **bugs cannot be reported using launchpad** but has to be reported directly to the [GNOME3 Team]("https://launchpad.net/~gnome3-team"), right ?
Would I have to report on their mailing list ? Because that would involve me applying for membership and as you know, I'm more a pain in the a.. than I'm a developer :biggrin: , only team members can post on the mailing list. 
Another solution could be to report to the teams admins but I don't know how they feel about being spammed with requests and bug reports ?

A little of topic but still.. [My GDM bug]("http://ubuntuforums.org/showthread.php?t=2125539&p=12558547#post12558547") seems to be present on the [Ubuntu Gnome mailing list here by Fran Dieguez]("https://lists.ubuntu.com/archives/ubuntu-gnome/2013-March/000101.html")
Is this the way to report a bug regardig Gnome 3.8 ? I thought this mailing list was for the official Ubuntu GNOME ( Gnome 3.6 ) ?

Complete confusion on where to report what and how ? Thats why I choose to use the forum instead but the messages seems to drown in the masses and are easily overlooked :(

I'm not talented when it comes to packaging but maybe I could learn if guided ? but I can  "identifying bug fixes, and more." if you show me where and what to do ;)

Regards 
Stinger

Ps.
Would it be possible for you, the Ubuntu GNOME team, to create your own forum ? 
It could have Bug and Request sub forums etc.
I think Ubuntu GNOME could benefit a lot from having a dedicated forum.
> The community is the most important asset of a distribution. It provides feedback, ideas, promotion, support, bug reports, artwork, motivation, it's the living heart of any open-source project. In my opinion you need both clear leadership and good communication with the community.
Guess who said that ( no, not Mark S ;) ) It's taken from [here]("http://www.muktware.com/5356/clement-lefebvre-mir-irrelevant-linux-mint")

---

### Post by mc4man on 2013-03-30
> **Stinger said:**
> 
**Gnome 3.8 is not official** and only available in the Gnome3 ppa, so therefore, as I understand it, **bugs cannot be reported using launchpad** but has to be reported directly to the [GNOME3 Team]("https://launchpad.net/~gnome3-team"), right ?

Don't use the Gnome3 ppa here but it states on the ppa page - 
> === Bugs ===
On Raring (13.04) please use 'ubuntu-bug' to report bugs against packages in this PPA



Edit: - gave it a try on a test install I'm dumping, accepts bugs on Gnome3 ppa package(s)

---

### Post by Stinger on 2013-03-31
@mc4man
Strange... I didn't see that before, my bad if it has been there all along.
Thanks for pointing it out :) Makes bug reporting for Gnome 3.8 much easier.
But I'm afraid it does not solve the situation regarding Epiphany/Web 3.8 request ( or packagekit for that matter, personally I think all of Gnome 3.8 should be available, but I know we must accept the developers decisions, they have their reasons )

I know Jeremy has been struggling with Web before in Quantal, it's not an easy task, but I can see that some progress has been made for getting Gnome 3.8 ready [here]("https://launchpad.net/~jbicha/+archive/dev"), [here]("https://launchpad.net/~ricotz/+archive/testing?field.series_filter=raring") and at the [staging ppa]("https://launchpad.net/~gnome3-team/+archive/gnome3-staging")

so I don't think it would take too long before all the peaces are put together in a working Gnome 3.8 and if we are lucky no peaces are missing ;)

Update: [GDM bug reported]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466")

---

### Post by jbicha on 2013-04-02
GNOME Web (Epiphany) 3.7.91 is available in the GNOME3 PPA now. It took several days to get the new WebKit to build on the Ubuntu PPAs. I don't plan on working on a newer WebKit any time soon (which is a pre-requisite to get a newer version of GNOME Web) but I may take a look once Debian gets around to packaging it. You'll need to install epiphany-browser-webkit2 if you want the brand new WebKit2 version; otherwise, epiphany-browser offers the more thoroughly tested WebKit version.

---

### Post by buzzingrobot on 2013-04-02
> **jbicha said:**
> GNOME Web (Epiphany) 3.7.91 is available in the GNOME3 PPA now.

Thanks much for taking the time to build it.  I installed the webkit2 version a few hours ago and so far, so good. 

Been using Ubuntu Gnome 13.04 since the iso's were available.  Moved over from Fedora 18.  That's really good.  This is better.  On 3.6, I had only one apport alert, from Rhythmbox.  I've had a few more with 3.8, especially from Network Manager, but fewer than I'd expect from an unreleased version of Ubuntu running a mix of Gnome 3.8 and 3.7.9-whatever.

---

### Post by Stinger on 2013-04-02
> **jbicha said:**
> GNOME Web (Epiphany) 3.7.91 is available in the GNOME3 PPA now. It took several days to get the new WebKit to build on the Ubuntu PPAs. I don't plan on working on a newer WebKit any time soon (which is a pre-requisite to get a newer version of GNOME Web) but I may take a look once Debian gets around to packaging it.
Thanks a lot for struggling with Webkit / Web / Epiphany once more. You really do make a difference and I mean it in the most positive way possible. Thumbs up from here. :D
( Now if only I could login to see it ;) , just teasing )
BTW I'm keeping my Gnome 3.8 updated daily using the command line, can't wait to see when all the goodies are revealed.

Regards
Stinger

---

### Post by mc4man on 2013-04-02
> **Stinger said:**
> 
( Now if only I could login to see it ;) , just teasing )

Curious - there is an upstream bug associated to your report, did you try what was mentioned in that report, - 
remove /var/lib/gdm/run-initial-setup (if that file exists.

---

### Post by ronacc on 2013-04-02
how does gnome 3 look with just the gnome 3 ppa enabled , I just installed todays daily for the final beta event and would like to update to the newest gnome 3 , when I updated m previous install with both gnome 3 and gnome 3 staging it was a little weird . the basic desktop was w white screen until you moved up to avtivities and then the normal ubuntu background appeare as long as the launcher was visible . I'm 64 bit.

---

### Post by Stinger on 2013-04-02
@ mc4man
It doesn't I'm afraid and Jeremy doesn't believe it's related, I already mentioned it on my [bug-report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466") ( #2 and #3 ) 

@ ronacc
I'm 64 bit too, with only Gnome3 ppa enabled and ran into the above bug. So I haven't seen it yet. Maybe if I had chosen automatic login during install instead it would have worked ?   .

---

### Post by ronacc on 2013-04-02
thanks I guess I'll hold off then .

---

### Post by Stinger on 2013-04-02
@ ronacc
Why ? that's not what your signature says ;)

---

### Post by ronacc on 2013-04-02
I had  a real mess getting the install done don't want to nuke it just yet , maybe tomorrow .

---

### Post by jbicha on 2013-04-02
Stinger, thanks for including the extra info in the bug. I've heard of problems with ATI graphics cards and GNOME Shell. Perhaps you could try different drivers? 

Also, you apparently don't have ubuntu-gnome-desktop (or ubuntu-desktop) installed? I don't think that would make a big difference here but it's a good idea to have it installed.

---

### Post by ronacc on 2013-04-02
seeing what jbicha  said about radeon I went ahead and added gnome 3 ppa and updated , something went very wrong . Now trying to boot the install I get an "out of disk error " and it says I need to load the kernel first .

---

### Post by jbicha on 2013-04-02
ronacc, the GNOME3 PPA shouldn't affect early boot like that. Do you happen to have another bootable device like a CD, USB stick, SD card, etc. plugged in that your computer is trying to boot?

---

### Post by ronacc on 2013-04-02
hmm it must have altered the grub.cfg  I was using my precise install as a master boot . I switched to the gnome3 raring install in bios and it booted but won't from the precise grub . It was booting ok from that one until I updaed with the gnome 3 ppa . Its 11;30 pm here I' investigate tomorrow .

---

### Post by Stinger on 2013-04-03
@ jbicha (and others)

I nailed the problem due to Kotrfa's post:  [http://ubuntuforums.org/showthread.php?t=2131890&p=12586232#post12586232](http://ubuntuforums.org/showthread.php?t=2131890&p=12586232#post12586232)

It's a dependency problem when upgrading via the Gnome3 ppa leaving 29 packages not upgraded in my case, and gnome-shell at version 3.6.3.1 and gdm at 3.8.0, causing Gnome-Shell to crash in my case.
Reported on [Bug #1162466]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1162466") too

---

### Post by ronacc on 2013-04-03
@ jbicha       this morning when I booted the raring gnome 3 install booted from my master boot grub on my precise install it booted ok, it was the first boot of the morning . on a guess I rebooted into a different install and then back to the raring gnome 3 install . No boot that time same message . I shut down instead of rebooted and it booted ok then so there must be some difference between a cold boot and a reboot . I still have the white background when the launcher is not active and the normal ubuntu background when it is . I'd post a screen shot but I can't figure out how with the new forum format .

---

### Post by ronacc on 2013-04-03
something else strange , I added epiphany browser 3.7.9.1-1 and it does not show up when I use the type to search bar but I can be started from terminal , when it is running I cannot add it to favorites by rt clicking the icon .

---

### Post by Flywaver on 2013-04-03
> **ronacc said:**
> something else strange , I added epiphany browser 3.7.9.1-1 and it does not show up when I use the type to search bar but I can be started from terminal , when it is running I cannot add it to favorites by rt clicking the icon .

you added it through synaptic? I did that and same thing happened but I then tried to install epiphany through the terminal and it installed the missing pakages :)

---

### Post by Stinger on 2013-04-03
@ ronacc
Do you have the Gnome3 ppa enabled ?
Do you have the Gnome3 staging ppa enabled ?
What does 
```
gnome-shell --version
``` 
in a terminal give you ?

---

### Post by ronacc on 2013-04-03
```
 ron@ron-desktop2:~$ gnome-shell --version
GNOME Shell 3.8.0.1
ron@ron-desktop2:~$ 
```

I have gnome 3 ppa. I do not have gnom 3 staging . should I ?

@Flywaver  I installed epiphany but when I tried to install the new  webkit it wanted to remove many packages so I did not install tthat .

---

### Post by Flywaver on 2013-04-03
> **ronacc said:**
> @Flywaver  I installed epiphany but when I tried to install the new  webkit it wanted to remove many packages so I did not install tthat .

you need epiphany-browser-data, epiphany-extensions and epiphany-browser-webkit2....if you try to install epiphany-browser it will remove webkit2...it's weird because epiphany-browser is listed as 3.7.91

---

### Post by Stinger on 2013-04-03
> **ronacc said:**
> ```
 ron@ron-desktop2:~$ gnome-shell --version
GNOME Shell 3.8.0.1
ron@ron-desktop2:~$ 
```

I have gnome 3 ppa. I do not have gnom 3 staging . should I ?

No, your install seems to be in good shape ( gnome wise that is ) unlike what mine was before.

---

### Post by Stinger on 2013-04-03
> **ronacc said:**
> I installed epiphany but when I tried to install the new  webkit it wanted to remove many packages so I did not install tthat .

> **Flywaver said:**
> you need epiphany-browser-data, epiphany-extensions and epiphany-browser-webkit2....if you try to install epiphany-browser it will remove webkit2...it's weird because epiphany-browser is listed as 3.7.91

I just installed epiphany-browser-webkit2, it installed 2 packages on my box, epiphany-browser-webkit2 and webkit2. My install is Ubuntu-GNOME only and the Gnome3 ppa.

But you are right ronacc, no entry in the app-window and you can't find it when searching. You have to use the terminal and type epiphany-browser to launch it.

BTW this is posted using epiphany-browser-webkit2. :D

---

### Post by ronacc on 2013-04-03
when I try to add epiphany browser webkit2 3.7.91-1 it wants to remove epi[hany-browser 3.7.91-1 and according to the properties depends list it even conflicts with itself obviously a screwwup in the depends .  see screnshot .

---

### Post by jbicha on 2013-04-03
No, that's intentional. You can install either epiphany-browser or epiphany-browser-webkit2. They each provide /usr/bin/epiphany-browser so they can't both be installed at the same time.

---

### Post by ronacc on 2013-04-03
@jbicha  Thanks for the info . I did'nt know that epiphany-browser-webkit included the browser I thought it was just the webkit .

---

### Post by ronacc on 2013-04-03
I installed epiphany-browser-webkit it works fine , it also solved having to start epiphany from term when you type in the search bar now it shows up as "web" .

---

### Post by Stinger on 2013-04-04
> **ronacc said:**
> I installed epiphany-browser-webkit it works fine , it also solved having to start epiphany from term when you type in the search bar now it shows up as "web" .

I got it too, just needed a reboot, Web is now present both in the app overview and when I search.

@ jbicha
Thanks again for taking the time to build it :-D

---

