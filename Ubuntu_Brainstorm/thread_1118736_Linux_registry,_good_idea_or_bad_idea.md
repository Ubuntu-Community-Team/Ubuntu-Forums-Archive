---
title: "Linux registry, good idea or bad idea?"
date: 2009-04-07
forum: Ubuntu Brainstorm
---

### Post by absolutezero1287 on 2009-04-07
I feel that a central place to control all config files is needed as opposed to having them thrown all over the place. We'll have a registry but we'll do it right with restrictions placed on important files like fstab, sudoers, and anything else in /etc.

Here is a hypothetical situation:
A casual user wishes to configure conky, automount certain partitions on startup (fstab, FUSE), needs to configure his printer because it doesn't exactly work flawlessly with CUPS, and wants to set up file sharing (Samba).

All the configuration files for these programs are in different locations, thus making it that much more difficult for the casual user to properly configure everything. Having one central location for configuring all those text files is a great idea, in my opinion. I'm sure most of you disagree because of prior experience with Windows' registry. However, we all know that in Windows the user is constantly running as administrator thus making the registry one giant exploit (UAC doesn't help, most people turn it off). 

Applying the idea of the registry with a proper *NIX based permissions system is actually a great idea and seems pretty solid. It could also control startup programs and configurations for Windows managers like fluxbox and awesome.

One central place to manage the plethora of config files, restrictions placed on systems files, it sounds like a good idea to me.

One user argued that the config files should all be in /etc and ~/.config. From my experience, very few programs bother to use ~/.config. So rather than changing programming habits why not write something to actually keep track of all these various configs (everything from sudoers to innitab)?

This new "registry" could work in tandem with the package manager.

Thoughts?

---

### Post by HavocXphere on 2009-04-07
Bad idea imo.=; (No offence)

Modular & decentralized = good.
Centralized huge file = Chaos & Format PC every X months MS-style.

Besides, I'm not keen on a flood of Linux registry cleaners. uugghh

With config files you can point a finger at some program. With a registry, there is little accountability and you've got other programs fidgeting with your programs data and maybe a registry cleaner or too deciding that some part of your config is not needed.8-[

The MS registry started out well...but then developers started storing pictures (!) and files (!) and @#$% in it and then the stuff hit the fan.

There is a small possibility that the *nix community could pull it off and make it useful, lean and efficient. The risk of it going the same way as MS is too much though compared to the potential benefit. And remember, its not like the MS programmers are idiots...they've got some seriously sharp people and it still went pear-shaped.

FYI: The MS registry also has permissions. Not quite as complicated as *nix permissions, but nonetheless.

---

### Post by ussndmac on 2009-04-07
Thoughts?

The registry file was a bad idea when MS introduced it and is still a bad idea.

Why? Because it creates a single point of failure for the system.

Single point of failure is never a good idea.

Add that the single point of failure is a database file that has to accessed by every process one to many (many) times and assumes everybody that writes to it plays by the same rules and you have a recipe for disaster.

Then add GUIDs (which even MS couldn't get right for years, and is still not living up to it's claimed potential) and now you have a bloated file which is always full of left over junk.

But I'm not biased... ;)

---

### Post by kpatz on 2009-04-07
If it ain't broke, don't fix it.

The registry, as implemented in Windows, is a royal PITA.  Proprietary format, stuff gets hidden in there where you can never find it again (ever uninstall an app, clean all the crap out of the registry, and reinstall only to find that the thing you were trying to fix with the reinstall is STILL THERE??)  Plus, if it gets corrupted, or you delete the wrong thing, it's game over, time to reinstall...

Maybe a happy medium for Linux would be a common configuration file directory (like /etc, but just for application configurations.  Maybe /etc/config or something, and $HOME/.config for user-based configurations).  Put all those .conf files in there, then you always know where to find them.  But each app gets its own file(s), so you don't get an impossible-to-clean mess like with the "wregistry". ;)

As a developer in the Windows platform, I still prefer the old-fashioned .ini files over the registry.  So much easier to work with, easier to hand-edit, easier to switch in and out when testing different configurations, etc.

---

### Post by Therion on 2009-04-07
> **ussndmac said:**
> 

[A] single point of failure is never a good idea.

+1, Came here to say this, etc.

All your egg's in one basket, and all that, you know.

---

### Post by Simian Man on 2009-04-07
Great idea!   Another thing we really need is to make ext4 support increased fragmentation and then write some defragmentation utilities.  Then Linux will be ready for the desktop!

---

### Post by iponeverything on 2009-04-07
It already has one. (at lease gnome does)

sudo gconf-editor

---

### Post by absolutezero1287 on 2009-04-07
All very valid points but try not to think of it as a clone of the Windows registry. It won't have access to "everything". Only certain things. Maybe it could be used to control Samba, cupsd.conf, fstab, sudoers, and other system files. Of course, you would have to be root to edit these files.

Now there could be another section for the user. Maybe make it easy to write a nice .bashrc? Of course, a GUI won't be as powerful as getting your hands dirty and manually editing the config files but for small tweaks it seems a lot easier.

Also, gconf-editor is just awful

---

### Post by iponeverything on 2009-04-07
> Also, gconf-editor is just awful

Luckily most linux users never have to use it.

Martin

---

### Post by showman47 on 2009-04-07
Hi

Linux registry, good idea or bad idea?

answer: yes and no !

Actually you've got one already surely !

synaptic package manager - yes ? (well, a sort of installed application registry)

I don't know the details of how synaptic package manager works, but it obviously uses some kind of database to store what's been installed and where the config files etc are on the  system (right-click on an installed application, and 'properties' gives you all the installation files).

What you don't have (and don't want!) is a stupid system like windows that loads and locks on to the registry every time you log in, which means it can change it in real time but slows everything down and gets slower as you install more software.

