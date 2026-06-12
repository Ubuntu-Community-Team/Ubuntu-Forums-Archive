---
title: "ubuntu criticism"
date: 2007-07-13
forum: The Cafe
---

### Post by sulekha on 2007-07-13
Hi all,

   I found criticisms in the name of tips at the following site:
  [http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html](http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html)
  
 to what extent these are true????

---

### Post by Espreon on 2007-07-13
Okay it was criticising Dapper Drake (still a little brat by my standards), Feisity is more mature.
Dapper was 2 releases ago!

---

### Post by strider1551 on 2007-07-13
I'll comment on a few things.

From #4:
> What this entails is installing the “build-essential” package...but of course, how would you know that as a new user? Check the manual. Crap. No manual. Check the online resource (wiki, etc.). If you didn’t know the first thing about forums and weren’t very good at using google (e.g., you listen to music and check email on yoru PC and that’s about it...which takes care of a large chunk of normal users) how would you know to do this? You wouldn’t.
If you aren't good with Google and you only use your computer for music/email (i.e. a casual user), what are the chances that you need to install something from source?  Moreover, what are the chances that you know *how* to install from source with the exception of needing build-essential  installed?  I'm not saying that this doesn't happen, just that the group of people who need things outside the repository and who can find things outside the repository and who don't know how to find help are a very limited number of people.

From #5:
> If you’re going to use or are using Ubuntu, you’re not taking advantage of the optimizations that i586 and i686 instruction sets have to offer
I used Arch Linux for several months, which is optimized for i686, and I have to say that my computer wasn't noticeably faster.  Besides, if the perfectionist in you want i686 optimization, you can always set your own CFLAGS and whatnot and "sudo apt-get -b source <package>"

---

### Post by mcduck on 2007-07-13
1. Keep in mind that Ubuntu IS NOT the only Linux out there
True

2. If you’re afraid of the shell (aka command line), Ubuntu may be scary for you.
As will any other Linux distro ;). At least you can do even most of administrative tasks with graphical tools. it's just that most instructions you find from web will be for CLI.

3. Ubuntu doesn’t come with an owners manual or User Guide
Wrong. System/Help (or whatever the true path is) includes manuals for just about all your apps, some other tasks, information about Linux and Ubuntu and how to do al basic tasks, install multimedia codecs and DVD support, mounting of drives and so on. (most of Ubuntuguide is actually included in the help :o)

4. You can’t install from source with Ubuntu without configuring the ability to compile from source.
Configurin? I suppose this is about the fact that you need to run a single command to install all tools needed for compiling. But the truth is that most people who would be interested inpoints 1, 2 and 3 are not likely to need to compile anything. And the rest can just use that simple command to get the tools needed.

5. Ubuntu will never be as fast as other Distributions; it’s not optimized for it.
Wrong. Even older versions of Ubuntu had optimized kernels in repositories, and since 6.10 Ubuntu's kernel has enabled correct optimizarins for your CPU at boot time. Ubuntu's packages are also alreadty compiled with several optimizations.

---

### Post by sir_cheats_a_lot on 2007-07-13
the only things in that article that wasn't discredited in the comments was that ever distribution is different and you may find another distribution that fits you needs better, and also there is the need to install 3rd party proprietary video drivers from command line. often times  its just "sudo ./filename.bin" from terminal.  there are instructions on the vendors  website on how to do it.   it would be nice however to see those drivers included in the ubuntu install CD though. 
 
 honestly its rare to HAVE to install anything from source, and in most cases from command line.  the package manager works fine; just enable all the repositories, then click reload as it says in the manual. every thing you need is there.  recently had to search for the restricted codecs, and the package for dvd playback, for whatever reason they were removed from the repository. but at least those were in a .deb package file already.  for the most part though everything you need is in the repository.  Devnet obviously didn't look in the "system menu" at all.  i only open the command line to play neverwinter nights, even then its just "cd nwn" and "./nwn"   its nothing near as difficult or scary as he makes it out to be.

 I'm still running dapper by the way. edgy eft, while it looked nice, i think was too buggy to really be called a official release.  haven't honestly heard anything good come out of feisty fawn so i haven't even looked at it yet.
