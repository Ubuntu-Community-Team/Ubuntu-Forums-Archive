---
title: "[Idea] OSX-style app installation"
date: 2007-12-10
forum: Ubuntu Brainstorm
---

### Post by castironpants on 2007-12-10
One of the things I really like about OSX is the way you can install programs by dragging an icon into an Applications folder. You can also run the program by clicking on the icon. I know it would be a big simplification, but I think some users (like me) would really like this. The source code could still be saved in some folder. but I think a separate folder of applications would be really neat.

---

### Post by Auria on 2007-12-10
Hmm i don't think this will happen anytime soon (not that i wouldn't like it to, though). Almost all Linux distros favor massive package management for everything... look at Gobo Linux though, they are trying to make a different file hierarchy that includes a "Programs" folder containing apps packaged in a format similar to that of OS X IIRC.

---

### Post by smartboyathome on 2007-12-10
You won't be able to drag an app to install it, but you can uninstall it by deleting the folder for it in /Programs. I like how it is done in Gobo, cause it is very organized (unlike the default filesystem, which has /usr/bin, /usr/share/bin, /usr/local/share/bin, etc).

---

### Post by coolen on 2007-12-11
As pointed out, Gobo Linux is doing something like this, but it won't make it into any existing mainstream distro.

---

### Post by smartboyathome on 2007-12-11
> **coolen said:**
> As pointed out, Gobo Linux is doing something like this, but it won't make it into any existing mainstream distro.

