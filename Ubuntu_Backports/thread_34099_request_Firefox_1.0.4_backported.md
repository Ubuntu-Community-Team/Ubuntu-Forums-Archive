---
title: "request: Firefox 1.0.4 backported"
date: 2005-05-13
forum: Ubuntu Backports
---

### Post by mc_cgp on 2005-05-13
Hi,

Using the last version in rep (1.0.3-2 from backports) but exploit still working 

[http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml)

Will there be an 1.0.4 backport?

Thanks in advance.
Best Regards.

---

### Post by jdong on 2005-05-13
[color=black]I can't find the source code.... :(


Never mind, found it:

[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/source/firefox-1.0.4-source.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/source/firefox-1.0.4-source.tar.bz2)
[http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.diff.gz)

1.0.4~5.04ubp1+1.0.2-0ubuntu1


Will package tonight
[/color]

---

### Post by mc_cgp on 2005-05-13
[QUOTE=jdong][color=black]I can't find the source code.... :(


Never mind, found it:

[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/source/firefox-1.0.4-source.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.0.4/source/firefox-1.0.4-source.tar.bz2)
[http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-firefox/mozilla-firefox_1.0.2-0ubuntu5.diff.gz)

1.0.4~5.04ubp1+1.0.2-0ubuntu1


Will package tonight
[/color][/QUOTE]

Thanks, we hope you had a very good birthday.

---

### Post by stoffe on 2005-05-13
Will be much appreciated, especially since this has started to happen when trying to get an extension:> You must upgrade to version 1.0.4 or newer of Firefox before accessing the Mozilla Update web service. In order to keep your computer safe when using the Internet, it’s important to install new updates of Firefox as soon as they are available. Click on the Upgrade Now link to get the latest version of Firefox.([http://www.mozilla.org/products/firefox/upgrade/?application=firefox/](http://www.mozilla.org/products/firefox/upgrade/?application=firefox/))

Thanks for your efforts! =)

---

### Post by crmanski on 2005-05-13
I am curious. Since this is an update(1.0.3 was too) that covers a couple security issues why wouldn't this package be updated in [http://security.ubuntu.com/](http://security.ubuntu.com/) ?

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=crmanski]I am curious. Since this is an update(1.0.3 was too) that covers a couple security issues why wouldn't this package be updated in [http://security.ubuntu.com/](http://security.ubuntu.com/) ?[/QUOTE]
 firefox introduces new features together with bug fixes with each release. Ubuntu in general only introduces new features with a new release since this is more secure. So the Ubuntu developers take the bug fixes from 1.0.4 but not the new features .. that's why the version number doesn't increase to 1.0.4

---

### Post by jdong on 2005-05-13
Firefox 1.0.4 in staging.

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=jdong]Firefox 1.0.4 in staging.[/QUOTE]
 I couldn't resist ...I'm running it now :)

edit :
but I still can't get to :
[https://addons.mozilla.org/?application=firefox](https://addons.mozilla.org/?application=firefox)
I end up here :
[http://www.mozilla.org/products/firefox/upgrade/?application=firefox](http://www.mozilla.org/products/firefox/upgrade/?application=firefox)

when I choose about .. I see 1.0.4 .. somehow this isn't communicated right :(

---

### Post by rpgcyco on 2005-05-13
I'm also running it now, no problems so far. Thanks again. :)

- Rpg Cyco

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=rpgcyco]I'm also running it now, no problems so far. Thanks again. :)

- Rpg Cyco[/QUOTE]
 can you get to the firefox addons page ? [https://addons.mozilla.org/?application=firefox](https://addons.mozilla.org/?application=firefox)
I get the "upgrade to 1.0.4" message

---

### Post by rpgcyco on 2005-05-13
Nope, I get the same problem as you. I don't really have a use for that page though, so it doesn't bother me much.

- Rpg Cyco

---

### Post by XDevHald on 2005-05-13
Hmm, runs perfectly ;)

---

### Post by ubuntu_demon on 2005-05-14
> **BB]Hmm, runs perfectly  said:**
> 
 you don't get the ::

