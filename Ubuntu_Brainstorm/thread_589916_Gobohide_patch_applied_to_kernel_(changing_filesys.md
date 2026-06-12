---
title: "Gobohide patch applied to kernel (changing filesystem structure)?"
date: 2007-10-24
forum: Ubuntu Brainstorm
---

### Post by smartboyathome on 2007-10-24
I thought I would post here, since the other topic from the gutsy idea pool isn't moved here yet. Basically, Gobohide is a kernel patch used on Gobolinux to change the structure of the files to a more "modern" (ie, good looking but longer on command line) file system. It has a compatibility layer that is hidden even from ls, so not to confuse you. The structure is organised into six folders which branch off of /: /Programs, /Users, /System, /Files, /Mount, and /Depot. In the /System, there are many subfolders for the different system files, such as /Links, /Settings, /Variable, and /Kernel. I haven't tested this yet, since I still need to patch the Gutsy kernel, but Apt should still work with this directory structure, since it still has the compatibility layers.

If the Gobohide patch can be used, then maybe the Gobohide module can too (they go hand-in-hand). It basically lists all the directories hidden by the kernel patch for you, and allows you to hide/show these directories. If this could be implimented, then I am sure many people would be pleased.

Anyway, I have been trying to apply the patch for the current Gutsy kernel, and I have not been sucessful yet, as it is a very long process, and I have a very limited amount of time. I will keep trying, though.

Also, to those that say that people shouldn't have to know about the directory structure, and those that do know about it should research it and learn, What about Ubuntu being for beginners at Linux (which is its purpose)? It isn't meant to be easy for the people who use the command line, but for people using the GUI (since that is what almost all beginners are used to). If Ubuntu can make the directory structure easier to navigate for the new people, then I am all for it.

---

### Post by zolookas on 2007-10-24
And i don't see any advantages, you can use .deb packages to graphically install stuff

---

### Post by smartboyathome on 2007-10-24
> **zolookas said:**
> And i don't see any advantages, you can use .deb packages to graphically install stuff

The advantages is that a user can navigate through the folders easily. Here are some examples:

Tom's system broke, and he doesn't know where to find the executable for the terminal is. He might know to look in /bin and /usr/bin, but he would have to look in two places in order to find it. With this system, there is one place for executables.

Suze wants to install flash to Opera (note: I have only tried this in Ubuntu Feisty, where I had to manually copy it). She can't find where the installer put the firefox folder, because there are too many folders to begin with. With this system, she would have an easy time finding it, because all the program's stuff would be in one folder.

---

### Post by amano on 2007-10-24
Hmm. This should either be a move from all distributions to the gobo style, or not at all. Maybe coordinated through the LSB.

People are already used to the UNIX style folders or  they shall get used to it. Otherwise you will not have any chance to continue what you are doing when changing from one distribution to another.

And normal users shouldn't have to wade through the directories and thus they are somewhat hidden by the GUI. Simplicity within the GUI, full control with the CLI. At least that is what it should be in my eyes. There is no need to dumb down the file structure, and if it is, then it should be coordinated for all Unix derivates or at least Linux distributions.

Rather your use cases with people having to copy files manually to get things working should be solved first.

---

### Post by Xbehave on 2007-10-24
i disagree, why should a desktop user learn the linux file system?
is there really even a linux file system, with different version and different distros?
i think this idea is great for desktop users, this would bring standerdisation to to current Desktops, making tri-booting simpler
and lets face it any power user has to be accessing files and folders in /etc and /etc/X11, even if you just want bery or compiz working properly you often have to edit /etc/Xorg.conf 

while to developers it would make no difference, this would jsut be a layer it wouldnt actually move any files so ubuntu wold look the same to devs and other people without this?
if it would be anything more than a compatibility layer so desktop users dont get confused then i would oppose it but aslong as its just a layer so that users have a simler fs then its fine

---

### Post by smartboyathome on 2007-10-25
> **Xbehave said:**
> i disagree, why should a desktop user learn the linux file system?
is there really even a linux file system, with different version and different distros?
i think this idea is great for desktop users, this would bring standerdisation to to current Desktops, making tri-booting simpler
and lets face it any power user has to be accessing files and folders in /etc and /etc/X11, even if you just want bery or compiz working properly you often have to edit /etc/Xorg.conf 

while to developers it would make no difference, this would jsut be a layer it wouldnt actually move any files so ubuntu wold look the same to devs and other people without this?
if it would be anything more than a compatibility layer so desktop users dont get confused then i would oppose it but aslong as its just a layer so that users have a simler fs then its fine

Basically, the folders ARE existant, and the paths such as /etc, /bin, /usr, etc, are symlinks to their current locations, so there WOULDN'T be any issues with it (if you typed /etc/Xorg.conf, it would pull up your Xorg.conf). Also, with the Gobohide module, you can choose what to hide and what not to hide (just use the gobohide command in the terminal).

---

### Post by insane_alien on 2007-10-25
i'd rather just keep it the way it is. it makes sense and i never had any promblems finding my way about when i was a n00b of n00bs. you can make an optional kernel if you want but i'm going to stick with the old way. if this does actually come through, i may just move to gentoo.

---

### Post by mangar on 2007-10-25
Not again...

1. If someone needs to mess around with the filesystem, than the OS is broken usability vise - fix the bugs, not the semantics.

2. A user that sees the need to mess around with the OS, isn't typical user, and can be arsed to spend 5 minutes in wikipedia to read about the file system structure.

3. Having another layer of indirection will only add confusion, overhead to the devs, and no actual purpose.

The only use case I see for making the file system "pretty": lazy "Power User" that want to see how the system works (and "make it go faster"), that have a deep, powerful fear of wikipedia and google; considering that even vista changed the filesystem directory names to be more "unixy", even the aforementioned User will have less of a problem.

---

### Post by Kow on 2007-10-25
I believe this is a bad idea. It is best to follow the LFS standards as closely as possible. If ubuntu went with this idea then a user could easily get confused when searching up information on "linux filesystem structure". They'll get information based on LFS and then be completely confused when they see that ubuntu's is completely different. This could also make package maintenance very difficult since upstream (debian) would stick with LFS. IMO, too much work for too little gain (or maybe anti-gain?).

---

### Post by smartboyathome on 2007-10-25
> **Kow said:**
> I believe this is a bad idea. It is best to follow the LFS standards as closely as possible. If ubuntu went with this idea then a user could easily get confused when searching up information on "linux filesystem structure". They'll get information based on LFS and then be completely confused when they see that ubuntu's is completely different. This could also make package maintenance very difficult since upstream (debian) would stick with LFS. IMO, too much work for too little gain (or maybe anti-gain?).

Like I said in the first post, there would be a compatibility layer for it so that nothing has to be changed other than that.

---

### Post by Xbehave on 2007-10-29
> **mangar said:**
> 
The only use case I see for making the file system "pretty": lazy "Power User" that want to see how the system works (and "make it go faster"), that have a deep, powerful fear of wikipedia and google; considering that even vista changed the filesystem directory names to be more "unixy", even the aforementioned User will have less of a problem.

actually they pretty much copied mac os X which is just like gobo
or just a windows vista/mac os x power user
it has no disadvantages in terms of compatibility, devs or anything
it has no advantage to old users (but they can turn it off)
it has no disadvantage to old users(unless they fear wikipedia and google)

so thats 1 set of users with an advantage and 0 with a disadvantage, only problem is its probably not worth it unless the developers run out of more important work???

---

### Post by smartboyathome on 2007-10-30
> **Xbehave said:**
> actually they pretty much copied mac os X which is just like gobo
or just a windows vista/mac os x power user
it has no disadvantages in terms of compatibility, devs or anything
it has no advantage to old users (but they can turn it off)
it has no disadvantage to old users(unless they fear wikipedia and google)

so thats 1 set of users with an advantage and 0 with a disadvantage, only problem is its probably not worth it unless the developers run out of more important work???

Or it could be user made. Like I said, I am working to apply the patch to the Ubuntu Gutsy kernel. :)

