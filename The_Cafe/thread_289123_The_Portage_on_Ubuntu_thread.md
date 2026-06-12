---
title: "The Portage on Ubuntu thread"
date: 2006-10-30
forum: The Cafe
---

### Post by DJ Wings on 2006-10-30
I just read [this thread](http://forums.gentoo.org/viewtopic.php?t=125553) on the Gentoo forums. I've been trying to get my laptop (which runs Xubuntu 6.06) to run as fast as possible, and adding Portage ought to help. I'm install Enlightenment as my window manager, and compiling it from scratch should work nicely. I'm syncing as I speak (s/speak/type/g).

---

### Post by xXx 0wn3d xXx on 2006-10-30
Please tell me how it goes. Having portage on Edgy would be awesome.

---

### Post by chaosgeisterchen on 2006-10-30
What's so good about portage? Having the things compiled and therefore optimized for your system?

---

### Post by compuguy1088 on 2006-10-30
Doesn't Ubuntu have something similar to Portage, specifically apt-build that does pretty much the same things as portage?

---

### Post by shining on 2006-10-30
Please go have fun on gentoo and leave ubuntu users alone ](*,)

---

### Post by maniacmusician on 2006-10-30
........? and what's your problem? did he say something offensive?  He's just trying to make his system run faster. You're telling him to take a hike because he's a gentoo user? please. that's pathetic.

take your elitist attitude and go shove it.

---

### Post by xXx 0wn3d xXx on 2006-10-30
> **chaosgeisterchen said:**
> What's so good about portage? Having the things compiled and therefore optimized for your system?

It's not about compiling...portage it much more powerful then apt. It has pretend options to see what will happen when you install something and much more. I like it but it can be troublesome sometimes.

> Doesn't Ubuntu have something similar to Portage, specifically apt-build that does pretty much the same things as portage?

Sort of. It compiles the packages from source, but not for your architecture. It doesn't use your make.conf file.

> Please go have fun on gentoo and leave ubuntu users alone ](*,) 

Wow ! Thanks ! I just love how this community is changing :) I don't know what I said/did but have a nice day. Later.

---

### Post by plb on 2006-10-30
The difference is minimal at best. Seriously, I've used gentoo for almost 2 years and find apt a much more mature and all around better package manager. There is a reason why debian is the most copied distro out there. Also portage has grown slow with the huge amount of packages available. If you want portage use gentoo. And portage is based on BSDs port system which is much better.

---

### Post by plb on 2006-10-30
> **xXx 0wn3d xXx said:**
> It's not about compiling...portage it much more powerful then apt. It has pretend options to see what will happen when you install something and much more. I like it but it can be troublesome sometimes.


How is more powerful? You know you can build packages from source with apt as well right? If you want to copy something like portage for Ubuntu at least do something proper and use FreeBSDs ports...much better.

---

### Post by shining on 2006-10-30
Sorry, I don't see the point of trying to use portage on ubuntu.
Either use a source based distrib like gentoo, if you believe there is any noticeable benefit, or use a binary based distrib like debian or ubuntu, where you can also recompile packages when you really need to.
You might need to recompile a package for upgrading it, applying a patch, or just changing configure option. See [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) for doing it properly.
But don't do it just for getting better performance, you probably won't see any difference, so it's most likely a waste of time.
Feel free to provide any meaningful benchmark to prove me wrong.

If there is a noticeable difference, and you think it's worth it, then you're better off just using gentoo. It's only about choices and preferences, just pick what suits you the best.

---

