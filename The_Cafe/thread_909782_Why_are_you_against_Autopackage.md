---
title: "Why are you against Autopackage?"
date: 2008-09-03
forum: The Cafe
---

### Post by Extreme Coder on 2008-09-03
I've read some of the threads on this forum, and I couldn't help but notice that a lot of people here are against Autopackage becoming the de-facto way of installing third party software in Linux. Why is that?

It offers everything DEB/RPM/TGZ/(Insert format of package here).
Sure,  DEBs can be easily installed, but these types have a lot of shortcomings(need root,have to install multiple packages for certain types of programs, have to make type for each distro..) and Ubuntu is not the only Linux distro available, and others have and will always exist.

Debs and RPMs should be used for installing system software, like GTK/QT, kernels, drivers and so on. But if you need for example to install the latest version of Pidgin, you shouldn't have to jump in hoops, look for compiled packages and so on.

My hope is that with the next LSB, Autopackage should be included. But it will never happen, what makes the Linux world special is the inability to agree on a standard.. (In the end, I will get fed-up and move to PC-BSD :P )

So what do you think? Arguments, opinions?

Ahmad

---

### Post by mrgnash on 2008-09-03
Because it murdered my father.

---

### Post by MaxIBoy on 2008-09-03
I've never heard of it, but I'm already worried about how you implied that Autopackage doesn't require root access. 


Also, do you realize how many "standards" have wound up adopted by only one or two distros? Basically this sounds like Yet Another Obscure Package Format (tm) on top of the pile.



It's also not possible to avoid having to install multiple packages when you have unfulfilled dependencies (otherwise each package would have to contain basically a full distro, and the same distro every time at that.) Just be glad the DEB format tells you *which* other packages you need.

---

### Post by Extreme Coder on 2008-09-03
> **MaxIBoy said:**
> I've never heard of it, but I'm already worried about how you implied that Autopackage doesn't require root access. 


Also, do you realize how many "standards" have wound up adopted by only one or two distros? Basically this sounds like Yet Another Obscure Package Format (tm) on top of the pile.



It's also not possible to avoid having to install multiple packages when you have unfulfilled dependencies (otherwise each package would have to contain basically a full distro, and the same distro every time at that.) Just be glad the DEB format tells you *which* other packages you need.
Why is it a problem for root access? It is designed so that end-users can use it to install non-core software. There are a lot of systems where users don't have access to root privileges, requiring a root password to install such software is a flaw itself.
And Autopackage has been around since 2003 if I remember correctly.

It is not a package format for just a distro or two, it's designed to be used with all of them.

And dependencies would be solved by distros actually conforming to the LSB, which contains a set of requirements and dependencies, all distributions should have, as common ground for running applications. Hopefully this will improve by the next release of it, which is soon.
and as I said before, DEBs will always be used for Debian-based distros only.


> Because it murdered my father.
Please keep useless posts out of the topic, kthxbai.

Most of what hinders Linux is political, not technical.

---

### Post by saulgoode on 2008-09-03
Making egg cartons is easy. The real work is in making the eggs.

---

### Post by Extreme Coder on 2008-09-03
> **saulgoode said:**
> Making egg cartons is easy. The real work is in making the eggs.
Assuming that I actually got what you meant, there are a lot of eggs out there that would reach more people if better egg cartons were made :)

---

### Post by loell on 2008-09-03
I don't know of anyone who hates autopackage, but i know a bunch who likes deb packages so much so that they won't entertain any other packaging system. 

from a users point of view, in parallel with a free software developers perspective,

**If it ain't broke, keep using it **:)

---

### Post by MaxIBoy on 2008-09-03
> **Extreme Coder said:**
> Assuming that I actually got what you meant, there are a lot of eggs out there that would reach more people if better egg cartons were made :)




That's like saying all OSs should be Windows because most programs are for Windows. If it was true, we wouldn't be here. 


Also, forcing programs to work with the LSB and nothing else would eliminate a lot of really useful stuff. You should have a right to create your own interdependent APIs and toolkits, and furthermore you should have a right to release them separately. 


The LSB seems to have picked RPM because its governing body is under the misconception that the LSB contains all dependencies ever, so dependency handling isn't needed. This can never be true and it's a good thing too.

---

### Post by FuturePilot on 2008-09-03
> **Extreme Coder said:**
> I've read some of the threads on this forum, and I couldn't help but notice that a lot of people here are against Autopackage becoming the de-facto way of installing third party software in Linux. Why is that?

