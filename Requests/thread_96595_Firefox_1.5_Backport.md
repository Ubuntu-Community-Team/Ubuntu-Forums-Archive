---
title: "Firefox 1.5 Backport"
date: 2005-11-29
forum: Requests
---

### Post by jdong on 2005-11-29
Today's the big day for Firefox, so I wanna address this before I get flooded with requests for it:

ONE LINE SUMMARY:
It's going to be a while before Firefox 1.5 is officially backported.

RATIONALE
Firefox 1.5 marks a major change in Firefox relative to the 1.0.x series. Backporting this big a change has **never** been done in Backports history, and as a result the migration needs to be treated with care... The new Firefox package threatens compatibility with existing components, from the Ubuntu-bundled  Totem plugins to user installed extensions and system locale packages. In addition, how security updates to the Firefox 1.5 series needs to be addresses, as it seems like the Ubuntu security team will try their best to avoid backporting 1.5 themselves (IMO a very good decision for stability/compatibility reasons).



The backporting of Firefox needs to be done in stages. First off, there will be **NO EXPERIMENTAL PACKAGES** released before 1.5 final is in Dapper. 

After that, there will be a rough closed-door experimentation time by Backports team members to make sure the Dapper packages do not break any system too extensively. 

Third, the Backports team will release experimental packages for early adopters and testers once the Dapper packages are confirmed not to be too dangerous...

Finally, if all goes well, Firefox 1.5 will be filed to James Troup for backporting


This thread is locked and only updated by me periodically to keep you guys informed on our process. You can subscribe to this thread if you're really obsessive-compulsive about it...



**FINAL FINAL FINAL UPDATE**:

A backport will not be done for Firefox 1.5 because of compatibility issues with introducing a new browser, both to the rest of the Ubuntu Breezy platform and to users with heavily customized Firefox setups.

Those who wish to use Firefox 1.5 are encouraged to download official binaries from mozilla.com and unpack them into their home directories -- a very simple, pure graphical process.

---

### Post by GothicX on 2005-11-29
[http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/)

It's already there =)

---

### Post by jdong on 2005-11-29
Please read the post before replying... I said that there will be nothing until it is in **DAPPER**.

---

### Post by akurashy on 2005-11-29
Good luck backporting it (to the team :D)

---

### Post by yaztromo on 2005-11-29
Gah! Windows users get all the fun first :(

---

### Post by jdong on 2005-11-29
UPDATE 1: 1.5 released today, identical to rc3.

1.5RC3 Dapper packages still not perfectly stable, and also currently evaluating exactly what packages I need to recompile...


UPDATE 2: Prelim list
UPDATE 3: Final list of source package depending on Firefox:

```

jdong@shuttle:~$ (apt-cache rdepends firefox && apt-cache rdepends mozilla-firefox) | sed 's/ //g;s/^|//g;' | sort | grep -v "^ReverseDepends" | sort | uniq | xargs apt-cache showsrc | grep "^Package" | sed 's/Package: //g' | sort | uniq | grep -v "buntu-meta$"
bookmarkbridge
checky
ctxextensions
devhelp
dhelp
diggler
djvulibre
dpkg-www
endeavour
epiphany-browser
epydoc
firefox
flashplugin-nonfree
galeon
gecko-sharp
gecko-sharp2
gnome-app-install
j2se1.4-amd64
j2se1.4-i586
librsvg2
liferea
livehttpheaders
meta-j2re1.4-mozilla
mozilla-bonobo
mozilla-firefox-locale-all
mozilla-firefox-locale-ar
mozilla-firefox-locale-ca
mozilla-firefox-locale-el
mozilla-firefox-locale-eu
mozilla-firefox-locale-it
mozilla-firefox-locale-ja
mozilla-firefox-locale-ko
mozilla-firefox-locale-nb
mozilla-firefox-locale-tr
mozilla-firefox-locale-uk
mozilla-mozgest
mozilla-stumbleupon
mozilla-thunderbird
mozplugger
mplayerplug-in
nip2
nukeimage
nvu
openoffice.org2
openoffice.org2-amd64
tabextensions
venkman
vlc
wysihtml
xfig
yelp

```
51 source packages in total.
Most likely all of these need to be rebuilt to say the least, if they're compatible with 1.5 at the source level at all... I'm hoping people are seeing why backporting Firefox 1.5 is going to be such a major job :)

---

### Post by GTvulse on 2005-11-29
Is it not the policy of the security team to provide the latest Firefox versions as security updates? Remeber the horrid conflicts between Hoary security and backports repositories with Firefox 1.07 some months back...

---

### Post by jdong on 2005-11-29
[QUOTE=dradul]Is it not the policy of the security team to provide the latest Firefox versions as security updates? Remeber the horrid conflicts between Horay security and backports repositories with Firefox 1.07 some months back...[/QUOTE]

OMG don't remind me :)

Security team established a long solid record of backporting changes without incrementing version number (even if the packages were source level equivalent to later upstream version) for nearly 9 months, and all of a sudden one day decided to issue a bumped version starting with Firefox 1.0.6.

That's why this time we're taking it slowly. I've asked devs several times about Security Team's plans for security updates to Firefox for the rest of Breezy's security support cycle, and have yet to receive official word, though peers tell me that they will fight importing 1.5 to breezy-security to the death basically...

That'll be something decided between phase 2 and 3.

---

### Post by zero0w on 2005-11-29
I am also interested in a Firefox 1.5 backport for Ubuntu Breezy, now that the official 1.5 version is out.

Will we see an official backport of this **important updates** used by thousands of web surfers using Ubuntu Linux?

---

### Post by zero0w on 2005-11-29
Thanks for the care and attention to detail on taking this backport project.
Keep up the good work.

---

### Post by GTvulse on 2005-11-29
> **jdong]OMG don't remind me :)
[/quote]
That's what Devil's advocates are for.  said:**
> 
Security team established a long solid record of backporting changes without incrementing version number (even if the packages were source level equivalent to later upstream version) for nearly 9 months, and all of a sudden one day decided to issue a bumped version starting with Firefox 1.0.6.

I still have the feeling that was a marketing move. But the "you are using an oudated browser yaddayadda" at mozilla.org's web sites wasn't good press either, most Ubuntu users are getting their feet wet with Linux and don't understand the point of view of a responsible software engineer (or IT manager as that seems to be the hat I wear these days). That version bump was a quick and effective way to put out some nasty witch roasting bonfires already building at the time[1].
[quote=jdong]
That's why this time we're taking it slowly. I've asked devs several times about Security Team's plans for security updates to Firefox for the rest of Breezy's security support cycle, and have yet to receive official word, though peers tell me that they will fight importing 1.5 to breezy-security to the death basically...

That'll be something decided between phase 2 and 3.[/QUOTE]

*Sigh* Considering the major Gecko ABI changes I can appreciate why the Security Team will stick its guns to the death. The need to update all dependent applications in main and universe would be too draining on the development of Dapper... Cross me fingers.

[1] Like the nice napalm grenade thrown a couple of posts down...

---

### Post by nix4me on 2005-11-29
So far the answer from backports is NO.

nix4me

---

### Post by denzilla on 2005-11-29
This is one of the major sucking points of Linux. The Open source world moves alot faster than the closed world of Microsoft, but if you want to stay on the cutting edge of application updates, you have to use them on a proprietary OS? Not bashing on the Ubuntu Dev team cause its not their fault but I absolutely hate this dependency crap about Linux.

---

### Post by strikeforce on 2005-11-29
[QUOTE=denzilla]This is one of the major sucking points of Linux. The Open source world moves alot faster than the closed world of Microsoft, but if you want to stay on the cutting edge of application updates, you have to use them on a proprietary OS? Not bashing on the Ubuntu Dev team cause its not their fault but I absolutely hate this dependency crap about Linux.[/QUOTE]

The difference is ubuntu try's to make it simpler for you.  If you want to install the latest version you can from source.

However I think the fact of the issues is that you will have to wait.  A lot of other packages will need to be rebuilt at the same time.  You have to remember Microsoft doesn't generaly update anything for a few years where as ubuntu updates every 6 months.

I'm not trying to bag Microsoft but the comparisons are not a fair appraisal.  The OS itself is stagnant and thats why upgraded packages can be installed where as linux is constantly changing and growing and thats the reason behind a multitude of package revisions when a major upgrade is done.

---

### Post by stray on 2005-11-29
I'm a little fuzzy on the whole "backports" thing. Is Firefox 1.5 on Breezy Badger considered a backport if Breezy is the latest version of the operating system?

---

### Post by Kuolio on 2005-11-30
[QUOTE=stray]I'm a little fuzzy on the whole "backports" thing. Is Firefox 1.5 on Breezy Badger considered a backport if Breezy is the latest version of the operating system?[/QUOTE]

Backports are newer program releases than those that come with Breezy and they are "backported features" from unstable version. Current stable Ubuntu release is Breezy. Backports come from the unstable, and that is atm. Dapper Drake. Unstable generaly means the "development" version, and they get all the goodies first (bleedingedge).

So, I summarize in my mind backports as "Porting the bleedingedge apps from unstable to stable in a safe and tested way."

In six months DD will be stable, and backports will be coming from from DD+1 (unstable).

---

### Post by doclivingston on 2005-11-30
[QUOTE=zero0w]I am also interested in a Firefox 1.5 backport for Ubuntu Breezy, now that the official 1.5 version is out.

Will we see an official backport of this **important updates** used by thousands of web surfers using Ubuntu Linux?[/QUOTE]

It won't be backported any time soon because they will also need to backport and heavily test at around 25 other packages that depend on Firefox for Gecko.

**Edit**: previously linked to the thread I've moved these posts to. --aysiu

---

### Post by jdong on 2005-11-30
There is a marked difference between how Windows and *nix handle applications... *nix has a lot more of the intertwining dependency effect, like yelp (GNOME Help) depending on Firefox, and so on. Windows would ship a version of Firefox at 25MB bundled with every program that could use it. There are two disadvantages to the Windows approach:

(1) Size -- every program bundles overlapping DLL's. Pointless, should be OS-managed... Ever wondered why Windows programs are so huge?
(2) Security -- Take the zlib vulnerability a few months back. Linux needed ONE library update, and every program on the system using zlib is protected. However, what about Windows? Each program bundles its own zlib, and as a result hundreds of applications developers had to release updates... IE, Acrobat Reader, you name it.


---

Anyway, **Firefox 1.5 RC3 debs are being uploaded to Sourceforge**.... Again, these are **EXPERIMENTAL QUALITY** packages for those of you who are obsessive-compulsive about updating your browsers... Note that the applications in my last post will be **BROKEN** by the update, and need recompiling... Locales probably will not install.

[http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041)

---

### Post by jdong on 2005-11-30
**UPDATE 4: ** source package list was inaccurately generated; did not take into account binary packages with same package names as sources...

Now, our total source rebuild count is up to 51.

---

### Post by vassie on 2005-11-30
AFAIK RC3 is the same as 1.5 Final, the Windows version of 1.5RC3 & 1.5 have the same MD5 hash
I don't know if this is the case for Linux
Please correct me if I am wrong
Ben

---

### Post by veloct on 2005-11-30
it is the same as RC3 for all platforms

---

### Post by stray on 2005-11-30
I suppose the next question is, will Ff1.5 RC3 automagically update to 1.5 full?

---

### Post by jdong on 2005-11-30
[QUOTE=stray]I suppose the next question is, will Ff1.5 RC3 automagically update to 1.5 full?[/QUOTE]
There *is* no update because there is no difference!

Look at your RC3, everything indicates that it's 1.5.

---

### Post by jasplund on 2005-11-30
So we have to live with the flickering menus? and that closing a tab with middle-click doesn't work?

---

### Post by farib on 2005-11-30
[QUOTE=jdong][...][/QUOTE]

(This is not a criticism, just a question)


Why do packages such as mplayerplugin, mozplugger, etc... do need to be repackaged ?

can't the just have a <= dependency upon mozilla-firefox  ?

---

### Post by GeneralZod on 2005-11-30
Just out of interest, once you have the initial backport of 1.5 up and running, how much of an effort will it be to backport each subsequent security fix? Is it just a case of applying the source patches direct from the Mozilla devs and re-building and testing, or is it much more involved than that? Generally speaking, is it signicantly easier to *maintain* a package than to create one from scratch?  Cheers!

---

### Post by tebibyte on 2005-11-30
Why can't the firefox team take some responsibility? It's their department to kick IE's butt, not ours. IF they want us to use firefox, then THEY should have to work for it too, WITH the Ubuntu community :)  What do you all think? :confused: 

Disclaimer: This person is a complete newbie, and has no idea how the structure of the open source communities operate.

---

### Post by jdong on 2005-11-30
[QUOTE=jasplund]So we have to live with the flickering menus? and that closing a tab with middle-click doesn't work?[/QUOTE]

File a bug report in bugzilla.ubuntu.com against the flickering menus... And go to about:config, turn off middleclick.contentloadURL and middle click works again :)


The upstream sources at mozilla.org are final, not the Ubuntu packages :)

---

### Post by nozdormu on 2005-11-30
[QUOTE=jdong]File a bug report in bugzilla.ubuntu.com against the flickering menus... And go to about:config, turn off middleclick.contentloadURL and middle click works again :)


The upstream sources at mozilla.org are final, not the Ubuntu packages :)[/QUOTE]

There already is a bug filed for this problem (which I have by the way):
[https://bugzilla.mozilla.org/show_bug.cgi?id=306426]("https://bugzilla.mozilla.org/show_bug.cgi?id=306426")
Unfortunately, despite being extremely annoying, no one seems to be taking care of  it.

---

### Post by jdong on 2005-11-30
Thanks... Note that since this is not a show-stopper bug (minor annoyance), it's understandable that they wouldn't delay the release of FF 1.5 for it... Otherwise you end up with the Debian fixing-minor-bugs-for-3-years-per-release effect, and people get equally ticked :)


Anyway, the bug does have a patch available, and I'll see if I can get our Ubuntu devs to include the patch.

UPDATE: [http://bugzilla.ubuntu.com/show_bug.cgi?id=20326](http://bugzilla.ubuntu.com/show_bug.cgi?id=20326) Filed Ubuntu bug.

---

### Post by ubuntu27 on 2005-11-30
I just want to say a word to Ubuntu Backport team and the Dev.

Keep up your good work. I love you guys :KS   You are the best.
Just take your time :)

---

### Post by Daedalus on 2005-12-01
Firefox 1.5 RC 3 is avaible on Dapper repositories ([http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/)](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/)). Why the same cannot be done in Breezy? It only differs in three packages.

---

### Post by ember on 2005-12-01
Because there are a couple of packages that depend on firefox and will break in breezy because of the newer firefox version.

---

### Post by Niomi on 2005-12-01
I just wanted to say that I really appreciate your hard work. I will be watching for 1.5 to show up in the repositories!

---

### Post by jdong on 2005-12-01
[QUOTE=Daedalus]Firefox 1.5 RC 3 is avaible on Dapper repositories ([http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/)](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/)). Why the same cannot be done in Breezy? It only differs in three packages.[/QUOTE]

A couple posts up, I did post SourceForge URLS to where you can get that package backported to Breezy. I also posted a list of 50+ package source archives that need to be recompiled in order for Firefox to run without breakage.

---

### Post by clayasaurus on 2005-12-01
I just downloaded firefox 1.5 from the mozilla site and it works fine on breezy. I don't see what the big deal is.

---

### Post by tenshu on 2005-12-01
And what would happen if a major security hole is discovered in 1.0.7 ?