### Post by DJ Wings on 2006-10-30
> because he's a gentoo user?
First off, I'm not a Gentoo user. I tried it, installed it successfully with XFCE (extremely minimalist, but it ran REALLY fast), and then switched back to Xubuntu because I wasn't ready yet. I'm a former Gentoo user, and I'm trying to put some Gentoo back into Ubuntu- and not switch completely.
The sync failed; my tree either isn't complete, or it's complaining about a symlink /etc/make.profile. I tried emerging SuperTux as a test package, and it doesn't work. Still, I'm intrigued by the idea.
As for switching completely making the only difference, no. What's the difference, that some key packages (X, kernel, etc) are optimized for your system? If I were to take out all the bloatware, recompile my X system and desktop (and window manager, of course) from scratch, it would probably run as fast as Arch.
And if you have something against Portage (which, by the way, is a ton l33ter than apt-get), then compile your packages from source. Recompile your X server, and you'll notice something.
> Please go have fun on gentoo and leave ubuntu users alone
So, you want me to switch? Fine, I'll buy some Sabayon CDs. At least that has a working Compiz/Beryl/Aiglx. Kidding, but really, watch it.

---

### Post by Turtle.net on 2006-10-30
Based on my own experience (ok that's maybe not such a relevant example ... let say that's an illustration) I never noticed any performance improvement when I used gentoo on my computer, but I noticed a lot of trouble and invested time in compiling and recompiling.
Eventhough that was a real investment on the knowledge side ... that was not such a good investment on the performance side...

---

### Post by zenwhen on 2006-10-30
Any more insults in here and I am editing posts containing them to contain only the full text of the current GNU GPL License.

---

### Post by spockrock on 2006-10-30
Seriously I dunno why people have to blow up on some one pointing out, one can use portage on ubuntu.  Its their os, they can add and modify it as they feel necessary, that is why we use gnu/linux right? Second, there is no harm in sharing, making snide remarks and flaming will only discourage people from posting stuff like this.

---

### Post by chaosgeisterchen on 2006-10-31
Thanks for the information. It sounds really interesting but I fear that it most assuredly won't integrate perfectly into the Ubuntu system, doesn't it? Debian-based distributions are built on emphasis of dpkg and apt. I see no reason to change unless the system becomes faster.

---

### Post by kuja on 2006-10-31
> **xXx 0wn3d xXx said:**
> It has pretend options to see what will happen when you install something and much more.
Something wrong with "apt-get -s"?

---

### Post by -Rick- on 2006-10-31
If you want to compile your packages (with customized CFLAGS etc) you could also try NetBSD's (portable) [pkgsrc]("http://www.netbsd.org/Documentation/software/packages.html").

---

### Post by christhemonkey on 2006-10-31
There was also a thread somewhere about using apt-make for a genbuntu type derivative...

So adapting apt to use CFlags and the like for recompiling from source.