It offers everything DEB/RPM/TGZ/(Insert format of package here).
Sure,  DEBs can be easily installed, but these types have a lot of shortcomings(need root,have to install multiple packages for certain types of programs, have to make type for each distro..) and Ubuntu is not the only Linux distro available, and others have and will always exist.

Debs and RPMs should be used for installing system software, like GTK/QT, kernels, drivers and so on. But if you need for example to install the latest version of Pidgin, you shouldn't have to jump in hoops, look for compiled packages and so on.

My hope is that with the next LSB, Autopackage should be included. But it will never happen, what makes the Linux world special is the inability to agree on a standard.. (In the end, I will get fed-up and move to PC-BSD :P )

So what do you think? Arguments, opinions?

Ahmad

I've wondered the same thing myself. I think Autopackage is great and I just wish it was used more. People complain about not having 1 type of installation format, well there's an answer to that sitting right here in Autopackage, yet there are some people that would rather see Autopackage die and I have no clue why.

---

### Post by toupeiro on 2008-09-04
I'm against ANYTHING that would circumvent a challenge/response root elevation (a.k.a sudo), or an su - and install anything in any place other than /home/username

What do you think this is, Windows?

Last time I looked, make and install works on all platforms too, and last I looked, gzipped tar files are supported in UNIX/Linux as far back as I can remember, which is pretty far. :)

---

### Post by MaxIBoy on 2008-09-04
Hear, hear! I very much want a standard package format, but not one that is so insecure. And I'd prefer DEB to be picked because many packages are already compiled in DEB format (same could be said for RPM, but RPM features dependency hell.)

---

### Post by toupeiro on 2008-09-04
> **MaxIBoy said:**
> Hear, hear! I very much want a standard package format, but not one that is so insecure. And I'd prefer DEB to be picked because many packages are already compiled in DEB format (same could be said for RPM, but RPM features dependency hell.)

I've actually had very good success with alien to convert packages between rpm and deb.  Hell, I've even had luck converting them to solaris pkg format.  Its not as if people are without very easy means to take one format and make it work for another.  Autopackage may be great, but for that matter, so is a shell script.  I guess I just don't understand why I should sacrifice decades of inherant UNIX security to use autopackage, when the package environments as they are are obviously no showstopper.

alien command usage:
> Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch	    Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version		    Display alien's version number.


---

### Post by EdThaSlayer on 2008-09-04
Personally, I like auto package because it makes everything much easier to do since it is sure to "work" most of the time. Also, I can use any linux OS and install the same program and it will work on all of them instead of getting separate compiled versions(debs, rpm, etc...).:)

---

### Post by Polygon on 2008-09-04
people are against it because it most likely makes incorrect debs or doesn't make them according to debian policy...doesn't handle dependencies....etc

---

### Post by loell on 2008-09-04
> **Polygon said:**
> people are against it because it most likely makes incorrect debs or doesn't make them according to debian policy...doesn't handle dependencies....etc

heh, you're most likely talking about checkinstall. :lolflag:

---

### Post by Extreme Coder on 2008-09-04
@FuturePilot & EdThaSlayer: Finally, someone who agrees with me! :P

@toupeiro: So you'd rather have new users to other distros go aliening packages, with a chance that it might not work, or mess up their system?

Or you want them to go learn how to make and install, with finding correct dependencies instead of double clicking on an autopackage, and follow instructions?

It doesn't need the system password because it doesn't install system wide!

@MaxlBoy: Yeah sure, I'm pretty confident in Red Hat and Novell converting their businesses and their distributions to using DEBS instead of RPMs, they will be glad to:rolleyes:
and RPM Dependency hell is a thing of a past btw.

---

### Post by loell on 2008-09-04
users may not hate autopackage, but after scanning [http://autopackage.org/developer-quickstart.html]("http://autopackage.org/developer-quickstart.html")

I think its the developers and potential packagers are the one hating it. ;)

also for the benefit of the discussion, can you explain? if its not system wide then its just userwide? if so, what if you have 4 users in one system, then all 4 users will have to install each same software 4 times?

---

### Post by Extreme Coder on 2008-09-04
> **loell said:**
> users may not hate autopackage, but after scanning [http://autopackage.org/developer-quickstart.html]("http://autopackage.org/developer-quickstart.html")

I think its the developers and potential packagers are the one hating it. ;)