---

### Post by GTvulse on 2005-12-01
[QUOTE=tenshu]And what would happen if a major security hole is discovered in 1.0.7 ?[/QUOTE]

The Security Team would backport the proper fix and release a patched package. Considering that the actual version installed in your computer is 1.0.7-0ubuntu20 you can be sure that has already happened more than once.

---

### Post by kiddo on 2005-12-01
Hi all, I just wanted to drop by the fact that I am an epiphany user mainly because Firefox 1.0.x series were such a performance hog, and I decided to give 1.5 a try.

I accidentally clicked the download link on mozilla's website actually (honest!) and found out that it was simply a tar.gz containing the firefox directory. That meant a simple install just like in my old firebird on windows days! :) so if you guys need it, although this is not going to install it system-wide, you can just extract that somewhere and run "firefox" (that's the name of the executable) inside that folder. Making a gnome launcher for that took me only a few seconds. And I have to say I'm impressed by the speed. It no longer lags while switching tabs.

---

### Post by duffman25 on 2005-12-01
[QUOTE=kiddo]Hi all, I just wanted to drop by the fact that I am an epiphany user mainly because Firefox 1.0.x series were such a performance hog, and I decided to give 1.5 a try.

I accidentally clicked the download link on mozilla's website actually (honest!) and found out that it was simply a tar.gz containing the firefox directory. That meant a simple install just like in my old firebird on windows days! :) so if you guys need it, although this is not going to install it system-wide, you can just extract that somewhere and run "firefox" (that's the name of the executable) inside that folder. Making a gnome launcher for that took me only a few seconds. And I have to say I'm impressed by the speed. It no longer lags while switching tabs.[/QUOTE]

you also need to have libstdc++5 installed.
```

sudo aptitude update
sudo aptitude install libstdc++5

```

---

### Post by siimo on 2005-12-01
[QUOTE=tebibyte]Why can't the firefox team take some responsibility? It's their department to kick IE's butt, not ours. IF they want us to use firefox, then THEY should have to work for it too, WITH the Ubuntu community :)  What do you all think? :confused: 

Disclaimer: This person is a complete newbie, and has no idea how the structure of the open source communities operate.[/QUOTE]
Umm, they already provide binaries that can be used perfectly fine with ubuntu?.  All you have to do is one command :D like this one:

```
cd /tmp && wget -c http://tinyurl.com/8wfs2  &&  cd /opt && tar -xzf /tmp/firefox-1.5.tar.gz  && ln -s /opt/firefox/firefox /usr/bin/firefox1.5
```

(you need to have libstdc++5 installed thats available in apt)
Note: the tinyurl simply points to ftp.mozilla.org try it out in your browser if you don't trust me. It's just there to stop this command wrapping onto two lines on irc. 

and then type firefox1.5 to launch it or creat your own shortcuts :???: .  Don't understand why you need a backport!  This way your 1.0.7 will still be there and all apps that depend on it will continue to function.

---

### Post by jdong on 2005-12-01
Yes, the Mozilla.org binary is **extremely** easy to install and use! Backports deals more with replacing the browser with Firefox 1.5 systemwide in the way that Dapper will implement Firefox 1.5...

To answer a few questions raised:
> 
What will happen if a security issue is uncovered in 1.0.7?


This situation is simple. There are two possibilities:

(1) It's unclear if Mozilla will continue supporting the 1.0.x series ("Aviary"), but most likely patches will continue to be developed for Aviary for quite some time. In this case, a 1.0.8 release would be made by Mozilla's security team, and Security team will "backport" 1.0.8 to Breezy, Hoary, and Warty like they've been doing with the point releases from 1.0.6 on.

(2) If Mozilla does not support the Aviary branch anymore, then patches will likely be made FOR Aviary by a Linux vendor, whether it's Ubuntu or another vendor with strict backporting policies (i.e. SuSE/Novell, RHEL, most of the other enterprise-oriented distros). That'll get backported to all security-supported Ubuntu distros, as a point release like other security updates for Ubuntu. (ie 1.0.7-0ubuntu20.1, 20.2, etc)

(3) If no patches can be made, worse comes to worse, Security team will be forced to make a Firefox 1.5 backport. I do NOT see much changes of this happening through Breezy's lifespan... as other Linux vendors have pulled off backporting patches / making patches for much longer than 18 months!



Now, the important question to ask is, what will happen if Firefox **1.5** develops a security hole after it's backported?

Well, this one is uncertain. Mozilla will release 1.5.1, 1.5.2, etc. Ubuntu Security team is out of the picture, since they do not support the Backports branch. That means the burden is on the Backports team to provide these updates. Remember the backports policy: it has to be in Dapper, it has to be buildable verbatim. How long will it take for Ubuntu Firefox team to get the package in Dapper? **I don't know**. Will the package still build under Breezy? **I don't know**. Furthermore, look at 15 months down the road? Will it still be possible to backport packages from Dapper+2 to *Breezy* to fix more Firefox holes? Just for reference, right now 85+% of the current backports requests do not build under Warty, and around 50% do not build under Hoary.


Choosing to backport Firefox 1.5 is a long lasting decision that has consequences for years down the road. It needs to be done carefully.

---

### Post by siimo on 2005-12-01
[QUOTE=jdong]Yes, the Mozilla.org binary is **extremely** easy to install and use! Backports deals more with replacing the browser with Firefox 1.5 systemwide in the way that Dapper will implement Firefox 1.5...

To answer a few questions raised:


This situation is simple. There are two possibilities:

(1) It's unclear if Mozilla will continue supporting the 1.0.x series ("Aviary"), but most likely patches will continue to be developed for Aviary for quite some time. In this case, a 1.0.8 release would be made by Mozilla's security team, and Security team will "backport" 1.0.8 to Breezy, Hoary, and Warty like they've been doing with the point releases from 1.0.6 on.

(2) If Mozilla does not support the Aviary branch anymore, then patches will likely be made FOR Aviary by a Linux vendor, whether it's Ubuntu or another vendor with strict backporting policies (i.e. SuSE/Novell, RHEL, most of the other enterprise-oriented distros). That'll get backported to all security-supported Ubuntu distros, as a point release like other security updates for Ubuntu. (ie 1.0.7-0ubuntu20.1, 20.2, etc)

(3) If no patches can be made, worse comes to worse, Security team will be forced to make a Firefox 1.5 backport. I do NOT see much changes of this happening through Breezy's lifespan... as other Linux vendors have pulled off backporting patches / making patches for much longer than 18 months!



Now, the important question to ask is, what will happen if Firefox **1.5** develops a security hole after it's backported?

Well, this one is uncertain. Mozilla will release 1.5.1, 1.5.2, etc. Ubuntu Security team is out of the picture, since they do not support the Backports branch. That means the burden is on the Backports team to provide these updates. Remember the backports policy: it has to be in Dapper, it has to be buildable verbatim. How long will it take for Ubuntu Firefox team to get the package in Dapper? **I don't know**. Will the package still build under Breezy? **I don't know**. Furthermore, look at 15 months down the road? Will it still be possible to backport packages from Dapper+2 to *Breezy* to fix more Firefox holes? Just for reference, right now 85+% of the current backports requests do not build under Warty, and around 50% do not build under Hoary.


Choosing to backport Firefox 1.5 is a long lasting decision that has consequences for years down the road. It needs to be done carefully.[/QUOTE]
I've heard the security releases will be 1.5.0.1  1.5.0.2 etc.  Don't ask me why...

---

### Post by duffman25 on 2005-12-01
[QUOTE=jdong]Yes, the Mozilla.org binary is **extremely** easy to install and use! Backports deals more with replacing the browser with Firefox 1.5 systemwide in the way that Dapper will implement Firefox 1.5...

To answer a few questions raised:


This situation is simple. There are two possibilities:

(1) It's unclear if Mozilla will continue supporting the 1.0.x series ("Aviary"), but most likely patches will continue to be developed for Aviary for quite some time. In this case, a 1.0.8 release would be made by Mozilla's security team, and Security team will "backport" 1.0.8 to Breezy, Hoary, and Warty like they've been doing with the point releases from 1.0.6 on.

(2) If Mozilla does not support the Aviary branch anymore, then patches will likely be made FOR Aviary by a Linux vendor, whether it's Ubuntu or another vendor with strict backporting policies (i.e. SuSE/Novell, RHEL, most of the other enterprise-oriented distros). That'll get backported to all security-supported Ubuntu distros, as a point release like other security updates for Ubuntu. (ie 1.0.7-0ubuntu20.1, 20.2, etc)

(3) If no patches can be made, worse comes to worse, Security team will be forced to make a Firefox 1.5 backport. I do NOT see much changes of this happening through Breezy's lifespan... as other Linux vendors have pulled off backporting patches / making patches for much longer than 18 months!



Now, the important question to ask is, what will happen if Firefox **1.5** develops a security hole after it's backported?

Well, this one is uncertain. Mozilla will release 1.5.1, 1.5.2, etc. Ubuntu Security team is out of the picture, since they do not support the Backports branch. That means the burden is on the Backports team to provide these updates. Remember the backports policy: it has to be in Dapper, it has to be buildable verbatim. How long will it take for Ubuntu Firefox team to get the package in Dapper? **I don't know**. Will the package still build under Breezy? **I don't know**. Furthermore, look at 15 months down the road? Will it still be possible to backport packages from Dapper+2 to *Breezy* to fix more Firefox holes? Just for reference, right now 85+% of the current backports requests do not build under Warty, and around 50% do not build under Hoary.


Choosing to backport Firefox 1.5 is a long lasting decision that has consequences for years down the road. It needs to be done carefully.[/QUOTE]

I think mozilla will support the 1.0.x branch for some time... or at least that's what I would try to do.

---

### Post by tenshu on 2005-12-02
[QUOTE=jdong]
(3) If no patches can be made, worse comes to worse, Security team will be forced to make a Firefox 1.5 backport. I do NOT see much changes of this happening through Breezy's lifespan... as other Linux vendors have pulled off backporting patches / making patches for much longer than 18 months!
[/QUOTE]

/me is crossing his fingers

Hope we will have 1.5 backported asap =)

Thank you for your answer jdong

/me go back to translations at launchpad.net

---

### Post by jdong on 2005-12-02
Uploading new experimental 1ubuntu4 package to Sourceforge... Just a backport update to match newest Dapper Firefeox sources. Fixes printer names / spaces issue, a few UI issues.


See [http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041&release_id=375529](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041&release_id=375529)

**IMPORTANT**: The same "this is experimental and requires many things to be recompiled" warning still applies!

---

### Post by zero0w on 2005-12-03
[QUOTE=jdong]Uploading new experimental 1ubuntu4 package to Sourceforge... Just a backport update to match newest Dapper Firefeox sources. Fixes printer names / spaces issue, a few UI issues.


See [http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041&release_id=375529](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=171041&release_id=375529)

**IMPORTANT**: The same "this is experimental and requires many things to be recompiled" warning still applies![/QUOTE]

Is it really a Bzip2 (bz2) file?
Because I am unable to extract and install it.

---

### Post by jdong on 2005-12-03
Yes, it's a tar.bz2 file, that opens fine with both tar xjvf and file roller (the GNOME archive manager)

Inside are all the debs associated with Firefox.

---

### Post by jdong on 2005-12-03
**UPDATE**:

Clearly the Dapper Firefox 1.5 package still suffers from issues here and there, primarily UI related, though some developers still inform me that there are packaging problems / disagreements. We are going to have to wait for those to settle.

---

### Post by TmP on 2005-12-05
Hi!
I noticed you didn't mention the polish language localisation among the packages you're workin on. Could you please include it?