I have actually started a topic to discuss this, but it seems people are afraid to move from the existing file structure. If someone wants it, they will have to recompile the kernel and patch it themselves. :(

---

### Post by coolen on 2007-12-11
It's not a matter of people being too afraid. For one thing, porting the existing system to a Gobo structure would take a tremendous amount of work, remove the Debian base, quite possibly break a lot of stuff, and it's non-standard. Linux (and almost all Unix variants) have used this filesystem structure for a long time, and do so to increase interoperability.

It won't happen with an existing distro. Someone, somewhere, may be able to assemble a team to bring the Gobo system to a user-friendly distro, but no one's going to do it themselves. There's not enough incentive.

---

### Post by Auria on 2007-12-11
Anyway my opininon is that when you need a database to know what's installed or not, it's because the way it's installed is broken :) but i know it's not going to happen, and i'm sorry about it cause there's some really nice improvmeents in it. Anyway.

---

### Post by qamelian on 2007-12-11
> **smartboyathome said:**
> You won't be able to drag an app to install it, but you can uninstall it by deleting the folder for it in /Programs. I like how it is done in Gobo, cause it is very organized (unlike the default filesystem, which has /usr/bin, /usr/share/bin, /usr/local/share/bin, etc).

Actually, the standard Linux filesystem hierarchy is also very organized if you take the time to learn it. Although some directories, like /usr/bin & /usr/local/bin, may appear to be redundant, they each serve a very specific purpose. In fact, if everybody follows the rules of the filesystem hierarchy, it is actually one of the best organized and least confusing filesystems I have ever used.

---

### Post by qamelian on 2007-12-11
> **smartboyathome said:**
> I have actually started a topic to discuss this, but it seems people are afraid to move from the existing file structure. If someone wants it, they will have to recompile the kernel and patch it themselves. :(

It's not fear. That fact is that the Gobolinux file structure is simply not very good in the opinion of a lot of people, myself included. From what I've seen, it does nothing really beneficial except to cater to users too lazy or afraid to learn the Linux Filesystem Hierarchy. If Ubuntu went the route of a Gobo-like filesystem structure, I would drop it like a shot. The LFS standard is extremely logical and easy to learn if you put your mind to it. When I first started using Linux, I managed to learn most of the important stuff about the structure of the filesystem over a weekend, so how tough can it be?

---

### Post by smartboyathome on 2007-12-11
> **coolen said:**
> It's not a matter of people being too afraid. For one thing, porting the existing system to a Gobo structure would take a tremendous amount of work, remove the Debian base, quite possibly break a lot of stuff, and it's non-standard. Linux (and almost all Unix variants) have used this filesystem structure for a long time, and do so to increase interoperability.

It won't happen with an existing distro. Someone, somewhere, may be able to assemble a team to bring the Gobo system to a user-friendly distro, but no one's going to do it themselves. There's not enough incentive.

Like I said before, it won't break the file system since it does it through symlinks. But lets keep this discussion to the relevent thread and go back to topic. :)

---

### Post by olskar on 2007-12-11
I like the way it is now. Mostly I dont have to know where the programfiles is, the things I want to change is the settings and they are often stored in hidden folders in my homefolder (forexample .amsn or .evolution).

One thing I would like to see is more programs following this "standard" so I know where to find my settingfiles.

---

### Post by raynevandunem on 2007-12-11
> One of the things I really like about OSX is the way you can install programs by dragging an icon into an Applications folder. You can also run the program by clicking on the icon. I know it would be a big simplification, but I think some users (like me) would really like this. The source code could still be saved in some folder. but I think a separate folder of applications would be really neat.

I would recommend [Klik]("http://klik.atekon.de/"), simply because it seems to be the less controversial approach to reaching the goal of an "easy-in, easy-out" app-running desktop system that is a bit more portable than, say, package managers.

Plus Gobo, while I am a fan of that distro, brings out "the ugly" from those *nix users who are ardently anti-Windows/anti-Mac (or who are at least of the opinion that application management and filesystem organization in Windows and OS X are for "the lazy"), and proves divisive to any discussion about the merits of different components of a given distribution, especially the filesystem hierarchy, package management systems, etc.

It's a case of the old "ain't broke, don't fix/improve/enhance/change" feeling.

[Observe]("http://developers.slashdot.org/article.pl?sid=03/05/10/1636245").

---

### Post by qamelian on 2007-12-11
> **raynevandunem said:**
> It's a case of the old "ain't broke, don't fix/improve/enhance/change" feeling.

Umm, no. It's a case of there being nothing to fix in the first place. This is another one of those topics that tends to be created by users of other operating systems who think their old way is a better way when it is actually just different. The Gobo approach does nothing to improve anything. All it does is encourage people not to learn how to use their operating system. I can't imagine any scenario in which this is a "good thing".

---

### Post by aquavitae on 2007-12-13
I agree with qamelian, with reservations.  The linux file structure is highly organised and really logical if you understand it, but I do think there's some room for improvement (although maybe that's just the bits I don't fully understand :)). E.g. the etc folder is a bit of a mess - unless you happen to know what each file refers to, how are you ever supposed to work out that the 'exports' file contains settings for nfs? Once you get to know the file names its fine, but I think there should be some sort of a naming standard.

---

### Post by Auria on 2007-12-13
> **qamelian said:**
> The Gobo approach does nothing to improve anything. 

Let me disagree :) it allows installing multiple versions of the same library/program at once without conflicts. It allows clean uninstalling without having to use a database or an uninstaller. I call that an improvement

Anyway you are free to disagree, but please do not say i do not understand the unix file system. I work with it everyday. So please drop that nasty *if you knew what you're talking about you'd agree with me* approach, i have no problem with different opininons but don't assume i'm a nut.

---

### Post by coolen on 2007-12-13
I don't think there's anything wrong with letting software track your installed applications. For one thing, it is capable of automatic dependancy and conflict resolution, the way it's set out in Debian at least allows for housekeeping tasks (scripts run at various stages of the installation/removal process), automatic and pain-free updates, etc.

This could be done with a Gobo-like structure, sure, but it'd still require the user to make use of some sort of package management software to handle these tasks.

APT is what drew me to Debian back when I first started using Linux. It's my single most beloved feature of Ubuntu.

The simple fact is, the filesystem is not broken, and does not need improvement on this scale. You might be able to point out small deficiencies, but it's fine the way it is. I think Gobo's a good project to have around, but I don't think there's any reason for existing distros to start using it. really, especially ones which are already so set in the ways of the Linux standard.

---

### Post by qamelian on 2007-12-14
> **Auria said:**
> Let me disagree :) it allows installing multiple versions of the same library/program at once without conflicts. It allows clean uninstalling without having to use a database or an uninstaller. I call that an improvement

Anyway you are free to disagree, but please do not say i do not understand the unix file system. I work with it everyday. So please drop that nasty *if you knew what you're talking about you'd agree with me* approach, i have no problem with different opininons but don't assume i'm a nut.
Well, if you knew what you were talking about, you would know that you can already do that without the Gobo approach, so please keep your rude comments to yourself. I've been able to do this with the standard Linux filesystem hierarchy since I started using it 10 years ago. I frequently install multiple versions of apps I am testing in Ubuntu in order to compare features vs stability across versions. If you are that familiar with *nix filesystems, surely you must know how to do this as well. It is also very easy for most applications to set the up for an easy clean uninstall, again without resorting to the Gobo approach. I stand by my original statement regarding Gobo. There is absolutely know technical reason to prefer it. None. Not one.