Here is that thread:
[http://ubuntuforums.org/showthread.php?t=208595](http://ubuntuforums.org/showthread.php?t=208595)

---

### Post by funkyade on 2006-11-07
Speaking as both an Ubuntu and Gentoo user (I have two identical AMD machines, one with U and one with G) and Gentoo on my PPC machines, I can confirm that in my experience Gentoo IS faster. However, this speed comes more from being able to minimally configure packages with USE flags, eg leaving out unecessary KDE, GNOME, and so on dependencies resulting in a smaller executable file, thus improving speed due to there being less memory swapping. I have used the GCC -Os optimisation flag as I found that -O3 is unstable when you least expect it. Compiling a vanilla kernel also helps somewhat, something that you are usually stuck with in Ubuntu unless you want a great deal of hassle. In addition, although Portage is very cool, I do agree that it has become very slow over the last year or so, and I much prefer aptitude/synaptic style package managment - although Kuroo has a very good stab at it.

I would generally install Gentoo on lower-end machines as they need the performance boost you get from the points I made above.

Gentoo is a great OS, but then so is Ubuntu. There is no reason why the two can't co-exist.

---

### Post by boban on 2006-11-07
> **funkyade said:**
> Speaking as both an Ubuntu and Gentoo user (I have two identical AMD machines, one with U and one with G) and Gentoo on my PPC machines, I can confirm that in my experience Gentoo IS faster. 

+1, but I have both distros installed on one machine... And Gentoo is a bit faster (you can tell the difference especially in X) - even thou Gentoo is installed on slower hdd. But Ubuntu is far "easier" and require less maintenance...

And -O3 flag most of the time is hurting performance - executables are getting too big...

---

### Post by regeya on 2006-11-16
I've been tempted to try Portage on Gentoo myself, but only if I can relocate packages to /usr/local or something.  Ubuntu is great, but I have two minor nits:  One, there are packages that Ubuntu cannot legally package, and two, for the same reason some of the Debian stuff in Universe is crippled out of necessity.  So it'd be nice to have an equivalent to Fink to fill in the gaps that, quite frankly, will always be there and cannot be easily fixed.

---

### Post by shining on 2006-11-16
> **funkyade said:**
> Speaking as both an Ubuntu and Gentoo user (I have two identical AMD machines, one with U and one with G) and Gentoo on my PPC machines, I can confirm that in my experience Gentoo IS faster. However, this speed comes more from being able to minimally configure packages with USE flags, eg leaving out unecessary KDE, GNOME, and so on dependencies resulting in a smaller executable file, thus improving speed due to there being less memory swapping. I have used the GCC -Os optimisation flag as I found that -O3 is unstable when you least expect it. Compiling a vanilla kernel also helps somewhat, something that you are usually stuck with in Ubuntu unless you want a great deal of hassle. In addition, although Portage is very cool, I do agree that it has become very slow over the last year or so, and I much prefer aptitude/synaptic style package managment - although Kuroo has a very good stab at it.


All this seems to make sense.

> 
I would generally install Gentoo on lower-end machines as they need the performance boost you get from the points I made above.


But that wouldn't be my conclusion. Using a source based distrib on a lower-end machine is even more painful.
If that was the only way to be able to do something usable with it, I guess it would be fine, but it isn't the only way.
You can either try to use a lighter Ubuntu, by switching to a lighter desktop and lighter applications.
Or you could try other distributions which work nicely with lower-end machines, like this one:
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

Again, that's only my opinion.

---

### Post by funkyade on 2006-11-17
> But that wouldn't be my conclusion. Using a source based distrib on a lower-end machine is even more painful. If that was the only way to be able to do something usable with it, I guess it would be fine, but it isn't the only way.

Yes, it IS painful! I do quite a few installations and use a virtual machine on a fast computer to do the installation then use partimage to 'install' the new install on the target computer. This works well for old computers that I use for various purposes - particularly 486, P-1, and P-2 machines. Updating them takes forever if you do it on the actual machine - I tend not to need to though - as they are single purpose installs. 

I am using gentoo in this situation because it gives me the performance boost I need, but also because the tools I need to use have ebuilds which makes installing and setting them up very easy in comparision to DSL, CRUX, etc... which I have to do from source. As long as I don't start compiling stuff on the actual machine but do it in a VM it is okay. I recently compiled a plain kernel on one of these machines as a speed test and it took over two days!

---

### Post by usernamebob on 2006-12-09
Okay.. sorry to bring up a semi outdated thread.. but it interested me somewhat..

Long ago (okay.. so maybe 2 or 3 years at most) I got into linux somewhat.. after trying out a few distros I ended up using gentoo.. and found that setting up use flags probably made a fair difference to speed (not cflags though they did seem to help in a tiny amount) of course all these performances increases were purely from my perspective.. and not benchmarked in any reasonable way..
anyway.. my main job at the moment is in audio engineering.. and basicaly.. for the level I was working at linux audio software didn't cut it (actualy.. it still doesn't.. but it's closer).. but yeah.. I went back to windows till about 2 months ago, when I decided I ought to get around to trying out linux again..

I was gonna go back to gentoo.. but one of my friends convinced my to try out ubuntu first.. and I've had that on my system since (it's now on my sisters laptop too (she saw mine and loved it) and will be on my parents computer also (they were interested in it.. and when I said there was no adware they asked me if I could please set it up for them)) But I've been thinking about trying gentoo for awhile..

anyway.. so doing some research now it seems that most people seem to dislike gentoo now (it used to be one of the most popular.. what happened?) and there seem to be a general consensus that all optimisations that can be done give almost no performance gains.. Which is a fairly different story to what I was hearing before. Though it does seem that ebuilds arent being maintained well these days, and that would explain some of it's loss of popularity.

Do Use/cflags give measureable performance gains?..

---