I've been using ubuntu now for over 6 months. I loaded loads and loads of programs. I had only 30Gb allocated to ubuntu (dual boot to windows xp). I got down to less that 1Gb of free space and ubuntu never slowed down (just complained if I tried to create a big file, of course).
Windows would have screwed up (or really slowed down) long before that.

So I suppose really the answer is no !

But maybe the package manager's database can be utilised in some way, just to provide info to the system only reading it when it's really needed.

I'm not a linux guru (been on a need to know basis as a web developer)
but I like it, should have learnt Linux years ago !

There's nothing wrong with looking at how microsoft have screwed up (and made a fortune in the process) and using their successes and mistakes to improve ubuntu. But I'm sure you know that already !

showman47

---

### Post by markbuntu on 2009-04-08
No no no never. NO.

Linux is a function based file system. There is no place for a registry file in the linux filesystem.

---

### Post by soltanis on 2009-04-09
Modularity is the key to simplicity, and less can sometimes be more. Building a central registry requires large amounts of time to be expended on design, development, and standards-writing (most of which will doubtlessly be ignored). Storing configurations in configuration files, one or more for each program,  in a relatively standard place (usually in the /etc/[program name]/ directory) means that when one thing screws up, it doesn't screw everything else up with it, and is relatively easy (compared to say, the win32 registry) to fix.

Most applications document where their config files are and what format they're written in. Most good applications store them in intuitive places with intuitive extensions (.conf).

There are always morons who don't document conf locations/formats, but those are the exception to the rule, and generally have alternatives/urge the writing of alternatives that do conform.

---

### Post by irrdev on 2009-04-10
I feel that the registry is Windows' greatest weakness. The registry is loaded each time at startup, and consumes considerable system memory. Additionally, even the best registry cleaner cannot truly find and delete all unused keys. Worst of all, if Windows crashes, there is no way of directly editing the registry to fix a problematic key value. In Linux, on the other hand, it is simple to open a settings file in the etc folder from a LiveCD and make some necessary fixes. 
> Also, gconf-editor is just awful 
This is debatable. The graphical interface of the editor itself is primitive to be sure. However, the concept of the gconf interface is quite good IMO. As I'm sure everyone knows, the gconf keys are actually separate xml files stored in a hierarchy beneath ~/.gconf . I think its wonderful that Gnome's settings are stored in traditional editable text files, but that there is an extremely logical and graphical approach to editing them if users so choose. I frequently make use of the gconf-editor to discover "hidden" gnome settings and make adjustments to the desktop. There are many great settings hidden within gconf. For example, there is even a setting which allows you to specify the screen-location of notifications, serving a similar purpose as that of Jaunty's new notification system. For those curious to try it out, it's located under /apps/notification-daemon. There's also a setting to set custom gtk themes for notifications. ;)

---

