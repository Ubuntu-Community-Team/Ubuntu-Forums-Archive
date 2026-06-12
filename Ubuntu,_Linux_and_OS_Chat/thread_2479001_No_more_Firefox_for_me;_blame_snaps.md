---
title: "No more Firefox for me; blame snaps"
date: 2022-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by SeijiSensei on 2022-09-11
First I tried to import a CSV file with logins by flipping the switch in about:config to enable login imports. Then I saved a password file from Firefox on another machine. I could not get the import to work. I can go through the steps, but the accounts never appear.

Well, I thought, it's probably an issue with using the snap version of Firefox. This is a new installation, and I hadn't yet bothered to switch from the snap to the deb version of Firefox as described, among other places, here: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) as I had done in the past. I followed all those steps carefully and still cannot get apt to choose the version of Firefox at the PPA over the snap version. I've done this on other machines, but I struck out entirely on this one.

So that's probably it for my decades-long experience with Firefox on Linux. I've switched to Chrome; at least I can install that from its repository. There needs to be a simple way to avoid all this snap business. How about a check box during installation that says, "Do not use snap packages"?

---

### Post by #&amp;thj^% on 2022-09-11
> **SeijiSensei said:**
> How about a check box during installation that says, "Do not use snap packages"?
I wish we had a say on that SeijiSensei, this would be a perfect option. (More work for the Devs though :))

---

### Post by &amp;KyT$0P# on 2022-09-11
The guide you linked is missing a [FONT=Courier New]sudo apt-get purge 'firefox*'[/FONT] somewhere.  Not sure if this should be done before step 1, between steps 1 & 2, or between steps 4 & 5.

Maybe the [guide you linked in other threads]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/") might work better for you?

Check output of these 3 commands -
```
apt-cache policy
apt-cache policy firefox
dpkg-query -l | grep -i firefox
```

---

### Post by ne29914 on 2022-09-11
The first thing I do after a xUbuntu install is to purge snapd.  This solves the issue once and for all.

---

### Post by dragonfly41 on 2022-09-11
Is PaleMoon worth considering?

