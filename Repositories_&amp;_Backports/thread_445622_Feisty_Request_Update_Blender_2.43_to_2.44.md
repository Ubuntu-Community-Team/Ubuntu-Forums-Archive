---
title: "Feisty Request: Update Blender 2.43 to 2.44"
date: 2007-05-16
forum: Repositories &amp; Backports
---

### Post by Statik on 2007-05-16
Hi all,

Since Blender 2.43 is in the repositories for Feisty, can we have it updated like our other programs? Blender just released version 2.44 and it would be nice to have the repositories update with it. I love seeing my little Software Update icon on my menu bar!

Statik

---

### Post by m0ns00n on 2007-05-18
I second that. No use staying with one version just because the next version of ubuntu isn't available yet. I do like to upgrade apps more than twice a year =)

---

### Post by WW on 2007-05-18
> **Statik said:**
> Hi all,

Since Blender 2.43 is in the repositories for Feisty, can we have it updated like our other programs? Blender just released version 2.44 and it would be nice to have the repositories update with it. I love seeing my little Software Update icon on my menu bar!

Statik
That is not how Ubuntu works.  Feisty is frozen, and will not receive updates except for security issues or critical bugs.  The closest thing to an "official" update is if gutsy updates to Blender 2.44, and then someone adds it to the  [feisty backports]("https://launchpad.net/feisty-backports").  If you really need 2.44 in feisty, you will have to compile it yourself, or find a third-party .deb package.

... or you could get a precompiled binary from the [Get Blender]("http://www.blender.org/download/get-blender/") page.  The Linux x86-32 version labeled "Blender 2.44, Python 2.4 (11 MB)" appears to work in Dapper.

---

### Post by Statik on 2007-05-18
So, when Firefox went to version 2, it was only because of security updates that it was added to the repository updates?

My other problem is that I can't seem to find an easy way to update each time Blender updates. The updates on the website are only archives, not packages. I'm never sure if I have properly copied the files to the right places. I am spending so much time learning the apps I don't have time to learn how to make the program work as well. 

Statik

---

### Post by calvinthomas on 2007-05-20
I've been thinking about this kind of thing over the last few days, not for blender specifically but for applications in general. I think it'd be nice to have an unstable repository, or testing, like is done in pclinuxos & debian. I realise the problems this causes in terms of stability if people use it and I'm not saying using it should be recommended but having the option to if you'd like to would be nice I think.

Calv

---

### Post by Statik on 2007-05-20
Even if there was a central place when debs for such things were available and request-able. I don't have time to learn the ins and outs of installing all these apps.

Statik

---

### Post by rsambuca on 2007-05-20
If there is a .deb file available, you don't need to know anything.  You just click on it!!

---

### Post by Statik on 2007-05-20
aye, there's the rub. No Deb that I can find, and no consistent place where I can find it.

Statik

---

### Post by rsambuca on 2007-05-20
I think if you guys want the latest versions of your programs the instant they are released, then ubuntu is probably not the best choice for you.  You might want to consider something with a rolling release schedule instead.

---

### Post by Statik on 2007-05-20
Nah, not the instant they are released, but not 6 months away either. Something happily in between.

---

### Post by rsambuca on 2007-05-21
Either way, by design ubuntu is not for you then.  You will have to either find another distro, or learn to install apps manually.

---

### Post by Statik on 2007-05-21
Or, some helpful fellow could tell me how to make a deb so that if I happen to learn how to update blender myself, I can make the deb avail to all.

Other than that, Ubuntu has been awesome!

Statik

---

### Post by rsambuca on 2007-05-21
> **Statik said:**
> Or, some helpful fellow could tell me how to make a deb so that if I happen to learn how to update blender myself, I can make the deb avail to all.

Other than that, Ubuntu has been awesome!

Statik

LOL, yeah, I would but to be honest, I am not really got at that stuff yet.  All I know is I have done it once and it was something like "make, checkinstall" to make the deb.  But from your previous post, you said you don't have time to learn this stuff anyways!  Make up your mind;)

