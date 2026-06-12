---
title: "Are we going to see Java SE 6?"
date: 2006-12-11
forum: Repositories &amp; Backports
---

### Post by rivasdiaz on 2006-12-11
Java SE 6 is released and came with lots of new features and a big speed boost. The Distributors License for Java SE 6 is ready so we could expect a version packaged for Ubuntu.

Java SE 5 was released for Dapper after Dapper was released, so I hope we can  install some sun-java6 packages (hopefully along with the sun-java5 packages). Are we going to see sun-java6 packages for Edgy??

Another question. Why sun-java5 packages are not updated when a new version is released? I installed sun-java5 v1.5.0-06 on Dapper and v1.5.0-08 on Edgy, and now I see v1.5.0-10 on Fiesty. Why v1.5.0-10 is not available for Edgy if it is a bug fix release?

Anyone has comments?

Thanks,
rivas

---

### Post by samjh on 2006-12-12
I very much hope that Fiesty will have JRE6 and JDK6 in its package repositories.

But realistically speaking, an upgrade to Java 6 is really not that much of a priority at the moment.  Most enterprises will not be adapting Java 6 so soon after its release.  Therefore, most professional Java programmers will not be working with Java 6 either, unless it is purely for private or non-business use.

If I had my way, I'd like to see Java 6 JRE and SDK on Feisty.  Feisty's release is still some months away, so surely a very significant piece of software like Sun's Java could be packaged for it.

---