[http://www.palemoon.org/](http://www.palemoon.org/)

---

### Post by ajgreeny on 2022-09-11
I'm now using the .tar.gz archive now downloaded direct from Mozilla, not the snap and not a PPA either.

This works very well and there in no possibility of the snap version taking over from that.
This will either notify you that a newer version is available and offer to download and update or if you trust it, it will update in the background and notify you to restart Firefox in order to start using the new version.

PS.
 I also purge snapd and remove all snap packages so i'm totally snap free and will remain so.

---

### Post by QIII on 2022-09-11
The community version of mysql workbench is a snap now.  If I happen to have enough energy one day to install it from Oracle (I'm a member of the ODN/OTN/Whatever-Oracle-is-calling-it-now), so I should be able to get it.  But I'm lazy now that I have retired.  I use mysql on my websites.

Aside from that I might ditch the whole snap thing altogether.  I don't have the visceral objection to it that some seem to.  But I think it's an idea that is going to sputter out in flames like so many other things have when they are too sharp a departure from the norm.  I'll live with it and learn it while it is around so I'm not left standing on the dock if the ship actually does set sail.  But I don't have to be really excited about it.

---

### Post by TheFu on 2022-09-11
Snap constraints break so many workflows that for power users, they are just in the way.

I'd never use Chrome - "Google is a hostile actor" now. [https://selfhosted.show/79](https://selfhosted.show/79)
Allowing the largest internet marketing company direct access to my browser seems really dumb to me.

There are a few snap packages that are unavailable in any other method.  I've been looking to replace those, but it takes effort, since LXD is controlling some of my critical Linux Containers and mostly does a good job ... er .... mostly.  My only real complaints are the use of snap packages and the lack of control that comes with it.  Mainly which storage can be used/accessed and forced package updates outside my exact control.  Lots of people left MSFT over their forced patching. Canonical should have learned that lesson, but apparently has not.

I don't mind the defaults being strict at all. That's probably a good thing, but when we need to use non-default constraints - or remove them completely - that should be possible for the admin.  Also, let me decide when snap packages are updated, if ever.

---

### Post by VMC on 2022-09-11
I'm with  ***ajgreeny*** on this, and here is the instructions he's referring to:
[https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users](https://support.mozilla.org/en-US/kb/install-firefox-linux#w_install-firefox-from-mozilla-builds-for-advanced-users)

---

### Post by QIII on 2022-09-11
From the user's perspective, snaps are a solution looking for a problem to solve.  From the developer's they are an easy way to avoid dealing with real and frustrating complexity.

There are OSes and applications that are developed for the ease of the developers, and they work just the way you'd better like them.  Which is exactly why I don't like them.

---

### Post by miguel001 on 2022-09-12
Oh snap!

---

### Post by mikewhatever on 2022-09-12
You can install Firefox from a PPA, or use the binaries Mozilla provides, so there is really no need to panic.

---

### Post by TenPlus1 on 2022-09-13
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by mIk3_08 on 2022-09-13
As what ajgreeny says. You can still have the Firefox with the .tar.gz archive. You can just run it directly from the extracted .tar.gz archive. Regards and cheers.

---

### Post by TheFu on 2022-09-13
22.04 is an LTS.  Any basic features should work for everyone, without fail.  A browser is one of those things.  People shouldn't HAVE to do anything special to use a browser in all the intended and possible ways, unless they configure it to be restricted themselves.

Test out the junk on non-LTS releases - great, fine. Go crazy.  Ubuntu is getting a bad name due to the mandated constraints for snap packages.  It dilutes the brand and makes me tell new users to head elsewhere for their first distro.  I'm not alone.

Snaps make perfect sense for IoT stuff.  I just hope that Canonical learns this experiment with tight constraints on desktops and servers with no local override has failed sooner than later. It feels like Unity DE all over again, but worse, since we didn't have to use UnityDE.

---

### Post by Frogs Hair on 2022-09-13
I've found it fairly easy run to FF from tar.gz and add to the menu and favorites , but I feel I _shouldn't have to_ explain how to do this to  new or established users who are apprehensive about snaps or disappointed with performance. Rather than purging snapd from the system it should be optional as it is on many other distros and those who wish to use sanp or flatpak can set those options up.  Hope to see snaps added to the list of things that have come and gone.

---

### Post by Tadaen_Sylvermane on 2022-09-13
> [COLOR=#000000]There needs to be a simple way to avoid all this snap business.

I know I don't have the rep or post count. There is a simple way. Use a distro that isn't moving toward snap as a primary. Problem solved. Snap isn't the problem, your choice of distro is at this point. As it is run by a for profit company you have few options, eventually it will get overwhelming to remove snap requirements if not impossible. They have a plan and they are going full bore ahead with it.

I suppose you can fork the whole distro and yank out snap but you'd be better of moving to Debian or something imho.[/COLOR]

---

### Post by VMC on 2022-09-13
> **Tadaen_Sylvermane said:**
> I know I don't have the rep or post count. There is a simple way. Use a distro that isn't moving toward snap as a primary. Problem solved. Snap isn't the problem, your choice of distro is at this point. As it is run by a for profit company you have few options, eventually it will get overwhelming to remove snap requirements if not impossible. They have a plan and they are going full bore ahead with it.

I suppose you can fork the whole distro and yank out snap but you'd be better of moving to Debian or something imho.[/COLOR]

True assessment. That's why I have several distros installed that don't utilize Snap, for when that day finally comes. I've been with Ubuntu for a ***very long time ***and I will hang on until the bitter end, finding ways to circumvent Snap as best I can. When that day comes, I am prepared.

---

### Post by QIII on 2022-09-14
> **Tadaen_Sylvermane said:**
> They have a plan and they are going full bore ahead with it.

As they did with Unity, phones and several other things that eventually got left behind.

But yes.  One is always free to use another distro -- which, in all honesty, I may do myself if I decide I don't like the way things go.  There's nothing wrong with that.

But I'll always also run an Ubuntu flavor and hang around here at the UF until they put all the stools on the bar and turn out the lights.

---

### Post by Tadaen_Sylvermane on 2022-09-14
> [COLOR=#000000]As they did with Unity, phones and several other things that eventually got left behind.

They might abandon apt for dnf as well. Never know... What might happen is irrelevant. What is happening is what matters. For the moment snap is here to stay and that is reality. If people don't like it there is nothing they can do about it. It might go away. It also may never go away. If it's such a big problem for people they should just move on in general instead of sitting around complaining about it.

Solve the problem instead of wishing it wasn't there in the first place.[/COLOR]

---

### Post by ne29914 on 2022-09-14
> **Tadaen_Sylvermane said:**
> 
Solve the problem instead of wishing it wasn't there in the first place.[/COLOR]
I did. Since some time I'm using the Brave Browser instead. The bloat of Firefox got my goat.

---

### Post by ajgreeny on 2022-09-14
> **ne29914 said:**
> I did. Since some time I'm using the Brave Browser instead. The bloat of Firefox got my goat.
Well, that will solve the firefox problem but not the big snap problem, if problem it be for users!
Not everybody is anti-snap but I'm afraid to say that I am; they just do not allow me to work with my system in the way I have for the past 17 years, and they largely remove my control which was one of the major reasons for moving from Windows XP to Ubuntu back in 2005.

---

### Post by slickymaster on 2022-09-15
Thread moved to **Ubuntu, Linux and OS Chat** since it's not a support request.

---

### Post by lammert-nijhof on 2022-09-15
I have seen this all before with the introduction of Unity, when Unity was abandoned and now with the snaps. 
I follow Canonical, because they always provided an excellent OS for $0.00. 
There is always a group of negative users, who confuse facts with their extreme opinions. That group is especially large in the Linux community.

---

### Post by mikewhatever on 2022-09-15
> **ajgreeny said:**
> Well, that will solve the firefox problem but not the big snap problem, if problem it be for users!
Not everybody is anti-snap but I'm afraid to say that I am; they just do not allow me to work with my system in the way I have for the past 17 years, and they largely remove my control which was one of the major reasons for moving from Windows XP to Ubuntu back in 2005.

I've removed all snaps + snapd from a couple of old machines to speed up boot times, and nothing bad happened. Given that the problem is easily solvable, I don't see any reason for anti-snap sentiments, least of all from old time users like yourself and a few others here. 
It reminds me of the brown themes Ubuntu used in the early days, and how a number of people enlessly argued that brown should not be the default, and new users should not need to change to a different theme no matter how easy it is.
I don't know what  the future of snaps holds. It could get better or worse or get cancelled. You don't always get what you want, but still, with Ubuntu, "don't like it - don't use it" has been working well for me. For example, I don't like Gnome3, and use more traditional Xubuntu, Kubuntu and Mate.

---

### Post by poorguy on 2022-09-15
Using Firefox Snap on Ubuntu 22.04.1 and Xubuntu 22.04.1 and no complaints.

I like Firefox so I'll use the default Firefox Snap as it ain't as bad as ya read about.

---

### Post by Frogs Hair on 2022-09-15
> But I'll always also run an Ubuntu flavor and hang around here at the UF  until they put all the stools on the bar and turn out the lights. 				 Me too ! :)

---

### Post by SeijiSensei on 2022-09-16
Did you try to import passwords from a CSV file? If so, how did you get it to work?

---

### Post by KingHanco on 2022-09-20
Type in about:config on the Firefox browser.
Then on the 2nd bar. Put this. signon.management.page.fileImport.enabled Change false to true.

Info [https://4sysops.com/archives/export-and-import-passwords-in-firefox/](https://4sysops.com/archives/export-and-import-passwords-in-firefox/)

---

### Post by SeijiSensei on 2022-09-21
I did that. It worked with .deb versions of Firefox.

---

### Post by Shibblet on 2022-09-22
> **ne29914 said:**
> The first thing I do after a xUbuntu install is to purge snapd.  This solves the issue once and for all.

Try installing Chromium.  Then sit there and watch in horror as APT reinstalls SnapD, and then uses it to install Chromium.

Basically, if they want the package to be a Snap Package, that's all you're going to get.

---

### Post by ne29914 on 2022-09-22
Which is why I use Brave. Why would I choose a browser that uses such sneak tactics?

---

### Post by ajgreeny on 2022-09-22
> **Shibblet said:**
> Try installing Chromium.  Then sit there and watch in horror as APT reinstalls SnapD, and then uses it to install Chromium.

Basically, if they want the package to be a Snap Package, that's all you're going to get.
Yes, but there are PPAs that can be used for dev and beta versions that can still install a .deb chromium, though you now have to use command ***sudo apt install chromium-browser*** not just ***chromium***, or, as you say, chromium pulls in snapd plus the snap version of chromium.
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)

I've used the dev version for a long time now and not had any real difficulties with it.

---

### Post by zebra2 on 2022-09-22
> **ne29914 said:**
> Which is why I use Brave. Why would I choose a browser that uses such sneak tactics?

Brave is already available as a Snap. I'm using it on my 22.10 system.  And I must say, it is very good and smooth.

PS: Open a terminal and type snap-store.  At the top choose Explore and in the Search box type Brave. When it comes up look in the upper right part of the display an there is a box that shows the format available, snap or deb and it will be Snap.

---

### Post by Shibblet on 2022-09-26
> **ajgreeny said:**
> Yes, but there are PPAs that can be used for dev and beta versions that can still install a .deb chromium, though you now have to use command ***sudo apt install chromium-browser*** not just ***chromium***, or, as you say, chromium pulls in snapd plus the snap version of chromium.
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)

I've used the dev version for a long time now and not had any real difficulties with it.

Strangely enough, I was never able to get the PPA's to work.  Ubuntu ignored the PPA's and installed the Snap.  Double check your install, and see if it is a Snap or not.

[https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")

---

### Post by mikewhatever on 2022-09-26
> **Shibblet said:**
> Try installing Chromium.  Then sit there and watch in horror as APT reinstalls SnapD, and then uses it to install Chromium.

Basically, if they want the package to be a Snap Package, that's all you're going to get.

"Watch in horror...", mehh. Do I sweat and tremble, or just watch? :lolflag:
Why are Linux users so melodramatic?

---

### Post by Shibblet on 2022-09-26
> **mikewhatever said:**
> "Whatch is horror...", mehh. Do I sweat and tremble, or just watch? :lolflag:
Why are Linux users so meladramatic?

[SIZE=4]**Me watching APT install SnapD...**[/SIZE]

[IMG]https://c.tenor.com/Nl-cimrpUNQAAAAC/scary-screaming.gif[/IMG]

---

### Post by ajgreeny on 2022-09-26
> **Shibblet said:**
> Strangely enough, I was never able to get the PPA's to work.  Ubuntu ignored the PPA's and installed the Snap.  Double check your install, and see if it is a Snap or not.

[https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")
Yes, I definitely have the .deb version from the [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) ppa. Version 101.0.4947.0 (Developer Build) Ubuntu 22.04 (64-bit)

When you tried to use the PPA did you then try to install **chromium** or did you install **chromium-browser**?
To use the PPA you must install chromium-browser package not chromium or you will get the snap unless you have removed the whole of the snap infrastructure as I have.
If I run command ***sudo apt install chromium*** I get the following output
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package chromium is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  chromium-bsu

E: Package 'chromium' has no installation candidate

```

---

### Post by Shibblet on 2022-09-26
> **ajgreeny said:**
> Yes, I definitely have the .deb version from the [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev) ppa. Version 101.0.4947.0 (Developer Build) Ubuntu 22.04 (64-bit)

When you tried to use the PPA did you then try to install **chromium** or did you install **chromium-browser**?
To use the PPA you must install chromium-browser package not chromium or you will get the snap unless you have removed the whole of the snap infrastructure as I have.
If I run command ***sudo apt install chromium*** I get the following output
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package chromium is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  chromium-bsu

E: Package 'chromium' has no installation candidate

```

LOL!  No...  Completely different package.  ;-)

**[SIZE=4]Chromium BSU[/SIZE]**
[IMG]https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Screenshot_of_Chromium_B.S.U.png/250px-Screenshot_of_Chromium_B.S.U.png[/IMG]

---

### Post by ajgreeny on 2022-09-26
No i did not install chromium-bsu.
However I've been using the PPA version of chromium now since whenever it was that the snap version was made the default in Ubuntu (20.04 or was it 18.04, I can't remember) so I wonder if I've got it wrong when I say the package chromium was what I used to install, which has now become chromium-browssr.

Whatever is the truth of all this, i can't figure out why you have so many problems using the PPA. I have made no changes to package priorities in order to use it but simply enabled it after removing all snaps and snapd then ran command ***sudo apt install chromium-browser*** and all was correctly installed and used.

---

### Post by Shibblet on 2022-09-26
> **ajgreeny said:**
> No i did not install chromium-bsu.
However I've been using the PPA version of chromium now since whenever it was that the snap version was made the default in Ubuntu (20.04 or was it 18.04, I can't remember) so I wonder if I've got it wrong when I say the package chromium was what I used to install, which has now become chromium-browssr.

Whatever is the truth of all this, i can't figure out why you have so many problems using the PPA. I have made no changes to package priorities in order to use it but simply enabled it after removing all snaps and snapd then ran command ***sudo apt install chromium-browser*** and all was correctly installed and used.

Yeah, I've never been able to figure it out either.  I followed many directions from the previous thread, and it still doesn't work.

Regardless, I use Brave now instead.  I only need Chromium for one thing, and it does that without issue.  This is the Snap version of Chromium.

My other issues with Snaps are:  When compared to the standard packages, or PPA's; Snaps seem to not be completely functional.  One Snap will not allow me to save data from the application to any other drive than /home.  I cannot even select mounted drives.  But the PPA of the same application has no problems doing this.

Sometimes Snaps look wrong...  This one is hard to explain... they look like a Windows app running in Wine(ish?), instead of an app running on my Plasma Desktop.  Does that make sense?  I mean, the app works, but it looks funky.  So I use the app in the software repos instead, or a PPA, and it all looks normal.

---

### Post by ajgreeny on 2022-09-27
> **Shibblet said:**
> 
<snip>
My other issues with Snaps are:  When compared to the standard packages, or PPA's; Snaps seem to not be completely functional.  One Snap will not allow me to save data from the application to any other drive than /home.  I cannot even select mounted drives.  But the PPA of the same application has no problems doing this.
<snip>

Yes, this is the biggest problem with snaps as far as I'm concerned and is precisely why I have removed anything to do with the snap way of doing anything on my Xubuntu.
Why do snaps have to be so "locked down" with no way of making real changes to that? It makes no sense to me, and I don't think it ever will!

Rant over; it makes no difference to me as I don't use any snaps at present and if I'm able, I never shall.

---

### Post by Shibblet on 2022-09-27
> **ajgreeny said:**
> Yes, this is the biggest problem with snaps as far as I'm concerned and is precisely why I have removed anything to do with the snap way of doing anything on my Xubuntu.
Why do snaps have to be so "locked down" with no way of making real changes to that? It makes no sense to me, and I don't think it ever will!

I am not entirely sure... but it may have something to do with the way FlatPaks are used with Fedora Silverblue.  From what I understand, the OS and the Kernal run independent of any applications.  The claim is:  "Silverblue is immutable."  This means that application packages have to have all of the dependencies in the package. 

All I can guess, is that they want to do the same thing with Snaps.

> **ajgreeny said:**
> Rant over; it makes no difference to me as I don't use any snaps at present and if I'm able, I never shall.
Agreed, with one caveat.  I hope, one day, I won't have to say "never," and Snaps work with all the functionality of standard packages.

---

### Post by tips2448 on 2022-10-22
With an fresh install to 22.10, regarding Firefox, at random times it won't open without a restart, I can't upload files to the web... I really would like a working browser.

---

### Post by zebra2 on 2022-10-23
If it is given that a "fresh install" means installed on a re-partitioned and formatted drive, I installed  the snap Brave Browser in 22.10 "fresh install" and I had to reboot before Brave would open.  After that it has worked every time.  My 22.10 install is from the 10/21/2022 ISO. I haven't tried to open Firefox so don't know about that.  But I don't think this issue is isolated to Firefox.

---

### Post by kurt18947 on 2022-10-24
This is my speculation only but I wonder if one reason for snaps is Canonical's effort to get proprietary software vendors like Adobe or Intuit to release their wares for Ubuntu. One of the big complaints by big software houses is that there are too many variations between the various distros to support. Are Snaps and Flatpaks an effort to address that complaint? If the same Snap or Flatpak of for example Quickbooks or Adobe would work on most distros, that would seem to be a step in the right direction to make wider use of Linux practical. 

One of the complaints about Snaps is that there can only be one repository whereas Flatpak can have more than one. I could see where proprietary software vendors would only want one source for their precious (unless the software houses have snap stores themselves).  

Or I could be full of it.O:)

---

### Post by bsniadajewski on 2022-10-24
> **kurt18947 said:**
> This is my speculation only but I wonder if one reason for snaps is Canonical's effort to get proprietary software vendors like Adobe or Intuit to release their wares for Ubuntu. One of the big complaints by big software houses is that there are too many variations between the various distros to support. Are Snaps and Flatpaks an effort to address that complaint? If the same Snap or Flatpak of for example Quickbooks or Adobe would work on most distros, that would seem to be a step in the right direction to make wider use of Linux practical. 

One of the complaints about Snaps is that there can only be one repository whereas Flatpak can have more than one. I could see where proprietary software vendors would only want one source for their precious (unless the software houses have snap stores themselves).  

Or I could be full of it.O:)

Agreed.  Whilst I haven't any snaps or flatpaks (yet) on my Kubuntu install, I can definitely see their (and AppImages') appeal and usefulness.  It'd be much easier for developers and users to have one package that works across multiple distros.