also for the benefit of the discussion, can you explain? if its not system wide then its just userwide? if so, what if you have 4 users in one system, then all 4 users will have to install each same software 4 times?
It's not as hard as you think. I successfully made a few for my own needs, it's easy.

---

### Post by Closed_Port on 2008-09-04
> **loell said:**
> 
**If it ain't broke, keep using it **:)
The point is though, that they argue that it is broke. And seeing how much of a clusterf... it is to actually get your packages out to people who want to use them, I'd have to agree.

> **MaxIBoy said:**
> That's like saying all OSs should be Windows because most programs are for Windows. If it was true, we wouldn't be here. 
Nope, it's not like saying this at all. Would you care to explain how wanting to deliver software in an easy way to every linux user out there is the same as saying all OSs should be windows?

> **MaxIBoy said:**
>  
The LSB seems to have picked RPM because its governing body is under the misconception that the LSB contains all dependencies ever, so dependency handling isn't needed. This can never be true and it's a good thing too.
This has to be one of the most uninformed comments I ever had the displeasure to read.
RPM doesn't resolve dependencies and DEB doesn't resolve dependencies. Package managers like apt do (for both debs and rpms).
Don't you think you should at least have a basic understanding of the issue before commenting on it?

About autopackage, I think that it's to complicated and has technical issues. Though I certainly don't claim to have a firm grip on each of the issues discussed, take a look at these critical takes on the subject for example:
[http://www.licquia.org/archives/2005/03/27/autopackage-considered-harmful/](http://www.licquia.org/archives/2005/03/27/autopackage-considered-harmful/)
[http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys/](http://kitenet.net/~joey/blog/entry/autopackage_designed_by_monkeys/)

I also think that autopackage has already failed in that it simply has not been successful despite being around for some time now.

Finally, I find systems like klik much more appealing and interesting:
[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by Keyper7 on 2008-09-04
> **Extreme Coder said:**
> I've read some of the threads on this forum, and I couldn't help but notice that a lot of people here are against Autopackage becoming the de-facto way of installing third party software in Linux. Why is that?

Because there's no such thing as a de-facto way in Linux.

For a specific distro, okay. But why reduce freedom in Linux as a whole?

---

### Post by zekopeko on 2008-09-04
well on the issue of installing programs without root privileges...

it's not a security issue since by default the rest of the system is closed to a normal user so even if you do run a nasty app the only thing thats gonna get nuked is the user's home. And since the user installed the app it's her problem.

i haven't heard anything about klik2 in a while and that thing was a dream come true. Mac's DMG way of "file-is-an-app-(libs-included)" on linux mmmm...

---

### Post by cb951303 on 2008-09-04
correct me if I'm wrong but if an autopackage (ie: pidgin) is compiled on platform X there is always a chance that it will not work on platform Y because of library version diffrences...
that's enough all by itself to not use it

---

### Post by Polygon on 2008-09-05
because linux is not binary compatible, its source compatible.

and the whole point of requiring root access to install programs is:

a: lets you know your doing something that may damage the system.
b: lets you restrict users you dont want to install stuff.
c: and this is just a security flaw waiting to be exploited, you can now install programs without root access, so its now even easier to install malicious standards
d: deb and RPM have been around for much longer times, much more stable and battle tested
e: we already have too many packaging formats, we don't need another one.

the whole POINT  of having dependencies is so only one copy of a library needs to be installed on the system, and every program can use it. With windows, every program you install may have a copy of a library that it needs to run, even if 500 other programs are installed that use that same library. So therefore you get much more bloat.

also, its easier to upgrade as if one library gets upgraded, it effects all programs that use it.

and also, if properly packaged, dependencies are no problem. it takes just an extra 2 seconds to download, which would of been spent downloading the package again from an autopackage package.

and of course, "what isnt broke, dont fix it!"

---

### Post by stimpack on 2008-09-05
I will take a look at Autopackage, as I think DEBs have many shortcomings.

The best method I have seen so far is the .app that Apple use, so simple and elegant. Copy it into home directory for single user, or copy it to the Applications folder for all users, you only grant root to the copying. Files stay in the .app directory and are not scattered all over your system.

---

### Post by lukjad on 2008-09-05
I am going to make a few foolish assumptions here.
1) Autopackages means something along the lines of Automatix.
2) That .DEB formats (and the like) are not Autopackages.
3) I know what I am talking about. (:

I don't like anything that has a "one size fits all" policy. In my experience, "one size fits all" fits no one. If you want to install a file, programs like Automatix seem to make a hash of it. It's sort of like putting a computer together. You can just grab any old piece, jam it into the socket and pray it works. And, most of the times, it will. However, if you make a little mistake like plugging the keyboard into the mouse slot (old tech here) or you jam the wire into the hard drive too hard, you will start getting problems. Most can be easily fixed by an experienced user, but to a new user, this can prove difficult. Also, if someone can just bypass sudo, then there is little use in having a password since anyone can walk up to your PC and install whatever they want.

A cautionary tale:
During the break for my computer class while I stepped away from my (Dualboot Ubuntu/XP) PC and when I came back 5 minutes later, a classmate had installed a program in XP that controlled my desktop. In Ubuntu that would have been very hard (if not impossible) without my jealously guarded password. 

A second cautionary tale:
This classmate walked away from his PC and came back to find all his setting changed and his computer unable to connect to the Internet.


The basic reason you want sudo is for security. You don't want just anyone coming up to your PC and mucking around with it.

---

### Post by Zyphrexi on 2008-09-05
it hides my socks

---

### Post by lukjad on 2008-09-05
I have never heard of this program "socks". Let up go to the Flame Thread and discuss this further.

---

### Post by frup on 2008-09-05
Forgive me now for my ignorance but if a program does not require root permissions to install, why does the binary need to be packaged at all?

One of the few sets of "binary downloads" I have had experience on Linux with is that of Songbird and Firefox.... For these I can download the tar.gz and extract to a folder called /Firefox or /songbird in my /~ for example and run it from there. Fantastic, all that's missing is the menu entry/icon and that is something that could be worked out with Gnome/KDE

BUT as soon as you're talking about installing in to /bin and /usr and /usr/bin etc. How does this not require root permissions? I prefer being able to use Add/remove and Synaptic and apt-get as they are to the rather clunky method of installing Songbird and Firefox (not the standard, I last did this from firefox 1.5.x to 2.0 on dapper I believe).

---

### Post by Polygon on 2008-09-06
> **stimpack said:**
> I will take a look at Autopackage, as I think DEBs have many shortcomings.

The best method I have seen so far is the .app that Apple use, so simple and elegant. Copy it into home directory for single user, or copy it to the Applications folder for all users, you only grant root to the copying. Files stay in the .app directory and are not scattered all over your system.

but then to upgrade you have to manually download any updates.

and also, same thing with windows, stuff has to be static linked so you end up with bloat, and if an exploit was found in some common library, then it would take a while (if ever) for the applications using it to fix itself.

and since the end user doesn't end up really caring either way, it doesn't matter if all the files are just in one .app package or if they are spread across the system but controlled by apt, since you can install, uninstall and upgrade programs in both systems easily

> **frup said:**
> Forgive me now for my ignorance but if a program does not require root permissions to install, why does the binary need to be packaged at all?

One of the few sets of "binary downloads" I have had experience on Linux with is that of Songbird and Firefox.... For these I can download the tar.gz and extract to a folder called /Firefox or /songbird in my /~ for example and run it from there. Fantastic, all that's missing is the menu entry/icon and that is something that could be worked out with Gnome/KDE

BUT as soon as you're talking about installing in to /bin and /usr and /usr/bin etc. How does this not require root permissions? I prefer being able to use Add/remove and Synaptic and apt-get as they are to the rather clunky method of installing Songbird and Firefox (not the standard, I last did this from firefox 1.5.x to 2.0 on dapper I believe).

because ubuntu and most other distros have standards and policies of doing things, and what files of a program are placed where. For example, for debian/ubuntu, the man files have to be placed in a certain directory, the icons have to be placed in /usr/share/pixmaps, there has to be a gnome menu entry, etc. Sure, downloading the .tar.gz works as well, but the whole point of the package is installing all the different files (icons, man pages, menu entries, so on) to the correct directories, which saves you the time of downloadng teh tar.gz and manually copying all of that to the directories yourself

---

### Post by kirsis on 2008-09-06
> **mrgnash said:**
> Because it murdered my father.

Hello. My name is Inigo Montoya. You killed my father prepare to die.

*stabs Autopackage*

---

### Post by t0p on 2008-09-06
> **Extreme Coder said:**
> Why is it a problem for root access? It is designed so that end-users can use it to install non-core software. There are a lot of systems where users don't have access to root privileges, requiring a root password to install such software is a flaw itself.

Does this mean that apps installed by non-sudo users will be installed in the user's home directory? 

> **Extreme Coder said:**
> 
And Autopackage has been around since 2003 if I remember correctly.


Autopackage has been around for 5 years?  And hasn't caught on yet?  Wow, it must be *really* good!!  :)

---

### Post by loell on 2008-09-06
> **t0p said:**
> Does this mean that apps installed by non-sudo users will be installed in the user's home directory and will run without any root privilege? 


yes, with bloated static linking of libraries needed to run, its possible.

---

### Post by joninkrakow on 2008-09-06
> **loell said:**
> yes, with bloated static linking of libraries needed to run, its possible.

The disadvantage being???? Seriously, with mongo-huge hard drives, this is _really_ less of an issue than many of us (myself included) have made it out to be. I've recently done an about-face on this point. Hard disk space is like dirt now. No big deal. 

There are problems with dynamic libraries, as people with eeePCs discovered when they tried to add non eeePC repos to their system. Adding the wrong lib can really break things. Dynamic libraries kind of limit one's ability to upgrade as you would wish. One simply waits for the distro to upgrade, not when one wants. So, for instance, my wife is still stuck with OOo 2.0, because her distro (Xandros on the eee) hasn't upgraded it yet. :-P (I noticed that 2.4 is what is on Ubuntu still, but I really prefer the 3.0 beta I'm using in Puppy. 

The truth is simple, each system has trade-offs... Nothing's perfect. Right now, I'm happy with apt and debs. 

-Jon

---

### Post by Guilden_NL on 2008-09-09
> **lukjad007 said:**
> 
A cautionary tale:
During the break for my computer class while I stepped away from my (Dualboot Ubuntu/XP) PC and when I came back 5 minutes later, a classmate had installed a program in XP that controlled my desktop. In Ubuntu that would have been very hard (if not impossible) without my jealously guarded password. 

A second cautionary tale:
This classmate walked away from his PC and came back to find all his setting changed and his computer unable to connect to the Internet.

The basic reason you want sudo is for security. You don't want just anyone coming up to your PC and mucking around with it.

Ahem, why would you walk away from an unsecured system?  Windows allows you to quickly lock your desktop in <5 seconds. :rolleyes:

It's quite easy to quickly hose up an Ubuntu system as well.  

Lack of good security procedures places systems at risk with any OS.

---

### Post by lukjad on 2008-09-09
True. But in Ubuntu you need sudo to make a real dent in the system. I usually lock the system. However, you sometime forget to do basic security percautions. It happens to the best of us. :)

---

### Post by cardinals_fan on 2008-09-09
> **lukjad007 said:**
> True. But in Ubuntu you need sudo to make a real dent in the system. I usually lock the system. However, you sometime forget to do basic security percautions. It happens to the best of us. :)
It isn't hard to set up a limited user account in Windows (and use SuRun if you like sudo behavior).

---

### Post by lukjad on 2008-09-09
I like to USE my computer when I am on it. (I'll look into the SuRun though. Thanks!)

---

### Post by toupeiro on 2008-09-09
> **Extreme Coder said:**
> 

Or you want them to go learn how to make and install, with finding correct dependencies instead of double clicking on an autopackage, and follow instructions?



um... well.... yeah, whats wrong with instructions???????  


and for that matter, why not use apt-get when on ubuntu, or yum when on redhat/fedora, which takes care of all the dependencies. Quite frankly, alien does a beautiful job at converting packages, when I do have the rare occurrence to need it. I dont know what kind of experience you have with it...  And I do trust its ability to translate a package better than some universal wrapper thats seemingly not supported by ANY mainstream distro that I've looked into.  I'd rather use subversion to pull down source and dependencies so you have 100% complete make/install procedures EVERY TIME than hope the wrapper that works now will work later.

---

### Post by cardinals_fan on 2008-09-09
> **lukjad007 said:**
> I like to USE my computer when I am on it. (I'll look into the SuRun though. Thanks!)
How does using the computer require administrative privileges?

---

### Post by lukjad on 2008-09-10
I am installing and uninstalling programs all day long. I don't have time to log out and log in again to an admin account. ;)

---