---

### Post by smartboyathome on 2007-12-14
> **qamelian said:**
> Well, if you knew what you were talking about, you would know that you can already do that without the Gobo approach, so please keep your rude comments to yourself. I've been able to do this with the standard Linux filesystem hierarchy since I started using it 10 years ago. I frequently install multiple versions of apps I am testing in Ubuntu in order to compare features vs stability across versions. If you are that familiar with *nix filesystems, surely you must know how to do this as well. It is also very easy for most applications to set the up for an easy clean uninstall, again without resorting to the Gobo approach. I stand by my original statement regarding Gobo. There is absolutely know technical reason to prefer it. None. Not one.

Well, it IS true that it doesn't have any "technical" advantages, since it is based off of the same file structure using symlinks. But there are user experience advantages. I am still looking into implimenting this, and if I can get it to patch on Ubuntu's kernel (bad kernel folder name :mad:), then I will release it as a download. There ARE users demanding it (because it looks nicer in the GUI, which more users are moving to, imho). I don't see any reason why NOT to move to it except that people "don't want to be like mac" and people "don't want to move away from the classic structure".

---

### Post by coolen on 2007-12-14
By all means, do your work. I'm sure there is demand for this. I'm not saying it's a bad structure, but my main point is that, with no real advantage other than slightly lowering the learning curve, it won't happen.
I hope you can make it work. I'd love to see some more Gobo-like distros out there.

---

### Post by qamelian on 2007-12-14
> **smartboyathome said:**
> Well, it IS true that it doesn't have any "technical" advantages, since it is based off of the same file structure using symlinks. But there are user experience advantages. I am still looking into implimenting this, and if I can get it to patch on Ubuntu's kernel (bad kernel folder name :mad:), then I will release it as a download. There ARE users demanding it (because it looks nicer in the GUI, which more users are moving to, imho). I don't see any reason why NOT to move to it except that people "don't want to be like mac" and people "don't want to move away from the classic structure".
I don't want to see it because the structure of the linux filesystem hierarchy (and an understanding of how it works) is an extremely important part of Linux and the obfuscation of important parts of the operating system is never, ever a good idea. For one thing it tends to make trouble-shooting problem a good deal more difficult. It also introduces a greater potential for security risks to be introduced into a system. A perfect example of this sort of thing is the default Windows behaviour of hiding file extensions from end-users, making it much easier to trick them into running malicious code on there own systems. 

Encouraging unnecessary obfuscation instead of encouraging education and understanding is just plain irresponsible.

---

### Post by smartboyathome on 2007-12-14
That is a bad example, qamelian, as this would NOT include more security risks. It doesn't hide any extentions in order to trick people, and a hacker would have to have access to the userspace module to hide any file (which would mean there wouldn't be any more security risk than there is now).

I also don't agree that not encouraging education is irresponsible. If it was, computers would still be using the CLI (after all, why simplify it for them instead of making it easier for them?).

It would make troubleshooting tough though, which is why it might need to start out on its own and then be incorperated into Ubuntu later.

---

### Post by qamelian on 2007-12-14
> **smartboyathome said:**
> That is a bad example, qamelian, as this would NOT include more security risks. It doesn't hide any extentions in order to trick people, and a hacker would have to have access to the userspace module to hide any file (which would mean there wouldn't be any more security risk than there is now).

I also don't agree that not encouraging education is irresponsible. If it was, computers would still be using the CLI (after all, why simplify it for them instead of making it easier for them?).

It would make troubleshooting tough though, which is why it might need to start out on its own and then be incorperated into Ubuntu later.
It is not a bad example at all. You are making the filesystem appear simpler than it is. Most users will look no further than this and I guarantee that problems will result. Your example fails because a GUI does not necessarily obfuscate, although I agree that it can. You will not convince me that the Gobo approach is better. I provide support to too many end-users each and every day who would not need to call me at all if they would take the time to learn even the most basic things about their OS. In fact, back in the days when CLI was your only option, you had no choice but to learn the basics. If you didn't, your computer became quite a handy paper-weight. 