I can give you a hand when it comes to translation ( although I'm only a rooky at programming...)

Thanx for your effort to bring it into Ubuntu!

---

### Post by ryanov on 2005-12-05
Tried the experimental backport that you posted a few items up. Everything works great, except the text in the toolbars (status bar, menus, bookmarks, etc.) is all one font size larger than they should be.

I use Kubuntu, not Ubuntu... Not sure whether this package (calls itself Deer Park) is using the Qt theme for GTK+ or not like it ought to be. I'm guessing not, but that's probably because it is experimental.

---

### Post by pbb on 2005-12-06
[QUOTE=siimo]All you have to do is one command :D like this one:

```
cd /tmp && wget -c http://tinyurl.com/8wfs2  &&  cd /opt && tar -xzf /tmp/firefox-1.5.tar.gz  && ln -s /opt/firefox/firefox /usr/bin/firefox1.5
```

(you need to have libstdc++5 installed thats available in apt)[/QUOTE]

Siimo, thanks a million! Your simple explaination helped this total newbie to install Firefox 1.5.
Two remarks however:
* Some of these command require root privileges. I don't know how that could be done in your concatenated line, I just issued those commands seperately with sudo.
* The link created doesn't work, you will get the following error:
```
run-mozilla.sh: Cannot execute /opt/firefox/firefox1.5-bin.
```
I managed to deduct that this had to do with the filename of the link. When you first rename or delete the original Firefox link, and then link to 1.5 using the name "firefox", everything works great. (PLUS, your shortcuts in the Gnome menu will point to the new version.)

---

### Post by mattisking on 2005-12-06
blam should probably be in there, too.

---

### Post by amokoura on 2005-12-07
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

as Fishfork said: "How to do it without messing up your system and confusing the package manager (hopefully!)".

I got it easily working.

---

### Post by Serzholino on 2005-12-07
Experimental build crashes on weather.com site when mouse scloll.

P.S.: I'm using Kubuntu

---

### Post by ryanov on 2005-12-07
The only thing that doesn't really work for me so far is the download manager. It's blank. The Windows build has crashed for me several times already, and it's a RELEASED package. :)

---

### Post by darne on 2005-12-09
[QUOTE=ryanov]The only thing that doesn't really work for me so far is the download manager. It's blank. The Windows build has crashed for me several times already, and it's a RELEASED package. :)[/QUOTE]

I get that on 1.0.4.  Assuming it's a config thing, but could never be bothered to look into it as I usually use other download managers.

---

### Post by jdong on 2005-12-09
[QUOTE=darne]I get that on 1.0.4.  Assuming it's a config thing, but could never be bothered to look into it as I usually use other download managers.[/QUOTE]

I've found that the Download Tweak Extension is often the cause of this. It's a very poorly written extension that never uninstalls cleanly. Usually, starting with a fresh profile directory is the best way to resolve this, unless you want to spend a few hours grepping and removing references to the extension in your profile.

---

### Post by darne on 2005-12-10
[QUOTE=jdong]I've found that the Download Tweak Extension is often the cause of this. It's a very poorly written extension that never uninstalls cleanly. Usually, starting with a fresh profile directory is the best way to resolve this, unless you want to spend a few hours grepping and removing references to the extension in your profile.[/QUOTE]

Thanks.  I think I did install that before using an external prog.

---

### Post by Ultraviolence on 2005-12-10
Does [Drudge Report]("http://www.drudgereport.com") freeze anyone else's Firefox 1.5? Using the Firefox 1.07 that is in the repository, it does not freeze, but when I open it with the 1.5 from mozilla.org (followed the instructions to install it on the Ubuntu Wiki) and it not only freezes Firefox but also X.

---

### Post by foxy123 on 2005-12-10
[QUOTE=Ultraviolence]Does [Drudge Report]("http://www.drudgereport.com") freeze anyone else's Firefox 1.5? Using the Firefox 1.07 that is in the repository, it does not freeze, but when I open it with the 1.5 from mozilla.org (followed the instructions to install it on the Ubuntu Wiki) and it not only freezes Firefox but also X.[/QUOTE]
no...

---

### Post by jdong on 2005-12-10
Works fine with the experimental .deb package.

---

### Post by veloct on 2005-12-10
[QUOTE=Ultraviolence]Does [Drudge Report]("http://www.drudgereport.com") freeze anyone else's Firefox 1.5? Using the Firefox 1.07 that is in the repository, it does not freeze, but when I open it with the 1.5 from mozilla.org (followed the instructions to install it on the Ubuntu Wiki) and it not only freezes Firefox but also X.[/QUOTE]

Works fine here on 1.5

---

### Post by Ultraviolence on 2005-12-10
I just installed the experimental deb and it doesn't freeze on that.

Why is the experimental deb Deer Park? Is it an earlier version of 1.5?

---

### Post by kleeman on 2005-12-10
Doesn't freeze for me with 1.5 (pity really :razz: )

---

### Post by jdong on 2005-12-10
[QUOTE=Ultraviolence]I just installed the experimental deb and it doesn't freeze on that.

Why is the experimental deb Deer Park? Is it an earlier version of 1.5?[/QUOTE]

The name stuck and never changed in Debian Experimental (where this package was initially made). It signifies NO change in functionality.

This is Firefox 1.5rc3, which is source equivalent to 1.5 final, plus Ubuntu and Debian patches.

---

### Post by segfaulty on 2005-12-11
Hi!

BTW: The expermental packages works fine here to, but I breaks devhelp (and maybe some other packages depending on the mozilla-libs).

Regards,
Johannes

---

### Post by jdong on 2005-12-11
I'm going to commence a rebuild of the affected packages soon and see how that works.

---

### Post by Greg T. on 2005-12-11
There is a patch to the resolve the flickering bookmarks menu problem... [https://bugzilla.mozilla.org/show_bug.cgi?id=306426](https://bugzilla.mozilla.org/show_bug.cgi?id=306426). It has yet to be approved, so it's not in the nightly builds, let alone the next official release version (1.5.1).

Mozilla wanted to hit their dates, so they didn't attempt to get this difficult-to-reproduce bug resolved before they released 1.5. However, this is a significant bug, and getting the patch included in the Ubuntu backport version of 1.5 would be *very* welcome, indeed.

---

### Post by jdong on 2005-12-11
I filed a bugzilla request at Ubuntu to take a look at that patch. No answer yet.

---

### Post by ryanov on 2005-12-12
[QUOTE=jdong]I've found that the Download Tweak Extension is often the cause of this. It's a very poorly written extension that never uninstalls cleanly. Usually, starting with a fresh profile directory is the best way to resolve this, unless you want to spend a few hours grepping and removing references to the extension in your profile.[/QUOTE]

Couldn't be my problem, though... I never had it... < shrug > might start with a fresh profile anyway.

The other issue I now have is that Thunderbird will not open Firefox when I click on a link. I don't see anyplace to set this in Firefox, so I'm not sure where that comes from.

---

### Post by NeoChaosX on 2005-12-12
Question: what kind of dialogs are opping up for opening and saving files? Is it the default Mozilla dialogs, or is it the GNOME file dialogs? I'm using FF in Kubuntu and it's annoying me to death how the Ubuntu package for FF uses the GTK/GNOME file dialogs even in KDE.

---

### Post by angrykeyboarder on 2005-12-12
[quote=jdong]OMG don't remind me :)
Security team established a long solid record of backporting changes without incrementing version number (even if the packages were source level equivalent to later upstream version) for nearly 9 months, and all of a sudden one day decided to issue a bumped version starting with Firefox 1.0.6..[/quote] 
They got a stroke of common sense perhaps?  What they were doing before only made sense to them.  The rest of us were confused as hell.  addons.mozilla.org was confused too.

Apparently that change took a while to make it to the "Things we do better than Debian" list.  I was glad it did.

Obviously some pocket-protector types weren't happy, but since I'm not one of them...  ;-)

BTW, people.....

[CENTER]*Who* dictates what software *you* use?  Your Linux distribution or **YOU?**

[[IMG]http://sfx-images.mozilla.org/affiliates/products/firefox/upgrade_1_5_468b1.jpg[/IMG]]("http://www.spreadfirefox.com/?q=affiliates&id=281&t=202")

[getfirefox.com]("http://ubuntuforums.org/%3Ca%20href=%22http://www.spreadfirefox.com/?q=affiliates&id=281&t=1%22%3E%3Ctextarea%20rows=%223%22%20cols=%2240%22%3E%3Ca%20href=%22http://www.spreadfirefox.com/?q=affiliates&id=281&t=1%22%3EGet%20Firefox%21%3C/a%3E")[/CENTER]

---

### Post by kleeman on 2005-12-12
Yeah but abrupt changes in versioning numbers makes the life of a backporter a little difficult.

---

### Post by jdong on 2005-12-12
Guys -- for now, I recommend unpacking an official 1.5 tarball to somewhere (/opt, home directory, etc) and running it from there if you want Firefox 1.5.

No matter how much I recompile everything, Backports is still going to introduce a dramatic ABI change by replacing the system Firefox version, disrupting 3rd party packages targeted at Ubuntu, not to mention the innocent bystander who has an ultra-customized Firefox profile.

In addition, the Ubuntu 1.5 package still appears to have some weird issues that I cannot explain, like some of my settings will magically revert, bookmarks magically disappear, etc.


Since extracting Firefox tarballs from mozilla.com can be done in pure GUI, I think that's a reasonably simple way of getting the job done.


Thanks for understanding and being considerate of others.

---

### Post by kleeman on 2005-12-12
Sounds very sensible to me jdong. I did that as soon as 1.5 came out. The only fiddle needed was transfering the plugins into the new firefox/plugins directory. Really very easy. All my prefs went over without problem. A couple of minor extensions did not work but they weren't going to anyway.

---

### Post by pt123 on 2005-12-13
Wow who would have thought Firefox would lead me to use Windows.

---

### Post by kleeman on 2005-12-13
[QUOTE=pt123]Wow who would have thought Firefox would lead me to use Windows.[/QUOTE]
You're kidding right? Hey Internet Exploder is just a click away now.

---

### Post by kaaredyret on 2005-12-14
[QUOTE=kleeman]You're kidding right? Hey Internet Explorer is just a click away now.[/QUOTE]

Hehe, no **on Windows FIREFOX 1.5 is just a simple click or two away**: download, click on install, done! ;) 

(Writing this from my Windows box)

---

### Post by ember on 2005-12-14
On Linux:
Download - Unpack - Install - Done ... not too hard, eh? ;)

Anyway I can't understand why all people are rushing to 1.5 now - there are a lot of extensions which do not work with it at the moment and Firefox 1.0.7 does not become worse as soon as there is a new version.

Best,
ember

---

### Post by foxy123 on 2005-12-14
[QUOTE=ember]On Linux:
Download - Unpack - Install - Done ... not too hard, eh? ;)

Anyway I can't understand why all people are rushing to 1.5 now - there are a lot of extensions which do not work with it at the moment and Firefox 1.0.7 does not become worse as soon as there is a new version.

Best,
ember[/QUOTE]
1.5 is faster... all extensions I usually use work fine with 1.5...

---

### Post by GothicX on 2005-12-14
And you can do some hack to put extensions working... like this one:

[http://www.lifehacker.com/software/firefox/make-extensions-work-in-firefox-15-136993.php](http://www.lifehacker.com/software/firefox/make-extensions-work-in-firefox-15-136993.php)

:-) have a nice day

---

### Post by ember on 2005-12-14
[QUOTE=foxy123]1.5 is faster... all extensions I usually use work fine with 1.5...[/QUOTE]

For me it did not seem faster (tested on Windows). 
And additionally, I use a lot of extensions (;)) and prefer to have them in german - maybe it's possible to have Firefox 1.5 running the way 1.0.7 does for me, yet I guess, I'll wait for 1.5.1, which will surely come.

Best,
ember

---

### Post by jdong on 2005-12-14
Under Breezy, Firefox 1.5 WILL render significantly faster than 1.0.7.

---

### Post by prizrak on 2005-12-15
Yeah aviary BLOWS under Breezy, but the 1.5 breaks my flash sound which is not a tradeoff I'm willing to take. Will wait for Dapper not that long of a wait anyways :)

---

### Post by ember on 2005-12-15
Does it only break the flash-sound or the whole flash thing?

---

### Post by dguido on 2005-12-15
Instead of all this useless chatter, can someone from backports please tell us how we can help test the Firefox1.5 deb package you're developing?

Also, where we can get status updates on your progress?

---

### Post by jdong on 2005-12-15
(1) [http://ubuntuforums.org/showpost.php?p=566619&postcount=75](http://ubuntuforums.org/showpost.php?p=566619&postcount=75) -- My decision on Firefox backport. It's not going to be done.

---

### Post by kaaredyret on 2005-12-15
[QUOTE=ember]On Linux:
Download - Unpack - Install - Done ... not too hard, eh?
[/QUOTE]

Never worked on Hoary for me :(

I just wait for the update for breezy, no ugly or tricky hacks pls

:)

---

### Post by GeneralZod on 2005-12-15
[QUOTE=jdong](1) [http://ubuntuforums.org/showpost.php?p=566619&postcount=75](http://ubuntuforums.org/showpost.php?p=566619&postcount=75) -- My decision on Firefox backport. It's not going to be done.[/QUOTE]

Might be a good idea to edit this into the first post for the benefit of newcomers :)

---

### Post by sadiini on 2005-12-16
[QUOTE=kaaredyret]Never worked on Hoary for me :(

I just wait for the update for breezy, no ugly or tricky hacks pls

:)[/QUOTE]
Take the source. Compile and install it. And that`s it! No monkeybusiness :D
It works! All my extentions and bookmarks are fine and in the right places after intall. 
Firefox 1.5 is Faster :)

---

### Post by foxy123 on 2005-12-16
[QUOTE=sadiini]Take the source. Compile and install it. And that`s it! No monkeybusiness :D
It works! All my extentions and bookmarks are fine and in the right places after intall. 
Firefox 1.5 is Faster :)[/QUOTE]
there is no need to compile it... I saw a topic about FF1.5 install script here in howtos and there is another topic about how to do it manually. But basically you extract the archive and use it from there...

---

### Post by sadiini on 2005-12-16
[QUOTE=foxy123]there is no need to compile it... I saw a topic about FF1.5 install script here in howtos and there is another topic about how to do it manually. But basically you extract the archive and use it from there...[/QUOTE]
My mistake!!!
Very true!
And that`s the case. 
Sorry! Anyway, I am pleased using 1.5.

---

### Post by dcstar on 2005-12-23
[QUOTE=jdong](1) [http://ubuntuforums.org/showpost.php?p=566619&postcount=75](http://ubuntuforums.org/showpost.php?p=566619&postcount=75) -- My decision on Firefox backport. It's not going to be done.[/QUOTE]
Having read the reasons, this makes a lot of sense, but can I ask one thing:

One the assumption that a FF 1.5 "backport" replaces too many existing code/compatibility links, would it be possible to just have a compiled FF 1.5 package in the repositories that basically doesn't replace/break any existing stuff, but just installs and provides the new FF 1.5 software as a separate entity?

If this is possible, then it may provide the proverbial "Best of both worlds" (and save the numerous "How do I install/I have problems with FF 1.5" posts in the other forums).

---

### Post by zbowling on 2005-12-24
I'm running firefox 1.5 on Ubuntu. Not necissarly a backport though. I'm running on x86_64 so there is not an offical installer for my platform, but I build mozilla's trunk all the time for development on gtkembedmoz for gecko# since I'm a developer on the mono project. All I did was build into /opt/firefox/ and use dpkg-divert and renamed the firefox binary. Pretty simple. That way totem and anything embedding gtkembedmoz can still work but firefox itself could be upgrade. Only thing I have thats different is that since its not an offical build, it says "Deer Park" and the icon is a world and not the real firefox logo. Oh well, not worth hacking the build file to fake an offical build to care.

---

### Post by Corrado on 2005-12-24
[QUOTE=dcstar]...
One the assumption that a FF 1.5 "backport" replaces too many existing code/compatibility links, would it be possible to just have a compiled FF 1.5 package in the repositories that basically doesn't replace/break any existing stuff, but just installs and provides the new FF 1.5 software as a separate entity?
....[/QUOTE]

Yes!!  That is the best solution!!  I vote for building a new repository entry for Firefox 1.5 and letting users install that alongside the "real" version.  :) 

Later...
  Richard

BTW: The fact that a browser is "hard coded" into the environment kind of bugs me.  It makes me feel all Windowish when people say "We can't remove the browser, it's part of the OS!".  :(

---

### Post by foxy123 on 2005-12-24
it is very easy to install FF1.5 from mozilla.org. Honestly, I do not see any point to build a package now. You can use either wiki or a script or Automatix to do it very easy.

---

### Post by dcstar on 2005-12-24
[QUOTE=foxy123]it is very easy to install FF1.5 from mozilla.org. Honestly, I do not see any point to build a package now. You can use either wiki or a script or Automatix to do it very easy.[/QUOTE]
The "point" is that not everyone is either capable, or motivated, or aware of all the extra steps for those options (a glance at the other forums constantly on the topic of FF 1.5 should make that clear).

I keep reading that Ubuntu is supposed to be "human friendly", but until it becomes less reliant on these "propeller-head" solutions (and yes, I am quite capable coming under that category myself), then it is failing in that regard.

If Ubuntu wants to be just another Linux distro where you still have to muck around (and that's after you find them) with fiddly extras just to get something like this installed, then is it achieving what it sets out to do?

---

### Post by foxy123 on 2005-12-24
[QUOTE=dcstar]The "point" is that not everyone is either capable, or motivated, or aware of all the extra steps for those options (a glance at the other forums constantly on the topic of FF 1.5 should make that clear).[/QUOTE]
those can stay with 1.07 which is not very different from 1.5. I still use it on my desktop without any problem.

---

### Post by Corrado on 2005-12-24
[QUOTE=foxy123]those can stay with 1.07 which is not very different from 1.5. I still use it on my desktop without any problem.[/QUOTE]

Yes, I too still use 1.0.7, but again that's not the point.  Firefox 1.5 has some significant improvements, especially memory use on Ubuntu stable as I understand it, as well as new security features.  Telling people to upgrade their whole system to get a new browser sounds like a tactic of that other major operating system.

Just make a package to install Firefox 1.5 in some out of the way location and I think very many people will be very happy.  I know I will.

---

### Post by foxy123 on 2005-12-25
[QUOTE=Corrado]Yes, I too still use 1.0.7, but again that's not the point.  Firefox 1.5 has some significant improvements, especially memory use on Ubuntu stable as I understand it, as well as new security features.  Telling people to upgrade their whole system to get a new browser sounds like a tactic of that other major operating system.

Just make a package to install Firefox 1.5 in some out of the way location and I think very many people will be very happy.  I know I will.[/QUOTE]

yes, it might be a good idea, like it has been done with java or some other non-free package, when you download and execute a script which then download and put the programme in say /opt. Though I am not sure how easy it might be to implement...

---

### Post by jasutton on 2005-12-25
Well, here's a script that I just wrote to do just that.  It's based on the instructions found [here]("https://wiki.ubuntu.com/FirefoxNewVersion").  Make sure you run the script as root (i.e., using sudo).  Anyone that sees something I didn't do right, feel free to correct it and upload a new version. :)

```

#!/bin/bash

cd /opt

# Make sure libstdc++5 (and wget) dependancy has been met
apt-get install libstdc++5 wget