---

### Post by hardyn on 2007-05-21
it may appear in the gutsey backports.

---

### Post by durand on 2007-05-28
it is in the gutsy backports but that deb doesnt work in feisty...oh and they need to update the deb to use python2.5 instead

---

### Post by waxblood on 2007-05-30
it is possible to download Blender 2.44 binaries from the official site in two versions, one to be used with  python 2.4 and another with python 2.5, No install is necessary, just copy & paste files wherever you want. 

Since Feisty now supports python 2.5, there's no problem using the relative Blender version, I've already tried it. 

Well, to tell the truth Blender keeps exiting abruptly too often :( , but it already did with 2.43 version,  maybe it doesn't like my video card... who knows.

---

### Post by durand on 2007-05-30
Thats what im doing at the moment, i basically looked at the deb package for blender, then copied the relevant file to the correct place...I would rather have it so everything was in the right place than everything is in one blender directory, it feels very untidy that way...

---

### Post by Statik on 2007-05-30
Well, I've done as you suggested . . . Python 2.5 was already installed so I used that one. Only blender and blender-player are in the zip, no blender-bin. I'm not sure what effect this will have. That is the only two new files. The plugins are .c files, so they obviously need to be built but I don't know how to do that. Is there any benefit to building them, or are the 2.43 versions good enough? If so, how do I do it?

Statik

---

### Post by ArtInvent on 2007-06-05
I don't get it. Ubuntu constantly updates packages of all kinds in between major OS releases. They update everything from the kernel to drivers to high level apps. But it's very uneven and things like Blender and other programs - actual useful programs for creating and achieving things - often languish in the repos for months after those projects release a major update. 

Personally, for me the high level apps like OpenOffice and Blender and Audacity and Gimp are far more important than the OS itself. THE APPS are why I use a computer. 

I mean, we don't even have a workable version of Cinelerra in Ubuntu and yet we can turn on silly things like 'Desktop Effects" with one click. Sure, eye candy is nice and everything, but, um, gee maybe it would be nice to have a truly robust and capable video editor. 

Blender 2.44 is not 'unstable.' It's the latest full release. At the least, put it in the repos along with whatever earlier version is 'fully approved' for Ubuntu. Let the user choose one or both. (PS, 2.43 doesn't really work right for me in Feisty anyway.)

And, oh yeah, I don't really want to update my entire OS every six months just to get the latest version of Blender or whatever. 

The ultimate irony to me is that it's very easy to get the latest Blender or the latest Audacity or the Audacity Beta - if I'm using Windows. "Want to enjoy the best apps that Free Software has to offer? Just boot into XP!" Which is exactly what I'm about to do so I can use Blender 2.44. 

Ugh.

---

### Post by waxblood on 2007-06-05
> **waxblood said:**
> it is possible to download Blender 2.44 binaries from the official site in two versions, one to be used with  python 2.4 and another with python 2.5, No install is necessary, just copy & paste files wherever you want. 

Since Feisty now supports python 2.5, there's no problem using the relative Blender version, I've already tried it. 