Let's be realistic. A computer is just a tool. Any tool requires some knowledge to use properly. Even a hammer can be used incorrectly if you haven't been show the correct grip, swing, etc. A computer is the same. If you want to use it well, you need to be prepared to learn a few things. Too many users would rather have an OS changed to suit them instead of actually learning the OS. I have no issue with changes that genuinely benefit Linux (and I've seen some great ones in the past 10 year!), but I do and always will have a problem with any change that be detrimental both to the OS and the end-user. At the end of the day, the Gobo route does encourage end-users to ignore the official LFS, and by doing so allows them to know that much less about their OS. That is a recipe for problems and always has been. 
You may not think that it could open the door to any security issues but I've seen a couple of analyses in magazine articles at one time or another by people better versed in *nix security than me who posited very convincing scenarios regarding how this kind of obfuscation could lead to a variety of exploits.
If this is your idea of a good move, more power to you, but I would absolutely refuse to use any Linux distro that went this route. 
Knowledge is power. Use it. Share it. Don't hide it.

---

### Post by coolen on 2007-12-14
It won't be incorporated into Ubuntu later. Period. You are of course free to experiment, replicate, and distribute, but don't expect everyone to drop a system which works so well.

---

### Post by EnvoyRising on 2007-12-15
Disclaimer: I haven't programmed anything in nearly 7 years, and I have certainly never programmed anything in Linux. 

As far as the drag/drop delete, could it be implemented as a nautilus script? What I mean is that dragging an application's launcher into the trash bin would launch an "apt-get remove" event. It's a bit clumsy, but it would allow those migrating from Mac to uninstall programs in a semi-familiar fashion, and would keep an already great file system in tact. As for security, there could be the usual "are you sure you want to uninstall this" dialog that pops up. 

As for doing something similar by just dragging the application folder, perhaps the script could search the contents of the folder to be deleted to see if there is a startup script, or executable binary file in it, then determine that the existence of these files means the user wants to delete the program itself, as opposed to the folder itself (prompting the user for clarification, of course).

---

### Post by smartboyathome on 2007-12-15
> **EnvoyRising said:**
> Disclaimer: I haven't programmed anything in nearly 7 years, and I have certainly never programmed anything in Linux. 

As far as the drag/drop delete, could it be implemented as a nautilus script? What I mean is that dragging an application's launcher into the trash bin would launch an "apt-get remove" event. It's a bit clumsy, but it would allow those migrating from Mac to uninstall programs in a semi-familiar fashion, and would keep an already great file system in tact. As for security, there could be the usual "are you sure you want to uninstall this" dialog that pops up. 

As for doing something similar by just dragging the application folder, perhaps the script could search the contents of the folder to be deleted to see if there is a startup script, or executable binary file in it, then determine that the existence of these files means the user wants to delete the program itself, as opposed to the folder itself (prompting the user for clarification, of course).

I don't think so, as Nautilus scripts don't work that way.

---

### Post by 23meg on 2007-12-15
It's not possible to automate it with Nautilus scripts, which are evoked manually, but it is possible to watch a specific directory for changes using Gamin, or a similar higher or lower level function.

To illustrate that, I put together a primitive script using [fileschanged]("http://fileschanged.sourceforge.net/"), which is a client to Gamin. This will watch a specific directory for new files. When a new file gets dropped, gdebi-gtk will be evoked to install it. (Note that for now, this assumes the file is a valid package; it will attempt to launch gdebi-gtk with every file you drop into the folder.)

First, make sure fileschanged is installed ([click here]("apt:fileschanged") to install). Create an empty directory (e.g. "Applications"), put fcinstall.sh in it, and double click it to run. Now, whenever you put a new file into the directory, gdebi-gtk will be evoked to install it. Drag and drop a .deb file to try.

---

### Post by KillerKiwi on 2008-01-30
Checkout klik2

[http://code.google.com/p/klikclient/](http://code.google.com/p/klikclient/)

It uses a single file for every application (applications are created from deb, rpms etc)

There is also klikd deamon that can watch a folder and add menu items etc when a klik2 cmg is copied in

re 23meg, you should make it unisntall when the deb is removed as well ;)

---

### Post by coolen on 2008-01-30
I must admit, klik doesn't sound like an overly terrible idea.

As long as it doesn't interfere with other parts of the system, then the applications are easily removed. It doesn't require changes to the system structure.

I like :)

---

### Post by KillerKiwi on 2008-01-31
> **coolen said:**
> I must admit, klik doesn't sound like an overly terrible idea.

As long as it doesn't interfere with other parts of the system, then the applications are easily removed. It doesn't require changes to the system structure.

I like :)

Every application is 1 file... you cant screw up your base system :)  removing applications is as simple as deleting the one file

---