---

### Post by Shingoshi on 2008-03-16
> **Xbehave said:**
> i disagree, why should a desktop user learn the linux file system?
is there really even a linux file system, with different version and different distros?
i think this idea is great for desktop users, this would bring standerdisation to to current Desktops, making tri-booting simpler
and lets face it any power user has to be accessing files and folders in /etc and /etc/X11, even if you just want bery or compiz working properly you often have to edit /etc/Xorg.conf 

while to developers it would make no difference, this would jsut be a layer it wouldnt actually move any files so ubuntu wold look the same to devs and other people without this?
if it would be anything more than a compatibility layer so desktop users dont get confused then i would oppose it but aslong as its just a layer so that users have a simler fs then its fine

I'm in complete agreement with the simplicity of this (Gobolinux) file structure. The majority of new users to Linux, are coming directly from Windows. And it's nothing but pure arrogance to think they should be forced to learn something which is completely unnatural.

The present unix system file structure can be related to having a public library, where all the pages of similar topics in different books are removed, and placed in folders by topic. The Gobolinux system brings sensibility back to the way the majority of people would expect to find things. The present convention, is plain nonsense!

I have been in the process of building a new Linux distribution for research professionals. Those people who have no problem learning new things, but shouldn't have to waste their time on arcane and pedantic systems, just to perform their daily tasks.