As for Firefox being installed as a Snap rather that a *.deb, IIRC the blame would be laid more on Mozillla rather than Canonical.  I'm thinking it makes it easier to push updates more quickly than through the repos.

---

### Post by Shibblet on 2022-10-25
> **kurt18947 said:**
> This is my speculation only but I wonder if one reason for snaps is Canonical's effort to get proprietary software vendors like Adobe or Intuit to release their wares for Ubuntu. One of the big complaints by big software houses is that there are too many variations between the various distros to support. Are Snaps and Flatpaks an effort to address that complaint? If the same Snap or Flatpak of for example Quickbooks or Adobe would work on most distros, that would seem to be a step in the right direction to make wider use of Linux practical.
I've been an Adobe user for over 20 years.  I remember when Aldus Pagemaker and Aldus Photostyler were the industry standards.  ;-)

I've been watching Adobe slowly change over the past few years... and it wouldn't surprise me if they released their own OS.  They have a file browser (Adobe Bridge), all the web-design and browsing tools needed, plus .PDF support, etc.  They are also an industry standard.

I find it easiest to just run a VM with Windows and use my Adobe Software in there.  VirtualBox or VMWare make great VM's for such software.

If Adobe decided to make their own OS, they'd probably use Linux.

> **kurt18947 said:**
> One of the complaints about Snaps is that there can only be one repository whereas Flatpak can have more than one. I could see where proprietary software vendors would only want one source for their precious (unless the software houses have snap stores themselves).  

