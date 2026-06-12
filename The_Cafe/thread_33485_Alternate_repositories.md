---
title: "Alternate repositories"
date: 2005-05-11
forum: The Cafe
---

### Post by Gowator on 2005-05-11
Is there a list of alternative repositores somewhere.  

Also where can someone ask this question apart from community chat?  

I want mplayer etal but the marillat sources don't work with ubuntu and I have no idea where to look for Ubuntu repositories?

---

### Post by TravisNewman on 2005-05-11
[QUOTE=Gowator]Is there a list of alternative repositores somewhere.  

Also where can someone ask this question apart from community chat?  

I want mplayer etal but the marillat sources don't work with ubuntu and I have no idea where to look for Ubuntu repositories?[/QUOTE]
 which Ubuntu version are you using?
 
You can always search repos with apt-get.org

---

### Post by ruben_b on 2005-05-11
you can check ubuntuguide.org there are extra reps listed and other usefull hints.

---

### Post by Gowator on 2005-05-11
[QUOTE=panickedthumb]which Ubuntu version are you using?
 
You can always search repos with apt-get.org[/QUOTE]


Hoary but are not all of the repos containing all versions or at least the current stable and current development?  

What is the reason for having a thread for officially supported only but non for unofficial sources ...  it makes it hard to know where to post.  Also how can someone ask about a repository if it later turns out to be in universe or something?  Should the post in official repositories be deleted or just the fact that the package in in a unofficial repository?

Are we allowed to post links to unofficial sources or answer where things are if we know or do we have to pretend that we don't know if someone asks the question in official repositoires?  (hence why noone actually answers this question but rather allude to finding it elsewhere?)  

For instance a search of apt-get.org get's Chrisitans repo's twice (in 23 sites) but no specific Ubuntu sources...  is it forbidden to say which ones might work with Ubuntu or not?  

Has anyone got mplayer working .. I also need acidrip and avidemux ... 
if its forbidden to post unofficial sites then pls pm me.

---

### Post by Gowator on 2005-05-11
[QUOTE=ruben_b]you can check ubuntuguide.org there are extra reps listed and other usefull hints.[/QUOTE]

Oh wow.. just found that.  Its got everything that noone is allowed to tell you on the official forums.  (aklthough a few extra repo's still wouldn't hurt)

---

### Post by TravisNewman on 2005-05-11
Um... most of that information IS on the official forums somewhere.

---

### Post by Knome_fan on 2005-05-11
[QUOTE=panickedthumb]Um... most of that information IS on the official forums somewhere.[/QUOTE]

Plus the following little sticky on top of the howto section:
[http://www.ubuntuforums.org/showthread.php?t=23368](http://www.ubuntuforums.org/showthread.php?t=23368)

---

### Post by Gowator on 2005-05-11
[QUOTE=panickedthumb]Um... most of that information IS on the official forums somewhere.[/QUOTE]
So are we allowed to post links to unofficial repositories or not?  

I don't get the whole idea of only acknowledging the official ones in their threads but what of unofficial ones?  

what does 
> This forum is for the installation, configuration, and usage of software supported by Ubuntu. That is, all the software in the main and restricted repositories.

Please only post relevant topics here.
mean?  

How are we meant to know if a piece of software is going to be in official or not ...  what if I ask about an unsupported app, is it ignored, locked or what?

---

### Post by TravisNewman on 2005-05-11
That's the section for ONLY the supported repos. Any other questions go in the "other software support"

We aren't only acknowledging those repositories, that's just the subforum for the supported software. If you ask about an unsupported package, if it's noticed it will get moved to the "other software support" section.

---

### Post by Gowator on 2005-05-11
OK, that was my main question since I expected mplayer would not be in main or supported (apt-cache says not) .. 

So you are saying that by forum you mean just this sub-forum (section) , not the whole of ubuntuforums.org ?  

Also is it then OK to post links to other .deb sources?  
I don't seem to see any on the forum and a search for mplayer doesn't give any in the first page.  

If I was negative it is because I read the sticky literally...

---

### Post by TravisNewman on 2005-05-11
The sticky was only for that forum section (or subforum or whatever ;)) 

as long as you aren't talking about pirating software you're ok. If you put something in the wrong section it'll get moved, but no big deal.

But yeah, i've posted links to other deb sources in the past, lots of people have. No biggie. The only thing is, USE THEM WITH CAUTION. There's no guarantee that things won't break if you use non-ubuntu repos, ESPECIALLY if you use full distro repos, like Debain, etc.

By the way, as for your first post, I use Marillat and it works fine with me.

---

### Post by Gowator on 2005-05-11
[QUOTE=panickedthumb]

By the way, as for your first post, I use Marillat and it works fine with me.[/QUOTE]


I keep getting stuck in libavi deps....  I wondered about forcing it ...
The reason for mplayer is that some avi's seems to play double speed sound in Xine that play fine in mplayer... and also because mencoder is a dep for acidrip  (less important)  

Im running straight Hoary though... perhaps I need some other sources (like security which rejects me) or upgrade to Breezy?

---

### Post by TravisNewman on 2005-05-11
don't upgrade to Breezy yet if you want things to work properly.

And I just remembered, marillat ISN'T working for me lately, but I got mplayer installed before that trouble started.

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=Gowator]
I want mplayer etal but the marillat sources don't work with ubuntu and I have no idea where to look for Ubuntu repositories?[/QUOTE]

For that reason I never use that repo and I stear people away from it now. The backport repo has everything it has that is really wanted in Ubuntued form. Also the multiverse has an mplayer in it, but it won't install when you use that one repo.

---

### Post by Gowator on 2005-05-12
[QUOTE=poofyhairguy]For that reason I never use that repo and I stear people away from it now. The backport repo has everything it has that is really wanted in Ubuntued form. Also the multiverse has an mplayer in it, but it won't install when you use that one repo.[/QUOTE]


But it used to work its only some library file versions that are stamped -ubuntu- that it fals over on?  

Are the win32 codec's also in multiverse?

---