### Post by giorgosts on 2006-12-12
You can always install jre-6 manually, by:
1. uninstalling any previous versions
2. downloading the  new jre-6 from sun [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
3. reading the instructions [http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting)
4. moving it under /usr/lib/jvm/
5. chmoding +x the binary (you can't build debs with fakeroot and java-package at the moment)
6. executing the self-extracting file
7.(not necessary after post  #5) (updating the links of /usr/bin/java and /usr/bin/java_vm to the new java location, since the update-alternatives --config java mechanism for selecting java doesn't work anymore)
8. updating the mozilla, firefox, swiftfox, opera java plugin links. 
see also the notes from sun about the java plugin [http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#plugin](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#plugin)

It's better to wait for debian and/or ubuntu to include the new jre-6 in the java-package tool for building the relevant debs, cause then you can use the alternatives mechanism cleanly to select the java you want to work with, and not break your system.

---

### Post by giorgosts on 2006-12-13
> **rivasdiaz said:**
> 
Another question. Why sun-java5 packages are not updated when a new version is released? I installed sun-java5 v1.5.0-06 on Dapper and v1.5.0-08 on Edgy, and now I see v1.5.0-10 on Fiesty. Why v1.5.0-10 is not available for Edgy if it is a bug fix release?

Anyone has comments?

Thanks,
rivas

see [http://www.azureuswiki.com/index.php/Java](http://www.azureuswiki.com/index.php/Java) a how-to update to a newer java. Be carefull though to select up to 1.5.0-10 because the tools to build the debs don't work with jre-6.

---

### Post by jan247 on 2006-12-14
You can add java 6 to update-alternatives:

```

sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.6.0/bin/javac 30
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.6.0/bin/java 30

sudo update-alternatives --config javac #then choose javac6 
sudo update-alternatives --config java #choose java6

```

---

### Post by giorgosts on 2006-12-14
Thanks ever so much

---

### Post by ijanos on 2006-12-17
I recommend to add this too:
```

sudo update-alternatives --install /usr/lib/firefox/plugins/libjavaplugin.so firefox-javaplugin.so /usr/lib/jvm/jdk1.6.0/jre/plugin/i386/ns7/libjavaplugin_oji.so 30
```
and then:
```
sudo update-alternatives --config firefox-javaplugin.so
``` 
and choose a 1.6.

---

### Post by Hairy_Palms on 2006-12-17
it works perfectly if you just run the setup file in /usr/lib/jvm then change the link 
java-1.5.0-sun
to point to the new 1.6 folder

---

### Post by olaf-g on 2006-12-20
As I am a java developer I need the sdk. So here is my howto for installing the j2sdk. The jre has got less tools to update in the alternatives.

**Repository packages you'll need**
[LIST]
[*]build-essential
[*]fakeroot
[*]java-common
[/LIST]

**Install the patched java-package**
Download the patched java-package from [this post]("http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15") or my attachment below. Untar it
```
tar xvfz java-package-0.28ubuntu1.tar.gz
```
Install it
```
sudo dpkg -i java-package_0.28ubuntu1_all.deb
```

**Create the package**
Download Java 6 from sun and cd into the same directory. Now issue
```
fakeroot make-jpkg jdk-6-linux-i586.bin
```

Finally install it
```
sudo dpkg -i sun-j2sdk1.6_1.6.0_i386.deb
```

**Update the alternatives**
general for jre
```
sudo update-alternatives --config java
sudo update-alternatives --config javaws
sudo update-alternatives --config firefox-javaplugin.so
```

sdk alternatives
```
sudo update-alternatives --config javac
sudo update-alternatives --config rmiregistry
sudo update-alternatives --config rmic
sudo update-alternatives --config rmid
```

Better check all your alternatives. I prefer to leave the jar tool with gcj as this native and has no new features.
for sun java
```
ls -la /etc/alternatives/ | grep j2
```
and for gij stuff
```
ls -la /etc/alternatives/ | grep java
```

Have fun with mustang

---

### Post by sabitha on 2006-12-20
failed here :
after doing this 
> fakeroot  make-jpkg jre-6-linux-i586.bin
.....
.....
Done.

Testing extracted archive... okay.

cat: /usr/share/java-package/sun-j2re1.6/install: No such file or directory

Aborted (/usr/share/java-package/sun-j2re1.6/install).

Removing temporary directory: done

what&#347; wrong. help please..!!

---

### Post by mlind on 2006-12-20
@ sabitha
download the package again, reinstall the .deb. Should work now.

---

### Post by sabitha on 2006-12-20
i reinstall the package like you said but not work. stil the same 
> ........
........
Creating jre1.6.0/lib/plugin.jar
Creating jre1.6.0/lib/javaws.jar
Creating jre1.6.0/lib/deploy.jar
 
Done.

Testing extracted archive... okay.

cat: /usr/share/java-package/sun-j2re1.6/install: No such file or directory

Aborted (/usr/share/java-package/sun-j2re1.6/install).

Removing temporary directory: done

---

### Post by mlind on 2006-12-20
> **sabitha said:**
> i reinstall the package like you said but not work. stil the same

I just tested it myself with 1.6 jre and it works. Make sure you use the package attached in post
[http://www.ubuntuforums.org/showthread.php?p=1877195#post1877195](http://www.ubuntuforums.org/showthread.php?p=1877195#post1877195)

---

### Post by lzap on 2006-12-21
> **jan247 said:**
> You can add java 6 to update-alternatives:

```

sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.6.0/bin/javac 30
sudo update-alternatives --install /usr/bin/javac java /usr/lib/jvm/jdk1.6.0/bin/java 30

sudo update-alternatives --config javac #then choose javac6 
sudo update-alternatives --config java #choose java6

```

You have forgot applets:

```
sudo update-alternatives --install /usr/bin/javac javac /opt/java/jdk1.6.0/bin/javac 30
sudo update-alternatives --install /usr/bin/javac java /opt/java/jdk1.6.0/bin/java 30
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /opt/java/jdk1.6.0/jre/plugin/i386/ns7/libjavaplugin_oji.so 30

sudo update-alternatives --config javac # and select ...jdk1.6.0...
sudo update-alternatives --config java  # and select ...jdk1.6.0...
sudo update-alternatives --config mozilla-javaplugin.so # and select ...jdk1.6.0...
```

In Czech: [http://lukas.zapletalovi.com/blog:jak_nainstalovat_javu_6_v_ubuntu_debianu](http://lukas.zapletalovi.com/blog:jak_nainstalovat_javu_6_v_ubuntu_debianu)

---

### Post by sabitha on 2006-12-22
> **mlind said:**
> I just tested it myself with 1.6 jre and it works. Make sure you use the package attached in post
[http://www.ubuntuforums.org/showthread.php?p=1877195#post1877195](http://www.ubuntuforums.org/showthread.php?p=1877195#post1877195)

yes i already use the package attached but still got eror.
just to make sure i saw this is for jdk, can this use for jre couse i install for this (jre-6-linux-i586.bin) please some advise.

---

### Post by mlind on 2006-12-22
> **sabitha said:**
> yes i already use the package attached but still got eror.
just to make sure i saw this is for jdk, can this use for jre couse i install for this (jre-6-linux-i586.bin) please some advise.

Yes, I tested with both jre and jdk. Both work. Patched java-package is now versioned as ubuntu2, do you have that one installed?

---

### Post by sabitha on 2006-12-22
> **mlind said:**
> Yes, I tested with both jre and jdk. Both work. Patched java-package is now versioned as ubuntu2, do you have that one installed?

after installed java-package vers. ubuntu2 i&#7743; succeded. thank you so much for help. :)

---

### Post by mlind on 2006-12-22
> **sabitha said:**
> after installed java-package vers. ubuntu2 i&#7743; succeded. thank you so much for help. :)

no problem, glad to help :)

---

### Post by lotsahelp on 2006-12-27
Worked for me, thanks. As a note, if installing on a box without x installed, you get some warning about x11 dependencies.

Also, this has been the best how-to I have read for linux in a while. Actually specified the build-essential package which no-one ever does. I am very grateful when no assumptions are made. Makes getting into this easier.

---

### Post by mlind on 2006-12-27
Feisty has Ubuntu provided **sun-java6** packages to get Java 6.0.

---

### Post by Tzalidar on 2007-01-01
Perhaps we should make a wiki page about this?

---

### Post by apapww on 2007-01-03
--------------------------------------------------------------------------------

Thanks ever so much[.](http://hk.yahoo.com)[.](http://www.ec2biz.com)[.](http://www.rthk.org.hk)[.](http://www.ads28.com)[.](http://www.ec2biz.com)[.](http://www.top1.com.hk)[.](http://www.ads28.com)

---

### Post by msundman on 2007-01-12
> **samjh said:**
> realistically speaking, an upgrade to Java 6 is really not that much of a priority at the moment.  Most enterprises will not be adapting Java 6 so soon after its release.  Therefore, most professional Java programmers will not be working with Java 6 either, unless it is purely for private or non-business use.

That's utter BS!

Many enterprises will want to start using java 6 within a year, which means that the branch of that version will either have been created already or be created very soon, and at that point the developers (such as myself) will need java 6. Sure that we won't start using our java 6 based system until 2007 Q3 or Q4, but we start making it now.

Still, even if I would want java 6 purely for private or non-business use, why should I have to go through hoops of manually installing it in a non-ubuntu (or should I say non-debian) way? Your contempt for "private" and "non-business" users make me sick.

Still, even if you completely disregard both private/non-business users and early-adopting professionals/enterprise developers I still don't understand why java 6 can't be added alongside java 5. Since there already are java 6 packages for feisty, what reason could there possibly be for not having java 6 packages also in edgy and dapper?

The latest dapper java is 1.5.0_06 FFS! "Long term support" my a&#115;s!!!

---

### Post by phossal on 2007-01-12
I wrote this [tutorial for a simple install of JDK6, eclipse and Tomcat. ]("http://ubuntuforums.org/showthread.php?t=332674") Ubuntu is *awesome*, but it's worth knowing how to use your system without relying on the Ubuntu-specific implementations and/or the package manager. 

For what it's worth, our company rebuilt all of our existing java projects for JDK6 on the day of release.

---

### Post by msundman on 2007-01-12
> **phossal said:**
> I wrote this [tutorial for a simple install of JDK6, eclipse and Tomcat. ]("http://ubuntuforums.org/showthread.php?t=332674") Ubuntu is *awesome*, but it's worth knowing how to use your system without relying on the Ubuntu-specific implementations and/or the package manager.
That's just wrong in so many ways.
I used to make custom java debs and put them on the company's internal deb repository, but now that there are official java packages I'd much rather use them. That's not quite possible in ubuntu, though, since the ubuntu folks apparently think security updates can be freely ignored even for a new "LTS" release.

> **phossal said:**
> For what it's worth, our company rebuilt all of our existing java projects for JDK6 on the day of release.
That might be possible for small projects and if you don't want to take advantage of features found in the new version, but for large projects where you also want to do significant changes (such as converting io->nio a few years back) it'll take a lot of time.

---

### Post by phossal on 2007-01-12
> **msundman said:**
> That's just wrong in so many ways.

? Our department had JDK5 (updates 6-10) and JDK6 on the day of release. Using a computer to do *work*, like running JDK6 is not *wrong* in *any* way. Are you being trollish or naive? If you're commenting on avoiding the package managers, the proof is in the pudding. I can slide a daily JDK update into 12 machines off a flash drive in a few minutes. It works for us, and for a thousand other people. It's a simple way to get up and running. To even make a statement like the quote above is *nonsensical.*

> **msundman said:**
> That might be possible for small projects and if you don't want to take advantage of features found in the new version

You're right. It's possible for small projects. You're right again, it's possible if you don't want to take advantage of features found in the new version. You didn't mention that it's possible for *large* projects. And it's possible for projects where you *do* want to take advantage of new features.

---

### Post by msundman on 2007-01-12
> **phossal said:**
> [blah blah.. non-deb installation is OK.. blah blah]
You apparently subscribe to the philosophy of *"If it's stupid but works, then it's not stupid!"* whereas I think *"If it's stupid but works, it's still stupid!"* so let's just agree to disagree on this one.

> **phossal said:**
> You didn't mention that it's possible for *large* projects. And it's possible for projects where you *do* want to take advantage of new features.
Sorry, you lost me. We probably agree, but just to make it clear: I think it's impossible to do several man-years of work regarding a complex transition from one java version to another over night. (An underlying assumption I made but didn't mention was that non-final java releases are not used even by developers.)

---

### Post by msundman on 2007-01-12
If anyone's interested, here are the java6 backport "bug" reports for _[dapper]("https://bugs.launchpad.net/dapper-backports/+bug/78619")_ and _[edgy]("https://bugs.launchpad.net/edgy-backports/+bug/78620/")_.

---

### Post by phossal on 2007-01-12
> **msundman said:**
> I'll ignore what you say, tell you what you think, and then make a bunch of nonsensical arguments to refute the point I've made for you. Get ready.

Take a break from yourself. Even *I'm* tired.

---

### Post by msundman on 2007-01-12
> **phossal said:**
> [QUOTE=msundman]I'll ignore what you say, tell you what you think, and then make a bunch of nonsensical arguments to refute the point I've made for you.[/QUOTE]
That's a serious misquote.
I'm sorry if I interpreted your nonsensical ramblings (such as *"Using a computer to do work, like running JDK6 is not wrong in any way."* WTF?! Seriously thinking anyone is against computers working or just trying your hardest to misinterpret things?) incorrectly, but the part about *"avoiding the package managers"* (as is reflected in my *"non-deb installation is OK"* summary) was the only thing I thought was relevant. If you feel I was wrong or left out something important then please do correct me (and if you are correct I will gladly and humbly stand corrected), but don't start spewing BS rhetoric or misquotes.

---

### Post by phossal on 2007-01-13
Let me say this as simply as I can:

If you're not a complete idiot, and having JDK 6 is your goal, I can help with that. I've been recently banned for calling a guy an idiot. He certainly is. You might be one too, and your next post will make it obvious. It'll be worth the ban. If you're not an idiot, or a troll, you'll let this go.

---

### Post by msundman on 2007-01-13
> **phossal said:**
> Let me say this as simply as I can:

If you're not a complete idiot, and having JDK 6 is your goal, I can help with that. I've been recently banned for calling a guy an idiot. He certainly is.
You know I'm capable of creating my own deb packages (which is the ubuntu way of installing programs), so I have no idea why you would think I'm
1) having problems installing java 6 on dapper/edgy, or
2) would want to install java 6 your (non-ubuntu) way.
I'm not saying that you are thinking any of those things, but if you are then you have misunderstood me and if you are not then I have misunderstood you.

> **phossal said:**
> You might be [an idiot], and your next post will make it obvious. It'll be worth the ban. If you're not an idiot, or a troll, you'll let this go.
I couldn't care less if you think I'm an idiot, and I have no idea what you want me to let go. Once more, if there is something to be clarified or resolved or whatever then describe it *plainly*, but exclude rhetoric and definitely exclude personal attacks. I will try my best to follow the same advice.

So, unless you have something else than instructions on how to install java 6 without involving the package manager then I thank you for your advice but respectfully decline to follow it. Have a nice day.

---

### Post by mlind on 2007-01-13
how the heck you guys were able to get this thread flaming? please don't post on this thread anymore unless you got anything constructive to say, thank you.

---

### Post by phossal on 2007-01-13
> **mlind said:**
> how the heck you guys were able to get this thread flaming? please don't post on this thread anymore unless you got anything constructive to say, thank you.

Sorry. I thought I *did* have something to say. I offered up a way of installing (any version of) the [JDK, eclipse and Tomcat]("http://ubuntuforums.org/showthread.php?t=332674") that wasn't (in the past) commonly known

A lot of new programmers come to Ubuntu thinking that working with eclipse and Tomcat is *easier*. I did. Plus, when I switched over, I had no idea how to make my own .debs, or any other package. Some people really benefit from having an easy method.

---

### Post by plheide on 2007-01-24
> **samjh said:**
> But realistically speaking, an upgrade to Java 6 is really not that much of a priority at the moment.  Most enterprises will not be adapting Java 6 so soon after its release.  Therefore, most professional Java programmers will not be working with Java 6 either, unless it is purely for private or non-business use.

Most enterprises start develop their products years before they are released. So many "professional" Java programmers work with Java 6 already.. So to me, it sounds like a good idea to always support the latest Sun Java releases..

---

### Post by louisgag on 2007-02-12
> **giorgosts said:**
> You can always install jre-6 manually, by:
.......
7.(not necessary after post  #5) (updating the links of /usr/bin/java and /usr/bin/java_vm to the new java location, since the update-alternatives --config java mechanism for selecting java doesn't work anymore)
......

thanks! Thats pretty much the hint I needed to complete my JAVA JRE 6.0 installation! :KS :KS

---

### Post by MadMan2k on 2007-02-12
> **msundman said:**
> I couldn't care less if you think I'm an idiot, and I have no idea what you want me to let go. Once more, if there is something to be clarified or resolved or whatever then describe it *plainly*, but exclude rhetoric and definitely exclude personal attacks. I will try my best to follow the same advice.

So, unless you have something else than instructions on how to install java 6 without involving the package manager then I thank you for your advice but respectfully decline to follow it. Have a nice day
just ignore him. I got flamed about pretty much the same point by him, when I put up some java6 debs for edgy...

---

### Post by phossal on 2007-02-12
Yeah, just ignore me. The package doesn't *do* anything, except create a security risk. I trust SUN. Most *serious developers* trust SUN. To waste any time installing a 3rd party package to get JAVA when it provides no value, is delayed significantly, and poses a *risk* just because you're in love with (and apparently don't know how to manually configure) the package manager is bizarre. 

You'll still have to configure the plugin, and set the classpath for javac and javaws. While I do occasionally recommend that people pull the package, it doesn't make *more* sense to use it. If you want an older version or the latest version, it's a moot point anyway. 

I'm sorry if I upset you guys, or ruined your impression that by packaging JDK 6 you had provided a significant gift to the world. It simply isn't true. 

Get over it, guys.

---

### Post by msundman on 2007-02-13
> **phossal said:**
> You'll still have to configure the plugin, and set the classpath for javac and javaws.

You shouldn't have to. If the package doesn't adjust the appropriate environment defaults then it should be fixed. I've never had to configure any plugin or adjust any classpath on ubuntu.

> **phossal said:**
> While I do occasionally recommend that people pull the package, it doesn't make more sense to use it.

Right.. just as it doesn't make sense to use any package. Just install all programs manually. Don't even use "apt-get source". Just sudo-run vendors' non-distro-specific install scripts that copies who knows what who knows where. And who needs easy updating? And nobody could ever want automatic updating, that's just for lazy ignoramuses! Besides, why should different software ever be installed the same way? What would be the fun in that? Things should be cumbersome and hard to do, so that you get a sense of achievement when you occasionally manage to keep your system from further degrading towards chaos and/or accumulating more cruft.

Seriously, there will always be people who want to do things *The Right Way*(tm), so get over it, and if you won't help then just STFU.

---

### Post by phossal on 2007-02-13
> **msundman said:**
> [COLOR="Gray"]Right.. just as it doesn't make sense to use any package.[/COLOR]
I didn't say that.
> **msundman said:**
> 
 [COLOR="Gray"]Just install all programs manually. Don't even use "apt-get source". Just sudo-run vendors' non-distro-specific** install scripts that copies who knows what who knows where**.[/COLOR]
You're kidding, right? You trust a third-party package to auto-install your stuff ahead of SUN's .bin file?
> **msundman said:**
> [COLOR="Gray"]And who needs easy updating? And nobody could ever want automatic updating, that's just for lazy ignoramuses! [/COLOR]
Downloading Java from SUN doesn't prevent easy updating. Besides, what do you imagine Ubuntu could update SUN's latest release *to?* SUN provides the releases. Nothing could be easier than downloading the latest version, rather than hacking together a package (six months after the release). Apparently packaging before installing is easier to you?
> **msundman said:**
> 
[COLOR="Gray"]Besides, why should different software ever be installed the same way? What would be the fun in that? Things should be cumbersome and hard to do, so that you get a sense of achievement when you occasionally manage to keep your system from further degrading towards chaos and/or accumulating more cruft. Seriously, **there will always be people who want to do things *The Right Way*(tm)**, so get over it, and if you won't help then just [COLOR="Red"]STFU.[/COLOR][/COLOR]
The *right way* doesn't exist in an absolute sense, especially for Unix/Linux OSes. The package system is useful quite often, but it's just a tool. **When it doesn't work (or when it lags painfully behind), I adapt it to me, not the other way around.** I think we can agree that you're allowed to do whatever you want with your system, and that if you want the latest *Java*, you can simply download it from SUN the day it's released, integrate it with your system, and be on your way. 

Typing *STFU* is a touch immature, but is totally consistent with your inability to communicate your point, unless your point peaks somewhere above your eyebrows. Perhaps you're as much of a beginner at life as you are at Ubuntu?

---

### Post by msundman on 2007-02-13
> **phossal said:**
> You trust a third-party package to auto-install your stuff ahead of SUN's .bin file?

Yes! If I feel even remotely suspicious I can inspect the package much more easily than I could even begin to reverse-engineer Sun's binary. Anyway, the package I'd use would be made from Sun's release by a friend who has no reason to do my system any harm. Also, I don't at all trust sun to know where what is supposed to be in my distro. For all I know Sun might put stuff in the places where fedora has things instead of where ubuntu has them. Also, I don't at all trust Sun's scripts won't leave tons of cruft after I've installed one version, then upgraded it to another version, then uninstalled.

> **phossal said:**
> Downloading Java from SUN doesn't prevent easy updating.

It doesn't? I have no idea how to update the previous version to the newest one. I'd have to hunt for some upgrade instructions from somewhere and even if I would find something like that I'd still have to do everything manually instead of everything being done completely automatically.

> **phossal said:**
> Besides, what do you imagine Ubuntu could update SUN's latest release *to?*

To the next version, of course! Duh!

> **phossal said:**
> Nothing could be easier than downloading the latest version

That's an outright lie. It's much easier to have ubuntu automatically check, download and update all installed programs every day. There is no way anyone could think it's simpler to manually check sun's website every day and then when there is a new release you have to find some instructions on exactly how to update your old system for everything to work (e.g., should you remove the old version before installing the new, or after, or will some parts upgrade automatically, or will some stuff have to be copied before installing so that the new version won't overwrite modified files from the old version, etc.?), then download the file manually and install it manually.

> **phossal said:**
> six months after the release

The main point was that the official packages should **not** be lagging behind much, wasn't it?

> **phossal said:**
> Apparently packaging before installing is easier to you?

**Yes!** It's a bit more work for one person, and a lot less for hundreds, totalling to a lot fewer manhours.

> **phossal said:**
> The *right way* doesn't exist in an absolute sense, especially for Unix/Linux OSes.

There is no right way to install software in ubuntu (which was what we were talking about)?!? Are you kidding me??? You are simply unbelievable.

> **phossal said:**
> if you want the latest *Java*, you can simply download it from SUN the day it's released, integrate it with your system, and be on your way.

Nobody has claimed you can't. I won't bother asking what your point is because by now it's clear that you don't have any relevant points at all.

> **phossal said:**
> Typing *STFU* is a touch immature, but is totally consistent with your inability to communicate your point, unless your point peaks somewhere above your eyebrows. Perhaps you're as much of a beginner at life as you are at Ubuntu?

Wow! That's so mature. You are so obviously not a beginner at life, and you are such an Ubuntu guru that has indubitably used ubuntu/debian a lot more than the meager 10 years I have. Now I clearly see that you indeed should not shut up when you won't help.

---

### Post by phossal on 2007-02-13
I'm sure there are plenty of people who agree with you. I don't want to waste any more time in this thread. We've each provided our point of view. People can choose for themselves. I don't blame you for choosing the easy road, but it isn't necessarily the *right* road as you claim. I'm surprised a self-proclaimed decade-long user of Ubuntu/Debian isn't better able to grasp the details involved with a direct installation of Java. Regardless of how *you* think, though, a direct installation is a good (if not the only) solution in many scenarios. It detracts nothing.

---

### Post by swv on 2007-05-26
This is something I never thought of- you can't download Java 6 SDK (or 5 or 4..) from Sun's site. It just never occurred to me at all that, java being run on a VM would not be available ... huh... 

Well, to tell the truth, I have to make a living and get things done here. If Java 6 is not beign made available on Linux, then I have to go back to M$. 

I have no idea what Sun is thinking... I can't even download from their site... it's just says "fatal error"  and as far as I can tell, that's the way it's going to stay for whatever reason....

Can't say I didn't try Linux.... back to giving that a**hole more money...

---

### Post by phossal on 2007-05-26
All previous versions are available at [http://java.sun.com](http://java.sun.com) -> Java SE -> Previous Releases

---

### Post by growltiger on 2007-07-19
Okay, I found a solution here:  <https://launchpad.net/ubuntu/gutsy/+source/java-package/0.31>

This is for gutsy.  I am using feisty (which is at 0.28).  Anyway, I took tar filel; expanded it; and then installed it.  I was then able to convert 6u2 from bin to deb and then install that.

---