# Download the Firefox Binary archive from Mozilla.org
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz

# Unpack the archive in /opt
tar -zvxf firefox-1.5.tar.gz

# Remove the now un-needed archive file
rm -f firefox-1.5.tar.gz

# Symbolically link the current Firefox plugins to the new Firefox plugins dir
cd /opt/firefox/plugins/
ln -s /usr/lib/mozilla-firefox/plugins/* .

# Remove link to incompatible totem plugin
rm libtotem_mozilla.*

# Move old symlink out of the way
mv /usr/bin/firefox /usr/bin/firefox.ubuntu

# Make sure future Firefox updates (through apt)  don't overwrite the symlink we create
dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

# Create new symlink to Firefox 1.5
ln -s /opt/firefox/firefox /usr/bin/firefox

# Backup a copy of the current Firefox profile
cp -rf ~/.mozilla ~/.mozilla.bak

# Fix Firefox 1.5 problem
touch /opt/firefox/extensions/talkback@mozilla.org/chrome.manifest

# Create an uninstall script
touch /usr/sbin/firefox-1.5-remove
echo dpkg-divert --remove /usr/bin/firefox >> /usr/sbin/firefox-1.5-remove
echo rm -f /usr/bin/firefox >> /usr/sbin/firefox-1.5-remove
echo mv /usr/bin/firefox.ubuntu /usr/bin/firefox >> /usr/sbin/firefox-1.5-remove
echo rm -rf /opt/firefox >> /usr/sbin/firefox-1.5-remove
chmod +x /usr/sbin/firefox-1.5-remove

# Tell the user about uninstalling
echo
echo To uninstall, run 'sudo /usr/sbin/firefox-1.5-remove' 
echo
echo A backup of your profile has been made to ~/.mozilla.bak
echo

# Wait 5 seconds, then exit script
sleep 5s
exit

```

---

### Post by Humanoid on 2005-12-25
I have my own deb here: [http://www.students.oamk.fi/~t3vasa02/ubuntu/]("http://www.students.oamk.fi/~t3vasa02/ubuntu/")

It works ok if you uninstall 1.07 before it..

---

### Post by jdong on 2005-12-25
Building a slotted 1.5 package would not be smart, from my experience, because you **never know** when Debian/Ubuntu devs will make an unexpected packaging change, spelling upgrade headaches for everyone. Seriously -- You can install Firefox 1.5 with a few mouse clicks in your home directory. It's not hard to do!

---

### Post by nousplacidus on 2006-01-02
[QUOTE=yaztromo]Gah! Windows users get all the fun first :([/QUOTE]

thats why it doesn't work properly...

---

### Post by haocheng on 2006-01-03
It took me about 20 minutes to install FF1.5.
And WOW!!! It's SO FAST!!! 
MUCH FASTER than FF 1.07 on Ubuntu.
I would have installed it much earlier if I knew the difference before.

So I suggest that most people should just follow the 
instructions on the wiki to install FF1.5.
It really worths the time you spend :)

---

### Post by jbus on 2006-01-04
***This is not a request, it's a comment***

I can clearly understand from reading this thread that there is some major work to be done before FF1.5 is added to backports. 

But, as a casual linux user that has been recruiting Windows users to Ubuntu/Kubuntu this concerns me that policies that only linux devs and linux gurus understand are going to make things difficult for regular users and make it difficult to update to the latest released version of an application as important as Firefox. I thought ubuntu was supposed to be easy to use???  

This may sound stupid, but in the mean time, why can't a .deb that installs FF1.5 binary from mozilla, without affecting the current Ubuntu Firefox version, be added to the repos??? This would make it simple for casual users and it could be removed later when the backport is complete.

---

### Post by jdong on 2006-01-04
[QUOTE=jbus]
This may sound stupid, but in the mean time, why can't a .deb that installs FF1.5 binary from mozilla, without affecting the current Ubuntu Firefox version, be added to the repos??? This would make it simple for casual users and it could be removed later when the backport is complete.[/QUOTE]

This is a question you'll have to ask Ubuntu developers. I cannot answer it for them, but what you say does make sense. Most likely it's just the amount of work involved to do so, but that's a pretty lousy excuse.

---

### Post by mr_pouit on 2006-01-05
[QUOTE=jbus]This may sound stupid, but in the mean time, why can't a .deb that installs FF1.5 binary from mozilla, without affecting the current Ubuntu Firefox version, be added to the repos??? This would make it simple for casual users and it could be removed later when the backport is complete.[/QUOTE]

On testing purpose, you can make a .deb, using the instructions in the wiki, that installs a binary ff1.5 from mozilla. I tried, but there were lots of issue :
- totem plugin is not working anymore
- thunderbird still opens ff1.0
- no gnome integration
...

so i think it would create more issues than backporting ff1.5 :???:

---

### Post by jbus on 2006-01-05
Well, I sure hope ubuntu figures a way around this type of problem. I like (k)ubuntu's simplicity and ease of use and that's why I have been recommending it to other people, but it does not make sense that users are expected to be stuck with older versions of applications until the next release. This is probably not a problem with minor updates but with a big update on a major app like FF1.5 it seems pretty riduculous that there is not a way around it that is simple for regular users.

The moment I tell my mother, sister, cousin, grand parents and friends to follow instructions on a "wiki" or to install a binary from Mozilla that kills all their plugins in order to upgrade their browsers to the latest version, they are going to be wishing they hadn't switched from Windows.

If I can have a bleeding edge version of SUSE (SLICK) on my laptop that gives me all the latest and greatest software KDE3.5, FF1.5, Etc.... through APT and have the system still continue to WORK, then I'm sure there is a way for a distro as large and popular as ubuntu to offer bleeding edge apps as an option to its users as well. 

At this point using Dapper is clearly not an option if you intend on having a working system. So, isn't there another way this could be accomplished?

---

### Post by jdong on 2006-01-05
[QUOTE=jbus]

The moment I tell my mother, sister, cousin, grand parents and friends to follow instructions on a "wiki" or to install a binary from Mozilla that kills all their plugins in order to upgrade their browsers to the latest version, they are going to be wishing they hadn't switched from Windows.

[/quote]
Umm, that's simply the nature of having dependent ABI's change, and happens on any OS.


> 
If I can have a bleeding edge version of SUSE (SLICK) on my laptop that gives me all the latest and greatest software KDE3.5, FF1.5, Etc.... through APT and have the system still continue to WORK, then I'm sure there is a way for a distro as large and popular as ubuntu to offer bleeding edge apps as an option to its users as well. 

You'll meet a breakage soon. Trust me. It's the same idea as Gentoo.
> 
At this point using Dapper is clearly not an option if you intend on having a working system. So, isn't there another way this could be accomplished?
The integration of a Klick type system into Ubuntu.

---

### Post by macleod199 on 2006-01-06
[QUOTE=jbus]
If I can have a bleeding edge version of SUSE (SLICK) on my laptop that gives me all the latest and greatest software KDE3.5, FF1.5, Etc.... through APT and have the system still continue to WORK, then I'm sure there is a way for a distro as large and popular as ubuntu to offer bleeding edge apps as an option to its users as well. 

At this point using Dapper is clearly not an option if you intend on having a working system. So, isn't there another way this could be accomplished?[/QUOTE]


There's a couple of issues here.

First of all, this is to a large extent Mozilla's fault. When the 0.x releases of Phoenix/Thunderbird started coming out 3+ years ago, much hue and cry was raised about the increased memory size of loading the same rendering engine twice. "Don't worry," Mozilla said, "we're factoring out the common bits as the GRE soon. No problemo." Where is our GRE now? Nowhere. 

While Firefox isn't really as integrated with Linux as IE is with Windows, it's getting close. Anything that needs to render HTML tends to use it's engine to do it, and therefore depends on a certain version of it's API/ABI. Really they only need the GRE, but there's no option to factor that out as of yet, becuase Mozilla abadoned a lot of core rendering engine projects to focus on new features and options and whatnot. I saw several comments from one core developer who was ready to leave the project because his complaints about changes that broke embedded uses of the engine were being ignored.

Once there is a GRE (now spun off into this XULRunner project I don't really understand), it will be a lot easier for standard package based distros to deal with stuff like this. As is Firefox is deep in the system, and it's hard to change it without changing the solar system of packages built up around it. Which a stable distro does not do.


The other issue is Ubuntu's release cycle. It's 6 months, which is pretty freaking fast and not that long to wait for new stable releases of everything, if you ask me. I especially like that they've pinned it to Gnome's release schedule, so you get new releases of Gnome a few weeks after they're released. Not even Gentoo usually has them stable by that point. Projects not tied to Gnome may just slightly miss the release schedule, causing these several month lags.

I'm not sure about SuSe, but AFAIK they're still on a 'when it's ready' release schedule, which has it's own pitfalls. It was apparently a priority for them to get Firefox 1.5 out in a stable release as soon as possible, and they scheduled around it. 

When you're choosing a distro, remember what you're choosing - a distribution. And make sure their distribution priorities coincide with yours, or you're going to be disappointed. The look and feel can be configured away to a large degree, so it's really the most important distinction.

---

### Post by angrykeyboarder on 2006-01-07
[quote=macleod199]There's a couple of issues here.

"Don't worry," Mozilla said, "we're factoring out the common bits as the GRE soon. No problemo." Where is our GRE now? Nowhere.[/quote] 

WI GRE?

While Firefox isn't really as integrated with Linux as IE is with Windows, it's getting close. Anything that needs to render HTML tends to use it's engine to do it, and therefore depends on a certain version of it's API/ABI. 

And therein lies a big problem that needs to be fixed.  No single application should be depended upon by so many other applications.  

What if I have an aversion to Firefox? I should be able to uninstall it.  But based on this, if I do, it will take 16 other applications with it and/or possibly cripple my system.

> The other issue is Ubuntu's release cycle. It's 6 months, which is pretty freaking fast and not that long to wait for new stable releases of everything, if you ask me. 

It depends on one's definition of "stable" I suppose.  There was quite a bit of criticism that Breezy was buggier than usual (in part because it was "rushed" to meet the deadline).

> I especially like that they've pinned it to Gnome's release schedule, so you get new releases of Gnome a few weeks after they're released. Not even Gentoo usually has them stable by that point. Projects not tied to Gnome may just slightly miss the release schedule, causing these several month lags. 
Depending on what the "project" is, users may or may not care, but if it's something major and with lots of publicity (e.g. Firefox,  OpenOffice.org) there's going to be outcry.

Ubuntu was well aware of the release schedule for Firefox and OpenOffice.org they had three options.

1). Ignore it (as they did).

2) Delay release for a month so that they could include Firefox 1.5 and OpenOffice.org  2

3) Update OpenOffice.org and Firefox in the current Ubuntu release (Breezy in this case) when they came out.

#3 Makes the most sense to me, but I could live with #2 as well. 

Personally I'd like to see Ubuntu do that and adopt the Fedora Project's release schedule. It's also every 6 months but it's "approximately" every 6 months..

All they needed was one more month and a lot of us wouldn't be complaining now.

> When you're choosing a distro, remember what you're choosing - a distribution. And make sure their distribution priorities coincide with yours, or you're going to be disappointed. The look and feel can be configured away to a large degree, so it's really the most important distinction. 
I chose Ubuntu because I'm not nerdy enough to use Linux from Scratch.  I don't know of any better out there.

Nothing is perfect.  It would be nice to see a Linux distro accept suggestions and feedback from non-propeller-heads on occasion.

---

### Post by dcstar on 2006-01-08
[QUOTE=angrykeyboarder]WI GRE?
.......
I chose Ubuntu because I'm not nerdy enough to use Linux from Scratch.  I don't know of any better out there.

Nothing is perfect.  It would be nice to see a Linux distro accept suggestions and feedback from non-propeller-heads on occasion.[/QUOTE]
Hey, I'm one of the "Propeller-heads" who has asked for the easy-peasy 1.5 package.....     ;)

BTW, I did the manual install of FF 1.5 last week, and apart from a few manual things like copying over all of my plug-ins to the new location where I put the files, it went extremely smoothly (and my 1.07 version still works).

About the hardest thing was creating a Launcher for the new version......  ;)

It still seems strange to me that someone couldn't package the binary and the few commands to do these miscellaneous things in a nice simple "Firefox1.5-interim" package to be installed via Synaptic from one of the Ubuntu repositories.

Anyway, here's exactly what I did:

[http://ubuntuforums.org/showpost.php?p=633942&postcount=315](http://ubuntuforums.org/showpost.php?p=633942&postcount=315)

---

### Post by Corrado on 2006-01-09
[QUOTE=dcstar]It still seems strange to me that someone couldn't package the binary and the few commands to do these miscellaneous things in a nice simple "Firefox1.5-interim" package to be installed via Synaptic from one of the Ubuntu repositories.[/QUOTE]
My feelings exactly.  How hard could it be?  What harm would it do?  Hell, I would do it if I knew how and had write access to the repositories.  Is there some sort of comittee that we could petition to or something?  Bitching about it on a forum is all well and good but it's not getting any results.  How can we be more effective?  (damn, I sound like a suit from work :().

Later...
  Corrado

---

### Post by macleod199 on 2006-01-09
[QUOTE=angrykeyboarder]
WI GRE?

While Firefox isn't really as integrated with Linux as IE is with Windows, it's getting close. Anything that needs to render HTML tends to use it's engine to do it, and therefore depends on a certain version of it's API/ABI. 

[/quote]

The GRE was (supposed?) to be the Gecko rendering engine. Basically the part that renders HTML, factored out so only one copy of it needed to be in memory at any given time. Note that this may not have necessarily fixed the problem that we're having now, but it could have helped.

[QUOTE=angrykeyboarder]WI GRE?
And therein lies a big problem that needs to be fixed.  No single application should be depended upon by so many other applications.  

What if I have an aversion to Firefox? I should be able to uninstall it.  But based on this, if I do, it will take 16 other applications with it and/or possibly cripple my system.

[/quote]

Gnome chose to depend on the Mozilla renderer as I imagine they thought it was the most secure/stable/feature complete. OS X decided to depend on KDE's renderer for their own reasons. But I agree (and that's my point above), that the renderer should be a separate package. It's Mozilla's problem there.

[QUOTE=angrykeyboarder]
It depends on one's definition of "stable" I suppose.  There was quite a bit of criticism that Breezy was buggier than usual (in part because it was "rushed" to meet the deadline).
[/quote]

Quite possibly. They were partially burned by the delays in Xorg's schedule. I switched right to Dapper, so I can't really comment. :)


[QUOTE=angrykeyboarder]
Ubuntu was well aware of the release schedule for Firefox and OpenOffice.org they had three options.

1). Ignore it (as they did).

2) Delay release for a month so that they could include Firefox 1.5 and OpenOffice.org  2

3) Update OpenOffice.org and Firefox in the current Ubuntu release (Breezy in this case) when they came out.

#3 Makes the most sense to me, but I could live with #2 as well. 
[/quote]

I wouldn't say they ignored it. They looked at the release schedule, determined it would not be out in time to meet their release schedule, and rejected it. They did opt to include OO2 based on it's (slipped) release schedule (as can be seen by the inclusion of the pre-release in Breezy), and I'm a little baffled that the final version isn't in breezy-updates yet.

[QUOTE=angrykeyboarder]
Personally I'd like to see Ubuntu do that and adopt the Fedora Project's release schedule. It's also every 6 months but it's "approximately" every 6 months..

All they needed was one more month and a lot of us wouldn't be complaining now.
 
I chose Ubuntu because I'm not nerdy enough to use Linux from Scratch.  I don't know of any better out there.

Nothing is perfect.  It would be nice to see a Linux distro accept suggestions and feedback from non-propeller-heads on occasion.[/QUOTE]

Exactly. No mp3 player does exactly what I want, but I chose the one that was closest. At least Linux distros are more configurable and updateable after the fact, though. You pretty much have to choose the one that has the easiest delta between what you want and what's installed by default, but there will always be a delta. [ubuntuguide.org](ubuntuguide.org) made it really easy for me to cross that delta in the Hoary/Breezy era.

---

### Post by kaaredyret on 2006-01-10
I am using most in my time back in Windows now... again. I could wait for the 1.0.x updates, but this time I wont. I lost enough sparetime on tweaking Ubuntu and getting things to work, I had to reinstall totally when Breezy didnt update anything but crushed my installation of Hoary, and now this?

I am a casual user and a real demanding costumer... I didnt install Ubuntu as a hobby or anything, but to see if it could replace Windows/Office/whatever now that I use computers almost only at work and consider problems and tweaking and optimizing a waste of time. I really dont care why the delay is so long. Firefox 1.0.7 on Breezy is an annoying and slooow experience, and Firefox 1.5 on Windows runs fast. The choice is very simple.

It really surprises me... the lastest version of Firefox and OOo should be EASY to install and made available as fast as possible, always. They are too damn important for Ubuntu. End users really dont care about explanations but about availability and usability. I trust that Mark S knows this and that it will get better with time. Right now, I just have to abandon Ubuntu for a while, fortunately most apps I use on Ubuntu are avalable for Windows, too.

---

### Post by Limulus on 2006-01-11
**kaaredyret:** The main problem is that Ubuntu strives for stable apps in a periodic release schedule, while some of its apps (e.g. Firefox) are in a relatively rapid state of flux and seem to release whenever (note that FF was originally supposed to come out with a 1.1 version in March, but they scrapped that).  This was especially noticable in Breezy because it was released just prior to OO.o 2 and FF 1.5, so there's going to be a lag until the next stable release. This sort of thing is why Ubuntu got Backports in the first place, but Backports is only to pull relatively minor upgrades from the next version back into the current one.

That being said, I have been paying attention to the efforts of people on this forum to get both of these working in Breezy and the solutions they've come up with are quite good.

For OOo2 see [this post](http://ubuntuforums.org/showthread.php?p=557274#2) (just use step 0a and 0b to install)

For FF1.5, see [post #102](http://ubuntuforums.org/showpost.php?p=603380&postcount=102) of this thread (by "jasutton").  Copy the code into a text file and run it with *sudo bash* in Terminal; it will do the rest for you.

Installing these are effectlvely no more difficult than installing them in Windows.  I hope that solves things for you and lets you get back to using Ubuntu :)

---

### Post by kaaredyret on 2006-01-11
Thanks a lot for the reply and help, Limulus :smile:

---

### Post by Limulus on 2006-01-11
**kaaredyret:** Glad I could help :)

My general philosophy with software is that if I'm having a problem, I'm probably not the first nor the only one... and even if I am, someone else will have the same problem soon too ;)

That's why forums are so great; people can discuss their problems and find out how others fixed them.  Without this forum, I wouldn't be near as happy on Ubuntu as I am ^^;

---

### Post by jbus on 2006-01-12
[QUOTE=Limulus]Installing these are effectlvely no more difficult than installing them in Windows.[/QUOTE]

This is not true... Windows users do not have to deviate from normal installation procedures to install these applications.

Ubuntu users shouldn't have to search/beg for scripts on discussion forums, or be advised to follow a long list of instructions on a wiki just to have a _temporary_ installation. 

For the good of the ubuntu community, we shouldn't sugarcoat this issue. We need to call attention to this problem so that it can be addessed. Those that say it's too hard to fix or that current solutions are good enough are just making lazy excuses. I'm willing to bet there are many ways to fix this problem, some are simple and others are complexed, but ultimately someone has to want to fix this problem before we see a solution. That won't happen unless more ubuntu users speak out.

---

### Post by foxy123 on 2006-01-12
[QUOTE=jbus]This is not true... Windows users do not have to deviate from normal installation procedures to install these applications.

Ubuntu users shouldn't have to search/beg for scripts on discussion forums, or be advised to follow a long list of instructions on a wiki just to have a _temporary_ installation. 

For the good of the ubuntu community, we shouldn't sugarcoat this issue. We need to call attention to this problem so that it can be addessed. Those that say it's too hard to fix or that current solutions are good enough are just making lazy excuses. I'm willing to bet there are many ways to fix this problem, some are simple and others are complexed, but ultimately someone has to want to fix this problem before we see a solution. That won't happen unless more ubuntu users speak out.[/QUOTE]

frankly speaking I do not see the problem that should be fixed. Honestly there are huge number of people who do not update their software very often. I know one multinational company which still use Outlook 97 in their offices around the globe without any complaints. And 80-90% of Windows users still use acient IE.

FF 1.07 is an excellent piece of software with all security patches and necessary upgrades. If someone wants to upgrade to 1.5 this person may simply untar the tarball into home directory and use it from there. Or use wiki to make it better.

---

### Post by kaaredyret on 2006-01-12
So, if a group of consumers in a supermarket dont give a damn about fresh milk and meat, then the owner shouldnt get it? He would of course get fresh milk and meat, satisfying all costumers.

Ubuntu needs costumers, not more praise within a community of young males.

---

### Post by kaaredyret on 2006-01-12
[QUOTE=foxy123]If someone wants to upgrade to 1.5 this person may simply untar the tarball into home directory and use it from there. Or use wiki to make it better.[/QUOTE]

This 'someone' is a user like you. Not a casual user or a newcomer from Windows or Mac.

If you want to expand the user base, then you have to adapt to the world, trying to make 99% of the world to adapt to all this geeky stuff is just naive.

I waited for sooo long for OpenOffice 2 to be released, and then I perhaps have to wait for further 6-12 months on Ubuntu? Nah, then I suddenly understand why I pay for Windows.

Ubuntu is now in a competitive environment too, and this waiting waiting or geek stuff is just not good enough.

---

### Post by Jeigh on 2006-01-12
If it isn't good enough for you, you are welcome to return to a windows life. No one is forcing you to use Ubuntu or anything else for that matter. So quit your whining or be patient :P

---

### Post by tenshu on 2006-01-12
[QUOTE=Jeigh]If it isn't good enough for you, you are welcome to return to a windows life. No one is forcing you to use Ubuntu or anything else for that matter. So quit your whining or be patient :P[/QUOTE]

or do it yourself =)
that is open source!

---

### Post by kaaredyret on 2006-01-12
[QUOTE=Jeigh]If it isn't good enough for you, you are welcome to return to a windows life. No one is forcing you to use Ubuntu or anything else for that matter. So quit your whining or be patient :P[/QUOTE]

No, I wont quit anything.

This is the reply I was expecting, and that I usually ignore. Read my post again and think... was Kaaredyret only talking about himself? Did he perhaps think "how could this product be improved, so it could really be used by more people?"

Some of you guys are sooo sensitive to critisism... hint, the people that could actually switch to Ubuntu some day, when it is more user friendly and attractive could care about some of these issues, that the current user base happily use hours on fixing. What will YOU do to make Ubuntu a competitive product? Teach them HOW do use terminal, sudo, tell them what they need and what they should mean? 

It is about improving the product and expanding the user base. So focus on that please, instead of giving childish and predictive answers.

---

### Post by kleeman on 2006-01-12
[QUOTE=kaaredyret]No, I wont quit anything.

This is the reply I was expecting, and that I usually ignore. Read my post again and think... was Kaaredyret only talking about himself? Did he perhaps think "how could this product be improved, so it could really be used by more people?"

Some of you guys are sooo sensitive to critisism... hint, the people that could actually switch to Ubuntu some day, when it is more user friendly and attractive could care about some of these issues, that the current user base happily use hours on fixing. What will YOU do to make Ubuntu a competitive product? Teach them HOW do use terminal, sudo, tell them what they need and what they should mean? 

It is about improving the product and expanding the user base. So focus on that please, instead of giving childish and predictive answers.[/QUOTE]

I understand your viewpoint and think it reasonable to an extent however I think you are perhaps being a little impatient. Ubuntu has a 6 month release cycle which means software doesn't get too out of date. I use firefox 1.0.7 on some machines without too much pain. 1.5 is nice but not absolutely essential. Compare this with Windows and Internet Exploder err Explorer. How long have we been waiting for tabbed browsing and for M$ to do something about security? Much longer than the Ubuntu 6 month release cycle.

The six month Ubuntu release cycle is a compromise between the need for the latest software and stability. Seems to be working fairly well for me so far...

---

### Post by aysiu on 2006-01-12
[QUOTE=kleeman]I understand your viewpoint and think it reasonable to an extent however I think you are perhaps being a little impatient. Ubuntu has a 6 month release cycle which means software doesn't get too out of date. I use firefox 1.0.7 on some machines without too much pain. 1.5 is nice but not absolutely essential. Compare this with Windows and Internet Exploder err Explorer. How long have we been waiting for tabbed browsing and for M$ to do something about security? Much longer than the Ubuntu 6 month release cycle.

The six month Ubuntu release cycle is a compromise between the need for the latest software and stability. Seems to be working fairly well for me so far...[/QUOTE] I'm in total agreement. The reason people are so upset about "cutting edge" versions is that the typical new Linux user is a former Windows power user--someone who has the *desire* for cutting edge software but only point-and-click *skills*.

Fortunately, I have no need for cutting edge software, so Ubuntu suits my needs.

---

### Post by kaaredyret on 2006-01-12
Oh, I agree that this is not a life-or-death update. Page rendering in 1.0.7 is just so slow, and element flicker on the screen for several seconds. Firefox on Windows renders pages lightning fast. I just want the updated version to safe myself from it, and 6 months of waiting is a long time, when you know it is ready.

What I dont like is the work and knowledge that is expected from the user, if he/she wants to use the last version of Firefox/OpenOffice.org/whatever.

Point and click skills is all you can expect users to have, when you want to make a distrubution for more than powerpowerpower users.

I ordered 10 Ubuntu CD's to give away to people, but I really only know one guy that knows enough about computers and has enough spare time to check Ubuntu out. After hours of struggling with how-to's and whatnot he eventually stopped booting into Ubuntu because... he got tired of 1.0.7 and the slow rendering and flickering.

Question: will Firefox 1.5 be available in Breezy when Dapper is released, or will I have to update Breezy to Dapper? The Hoary -> Breezy update froze and I had to reinstall.

---

### Post by kwaanens on 2006-01-12
I agree with you kaaredyret, but when it comes to slow rendering time i 1.0.7, maybe you should promote the "fasterfox" extension? Or "Tweak network settings"?

- Ketil

---

### Post by kleeman on 2006-01-12
I honestly don't mean to be rude but why don't you just use arnieboy's Automatix script? It updates firefox plus installs a whole bunch of other goodies with very little pain indeed. See the customization section.

---

### Post by foxy123 on 2006-01-12
[QUOTE=kaaredyret]Oh, I agree that this is not a life-or-death update. Page rendering in 1.0.7 is just so slow, and element flicker on the screen for several seconds. Firefox on Windows renders pages lightning fast. I just want the updated version to safe myself from it, and 6 months of waiting is a long time, when you know it is ready.

What I dont like is the work and knowledge that is expected from the user, if he/she wants to use the last version of Firefox/OpenOffice.org/whatever.

Point and click skills is all you can expect users to have, when you want to make a distrubution for more than powerpowerpower users.

I ordered 10 Ubuntu CD's to give away to people, but I really only know one guy that knows enough about computers and has enough spare time to check Ubuntu out. After hours of struggling with how-to's and whatnot he eventually stopped booting into Ubuntu because... he got tired of 1.0.7 and the slow rendering and flickering.

Question: will Firefox 1.5 be available in Breezy when Dapper is released, or will I have to update Breezy to Dapper? The Hoary -> Breezy update froze and I had to reinstall.[/QUOTE]

I guess those users who can only point and click do not care much about what version of Firefox they use. And page rendering of 1.07 is not SO painfully slow. I am using it at the moment on my desktop and cannot say that it annoys me...

---

### Post by aysiu on 2006-01-12
[QUOTE=kaaredyret]
What I dont like is the work and knowledge that is expected from the user, **if he/she wants to use the last version** of Firefox/OpenOffice.org/whatever.

**Point and click skills is all you can expect users to have**, when you want to make a distrubution for more than powerpowerpower users.[/QUOTE] But these two paragraphs **together** are the problem. From what I've seen in 
Linux forums, there appear to be basically three types of Linux users:

1. Basic needs, basic skills.
2. High needs, high skills.
3. High needs, medium skills.

If you're type #3, you're screwed. You've either got to dumb down your needs or pump up your skills. I happen to be type #1, so I'm perfectly fine, as my needs are simple, so everything's point-and-click, and I just use Synaptic Package Manager for all my software needs.

---

### Post by Limulus on 2006-01-12
[QUOTE=jbus]
[QUOTE=Limulus]
Installing these are effectlvely no more difficult than installing them in Windows.
[/QUOTE]
This is not true... Windows users do not have to deviate from normal installation procedures to install these applications.

Ubuntu users shouldn't have to search/beg for scripts on discussion forums, or be advised to follow a long list of instructions on a wiki just to have a _temporary_ installation. 

For the good of the ubuntu community, we shouldn't sugarcoat this issue. We need to call attention to this problem so that it can be addessed. Those that say it's too hard to fix or that current solutions are good enough are just making lazy excuses. I'm willing to bet there are many ways to fix this problem, some are simple and others are complexed, but ultimately someone has to want to fix this problem before we see a solution. That won't happen unless more ubuntu users speak out.[/QUOTE]

What I meant by "no more difficult than installing them in Windows" was that they're as simple or simpler than an installer in Windows. And there are those debs for OOo2, you just have to enable the repository (which brings me to another point; using a properly setup repository system with Synaptic is *far* easier than installing software in Windows).

Now, when you say "Ubuntu users shouldn't have to search/beg for scripts on discussion forums" you are right, but you're complaining about the wrong company; If Mozilla put out a DEB of Firefox 1.5 (as they put out an EXE for Windows), installation would be super simple (Opera and Skype do this, BTW).  But Mozilla doesn't (imagine you used windows and someone put out their software in RAR format archive.  Whould the average user know what to do to make it run?  And yet, that's very similar to what Mozilla did with Firefox 1.5 for Linux), so Ubuntu has to make one... but because it was released after Breezy, its being made for Dapper. And because of that, there were too many complications to backport it.

**The backporting team is not there to make packages from scratch.**

Imagine it this way: When you buy a brand new motherboard, it will be able to handle the latest processors.  But new computer processors are released every few months or so.  So a a few months from now you may come across a top of the line brand new processor with a new pin arrangement that won't fit into your old motherboard.  Is it just "lazy excuses" to say that you can't run it? (especially when you're going to be getting a new motherboard every six months? ;)

Really, what the problem here is, is that you want Ubuntu with a much shorter release cycle.  This can be accomplished if you run the next version (Dapper) from repositories or from the intermediate colony CDs (aka flight CDs for Dapper; see [this announcement](http://debianplanet.org/node.php?id=1294) for example).  Mind you, you trade some stability for the latest stuff... you might want to try testing it with a Live CD first.  But that might be just what you're looking for.

---

### Post by kwaanens on 2006-01-12
Still, it wouldn't be that hard to make a deb that places FF 1.5 in /opt and sets up the shortcuts. (Even though I can't do it)

- Ketil

---

### Post by Limulus on 2006-01-12
[QUOTE=kaaredyret]Question: will Firefox 1.5 be available in Breezy when Dapper is released, or will I have to update Breezy to Dapper? The Hoary -> Breezy update froze and I had to reinstall.[/QUOTE]
You will have to upgrade; backports was really the only chance it had of making it into Breezy.  I saw that note about upgrading failing in the other post you made; that concerns me.  I have never had trouble upgrading (and I went from Warty -> Hoary on a test computer and Hoary -> Breezy on this computer without incident) so I feel bad for you that your experience didn't go as smoothly...  When you upgraded, was it by inserting an install disk while Hoary was running or installing via repositories in Synaptic?

---

### Post by Limulus on 2006-01-12
[QUOTE=kwaanens]Still, it wouldn't be that hard to make a deb that places FF 1.5 in /opt and sets up the shortcuts. (Even though I can't do it)[/QUOTE]
Perhaps (though, I can't do it either, so i don't really know :), but another concern was that because Backports is now official (and has been since late into Hoary), they also have to support those packages for the duration of the release itself...  So for the developers, its do we let people install via a script that works ok for another three months, or do we take time off from the dapper one to make a breezy version that will need support (bug fixes, etc.) for over a year?  I think you can see why they chose the path they did ;)

Don't forget they're still supporting Warty (and that it still has users! :) and that it will continue to be supported until Dapper is released in April...  Here's what they have to maintain:

4.10 (Warty) supported until 6.04
5.04 (Hoary) supported until 6.10
5.10 (Breezy) supported until 7.04

and the next version 6.04 (Dapper) will be supported until 9.04 (!) on the desktop and 11.04 (!!!) as a server. Seriously, until 2011. Crazy! 8-)

So as you can see, they're trying for relatively stable releases, not necessarily the latest software; we who want FF 1.5 right now are perhaps not the target demographic for Ubuntu...  as I mentioned in the other post, maybe the alpha and beta releases (flight/colony/whatever) are the way to go.

---

### Post by jbus on 2006-01-12
I think a lot of you guys are getting caught up in the fact that **YOU** think its easy to add extra repositories or use scripts like Automatix. It's not that hard, I agree. In fact I'm using FF1.5 right now courtesy of Automatix.

But the point is, that NEW users from other platforms will have a much harder time with this than any of us. They will certainly not understand why they must jump through hoops to install this application (_which is an official release, not a beta_) or that they have to wait 4-5 months AND upgrade their OS before they can use an new version of an application like this. Do Windows 2000 users have to upgrade to XP to run Firefox1.5? Do XP users have to wait for Vista? Do OSX 10.3 users have to upgrade to 10.4? The answer is NO, as it should be. Even poor little Windows 98 users can install FF1.5. 

All the arguments about how it's partially Mozilla's fault and how backports are a burden on developers, or how ubuntu has a fast release schedule are meaningless. All this should be transparent to the end user. 

Technical and philosophical reasons aside this IS a big problem if in the eye of the user Windows 98 is more capable than ubuntu. This has to be fixed if ubuntu is going to be anything other that an easy Linux desktop for lazy geeks.

Maybe it's time ubuntu developers bite the bullet and work on a server side APT system like klik or AppDir like Mac??? Drag and drop, no worry installs would be hard to resist. Ultimately it would save a lot of bandwidth too because users could download an application once and copy it to all their other computers as well as share it with others.

---

### Post by aysiu on 2006-01-12
[QUOTE=jbus]
But the point is, that NEW users from other platforms will have a much harder time with this than any of us. They will certainly not understand why they must jump through hoops to install this application (_which is an official release, not a beta_) or that they have to wait 4-5 months AND upgrade their OS before they can use an new version of an application like this. Do Windows 2000 users have to upgrade to XP to run Firefox1.5? Do XP users have to wait for Vista? Do OSX 10.3 users have to upgrade to 10.4? The answer is NO, as it should be. Even poor little Windows 98 users can install FF1.5. [/QUOTE] New users usually have the chops to use Automatix. Other users honestly *don't care what version of Firefox they have*. They're perfectly content using 1.0.2 or even 0.9. Seriously. I work with these people. Ordinary users (ones who would never install their own operating system) do not upgrade their software to newer versions. They don't even install Windows updates.

---

### Post by angrykeyboarder on 2006-01-12
> **dcstar]Hey, I'm one of the "Propeller-heads" who has asked for the easy-peasy 1.5 package.....      said:**
> http://ubuntuforums.org/showpost.php?p=633942&postcount=315[/URL] 
I've been running 1.5 since a day or two after it came out.  I'd first unpacked the tarball in my home directory.  Later I moved it to "/opt" when I found out what else I needed to do to make it work from there.

1.0.7 is still around, but I've killed the symlink to it (replacing it with a symlink to 1.5).    

It's fairly easy to accomplish.  In fact, I've changed permissions on /opt/firefox so that I'm the owner.  This allows for Firefox's new automatic update system to work.   

Honsstly after this, I think this will be my continued M.O. for any Mozilla products I use with the update feature.  It's much preferable to having to rely on somone at my current Linux distro of choice to update for me.

I'm running Thunderbird 1.6a1 the same way right now.  It's cool cuz I get a software update dailiy. It says "hey an update is ready, click here to restart and complate installation".

Yep, from now on I don't care what my Linux distro is doing with regard to Mozilla products.  Cuz I'm doing my own thang and it's not what they are doing. :-)

---

### Post by angrykeyboarder on 2006-01-12
[quote=Jeigh]If it isn't good enough for you, you are welcome to return to a windows life. No one is forcing you to use Ubuntu or anything else for that matter. So quit your whining or be patient :P[/quote]

Of find a Linux distro that better meets your needs?

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=aysiu]But these two paragraphs **together** are the problem. From what I've seen in 
Linux forums, there appear to be basically three types of Linux users:

1. Basic needs, basic skills.
2. High needs, high skills.
3. High needs, medium skills.

If you're type #3, you're screwed. You've either got to dumb down your needs or pump up your skills. I happen to be type #1, so I'm perfectly fine, as my needs are simple, so everything's point-and-click, and I just use Synaptic Package Manager for all my software needs.[/QUOTE]

Nice way to put it.

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=jbus]I think a lot of you guys are getting caught up in the fact that **YOU** think its easy to add extra repositories or use scripts like Automatix. It's not that hard, I agree. In fact I'm using FF1.5 right now courtesy of Automatix.

But the point is, that NEW users from other platforms will have a much harder time with this than any of us. They will certainly not understand why they must jump through hoops to install this application (_which is an official release, not a beta_) or that they have to wait 4-5 months AND upgrade their OS before they can use an new version of an application like this. Do Windows 2000 users have to upgrade to XP to run Firefox1.5? Do XP users have to wait for Vista? Do OSX 10.3 users have to upgrade to 10.4? The answer is NO, as it should be. Even poor little Windows 98 users can install FF1.5. 

All the arguments about how it's partially Mozilla's fault and how backports are a burden on developers, or how ubuntu has a fast release schedule are meaningless. All this should be transparent to the end user. 

Technical and philosophical reasons aside this IS a big problem if in the eye of the user Windows 98 is more capable than ubuntu. This has to be fixed if ubuntu is going to be anything other that an easy Linux desktop for lazy geeks.

Maybe it's time ubuntu developers bite the bullet and work on a server side APT system like klik or AppDir like Mac??? Drag and drop, no worry installs would be hard to resist. Ultimately it would save a lot of bandwidth too because users could download an application once and copy it to all their other computers as well as share it with others.[/QUOTE]

Your entire premise is flawed. Automatix is VERY easy to use (and once we get gdebi it can be installed all through a GUI), even for a new user. How hard is it to click a checkbox? Really?

Being dishonest about whats going on (aka Windows 98 can do something Ubuntu can't when thats not correct) won't make you any friends around here.

---

### Post by poofyhairguy on 2006-01-12
[QUOTE=kaaredyret]
Ubuntu needs costumers, not more praise within a community of young males.[/QUOTE]

Last thing I will say in this thread:

Ubuntu has no customers. Ubuntu has users. No one pays Mark in order to use Ubuntu.

If you want to be a customer and demand things like a customer than use an OS that treats you like one. Ubuntu is not such an OS. Till you grok that, you can never be happy in Linuxland.

---

### Post by jbus on 2006-01-13
[QUOTE=poofyhairguy]Your entire premise is flawed. Automatix is VERY easy to use (and once we get gdebi it can be installed all through a GUI), even for a new user. How hard is it to click a checkbox? Really?

Being dishonest about whats going on (aka Windows 98 can do something Ubuntu can't when thats not correct) won't make you any friends around here.[/QUOTE]

I agree Automatix is very easy to use. I never said that it wasn't.

But right now is it installed by default??? Is there documentation and a link on the desktop for new users??? No,  so new users need to search for it in the forums to find out about it. I wonder what percentage of people trying ubuntu ever get to the forums before they give up? It would be interesting to find out wouldn't it? Outside of Linux, do you think many people are used to looking in discussion forums for help on installing basic applications???

I can count up to 10 ways to install applications on ubuntu (there are probably more). Claiming an app is easy to install because it is installable from one of TEN ways is ridiculous. Users should have ONE way to install BASIC applications (And I concider the latest version of Firefox to be about as BASIC as they get). Power users can install apps 100 different ways for all I care. But regular users should not have to jump back and forth between command console apt-get, to synaptic, to Automatix, to some script that got posted on the forum or wiki, to compiling an app, to installing with autopackage, to installing a binary, to fooling around with other package systems like klik and so forth... That is all I'm saying. We need consistency.

About Windows 98 I'm not being dishonest, I'm just reading the Firefox [system requirements ]("http://www.mozilla.com/firefox/system-requirements.html") and if you will read my post you will see I was talking about users PERCEPTIONS based on these system requirements, NOT actually comparing ubuntu to Win 98. I think a user coming from Windows 98 WOULD be curios as to why he can install the latest version of Firefox on Win 98 with a simple click, but needs a "special" procedure to install it on Ubuntu Breezy which was released at the end of 2005.  

Poofyhairguy, I'm not here to make friends... I'm here to keep my system running and to discuss an issues that many do not care to give attention to because it's not a problem for them, or because they take any kind of criticism of "their distro" personally... Even if the criticism is constructive. I am not trying to put ubuntu down either. I like ubuntu and I want to see it improve to the point that is truely a "linux for human beings".

---

### Post by angrykeyboarder on 2006-01-13
[quote=macleod199]The GRE was (supposed?) to be the Gecko rendering engine.[/quote] 
Gecko is still alive and well. It ***is*** the HTML rendering engine for all Mozilla products.  I'd just never seen Gecko abbreviated as "GRE" before. :-)

[quote=macleod199] Basically the part that renders HTML, factored out so only one copy of it needed to be in memory at any given time. Note that this may not have necessarily fixed the problem that we're having now, but it could have helped.[/quote] 
I'm not sure what you mean here.  I assumed because so many apps in GNOME relied on Firefox, they were actually relying on it's "GRE".  

[quote=macleod199] Gnome chose to depend on the Mozilla renderer as I imagine they thought it was the most secure/stable/feature complete. OS X decided to depend on KDE's renderer for their own reasons. But I agree (and that's my point above), that the renderer should be a separate package. It's Mozilla's problem there.[/quote] 

Are you sure GNOME chose this and not Ubuntu?  I know that GNOME relies on GTKhtml2. And i[t's part of Ubuntu as well]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=libgtkhtml2&searchon=all"). I'd thought yelp uses the gtkhtml2 engine, but I guess not.  I know[ Straw]("http://www.nongnu.org/straw/") does.  [Liferea]("http://liferea.sourceforge.net/") allows you to choose.  

* Off the top of my head*, the only part of GNOME that relies on Gecko is 
Epiphany, which Ubuntu chooses not to include in it's default installation to begin with.  I wish they would, then they could tie all thoes upteen apps to it instead of Firefox.  Firefox is much more popular.

Better yet, why not just include the Gecko libraries and then tie all those apps that rely on Firefox to it instead?

BTW, these are basically rehetorical questions.

[quote=macleod199] Quite possibly. They were partially burned by the delays in Xorg's schedule. I switched right to Dapper, so I can't really comment. :)[/quote] 
Heh. I switched to Dapper a few weeks ago and they can't even produce Firefox 1.5.  For some odd reason they are hovering at tiny point releases just prior to it.

[quote=macleod199] I wouldn't say they ignored it. They looked at the release schedule, determined it would not be out in time to meet their release schedule, and rejected it. They did opt to include OO2 based on it's (slipped) release schedule (as can be seen by the inclusion of the pre-release in Breezy), and I'm a little baffled that the final version isn't in breezy-updates yet.[/quote] 
I didn't literally mean they ignoired it.  In fact, I meant what you've said here, but they should have waited.  The only people who cared about their self-imposed schedule, was them (Ubuntu).

[quote=macleod199] Exactly. No mp3 player does exactly what I want, but I chose the one that was closest. At least Linux distros are more configurable and updateable after the fact, though. You pretty much have to choose the one that has the easiest delta between what you want and what's installed by default, but there will always be a delta. [ubuntuguide.org]("http://ubuntuguide.org") made it really easy for me to cross that delta in the Hoary/Breezy era.[/quote] 
I was a fan of Ubuntu and had been using it several months before I learned of the now- (unfortunatly) defunct [ubuntuguide.org.]("http://ubuntuforums.org/ubuntuguide.org") 

I've done a lot of bitching and moaning around here and on the mailing lists.  I'm sure some can't help but wonder why I've not abandoned Ubuntu.

Why haven't I?  Because it sucks less than any Linux distro I'm aware of. :-)

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=jbus]I agree Automatix is very easy to use. I never said that it wasn't.

But right now is it installed by default??? Is there documentation and a link on the desktop for new users??? No,  so new users need to search for it in the forums to find out about it. I wonder what percentage of people trying ubuntu ever get to the forums before they give up? It would be interesting to find out wouldn't it? Outside of Linux, do you think many people are used to looking in discussion forums for help on installing basic applications???[/QUOTE]

Not really a fair question. I mean....how many users actually install new OSes? A VERY small percent. Less than the amount that uses message boards I believe. 

Within the current target market of Ubuntu, Automatix works well. Should it be in the default install? I think so and maybe the developers will think so one day too.

> 
I can count up to 10 ways to install applications on ubuntu (there are probably more). Claiming an app is easy to install because it is installable from one of TEN ways is ridiculous. 

I was thinking "cool," but sure - let it be "ridiculous" if it suits you.

> 
Users should have ONE way to install BASIC applications 

They have one. Heck they have more than one. But one main one- that "add/remove programs" tool.

Does it let you install the newest Firefox? No, but officially there is no way to install new applications in Ubuntu. Backports is a community project.

Ubuntu is a distro that is meant to be upgraded all at once every six months. Its intended for the kind of users that aren't constantly checking Slashdot to see if the newest Firefox is out- aka most of the computer using population. It was never intended to be a "rolling" distro that gets new applications as they are released. Many other distros do that...Ubuntu has a different role.

Ubuntu only fails you if you use it in a way not intended.  

> 
(And I concider the latest version of Firefox to be about as BASIC as they get). Power users can install apps 100 different ways for all I care. But regular users should not have to jump back and forth between command console apt-get, to synaptic, to Automatix, to some script that got posted on the forum or wiki, to compiling an app, to installing with autopackage, to installing a binary, to fooling around with other package systems like klik and so forth... That is all I'm saying. We need consistency.

Fine. Be consistent. The official way is apt-get (and its many GUIs). Apt-get does not have what you want? Then its not released for your operating system yet. Thats the official answer.

But that answer sucks for some nerdier types. So things like backports and Automatix were made. But they are not official. Apt-get is.

From the beginning Ubuntu was intended to be like this. You can argue that the original plan sucks, but you can't argue that there was not consistancy in the original plan.

> 
About Windows 98 I'm not being dishonest, I'm just reading the Firefox [system requirements ]("http://www.mozilla.com/firefox/system-requirements.html") and if you will read my post you will see I was talking about users PERCEPTIONS based on these system requirements, NOT actually comparing ubuntu to Win 98. I think a user coming from Windows 98 WOULD be curios as to why he can install the latest version of Firefox on Win 98 with a simple click, but needs a "special" procedure to install it on Ubuntu Breezy which was released at the end of 2005.  

A user coming from Windows 98 might also wonder why clicking on exe's does not work ("hey it worked in Windows 98!"). Not all attributes transfer from one OS to another. Getting new applications officially without the six month upgrade is not an attribute of Ubuntu. 

Does Windows automatically update my Firefox and OpenOffice and whatever else when I go from 98 to XP? No?! Why the heck not?! My Ubuntu install could! Oh yeah, thats because attributes of one OS might not transfer to another.

And for the record, it takes two clicks to install Firefox 1.5 in Automatix. WAY less than in Windows 98 ("next, next, next").

> 
Poofyhairguy, I'm not here to make friends... I'm here to keep my system running and to discuss an issues that many do not care to give attention to because it's not a problem for them, or because they take any kind of criticism of "their distro" personally... Even if the criticism is constructive. I am not trying to put ubuntu down either. I like ubuntu and I want to see it improve to the point that is truely a "linux for human beings".

I'm not taking offense because its my pet distro. I am arguing that you are wanting Ubuntu to be something it was never designed to be. Its not a "rolling" Desktop Linux. Its a "freeze and upgrade every six months" Desktop Linux. Other distros had Firefox the day it was released. Users that care about such should use those distros. Ubuntu is for people that want a distro sent to them for free with free upgrades every six months. You might argue not many want a distro like that, but the fact that Mark has mailed more than a million Ubuntu CDs tells a different story.

And for the record, I thought I WAS a human being. Am I not? If Ubuntu is not yet a "Linux for human beings" than how can I use it?

> 
Better yet, why not just include the Gecko libraries and then tie all those apps that rely on Firefox to it instead?

There is the core of the issue for today. The answer to this question is because:

"Mozilla has not yet seperated Gecko from Firefox/Mozilla Browser."

Its not Ubuntu's fault that Mozilla has not done this yet....and Ubuntu can't gut Firefox like that and still call it Firefox. Its up to Mozilla to do...and they will....but not yet. And then that problem will be solved.

If they had done this already then Firefox 1.5 would exist in the backports repo. Yet even if that happened this debate would still exist in a different form. 

The essential problem you have is that the Ubuntu developers made a decision you don't like at the start- that Ubuntu will not officially get updated versions of software when they are released. You have to wait the six months.

Mark and the Ubuntu Team made this decision from the beginning for good reasons:

1. Ubuntu is about driving Linux development forward. That moves faster without the baggage of the past.

2. Ubuntu is a Debian based distro and this is how Debian does it. Why? Because new applications might break a stable platform and require a lot of work to backport, thats why (and Firefox 1.5 is a GREAT example of this). Ubuntu developers want most of their time spent on the next release, not upgrading the last one.

3. Ubuntu is aimed at regular users, not geeks. I have honestly never met a non-geek that cares to have the newest software every time. Every Windows user I have installed Firefox for is still using the EXACT same version I put on their machines (I check when I see them next), despite how easy it is to install new versions in XP. Why? Only nerds know new versions exist and care...

For these reasons and more, Ubuntu does not provide newest software except every six months.

Yet you are not alone in not liking that. Yet unlike others, you expect Ubuntu to change its ways to accommodate you.

Others (Jdong) fixed the problem themselves by starting Ubuntu Backports. Others (Arnieboy) fixed the problem by providing easy other non official ways to get the software. Others (many) have written guides and how tos to tell how to get new software.

These people understand: Ubuntu is what it is. Take it and fix it yourself or leave it alone. Don't expect Ubuntu to change for you- you are not the target market.

If this is really a problem for you, then find a way to fix it. Don't demand that others fix it. Don't complain that Ubuntu's entire philosophy from the start is flawed. It works well for some people. Heck...some of my friends are still using WARTY! Freaking Warty from a year ago. Why you ask? Because they are not geeks and they don't care about the newest software. The Firefox in Warty works well enough for them, so they don't mess with it. Like huge chunks of the world's population (and the Ubuntu team) they believe "if it ain't broke don't fix it."

You think the system is broken. I can't tell you that you are wrong. Its your opinion. I will say that complaining on the forums about it won't solve anything. And not just because the developers don't read the forum (and they mostly don't), but because that is not the way for your solution to appear.

Linuxland is not a commercial landscape. Its not a system of customers and sellers. Its a meritocracy. If you believe your idea has merit, then prove it. Make a better apt-get or Ubuntu or whatever. But if all you plan to contribute is that "hey guys, the system is broken" please don't get too offended when we act like we don't care.

Ubuntu might not be the best fit for you. There are like 300 Linuxs. One for each kind of person. Find the one for you, or help the community change Ubuntu to serve your kind of user. Those are your only real options.

Of course, if you want to keep beating this horse on the forums then thats fine with me. Ask anyone who is on here a lot- I LOVE discussing what I think Ubuntu is and can be. I can do this all day. But lets not pretend its helping anything but ourselves, ok?

---

### Post by aysiu on 2006-01-13
[QUOTE=poofyhairguy]
Ubuntu is a distro that is meant to be upgraded all at once every six months. Its intended for the kind of users that aren't constantly checking Slashdot to see if the newest Firefox is out- aka most of the computer using population. It was never intended to be a "rolling" distro that gets new applications as they are released. Many other distros do that...Ubuntu has a different role.

Ubuntu only fails you if you use it in a way not intended.[/QUOTE] Unfortunately, Ubuntu's target audience is not its main body of users. I think Ubuntu is designed to be **installed** by a Linux expert (or novice who's willing to learn to be an expert) and **used** by a computer novice.

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=aysiu]Unfortunately, Ubuntu's target audience is not its main body of users. [/QUOTE]

Yet.

I hope for a better future.

---

### Post by kleeman on 2006-01-13
You must only be in your 20s or 30s poofy :p

---

### Post by kwaanens on 2006-01-13
> **Limulus]Perhaps (though, I can't do it either, so i don't really know :), but another concern was that because Backports is now official (and has been since late into Hoary), they also have to support those packages for the duration of the release itself...  So for the developers, its do we let people install via a script that works ok for another three months, or do we take time off from the dapper one to make a breezy version that will need support (bug fixes, etc.) for over a year?  I think you can see why they chose the path they did  said:**
> 

One option would be to issue a deb of 1.5 that:
- just placed it in /opt and set up shortcuts, like I said, 
- and didn't remove 1.0.7. 
And they could say: "hey, this will be the *only* deb of FF 1.5 in this Ubuntu release. Forget about bug fixes!" 
That way, we could enjoy being somewhat bleeding edge, and still be able to turn to the old official Ubuntu-version if 1.5 gets a huge bug that will make it dangerous to use.

[QUOTE=Limulus]So as you can see, they're trying for relatively stable releases, not necessarily the latest software; we who want FF 1.5 right now are perhaps not the target demographic for Ubuntu...  as I mentioned in the other post, maybe the alpha and beta releases (flight/colony/whatever) are the way to go.

But I don't want bleeding edge all over the place, but I want to utilise the power of an upgraded version of the software that I use way more than all other software.

- Ketil

---

### Post by poofyhairguy on 2006-01-13
[QUOTE=kleeman]You must only be in your 20s or 30s poofy :p[/QUOTE]


LOL. 23.

---

### Post by kaaredyret on 2006-01-13
[QUOTE=poofyhairguy]Yet.

I hope for a better future.[/QUOTE]

Hope is never enough. Automatix isnt either.

---

### Post by aysiu on 2006-01-13
[QUOTE=kaaredyret]Hope is never enough. Automatix isnt either.[/QUOTE] Can you explain this statement? Why is Automatix never enough?

---

### Post by Limulus on 2006-01-13
[QUOTE=poofyhairguy]Automatix is VERY easy to use[/QUOTE]
I tried it last night.  I installed "Midi capability", "Eject CD from Drive" and "Ctrl-Alt-Del".  The first one didn't work as far as I can tell.  I also noted a general lack of explanation of exactly what it was going to do (can we say 'informed consent'?) and a lack of an uninstall feature.  Then this morning I went into Synaptic and I noticed that it had replaced my sources.list without telling me first. That wasn't very nice. So I uninstalled it.  Fortunately it made a backup of my old sources.list first, or I would have been *pissed*.

I see now why they say you shouldn't run programs as root ;)

**Edit:** I went over to the Automatix thread to get some help (I basically copied in the above text) and eventually got some help, but the guy who runs it, "arnieboy" acted like a jerk about it.  Anyway, I will be taking the info from Automatix that work on my system and incorporate them into my page.

---

### Post by kaaredyret on 2006-01-13
[QUOTE=aysiu]Can you explain this statement? Why is Automatix never enough?[/QUOTE]

Oh, this tool is just not enough to push Ubuntu much further, thats all I meant. I used it myself, but I only use it because I have been all around the forum, looking for how to's, help, etc.

Users should be able to get the most out of Ubuntu without having relying on community support. Its wonderful to have the community and it does make some open source/closed source products special, but usability is not about bringing desperate people together but about making things work.

Again, just in case: forget about me and my rants, but reflect a little about the core of the problem: how to improve Ubuntu and make all this work, out of the box.

I put a lot of effort into my installation, and it still wasnt enough. Some issues cannot be resolved, some took days, weeks to resolve, using obscure how-to's. I am very grateful for the help, but think about all those that gave up, all those that looked at the how-to's and thought "jesus", all those that wasnt into all this sudo stuff and editing config files, all those that just didnt understand and all those that refused.

I have been listening to (geeks, thats what they were) telling people like me "take it or LEAVE IT" for ... 10 years I think. The problem for Linux is, that so few take it.

I have been working with usability for some time now, and I have been listening to A LOT of rants. Did I get upset, tell people to take it or leave it, or just ignore them? No, certainly not. Feedback is feedback, and even angry persons can have a valid point. They cant even speak on behalf of a lot of people. Critisism is important.

Ubuntu Linux still isnt good enough for me, and I wont stop telling you why. I really dont care about whether or not this gives me friends in here, because I am here for two reasons: finding how-to's (a problem in itself that I need them at all) and to make you guys THINK! I read your replies with satisfaction, because if I provoke you then it makes you reflect a little, that is my hope at least.

If you want Linux to gain a lot of new users and supporters, then please understand that these users could be unlike yourself. Users are costumers: their satisfaction is important to you. If people spread the word "Linux is too complicated" then its really not good for "the community".

---

### Post by Turin Turambar on 2006-01-14
Hey Kaaredyret, I know what you mean, but let me tell you that Breezy is much faster and more "out of the box" thing than Hoary was. So, take it easy. Ubuntu is still, unbelievably polished, but young distro! :)
Expect that DD will be even better, although I really am satisfied with Breezy. I spent much more time tweaking the stuff, doing this, doing that in Hoary! Breezy worked almost instantly (both were installed clean).

---

### Post by Limulus on 2006-01-14
[QUOTE=aysiu]I think Ubuntu is designed to be **installed** by a Linux expert (or novice who's willing to learn to be an expert) and **used** by a computer novice.[/QUOTE]
That reminds me, way back when, of when I got my first computer: a [Tandy 1000 SX](http://users2.ev1.net/~switchtech/Tandy1000/T1000Catalog.GIF) :)  A friend of my mom's set it up to run DOS; I recall it took a while and there was a lot of command line magic I totally had no clue about at the time... :)

I'm starting to think that Ubuntu needs some sort of tutorial file (animation?) sitting near the center of the desktop when there's a clean install.  Even just something to teach the newbies about Synaptic (an almost alien concept of installing programs to someone migrating from Windows).  The more I think about things like Automatix, the more [I get annoyed](http://members.shaw.ca/Limulus/manumatix.html); I've been looking at the code and most of it is just installing packages (there are a scripts that do neat things, but they could probably be done with packages too ;P).

Maybe I'm just biased; its been almost a year since I first tried Ubuntu (my first real taste of Linux :) and once I discovered Synaptic, I was like a kid in a candy store ^_-

But getting back to your comments about setup, I suspect its really that way for most OSs; just think how much better Windows would be for a newbie if you got an expert in to setup all the antivirus, antimalware, firewall, misc. security stuff, put Firefox and Thunderbird on, maybe even remove Windows Media player and replace it with one of the alternatives... that sort of thing.

Ubuntu definitely has the security aspect down though :)

---

### Post by foxy123 on 2006-01-14
[QUOTE=kaaredyret]Oh, this tool is just not enough to push Ubuntu much further, thats all I meant. I used it myself, but I only use it because I have been all around the forum, looking for how to's, help, etc.

Users should be able to get the most out of Ubuntu without having relying on community support. Its wonderful to have the community and it does make some open source/closed source products special, but usability is not about bringing desperate people together but about making things work.

Again, just in case: forget about me and my rants, but reflect a little about the core of the problem: how to improve Ubuntu and make all this work, out of the box.

I put a lot of effort into my installation, and it still wasnt enough. Some issues cannot be resolved, some took days, weeks to resolve, using obscure how-to's. I am very grateful for the help, but think about all those that gave up, all those that looked at the how-to's and thought "jesus", all those that wasnt into all this sudo stuff and editing config files, all those that just didnt understand and all those that refused.

I have been listening to (geeks, thats what they were) telling people like me "take it or LEAVE IT" for ... 10 years I think. The problem for Linux is, that so few take it.

I have been working with usability for some time now, and I have been listening to A LOT of rants. Did I get upset, tell people to take it or leave it, or just ignore them? No, certainly not. Feedback is feedback, and even angry persons can have a valid point. They cant even speak on behalf of a lot of people. Critisism is important.

Ubuntu Linux still isnt good enough for me, and I wont stop telling you why. I really dont care about whether or not this gives me friends in here, because I am here for two reasons: finding how-to's (a problem in itself that I need them at all) and to make you guys THINK! I read your replies with satisfaction, because if I provoke you then it makes you reflect a little, that is my hope at least.

If you want Linux to gain a lot of new users and supporters, then please understand that these users could be unlike yourself. Users are costumers: their satisfaction is important to you. If people spread the word "Linux is too complicated" then its really not good for "the community".[/QUOTE]

the best thing about Linux is that you have a vast choice. I am not telling about only other Linux distros, but also FreeBS, Solaris, Windows and so on. So if you feel that Ubuntu is not up to your expectation, try other OS. You may find the one which suits your needs if not perfectly but close.

While I understand your point to improve Ubuntu, I guess it is easier to switch to something more suitable then to make so much efforts to tell people that Ubuntu is not good here and there.

I started with Windows, then eventually switched to SuSE, tried acouple other distros and ended up with Ubuntu, because it suits all my current computer needs. However, on my laptop I use XFCE and E17 both compiled from CVS/SVN, Amarok, Mplayer, Gaim from CVS, experimental InitNG, FF and TB 1.5 and a number of other programmes compiled from source and I am not a comuter geek at all. I do it because it's very easy. 

While on the desktop I have a mostly pure Ubuntu without much alterartions and it suits most of my family. So the point is that one chooses the system which fits one's needs.

---

### Post by aysiu on 2006-01-14
[QUOTE=Limulus]
But getting back to your comments about setup, I suspect its really that way for most OSs; just think how much better Windows would be for a newbie if you got an expert in to setup all the antivirus, antimalware, firewall, misc. security stuff, put Firefox and Thunderbird on, maybe even remove Windows Media player and replace it with one of the alternatives... that sort of thing.[/QUOTE] I agree with this, too (after all, that's why ["The Geek Squad"](http://www.geeksquad.com/) exists--I know people who actually pay "professionals" to install a CD-ROM they bought... I'm not kidding), but I think Windows actually isn't for the novice user even after it's been set up properly. If the novice user isn't administrator, she can't even change the time on her computer or install Windows security updates! Yet, if she is the administrator, it's very easy for her to screw the whole installation. 

On Ubuntu, however, you can make a novice user the *sudo* user and not have her screw things up accidentally if you don't give her a *gksudo nautilus* button or a handbook of commands like *rm* and *chmod*. She can still change the time on her clock, install software safely through Synaptic Package Manager and not endanger her entire installation.

---

### Post by jbus on 2006-01-14
I've been a distro hopper for quite a while. I'm sure I've done more installs of different flavors of Linux and BSD, in less time than a lot of people. I have chosen to stick with (k)ubuntu because it has the promise of making things easy for novice users. I've encourage friends and family that have been plagued with viruses and other problems on windows to switch to ubuntu as well. 

I don't live on the forums or have a billion posts, but I do read them. I am a member of the ubuntu community and I find it very insulting when the response to a little constructive criticism is essentially "Like it or leave it". I have made an effort to contribute what I can to the kubuntu community. The Kubuntu KDM and Splash themes that I made have been downloaded by many people and are rated well. Not everyone likes them or sees the need to use anything other than the default themes, but at least kubuntu users have one more option. I also plan on releasing updated versions under GPL and possibly a window dec theme for kubuntu when I have more time in a couple of weeks. So don't think that because people are not devs or because they don't have programing skills that they can't contribute to this community.

If I was personally capable of fixing this issue to my liking, believe me I would. But I'm not, so the most I can do on this matter is state my opinion and ideas. Some of you feel, it's a waist of time to discuss this here since the ubuntu devs don't read these forums. That's their problem not mine. The ubuntu devs should concider looking at these forums once in a while, it might help them make decisions that would benefit more people. In any case it shouldn't prevent us from discussing these types of issues.

---

### Post by aysiu on 2006-01-14
[QUOTE=jbus]
I am a member of the ubuntu community and I find it very insulting when the response to a little constructive criticism is essentially "Like it or leave it". 

Some of you feel, it's a waist of time to discuss this here since the ubuntu devs don't read these forums. That's their problem not mine. The ubuntu devs should concider looking at these forums once in a while, it might help them make decisions that would benefit more people.[/QUOTE] I don't see why the developers should have to scour the forums for suggestions when forum members have a way of directly communicating suggestions to the developers. That's dumb--I'm sorry, but it is.

And, yes, I do think it's silly, too, to think that the forums are a place to voice "constructive criticism." It's about as useful as me complaining to my wife about government policy rather than writing letters to my local congressperson. If you just want to blow off steam, that's understandable, but why you think the forums are a good venue for "constructive criticism" is beyond me.

For more on what you can do to make a difference, [read this](http://www.ubuntuforums.org/showthread.php?t=75000) or [this](http://www.ubuntuforums.org/showthread.php?t=78741).

---

### Post by kaaredyret on 2006-01-14
I do know how to reach the developers and even Mark S. I made my posts to help people - the community - see that there are other viewpoints and type of users than themselves.

Its is not strange at all that you see my opinion here; it was my response to other viewpoints etc.

---

### Post by macleod199 on 2006-01-15
[QUOTE=aysiu]Unfortunately, Ubuntu's target audience is not its main body of users. I think Ubuntu is designed to be **installed** by a Linux expert (or novice who's willing to learn to be an expert) and **used** by a computer novice.[/QUOTE]

You mean like your furnace? Or your car engine? This is why we have IT departments.

---

### Post by macleod199 on 2006-01-15
[QUOTE=angrykeyboarder]Gecko is still alive and well. It ***is*** the HTML rendering engine for all Mozilla products.  I'd just never seen Gecko abbreviated as "GRE" before. :-)
[/quote]

Gecko is alive and well, but the GRE is a dead project. Or at least has been reincarnated as XULRunner. Sort of, maybe? It's hard to tell.  The reason you've never seen it is probably because they stopped talking about it years ago. To the consternation of many.

 [QUOTE=angrykeyboarder]
I'm not sure what you mean here.  I assumed because so many apps in GNOME relied on Firefox, they were actually relying on it's "GRE".  
[/quote]

If you can't install the GRE by itself, though, they have to rely on Firefox to provide it. It's not factored out.
 
 [QUOTE=angrykeyboarder]
Are you sure GNOME chose this and not Ubuntu?  I know that GNOME relies on GTKhtml2. And i[t's part of Ubuntu as well]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=libgtkhtml2&searchon=all"). I'd thought yelp uses the gtkhtml2 engine, but I guess not.  I know[ Straw]("http://www.nongnu.org/straw/") does.  [Liferea]("http://liferea.sourceforge.net/") allows you to choose.  

* Off the top of my head*, the only part of GNOME that relies on Gecko is 
Epiphany, which Ubuntu chooses not to include in it's default installation to begin with.  I wish they would, then they could tie all thoes upteen apps to it instead of Firefox.  Firefox is much more popular.
[/quote]

Dependency of:
OOo2
libgecko-cil
galeon
beagle
yelp
libdevhelp
gnome-app-install

I'm not sure what the specific issues, but I trust that jdong knows what he's talking about when he says it's tied in tightly. It's also possible that things like the SSL and plugin libraries would have to be updated, and there's additional applications that rely on those. I can't say whether it's a Gnome or a Ubuntu decision, but that's the way it is.


 [QUOTE=angrykeyboarder]
Better yet, why not just include the Gecko libraries and then tie all those apps that rely on Firefox to it instead?

BTW, these are basically rehetorical questions.
[/quote]

This is exactly what the GRE was supposed to be. That was my point. But Mozilla doesn't seem to care.

---

### Post by prizrak on 2006-01-20
To those of you who was asking for a .deb
If you care enough to go through the thread someone mentioned posting a .deb that puts FF1.5 into the /opt directory only works if you delete the old firefox tho.

---

### Post by jrevillini on 2006-01-23
there are many posts declaring that installing applications in ubuntu should be more intuitive, frequently comparing to the user experience of windows.

i think that it's important to look at competing (and when i say that i mean "stuff for the same general purposes") software and see what they're doing that works well for users to get ideas for the target software - in this case, ubuntu - but there are a few things to keep in mind:
[LIST]
[*]windows is one piece of software.  ubuntu is another.  firefox is yet another.  a lot of this thread is spent arguing and discussing a combination of software which makes up only 1 small part of the entire user experience.  sure, they're all popular software titles, but demanding that ubuntu immediately have 1-click install support for firefox 1.5, which i understand has some issues which have made it a little more difficult to package than before, is asking too much.  i mean, the forum IS here for us to voice our opinions, but like others have said, there is a release cycle to keep in mind.  ff1.5 will come, it's just not going to come at the speed some people want it.
[*]if we are going to compare to windows, we have to take the bad with the good.  many have praised the windows installation method as being easy - that's IF everything goes as expected.  that's IF you, the winxp/ff user notices the little red update button in the upper right corner, clicks it, and updates it successfully.  i should also note that this method of upgrading firefox is not completely obvious to everyone, nor does it follow some standard upgrading protocol in windows.  in fact, the only thing the windows OS is going to help you update/upgrade/patch is the OS itself.  you're on your own for most of the applications, except the one's that are prebundled, microsoft products.  so imagine you're a windows xp user now.  you're using firefox 1.0.7 and want to upgrade to the latest.  you still have to go online and figure out how, whether it be a M$ forum, a knowledge base, or the mozilla site.  the information you find will be different that what we, the ubuntu users find, but it's going to be just as mystifying to the basic user.  regardless of OS, the basic user is always going to have difficulty when the OS doesn't behave as expected.
[*]also, we can't argue that windows has 1 way to install/upgrade everything.  there are the windows updates (can be done through the system tray or by going to the site manually or by clicking windows update in the program menu), the windows catalog(program menu or manually entering site), notifications from within specific software titles which manage themselves, upgrading the software through the 'help' menu on some software, manual installations, installations automated by exe'd zip files... maybe more.  those of you who have proposed 1 installation method have proposed a concept which has not yet been implemented by any operating system that i'm aware of, and i personally don't think it's a good idea at all.
[/LIST]

now i'm going to stop comparing ubuntu to windows because while it's important to consider what's working (most of the time) for the competition, each OS needs to have its own strengths and consequently, its weaknesses.

personally, i've used ubuntu with ff1.0.7 and with 1.5.  i honestly noticed no difference, but there must be one since everyone is raving about it.  but more importantly, i'm not sure i understand the rationale of wanting - no, EXPECTING everything handed to us as we see fit.  that's not to say we shouldn't ask and show support for software upgrades through apt or synaptec - we should.  but we need to be aware of the difference between suggesting and expecting.  if we take the attitude that a "problem" is not a barrier but an opportunity, then we have a model for self-improvement, software improvement, and mutual benefit - in short: the GNU way.

the people who have suggested "take it or leave it" are not responding with hostility (well maybe they are, what do i know) - they're pointing out our options.  it sounds blunt, but when i read a post like that, rather than get pissed, i usually sit back and think: that's true, i do have that option!  it's yet another opportunity to do something else - something new.  i'm glad i have that option.

so if you're still lamenting the ff1.5 thing, please realize the scope of the situation, the reality of what other OS users deal with (not the rose-colored one but the real one), the opportunity YOU have to make this better, and the alternatives.  Keeping these things in mind keeps me in a very balanced place.  I hope it will serve someone else to think this way too.

---

### Post by Simplex on 2006-01-23
[QUOTE=macleod199]Gecko is alive and well, but the GRE is a dead project. Or at least has been reincarnated as XULRunner. Sort of, maybe? It's hard to tell.  The reason you've never seen it is probably because they stopped talking about it years ago. To the consternation of many.[/QUOTE]

It is planned to have [Firefox 3 ship on top of XULRunner]("http://benjamin.smedbergs.us/blog/2005-10-31/using-the-gre/").  It is expected that [Firefox 3 will release in Q1 2007]("http://www.mozilla.org/roadmap/branching-2005-12-16.png").

---

### Post by towsonu2003 on 2006-02-27
I filed this one a while ago, and thought I should mention it here [https://launchpad.net/products/firefox/+bug/32083](https://launchpad.net/products/firefox/+bug/32083)

thanks.

PS. I honestly didn't read all of the thread (17 pages) - sorry...

---

### Post by Limulus on 2006-02-27
[QUOTE=towsonu2003]I filed this one a while ago, and thought I should mention it here [https://launchpad.net/products/firefox/+bug/32083](https://launchpad.net/products/firefox/+bug/32083)[/QUOTE]

I get an error when visiting the page:
"Sorry, you don't have permission to access this page."
even though I'm logged in...

---

### Post by towsonu2003 on 2006-02-27
[QUOTE=Limulus]I get an error when visiting the page:
"Sorry, you don't have permission to access this page."
even though I'm logged in...[/QUOTE]

my bad. try again now...

---

### Post by cphuntington97 on 2006-03-14
Great forum... I love that I had to type in my birthday to register... I'm sure that is critical info here.

ANYWAY.. background: I'm a long time linux "hobby user" starting with slackware in 1996.. etc. etc. I use windows (need my audio production apps plus anything else that comes out) and mac (love the powerbook)  but I also use linux for fun.

There was a lot of fuss about ubuntu online so I decided to check it out (currently loving knoppix but I never did like kde...)

I booted the live cd... first thing I did (after a bit of poking around) was launch firefox (GREAT default gnome config btw!)... and I decided to install a theme, just to see that all the little bits and pieces really do work on this thing. Of course, I got the error - sorry, theme requires 1.5... and that was it. That was the deal breaker, after less than a minute of use. Knoppix... I <3 you.

Now, it's great that I can go back to knoppix (installed... k2hd) and apt-get myself whatever new apps come out, but I am always looking at linux for situations where windows apps are not needed... and these major updates (firefox, open office, etc.) just absolutely must be supported. Soon. It's a deal breaker.

So for the good of your own distro, someone figure out how to support this stuff- easily. I poked around some of the package management and was really shocked to not find firefox 1.5 in there.

This concludes my advice to ubuntu developers... maybe I'll be back some time if things improve. In the mean time, knoppix reigns supreme!! for me.

---

### Post by Limulus on 2006-03-17
[QUOTE=cphuntington97]So for the good of your own distro, someone figure out how to support this stuff- easily. I poked around some of the package management and was really shocked to not find firefox 1.5 in there.[/QUOTE]
I take it you're using a Breezy Live CD?  Dapper will have FF 1.5 when its released (originally mid-April, but now looking like June 1st or so) and the Flight CDs for it (~alpha versions) are already using version 1.5

See [http://www.ubuntu.com/testing/flight5](http://www.ubuntu.com/testing/flight5)

---

### Post by godard on 2006-04-20
I feel a little awkward saying this since i've only been an Ubuntu user for the last few weeks, but something no one seems to have mentioned in this thread is security. I'm a regular Mac tester of Firefox (and TB for the last 12 months), there have been a number of security issues that have been cleared up with both the 1.0 and 1.5 releases, including the release of 1.5.0.2. In fact, if you take a look on the Mozilla site or follow any of the developer blogs (sorry, i can't find the page right now), the Mozilla folks are recommending all users upgrade to the 1.5 releases from the 1.0 versions. They have also been forthright on the approximately 30-40 security fixes the release includes. I should also mention that Thunderbird should be updated for the same reason. 

The incremental release versions of both Firefox and Thunderbird are not for 'the bleeding edge', they are in fact bug fix and security fix releases.

Another thing that has been mentioned in this thread is the use of Automatix. Automatix is great for those who are on Intel/x86 architectures, for those of us on PPC, i'm afraid we're SOL. In my few weeks of dual booting between OS X and Ubuntu, i've been really impressed with Ubuntu. However, and i don't really mean this as a slight on anyone, i do wish more support was given to what is the default Ubuntu browser - if for no other reason than the peace of mind of its users.

---

### Post by aysiu on 2006-04-20
[QUOTE=godard]the Mozilla folks are recommending all users upgrade to the 1.5 releases from the 1.0 versions. [/QUOTE] Even as of December 2005, [most Ubuntu Forum members were using 1.5](http://www.ubuntuforums.org/showthread.php?t=103393).

---

### Post by towsonu2003 on 2006-04-20
bugs were reported, but devels chose not to patch 1.0.7. Instead, they waited for the 1.0.8 released by mozilla. I don't like this policy either, but it seems there is little to be done by us the users...

[https://launchpad.net/distros/ubuntu/+bug/32083](https://launchpad.net/distros/ubuntu/+bug/32083) (later marked as duplicate of: )
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/30976](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/30976)

PS. afaik, 1.0.8 resolves all security issues found in 1.0.7, though I'm not sure.

---