might request a cd given my current situation (the situation being i am out of CD's and have no money to buy blank cds).  hopefully all the complaints about it here in the forum about it have been resolved with updates :).  or i just might sit back and wait for support for dapper to run out and then request a copy of  the newest release when ever it comes. :-k

---

### Post by rillip on 2007-07-13
My take:

1. Half true.  They're 100% dead on about having choices, Ubuntu != Linux, etc.  I challenge them to provide some sort of imperical information about how another community is better.  Of course paid for versions have paid for support, but that's not really a community then, is it, it's a help desk.  

2. This isn't even a statement.  If you're affraid of the command line, Windows may be scary for you.  Ever try getting your IP address set up right when dhcp didn't respond?  Good luck finding a Windows gui for ipconfig.

That asside, Ubuntu does want you to use the command line every now and then for advanced troubleshooting.  However, the average end user doesn't ever need to use it.  It's only when something's not working that it's needed, and really, 90% of the time people are givn CLI instructions because it's easier for those who know how to fix it. If they ask for non-cli ways, they'll probably get told how to do what they want with Nautilus or some GUI face for a CLI tool.

3. was addressed in his update. There are tons of books, guides, pdfs, etc. that you can buy/print/download.  Sure, you can't pay to have a manual shipped to you like RedHat. Ask how many Windows users know wherer their Windows manual is.  Now ask how many times they've read it.  Now ask how many of those times it was USEFULL.  The fact is a traditional manual doesn't really help most people.  People in regards to their OS are goal driven; they don't care to read a manual, find out a bunch of superflous information, and not have a solution to their issue.  They want to make a post or read an article on "how do I install multimedia codecs." It's really a stupid "flaw" to bring up.

4. On one hand, he complains you need to do too much to install from source, a daunting process, and on the other he complains you need to use CLI at all.  This is stupid to bring up too.  If you want to install from source, you can figure out how to make it work.

> If you didn&#8217;t know the first thing about forums and weren&#8217;t very good at using google (e.g., you listen to music and check email on yoru PC and that&#8217;s about it...which takes care of a large chunk of normal users) how would you know to do this? 

Bullocks.  If you just listen to music, you're not going to need a program that's installed by source.  Almost everything comes with a .deb, is in a repository, has an rpm, etc.  I have never once had to install from source yet.  This comment is just totally off.

>  I&#8217;d rather give a new user Slackware than Ubuntu for this reason alone.

You have GOT to be kidding me.  Slackware is NOT for the feint of heart.  This is just about the biggest hyperbole I have ever seen.  Saying you should use Slackware as a totally new-to-Linux-former-Windows-user because you can install from source and it has a guide (which Ubuntu does) is just stupid.

5.  Moot point.  The speed increase, as mcduk noted, is trivial compared to other factors that are beyond the scope of the article.  Also, if you so choose, you can make use of that.  I'm not running the i386 kernel, and it wasn't rocket science to do either, just install from the repo, check the grub menu, chose it at start up. Wooooow.  So hard, since he can install his crazy never heard of music program from source on Slackware with a user's manual in hand. :roll:

Overall, the article is completely off. The first point is the only one that makes any reasonable statement at all.

---

### Post by rillip on 2007-07-13
> **sir_cheats_a_lot said:**
> 
 I'm still running dapper by the way. edgy eft, while it looked nice, i think was too buggy to really be called a official release.  haven't honestly heard anything good come out of feisty fawn so i haven't even looked at it yet.
might request a cd given my current situation (the situation being i am out of CD's and have no money to buy blank cds).  hopefully all the complaints about it here in the forum about it have been resolved with updates :).  or i just might sit back and wait for support for dapper to run out and then request a copy of  the newest release when ever it comes. :-k

FYI, that does seem to be the general consensus; Edgy Eft was the redheaded step-child.  Fiesty Fawn seems to work great for most people, but upgrding to Fiesty seems to be a little troublesome.  Most of the complaints/help requests I've seen about Fiesty aren't Fiesty specific, but rather run of the mill "this feature isn't working."  I'm still running dapper and don't see the need to upgrade yet.  I'll probably wait until a version comes out with KDE 4.0 integrated.

---

### Post by stchman on 2007-07-13
> **sulekha said:**
> Hi all,

   I found criticisms in the name of tips at the following site:
  [http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html](http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html)
  
 to what extent these are true????

Seems to me that he ponders on and on about Ubuntu having no manual.  When you buy a system pre-installed with XP or Vista there is no manual either.

Point 1.  Yes you are free to install nay distro out there you want.  I like that ability.

Point 2.  Since the advent of Feisty you won't need a terminal to do most things.

Point 3.  Already covered.

Point 4.  Yes build-essential should be installed by default.  I like that Windows people crab about this when Windows comes with no compilers at all.

Point 5.  Should Ubuntu compile using a compiler optimized for i686?  Would there be much of a performance improvment.  Is XP i686 optimized?

Interesting but not that interesting article.

---

### Post by sulekha on 2007-07-15
Hi all,

   I found a more detailed criticism as,
                                         Ubuntu Linux's Achilles' Heel: It's Tough To Install On Laptops
   read the full story here:
                                      [http://www.informationweek.com/software/showArticle.jhtml?articleID=201000451](http://www.informationweek.com/software/showArticle.jhtml?articleID=201000451)

---

### Post by bapoumba on 2007-07-15
Thread moved to "Community Cafe".

> **sulekha said:**
> Hi all,

   I found a more detailed criticism as,
                                         Ubuntu Linux's Achilles' Heel: It's Tough To Install On Laptops
   read the full story here:
                                      [http://www.informationweek.com/software/showArticle.jhtml?articleID=201000451](http://www.informationweek.com/software/showArticle.jhtml?articleID=201000451)
This last point is already been discussed here:
[http://ubuntuforums.org/showthread.php?t=498482]("http://ubuntuforums.org/showthread.php?t=498482")

---

### Post by rbmorse on 2007-07-15
Ok...but I'm not clear about what it is you are really asking here. 

I personally think Mr. Wolfe is a world-class idiot (based upon some of his other work) so I am not particularly surprised he elected to do a "hit piece" on the most popular Linux distribution available simply because it is the most popular.  I'm sure he views his mission as a "journalist" is to "...comfort the afflicted and afflict the comfortable." But, so be it. 

Still, Ubuntu is not perfect and many people have trouble during installation. This is no secret. Look at the new user, general help, and installation and upgrade forums on this very site. While  the volume of posts may be a little disturbing, I think we could better address your specific concerns if you would tell us what they are.  Simply putting up pointers to someone else's opinion and experience may be entertaining, but it is not really useful as each installation is different and there are many, many individual factors that come into play. 

If you think your hardware suite may be problematic with Ubuntu, tell us what you're using and see if others with the same machines have been successful, or see what they've had to do to get working. If you concern is whether or not functionally compatible software may be available to fulfull a specific need then ask...chances are there is, or perhaps  even a way to use the same package you use now, but on Linux. 

I suspect that if you were to try to install Ubuntu in the same hardware Mr. Wolfe chose for his article you would have much the same experiece he did.  But, if you were to ask here if Ubuntu is a good match for whatever hardware suite you are using I believe you will get accurate, honest and reliable advice as to whether or not Ubuntu would be good for you to try.

---

### Post by Naralas on 2007-07-15
Why does he criticize an OS... about being installable from source...

Since when is that the easy way to do it?

---

### Post by Wiebelhaus on 2007-07-15
The better & more popular ubuntu gets , the more people will bitch and hate , that's the bottom line mate.

---

### Post by godd4242 on 2007-07-15
> **sulekha said:**
> Hi all,

   I found criticisms in the name of tips at the following site:
  [http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html](http://linux-blog.org/index.php?/archives/154-5-Unique-Tips-for-New-Ubuntu-Users.html)
  
 to what extent these are true????

What an absurdly outdated article.

---

### Post by ThinkBuntu on 2007-07-15
> **strider1551 said:**
> I'll comment on a few things.

From #4:

If you aren't good with Google and you only use your computer for music/email (i.e. a casual user), what are the chances that you need to install something from source?  Moreover, what are the chances that you know *how* to install from source with the exception of needing build-essential  installed?  I'm not saying that this doesn't happen, just that the group of people who need things outside the repository and who can find things outside the repository and who don't know how to find help are a very limited number of people.

From #5:

I used Arch Linux for several months, which is optimized for i686, and I have to say that my computer wasn't noticeably faster.  Besides, if the perfectionist in you want i686 optimization, you can always set your own CFLAGS and whatnot and "sudo apt-get -b source <package>"
Don't knock Arch on speed...it's noticably faster than Ubuntu.

---

### Post by tbroderick on 2007-07-15
> **godd4242 said:**
> What an absurdly outdated article.

Agreed. Why is it being posted now? It's over a year old. Let it rest.

---

### Post by crimesaucer on 2007-07-15
Anyway...how difficult is it to follow the directions that are usually posted when you have to compile a program from source?

It sounds worse then it actually is.

---