So I'm in the process of researching the implementation of the Gobolinux file structure to be used for a server system. Given what I'm seeing, I should probably just install Gobo, and build my server on top of it.

Shingoshi

---

### Post by chrisccoulson on 2008-03-16
> **Shingoshi said:**
> I'm in complete agreement with the simplicity of this (Gobolinux) file structure. The majority of new users to Linux, are coming directly from Windows. And it's nothing but pure arrogance to think they should be forced to learn something which is completely unnatural.

The present unix system file structure can be related to having a public library, where all the pages of similar topics in different books are removed, and placed in folders by topic. The Gobolinux system brings sensibility back to the way the majority of people would expect to find things. The present convention, is plain nonsense!

I have been in the process of building a new Linux distribution for research professionals. Those people who have no problem learning new things, but shouldn't have to waste their time on arcane and pedantic systems, just to perform their daily tasks.

So I'm in the process of researching the implementation of the Gobolinux file structure to be used for a server system. Given what I'm seeing, I should probably just install Gobo, and build my server on top of it.

Shingoshi

It took me about 5 minutes to learn where everything goes in the Linux filesystem structure, and everything makes sense. I can find everything I need to on the rare occasions that I actually need to traverse outside of my home folder.

To me, the Windows filesystem structure doesn't make sense anymore, and I can't work out where stuff is meant to go. Microsoft should adopt the Linux filesystem structure because I don't want to spend 5 minutes learning where files go.

---

### Post by gnomeuser on 2008-03-16
Let's be a bit objective here:

Pros:
Different, potentially easier, filesystem layout

