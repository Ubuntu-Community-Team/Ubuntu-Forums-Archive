---
title: "Unifying Linux - Relative Paths"
date: 2007-12-28
forum: The Cafe
---

### Post by Yfrwlf on 2007-12-28
Keep in mind I'm a bit of a noob so please correct and teach me and others if there is less of an issue here than I think there is, or whatever.  Input!  Communicate!  Voice your opinions!

Seems to me like something that could help developers and administrators and users (or quite simply, everyone) always know where to access libraries and such would be if everything had a relative name.  I wanted to hear if anyone had any input about such an idea. :)  I think this would go a long way in making the silly structural differences between, say, Red Hat and Debian distros, not matter.  It'd even allow everything to eventually be all moved to the same place in the future because it simply wouldn't matter.

Sort of like ~ is universal for home, what if there was a special relative path term for say, all of this kind of library, or all libraries period, or how about init?

Example:

(lib)/
'/apache restart

These universal bash changes could be made with very little effort, and wouldn't this further help Linux to be *cross-distro*, pushing back fragmentation of a very nice operating system?  I think it's as important enough for users and developers to keep things like this in mind as it is to keep licensing in mind.  Freedom hinges on these kinds of decisions.  Keeping some standard methods of communication around that aren't detrimental to anything and only promote universal learning and unification of Linux is not a bad thing.

I know that relative paths are used a lot already in scripts, config files, and programming, so it seems to me that to expand upon that to easily allow a new system that was totally distro-independent would be easy.

OK OK, I'll break down and say or just put things in the same damn place, but I know that solution won't fly and that's why I'm presenting this one. ;)  Standards really should be promoted more...but instead it's "OUR system is the standard!  No, ours is!"  No, I'm not saying differences are bad, I'm saying having a universal way to communicate as long as it's not at all detrimental is not.  **Standard APIs, methods of communication, whatever you want to call them, take away no one's freedom, but instead give everyone more**, including saving everyone time which some people find valuable.

P.S.  Yeah yeah, Linux is just the kernel, I know.  It'd be nice if it was modular enough to be swapped out with other kernels, too.  I'd really like to see "Linux" become a collective of standardized APIs more than anything, allowing for true modularity, program competition, and cross-distro-and-platform-ization.  It really shouldn't matter what distro you're running or what kernel it has as long as it meets certain standards of communication.

---

### Post by 23meg on 2007-12-28
Have you read the LSB specification?

---

### Post by Palmyra on 2007-12-28
Welcome to this community.

I should warn you that there might be a flood of people telling you that this issue has been discussed already.  It might happen.

---

### Post by Yfrwlf on 2007-12-28
> **Palmyra said:**
> Welcome to this community.

I should warn you that there might be a flood of people telling you that this issue has been discussed already.  It might happen.

Well I'm not a total noob, I have 170 or so beans. ;)  I haven't seen this particular issue being discussed before, so if it has then, well, here it is again, don't reply if you're not interested in rehashing! :)  Or you could post a link to the old one I guess..

> **23meg said:**
> Have you read the LSB specification?

The LSB specification defines where init should go?  How about libraries?  But, are they in the same location on, say, both Red Hat and Debian systems?  I was under the impression that they aren't, even though I haven't looked yet (why can't you start a computer that has no video card!?  Curses!).  But I guess what I'm getting at is if you made Bash so that it had relative paths for everything pretty much, then you could make programs be completely independent of distro lock-in, and you'd have less problems to worry about between DEB and RPM package formats, too.  I dunno maybe I'm crazy. :P  Or just need more information.  Or both.

---

### Post by 23meg on 2007-12-28
You really should read it. Not because it's a panacea; it has plenty of room for criticism, but it will be a good basis that will help you understand the issues (and non-issues) better.

---

### Post by toupeiro on 2007-12-28
Definately not a noob question! :)  Nor were any of the other question posts I've seen you post.  (a.k.a. don't underestimate yourself!)