Or I could be full of it.O:)
Nope... Not full of it at all.  Snaps kinda go against the whole "free and open source" concept.  Since they are only available from one provider.

---

### Post by exploder on 2022-11-05
Firefox now starts fast on my systems, updates are available much sooner and most sites I was having issues with are not much of a problem now. Canonical have greatly improved the Firefox snap in a reasonable amount of time in my opinion. I am perfectly happy with the Firefox snap package now. I use it everyday and it does everything I need just fine.

---

### Post by herman-jongkind on 2022-11-05
Same for me. Firefox works perfectly.

---

### Post by VMC on 2022-11-05
Same for me also, just not on snaps.

---

### Post by donald187 on 2022-12-05
A couple of things that I've found I don't like about snaps is the inability to check their publishing history as well as their cve ratings.  

I was trying to decide between snap Thunderbird and Thunderbird from the repositories and I found I couldn't see the publishing history of snap Thunderbird to see how long historically it took to version bump after the release.

And now I wanted to see the cve rating of Chromium because there's a zero day out on Chrome rated as high.  Now I see that the cve rating of CVE-2022-4262 of chromium-browser in bionic is medium so I feel a bit better about the fact that snap Chromium hasn't version bumped the fix yet.  But once bionic loses support I won't be able to do that.

[https://ubuntu.com/security/CVE-2022-4262](https://ubuntu.com/security/CVE-2022-4262)

So there's a lot more trust required of snaps than packages from the repositories.

---

### Post by exploder on 2022-12-05
Snaps have gotten much better but it bothers me that the Firefox snap has taken my system down 3 times since installing 22.04. An app should NEVER be able to do that. The snap store is pretty crappy too. I have had to use this command more than once to fix it! ```
sudo pkill snap-store && sudo snap refresh snap-store
```. This is an LTS release! I would like Canonical to succeed with snaps but so far they are not the best choice in my opinion.

---

### Post by donald187 on 2022-12-06
> **donald187 said:**
> 
And now I wanted to see the cve rating of Chromium because there's a zero day out on Chrome rated as high.  Now I see that the cve rating of CVE-2022-4262 of chromium-browser in bionic is medium so I feel a bit better about the fact that snap Chromium hasn't version bumped the fix yet.  But once bionic loses support I won't be able to do that.

[https://ubuntu.com/security/CVE-2022-4262](https://ubuntu.com/security/CVE-2022-4262)

Chromium was version bumped today, four days after its release, which is fine.

---

### Post by nm2 on 2022-12-06
> **SeijiSensei said:**
> 
Well, I thought, it's probably an issue with using the snap version of Firefox. This is a new installation, and I hadn't yet bothered to switch from the snap to the deb version of Firefox as described, among other places, here: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) as I had done in the past. I followed all those steps carefully and still cannot get apt to choose the version of Firefox at the PPA over the snap version. I've done this on other machines, but I struck out entirely on this one. 

 
I just used this same guide a few days ago on my Ubuntu 22.04 LTS machine. Perhaps retry the steps again or go over file in preferences.d and made sure you typed everything correctly.

---

### Post by AR_Kozz on 2022-12-12
I've used Ubuntu 18 years, but always resented the dynamic of devs dragging users into bad systems to fix what ain't broke. 

But this firefox snap business is a real "Huh?" moment for me. I've purged it twice and seen it restore itself on reboot, and the PPA disappeared both times too. I'm sure I can fix whatever monkey business was written in to make my sudo actions reversible, but I shouldn't have to.

---

### Post by The Cog on 2022-12-13
I too used Ubuntu since they released Hoary Hedgehog. Until recently. Between them, Unity and snaps have made me look elsewhere, and I find that Mint is my choice now. No snaps, and the Cinnamon desktop feels really comfortable to me - "Fits like an old glove" as the saying goes. It's at least worth a try.

I wrote a replacement df and lsblk script on Ubuntu to get rid of the dozens of snap lines they gave me. I put them in ~/bin, and they look like this:
```
$ cat ~/bin/df
#!/bin/sh
/bin/df "$@" | grep -v snap
```
That removes a lot of the major irritation from snaps, for me at least. I use df and lsblk a lot during the day at work.

---

### Post by ajgreeny on 2022-12-13
It is now much simpler to uninstall all **firefox** packages and download the .tar.gz archive direct from Mozilla then run **firefox** directly from the executable file in the extracted archive.

I have been doing so since 22.04 pushed the snap as its default version, having removed the complete snap infrastructure from my computers.
It works with no difficulties and can be set up to notify you of available updates.

---

### Post by exploder on 2022-12-13
I had another complete system crash with the Firefox snap on 22.04... I had Gedit open at the same time, noticed some bad screen tearing with it, closed it, went back to Firefox and about 10 minutes later the screen went black and the PC rebooted. The PC has fully supported hardware out of the box, no proprietary drivers at all. Changing sessions does not make a difference. I really can't have the system randomly crashing...  Also, random site issues that come and go with updates.

I have Mint 21 Cinnamon Edition on two other systems with the Firefox deb package and no issues of any kind. The Cog summed things up very well!

---

### Post by DuckHook on 2022-12-13
> **exploder said:**
> Snaps have gotten much better but it bothers me that the Firefox snap has taken my system down 3 times since installing 22.04. An app should NEVER be able to do that … they are not the best choice in my opinion.

> **exploder said:**
> I had another complete system crash with the Firefox snap on 22.04 … I really can't have the system randomly crashing...  
I know that I sound like a fanatic flogging my pet topic, but have you considered running apps like FF inside a container? You don't have to use LXD if you are allergic to snaps—there's everything from Docker to Flatpack to AppImage. Lots of additional advantages besides security and sandboxing (like portability and easy redundancy).

Your system crashes could be due to other issues that may be unrelated to snap. It's a good idea to check through your logs and do some diagnostics after such a crash. It could be anything from a bad RAM block to a corrupted binary.

---

### Post by exploder on 2022-12-14
>  Your system crashes could be due to other issues that may be unrelated to snap. It's a good idea to check through your logs and do some diagnostics after such a crash. It could be anything from a bad RAM block to a corrupted binary. 

Logs did not reveal anything unfortunately. Mixed versions of Gnome, wayland and xserver mash up, it could be anything... Not an ideal situation for an LTS in my opinion. I had NO problems with 21.10. Originally I thought DistroWatch's review of 22.04 was kind of harsh but the sad truth is he was right. 

This desktop uses an AMD RX 560 2GB. Before the system crashes the compositor goes crazy, things tearing and flickering. Does not matter what session I use. All my hardware has been tested and is in good shape.No issues using Mint or Windows 10, only Ubuntu. My newer system with an RX 570 suffers the exact same issues. 

Real tired of fixing the software center every single time it is updated, it's ridiculous.I have installed 22.04 on three systems now. The system with an NVIDIA GT 1030 was completely unusable, the two that have AMD graphics crash fairly often. Sorry but the LTS seems more like a beta release than production ready to me. I like Ubuntu but I need my systems to work reliably. The only bug I have found with Mint is the monitor will not go to sleep on the system with the AMD RX 560, I can live with that. It tries to go to sleep, then turns back on. No big deal, I can always press the power button.

I do not want to spend my spare time fixing things. I just want it to work reliably.

---

### Post by DuckHook on 2022-12-14
I feel for you that you've run into such problems. I have Jammy installed on six boxes ranging from laptops to desktops to servers and they all run flawlessly (so far). I suppose that everyone's mileage varies.

If Mint works for you, then that's the way to go. I more than agree that life is too short to put up with crashes and bugs.

---

### Post by mIk3_08 on 2022-12-16
> **exploder said:**
> Logs did not reveal anything unfortunately. Mixed versions of Gnome, wayland and xserver mash up, it could be anything... Not an ideal situation for an LTS in my opinion. I had NO problems with 21.10. Originally I thought DistroWatch's review of 22.04 was kind of harsh but the sad truth is he was right. 

This desktop uses an AMD RX 560 2GB. Before the system crashes the compositor goes crazy, things tearing and flickering. Does not matter what session I use. All my hardware has been tested and is in good shape.No issues using Mint or Windows 10, only Ubuntu. My newer system with an RX 570 suffers the exact same issues. 

Real tired of fixing the software center every single time it is updated, it's ridiculous.I have installed 22.04 on three systems now. The system with an NVIDIA GT 1030 was completely unusable, the two that have AMD graphics crash fairly often. Sorry but the LTS seems more like a beta release than production ready to me. I like Ubuntu but I need my systems to work reliably. The only bug I have found with Mint is the monitor will not go to sleep on the system with the AMD RX 560, I can live with that. It tries to go to sleep, then turns back on. No big deal, I can always press the power button.

I do not want to spend my spare time fixing things. I just want it to work reliably.
I also have 4 Ubuntu Jammy System. 2 of them installed in HP and acer  Laprop It runs normally and so smooth. So far so good and I haven't encountered anything you have mentioned. Regards and  cheers

---

### Post by AR_Kozz on 2022-12-18
The instructions for installing the PPA version and keeping it more current than the snap version worked for about a week, before once again I booted up to the snap version. 

Among the reasons I won't use that is I'll have to fix its less than 100% compatibility with all my history and settings, and not sure if that would succeed. 

Can't purge snap, because I do have snap Chromium and would have to fix a bunch of stuff switching away from that. 

If this is still real linux, the user should have the option to simply disable the snap version and not have it rise from the dead.

---

### Post by agentl074 on 2022-12-19
Well, Firefox is an OK browser; however, I've had the best results with Brave (command install). There are, of course, MANY other options.

---

### Post by TheFu on 2022-12-19
A guy trying to watch the World Cup Finals was screwed by snap updating Firefox.
[https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/](https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/)
Local control over when snaps are updated need to happen, with the ability to delay them forever, if desired.  If someone is using the system, a popup should ask if installing updates now or in 2, 4, 8, 12 hours is preferred, at a minimum.

---