Cons:
Patch will never go upstream (thus we'll be maintaining it forever, time and money that could be spend to better Ubuntu)
Requires changes to many packages to work (this one represents a lot of work)

If the aim is to hide the nasty FHS nature of the layout then we can look at this differently:

We are interested in the way we display data to the user, not as such the actual layout, what the gobo patch does we can do and more can be done using indexers like Beagle and Tracker on a user basis. In fact as a user you should never see data outside of your home dir (even manual configuration should happen in a GUI for translated strings, a common UI and so on).

I think this option allows for a more flexible and extensible way of displaying data, and it does require any changes to the underlying system so for old school admins things don't change. We can do this staged, so as applications get ported the system makes more sense to the user without having a "throw the big switch" day where everything breaks and thus halts development. This means we could do Xesam based population of the database in the mediaplayers as step one along with searching which we already have. Then in the next cycle Nautilus could get extended to do virtual folders based on search results (display all music in one folder regardless of path and so on).

About 2 years ago I was very interested in exploring this problem space so I have a public talk that deals with this. I can dig up the slides and translate them to English for interested parties.

---

### Post by bruce89 on 2008-03-16
I don't see why people would need to know where things are actually. So what if programs are in /bin, /usr/bin or /usr/local/bin?

---

### Post by chrisccoulson on 2008-03-16
I was just having a look at the Gobolinux FAQ, and I found this interesting:
> Did you redesign the tree to make it more newbie-friendly?


No. In fact, it was motivated to fulfill the needs of users who prefer to install applications from the original source packages instead of relying on the distribution. That is the main reason why each application gets its own directory: so you can install it from source there and then remove it with an "rm -rf". So, you see, GoboLinux was designed focusing the experienced user who doesn't like things to be automagical. Our scripts merely automate procedures, but they don't "make decisions", and whenever they have to, they ask first. 



I don't think that users who prefer to install applications from source are typical of Ubuntu users. And users who install applications from source will generally know the Linux filesystem anyway. The typical Ubuntu user uses apt and dpkg, which removes the need to understand the underlying filesystem (as has already been said). IMO, the package manager makes the Gobo filesystem structure redundant, and it would be wasted effort implementing it.

From the Gobolinux home page:
> In GoboLinux you don't need a package manager because the filesystem is the package manager
Again, Ubuntu uses a package manager. In Ubuntu, the filesystem is NOT the package manager.

Implementing and maintaining the Gobo hierarchy would be lots of effort with very little gain - I would prefer developers to work on stuff that is going to benefit everyone who uses the distribution.

I tried Gobo in a virtual machine today. I didn't find the hierarchy any more intuitive than what we've got already, and I actually found it less efficient and productive navigating around their hierarchy. Working in the terminal is a pain because they use capitals in all of their standard folders (which is unecessary - they should stick to lower case), and the folders are all nested too deep. Stuff isn't where I expect it to be , because there is a learning curve for the Gobo hierarchy too. However, I don't see why I should have to learn the Gobo hierarchy, so they should implement the standard Linux hierarchy ;)

---

### Post by oomingmak on 2008-03-16
> **chrisccoulson said:**
> Working in the terminal is a pain because they use capitals in all of their standard folders (which is unecessary - they should stick to lower case)

Ubuntu uses capitals as well (and worse still, it doesn't even do it in any kind of consistent manner). Ubuntu  **forces **you to use a lower case letter for your username when creating your account (despite the fact that names routinely start with a capital letter) but yet folders such as 'Desktop', 'Music' etc. start with an upper case letter.

Blaming Gobo for making it "a pain" to work with mixed case in the terminal is entirely missing the real culprit. It's  the stupid case sensitivity in Unix / Linux systems that is causing you the problem you referred to. If you don't like it, then why not just turn the case sensitivity  off? (then upper / lower case won't matter .... at least far as the Terminal is concerned).

I have lost count of the amount of times that I have read people saying "Linux is all about choice", but whenever this particular topic is raised 'choice' always seems to go straight out of the window and you are supposed to just do as you're told and obey the FHS.

A big deal was made over the introduction of the XDG base directory specification (which recognised that people want to layout their folders differently) and so a standard was created that allowed each user to define their preferred locations. I don't see how someone extending this principal to the rest of the file system is any different. The entire FHS standard is not going to collapse just because someone wants to experiment with getting gobohide to work in Ubuntu. It's not as if this is a launchpad blueprint proposal being considered by Canonical.

---

### Post by bruce89 on 2008-03-16
> **oomingmak said:**
> Ubuntu uses capitals as well (and worse still, it doesn't even do it in any kind of consistent manner). Ubuntu  **forces **you to use a lower case letter for your username when creating your account (despite the fact that names routinely start with a capital letter) but yet folders such as 'Desktop', 'Music' etc. start with an upper case letter.

The folders are thanks to [xdg-user-dirs]("http://freedesktop.org/wiki/Software/xdg-user-dirs").

Regarding the user name "issue", perhaps this is a UNIX requirement.

---

### Post by Triggerhapp on 2008-03-20
> Regarding the user name "issue", perhaps this is a UNIX requirement.

I happily got Captial letters on the T in my name on every other version of linux i tried before Ubuntu.

---

### Post by bruce89 on 2008-03-21
> **Triggerhapp said:**
> I happily got Captial letters on the T in my name on every other version of linux i tried before Ubuntu.

Alright, a Debian thing.

```
adduser (3.105ubuntu1) hardy; urgency=low

  * Merge from debian unstable, remaining changes:
    - Allow uppercase letters in the names of system users.
      This is done by having a separate NAME_REGEX_SYSTEM configuration
      setting which applies when --system is specified.
  * Modify Maintainer value to match the DebianMaintainerField
    specification.
```

---

### Post by Ptero-4 on 2009-03-12
Hi. A couple questions.
1) Where do I download the gobohide patch?
2) Does it move folders around or just merely makes the existing ones "hidden"?

---

### Post by smartboyathome on 2009-03-13
> **Ptero-4 said:**
> Hi. A couple questions.
1) Where do I download the gobohide patch?
2) Does it move folders around or just merely makes the existing ones "hidden"?