[QUOTE]
You must upgrade to version 1.0.4 or newer of Firefox before accessing the Mozilla Update web service. In order to keep your computer safe when using the Internet, it’s important to install new updates of Firefox as soon as they are available. Click on the Upgrade Now link to get the latest version of Firefox.


when you try to go to firefox addons ?

---

### Post by Gandalf on 2005-05-14
ok i get firefox 1.0.4 through backports today  but the major security hole is still there!

someone else can run the demo from this page?
[http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml#](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml#)

i can run it :o


//EDIT:
also i can't view the sources of any page
i get:
```

XML Parsing Error: syntax error
Location: chrome://global/content/viewSource.xul
Line Number 1, Column1:

xulUT
^

```

---

### Post by ubuntu_demon on 2005-05-14
[QUOTE=Gandalf]ok i get firefox 1.0.4 through backports today  but the major security hole is still there!

someone else can run the demo from this page?
[http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml#](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml#)

i can run it :o


//EDIT:
also i can't view the sources of any page
i get:
```

XML Parsing Error: syntax error
Location: chrome://global/content/viewSource.xul
Line Number 1, Column1:

xulUT
^

```[/QUOTE]
 I can view sources

When I go to [http://www.mikx.de/firelinking](http://www.mikx.de/firelinking) and I click run example .. I see nothing happening.

---

### Post by Gandalf on 2005-05-14
[QUOTE=demon666_nl]I can view sources

When I go to [http://www.mikx.de/firelinking](http://www.mikx.de/firelinking) and I click run example .. I see nothing happening.[/QUOTE]
 hmmmmmmm.... weird!!!
wait i reboot my ubuntu just in case, but firefox has already been rebooted and i see in the about window 1.0.4

---

### Post by ubuntu_demon on 2005-05-14
[QUOTE=Gandalf]hmmmmmmm.... weird!!!
wait i reboot my ubuntu just in case, but firefox has already been rebooted and i see in the about window 1.0.4[/QUOTE]
 can you include a screenshot of what's happening in your case ?

---

### Post by Gandalf on 2005-05-14
i rebooted, after reboot it worked, now i can see nothing when i click and i can see sources, weird that it needs ubuntu reboot :o

---

### Post by stoffe on 2005-05-14
[QUOTE=Gandalf]i rebooted, after reboot it worked, now i can see nothing when i click and i can see sources, weird that it needs ubuntu reboot :o[/QUOTE]
 Well it sounds exactly like you didn't restart it, and it shouldn't take more than that; sometimes Firefox can linger around a bit though, so if it doesn't seem to work, start looking for processes and slay them manually.

---

### Post by rwabel on 2005-05-14
[QUOTE=demon666_nl]can you get to the firefox addons page ? [https://addons.mozilla.org/?application=firefox]("https://addons.mozilla.org/?application=firefox")
I get the "upgrade to 1.0.4" message[/QUOTE]

same for me, I cannot get to the addons page. Did someone try out the 1.0.4 version from the firefox homepage and not the ubuntu one if the same problem occurs?

---

### Post by Gandalf on 2005-05-14
[QUOTE=rwabel]same for me, I cannot get to the addons page. Did someone try out the 1.0.4 version from the firefox homepage and not the ubuntu one if the same problem occurs?[/QUOTE]
 me too :S

---

### Post by rwabel on 2005-05-14
I've installed the firefox version which was suggested by firefox to get to the addon page. it's the installer version and it worked fine. But I usually don't like installer so I've also tried the normal version.
Both are working fine, I guess that there is a problem with the ubuntu version. I prefer the ubuntu version because some of the plugins don't work with the one from firefox, even if java, flash etc is installed

---

### Post by jodef on 2005-05-14
[QUOTE=rwabel]same for me, I cannot get to the addons page. Did someone try out the 1.0.4 version from the firefox homepage and not the ubuntu one if the same problem occurs?[/QUOTE]

I didn't use the one on mozilla's page but I updated the version in PclinuxOS to 1.04 and it works perfectly; exploit not working and I can access the mozilla add-ons page hope we get it working in Ubuntu soon.

---

### Post by XDevHald on 2005-05-14
[QUOTE=demon666_nl]you don't get the ::



when you try to go to firefox addons ?[/QUOTE]

Ah now that is a different story, it's asking for me to upgrade to 1.0.4. I'll have to check my configs and see why it's doing that...

---

### Post by andrewpmk on 2005-05-14
When I try to install the firefox_1.0.4 packages (main and gnome-support) from backports-staging, dpkg gives me an error message:

andrew@andrew:~/temp$ sudo dpkg -i mozilla-firefox*
(Reading database ... 105272 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.3-2~5.04ubp1+1.0.2-0ubuntu5 (using mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/mozilla-firefox/components/libdocshell.so')
Preparing to replace mozilla-firefox-gnome-support 1.0.3-2~5.04ubp1+1.0.2-0ubuntu5 (using mozilla-firefox-gnome-support_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: dependency problems prevent configuration of mozilla-firefox-gnome-support:
 mozilla-firefox-gnome-support depends on mozilla-firefox (= 1.0.4~5.04ubp1+1.0.2-0ubuntu1); however:
  Version of mozilla-firefox on system is 1.0.3-2~5.04ubp1+1.0.2-0ubuntu5.
dpkg: error processing mozilla-firefox-gnome-support (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb
 mozilla-firefox-gnome-support

---

### Post by jdong on 2005-05-14
Hmm, that's a WIERD message... make sure you have enough disk space and your filesystem isn't corrupted.

Can anyone else confirm this?

---

### Post by andrewpmk on 2005-05-14
[QUOTE=jdong]Hmm, that's a WIERD message... make sure you have enough disk space and your filesystem isn't corrupted.

Can anyone else confirm this?[/QUOTE]
 I don't think that disk space is a problem.

[FONT=Courier New]andrew@andrew:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda5               240863    112831    115182  50% /
tmpfs                   250336         0    250336   0% /dev/shm
/dev/hda10            12239248   5571872   6035624  49% /home
/dev/hda8               384373      9600    354293   3% /tmp
/dev/hda6              5036284   2688308   2092144  57% /usr
/dev/hda7               812943    162876    606694  22% /var
/dev/hda1             19535008  18773956    761052  97% /windows
/dev                    240863    112831    115182  50% /.dev
none                      5120      2852      2268  56% /dev[/FONT]

(don't worry about the Windows partition)

Furthermore, the backport hosed Firefox 1.0.3, requiring me to reinstall Firefox.

---

### Post by Bob D. on 2005-05-14
I just installed 1.0.4 from Backports staging via the Ubuntu Update Manager without any problems.

Bob

---

### Post by andrewpmk on 2005-05-14
[QUOTE=Bob D.]I just installed 1.0.4 from Backports staging via the Ubuntu Update Manager without any problems.

Bob[/QUOTE]
 Any ideas? Any other people suffered the same problem?

---

### Post by Gandalf on 2005-05-14
if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for [color=blue]general.useragent.vendorSub[/color]
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)

---

### Post by Bob D. on 2005-05-14
Thanks Gandalf! Works perfectly!

Bob

---

### Post by Gandalf on 2005-05-14
[QUOTE=Bob D.]Thanks Gandalf! Works perfectly!

Bob[/QUOTE]
 no problem!!!

---

### Post by fishfork on 2005-05-14
[QUOTE=demon666_nl]firefox introduces new features together with bug fixes with each release. Ubuntu in general only introduces new features with a new release since this is more secure. So the Ubuntu developers take the bug fixes from 1.0.4 but not the new features .. that's why the version number doesn't increase to 1.0.4[/QUOTE]
Yes, that's what Ubuntu line on this is. The thing is, 1.0.4 is a bugfix release - it doesn't include new features AFAIK. So I'm not sure why they're not rolling it out. Maybe they're worried that, if they keep incrementing the version, it'll need new versions of some libraries which aren't available. Or maybe it's just a bureaucratic problem... I really don't know.

---

### Post by AgenT on 2005-05-14
You guys are being too harsh on the Ubuntu devs. They have a policy that they stick with which more or less says that no new software is to be released after the initial Ubuntu release. Bug fixes being the only updates accepted. A lot of people and companies count on Ubuntu sticking to this plan. It's what one may call having a set goal toward stability and yet, due to the constant release cycle (6mo), having a good up-to-date desktop. Breaking this would be breaking their promise of sticking to their plan.

Bug fix release or not, it is still a new version numbered release which makes it count as a new release. I am sure that the bug fixes will trickle down to 1.0.2 which is the official build (in fact, after updating the system the bug exploit proof of concept does not work). Anyway, this is starting to get off topic and I don't want to start a flame war or anything but everyone should remember that they are doing this for *our* benefit and as per their promise.

And, after all, there is this thing called the backports projects. If you want the new updates, use backports (which you obviously do). What, then, seems to be the problem? You are getting the best of both worlds. You get a choice of either using backports or not.

But that is just me and I have been using Ubuntu for less than a week now so I may be wrong.

---

### Post by fishfork on 2005-05-14
Apologies if I came across as critical, it wasn't intended. I respect what the devs are trying to do here and think Ubuntu is a fabulous distribution in general (the best I've tried). However, I believe there is an issue here. Look at Warty - apparently it is still officially supported with security fixes but the version of firefox there is full of holes. And even in Hoary, it took the best part of a month for the fixes from 1.0.3 to appear; meanwhile the exploits were visibly documented on mozilla.org.

On the other hand, I've never tried to put together a linux distribution myself, so I probably have no idea of the sort of problems that might arise from updating to the newest version of smaller apps like FF. The real question is, would it affect stability or not?

> Bug fix release or not, it is still a new version numbered release which makes it count as a new release.
Agreed, but that's exactly the kind of bureaucratic problem I was talking about! Perhaps they could look at each package seperately and decide whether releasing a new version would affect stability or not. Is there any particular reason to 'keep all the numbers the same'?

Maybe I'm flogging this one to death, but it really galled me was when I realised that Firefox on windows was safer than on Ubuntu. As you say, I've got backports, so my desktop's fine for the time being. It would be nice to be able to download the updates as official signed packages, though!

Hope this clarifies,

Ben

---

### Post by ubuntu_demon on 2005-05-15
[QUOTE=Gandalf]if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for [color=blue]general.useragent.vendorSub[/color]
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)[/QUOTE]
 works perfectly .... thnx!

---

### Post by ubuntu_demon on 2005-05-15
[QUOTE=fishfork]Apologies if I came across as critical, it wasn't intended. I respect what the devs are trying to do here and think Ubuntu is a fabulous distribution in general (the best I've tried). However, I believe there is an issue here. Look at Warty - apparently it is still officially supported with security fixes but the version of firefox there is full of holes. And even in Hoary, it took the best part of a month for the fixes from 1.0.3 to appear; meanwhile the exploits were visibly documented on mozilla.org.

On the other hand, I've never tried to put together a linux distribution myself, so I probably have no idea of the sort of problems that might arise from updating to the newest version of smaller apps like FF. The real question is, would it affect stability or not?


Agreed, but that's exactly the kind of bureaucratic problem I was talking about! Perhaps they could look at each package seperately and decide whether releasing a new version would affect stability or not. Is there any particular reason to 'keep all the numbers the same'?

Maybe I'm flogging this one to death, but it really galled me was when I realised that Firefox on windows was safer than on Ubuntu. As you say, I've got backports, so my desktop's fine for the time being. It would be nice to be able to download the updates as official signed packages, though!

Hope this clarifies,

Ben[/QUOTE]
 I don't think warty's firefox is full of holes ... because all security fixes that apply to warty's firefox are "backported" into it.

---

### Post by N'Jal on 2005-05-15
Um what are the backports repo's? I always like to have the most recent FF and thunberbird OO.o etc as i use them the most. So if someone could point me in the direction of them i would appriciate it

---

### Post by Gandalf on 2005-05-15
[QUOTE=N'Jal]Um what are the backports repo's? I always like to have the most recent FF and thunberbird OO.o etc as i use them the most. So if someone could point me in the direction of them i would appriciate it[/QUOTE]
 ubuntu backports repo are these
```

# ubuntuforums.org backports
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```

---

### Post by ubuntu_demon on 2005-05-15
[QUOTE=Gandalf]ubuntu backports repo are these
```

# ubuntuforums.org backports
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```[/QUOTE]
 don't include staging unless you wanna help testing

if you want only firefox from backports staging (pretty stable)
go here and download the deb

[http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/binary-i386/)
don't forget to download the gnomesupport deb too!

install it with :
dpkg -i packagename

---

### Post by XDevHald on 2005-05-15
[QUOTE=demon666_nl]don't include staging unless you wanna help testing

if you want only firefox from backports staging (pretty stable)
go here and download the deb

[http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/binary-i386/]("http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/binary-i386/")
don't forget to download the gnomesupport deb too!

install it with :
dpkg -i packagename[/QUOTE]

Nice :D thanks for the link demon, had to get gnomesupport considering I never had it ;)

---

### Post by N'Jal on 2005-05-15
Thanks guy's i decided to include staging but leave it commented out. Dl ff and gnome support now

---

### Post by rwabel on 2005-05-15
[QUOTE=Gandalf]if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for [color=blue]general.useragent.vendorSub[/color]
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)[/QUOTE]
 thanks a lot for the tip. works fine now

---

### Post by Gandalf on 2005-05-15
[QUOTE=rwabel]thanks a lot for the tip. works fine now[/QUOTE]
 no problem!!!

---

### Post by jdong on 2005-05-15
Alright, it seems like this backport's stable. Due to the security nature of this update, I'm promoting it now.

---

### Post by fishfork on 2005-05-15
[QUOTE=demon666_nl]I don't think warty's firefox is full of holes ... because all security fixes that apply to warty's firefox are "backported" into it.[/QUOTE]
Unfortunately not. According to [this page](http://people.ubuntu.com/~pitti/ubuntu-cve/), there are **a lot** of unfixed issues in Warty's firefox.

---

### Post by AgenT on 2005-05-15
[QUOTE=fishfork]Apologies if I came across as critical[/QUOTE]
Nothing wrong with being critical as it can point out ways to improve. I also did not mean to sound too harsh.

[QUOTE=fishfork]It would be nice to be able to download the updates as official signed packages, though![/QUOTE] I may be wrong, and probably am, but I seem to remember reading somewhere that signed packages are in the works. I tried looking where I could have read this but found nothing. :-\"

---

### Post by AgenT on 2005-05-15
[QUOTE=fishfork]Unfortunately not. According to [this page]("http://people.ubuntu.com/%7Epitti/ubuntu-cve/"), there are **a lot** of unfixed issues in Warty's firefox.[/QUOTE]

I would take a venture to guess that is because Ubuntu is focusing its efforts on the newest release, not the older one. Both are supported, but the newer version gets priority. But this is not the fault of the method, just look at Debian. They use very *old* packages in stable and yet they are, well, the most stable distro out there (if you use only stable packages). And it has few vulnerabilities. There are a lot of jokes that go around from silly people about how old Debian packages are, but there is a good reason for that.

---

### Post by jodef on 2005-05-15
> Agreed, but that's exactly the kind of bureaucratic problem I was talking about! Perhaps they could look at each package seperately and decide whether releasing a new version would affect stability or not. Is there any particular reason to 'keep all the numbers the same'?

Maybe I'm flogging this one to death, but it really galled me was when I realised that Firefox on windows was safer than on Ubuntu. As you say, I've got backports, so my desktop's fine for the time being. It would be nice to be able to download the updates as official signed packages, though! It's not exactly a bureaucratic problem it's the same debate that has always existed security vs stability; Breezy has all the up to date packages but that also means there is the chance of system instability. In the case of Firefox the releases aren't strictly security updates some enhancements/changes also end up in the mix hence the reason as well for a lot of broken extensions even between the minor version changes. I would like to see the security patches end up as incremental changes rather than whole downloads. Having to d/l a 8MB+ file on dial up to fix a security flaw really sucks :sad: but then I really don't know how much work is involved in implementing that suggestion.

---

### Post by jdong on 2005-05-15
[QUOTE=jodef] Breezy has all the up to date packages but that also means there is the chance of system instability.[/QUOTE]

That's not a true statement in itself. For a "fast-releasing" distro, I'm disappointed that Ubuntu's dev branch isn't as fast paced as slower brethren, like Redhat's RawHide. Look at RawHide. Firefox 1.0.4 was uploaded hours after unofficial tagging. They're running CVS snapshots of libraries, testing them out. Fedora releases even less often than Ubuntu, but the dev branch is interesting.


Breezy still has Firefox 1.0.2, and barely keeps in check with Sid. I really hope that Grumpy kicks off soon, because I can't satisfy backports requests using Ubuntu packages (have to go off to Debian, which proved inadequate as far as Firefox goes)

---

### Post by jodef on 2005-05-15
[QUOTE=jdong]That's not a true statement in itself. For a "fast-releasing" distro, I'm disappointed that Ubuntu's dev branch isn't as fast paced as slower brethren, like Redhat's RawHide. Look at RawHide. Firefox 1.0.4 was uploaded hours after unofficial tagging. They're running CVS snapshots of libraries, testing them out. Fedora releases even less often than Ubuntu, but the dev branch is interesting.
[/QUOTE]I do apologise I thought Breezy was up to date, well that's disappointing. I use Pclos as my KDE distro of choice more a less a very small dev team and Firefox 1.04 was in the repository since early yesterday.

---

### Post by fishfork on 2005-05-15
[QUOTE=AgenT]But this is not the fault of the method, just look at Debian. They use very *old* packages in stable and yet they are, well, the most stable distro out there (if you use only stable packages). And it has few vulnerabilities.[/QUOTE]
The thing about debian stable is it's probably mostly used on servers, so it doesn't really matter that it comes with an ancient Mozilla version 1.0 or whatever (and I'd be surprised if that had all the latest patches). But with Ubuntu, I get the impression most people are using it as a desktop OS - and in that case, web browser security is one of the main security weakpoints.

Admittedly there aren't any malicious webpages I know of that target linux, but Firefox is getting very popular and [malware is beginning to target it](http://www.channelregister.co.uk/2005/03/11/alternative_slimeware/). I suspect it's architecture would make it reasonably easy for someone to make, for example, a web page with a platform-independent keylogger to harvest banking details.

I may have been a bit harsh on Ubuntu. Perhaps bureaucracy was the wrong word to use - I can see any changes of this nature might well be disruptive. The real reason for posting is to spread awareness, I suppose - I really don't want to see us go the same way as the infamous Internet Explorer. Sorry I've taken the thread so far off topic, I just felt this all had to be said.

Ben

PS: Suppose I should actually install the backport now  :)

---

### Post by mc_cgp on 2005-05-15
[QUOTE=jdong]Alright, it seems like this backport's stable. Due to the security nature of this update, I'm promoting it now.[/QUOTE]


Running it now, no problems so far. Thanks again for the port. Backports and the forum rely make a diference for Ubuntu and make this distro stand out.

Bye

---

### Post by jodef on 2005-05-16
Finally able to d/l Firefox 1.04 backport working fine no problems. Thanks for pointing out the version change info req'd Gandalf. :)

---

### Post by NeoChaosX on 2005-05-17
Um, I can't change the "Show Download Manager when a download begins" option anymore (and it's disabled to boot).  :-?

---

### Post by bonifacio on 2005-05-17
I am using 1.0.4 from the Backports Project.

Tools/Extensions/Get More Extensions leads me to a page that says **Latest Update of Firefox Now Available**

Further it states:
> You must upgrade to version 1.0.4 or newer of Firefox before accessing the Mozilla Update web service. In order to keep your computer safe when using the Internet, it’s important to install new updates of Firefox as soon as they are available. Click on the Upgrade Now link to get the latest version of Firefox.

Any way to resolve it?

---

### Post by AgenT on 2005-05-17
[QUOTE=bonifacio]I am using 1.0.4 from the Backports Project.

Tools/Extensions/Get More Extensions leads me to a page that says **Latest Update of Firefox Now Available**

Further it states:


Any way to resolve it?[/QUOTE]

This has already been answered in *this* thread. Please at least take the time to read the thread you post on for an answer before asking others to spend their time helping you.
:roll:

---

### Post by jdong on 2005-05-17
I won't consider this a packaging bug, because the setting is actually stored in user profiles, which install scripts undoubtedly shouldn't touch for safety's sake!

---

### Post by bonifacio on 2005-05-17
So how's it going to affect the future release of FF (say 1.0.5) .  Should I be changing the config/user profiles everytime now?

---

### Post by loom001 on 2005-05-17
quick noob question?  Where is the about:config

Thanks

---

### Post by rwabel on 2005-05-17
[QUOTE=loom001]quick noob question?  Where is the about:config

Thanks[/QUOTE]
 just write about:config where you write the url's for a website (don't know the name for it) and it opens the about:config page from firefox

---

### Post by loom001 on 2005-05-17
thanks for the help!

---

### Post by Technoviking on 2005-05-17
[QUOTE=Gandalf]if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for [color=blue]general.useragent.vendorSub[/color]
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)[/QUOTE]
My Firefox reset general.useragent.vendorSub switches back to 1.0 when it exits, anyway to stop it from doing that?

Mike

---

### Post by AgenT on 2005-05-17
[QUOTE=Mike Basinger]My Firefox reset general.useragent.vendorSub switches back to 1.0 when it exits, anyway to stop it from doing that?

Mike[/QUOTE]

Something must be wrong with your configuration files. Does changing any other setting result in the same thing? Also, are you *sure* that every Firefox instance was killed? Try doing:
 ```
ps -ef | grep firefox
``` 
If all else fails, backup your bookmarks (export) and close all Firefox instances. Then rename your profile folder so that Firefox thinks this is the first time it is running. See if your settings are now saved, if so, you know something went wrong with your profile. You can either try to hunt the problem down or keep your current new profile and import your bookmarks and redo your preferences.

---

### Post by fishfork on 2005-05-17
[QUOTE=Mike Basinger]My Firefox reset general.useragent.vendorSub switches back to 1.0 when it exits, anyway to stop it from doing that?
[/QUOTE]Also, which extensions have you got installed? If you're using firesomething or user agent switcher they might be causing problems.

---

### Post by Technoviking on 2005-05-18
[QUOTE=fishfork]Also, which extensions have you got installed? If you're using firesomething or user agent switcher they might be causing problems.[/QUOTE]
It was User Agent, good call.

Mike

---

### Post by Dax0r on 2005-05-19
[QUOTE=Mike Basinger]It was User Agent, good call.

Mike[/QUOTE]

You can add with user agent switcher a Firefox 1.0.4 user agent  ;-)

---

### Post by zenrox on 2005-05-19
one prob i have bine having with firefox 1.0.4
every time i run it wont start untill i kill a progam that is starting
fuser and sed  trying to play a sound directaly my sound card
but once fuser has bine killed firefox continues to load up ](*,)
(nevermind FIXED "a reboot goes a long way"  :roll:

---

### Post by allforcarrie on 2005-05-28
the about cofig work around got me in....

---

### Post by bk452 on 2005-05-29
[QUOTE=Gandalf]if someone is still suffering from the problem that they can't visit firefox addons page here's the solution
go to about:config
search for [color=blue]general.useragent.vendorSub[/color]
change it from 1.0 to 1.0.4
and it should work

source : [https://bugzilla.ubuntu.com/show_bug.cgi?id=10681](https://bugzilla.ubuntu.com/show_bug.cgi?id=10681)[/QUOTE]

How do I get to the about:config file?  Where is it?

---

### Post by Gandalf on 2005-05-29
[QUOTE=bk452]How do I get to the about:config file?  Where is it?[/QUOTE]
 type about:config in the address bar

---

### Post by mglukhovsky on 2005-06-05
I just installed Hoary and went ahead to get backports. Now when I try to access "about:config" I get the following message:
```
XML Parsing Error: syntax error
Location: jar:resource:///chrome/toolkit.jar!/content/global/config.xul
Line Number 1, Column 1:ndTimeoutLength);
^
```
Any ideas? I really need to have this working!

---

### Post by Gandalf on 2005-06-06
[QUOTE=mglukhovsky]I just installed Hoary and went ahead to get backports. Now when I try to access "about:config" I get the following message:
```
XML Parsing Error: syntax error
Location: jar:resource:///chrome/toolkit.jar!/content/global/config.xul
Line Number 1, Column 1:ndTimeoutLength);
^
```
Any ideas? I really need to have this working![/QUOTE]
 yes, you are having this because firefox has not been restarted yet so try either
killall firefox-bin
or reboot your PC

---

### Post by jdong on 2005-06-06
That error's caused by using firefox while it's being updated. Try the already mentioned killall command. If that doesn't work, log out and back in.

---

### Post by desdinova on 2005-06-09
Im getting an issue wit Java freezing firefox for Java Apps - using the UBP version - anyone else seeing it?

---

### Post by j_baer on 2005-06-12
The Backports are generating an error.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)
  MD5Sum mismatch

Any thoughts?

---

### Post by Burgundavia on 2005-06-12
us.archive.ubuntu.com is having some issues.

Corey

---

### Post by dcatdemon on 2005-06-22
[QUOTE=Mike Basinger]My Firefox reset general.useragent.vendorSub switches back to 1.0 when it exits, anyway to stop it from doing that?

Mike[/QUOTE]

You could prevent that by adding this line to your user.js file (located in your $HOME/.mozilla/firefox/xxxxxxxx.default directory).

user_pref("general.useragent.vendorSub","1.0.4");

restart firefox and all will work fine  ;-) .

k-leb.

---

### Post by banditti on 2005-06-29
stupid user question.  What is the package name to install 1.0.4?

---

### Post by sjmorgan on 2005-06-29
[QUOTE=Gandalf]yes, you are having this because firefox has not been restarted yet so try either
killall firefox-bin
or **reboot your PC**[/QUOTE]Shame on you! This is Linux, not Windows.

---

### Post by banditti on 2005-06-29
I don't understand that reply.  Windows doesn't have packages.

---

### Post by MaX on 2005-06-29
[QUOTE=banditti]I don't understand that reply.  Windows doesn't have packages.[/QUOTE]
 You don't need to reboot your PC ever with Linux (for the occasional kernel upgrade you will but)...

---

### Post by banditti on 2005-06-29
Ok.  Maybe I asked my question wrong.  I want to upgrade from 1.0.2 to 1.0.4, what is that package name?  

apt-get install ???????

or maybe

apt-get upgrade ?????

I already have the backports in my sources.list file.


Thanks,

---

### Post by sjmorgan on 2005-06-29
[QUOTE=banditti]Ok.  Maybe I asked my question wrong.  I want to upgrade from 1.0.2 to 1.0.4, what is that package name?[/QUOTE]```
sudo apt-get install firefox
```

---

### Post by banditti on 2005-06-29
Thanks, that worked.....eventually.

I had to remove mozilla-firefox first, then it would go in.

---