what you are asking for has existed for quite some time -- its usually only used in the business world.  

**warning**  T_he following process is not for the faint of heart (not something a newbie to unix/linux wants to take on without understanding native linux networking, exports, NIS, automounting, and linux permissions)_  I'll touch on the basic concepts because the question was asked about relative paths.
**--------------=============================================== START OF LONG RELATIVE PATH EXAMPLES=====================================------------------**
One of the most efficient ways (and one of the most beneficial circumstances) to do this would require a NIS domain, and an automounter like [AMD (Automounter Daemon)]("http://en.wikipedia.org/wiki/Berkeley_Automounter") then create NIS maps for what you want like a:

amd.map.machines: <tab delimited>

machine1   x86-linux     insert_physical_location_here
machine2   x64-linux     do_the_same
machine3   solaris-sparc     and_again_the_same
machine4   irix             you_guessed_it


then a data map like amd.map.data <tab delimited>

firefox     x86-linux    hostname.fully.qualified:/path/to/exported/firefox/location
firefox     x64-linux   hostname.fully.qualified:/path/to/exported/firefox/location
evolution  generic      hostname.fully.qualified:/path/to/exported/evolution/location

you could even do a users map if you wanted to so the user has the same home directory on every system, again, all map metafiles have to be tab delimited on your NIS master domain controller.

username     generic     hostname.fully.qualified:/path/to/exported/user/home


you can make the map names whatever you want, but in my example, generic will contain data that can be opened regardless of platform.  x86-linux will contain 32-bit linux specific data and x64-linux will contain 64-bit etc etc..


Now, you configure AMD to look at the NIS maps (usually /etc/amd.conf when AMD is installed)
so in the amd.conf you would tell it you NIS information, and where you want it to start its tree (like /amd which I believe is the default setting)
then link various directories through the /amd path once the daemon is started.

the structure, if you research AMD will be: (in a parient child directory structure)  *curses forums for removing my space delimiters*

/amd 
       /domainname
                           /platform (generic,x86,x64 etc)
                                                                            /map (data,users, etc) 

so to make the platform independant users map, link /users or /home  to /amd/domainname/generic/users.  for the data map, link /data to /amd/domainname/x64-linux/data (or x86-linux or whatever the machine happens to be)


so, basically with any AMD enabled system using the above example config, when you go to **/data/firefox**, AMD will create a link under /data called firefox, pointing to the correct version of firefox for the platform you are trying to access firefox from.  The beauty of this is it gives you one path that works across many different platforms and one install per platform to focus on.  And, its not NEAR as network taxing as you might think.  

**--------------=============================================== END OF LONG RELATIVE PATH EXAMPLES=====================================------------------**

That being said, I don't recommend going to all this trouble if you only have a discrepancy between say fewer than 10 machines, because as you can see there is a considerable amount of setup and app config to do, and knowledge required of NIS/NFS and security.  I do something pretty similar to this for a few hundred systems, and it works beautifully.  UNIX and linux do have a[ physical path standard]("http://www.tuxfiles.org/linuxhelp/linuxdir.html") which developers are expected to follow.  I cannot say that all developers and distributions do.  The above AMD configuration would consist of isolating an install down another directory tree other than it was intended for, which is why I say its not for beginning users.  For local, un-networked linux systems, it just makes more sense to follow the standard for the platform you are trying to use.  If you want a little transparency without  a complete infrastructure change,  consider modifying your $PATH variables to include the directory paths you need that are not in the standard structure or already in your $PATH.  Another variable most developers use is $LD_LIBRARY_PATH.  add the paths you need to this variable and your apps will find what they are looking for.

you can do this by doing something like setenv LD_LIBRARY_PATH ($LD_LIBRARY_PATH /path/one /path/two /path/three)     <--- c shel scripting being used here.  I think in bash you just type export  LD_LIBRARY_PATH=$LD_LIBRARY_PATH;/path/one;/path/two