Just to note everyone: You will have to recompile the kernel to a different location if you want to move it. Other than that, everything else can be symlinked.

1) You can get the patch from [this GoboLinux recipe]("http://recipes.gobolinux.org/r/?list=Linux&ver=2.6.28.1-r1"). Apply it to your own kernel. Unfortunately, the SVN seems to be down now (besides it being reported up) so I don't know if you will be able to get a patch for a newer kernel. The patch *should* work on 2.6.28.* kernels, though. ;)

2) It doesn't move anything around. Combined with the gobohide userland app (I can't find the sources now, will tell you when I do find them), it will allow you to hide files and folders without having a . in front of them.

---

### Post by Ptero-4 on 2009-03-13
> **smartboyathome said:**
> Just to note everyone: You will have to recompile the kernel to a different location if you want to move it. Other than that, everything else can be symlinked.

1) You can get the patch from [this GoboLinux recipe]("http://recipes.gobolinux.org/r/?list=Linux&ver=2.6.28.1-r1"). Apply it to your own kernel. Unfortunately, the SVN seems to be down now (besides it being reported up) so I don't know if you will be able to get a patch for a newer kernel. The patch *should* work on 2.6.28.* kernels, though. ;)

2) It doesn't move anything around. Combined with the gobohide userland app (I can't find the sources now, will tell you when I do find them), it will allow you to hide files and folders without having a . in front of them.
Downloading the patch now.
A Q? What files are hidden by default (when you boot the patched kernel, but doesn't have the userland app)?
Also. What did you mean by, "You will have to recompile the kernel to a different location if you want to move it."?

---

### Post by smartboyathome on 2009-03-14
No files are hidden by default.

Also, you have to compile the kernel to the location where you want it (ie, you can't install it to /usr/src/linux* if you aren't going to keep it there). If you want it in /Kernel, for example, you have to tell it to compile there (usually with ./configure --prefix=/Kernel, or something like that).

---

### Post by oasmar1 on 2009-03-14
I am definitely up for applying this patch. This is one of my main issues with Linux. Not only is it good for new users and people who don't want to learn it, it is also easier for learning developers. Why should the original UNIX continue, everything should be improved to make it more usable.

---

### Post by smartboyathome on 2009-03-15
By the way, [GoboHide's page]("http://gobolinux.org/?page=doc/articles/gobohide") is back up. Check it out. :D

---

### Post by damis648 on 2009-03-15
This is pretty much *exactly* what OS X does. If you look in /, all you see is /System, /Users, /Volumes, /Library, and something else I think. However, if you view all hidden items, you can see clearly that /var, /bin, etc all still exist there. Everything is hidden and symlinked. :popcorn:

---

### Post by smartboyathome on 2009-03-15
By the way, I created a patch to be applied to the kernel which changes the makefile to store the kernel in /Kernel/$kernelversion. I haven't tried it yet (going to now), but if anyone wants to, here it is (rename it to .patch instead of .patch.txt). To modify where the kernel gets stored, change the lines in the Makefile (should be pretty self explanatory when you look at it).

---