Well, to tell the truth Blender keeps exiting abruptly too often :( , but it already did with 2.43 version,  maybe it doesn't like my video card... who knows.

@ArtInvent

I'm using Blender to learn its features on Xubuntu, and it seems to work, at least for modelling. I think the problems I mentioned are about the game engine, but are so evident I think they are related only to my system. 

To use v2.44 just do what I said in my previous post.

As for the rest, you must remember the Linux distros in general are still to be considered beta operating systems, so a conservative approach like the Ubuntu's one is perfectly reasonable. Think Ubuntu itself is based on the Debian *unstable* branch! 

Ubuntu is gaining more and more credit much to the fact it *simply works* . To achieve such a result you have to do some compromise.
I've tried various distros before and Ubuntu was the only quite reliable thing I've found.

Ciao,
David

---

### Post by durand on 2007-06-05
> **Statik said:**
> Well, I've done as you suggested . . . Python 2.5 was already installed so I used that one. Only blender and blender-player are in the zip, no blender-bin. I'm not sure what effect this will have. That is the only two new files. The plugins are .c files, so they obviously need to be built but I don't know how to do that. Is there any benefit to building them, or are the 2.43 versions good enough? If so, how do I do it?

Statik

Right, you have to compile the c files included, im not sure why its not already compiled. All you have to do it cd to the plugins directory and then type make. ie:

```

cd plugins
make

```
Then you should have some so files in the relevant directories. You can just copy that over.
By the way, what I did was, I downloaded the blender deb from [http://packages.ubuntu.com/feisty/graphics/blender]("http://packages.ubuntu.com/feisty/graphics/blender") then used gdebi to see whats in it and placed the relevant files in the right place. I had to make some directories as well. As for blender-bin, its not that important, i just copied the blender executable to blender-bin. Oh and there are hidden files in the blender folder you downloaded. Press ctrl + h in nautilus.

---

### Post by sel on 2007-06-05
Blender 2.43 is bugged on the amd64 platform and comes with this warning in it:

```
$ blender -v
The following warning messages come from the Blender coders. The Debian 
maintainers would like to point to the following file for rationales: 
  /usr/share/doc/blender/NEWS.Debian.gz

64 bits compiles will give incorrectly saved .blend files. Do not use it.

*** If you continue to run this executable, you really are quite stupid ***

```

In the interests of not being being 'really quite stupid' I decided that upgrading would be a good thing... I found a nice deb package [here]("http://packages.debian.org/unstable/graphics/blender") (packages.debian.org) that I felt would be a good plan...

trying to install this resuled in complaints:

```
$ sudo dpkg -i /home/sel/Desktop/blender_2.44-1_amd64.deb 
(Reading database ... 159913 files and directories currently installed.)
Preparing to replace blender 2.43-0ubuntu3 (using .../blender_2.44-1_amd64.deb) ...
Unpacking replacement blender ...
dpkg: dependency problems prevent configuration of blender:
 blender depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
dpkg: error processing blender (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 blender
```

So my position as I see it (as a nub) is as follows:
I have a bugged version of blender that warns me that I'd be an idiot to use it.
I don't particularly want to mess with libc6 as AFAIK half the system depends on it...
That leaves me with very manual processes to remedy this issue.

Surely this is a good candidate for a proper repository fix?

Any tips, pointers, workarounds or abuse would be appreciated ;)

---

### Post by durand on 2007-06-05
Does anyone know how to actually make a blender deb? how do the package maintainers do it? That kind of info would really really help with all these problems...

---

### Post by ArtInvent on 2007-06-06
Blender, as  I recall, is one of those few programs that you just stick on your disk somewhere and run the file and it works. So yeah, if you can get the binary, just copy it over. And has been mentioned, the Python v. needs to be matched.

But this is not a well known fact. And most people will assume that they will need a deb file or have to compile it themselves. So they will bitch that it's not in the repos as in this thread. And that also begs the question, since you don't even need to compile it, why doesn't someone just stick in the repos and let people choose, since it's basically zero effort to do so.

And the fact is that Blender is far from the only app that lags in the Ubuntu repos. Here's a typical example: Wine. Wine is available in the standard Ubuntu repos, but it's generally about 4 months out of date. Wine barely works, and in general you will really want to have the latest version because they just might have fixed the bug that causes your favorite app not to work right. You have to enable a special repo just for wine to get the latest v. Another example: Audacity. Audacity has a stable branch 1.2 and a beta series 1.3 that has a whole bunch of very nice features. Both of these seem to work perfectly in Windows, and I have no trouble installing both and running each, at the same time. The last time I checked, Audacity was stuck in the Ub. repos at 1.2.4 while the current release was 1.2.6. The beta, you'd have to compile that yourself. Again, I ask, why is open source software clearly more accessible on Windows than it is on Linux? 

Also, I really take issue with the suggestion that Ubuntu is meant to be an unstable or beta or in some way experimental operating system. I think Ubuntu is supposed to be a polished and mature OS and the vast majority of people who are into it think of it as such. Linux for human beings, right? I think that if you want to be an OS wonk or a Linux geek, go with Debian. Ubuntu is supposed to be for the rest of us.

---

### Post by Mr. Picklesworth on 2007-06-07
First, since I'm a complainer, I'll just join the little rant here for a moment: Apps that have absolutely no imact on the environment around them (eg: Blender, which is completely without integration), and which are in tested major releases that can be trusted, should be trusted as worthy additions to some kind of official or semi-official repositories for an existing release. Granted, though, it is not easy to keep track of updates for the thousands of packages available. Perhaps it could some day become the community's job, but in a reliable / semi-official way?
Remember that centralized updater? That feature is *big*! It is one of the best reasons to use a distro like Ubuntu: It relieves you of the bother of updating software yourself. Unfortunately, this does not currently happen (at all) except for security updates which you get in a central place with *that other OS* anyway. Thus, this great feature is used to the least of its potential and the only way to use it to its actual potential is to enable dozens of unofficial repositories that pose a risk to your system.
There are a few productive solutions I can think of that do not involve changing *the ways*. After all, I agree, it's dangerous to change from the current behaviour.
(Perhaps easily set up application-specific mini-repositories hosted by the application developers themselves and powered by a variety of possible means, such as PHP scripts, feeding Deb or at least source code updates to the centralized updater, registered with APT upon the original installation?). Err, I won't discuss them here since that would be derailing this thread...


Anyhow, moaning aside, this is a good source for debs:
[http://rpmseek.com/rpm-pl/blender.html?hl=com&cs=blender:PN:0:0:2:0](http://rpmseek.com/rpm-pl/blender.html?hl=com&cs=blender:PN:0:0:2:0)

None at the moment for 2.44, but I'm sure there will be eventually :)

As for Sel's problem there... I doubt you'll find a deb for libc6 2.5-5, but you could find the source via Google and compile that, then deal with Blender. That, however, would not be fun.

Edit:
Woah, are you pulling my leg?
Head to Blender.org, under the [Download](http://www.blender.org/download/get-blender/) section, download the tar.gz file for Linux with Python 2.5. Don't be shy.
Now extract it and put it in a nice place, and you can (hopefully) run the executable file called "Blender" fairly easily. You won't have a launcher, though; you must do that yourself by editing the menus.

---

### Post by Statik on 2007-06-07
All I've done is copy the two blender files, blender and blender-player, from the tar.gz to /usr/bin . Thats it. Instant upgrade. I'm still waiting on a response from the blender forums on the necessity of the other files in the upgrade.

Statik

---

### Post by durand on 2007-06-07
Yeah, Ive known that there was a blender binary on the website, its just that debs are built specifically for ubuntu with all the scripts and locale, etc in the correct place. With the website tarball, they are in one directory which is an untidy way to do an install...

---

### Post by sel on 2007-06-07
Ok plan B based on feedback from Mr.Pickles, durand and Statik above...

1. I got a fresh copy from here: [The 64 bit area]("http://www.blender.org/download/get-blender-64-bits/") (blender.org) - and it's the download on the right with python 2.5

2. I extracted it:
```
tar -jxf ./blender-2.44-linux-glibc236-py25-x86_64.tar.bz2
```

3. I ran 'make' in the extracted plugins folder:
```

cd blender-2.44-linux-glibc236-py25-x86_64/plugins
make

```

4. I matched the permissions to match the current installed blender:
```

chmod 644 sequence/*.so
chmod 644 texture/*.so
sudo chown root sequence/*.so
sudo chown root texture/*.so
sudo chgrp root sequence/*.so
sudo chgrp root texture/*.so

```

5. Copied them accross:
```

sudo cp sequence/*.so /usr/lib/blender/plugins/sequence/
sudo cp texture/*.so /usr/lib/blender/plugins/texture/

```

6. Changed the permissions on the  main blender file in the root of the extracted blender directory to match it's predecessor in /usr/bin, and then copy it there:
```

cd ..
chmod 755 ./blender 
sudo chown root ./blender
sudo chgrp root ./blender
sudo cp ./blender /usr/bin/

```

7. Do the same for the player:
```

chmod 755 ./blenderplayer
sudo chown root ./blenderplayer
sudo chgrp root ./blenderplayer
sudo cp ./blenderplayer /usr/bin/

```

8. copy the scripts accross:

```

cd .blender
sudo chown -R root scripts/
sudo chgrp -R root scripts/
sudo cp -R scripts /usr/lib/blender/

```

This seems to have worked for me YMMV - I just use my old menu items as they now point at the upgraded version.

Thanks and kudos to Mr.P, durand and Statik

I think that if the dastardly M$ had released a program that silently saved corrupt files and then decided that patching it as a mater of policy was something for 'the next version' they'd get a lot of abuse...

---

### Post by flawedprefect on 2007-06-08
I can only say one thing: LEGEND.

Worked perfectly.

---

### Post by durand on 2007-06-08
Thanks a lot, sel. Now to work out how to make a deb

---

### Post by ePharaoh on 2007-06-09
> **Mr. Picklesworth said:**
> 
Remember that centralized updater? That feature is *big*! It is one of the best reasons to use a distro like Ubuntu: It relieves you of the bother of updating software yourself. Unfortunately, this does not currently happen (at all) except for security updates which you get in a central place with *that other OS* anyway. Thus, this great feature is used to the least of its potential and the only way to use it to its actual potential is to enable dozens of unofficial repositories that pose a risk to your system.


Well, said Mr P.

I find this lack of flexibility in Ubuntu utterly frustrating!
I am going back to my comfortable ex-love. Gentoo!
;)

Sigh! I did have some good time with Ubuntu though...

---

### Post by Statik on 2007-06-09
I do see the need to limit the amount of software included in the repository updates. There are only so many things that you guys can check on. It would be nice to have MAJOR OS projects included (yes, Blender is definitely a major project, its been around twice as long as Ubuntu and probably has more staff.) However, if I knew how to go through the process of building and installing and creating the deb for each blender, I would. I'd even host it on my own server. Its not that I don't want to, I don't know how and I don't really have the time to go searching high and low for instructions and learning specific tricks from general instructions. If someone can walk me through it, I'll do it all, for the benefit of the community, but I need that initial help.

Rod/Statik

---

### Post by foxmulder881 on 2007-06-11
What the big deal here? Just download the latest binaries from blender.org. Extract it to any directory of your choice (It really doesn't matter where it goes). Then double click on the blender icon in the newly created folder to run application. You should now be using Blender 2.44.

---

### Post by durand on 2007-06-11
Yes, lots of people have said the exact same thing. The difference is that things work differently with the packaged one and with a deb install. The files are in different places and everything's a lot neater. Imagine if you had a lot of software all installed in the same place, wouldn't it be a bit untidy and messy when compared to an apt database where everything is in the right place and you can easily uninstall and upgrade it?

---

### Post by foxmulder881 on 2007-06-11
> **durand said:**
> Yes, lots of people have said the exact same thing. The difference is that things work differently with the packaged one and with a deb install. The files are in different places and everything's a lot neater. Imagine if you had a lot of software all installed in the same place, wouldn't it be a bit untidy and messy when compared to an apt database where everything is in the right place and you can easily uninstall and upgrade it?

I have a "Yes" answer and I have a "No" answer to your post. Let me explain why.

Yes, it is neater to have software installed via a deb install. Why? Because as you explained, the installer puts the files in the correct locations of where they were intended to go. But with saying that, it really doesn't matter where the files are in this case, it'll still work 100%.

No, as I mentioned above, it really doesn't matter where you put the files, it'll 'just work'. durand, I highly doubt that a user has 'that much' software on their system that is run by the method that I have described. On my system, Blender 2.44 is the only one that is run by this method. It's not that hard to keep an eye on your installed software if done in a logical manner. Such as putting the software in the /opt directory and then creating another folder with the software title so that you know where exactly everything is.

In my case, I have it installed in /opt/blender-2.44-linux-glibc232-py24-i386. And then I have a shortcut in the Applications Menu linking to this directory. Simple really. See below for example.

Screenshot...
[IMG]http://img.techpowerup.org/070611/Screenshot.png[/IMG]

---

### Post by durand on 2007-06-12
Yeah, I guessed that you'd say this. All I'm saying is that it is better to install via deb than by the archive method. And since there is already a deb for gutsy, it can't be that hard to make one for feisty.

---

### Post by Statik on 2007-06-12
I'm glad that its easy for you to install the latest version by copying the files. That's great. I've done the same thing. That's great too. Its not because I can't do it that way, or that I'm particularly lazy. I just believe that Blender is one of those essential and identifying pieces of open source, Linux type, applications that are part of the spirit of Ubuntu. The even #'d releases of Blender are bug fixes anyway. I could compromise with only receiving even numbered updates in the repository. However, I'd still like to know how to make a deb from an install so that I could build the latest Blender, install it in the proper places and then make a deb that could be available to all. I think this will help not only the Blender community, but the Ubuntu community as well.

Just because you like installing it in its own folder, as you have, doesn't mean that everyone else should do it that way too. Don't sideline us because we prefer a different method. ;)

Rod/Statik

---

### Post by foxmulder881 on 2007-06-12
> **Statik said:**
> Just because you like installing it in its own folder, as you have, doesn't mean that everyone else should do it that way too. Don't sideline us because we prefer a different method.

I never installed that way because I like to install software like that. In fact, I hate it too. But I didn't see the point in waiting for someone to compile a deb installer when I could be enjoying using the new 2.44 version in the mean time.

Frankly, I don't care whether you do it this way or that way. I was just sharing my knowledge of how to get it working.

The way I see it, if there's no current deb for it, find another way to install it. And that's the conclusion I came up with.

---

### Post by Statik on 2007-06-12
And I'd have to agree with you, since that's what I did as well. But it got me thinking, why isn't a deb available? (which we've discussed) and How could I make it available? (not asking someone to take on the task just because of my foibles)

I hope I didn't offend you there earlier. It wasn't my intention.

Rod/Statik

---

### Post by foxmulder881 on 2007-06-12
No offence taken...

In regards to compiling a deb, I haven't got a clue?!?

---

### Post by Statik on 2007-06-14
Well, it looks like I won't have to figure it out at this time! I just got it as a software update! Thank-you whoever it was who was listening!

Rod/Statik

---

### Post by durand on 2007-06-15
Ive posted in the blender forums, no replies >.<

---

### Post by ArtInvent on 2007-06-19
2.44 made it a few days ago. Yay. 

However, now I start with command blender and it is no longer fullscreen, it is windowed. Drag. I really need the screen real estate. That was a great feature, though I would prefer being able to hit f11 like many Linux programs to toggle between window and fullscreen.

---

### Post by vexorian on 2007-06-19
> **Statik said:**
> So, when Firefox went to version 2, it was only because of security updates that it was added to the repository updates?

My other problem is that I can't seem to find an easy way to update each time Blender updates. The updates on the website are only archives, not packages. I'm never sure if I have properly copied the files to the right places. I am spending so much time learning the apps I don't have time to learn how to make the program work as well. 

Statik
Breezy was the one version using 1.5 and afaik the package was never updated to 2.0 until dapper came in?

---

### Post by WW on 2007-06-19
> **vexorian said:**
> Breezy was the one version using 1.5 and afaik the package was never updated to 2.0 until dapper came in?

The Dapper version of Firefox is still 1.5: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firefox&searchon=names&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firefox&searchon=names&version=all&release=all)

---