if you just want to extract RPM and DEB files to use on systems with conflicting package management, try these commands (in a /tmp directory), and place them accordingly.

for DEB: ar xv <package>.deb

for RPM: rpm2cpio whatever.rpm | cpio -idv
for RPM pre/post install scripts try: rpm -q -v --scripts -p whatever.rpm


I hopeI  posted in context to what you were asking :)

---

### Post by Yfrwlf on 2008-01-04
> **23meg said:**
> You really should read it. Not because it's a panacea; it has plenty of room for criticism, but it will be a good basis that will help you understand the issues (and non-issues) better.

Will do, thanks for the suggestion, I'm curious to learn just what the difficulties are.  I see Ubuntu 6.06 is in there because it's LTS, so I'm assuming 8.04 will be tested and compliant as well.  I've heard the testing process can be a bit lengthy...I wonder if they have an automated way to test compliancy, that'd be helpful...

> **toupeiro said:**
> Definately not a noob question! :)  Nor were any of the other question posts I've seen you post.  (a.k.a. don't underestimate yourself!)

Thanks, though I do know that there's *tons* I don't know, but I also know that sometimes it takes an external perspective to find ways to resolve problems.  I mean, come on, it's Linux, you can do anything you want, and powerful easy ways of doing things get a lot of attention and standards can exist around them and be used by them.  There are always ways to solve any problem!

> **toupeiro said:**
> what you are asking for has existed for quite some time -- its usually only used in the business world.  

<snip>

I hopeI  posted in context to what you were asking :)

Wow, that's pretty neat, I figured there may have been a way to do it, thanks for sharing. :)

For the package installation issues (universal package management!  I've complained enough times about it..) I guess the important part may be the fact that it takes effort to unpack DEBs and RPMs and manually place the files where they need to be when your package manager can't understand those file formats.  What I mean is simply that if the package managers were more intelligent, or were compatible with both package types, that'd solve that problem.  Of course you want to make it easier to do things.  Computers are there to compute for you.  While you may learn some things by doing it manually, issues like these being resolved will make everyone's life easier, including developers and admins.

But back to the paths thing.  Honestly, this may not be a huge issue, but at the same time, it may be something that *does* cause a lot of problems down the road that just are sort of ignored, but tell me if I'm wrong and why if so.  I think most admins simply use locate and find frequently any way to find files, and they can use them on distros they aren't familiar with to locate the proper paths where the programs and config files are found.  But, again, that's doing some work to get something that if it were the same on all systems, wouldn't be required, eliminating a step and some effort, making guides easier, making programs needing to look for things easier, etc.  The guide you showed me is a patch for a small group of computers that takes effort to set up.  It's a nice solution to have available, but I guess I'm just asking the following question:

Could any aliases for bash or other shells, or any other fixes, be done to make it easier for programs to find libraries and the like, or is that not really and issue, and regardless what about making it easier for admins and such?  Why not have something as frequently used as /etc/init.d/ be aliased by, say, I dunno what special character you could use, not many left for use...~c perhaps, if that's possible, for the place where all configuration files are stored.  ~c/apache/, ~c/init.d/, ~c/bash/, ~c/whatever.  Just an idea.  It might catch on!

I think having universal installation packages that work on nearly every version of nearly every distro is a much more important issue though, but I just wondered if this pathing differences issue could be partially contributing to this problem as well.

Thanks for your input on this possibly silly subject regardless. :)

Off topic, but if anyone is interested in the unifying Linux installation packages topic, check the links on [here]("http://www.linux-foundation.org/en/Packaging").

---

### Post by Yfrwlf on 2008-01-04
I found [Gobo Linux]("http://www.gobolinux.org/?page=at_a_glance")'s file system layout pretty interesting.  Wonder if it could ever catch on.  Perhaps it's possible for it to if a reverse of the remapping that is described there on their page is used, and if Compile catches on.

---

